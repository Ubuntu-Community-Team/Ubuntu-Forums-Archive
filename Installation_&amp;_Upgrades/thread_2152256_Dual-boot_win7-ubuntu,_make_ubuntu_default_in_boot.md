---
title: "Dual-boot win7-ubuntu, make ubuntu default in boot"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by celiae on 2013-06-07
Hi,

I'm new to Ubuntu (and everything Linuxy) but desided to give it a try. I didn't want to lose Windows completely incase I'd run into problems so I installed Ubuntu 12.04 lts alongside using the CD. Everything is working as it should and I can boot into both systems without problems. The only thing I'd like to change is the boot order, right now it boots Windows by default and I want it to boot Ubuntu. (I want to be able to leave the pc during startup). Been searching high and low but 9/10 is how to make Windows default (with the last one usually being unsolved, dead threads), but I figured I could use the same solutions. 

So I have tried:

*Grub Customizer, Windows 7 doesn't show in the list.

*Changing GRUB_DEFAULT from 0 to 1. In the solutions I found, making Win default, Win was last in boot list. When I start up my PC I only have Win7, listed first, and Ubuntu, listed second. So thought I could change default from 0 to 1 but ended up with alot of text scrolling on startup, repair choices and changed graphics. So I changed the grub file back and everything is now back to normal.


These two methods are the only ones I've found and none of them are working. :( Would really appreciate every little piece of advise, no matter how small.

/Celiae


**UPDATE:**

**oldfred**, so very true. lol Logged into windows and had a look around and found Ubuntu. Reinstalled after finally getting my pc to boot from usb. Did the trick (mental note: start reading manuals).

Thank you for your help!!! :)

---

### Post by fantab on 2013-06-07
When GRUB is installed during Ubuntu Installation it ALWAYS makes Ubuntu as default OS. Are you sure you are using GRUB?

Boot Ubuntu and from Terminal post the output of:

```
sudo update-grub
```

---

### Post by oldfred on 2013-06-07
As fantab says Ubuntu will be default.

Is this a wubi install? Then you are booting with the Windows boot loader. If Windows Vista or 7 you can use Windows bcdEdit to modify boot or if XP any Windows editor to edit boot.ini (If Linux editor be sure to save with Windows line endings).
       [URL="http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html"]http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html
[/URL]
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you like Ubuntu, it may be time to convert to a full install.

 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

 
    [URL="http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html"]
[/URL]

---

