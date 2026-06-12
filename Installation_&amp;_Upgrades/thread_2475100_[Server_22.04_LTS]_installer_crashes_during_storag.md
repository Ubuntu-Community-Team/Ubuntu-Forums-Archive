---
title: "[Server 22.04 LTS] installer crashes during storage (RAID-1) config on Dell T320"
date: 2022-05-16
forum: Installation &amp; Upgrades
---

### Post by kleinmat on 2022-05-16
Hi all,


I have a Server Dell T320 with PERC S110 and two SATA drives (Western Digital, 2TB each), and I would like to install Ubuntu Server 22.04 LTS on it, while running the drives as RAID-1. 
Since the integrated RAID-Controller PERC S110 apparently can't create a hardware RAID that's usable with Linux (only seems to work with Windows), I put it in AHCI mode and started the Ubuntu Installer.
Because the installer does not have a convenience function such as "create RAID & use entire RAID", I had to select "Custom Storage Layout".


Below, I have tried to capture my choices, and I have to apologize for the utterly bad image quality.


But the short story is, I

[LIST=1]
[*]created a software raid-1 selecting both active partitions
[*]selected the resulting virtual device, selected "format" and told it to format with ext4 and mount to /
[*]selected the first physical drive and selected "use as boot device"
[*]selected the other physical drive and selected "use as additional boot device"
[*]confirmed the "destructive action"
[/LIST]


That led me to the screen where one can enter username and password, etc. 


But whether I entered something there or just waited a few seconds, the installer always crashed.


What can I do to use software raid-1 with ubuntu server on my machine?


Thanks
Matt

--



[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290477&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290476&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290474&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290473&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290475&stc=1[/IMG]
[IMG]http://www.qunnect.com/01.jpg[/IMG]
[IMG]http://www.qunnect.com/01.jpg[/IMG]

---

### Post by kleinmat on 2022-05-17
I think here is the solution:

[https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices](https://askubuntu.com/questions/1234949/install-ubuntu-20-04-focal-fossa-with-raid-1-on-two-devices)

I followed the instruction laid out by user "[fevangelou]("https://askubuntu.com/users/570422/fevangelou")", which is also marked as "best answer". 

Even though in 22.04 LTS there does not seem to be the need for a swap partition, but still...

---

