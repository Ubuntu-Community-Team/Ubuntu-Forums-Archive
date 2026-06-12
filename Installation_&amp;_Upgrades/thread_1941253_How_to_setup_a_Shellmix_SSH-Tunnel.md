---
title: "How to setup a Shellmix SSH-Tunnel?"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by Hellageddon on 2012-03-15
So, I have made myself an account on shellmix.com and now I own a login.
It works, I can connect to my shell with** ssh [EMAIL="username@shellmix.com"]username@shellmix.com[/EMAIL]**

But now I want to tunnel all my traffic of my machine through that ssh connection, is that even possible?

So first of all, I went to my router and opened UDP/TCP from 9070 to 9070.
Then I started an SSH-Session with **ssh -ND 9070 [EMAIL="username@shellmix.com"]username@shellmix.com[/EMAIL]**

Then I went to my system preferences > proxy config > manual proxy config:

[x] user same proxy for all protocols
127.0.0.1 Port 9070

And that doesn't work.
When I fire up Firefox to connect to any site, my connection gets a reset.
Where is the flaw here?

---

### Post by Hellageddon on 2012-03-15
Allright, I figured it out.

When connecting to Shellmix the command ssh -ND 1234 [email]user@tunnel.shellmix.com[/email] is legit. Afterwards you want to go to your Preferences>Network Proxy>
and on manually proxy config you want to leave everything blank, except on Socks host. There you type in localhost and the port is, as in your custom command, 1234.

No router-config needed, as far as I know.

---

