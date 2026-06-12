---
title: "first thoughts on Ubuntu"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by baomike on 2007-01-30
Two stumbling blocks to the install (which was simple):
logging in a root. I found instructions to do this but I was a bit surprised this wasn't easier to find. 

No ssh. It turns out it need to be installed. Had to find out about  apt-get (that was a new one).


Being a slackware user for many years this is new stuff.

---

### Post by taurus on 2007-01-30
1.  Root account is disable for a reason.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

2.  Not sure about your machine but my install came with ssh.  The ssh server is the one that I have to install by hand.

---

### Post by Benchrest on 2007-01-30
I guess the finding info on root wasn't easier because Ubuntu doesn't recommend root, but sudo instead. In two years I've never found anything I needed to do that I couldn't do with sudo. But because this is different from other Linux distros perhaps this should be publicized more for those coming from another distro.

---

### Post by baomike on 2007-01-30
<<When sudo asks for a password, it needs YOUR USER Password;>>

That was what threw me. It did not seem right  to use a "user" password to get SU privileges.

my next task is seeing if I can find a version of vi that works on ubuntu.  When I am in a hurry VIM does too many wierd things.

Then on to play with MythTV.



NB: Evidently ssh is not installed in the server version, would seem to be a natural for remote adminitration like I am doing.

---

### Post by taurus on 2007-01-30
For vim:
```
sudo aptitude update
sudo aptitude install vim-full
```

But if you are running a server, shouldn't you be installing ssh-server (sshd) so you can connect to your server from another machine?

---

### Post by aysiu on 2007-01-30
The lack of root is confusing only to those who expect root (i.e., Linux users). After all, you don't get Mac OS X users complaining about the lack of a root account login.

*sudo* makes sense to people who've never used Linux before. You go to Synaptic and are asked for your password to install software. Makes sense.

If you have previous Linux experience, how hard is it for you to do [a Google search for *ubuntu root login*](http://www.google.com/search?hl=en&q=ubuntu+root+login&btnG=Google+Search)?

---

### Post by baomike on 2007-01-30
Only using Ubuntu server because  my son had burned a copy of it , and it does load Mysql.
The access is all on an internal net. Since ubuntu is what MythTV is made for I figured I had better try using it. I tried once before on Slack and did not succeed.

Finaly tracked down the prompts. I was used to  changing them in /etc/profile but ubuntu has them in ~/.bashrc. (and a messy one to boot) .  I 'm used to "$ and #".  Leaves more room for the command.

I know new ubuntu users don't know about "pwd".

so far so good. Mythtv is in /usr/local and the fun begins.



NB: mildly surprised that firefox was not included in Ubunto-server. But not a problem.

---

