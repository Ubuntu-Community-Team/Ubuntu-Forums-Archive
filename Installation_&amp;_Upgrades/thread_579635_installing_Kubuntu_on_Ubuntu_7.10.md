---
title: "installing Kubuntu on Ubuntu 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by jonray74 on 2007-10-18
Hello everyone. It's my 1st post here. I have a couple of questions about installing Kubuntu on Ubuntu 7.10.

1.) I just reinstalled my PC with 7.10 from 7.04 and now I can't seem to install Kubuntu Desktop directly when it takes me to the prompt.
I tried the ff:

[I]sudo apt-get update
sudo apt-get install kubuntu-desktop[/I]

but said couldn't find it. How do I install Kubuntu on Ubuntu 7.10 server? I was able to do it on 7.04 Server. 

2.) I also read that Ubuntu 7.10 comes with Gnome 2.20 or something. If so, how do I turn it on from the command prompt? If anyone of you guys can help that would be great.

Thanks,
John

---

### Post by paxmark1 on 2007-10-18
Others are probably more experienced.  

2.  Ubuntu 7.10 would come the new and flashier Gnome 2.20.  That would be your "window" environment.  However if you have only gone with the Ubuntu 7.10 SERVER   -   you have no windowing environment.  You are console based  i.e. everything is just black and white.  It is designed for computers doing tasks that are not visually based, such as ftp servers, mail servers, web servers, etc.  

To install it 

sudo aptitude update    
sudo aptitude install ubuntu-desktop         

or if you prefer apt-get

sudo apt-get update
sudo apt-get install ubuntu desktop



The servers are busy from Ubuntu are busy today (many of them are using the server verion of Ubuntu), so you might have to repeat the update and install process once or twice.  

peace, Mark

---

### Post by jonray74 on 2007-10-18
Hi Mark,

Thanks for the reply. Yes, you are right, I do prefer the Server Edition because I have a website that I manage, and i'm currently testing Ubuntu to run my Website later on cause it's currently on Win2K Server, and i'm tired of it.

I will try the command you gave and see if it works. Otherwise, I may just put 7.04 back again until 7.10's bugs gets fixed.

Thanks,
John

---

