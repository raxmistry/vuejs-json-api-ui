<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <div>
            <div class="mybutton" v-on:click="showdiv">
                <p>My Button</p>
            </div>
            <div id="hideme" hidden="true">
                <p id="replacetext">{{ myfunction() }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HelloWorld',
    props: {
        msg: String,
        text: String
    },
    data: function() {
        return {
apiMessage: {} 
        }
    },
    methods: {
        showdiv: function(event) {
            console.log("showdiv event");
            this.axios.get("http://localhost:4000/bot").then( (response) => {
                console.log(response.data.text)
                this.apiMessage = response.data;
            });
            document.getElementById("hideme").hidden=false

        },
        myfunction: function(event) {
console.log(this.apiMessage);
return this.apiMessage.text;
}
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
.mybutton {
    color: blue;
    margin: 5px 5px 5px 5px;
    padding: 10px;
    border-style: solid;
    border-width: 2px ;
    border-radius: 25px;
    width: 50px;
    box-shadow: 0 9px #999;
    text-align: center;

}

.mybutton:hover {
    background-color: lightblue;
}

.mybutton:active {
    background-color: lightblue;
    box-shadow: 0 5px #666;
    transform: translateY(4px);
}
</style>
