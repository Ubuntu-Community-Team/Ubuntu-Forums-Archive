---
title: "difficulty installing Lubuntu"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by jmbarsk on 2012-12-08
[FONT=&quot]I just tried to install Lubuntu onto my old laptop but I am having some difficulties. I have searched online for help and believe that my problem is that I need to install video drivers but I have been unable to find a step by step for somebody like me - first time user. 

When I startup ubuntu normally, the screen will go black, If I go into advanced options and type "nomodeset" into the GRUB, then my computer starts up without a graphical interface and brings me to [/FONT]
  [FONT=&quot]Jacob@lubuntu:~$[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]From that point I am unsure of what to do. I do not have any experience using commands in Lunix. I assume that I arrived at what is called the terminal? Is that correct?[/FONT]
[FONT=&quot]
[/FONT]
  [FONT=&quot]How do I fix things so that I can access the graphical interface? Do I need to install video drivers? How do I do that – step by step. [/FONT]
  
_My video card is_ [FONT=&quot]
[/FONT]NVIDIA CORPORATION, model NV11 (GeFroce2 Go) (rev b2)
  My computer is _Dell Inspiron 8100_ 
  

Please help me get this installation working. 



  Sincerely,
  Jacob

---

### Post by TheFu on 2012-12-08
[http://forum.linuxmint.com/viewtopic.php?f=46&t=63805](http://forum.linuxmint.com/viewtopic.php?f=46&t=63805) seems to say that this laptop probably has limited RAM.  Do you have 512MB or less?
At that link, the person waited 30 minutes to see the Mint desktop.
On a RAM limited machine, I'd recommend installing Ubuntu Server, then install a minimal LXDE desktop. 

You will be at the shell, which is what happened above. Some might call it a terminal or CLI, but a terminal is usually a program, not just the interface.

On an extremely limited PC with less than 512MB of RAM, Ubuntu (any type) is probably not the best desktop version.  I'd recommend that you check out TinyCore. I used to recommend Puppy Linux, but running as root all the time just seems "wrong" and lazy.  Linux developers should know better.

I believe the default F/LOSS video drivers should work fine on your hardware. No need to install proprietary nvidia drivers.

Sorry I'm not any real help with a point-n-click answer.

---

### Post by 2F4U on 2012-12-08
> Do you have 512MB or less?
At that link, the person waited 30 minutes to see the Mint desktop.
On a RAM limited machine, I'd recommend installing Ubuntu Server, then install a minimal LXDE desktop. 

As far as I understand the poster, he attempts to install Lubuntu, which is LXDE. So, even if the machine has only 512 MB of RAM, it would be sufficient to run Lubuntu.

Here is a extensive post about dealing with black/blank screens and desktop environments that won't start:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

This is a multi-step analysis process and you might have to apply different workarounds.

---

### Post by vasa1 on 2012-12-08
> **2F4U said:**
> ...
Here is a extensive post about dealing with black/blank screens and desktop environments that won't start:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
...
Very nice! Worth reading in any case.

---

### Post by snowpine on 2012-12-08
> **TheFu said:**
> 
On a RAM limited machine, I'd recommend installing Ubuntu Server, then install a minimal LXDE desktop. 

Desktop/laptop users should not install Ubuntu Sever. Ubuntu Server is for, well... servers.

---

### Post by jmbarsk on 2012-12-09
Thank you for the replies

TheFu: Thanks, I looked at your link. In that thread the OP seems to have somehow got Mint working. I am not familiar with the term LXDE but I installed Lubuntu. My understanding is that Lubuntu is a minimal version of ubuntu that I thought would work well on my older computer. Correct me if I am mistaken.
  
2F4U: Thank you for the link. I will read through it and try a few things. 
   
  If anyone else has any ideas, the following is a more detailed list of my system
  
Dell Inspiron 8100 1133VT Setup
  Mobile Pentium III-1.13 GHz/733 MHz
  CPU Speed 1.13 GHz
  Memory: 512 MB
  Video Controller: NVIDEA GeForce2GO
  Video Memory: 32MB
  Audio Controller: ESS Maestro 3
  Hard Drive: 20005 MB
  Other details: my keyboard is broken so I use a USB keyboard for this machine. I believe everything else is working except I am unsure about the CD drive. I had trouble with when I first tried using a CD to install the OS.

---

### Post by vasa1 on 2012-12-09
I think it would help if you mention 
what this computer was running before you tried to install Lubuntu
how exactly you prepared the computer before you installed Lubuntu
what options you saw and chose during installation
the size of your hard disk
the free space available
anything else you can think of

---

### Post by johnycsf on 2012-12-09
when you get to [FONT=&quot]Jacob@lubuntu:~$
Try typing:
#startx
[/FONT]

---

### Post by jmbarsk on 2012-12-09
Thank you vasa1

Before installing Lubuntu - I was running Windows XP, however it ran extremely slowly and was not satisfying to use. Originally this computer ran Windows Millennium.


  How I prepared the computer &#8211; well I was unable to use a CD or bootable USB drive to install the software so I copied and pasted the Lubuntu ISO onto my computer and used Unetbooting to install. During the install I believe I wiped the previous OS. 



  Options during installation &#8211; unfortunately I do not remember what options I choose. I was following a guide but now, after the fact, I do not recall which guide I used. 
  

My hard drive is 20gb
  

Free space &#8211; well I used the whole drive for the Lubuntu. Its all free except for the space taken up by the Lubuntu installation.

---

### Post by jmbarsk on 2012-12-09
johnycsf - what is this supposed to do? I typed it and it did not do anything

---

### Post by johnycsf on 2012-12-09
startx on some distros is what starts the GUI.

---

### Post by vasa1 on 2012-12-09
> **jmbarsk said:**
> johnycsf - what is this supposed to do? I typed it and it did not do anything
Generally speaking, you'd be better off not typing what people suggest without knowing what it means.
I think your best bet is to go through the thread that 2F4U referred to.

---

### Post by johnycsf on 2012-12-09
> **jmbarsk said:**
> johnycsf - what is this supposed to do? I typed it and it did not do anything

startx is what starts the GUI.

---

### Post by johnycsf on 2012-12-09
> **vasa1 said:**
> Generally speaking, you'd be better off not typing what people suggest without knowing what it means.
I think your best bet is to go through the thread that 2F4U referred to.


FYI:
[http://www.brighthub.com/computing/linux/articles/17895.aspx](http://www.brighthub.com/computing/linux/articles/17895.aspx)

---

### Post by claracc on 2012-12-09
I think the problem can be in the old nvidia graphics card.

I have found this thread: [http://ubuntuforums.org/showthread.php?t=1687699](http://ubuntuforums.org/showthread.php?t=1687699). Perhaps it can help you to install legacy nvidia drivers ( it seems the newest doesn't work in so old cards) as it is addressed in this thread.

I have lubuntu 12.04 in a similar laptop (2002 hardware), pIII 1GHz CPU, sys 630/730 64 MB graphics card, 448 MB RAM, 20 GB HDD, and it is usable with lubuntu to surf web (not flash videos, it is a resources hog, I have to use a special script to convert youtube videos to be in .mp4), doing office tasks and playing streaming music. 

I hope it helps

---

### Post by TheFu on 2012-12-09
> **jmbarsk said:**
> TheFu: Thanks, I looked at your link. In that thread the OP seems to have somehow got Mint working. I am not familiar with the term LXDE but I installed Lubuntu. My understanding is that Lubuntu is a minimal version of ubuntu that I thought would work well on my older computer. Correct me if I am mistaken.

Lubuntu is LXDE on Ubuntu - what you want.  It it didn't work, then I'd follow that other link about all the fixes for blank screens during installation, especially if you are not comfortable with the shell.

In Linux, the GUI interface is not core to the OS, so getting the OS installed can be without any GUI. Later the GUI libraries can be added as needed with a little typing.  I find this way easier to trouble shoot because the OS is more easily available to provide data about what it sees and 1 task, driver install, can be performed at a time.  

When I say "a little typing, I really do mean it.  Most commands can be started with a few characters, then a {tab} pressed to complete them. Options can often be auto-completed too.  Once you see someone else using tab-completion, you'll never go back.  To people that don't know about this, it looks like magic.

BTW, I've run Lubuntu on Pentium4 machines with 1G of RAM. It runs nicely.  The motherboard for that box fried over the summer and was replaced with a hot, new, MB and CPU, so it is not a low-end box anymore. Actually it is the fastest box that I manage now for Mom to check her email and do some investment trading with over the web.  She has never noticed the difference between the Core i7 box and that old Pentium4 thanks to LXDE-buntu.

---

### Post by jmbarsk on 2012-12-09
Hello Bogan,
  I tried all the things that you asked me to do. Here I posted two pics that show how it played out for me. By the way, do I need to be connected to the net while using these commands?
[IMG]http://ubuntuforums.org/<a href=http://imageshack.us/photo/my-images/525/img0124se.jpg/ target=_blank>[IMG]http://imageshack.us/a/img525/8462/img0124se.th.jpg[/IMG] [[IMG]http://imageshack.us/a/img809/6532/img0125aw.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/809/img0125aw.jpg/")[/IMG]

Sorry, this post was meant to be placed in a different thread. my mistake

---

### Post by Mister08 on 2012-12-09
> **jmbarsk said:**
> johnycsf - what is this supposed to do? I typed it and it did not do anything

Under some distros e.g. Backtrack startx starts the graphical interface

---

