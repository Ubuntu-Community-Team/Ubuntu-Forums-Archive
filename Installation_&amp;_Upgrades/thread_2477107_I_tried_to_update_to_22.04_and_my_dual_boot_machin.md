---
title: "I tried to update to 22.04 and my dual boot machine gets stuck on splash screen"
date: 2022-07-14
forum: Installation &amp; Upgrades
---

### Post by mara-jade on 2022-07-14
CPU: Intel i5 2nd gen
RAM: 2x4GB
HDD: 3 x 500 GB (one drive has Windows 10, the other Kubuntu, and the last one formatted on Windows side)
GPU: AMD Cedar card
This is a Dell Optiplex 390, with an extra HDD and stick of RAM.

I can boot into Windows 10. When I try to boot into Kubuntu, I get stuck on the black screen with a logo, and loading wheel, which freezes after spinning for a bit, but I can move the mouse.

I thought it upgraded correctly, and I told it to restart as needed.

I was able to boot into Kubuntu 22.04 at least once (changed background and ran glmark2), before when I tried again the next day, it had this issue.
 I tried booting into recovery mode and can boot to there. I haven't ran any memory testing since the upgrade. It worked fine before I upgraded to 22.04.

Please help, thanks. I'm tech savvy (or at least thought I was), but IDK what to do.
I've already tried 
- power cycling (failed)
- pulling GPU, and running on integrated graphics (failed)

I need a step by step explanation on how to upgrade GPU drivers (if that's the case).
I don't know how to update the drivers in recovery mode.

I also posted it [here]("https://askubuntu.com/questions/1418625/i-tried-to-update-to-22-04-and-my-dual-boot-machine-gets-stuck-on-splash-screen?noredirect=1#comment2468050_1418625").

---

### Post by mara-jade on 2022-07-14
If I have to reinstall Kubuntu to fix it, I need tips on how to move my files to the Windows drive or the other drive.

---

### Post by mara-jade on 2022-07-14
Hey mods, if I posted this in the wrong spot, please move it. I'm new here, and wasn't sure where to post it.

---

### Post by ubfan1 on 2022-07-14
[https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)  is pretty old, you haven't had to add the graphics-drivers PPA for awhile.  Backing up to a Windows drive is likely to lose permissions when you restore, but if you make a tar file for you backup, copy the tar file to Windows, and copy back on a new install, then untar, you avoid those issues.  I think the nvidia driver install is pretty straightforward with the ubuntu-drivers script or with the "Software and Updates"/Additional Drivers program. Take the "tested" version.  If you have any leftover previous Nvidia installs, those should be cleaned out first. check the packages by:
sudo dpkg -l |fgrep -i nvidia   and purge them with sudo apt-get purge <package>  The purge is needed to remove any config files left around. 
I don't know of what issues recovery mode might have, other than maybe missing networking.  Install then reboot.

---

### Post by mara-jade on 2022-07-15
> **ubfan1 said:**
> [https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers](https://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers)  is pretty old, you haven't had to add the graphics-drivers PPA for awhile.  Backing up to a Windows drive is likely to lose permissions when you restore, but if you make a tar file for you backup, copy the tar file to Windows, and copy back on a new install, then untar, you avoid those issues.  I think the nvidia driver install is pretty straightforward with the ubuntu-drivers script or with the "Software and Updates"/Additional Drivers program. Take the "tested" version.  If you have any leftover previous Nvidia installs, those should be cleaned out first. check the packages by:
sudo dpkg -l |fgrep -i nvidia   and purge them with sudo apt-get purge <package>  The purge is needed to remove any config files left around. 
I don't know of what issues recovery mode might have, other than maybe missing networking.  Install then reboot.

Sorry, I had an **AMD** GPU (before I pulled it to clean it, and to test integrated graphics, which *still* made it freeze).

How do I backup when I 
- can't just open the drive in File Explorer on Windows 10
- can't get into normal Ubuntu (at best, recovery mode), because I want to backup my files

Is AMD Cedar a rebranded Nvidia chip?

---

### Post by ubfan1 on 2022-07-15
I guess I thought ubuntu-drivers and Software and Updates/Additional Drivers would be driver agnostic, but I could be wrong, never had an AMD GPU. (But did have an AMD cpu with an N 130? GPU which turned out to be a peripherial controller including an Nvidia  Geforce 6150.  Anyway, from recovery mode, you should be able to mount a Windows drive and backup, the main thing recovery mode does is boot with a kernel param (nomodeset) to use the default video.  So, sudo mount -tntfs /dev/sdxy /mnt  (or make a dir under /mnt and mount there if other things are already mounting in /mnt/xx), and you should be able to write to the windows drive.  I seldom do that, and can't say how likely a failure of some sort would be, but one tar file is more likely to succeed than a whole directory tree.

---

### Post by oldfred on 2022-07-15
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Report may not show much, as if you can boot recovery mode, then it really is not a boot issue.
But it may be some setting or configuration that report could show.

Are both installs UEFI? Or both BIOS? Report will show that.

I do not know AMD video, but most of the posts I have seen, say it just works with the default driver that installer provides. There is an advanced driver that will better support very new AMD video cards/chips.
And Intel video should just work.

---

### Post by mara-jade on 2022-07-15
I haven't tried it because I thought it was for Nvidia only.

Also, can you give me step by step instructions, because I'm newer to Linux than Windows, and not great with the command line.

---

### Post by mara-jade on 2022-07-15
My GPU is an older AMD gpu, and that's before I pulled it to try integrated graphics (as well as clean the dust out and change thermal paste). It worked fine prior to update, and for the one time  that I got it to work. I may have had to upgrade packages after upgrade (I know it took me a couple of tries pre-upgrade), but I don't remember for sure.

I remember setting the thing up in Legacy Mode in BIOS to make it work. I'm getting ~ 8-something KB to 1.2 MB a second, and 13 min left on the download.

---

### Post by mara-jade on 2022-07-15
I was downloading it onto a USB to make a live USB. 
What do you mean not Boot-Repair ISO?

---

### Post by oldfred on 2022-07-15
Boot-Repair has a downloadable version that is also a live system based on Lubuntu. But ISO is not updated as frequently as the ppa.
So best to just use your Ubuntu live installer in live mode and use ppa to add Boot-Repair. Details are in link to Boot-Repair above.

---

### Post by mara-jade on 2022-07-15
So try doing the console commands using root prompt in recovery mode?

---

### Post by oldfred on 2022-07-15
If you are at recovery mode, you cannot run Boot-Repair as it needs a gui.
But then you are booting, so issue is something after boot, anyway.

You then need to try repairs from command line, the recovery mode has several options.

---

### Post by mara-jade on 2022-07-16
I need step by step what code to try in the command line. I can't get to my desktop, but when I mess with BIOS (I swapped things to now make Windows 10 the default because it works right now), I should be able to get into recovery mode. Maybe something about nomodeset (I've heard about it from other spots)? 

There are four options in advanced options. What do each of them do? Which recovery mode do I need? 

Ubuntu something.something
Ubuntu something.something (recovery mode)
Ubuntu something else.something else
Ubuntu something else.something else (recovery mode)

---

### Post by mara-jade on 2022-07-16
I downloaded the boot repair iso, when I was confused, and was about to make it into a bootable USB. Would it be worth a try to try the bootable USB, even though it's older?

---

### Post by oldfred on 2022-07-16
I would use your Ubuntu live installer and use the ppa to add Boot-Repair to live installer.

If you boot the first recovery mode, do you get a text like menu of options?
Then you may be able to boot, repair or do updates or install fixes from terminal. But not sure what you need.

---

### Post by mara-jade on 2022-07-16
I don't have the bootable USB I put kubuntu on to install it on when I installed it. So can I just make another?

I got a text like menu, last time I tried getting into recovery mode.

---

### Post by SeijiSensei on 2022-07-16
You can boot from the Kubuntu USB and choose "Try Ubuntu". You can then open a terminal and mount your other drives and copy files between them. Open a terminal, then run "[FONT=System]sudo fdisk -l[/FONT]" to see a list of devices. There should be a /dev/sda, /dev/sdb, and /dev/sdc corresponding to your three drives. The /mnt and /opt directories are empty by default on Ubuntu. Mount the partition you want to copy from to one of these, and the destination partition to the other. Something like:
```

sudo mount /dev/sdb1 /mnt
sudo mount /dev/sdc1 /opt
ls /mnt
ls /opt

```
If the destination drive is not formatted with ext4 or another Linux-compatible filesystem, I strongly recommend following the suggestion above to put the files you want to save into a tar archive, then copy the archive to the other drive. You will be able to preserve permissions and the like this way.

---

### Post by mara-jade on 2022-07-16
So, I need to
1. make a new Kubuntu USB
2. Try Ubuntu
3. [COLOR=#000000][FONT=System]sudo fdisk -l
4. Somehow put the files in a tar [/FONT][/COLOR][FONT=System][COLOR=#000000]archive (IDK how to do that)
5. Move them to drive (do I need to make that drive unallocated in Windows?)
At **best**, if everything goes well, I might be able to get to 3. The closest thing I remember to moving files is the cd (change directory) command. I want to just copy my whole set of user files, programs included.

I'm used to the GUI, not the command line. I use the command line mainly for installing stuff, and upgrading stuff.[/COLOR][/FONT]

---

### Post by SeijiSensei on 2022-07-20
You might be able to mount the drives from Dolphin. Boot from the USB stick, choose "Try Ubuntu", then open Dolphin. See if it shows your hard drives under Devices. 

If you just want to move your home directory, see if you can navigate to /home on the source device. Then right-click on your directory and choose Compress. Choose tar.gz. Create the archive, then move it to /home on the new device. Click on the archive and decompress it with Ark.

---

### Post by mara-jade on 2022-07-20
> **SeijiSensei said:**
> You might be able to mount the drives from Dolphin. Boot from the USB stick, choose "Try Ubuntu", then open Dolphin. See if it shows your hard drives under Devices. 

If you just want to move your home directory, see if you can navigate to /home on the source device. Then right-click on your directory and choose Compress. Choose tar.gz. Create the archive, then move it to /home on the new device. Click on the archive and decompress it with Ark.
I'll try that, when I next have time. 
When I make my USB stick, can I just use whatever standard Ubuntu desktop? Should I stick to Kubuntu (or use Cinnamon, which I've been using on another device)? Should I try a different distro (note: I've only worked with Ubuntu based distros)?

---

### Post by oldfred on 2022-07-20
Boot-Repair has a ppa to install the most current version into your Linux live installer.
It also builds a live ISO based on Lubuntu, but that is not updated quite as often.
Best to always have live installer for all current versions of systems installed. 
And good backups.

---

### Post by mara-jade on 2023-03-20
Update: Ended up fixing by taking files off and reinstalling Kubuntu. It works fine now. Thanks.

---

