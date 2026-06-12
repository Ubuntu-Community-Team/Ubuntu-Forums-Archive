---
title: "Getting ready for the install...."
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by enduser79 on 2013-07-02
Been a Windows guy for 17 years now (95 came out when I was in high school).  Recently Cisco certified, but wanted to learn Linux.

[U][B]Before I go further, here's what I've been dealing with in the past few days:

[/B][/U]I bought the "Linux for Dummies" book at the store and it came with a CD containing the different versions.  I tried Mint first, but it does not recognize my USB keyboard/mouse on my old desktop.

I tried dual boot last night on an IBM Lenovo x60 but Mint isn't loading, just a blank screen. Heck I didn't even get a dual boot option.

No worries, I made a complete backup of my Windows partition so I'm back to square one.

A good friend suggested I go with Ubuntu, so tonight I'd like to try and make it work.

Was wondering if anyone had any tips. I will try it on my old desktop first, since I have nothing important on that machine.

---

### Post by cub on 2013-07-02
Start up in Live CD before you install to check if everything's working. So you don't have to go through the process of installing only to find out something is not supported or not working.

If the desktop pc (which is another one than the Lenovo?) is very old you could try out Xubuntu or Lubuntu which use less resources than the standard Ubuntu.

---

### Post by su:bhatta on 2013-07-02
In case u get the same problem with Ubuntu i suggest u try this once before u r done.. 
In case the following is the solution then even the Live cd will not work and give u a live session.... hence u gotta reboot and try the following...

worked for me gr8 n later found out itz a well known work around:


On the first boot from the Ubuntu DVD u will find a **purple screen with a Man=keyboard** sign at the bottom of the screen ... u have noticed it right?

1)At that screen u hit **Enter**...
it gives u a next screen where by default u will get a list of languages with English selected as default..

2)on that screen select English---> hit enter... It will get u the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen u will see options underneath F1 F2 ... **Hit F6** on that screen.. 
u will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 
It should just boot up fine ....

Let know what happened...

---

### Post by enduser79 on 2013-07-02
Wow, 42 minutes and I already got a response. You guys rock!!! I will try this stuff later this afternoon. (I'm in the Pacific Time zone)

---

### Post by enduser79 on 2013-07-02
Ok, made a lot of progress today. I booted from the CD, it's Ubuntu 10.04.  I installed it into the HDD (formatted the entire 120GB).

I am working on the old desktop computer.

The only problem I had was the password I thought I chose was not working, so I re-installed the whole thing over again and chose to allow myself to log in without typing in the password.

So far so good. The keyboard/mouse work just fine.  I did some message about the Nvidia driver, but I didn't care about it too much. I just want to make the internet work.

At this point, the desktop is in another room, it has power, ethernet and keyboard. I would like to work on it from a Windows terminal.

I tried RDP, Telnet, SSH nothing seemed to work.  Do I need to tell Ubuntu I want to remote into it?  I know it's on the network, hence I can see it in the router, it's pinging fine from 192.168.1.12

---

### Post by enduser79 on 2013-07-02
Ok, I did some searching, I think I found it. I have to install the xRDP package on Ubuntu ?

[http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/](http://www.liberiangeek.net/2012/05/connect-to-ubuntu-12-04-precise-pangolin-via-windows-remote-desktop/)

---

### Post by SuperFreak on 2013-07-02
Ubuntu 10.04 is no longer supported so you will not get any security or other updates. I would suggest before you get too far with 10.04 you instead install ubuntu 12.04 which is supported till 2017 (Download available [COLOR="#0000FF"][HERE]("http://www.ubuntu.com/desktop")[/COLOR]. You will find instructions [HERE]("https://help.ubuntu.com/lts/installation-guide/")

---

### Post by KARNVORbeefRAGE on 2013-07-02
Agreed SuperFreak, [[COLOR=#000000]enduser79[/COLOR]]("http://ubuntuforums.org/member.php?u=1835926")  if your computer is older and having trouble running the newer Ubuntu versions (12.04 or 13.04) with the Unity interface, you could try Lubuntu or Xubuntu which are lighter interfaces.

Lubuntu:  [http://www.lubuntu.net/](http://www.lubuntu.net/)

Xubuntu:  [http://xubuntu.org/](http://xubuntu.org/)

---

### Post by enduser79 on 2013-07-03
Alright, so I got the RDP to work.  I can now remote into the machine, so it's much easier to work on.

I tried to utilize the Update Manager in order to install 12.04, but ran into the following error:

[B]"Failed to run /tmp/tmpdmev9c/precise as
user root.
Unable to copy the user's Xauthorization
file"[/B]

[IMG]http://i.stack.imgur.com/Lnhnf.png[/IMG]

I will try to download it manually......stay tuned.

---

### Post by enduser79 on 2013-07-03
I am looking to disable the 'S' shortcut key. I was able to disable the 'M' by un-checking the Expo, but the 'S' is still active...

---

### Post by Bucky Ball on 2013-07-03
*Thread moved to **Installation & Upgrades**.*

---

### Post by cub on 2013-07-03
> **enduser79 said:**
> I tried to utilize the Update Manager in order to install 12.04, but ran into the following error:

I will try to download it manually......stay tuned.
Yeah, running an upgrade from 10.04 to 12.04 will be difficult. Much better to download and do a fresh installation.

---

### Post by Bucky Ball on 2013-07-03
> **cub said:**
> Yeah, running an upgrade from 10.04 to 12.04 will be difficult.

Why? LTS is designed for upgrade to the next LTS. Has been like this for awhile, you don't have to upgrade through the interim releases to get there. 10.04 upgrades directly to 12.04, no difficulty about it, in theory. Upgrading through Update Manager can be problemmatic, though, regardless of what release you're upgrading to.

---

### Post by enduser79 on 2013-07-03
> **SuperFreak said:**
> Ubuntu 10.04 is no longer supported so you will not get any security or other updates. I would suggest before you get too far with 10.04 you instead install ubuntu 12.04 which is supported till 2017 (Download available [COLOR=#0000FF][HERE]("http://www.ubuntu.com/desktop")[/COLOR]. You will find instructions [HERE]("https://help.ubuntu.com/lts/installation-guide/")


Many many thanks again!! :p

I was able to burn the ISO and boot from the disk. I installed 12.04 and it's running.  I then went through some updates and rebooted.

I then installed the xRDP so I can manage this machine from a Windows terminal.

---

### Post by enduser79 on 2013-07-03
Ok, I was able to share a folder and move files between the server and my Windows terminal.

2. I like the way you can tell the OS to "grab" a package and install it, beats searching for the EXE in Google, example:

**sudo apt-get install wireshark**

---

### Post by Bucky Ball on 2013-07-03
Glad you got your issue solved and you're loving Ubuntu! Please mark thread as solved by following the link in my signature and post back with a descriptive title, plenty of info, and in the appropriate category for any further issues/questions. Good luck. ;)

---

