---
title: "How to install KPPP to ubuntu 8.04"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by drileysr on 2008-09-15
I just installed ubuntu 8.04 and this is my first experience with this o.s. My only means of connecting to the internet is via verizon wireless card. Some of the comments I have read indicate the best way to set up the dialer is using KPPP. Can anyone explain to me how to see if I have this already installed in my ubuntu o.s. or how to install it if not? Thanks.

---

### Post by drileysr on 2008-09-15
Anybody????? Or am I possibly in the wrong ubuntu forum for this type of question?

---

### Post by wesley_of_course on 2008-09-15
First off  " Welcome " to Ubuntu !  Now I'm probably being dense here but ,,,,, Are you trying for wireless or dialup ?   Synaptic has most every piece of software to get U going .  Could you explain in a little more detail what it is your trying to do ?

---

### Post by drileysr on 2008-09-15
wesley_of_course, thanks for the reply. I am of course new to linux. Have always used xp pro. But was given an old laptop and decided to give linux a try. My only means of connection to the internet is with a verizon usb 720 wireless card which I insert into the usb 2.0. I then use the same wireless towers as cell phones. In the xp's that I have installed this to, I simply inserted the cd and installed the drivers and off I go. When I tried it with ubuntu, nothing!! I understand that it can be programmed to work but requires somthing called KPPP. How do I get KPPP if I can't connect to the internet? Evidently, ubuntu doesn't come with it. Thanks for any and all help.

---

### Post by johnnycalifornia on 2008-11-23
Hi Wesley, 
            I think he an I are having the same problem.  Ironically, Ubuntu installation CD has no means to allow you to connect to the internet so you can download packages from the repositories.  Mostly, he and I need the files needed to connect to the internet since we both have USB wireless aircards as our only means of connecting to the internet. The files needed, are (again Ironically) kppp and I believe kppp logging which are connection configuration programs that will allow us to actually connect to the internet.  I am looking for an alternative way to do this.  I have connection in my windows computer, but I have no idea where, how, and what to look for to get this process completed. I have a typical PC intel with Ubuntu 8.10 installed.  Thank you for your time and consideration.

---

### Post by robert shearer on 2008-11-23
The easiest way is possibly to order or download and burn on another computer(or using windows if you dual boot) the 'Kubuntu  8.04 alternate cd'.

Kubuntu ships with kppp and kppp logging.

Then boot back into Ubuntu and simply put the Kubuntu disc into your disc drive.Wait....

A window will appear saying that a disc of software has been detected and do you want to open it with the package manager.

Hit OK and wait....

The disc will be read and added as a local repository of software.

Log out and back in then open Synaptic package manager and search for kppp.

When it is found right click on it and select 'mark for installation' then 'apply'.

You will be prompted to put the Kubuntu disc in the drive and the packages will be downloaded and installed.

I think this is easiest because there are a number of libraries that need to be installed to support the kppp packages as they are from the KDE desktop and Ubuntu uses Gnome.
Using KDE bits like this is fine and works no problem.

It is simpler to let Synaptic take care of all the associated packages needed than to do it manually.

When you select install for kppp there will be a long list of other packages needed.Accept these.

Last note. Use the Kubuntu disc version that corresponds to the Ubuntu you have installed..so if you have 8.04.1 Ubuntu then use 8.04.1 Kubuntu.

No doubt someone with more experience than me can suggest a simpler way so may pay to wait and check.

However, the above worked for me, so as a last resort....

---

