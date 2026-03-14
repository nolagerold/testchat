# testchat
**NOTE:** This was more of a technical, for fun, and short-term project, and does not have a user interface (as of the time of writing this README).
## Usage
### client.py
A module, not a standalone script, containing the `Client` class, which is usable for all client-side operations. The `Client` class' methods are described briefly below.
- When a Client class is being initialized via `Client(ip, port)`, at least an IP address is expected. The default port is `5500`.
- `.connect()` attempts to establish an initial connection to a server using the defined IP address and port.
- `.register(username)` expects a username, which it will then send to the server and request to make a user entry for. Additionally, `.register()` generated a UUID to be used as a user ID for logins. This is not currently saved to any file or configuration and will only exist per-session.
- `.send(message)` expects a message, which will be sent to the server, and the server will verify the sender's identity via the user's UUID and username.
- `.fetch(since=None, last=None)` defaults to fetching the most recent message sent to the server. The optional argument `since` should be a timestamp, and the server will return all messages sent after that timestamp, while the optional argument `last` will fetch a specific quantity of recent messages.
- `.close()` closes the client's connection to the server.
### server.py
The server does most of what it needs to do automatically, and is an executable python script on its own, but if you want to specify a specific IP and port (other than a blank IP and port 5500), you will need to do so at the end of the file, where `main()` is executed.
**TODO/BUG:** The server currently doesn't shut down until all clients are disconnected. It is possible to forcibly terminate it, but be aware of this nuance when testing.
## Info
This was a small idea I worked on with a school friend. I may revisit it in the future. A rough outline of the protocol can be found in [OUTLINE.md](OUTLINE.md), while examples can be found in [EXAMPLES.md](EXAMPLES.md) (though I have not checked if they are up to date).
