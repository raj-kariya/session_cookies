# Understanding Cookies And Session
- In the world of web devlopment, cookies and sessions are two important concepts that helps store and retrieve information about users.
- As we know, HTTP is stateless, which means that all requests sent are independent. However, in some situations, we need to keep track of user activity. A common example is the shopping cart in an ecommerce website. When we add an item to the cart, we don’t want it to disappear when we visit the next page. Therefore, we need to maintain this type of information.
- One Solution to overcome the stateless behavior of the HTTP protocol is to use Session. We'll start by exploring sessions, and then move on to cookies.

## Session 
- Sessions are a way of storing information about a user on the server-side. Those information will then be used in subsequent requests.

- By definiton, Web Session is a sequence of network HTTP request and response transactions within the same user.
  
- Sessions provides the ability to establish variables — such as access rights and localization settings — which will apply to each and every interaction a user has with the web application for the duration of the session.

- Let’s take an example. Suppose you’re logged into a web application and you provide your username (or email) and password, then submit. Next, you are redirected to the dashboard page where you can access it if you’re logged in.

- In a non-session mechanism, you’ll not be able to access the dashboard, even though you logged in. This is because HTTP requests are independent of each other. When you send the second request to the dashboard page URL, the server doesn’t know who you are.

-In a session-based mechanism, when you log in, the server stores some information about you in the session variable (for example, creating a variable that store the authenticated user ).In the next request, when you go to the dashboard page, the server recognizes you by checking that session variable and let you access the dashboard page.

### How does session work
- When a user logs into the website, a session is created. In this session, you can created variable called “session variable” that store data in a key/value format ( like cookies ).
This session is associated with a randomly generated unique ID, which is created by the server. It’s called “session ID”.

- The generated session ID is then sent to the user’s browser and stored as a cookie, while the session data is stored on the server-side.Now, when the browser send a request to the server, it’ll send the cookies with the request.The server will receive the cookie from the incoming request and retrieve the value of the session ID.

 ![How Session id is sent to the user browser](https://user-images.githubusercontent.com/34595361/213847155-8d94e041-3ace-4628-9486-e3f696cd6668.png)

-  Afterwards, the server will search for the session and retrieve all the data stored within it once it is found.

-  Well, The cookie store the session ID of the active session. PHPSESSID is the default name given by the PHP back-end server that created the session ID.

- Let’s take a closer look at our previous example to understand what is happening in more detail.When you log in, a session is created with a unique ID (session ID). The session ID will be sent to the user’s browser.The server will then create a session variable auth_user ( for example ) and store in it the information of the actual logged in user. The session data will be stored in a file on the server side. The name of the file will be the session ID.

- When the user request the dashboard page, the browser will send the cookie that contain the session ID with the request.The server receives an incoming request, retrieves the session ID, and searches for the associated session. Once the session is found, the server retrieves the data.Finally, the server will need to check the existence the that auth_user session variable. If he found it, the server will give the access to the dashboard page.

- Sessions are often used to store sensitive information such as user credentials and financial data. They are more secure than cookies because the information is stored on the server-side and not on the client-side.

- Session data are stored in a file in the server. Well, you should know that the session data are stored in different ways depending on the configuration.For example, in PHP the default mechanism is to store the session in the file system This provides the advantage of simple file-based storage and the ability for sessions to exist for long periods of time.

- Another way is to store the session data in a database, there are several advantages. You have better control over the length of a session, as you can control when the session data is cleared out. You have better security because the data is not stored in a common area.
  
- Most of the time, the session is stored in the cache for performance purposes, for example, if a website has a lot of users, it will be a good practice to store the session file in a cache so that the retrieval process will be fast.
