---
title: "Need help with Installing Java"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by jeremy.reid on 2007-12-27
I am trying to install java with the instructions that are givin to me at the link below

[http://www.java.com/en/download/help/5000010500.xml#selfextracting]("http://www.java.com/en/download/help/5000010500.xml#selfextracting")

I cant even get through the first step of the process because after the first step i get this message

> jeremy@Beast:~$ su
Password: 
su: Authentication failure
Sorry.
jeremy@Beast:~$ 


why am i getting an authentication failure i tried again thinking that i just typed password wrong but nope could you all help me out here

thanks in advance
Jeremy Reid

---

### Post by icheyne on 2007-12-27
To install Java, you are best using this guide, rather than going to Sun directly:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Use sudo instead of su:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by naugiedoggie on 2007-12-27
> **jeremy.reid said:**
> I am trying to install java with the instructions that are givin to me at the link below

[http://www.java.com/en/download/help/5000010500.xml#selfextracting]("http://www.java.com/en/download/help/5000010500.xml#selfextracting")

I cant even get through the first step of the process because after the first step i get this message

why am i getting an authentication failure i tried again thinking that i just typed password wrong but nope could you all help me out here


Well, as already noted, you are getting the auth error because you can't 'su' in ubuntu unless you specifically enable it.  you have to use 'sudo' to execute your root commands.

The link given for installing java is useful for making you think about what you are going to be doing.  Myself, I have no interest in experimenting with alternative Java implementations.  I use NetBeans for Java development and I want the real mcCoy to go with it -- and that includes the current version (which may or may not be available at this time through apt-get).  My experience with using the software libraries is that they are slow to update and if you rely on them, you will usually be behind in your versioning.  YMMV.  Ubuntu 7.10 ships with gij 4.2.1, "Java 1.5.0" OOB.  That's only a JRE, of course.

If you care about automatic updates and keeping track of your software additions, then you need to follow the instructions given at that link.  If you don't care, then you can just download from Sun and run the installer.  The downside to riding The Cowboy Way is that you may well be on your own if trouble appears.

After you d/l the installer, remember to set the permissions to make it executable.  You probably already did that, but I often forget it.  Then:

# sudo ./jdk-6u3-linux-i586.bin

That is it.

Thanks.

mp

---

