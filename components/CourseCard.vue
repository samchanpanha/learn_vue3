
app.component('coursedisplay',{
    props:{
        paid:{
            type: Boolean
        }
    },
    data(){
        return {
            course: 'Vue 3 Intro',
            tags:[
                'Vue',
                'Javascript',
                'WebDev'
            ],
            languages:[
                {id:1,name:'Vue'},
                {id:2,name:'Javascript'},
                {id:3,name:'WebDev'}
            ],
            description:'This is an introductory course to Vue',
            price:'$ 19.99',
            available:true,
            imgURL:'https://source.unsplash.com/user/erondu/200x150',
            imgALT:'An image with a desktop computer!'
        }
    },
    methods:{
        purchase(){
            alert('You bought this course!');
        },
        addMoreItem(){
            let num = this.languages.length+1;
            return this.languages.push({id:num,name:`Samchanpanha${num}`});
        }

    },
    computed:{
        hasImageAlt(){
            return this.imgALT.length > 0 ? 
            this.imgALT : 'This is an image without ALT text!';
        },
        premium(){
            return this.paid
        }
    },
    template:
    /*html*/
                  `<h1>{{course}}</h1>
                    <ul>
                        <li v-for="(tag,index) in tags" :key="index">
                            {{index+=1}} {{tag}}
                        </li>
                    </ul>
                    <h1>Loop of Object</h1>
                    <ul>
                        <li v-for="language in languages">
                            {{language.id}} : {{language.name}}
                        </li>
                    </ul>

                    <h1>How to use IF</h1>
                    <p v-if="available">You can buy the course!</p>
                    <p v-else>You cannot buy the course!</p>

                    <h1>How to use Click</h1>
                    <button class="btn btn-primary lg" 
                    @click="purchase">Buy Now!</button>

                    <button class="btn btn-success lg" 
                    @click="available = !available">Toggle me available</button>

                    <button class="btn btn-success lg" 
                    @click="addMoreItem">Add more language</button>

                    <h1>How to Images In Vue</h1>
                    <img v-bind:src="imgURL" :alt="hasImageAlt">
                    <br/>
                    <p>{{price}}</p>
                    <p>{{description}}</p>

                    <h1>How To use coomputed Properties</h1>`
});