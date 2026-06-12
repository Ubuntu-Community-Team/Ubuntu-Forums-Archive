---
title: "Using Wubi from Windows 8?"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by HP dv4 on 2011-09-22
I have a macbook pro 2011 that I would like to triple boot Windows, OS X, and Ubuntu on. I really care very little about the Windows 8 installation currently on my Mac. I thought that after having a boot camped Windows installation I could run Wubi and have my triple boot-ish Ubuntu. I ran Wubi, rebooted, and the new Windows 8 boot menu came up, but the only choice was Windows 8. It obviously did something because the boot manu is prompting me, but where is my Ubuntu? Can someone tell me what's going on here? 
If this isn't fixable, can someone tell me how to use my current Windows partition for Ubuntu. REFIT does not work.
Thank You

---

### Post by Frogs Hair on 2011-09-22
I can only offer that current versions of Wubi may not be compatible with Win 8 . As far as I know only the developer preview of Win 8 has been released .

---

### Post by Hungry Man on 2011-10-05
I am using Windows 8 right now and would like to dual boot using Wubi.

It doesn't seem to work properly.

---

### Post by Mark Phelps on 2011-10-06
I would be surprised if it DID work! 

After all, Windows 8 has not even made it into Beta testing, yet.  The current version is essentially an Alpha version.

Once Windows 8 gets actually released, I would expect Wubi compatibility to follow soon after -- not before.

---

### Post by dekinstoke on 2011-11-22
Ok .... I had the same issue installing Ubuntu 11.10 using Wubi on Windows 8 Developer. The only system in the boot menu was Windows 8 after installing.

Seem to have fixed this by going into the Advanced Setting in System in Control Panel on Windows 8, and selecting Ubuntu as the default operating system. Next boot I had both Windows 8 and Ubuntu in the boot menu.

---

### Post by Mark Phelps on 2011-11-23
If anyone reading this is using Win8 and has questions, the best place to go is to the Windows 8 forums: eightforums.com

---

### Post by Viral_Weaponry on 2012-06-18
here is your answer guys.

[http://google-ite101.blogspot.com/2011/10/windows-8-linux-dual-bootwubi.html](http://google-ite101.blogspot.com/2011/10/windows-8-linux-dual-bootwubi.html)

---

### Post by Scoobford on 2012-07-01
yep thats how I got it to work!
my blog BTW thanks alot for the pageviews! :D

---

### Post by freechelmi on 2012-08-06
Hi, Did anybody reproduce this bug ? 


[https://bugs.launchpad.net/wubi/+bug/1033434](https://bugs.launchpad.net/wubi/+bug/1033434)

---

### Post by nitrofurano on 2012-10-19
> **Hungry Man said:**
> I am using Windows 8 right now and would like to dual boot using Wubi.

It doesn't seem to work properly.

you mean that we can delete all files from the host htfs partition from wubi, even from inside windows folder, all of them? this is really awesome! \o/

---

