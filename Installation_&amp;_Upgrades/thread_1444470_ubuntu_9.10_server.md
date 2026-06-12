---
title: "ubuntu 9.10 server"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by mikeprosceo on 2010-04-01
I was having so much trouble with ubuntu 8.04 that I deleted off my computer and did a fresh install of 9.10.  I downloaded the 64 bit iso from the internet, burned it to a disc and installed it.  When it asked if it should be the server version I thought I said no.  Now when I boot it only boots to the server version and all I get is command line.  Can I get out of this and get my regular ubuntu screen back or did I install the wrong version?  Please someone help. - Thank you - Michael Prosceo

---

### Post by tommcd on 2010-04-01
> **mikeprosceo said:**
>  When it asked if it should be the server version I thought I said no.
Can you provide an exact link to the iso you downloaded, including what exactly you clicked on? You may have downloaded the server iso by mistake. Also, how big, in megabytes, is the iso you downloaded? That is, if you still have it. The server iso is significantly smaller than the desktop live CD iso. 
> **mikeprosceo said:**
> 
 Now when I boot it only boots to the server version and all I get is command line.  Can I get out of this and get my regular ubuntu screen back or did I install the wrong version?
Fortunately, thanks to the power of the APT package manager, there is an easy fix for this.
Boot up your Ubuntu install. Login at the command line and run:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
Then reboot and (hopefully) enjoy your new Ubuntu 9.10 system!
Reference:
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)
> 
The Server CD provides you all the tools you need to set up a server (including LAMP). It does not come with a GUI (graphical user interface), but you can add one later if you feel you really need one (most people recommend against using a GUI on a server). If you accidentally downloaded the Server CD and want a home desktop instead of a server, you can install a home desktop by typing
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start

EDIT:
NOTE: Nowadays the correct command to start gdm (and login and get to the desktop) is:
```
sudo service gdm start
```
I'm not sure if the "sudo /etc/init.d/gdm start" still works or not.

Write back if you need more help.

---

### Post by mikeprosceo on 2010-04-01
Ok, boy do I feel stupid.  The iso I downloaded actually says (it is still on my desktop of another computer) Ubuntu-9.10 server AMD 64.iso and it is 654.5 mb. I tried the steps you said to get the desktop but when I asked for the update I got "could not resolve us.arcive.ubuntu.com", "could not resolve security.ubuntu.com" and "couldn't find package ubuntu-desktop."  Does this mean I have to look for the non server iso and reinstall again?  I don't mind doing it but is there another work around?  Thanks - Mike

---

### Post by tommcd on 2010-04-01
Can you post your /etc/apt/sources.list, just to see where you are working from ??

---

### Post by mikeprosceo on 2010-04-01
can you tell me how to get the /ect/apt/sources.list? I tried a few things but really don't know how to get it. - thanks

---

### Post by mikeprosceo on 2010-04-01
I figure I wasted enough of everyone's time and mine as well.  I am just going to reinstall the desktop 9.10 vs.  Thank you for your help - Mike

---

### Post by tommcd on 2010-04-02
> **mikeprosceo said:**
> can you tell me how to get the /ect/apt/sources.list? I tried a few things but really don't know how to get it. - thanks
1. Form the terminal you could just type:
```
less /etc/apt/sources.list
```
You can then scroll through the file with the arrow keys, then hit the "q" key to exit from less. Also:
```
cat /etc/apt/sources.list
```
will also dump the whole file into the terminal.
2. Just open any nautilus file manager window and navigate to: file system > etc directory > apt directory. Inside the /etc/apt directory will be a file named sources.list that you could copy and paste here.

Write back if you still need more help.

---

