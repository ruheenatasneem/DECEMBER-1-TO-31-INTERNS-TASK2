# DECEMBER-1-TO-31-INTERNS-TASK2
 Build a Simple Web Interface for Owl AI using Python   


 

 <img width="1366" height="768" alt="Screenshot (198)" src="https://github.com/user-attachments/assets/ae5e4d00-b73a-43b0-ae19-86e0457e4025" /> 













 <img width="1366" height="725" alt="Screenshot (199)" src="https://github.com/user-attachments/assets/cb75a56a-e39c-4081-9ab8-bd707b039b9a" /> 










 <img width="1366" height="768" alt="Screenshot (200)" src="https://github.com/user-attachments/assets/a973cb15-7918-40e2-9843-e2bd30ff727e" /> 












 <img width="1362" height="725" alt="Screenshot (201)" src="https://github.com/user-attachments/assets/da2ad335-8ccc-404f-956b-d15a1424f1fc" /> 













 index.html 


 <html>
    <head>
       <title> 
             Owl Ai
       </title>  
       <style>
       body { font-family:Arial;
       margin:50px;
       background-color:#f4f4f4; 
       }  
       .container{ 
        max-width: fit-content; 
        margin:auto;
        width:300px;
       }
       </style>
    </head> 
     <body>
        <div class="container">
            <h2>🦉 Owl AI Interface</h2>
            <form action="/result" method="post">
                <label>
                    Enter your question:
                </label><br><br>
                <input type="text" name="message"  required style="width: 100%"; padding: 8px;> <br><br>
                <button> submit</button> 
            </form>
        </div>
     </body>

</html> 




result.html 




<!DOCTYPE html>
<html>
    <head>
        <title > Owl AI Result </title>
    </head> 
    <body>
        <div class ="container">
            <h1> Owl AI Response </h1> 
            <p><b> Your input:</b> {{message}} </p> 
            <p><b>Response: </b> {{response}}</p> 

        </div> 
        <br> 
        <a href ="/"> Back to Home</a>
    </body>
</html> 



app.py 


from flask import Flask, render_template , request

app=Flask(__name__)   
def owl_ai_response(message): 
    return f"Qwl AI response to: {message}"  

@app.route('/')  
def home():
  return render_template('index.html') 

@app.route('/result', methods=["POST"]) 
def result():
     user_msg = request.form.get('message') 
     response = owl_ai_response(user_msg)
     return render_template("result.html", message=user_msg, response=response)

 
if __name__ == '__main__' :
    app.run(debug=True)    

    









