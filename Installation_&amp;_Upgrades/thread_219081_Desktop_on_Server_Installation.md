---
title: "Desktop on Server Installation"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by garry_wx on 2006-07-19
Hi, I tried searching for this topic but did not find anything. 
I managed to install the Server w/LAMP. Installed it on an IBM BC 8843 blade. Seemed to go ok. Logged in. Good. Tried a browser from outside, got the default page. Good. I want to run the desktop that I think is installed (not sure). Previously I had downloaded the Alternate CD, then used aptitude to install GNOME. But could not figure out how to start it after logging in. Now on the server I am not sure if GNOME is installed by default and if it is how to start it. 
Second question would be to configure SSH, I'll try searching for that unless someone has a quick answer. 

Thanks.

---

### Post by T700 on 2006-07-19
If I understand your question, no, there is no GUI installed by default with the server version.  It is however, a simple matter to install it via Aptitude.

Paul

---

### Post by garry_wx on 2006-07-19
Thanks for that, managed to figure out I needed openssh-server and used aptitude to install that. ubuntu-desktop is not in the list of things I can install. Will go and put the alternate CD in and try that. I still need to figure out how to start the desktop once I install it.

---

### Post by garry_wx on 2006-07-24
Updating this for anybody who cares. 
Just puting in the alternate cd won't help to install anything off of it. Found out, not sure how, some message I got I think, that I need to run apt-cdrom to get the different source to be recognized.   Proceded then to run aptitude install ubuntu-desktop. So that started. It wanted to know the answers to some question I wasn't sure about. So I tried to cancel the choice I had made and it just sat there looking stupid at me. So I hit ctrl-c and started aptitude again, chose local or something, and it proceded to do a bunch of stuff. Finally in the end it finished and I typed startx and wow a desktop. Ok great I say. Start poking around and now if I try to run anything other than a terminal the thing hangs and then the whole system reboots. This is so much fun! ](*,)

---

