---
title: "Lubuntu broken after update"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by Engineeringtech on 2014-08-22
Hi,

I'm a Linux novice.   I installed Lubuntu 13.10 on an old, underpowered laptop, just yesterday.   I used it for about two hours with no problem.    I thought I should udate it, so I started the update manager from the menu in the lower left corner of my screen.  It downloaded and installed a bunch of security, software, and kernel updates.  No error messages.     I shutdown rather than reset, because it was very late, and I needed some sleep.

This morning, I booted it up.  Everything progressed normally, up to and including the login screen.  After I entered my passord, the desktop switched to black and left me with a white band at the bottom of the screen, devoid of any icons, applets, or menus.    After I installed the OS, there were applications menus, and icons in this band.  But they are not there anymore.    If I right click the desktop, I am presented with a very limited list of applications, including Firefox.  That is how I am posting this thread.   "Desktop preferences" appear in this right click list, but they don't seem to be functional.   

What happened to my desktop, and how do I fix it?

JC

---

### Post by Rex Bouwense on 2014-08-22
Not sure what happened.  However, you should be aware that Lubuntu 13.10 is no longer supported.  It reached its End Of Life in June 2014 I think.  Recommend that you install 14.04.  It is a Long term Support version.

---

### Post by vasa1 on 2014-08-22
Maybe OP opened an Openbox session?

---

### Post by Engineeringtech on 2014-08-22
I was just looking for a lightweight package that would run quickly on my old hardware.   Is 14.04 still going to do that?  I don't think this machine will last more than a year.....

---

### Post by Engineeringtech on 2014-08-22
> **vasa1 said:**
> Maybe OP opened an Openbox session?

I have no idea what this means, or how to fix it.  I am a linux novice.  This is my first installation of Lubuntu.

---

### Post by kansasnoob on 2014-08-23
> **Engineeringtech said:**
> I have no idea what this means, or how to fix it.  I am a linux novice.  This is my first installation of Lubuntu.

In the upper right hand corner of the login screen there's a widget you can click to display the available sessions. Here's a [screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=250351&d=1392455047"). Just make sure you select Lubuntu.

But you would be much better off installing 14.04.1 because EOL is just that - end of life!

---

### Post by vasa1 on 2014-08-23
> **kansasnoob said:**
> ...
But you would be much better off installing 14.04.1 because EOL is just that - end of life!
+1 to that. 14.04 is not heavier than 13.10 and if 13.10 ran okay for you so should 14.04.

---

### Post by kansasnoob on 2014-08-23
> **vasa1 said:**
> +1 to that. 14.04 is not heavier than 13.10 and if 13.10 ran okay for you so should 14.04.

I do maintain over 20 old boxes that won't run 14.04 because of recent changes to the Xstack, but they will run 12,04 with it's original 3.2 series kernel and Xstack (which is supported until April 2017) if I install using the archived [Ubuntu 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/") and running the [Classic (no effects)]("http://ubuntuforums.org/showthread.php?t=1966370") DE. But the 12.04.2, 12.04.3, 12.04.4, and 12.04.5 images must NOT be used to avoid [Precise HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support") and [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL")!

---

### Post by vasa1 on 2014-08-23
> **kansasnoob said:**
> I do maintain over 20 old boxes that won't run 14.04 because of recent changes to the Xstack, but they will run 12,04 with it's original 3.2 series kernel and Xstack (which is supported until April 2017) if I install using the archived [Ubuntu 12.04.1 images]("http://old-releases.ubuntu.com/releases/12.04.1/") and running the [Classic (no effects)]("http://ubuntuforums.org/showthread.php?t=1966370") DE. But the 12.04.2, 12.04.3, 12.04.4, and 12.04.5 images must NOT be used to avoid [Precise HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support") and [HWE EOL]("https://wiki.ubuntu.com/1204_HWE_EOL")!

That's going to get OP running for cover :(

But OP's already on 13.10. Do you have instances of what ran on 13.10 not working on 14.04?

---

### Post by mörgæs on 2014-08-23
OP, just do a fresh install of Lubuntu 14.04.1. Only if you face trouble, which is unlikely because 13.10 was working well, we might need to take a look at the warnings posted here.

---

### Post by Engineeringtech on 2014-08-23
Just to explain my actions...  I downloaded 13.10 several months ago, when I started having problems with my laptop.  I was just looking for a lightweight Linux release that could run quickly on my old hardware.  I didn't know 13.10 was soon to become unsupported.  In fact, I didn't know much of anything about Lubuntu, and have very minimal experience with Linux.     So when my old OS died, I reached for the 13.10 disk I had burned.    It ran great for 3 hours, before I performed an update.

The hardware works fine on this machine, excepting the optical drive, which is unreliable.  This machine won't boot from a USB connected drive.    So I would like, if at all possible to repair whatever happened with 13.10, rather than attempt the installation of 14.04, which may not work.   

If no one here can help me with this, I say my thanks and goodbye now.

But i

---

### Post by vasa1 on 2014-08-23
> **Engineeringtech said:**
> ...
If no one here can help me with this, I say my thanks and goodbye now.

But i

You should realise that in order to be helped over the internet, enough information has to be provided. You don't know the people here and *vice versa* and so your intentions or purpose or whatever isn't clear to the rest of us. Even the most experienced person here isn't a mind reader.

There's no point in anyone being snippy. All the best.

---

### Post by Engineeringtech on 2014-08-25
> **kansasnoob said:**
> In the upper right hand corner of the login screen there's a widget you can click to display the available sessions. Here's a [screenshot]("http://ubuntuforums.org/attachment.php?attachmentid=250351&d=1392455047"). Just make sure you select Lubuntu.

But you would be much better off installing 14.04.1 because EOL is just that - end of life!

Lubuntu is selected.

---

### Post by Engineeringtech on 2014-08-25
> **vasa1 said:**
> You should realise that in order to be helped over the internet, enough information has to be provided. You don't know the people here and *vice versa* and so your intentions or purpose or whatever isn't clear to the rest of us. Even the most experienced person here isn't a mind reader.

There's no point in anyone being snippy. All the best.

No one was being "snippy".   If you took it that way, sorry.  But it did not seem to me that anyone was offering any solution, other than to tell me to install another package.  I explained why that is not so easy.  (unreliable optical drive, no USB boot)

---

### Post by mörgæs on 2014-08-26
If your CD drive is able to read just 30 MB of a disc then you can install the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

---

### Post by Programmer135 on 2014-08-26
If you have a USB or cd/dvd I recomend a reinstall of the latest LTS version of lubuntu, you could possably enter shell and update the desktop enviroment to lets say XCFE or something similear and lightweight, but considering the technicality and time I suggest the first option, good luck :3

---

### Post by Engineeringtech on 2014-08-27
Not to sound stupid, but what is the latest LTS version of lubuntu?   How would I "enter shell and update desktop environment to XCFE"?   I've heard about alternative desktops, but don't know how to install one.

---

### Post by mörgæs on 2014-08-27
[http://en.wikipedia.org/wiki/Lubuntu#Timeline](http://en.wikipedia.org/wiki/Lubuntu#Timeline)

---

### Post by Engineeringtech on 2014-08-30
Thank you for the link.  I will update.   How do I mark this thread as solved?   I can't see any checkboxes or icons to do so.

---

### Post by Iowan on 2014-08-30
> **Engineeringtech said:**
>  How do I mark this thread as solved?  [[Solved]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

