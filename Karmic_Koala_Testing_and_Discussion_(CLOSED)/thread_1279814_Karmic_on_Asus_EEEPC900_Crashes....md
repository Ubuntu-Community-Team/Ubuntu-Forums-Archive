---
title: "Karmic on Asus EEEPC900 Crashes..."
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kingster on 2009-10-01
And I mean it crashes doing ANYTHING.

This is on an Asus EEE PC 900/XP with 1GB RAM, and 16GB SSD (all one partition space, not the 4/12 split).

Now, I know Karmic is alpha, and I'm not upset that it's crashing, I'm just trying to fix whatever is causing the issue.  

My first stab (after the default install) was to update it...  Update manager crashed continuously, even just loading files from the repositories.  Then I tried from the command line: "sudo apt-get dist-upgrade".  Crashed several times, before retrieving all the files, however, it finally did, and started the upgrade.  Then Terminal crashed.  /usr/bin/dpkg is still running in the background, and doing things, which I can watch with occasional ps -ef's and the HD LED, but, that's just not how it's supposed to go.

Heck, I'd even submit crash reports, but those crash too.

I'm just curious if others out there are having the same issue, have seen this, fixed it, etc.  I've used EasyPeasy and a couple other distros on this thing (it's a play netbook, nothing important on it).

---

### Post by Kingster on 2009-10-02
No one else is experiencing this??  [sigh]

I was hoping that I wouldn't be the only one.

Further testing...


[LIST]
[*]I get this on the LiveCD (really more like a LiveUSB).  I've used unetbootin to build the USB drive several times, including with the most recent release (Beta).
[*]Every app crashes.  From Netbook Launcher, to Firefox, to Terminal, and even occasionally, the installer.
[*]I can't submit a bug, as the terminal crashes, or Firefox crashes when logging into Launchpad.
[/LIST]
When looking through the bug reports (before they crash), I see SIGSEGV when trying to access 0x00000000...  In every instance.  Does this help anyone?

---

### Post by barrieluv on 2009-10-02
> **Kingster said:**
> No one else is experiencing this??  [sigh]

I was hoping that I wouldn't be the only one.

I installed Alpha 6 to SDHC when it arrived (I boot Mint from the internal 4GB) and have applied every update.  
Apart from the lengthy boot time (this should get better), everything works and I've not had a single crash.  Not one.
All of my updates have been administered through Synaptic.

---

### Post by Pat L.I. on 2009-10-02
Strange, It works fantastic on my 900 (regular 900 Not 900a)

are you using a recent iso?

is there a recovery kernel listed in grub? try booting into that and then doing the upgrade.

---

### Post by Kingster on 2009-10-02
> **barrieluv said:**
> I installed Alpha 6 to SDHC when it arrived (I boot Mint from the internal 4GB) and have applied every update.  
Apart from the lengthy boot time (this should get better), everything works and I've not had a single crash.  Not one.
All of my updates have been administered through Synaptic.
Well, one thing that's different between you and I is that I had an older BIOS.  I'm in the process of flashing to 1006.  We'll see if that makes a difference.

> **Pat L.I. said:**
> Strange, It works fantastic on my 900 (regular 900 Not 900a)

are you using a recent iso?

is there a recovery kernel listed in grub? try booting into that and then doing the upgrade.
I am using a recent ISO - the beta I downloaded just last night.  I'm trying simply to boot cleanly into the LiveCD - I have instability the minute I get there.  Apps crash left and right.

I did just get this thing back from Asus - the SSD died in it (days before the warranty was up, how often does THAT happen??).  Prior to that SSD death, I had EasyPeasy working just fine, but wanted to get the latest and greatest.  May have to roll back to it, I find I like a lot of things in Karmic better though...

I'll report back shortly.

---

### Post by Kingster on 2009-10-02
Well, this sucks.

Updated the BIOS, and still get the same issue.  Things just die after any random amount of time, just in the "LiveCD" screens, or just running the install from the "CD" (really the USB drive).  I think I'll try, just for grins, the Alternate Install CD.

Just as an FYI, they all crash with sigsegv's.  I just had a full blown X crash with sigsegv.  Also, running MemTest86, memory shows hunky dory...

wonder what the heck is going on here...  [sigh]

I did have Easy Peasy working, I'll try that one next.

---

### Post by Kingster on 2009-10-02
Must be something with the hardware.

Easy Peasy does it as well.  [sigh]

Grand.  Another 2 week wait for it to come back.  I bought two of these things - one for me, one for the wife.  Hers runs like a dream.  Mine is borked.  Time to hijack hers.

---

### Post by Kingster on 2009-10-02
Testing further now - I popped open the panel to the SSD and memory, and then reseated them both...  Things are more stable it appears.  I'll give it another go now, and report back.  If this is what it was, I'm gonna be ticked.

[sigh]

[edit] Then again, I may have spoken too soon. [/edit]

[edit 2] Yup.  Spoke too soon. RMA'd.  Again.  What fun!  [/edit 2]

---

### Post by Sven6210 on 2009-10-15
Ubuntu Netbook Remix 9.10 Beta works extremely stable on my EeePC 900a, in the base version and also with all the latest updates.

---

