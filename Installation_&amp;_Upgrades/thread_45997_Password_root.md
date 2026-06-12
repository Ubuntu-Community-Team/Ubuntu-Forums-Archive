---
title: "Password root"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by cyberdancer on 2005-07-02
I have just installed ubuntu, but the installation never asked for a password for the root.

So when i type su in the terminal i dont know wich password i must give.

I have an account with a password, but that password doesn't work

---

### Post by PMO6022 on 2005-07-02
[QUOTE=cyberdancer]I have just installed ubuntu, but the installation never asked for a password for the root.

So when i type su in the terminal i dont know wich password i must give.

I have an account with a password, but that password doesn't work[/QUOTE]

By default ubuntu does not enable a root account. You can use sudo <command> instead, and supply your user password when prompted. If you really want a root account, see [http://ubuntuguide.org/#setchangeenablerootpassword]("http://ubuntuguide.org/#setchangeenablerootpassword")

---

### Post by Hyperion on 2005-07-02
Hi,i m a newbie too,but that's the only thing about Ubuntu i know.There is no separate root account in Ubuntu.You use sudo to get root priviledges.So your user password is used only to login after booting.the password it asks you in the konsoles is always your root password.

I hope i was clear enough.Actually i think it's a good system not having separate root account.It's confusing for linux newbies.Good luck!My first encounter with ubuntu is the most problematic of all the distros i ve tried  :-|

---

### Post by Omnios on 2005-07-02
YOu can also use " sudo su root " to go into root if you have a lot stuff you want to do but then again you can launch root terminal. Personaly I prefer sudo......................... 
Just makes me feel a bit more secure "secure is inportant!". And never go no password! And read up on security I found a frew tricks and heard of problems and now typing a pasword all the time don't bother me any more.

 Anyways when using sudo su or su you need to add the user you want be it root or your personal account etc otherwise is just gives a bad password warning.

---

### Post by rioki on 2005-07-03
I personly find the sudo / root as deamon user quite a good idea. But the instalation prosess sould ask you if you want to set the root password or not. (With a BIG notice that it is realy bad... bla bla bla) 

I had used the better part of a morning at work to figure that out. I am lucky to be the admin of my machine at work and I decided to migrate from debian sid to ubuntu. This because I used it a home and liked it. 
Now our users are all stored in a nis database and I never add users at instaltion. Once the instalation was finished I noticed that 1. I had no user installed and 2. no root password. Ok I googled, with my second pc (a win 2000 that I am not admin of) and got the procedure out to blank the root password. I finaly worked. 
I then setup a root password for the machine and it worked. The thing is I need a root acount to get things back on trak if something goes kablowe in the Server-Pool. This includes changes to nis or nfs/automount. 

My point is that for the default local users instalation this is a good polecy to use sudo but one should be able to change that while instalation.

---

### Post by irusun on 2005-07-03
As a long time user of Linux, I was quite confused after installing Ubuntu - it took me a few hours to figure out what was going on with the whole sudo/root thing.  If Ubuntu is going to do something radically different like change the nature of the root user (from every other distro I've ever used), it should be much more clear up front during the installation.

It appears that Ubuntu tried to tackle the issue that many new users to Linux would simply use the root account as their personal account because it was often inconvenient to do routine system maintenance otherwise.

However, I think there's often a tendency to go a bit overboard about using root - as displayed by this thread.  It starts to sound like some 1950's American propaganda film - and it's obvious that some of the posters are just regurgitating what they've read from some other overzealous poster.  

*nix has its origin in a multi-user environment, often involving dozens if not hundreds of users.  With so many remote and sometimes unknown logins, security is obviously an issue.  But the reality is that most of the people using Ubuntu are just single (or family) users who just want an alternative to Microsoft.

The idea that there's rarely a use for root is a complete Utopian Linux fantasy.  It's nice to see Ubuntu has made it less necessary to be a root user than a lot of other distros, but the root user is a very useful thing to have around for involved system administration.

The danger in Ubuntu, in my opinion, is that the user uses the password so frequently for everyday tasks, that is soon becomes automatic to just enter it in without thinking about it.

I'm not complaining about how Ubuntu uses root, but it really starts to sound ridiculous the way some go on about how "bad" logging in as root is.  It's like any tool - learn how to use it, respect it, and have fun!

---

