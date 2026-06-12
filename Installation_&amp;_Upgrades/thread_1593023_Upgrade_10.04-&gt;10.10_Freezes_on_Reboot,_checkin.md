---
title: "Upgrade 10.04-&gt;10.10 Freezes on Reboot, checking non-existent battery"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Ubangi on 2010-10-11
I did normal net upgrade after the official release of 10.10 yesterday evening. On reboot I get a frozen system with a blank screen. 
Checking via safemode, I find it is stuck when 'checking battery state' but this is a desktop machine!

Following various hints* on this forum did not help.

* apt update, uninstalling ubuntu-desktop, reinstalling ubuntu-desktop, etc.

---

### Post by adrianrdzv on 2010-10-11
Exactly the same problem over here... :(

---

### Post by Ubangi on 2010-10-11
Anyone has any ideas then? I imagine there are lots of silently suffering people out there who don't necessarily have another computer to even be able to report it here.

---

### Post by gwiltgen on 2010-10-11
Exactly the same problem over here... also :?

---

### Post by Ubangi on 2010-10-11
I am desperately searching forums and bug reports. I see this reported as long as five years ago but no solutions :(

---

### Post by smattos on 2010-10-11
Quick question:  How do you boot in SAFE MODE?  I do not know the key presses required during Ubuntu boot up to force SAFE MODE.  I'm having difficulty after upgrading from 10.04 to 10.10 on my Acer Aspire One netbook.

Thanks for any help provided.

---

### Post by smattos on 2010-10-11
Never mind, after some digging I found out that all I have to do is hold the ***[FONT="Times New Roman"][COLOR="Red"]Shift[/COLOR] [/FONT]***key during boot up.

---

### Post by Ubangi on 2010-10-12
or select a recovery mode, which is normally the second line in your boot options

---

### Post by Revjohn on 2010-10-17
Same problem here.

---

### Post by PollekePol on 2010-10-18
Same problem here. Updated my HP laptop from 10.04 LTS -> 10.10 yesterday. When booting I just see this black screen with a blinking cursor in the top left. When doing CTRL+ALT+F7 I see it hangs at the message 'Checking Battery Status'. Of course (?!) this has nothing to do with the fact whether your system has a battery. Guess it's because it f*d up the configuration for the graphics card, is not able to start X anymore? My laptop has an onboard Intel card. I see many threads with the same issue. But nowhere a solution yet.

---

### Post by PollekePol on 2010-10-25
> **PollekePol said:**
> Same problem here. Updated my HP laptop from 10.04 LTS -> 10.10 yesterday. When booting I just see this black screen with a blinking cursor in the top left. When doing CTRL+ALT+F7 I see it hangs at the message 'Checking Battery Status'. Of course (?!) this has nothing to do with the fact whether your system has a battery. Guess it's because it f*d up the configuration for the graphics card, is not able to start X anymore? My laptop has an onboard Intel card. I see many threads with the same issue. But nowhere a solution yet.
 
F* it, I have moved to Linux Mint.

---

### Post by TheKiteGuy on 2010-10-27
I had the same problem. I was initially prevented from doing the upgrade due to some conflict, so I uninstalled the conflicting package (xorg-something?). After rebooting after the subsequently completing the distribution upgrade, for every following reboot, PC got as far as the Checking battery and would stay there doing nothing indefinitely. 

I fixed it by pressing CTRL+ALT+F1, logging in at the console and then 
sudo apt-get install gdm. This found the missing packages needed to get X to start. After rebooting, PC functioned correctly once more!

---

### Post by mit_brooks on 2010-11-11
I had the same problem - Turned out that my root file system was full and needed cleaning out. All good now.

---

