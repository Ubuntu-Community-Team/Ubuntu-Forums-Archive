---
title: "Need a suggestion on Ubuntu server"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by Surendra on 2008-11-19
Hi everybody,
I installed Ubuntu 8.04 server on my virtual pc. Now i download ubuntu-desktop and trying start it but i am getting below errors

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo apt-get update

sudo /etc/init.d/gdm start
 * Starting GNOME Display Manager...                                     [ OK ]
home@ubuntu:~$

When i ran the startx command i am getting below error message.

 startx

X: user not authorized to run the X server, aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console
home@ubuntu:~$


Can anybody tell how to fix this problem.

Thanks in Advance
Suren

---

### Post by donkyhotay on 2008-11-19
From the error message it looks like a permissions problem to me. Although it is a *bad* idea to run X as root I would try running it with sudo just to confirm/deny if this is the cause of your problem. Obviously if it works then you'll want to immediately exit out of X and start rummaging through your file permissions. Course depending on what your server is and how vital it is you may not want to even temporarily give it less security then the average windows desktop installation.

---

### Post by Surendra on 2008-11-20
I didn't run startx command as a root. I ran this command on my user id.

---

### Post by donkyhotay on 2008-11-20
No, no, I assumed you did run startx as a regular user, thats just common sense on linux. Thats the way you are supposed to do it because running as root can compromise the security of your system. What I said was I would try running 
sudo startx
just to find out if it works that way or not. From the error message it sounds like your user account doesn't have permission to run the X server. If this is the problem then running startx while as root will allow X to run but with seriously compromised security. This is just a way to confirm whether or not the problem is with your permissions. If the problem is with permissions then startx will work because you will have permission to do anything you want (as root) and X will then start (though you will want to immediately quit). If the problem is with something else then it still won't launch with root.  But then having confirmed whether or not if the problem is with your permissions it will help narrow down what the cause of your problem is. If it's with user permissions then you'll want to start going through your files relating to the X server and find out what does/doesn't have read/write/exec permissions that should. If it isn't with user permissions then you'll need to look at something else (what I don't know).

---

### Post by Surendra on 2008-11-22
I resolve this issue with following commands.

1. sudo apt-get install xfonts-base

2. sudo apt-get install ubuntu-desktop

I ran these two commands and rebooted my server. IT'w works.

Thanks for you suggestions.

---

### Post by Lars Noodén on 2008-11-22
It's a server, not a desktop, so you might reconsider the wisdom of installing a desktop environment on the server.  If you can't live without graphics, then maybe just X by itself (plus some key applications) will do the job: if it's not there, it can't break

If you do insist on turning a server in to a desktop, then try running a lighter desktop, such as Fluxbox, or even just a plain window manager like Fvwm.  If nothing else, while using it, you will be reminded that "now I am on the server"

---

