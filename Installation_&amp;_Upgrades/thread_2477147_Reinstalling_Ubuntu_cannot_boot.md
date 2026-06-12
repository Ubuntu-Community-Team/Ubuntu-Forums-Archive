---
title: "Reinstalling Ubuntu cannot boot"
date: 2022-07-15
forum: Installation &amp; Upgrades
---

### Post by eippoliti on 2022-07-15
Dear Ubuntu users, I have a workstation where I installed Ubuntu 18.04 LTS some years ago. A couple of weeks ago, the system got unresponsive and after rebooting I landed to the Grub command line. Therefore, I backed up the relevant data and I reinstalled the OS from scratch erasing the disk. Since the disk is really a RAID volume, I even deleted and rebuilt the RAID volume. Then, I proceeded as usual by booting from a live-USB stick in UEFI mode (by selecting Minimal installation, Update during the installation and Install third party software). The installation seemed to complete normally but after rebooting the system landed again into the Grub command. Then, I tried to install Ubuntu 16.04 LTS and later Ubuntu 20.04 LTS with the same result. 
Going through the forum I found this procedure to try to fix the boot problem: 

[https://askubuntu.com/questions/883992/stuck-at-grub-command-line](https://askubuntu.com/questions/883992/stuck-at-grub-command-line) 

but it does not work for me because when I try to read inside the folders of disk (hd0,2), which in my case is the main partition where boot/ root/ ... are, for example with the command:

[FONT=courier new]ls (hd0,2)/boot[/FONT]

I got the message: 

[FONT=courier new]error: Attempt to read or write outside of disk `hd0'[/FONT]

Then, after reinstalling Ubuntu 18.04 LTS, I attempted the Boot-Repair procedure.
At this link you can find the Boot-Info summary before attempting the repair:

[https://pastebin.ubuntu.com/p/6rxfv62xcg/](https://pastebin.ubuntu.com/p/6rxfv62xcg/)

and here the one after running the Boot-Repair with default parameters:

[https://pastebin.ubuntu.com/p/tF2csZQNhy/](https://pastebin.ubuntu.com/p/tF2csZQNhy/)

I checked also the sanity of the disks but both the RAID controller and the check performed with the Ubuntu USB live stick did not find any problem there. I really do not understand why now the Ubuntu installers cannot correctly install the boot loader on this machine. Do you have any idea or something to propose in order to find where is the problem?

All the best,
Emiliano

P.S. Setting in the BIOS that might be relevant: only UEFI mode is enable, Secure boot is disabled.

---

### Post by oldfred on 2022-07-15
You have a large / (root) partition that is most of your 5.5TB drive.
Most suggest smaller / partition and larger /home and/or data partitions.

At one time grub had an issue booting beyond 600MB when drives when over 1 or 2TB. I know they fixed that, but not sure if / only on that large of a drive is an issue.

Also 16.04 is EoL, so any tests with that would not work.

I might reinstall with smaller / partition.
Do not know RAID, is this FakeRAID, or BIOS based? 
Most with Linux seem to suggest using mdadm, but I have never used RAID nor know any details.

---

### Post by eippoliti on 2022-07-19
> **oldfred said:**
> You have a large / (root) partition that is most of your 5.5TB drive.

Yes. I installed Ubuntu leaving the installer decide the partitioning (default behaviour)

> **oldfred said:**
> Most suggest smaller / partition and larger /home and/or data partitions. 
At one time grub had an issue booting beyond 600MB when drives when over 1 or 2TB. I know they fixed that, but not sure if / only on that large of a drive is an issue.

OK. I created a partition for / of ~100 GB size and assigning the rest of the space to /home, and in fact this way the system can boot regularly (but see the new problem later). However, I am wondering why this happens: I have currently 9 workstations, each one with Ubuntu (16, 18, 20 according to when I installed it) installed over a RAID volume of identical size. So far I always installed the OS without changing the default partitioning of the installer. Why now what the installer does by default does not boot the machine?

> **oldfred said:**
> 
Also 16.04 is EoL, so any tests with that would not work. 

Sure. I tried 16.04 only because I had an installer available for that version. But I wanted to install Ubuntu 18.04 on that because that was the OS installed on that machine before. If it worked in the past I do not see the reason why it should not work now.

> **oldfred said:**
>  I might reinstall with smaller / partition. 

As I mentioned above, I did so, and in fact the system boots. However, the first time I tried to login into my account, I could see the desktop for 1-2 seconds and then the system came back to the login screen. Any further attempt goes in a login loop. I can instead enter via Terminal (CTRL+ALT+F3). Therefore, I tried to fix the login loop by following each of the suggestions in: 

[https://webcache.googleusercontent.com/search?q=cache:hGeMGrCq25gJ:https://techsphinx.com/linux/fix-ubuntu-login-loop/+&cd=2&hl=en&ct=clnk&gl=de&client=safari](https://webcache.googleusercontent.com/search?q=cache:hGeMGrCq25gJ:https://techsphinx.com/linux/fix-ubuntu-login-loop/+&cd=2&hl=en&ct=clnk&gl=de&client=safari)

including reinstalling and switching the display manager from gdm3 to lightdm but no success (the permissions are OK, .Xauthority file is not present in my home and I removed the splash option in the GRUB configuration file). Again, why such a problem in a fresh installation of Ubuntu 18.04, if before I didn't have any problems in installing this version of Ubuntu on such workstations?

> **oldfred said:**
>  Do not know RAID, is this FakeRAID, or BIOS based? 
Most with Linux seem to suggest using mdadm, but I have never used RAID nor know any details.

It is a BIOS RAID, and from the BIOS the disks and the RAID volume are OK.

All the best,
Emiliano

---

### Post by oldfred on 2022-07-19
Before when there were issues with drive size users had similar issue. It would work when installed (or not) and then would stop working (or work on reinstall).
The Boot-Repair report shows where on drive the boot files, grub, kernel etc in /boot are on drive. And issue of not booting was when files were not near beginning of drive.  So on a system that worked files were near beginning. But kernel update wrote new kernel files far into drive and then it stopped working. Do not know if still an issue, or maybe BIOS/RAID drivers make a difference?

Many years ago when standard drives were 20 MB and users put in larger drives, BIOS would not boot beyond a certain point. But that was a BIOS issue, not a boot file issue. Users then had to keep / inside first 20MB or have separate /boot inside first 20MB.

Ubuntu installer default install of just / (root) (and ESP if UEFI), is from many years ago when drives were smaller. And many installs are dual boot so / would also then not be large. Often for a new user, having just / without any additional partitions to manage is preferred. But now that drives are much larger having only / is not preferred.

---

### Post by eippoliti on 2022-07-19
I see. This makes a lot of sense: it explains both the boot issue I had and the reason why I didn't face that on other similar machines, and now I have a protocol to avoid it. Thank you.

For the login loop immediately after the installation of Ubuntu 18.04 I think I have found a solution as well: 

- First I login via Wayland instead of Xorg display server
- Then I upgrade the OS
- Finally, after rebooting I can login with the standard Xorg display server

All the best,
Emiliano

---

