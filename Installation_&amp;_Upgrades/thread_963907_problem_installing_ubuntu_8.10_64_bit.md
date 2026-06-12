---
title: "problem installing ubuntu 8.10 64 bit"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mannaa on 2008-10-30
Hi all!
I have downloaded the latest ubuntu, 8.10 64 bit. Burnt it to a disc and restarted my cpu. The disc boots correctly, but when I choose the install option the cpu reboots and returns to the main meny. The same thing happens when I try to start ubuntu without installing it. I have tried o burn a second disc, but the same problem accurs. What's the problem? What can I do?

Thankfull for all the help I can get

---

### Post by Jagot on 2008-10-30
Same thing happening to me and I have no solution yet.

---

### Post by rockstar82 on 2008-10-30
I got your PM mannaa, i answer here instead.

I got this exact problem, and im not 100% sure what did solve the problem.

I am using an Asus P5B-VM motherboead, and these are the settings that worked for me.

* In bios i enabled the option "Bios EHCI Hand off". It was found under USB-settings.

* I changed JMicron SATA Controller Mode to [RAID], even though I dont use it.

* I played around with the advanced CPU-settings. I ended up enabling all settings. C1E Support, Max CPUID Value Limit, CPU TM function, Execute Disable Bit and so on. Some people are doing the opposite.

Hope this makes any sense. Also try install from USB, and also 32 bits version.

---

### Post by jimv on 2008-10-30
If you don't need support for 4 gigs of RAM, see if you can load up with the 32bit version.

---

### Post by mannaa on 2008-10-30
Thanks for the answer rockstar. 
Unfortunetly I couldnt find any EHCI option in my bios.

The problem remains, hope some one else got any tips.

I have 4 gb of ram installed, so I would very much like to use it

---

### Post by rockstar82 on 2008-10-31
I kept getting Kernel Panic-issues when booting, and I have now found what was causing my problems.

I flashed to the latest Bios, and it now works like a charm. Apparently a known Memory Remap-issue stopped me from using 64 bits.

---

### Post by mannaa on 2008-11-01
I have read something about pressing F6 and changing whatevers in there to something else. I am all new to ubuntu, so does anyone have a clue?

---

### Post by Jagot on 2008-11-01
Some people have managed to get it working by removing quiet and splash from the boot options, which is what you are referring to, though it hasn't worked for me.

---

### Post by mannaa on 2008-11-02
I tried removing quite & splash, but it didnt help. It started loading, ran through some text real fast and suddenly rebooted the whole system. =( But thx anyway

8.10 has been out for a while now, is there really no one that have come up with a solution yet?

---

### Post by tuxxy on 2008-11-02
I ad no issues installing fresh 8.10 it has to be something to do with BIOS or hardware

---

### Post by sirius11 on 2008-11-02
That is really not surprising to see ubuntu not wanting to install on a normal AMD system. Even when previous version of ubuntu can be installed but suddenly for no good reason, it wont install the 8.10 version.

So  anyway,   Ubuntu wont even load the live cd on a AMD 5400+ on a asus  590 chipse mobo , nothing weird or fancy,with an nvidia 8800gts card.

When I try the live cd, I Only get a bunch of white lines saying that there are error on buffer i/o something.Lines after lines.


EDIT :  I finally got it to work by burning another dvd..   first one was a bad burn.   Sorry for bitching for no reasons.

---

### Post by mannaa on 2008-11-02
I am currently running vista 64 bit, but would really want to switch over to ubuntu. I have a FSC amilo 3540, 320 gb, geforce 9300m, intel P8400, 4 gb ram etc. The hardware should be compatible. Unforunatley my BIOS options are very restricted, I am hardley able to configure anything from inside the BIOS. Is there a way to "make/force" the BIOS to show all config settings, or possibly changing the settings from inside the current OS?

Any tip would be great

---

### Post by mannaa on 2008-11-02
Sirrius11: I had ubuntu 8.04 32 bit running on my old laptop, it worked pretty well, some minor configs and I was set. Now that I have a 64 bit compatible cpu I would like to run a 64 bit OS and are running in to some problems, so what?! Ubuntu is for free, and includes a lot of support and software. And u have the nervs to squeak about it?

---

### Post by sirius11 on 2008-11-02
yes manna,  I was upset to loose so much time and effort..   I got it to work now

---

### Post by jimv on 2008-11-04
Try the Alternate CD.  Sometimes it works when the regular installer does not.

[http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-amd64.iso](http://ubuntu.osuosl.org/releases/8.10/ubuntu-8.10-alternate-amd64.iso)

(Download is from Oregon State University)

---

### Post by mannaa on 2008-11-04
Thanks jimv for all your posts. Unfortunately the alternate installer didnt work, either. I get the same "message" for both installer, just seconds before the whole system reboots. Something like this: "unsupported PM cap reg 7". Dont know what it means, maybe it has something to do with it. Any clues?

---

### Post by mannaa on 2008-11-09
bump..

To my suprise the issue remains, even though there are some ppl having this problem. 

Have anyone got a clue? 

I have tried using the alternate CD, and I have tried kubuntu aswell. I still get the same problem. The computer is currently running vista 64 bit and the ubuntu live CD autoruns in windows and boots. But it wont install...I am kind of getting desperate here

---

### Post by unknown user on 2008-11-29
I too am having a problem with the install of 8.10, but I have opened this thread as not to hijack this one as was pointed out ([http://ubuntuforums.org/showthread.php?t=998175](http://ubuntuforums.org/showthread.php?t=998175))

---

### Post by mannaa on 2008-12-11
Ok, the problem is finally solved =)

A member here at the forum helped me out, thank u very much JagerQ!!

This is what he told me:  I had a similar problem with the PM45 chipset and 4GB Ram. Adding a mem=4096m flag on boot got me past the splash screen.

his solved it for me, got pastthe installation and then in the grub I entered mem=4096m once again in order for it to boot. 

Once again thank u JagerQ

---

### Post by sirius11 on 2009-01-27
follow up :

I was able to install Ubuntu 64 by burning another dvd. the first DVD must of had a problem.  So I've been upset for no reasons, it was just a bad iso burn..

everything is working fine with my amd 5,400+  with nvidia 8800gts

---

