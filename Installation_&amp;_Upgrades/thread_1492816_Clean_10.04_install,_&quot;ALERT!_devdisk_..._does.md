---
title: "Clean 10.04 install, &quot;ALERT! /dev/disk ... does not exist.&quot; error"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by ShepHeard on 2010-05-25
Hi All,

I recently clean-installed Lucid on my Toshiba NB200 netbook as a dual boot with XP. I previously had 9.10, no problems.

However, now when I boot I get the above error and the computer drops to the BusyBox shell (initramfs). However, if I wait a while and type reboot the machine loads linux OK (albeit slowly).

Any ideas? This is driving my nuts. I've looked around the fora, but no one has really found a solution, just lots of possible causes (i.e. dodgy init .img etc) and none of them explain why sometimes I can boot OK.

Cheers,

Shep

---

### Post by michaelA1330 on 2010-05-25
try backing up all your data and then go for a fresh install ,if that dousnt help , i'll get back to you, or check if your partisoins are ****ed

---

### Post by darkod on 2010-05-25
The message doesn't sound exactly the same, but see if this will help you:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by ShepHeard on 2010-05-25
Hmmm.. interesting. I'll give that a try - it sounds like an intermittent fault too... I'm not sure, but I may be having more success booting into the old kernel (21, not 22).

I'll get back to you all


PS - I've already re-done the installation once...

---

### Post by ShepHeard on 2010-06-03
Hi again darkod,

I tried that suggestion and no joy - removing the 'search ...' line from the grub list doesn't solve the issue.

Any more ideas?

Cheers,

Shep

---

### Post by ShepHeard on 2010-06-14
Bump? No ideas at all? :(

---

### Post by ShepHeard on 2010-06-15
I downloaded a fresh copy of 10.04 LTS, reformatted my Linux partition and then installed Ubuntu again (using the LiveUSB Creator software) but I still have the same issue. 

Is this Ubuntu bug even? I can't see that it can be a problem with my hardware as I never had this problem with my previous Ubuntu install... 

If this is a bug that needs reporting, where is the problem likely to lie? grub?

---

### Post by Zatta on 2010-06-18
Hi.

I helped a friend to install 10.04 on her NB200 and this problem happened.

Here is how I resolved it:

Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Don't forget saving the changes afterwards (with F10). Done.

Zatta.

---

### Post by ShepHeard on 2010-06-20
Hi Zatta,

Thanks for this. I've actually reported it on Launchpad and as part of that installed the latest dev. version of 10.10. The problem no longer exists.. Weird eh?

I will try out your idea though as I'm not sure I want to be stuck with an early build of 10.10. 

What difference do these BIOS settings make? 

Thanks a lot!

Shep

---

### Post by dimeotane on 2010-07-01
Thanks Zatta, you're a lifesaver! This fixed the problem.



> Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Don't forget saving the changes afterwards (with F10). Done.


---

### Post by zachstauffer on 2010-07-01
Hi, I have the same problem. I'd really appreciate it if you could look at my thread. 
[http://ubuntuforums.org/showthread.php?t=1522005](http://ubuntuforums.org/showthread.php?t=1522005)
Nobody's replied to it :(

---

### Post by ShepHeard on 2010-07-06
Hi All,

It seems that for some reason, 10.04 has a problem with the AHCI driver. It is odd, because neither 9.10 nor 10.10 (at least in my case) do. Changing the BIOS settings from AHCI will overcome this problem, because then the AHCI driver is not needed. However, you then lose some of the HDD performance. Moreover, you may run into problems where you are dual-booting Windows. 

I'm not sure what the solution is, I'm still waiting for something on the bug report I submitted: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594523](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594523)
 maybe check it out...

@Zach: I'm not sure why you had problems with 9.10 - it worked fine for me... This problem only seems to be affecting a minority of people, and given that (in my case) it seems to be OK in 10.10 I can't see that they're going to rush out a fix for us... Have you tried 10.04? Or the latest alpha of 10.10?

Shep

---

### Post by jstalnak on 2010-08-30
I had this same issue after installing the 10.04 64-bit of Lucid on a Dell 9150 Dimensions desktop with 4Gb ram and an Nvidia GeForce graphics card. I did a safe-upgrade after the install that included a kernel update, followed by the required reboot, and that resulted in the same error reported in this  post. Modifying ACPI settings had no affect. I had to upgrade to 10.10 Maverick Alpha3 to restore successful boot. And lost a full day's work in the process.

---

