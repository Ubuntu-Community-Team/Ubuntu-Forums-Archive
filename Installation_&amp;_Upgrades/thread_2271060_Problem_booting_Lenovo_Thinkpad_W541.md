---
title: "Problem booting Lenovo Thinkpad W541"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by manadi on 2015-03-27
Hello all,
 
I got a Thinkpad W541 and want to install Ubuntu on it. When I boot the machine using a bootable USB having Ubuntu image, I get the following error at boot time:
 
"mmc0 unknown controller version(3), You may experience problems"
 
And sure enough I do. The Ubuntu welcome screen shows up having two options, Try Ubuntu or Install Ubuntu.
From this point on, nothing works. I choose Try Ubuntu option and it just stays there forever. Actually any other click (eg. wifi configuration) also results in a hang.
 
Any pointers would be helpful.
 
Thanks.

---

### Post by aranaea on 2015-04-03
I was having the same issue.  Brand new W541, exactly the same error, and then hanging with a black screen.  While trying to find out more information I found a little dance that got me through the install.

Right when you start loading the DVD or USB stick the screen goes purple and you see a keyboard at the bottom of the screen.  Hit Escape here and you get the menu to "Try Ubuntu" etc.

Select "Install Ubuntu" and then, after you see the error about "mmc0 unknown controller" and the screen goes black hit ctrl-alt-fn-fn1 to switch to screen 1.  

You should see some messages as it loads and a couple of times it will go black on you again as it tries to switch back to screen 7 for X.  When it does this hit the ctrl-alt-fn-fn1 combo again to get back to screen 1.  

Soon you'll see a command prompt where you can do your normal command prompty things.

Now hit ctrl-alt-fn-fn7 to switch to screen 7, where X is being displayed.  

For me, I saw a mostly black screen with the installer dialog in the middle of the screen.  I was able to complete the installation normally after this.

---

### Post by manadi on 2015-04-09
Thanks for the input aranaea. It did not work for me though, each time the system hangs.

Is Ubuntu working fine with the trackpad on W541. How about display and GPU? Any problems with the drivers so far?

---

### Post by aranaea on 2015-04-13
> **manadi said:**
> Thanks for the input aranaea. It did not work for me though, each time the system hangs.

Is Ubuntu working fine with the trackpad on W541. How about display and GPU? Any problems with the drivers so far?

I'm sorry to hear that it didn't work for you.  We have 2 other devs with the same laptop who put Ubuntu on them.  One used the early 15.04 release and the other was able to follow the instructions above to get it installed.  Maybe you'll have more luck with the 15.04 pre-release.

The trackpad is working fine without any extra work and the trackpoint stick is working but the physical trackpoint buttons appear to be mapped incorrectly.  I need to do the following to get them working:

```
/sbin/modprobe -r psmouse
/sbin/modprobe psmouse proto=imps
```

The Intel GPU is working fine but only seems to support 1 external monitor through the ultradock.  I'm currently running one through thunderbolt and one through the dock.  I had to install bumblebee to get optirun to use my Nvidia GPU and I've been told that I can run my dual monitor setup through the dock with the Nvidia driver but I haven't managed to get that working yet. 

The only other additional things I've done are the bios update, which had no effect that I could detect, and the fingerprint gui.  

Overall, I'm really happy with the way the machine is working.  Previously I had a macbook with Ubuntu on it and had daily errors from crashing processes and occasional sleep/hibernate issues.  I haven't seen anything like that on this machine.

---

### Post by manadi on 2015-04-14
Lucky you.

Here is the link for bug I filed.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1437386](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1437386)

---

### Post by manadi on 2015-04-15
Can you tell me what disk model you have ?

---

### Post by tony80 on 2015-06-20
> **aranaea said:**
> I was having the same issue.  Brand new W541, exactly the same error, and then hanging with a black screen.  While trying to find out more information I found a little dance that got me through the install.

Right when you start loading the DVD or USB stick the screen goes purple and you see a keyboard at the bottom of the screen.  Hit Escape here and you get the menu to "Try Ubuntu" etc.

Select "Install Ubuntu" and then, after you see the error about "mmc0 unknown controller" and the screen goes black hit ctrl-alt-fn-fn1 to switch to screen 1.  

You should see some messages as it loads and a couple of times it will go black on you again as it tries to switch back to screen 7 for X.  When it does this hit the ctrl-alt-fn-fn1 combo again to get back to screen 1.  

Soon you'll see a command prompt where you can do your normal command prompty things.

Now hit ctrl-alt-fn-fn7 to switch to screen 7, where X is being displayed.  

For me, I saw a mostly black screen with the installer dialog in the middle of the screen.  I was able to complete the installation normally after this.

This TOTALLY worked for me. THANK YOU for posting this. Saved me LOTS of hassle.  You rock! :-D

---

### Post by iredden on 2015-06-23
I believe this is the same issue I had, but found another solution that I will share.

I have a Lenovo W541 with the K2100M NVIDIA 2GB video card.  It has 32GB of RAM and an Intel Core i7.

I used Universal USB Installed to burn the 15.04 AMD64 ISO to a Lexar 32GB key and booted by turning the machine on, hitting enter and then f12.  At the boot menu I selected my USB HDD and booted to the 15.04 boot screen.

With the first 'Try Ubuntu without installing' menu item selected, I hit TAB.  I prepended (before the ---) the command 'nomodeset'.  So it read 'quiet splash nomodeset ---'.  I hit enter and ubuntu booted successfully.

Ian.

---

### Post by lento-manickathan on 2015-08-03
I had the same issues. I followed aranaea's approch and was able to install ubuntu 14.04 with nvidia drivers. In addition I disabled the multimedia card and smard card in bios to remove the mmc0 error (not really a long term fix). 

However, multiple display did not work properly and was very buggy. 

I was finally able to fix the problem by installing Linux Mint 17.1 (17.2 does not work) with nouveau, out of the box without any modification. I haven't tried installing nvidia drivers yet.

Hopefully, this helps.
Lento

---

### Post by david-flory on 2015-08-09
I have found an official list of [Ubuntu certified hardware]("http://www.ubuntu.com/certification/").  The Lenovo ThinkPad W540 is on the list.  The W541 is NOT.  Does anyone know how or when the W541 might get added?

---

