---
title: "Kubuntu won't install"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Corners on 2009-12-16
Hello,

Beginner here.  Trying to install Kubuntu on a machine running Windows XP (2.54 Ghz, 1 gb ram, Pentium).  I burned the ISO disk, it trys to run, but all I get is a screen that shows a blue Kubuntu "gear" icon and the Kubuntu logo, but that's it.  No desktop or anything.  The computer has been running for 40 minutes without a change in the screen.  Any ideas?

---

### Post by Corners on 2009-12-16
Ok, now I just tried to run Ubuntu live, and it froze up as well.  So, that's 2 failed attempts at Kubunto, and 1 failed attempt to install Ubuntu.

XP runs fine.

What's the deal?

---

### Post by Corners on 2009-12-16
Here's what happened when I tried to run Ubuntu "live".

[IMG]http://i45.tinypic.com/27ywcnt.jpg[/IMG]

---

### Post by presence1960 on 2009-12-16
did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it as an image to CD?

Did you burn the iso as image to CD at 4x-8x speed? Burning data at higher speeds is ok, but an image is critical- if one piece of data is missing or corrupted the whole image is no good.

If both of these check out then boot the CD and choose check disk for defects prior to trying the Live CD or installing .

If that does not work post back.

---

### Post by Corners on 2009-12-17
> **presence1960 said:**
> did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it as an image to CD?

Did you burn the iso as image to CD at 4x-8x speed? Burning data at higher speeds is ok, but an image is critical- if one piece of data is missing or corrupted the whole image is no good.

If both of these check out then boot the CD and choose check disk for defects prior to trying the Live CD or installing .

If that does not work post back.

Thanks for the reply.

No, I did not try MD5SUM.  I simply followed the instructions on the ubuntu website.  I didn't see MD5SUM mentioned.

I gave the install another shot.  I downloaded the alternate ISO file (Kubuntu), burned it at 4X, and once again, failure.  It failed on the install base file system step.  Here's a screen shot of the first error that showed up.

[IMG]http://i50.tinypic.com/11skq4m.jpg[/IMG]

A friend here at work said to try Mandriva and that the install is more user friendly.  I guess Ubuntu is not ready for the layman install just yet.  :(

Let me know if you have any other ideas.

Thanks,

---

### Post by dandnsmith on 2009-12-17
I think Ubuntu is a straightforward as WindowsXP or WindowsME - where either can fall down is if there are problems with RAM or the CD drive.
I spent some time before deciding, on an XP install, to get a new drive - instant success (but then, I had already some idea that that particular drive was suspect).

Good Luck in your endeavours

---

### Post by Corners on 2009-12-17
> **presence1960 said:**
> did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it as an image to CD?

Did you burn the iso as image to CD at 4x-8x speed? Burning data at higher speeds is ok, but an image is critical- if one piece of data is missing or corrupted the whole image is no good.

If both of these check out then boot the CD and choose check disk for defects prior to trying the Live CD or installing .

If that does not work post back.

Mandriva's website is down, so I tried the Kubuntu again.  Re-downloaded the ISO, burned at 4X.  Check the disk for errors (none), and in trying to run the CD live, it just hangs up on the Kubuntu screen.  Nothing ever loads.  I also have 2 optical drives, so I tried both and still nothing.

---

### Post by presence1960 on 2009-12-17
> **Corners said:**
> Mandriva's website is down, so I tried the Kubuntu again.  Re-downloaded the ISO, burned at 4X.  Check the disk for errors (none), and in trying to run the CD live, it just hangs up on the Kubuntu screen.  Nothing ever loads.  I also have 2 optical drives, so I tried both and still nothing.

did you MD5SUM the iso prior to burning?

Also take a look here for boot options for the Live CD: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If the F6 and F4 options do not work try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). I see you tried it earlier but you have to MD5SUM those isos before burning them. One character on the hashes could be off and that means your iso is not good.

---

### Post by Corners on 2009-12-18
> **presence1960 said:**
> did you MD5SUM the iso prior to burning?

Also take a look here for boot options for the Live CD: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If the F6 and F4 options do not work try the alternate text based installer [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"). I see you tried it earlier but you have to MD5SUM those isos before burning them. One character on the hashes could be off and that means your iso is not good.

Yep.  I ran the little MD5SUM compare, and the ISO checks out.  The disk checked out as well.  The thing just freezes up for some unknown reason.  

I also just downloaded openSUSE.  Similar deal here.  Trying to use it "live" will get a little further than Kubuntu, but still freezes before completely loading.  

Somebody/something REALLY doesn't want me messing around and learning Linux.  :(

---

### Post by presence1960 on 2009-12-18
> **Corners said:**
> Yep.  I ran the little MD5SUM compare, and the ISO checks out.  The disk checked out as well.  The thing just freezes up for some unknown reason.  

I also just downloaded openSUSE.  Similar deal here.  Trying to use it "live" will get a little further than Kubuntu, but still freezes before completely loading.  

Somebody/something REALLY doesn't want me messing around and learning Linux.  :(
OK did you go to the next step and read about boot options for the Live CD and try any of them? After you have tried them and if they still don't work you may need to try the alternate text based installer.

---

### Post by Corners on 2009-12-18
> **presence1960 said:**
> OK did you go to the next step and read about boot options for the Live CD and try any of them? After you have tried them and if they still don't work you may need to try the alternate text based installer.

I tried changing the settings.  I honestly have no idea what they do, but I tried changing them around, and the thing still freezes at the same point.  

I tried the alternate text CD again and it did not work.  It did the same thing it did in the message I posted above.

---

### Post by Corners on 2009-12-18
Update:

The 3rd time downloading, checking, and burning the Alternate Kubuntu disk worked, well, as far as installation goes.  I ran through the complete installation without a single error.  GRUB loader installed, and everything looks good.  HOWEVER, when booting up Kubuntu, the system freezes.  It never gets any further than the live CD.  I get to the page with the blue Kubuntu gear icon, with a blue progress bar at the bottom.  The progress bar gets to about 2/3rds of the way and just stops, and the computer will sit there.  I gave it 20 minutes and still nothing happened.  

Any ideas on this one?

---

### Post by darkod on 2009-12-18
Sounds like an issue with some driver/hardware. That's why the LiveCD was also stopping at similar point.
Usually I would blame the video driver but it's difficult to know remotely like this. What video card or integrated graphics do you have?
If ATI/Nvidia, there is one package that could download a new driver for you and use it. You don't need to reinstall kubuntu.
That's as much as I know.

---

### Post by darkod on 2009-12-18
In case you want to try, here's what I did with similar problem (ubuntu was restarting the PC just before showing the login screen):
From grub menu select the recovery mode entry, not the "normal" one. In the next menu select something like "root with networking" to have internet access. That should load a text based system for you.
If you get this far, install EnvyNG package with:
sudo apt-get install envyng-core envyng-qt

Run it in text mode with:
envyng -t

From the menu select your manufacturer (mine was ATI), no need to remove the current driver. It will download a driver automatically, it knows which one to get somehow. Follow the instructions and after download and install is finished it will ask to reboot.
After the reboot select the normal mode from grub menu. Hopefully it will load kubuntu OK for you.

---

### Post by Corners on 2009-12-20
SUCCESS!!  \\:D/

On the tip that maybe some piece of hardware wasn't compatible, I pulled all the unnecessary components leaving my hard drive and video card.  She boots up first try.  So, I started putting thing back, and I found the culprit; a Belkin internal wireless card.  

So, the operating system is up and running.  Now to get this sucker on the internet.  Unfortunately, the only option I have right now is WiFi.  I have a Linksys USB wireless adapter, but when I plug it in, nothing happens.  The little light flashes once or twice, and Kubuntu shows a box about a network adapter, but nothing ever happens.  No internet.  :(

---

