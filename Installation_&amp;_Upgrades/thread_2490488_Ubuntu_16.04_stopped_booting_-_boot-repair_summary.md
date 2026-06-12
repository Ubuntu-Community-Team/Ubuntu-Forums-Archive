---
title: "Ubuntu 16.04 stopped booting - boot-repair summary"
date: 2023-09-05
forum: Installation &amp; Upgrades
---

### Post by samuelgardner on 2023-09-05
Hi,

This is my first post on the Ubuntu forums so I hope I'm posting this in the correct one. I've run a boot repair summary and the diagnostic report url is:
[https://pastebin.ubuntu.com/p/WZ6KtMThb3/](https://pastebin.ubuntu.com/p/WZ6KtMThb3/)

Every time I boot my PC now it goes to the grub rescue prompt. I ran 'ls' on the various partitions but I just get "Filesystem is unknown" so I've run the boot repair summary. Please can you advise if I should go ahead and perform the repair?

I've always had an issue with booting Ubuntu. Most times when I powered on it would boot to the grub rescue prompt initially. So I would power off and then immediately power on and it would boot to the OS menu. However, the other day it started behaving a lot worse and I would get the grub rescue most of the time. One time (I may have had a usb installer plugged in - I can't rememeber) I was prompted to run fsck to repair one of the partitions (I can't remember which one) so I ran the repair and since then I always get the grub rescue prompt. I've tried Ubuntu from a usb installer and my data is still accessible so I've backed-up most of it. 

FYI: My PC is dual boot. It has a Windows OS and Ubuntu 16.04

Kind Regards,

Sam.

---

### Post by ajgreeny on 2023-09-05
Well, according to your boot-repair output you have only Windows installed.

There is no mention there of any Linux OS installed so give us a lot more detail of what you may have done and when this problem occurred first.

---

### Post by samuelgardner on 2023-09-05
Looking at the report I had a feeling Windows was the only available OS on sda. It looks like Ubuntu was on sdb and this is now corrupted. I really don't know what happened. I switched off my desktop at the mains before I went on holiday. When I got back it just kept booting to grub rescue. It looked like the disk was corrupted. The next day it booted to Ubuntu so I thought maybe it was just a glitch. Then in the evening I was browsing the internet and Ubuntu crashed so I powered off. Then I think I may have plugged in a Ubuntu usb installer because I got an option to check the disk which I ran and it reported there were errors. I then ran fsck to repair it and fixed the errors. I think the partition was /dev/sdb5 (Could be wrong). Since then it always boots to grub rescue. With hindsight I think it was a mistake to repair using fsck.

Sounds like boot repair will fix it so it only boots to Windows. Is that correct? I've got a Ubuntu 16.04 installer usb. Is my best bet to re-install Ubuntu? I was hoping to recover the installed Ubuntu, but I've backed up most of my data so I could just re-install Ubuntu if that looks like its my only option. What do you suggest?

---

### Post by guiverc on 2023-09-05
Ubuntu 16.04 LTS was released in 2016-April (*why it's 16.04*) with 5 years of *standard support*, which ended in **April 2021**.

I'd not recommend using 16.04 unless you use your system **off-line**, or you're using **ESM** or **Ubuntu Pro**, as you won't have received security fixes since April 2021 when standard support ended.

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

You didn't say what type of system it is, esp. if Desktop or Server.

If it was me and you were using a Desktop system, what I'd do is the following

- perform SMART checks on your drive health (*I do that on any unexpected disk or system issue, usually also RAM tests & some other standard machine checks*). [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

- check drive partition table for issues (*what's on it I don't know as you've given few details as to system (Server/Desktop), file-systems involved, or your hardware, only mention of sdb5*).

- IF a Desktop system, I'd perform a *non-destructive re-install *of a later Desktop system, to achieve bringing it up to date and back into the *secured* world of using a *fully supported* system.



---

[B]Non-destructive re-install

[/B]I do this type of install somewhat often (*mostly with flavors though*), but I'm always usually aware of what packages I have on my systems, and have  few 3rd party which can be problematic here & require some manual fixes (*meaning I just re-install those 3rd party packages**, for some I remove them before re-install & install back after re-install*). I've written about this type of install here ([https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533))

Earlier this year I finally upgraded a 16.04 Desktop system of my own (*16.04 thus using Unity 7 Desktop*), my  delay was because I didn't want it to be GNOME (*17.10 & later Ubuntu Desktop use GNOME*) & thus had to choose a *flavor* I was going to re-install with, being stuck on that decision for  near two years... In the end I performed *release-upgrade* only because a number of users were reporting they were unable to *release-upgrade* 16.04, so I did it that way (*2x upgrades; 16.04->18.04, 18.04->20.04*) & reported the upgrade path was still possible online.. instead of my intended re-install of the system.  I'll *non-destructively re-install *a 22.04 *flavor* anyway once I decide which I'll be happiest with anyway (GNOME doesn't suit how I use that box).

FYI:  The *release-upgrade* (16.04 to 18.04, then again 18.04 to 20.04) took the machine MANY HOURS (x2) with it happening over night. In contrast a the non-destructive re-install would have taken me less than 30 minutes  (*and I'd have gone straight to 22.04 like my next re-install will; once I decide what I'll install!*)

---

### Post by oldfred on 2023-09-05
It also looks like you have Windows 7 in the old BIOS/MBR boot mode.
The end of the Windows 7 lifecycle is set for 14 January 2020, Windows 7 will reach its natural End of Life (EoL). "End of life" means Microsoft will discontinue all support, including paid support; and all updates, including security updates.
Even Windows 8 is EoL. Microsoft required vendors to install Windows 8 in UEFI/gpt mode in 2012. So most hardware is now UEFI based.
Windows 8 reached end of life in January 2023

You seem to have newer hardware as the Boot-Repair report says you booted in UEFI boot mode.
How you boot install or repair media UEFI or BIOS is then how it installs or repairs. You must always be consistent.

If you convert to UEFI, Windows has to have gpt partitioning. The conversion from MBR(msdos) to gpt will totally erase drive, so be sure to have good backups.

---

