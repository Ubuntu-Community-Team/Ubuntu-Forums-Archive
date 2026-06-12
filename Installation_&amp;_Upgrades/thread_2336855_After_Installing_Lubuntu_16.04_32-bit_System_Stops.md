---
title: "After Installing Lubuntu 16.04 32-bit System Stops on Reboot"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2016-09-12
I had a system that was running Ubuntu 12.04 and installed Lubuntu 16.04 32-bit on (erasing Ubuntu), but right after the install and rebooting, it halts with:
```
/dev/sda1 clean, 12316/12148736 files, 1558553/48580096 blocks
```
I tried Ctrl-Alt-Delete reboot as well as powering down by holding the power key and restarting, but it keeps halting with the same statement above. I checked the MD5SUM of the .ISO image, which matched, so now I don't know what else to do. It is a Pentium 4 with 1 GB RAM and 200 GB hard drive.

---

### Post by Bucky Ball on 2016-09-12
Which one do you want help with on this thread? Please create another thread for the other if you also want support with that. You will improve your chances and avoid confusion here. Thanks.

So I'll go for the first issue and machine. It is a 32bit machine? You are installing from USB or disk? How did you create the disk? What video card has that machine got in it? If Lubuntu has the option, are you ticking the boxes to enable third-party apps/drivers and update during install? If so, don't and try again.

I'm presuming you don't already have 4 partitions on that hard drive ... :-k

---

### Post by HDTimeshifter on 2016-09-12
I think it is 32-bit since I first tried using the Lubuntu 64-bit install and got an error like "Kernel requires an x86-64 CPU, but only detected an i686 CPU". So then I downloaded the 32-bit ISO and burned it to DVD. I guess I can try running the MD5SUM directly on the DVD instead of the downloaded ISO? The machine has 8MB Integrated AGP Video. I did check the boxes to enable third-party apps/drivers and update. There were 2 partitions on the drive before I erased it and created 2 again (ext4 and swap by default).

I reinstalled again (with erase disk and install Lubuntu option) and it thinks Ubuntu was still on the disk. I also unchecked the update and enable third-party apps/drivers options. This time the I/O (mouse and keyboard froze up sometime after the "restart to finish install" came up and I pressed the reboot button on the PC to reboot. The same files and blocks message came up again (with different number of files and blocks out of the totals) and a line above it also shows up:
> /dev/sda1:  recovering journal

---

### Post by HDTimeshifter on 2016-09-20
I tried installing on another machine (even older), and get the same "/dev/sda1 clean..." error message after rebooting. I let it run for a while and then it comes up with:;
```

[drm:drm_edid_block_valid drm]] *ERROR* EDID  checksum is invalid, remainder is 32
Raw EDID:
(a bunch of hex addresses)

```
Then it repeats the above lines with a different remainder value.

---

### Post by mörgæs on 2016-09-20
These problems are common to a 16.04.0-install. 
If you haven't done already I suggest that you try 16.04.1.

---

### Post by HDTimeshifter on 2016-09-21
16.04.1 worked. I'm surprised they put out a major release with such a major bug. It was out a while too - I think I downloaded and burned a second 16.04 disc a month after the first one because I thought I had a bad burn.

Thanks.

---

### Post by mörgæs on 2016-09-22
I was surprised, too, but it's due to only a few people testing Lubuntu.

Please mark the thread 'solved'.

---

### Post by HDTimeshifter on 2016-09-22
Oh, forgot to mark it solved earlier.

By the way, when I previously searched on the error, I noticed a reference to long video cables causing the problem. The 2 computers I installed this on were connected through a KVM switcher, so have longer VGA cables. The second PC I installed on is a 2.7 GHz Celeron, which technically doesn't meet the minimum Pentium 4 hardware requirement, although it does run. It's an old PC that I haven't used in a while and just wanted to reformat the drive and install a workable OS before I donate it. Also kind of surprised that the HW requirement isn't lower for a lightweight OS, although I guess there are other non-Ubuntu based Linuxes with lower requirements.

---

### Post by Bucky Ball on 2016-09-22
Lubuntu-core is lighter again. You can also go the minimal install, which is the Ubuntu kernel only, and you add only what you want/need. About as light as you can go with Ubuntu.

---

### Post by mörgæs on 2016-09-22
The hardware requirements for Lubuntu itself are low. Lubuntu installs on almost everything. 

What matters is not the operative system but the applications that one wants to run. Luckily people often post hardware requirements for (the operative systems plus a common selection of applications) in order to give people a realistic impression of the system as a whole.

---

### Post by HDTimeshifter on 2016-09-22
I wasn't aware of Lubuntu-core. I never tried Ubuntu-server because I didn't want to deal without a GUI and using command line to copy files (the oldest PC and newer/faster replacements were simply used as file [backup] servers). Ubuntu desktop 12.04 seemed to work ok on these old PCs. Core sounds like the best current release option for them, however I replaced them with an i3 a few months ago as my current file server Ubuntu 16.04 desktop and I'll be donating all the older PCs, but maybe keeping a Pentium D (and maybe also an Athlon 3800+) around as backup(s). I have enjoyed the luxury of also using it to do some browsing/e-mail and viewing some LibreOffice word processing and spreadsheet documents in the basement while working down there instead of bothering to go upstairs to a hot room to work on my main PC in the summer.

---

### Post by Bucky Ball on 2016-09-22
mini.iso is a step down from the server. You get to a section in there called 'tasksel' where you can select a machine profile. You can select 'lubuntu-core' from there. If you select no profile, yes, once install is done, you will boot to a cursor only, no desktop, but that is easily fixed. Just install one! The desktop environment used by Lubuntu is lxde, so

```
sudo apt install lxde
```

Replace lxde with xfce4 for the Xubuntu desktop environment. A bit of food for thought and the future. A mini install is a learning curve but a worthwhile one if you have the time and inclination. Have fun. Sounds like you have been. :)

---

