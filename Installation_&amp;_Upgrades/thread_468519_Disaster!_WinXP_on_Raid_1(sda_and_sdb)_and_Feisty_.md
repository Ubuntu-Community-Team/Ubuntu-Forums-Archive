---
title: "Disaster! WinXP on Raid 1(sda and sdb) and Feisty on 3rd HDD(sdc). None Working!"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by easygoing on 2007-06-08
Feisty turns out to the worst Linux distro so far, bar none. It is the first time that a Linux distro corrupted my Windows.
I have a Dell XPS 400. The primary disks are two HDDs in Raid 1, with Windows XP on it. I have another HDD (/dev/sdc) for Linux. I like to use boot manager on Dell computer, so every time I will select which device as boot device, so Windows and Linux will stay cleanly on separate HDDs, with minimal interference to each other.
Two weeks ago I installed CentOS 5 on the 3rd HDD, with any problem in installation. Well, CentOS turns out to be a painful distro to work with. It refuses to boot into KDE, and startx will give me fatal errors.
Last year I installed Kubuntu 5.10 on another computer on a HDD separate from the primary HDD that Windows reside on, without any problem. So this time I naturally was attracted to the latest Kubuntu.
I boot up with Kubuntu 7.04 desktop release CD. I click the "install" icon, and selected "/" and swap partitions, using the same partitions on the 3rd HDD used by CentOS 5 before.
In the window "Ready to install" there is a "Advanced..." button. Clicking that shows a menu "Advanced Options". It displays:

Boot loader
Help for GRUB device selection goes here.
[input field] hda(0)
...

Since the install process lists my partitions in "SCSI4" etc, and the device is listed as "dev/sba" etc. I thought the word "hda(0)" does not mean much. CentOS correctly installed the boot section in the 3rd HDD where I selected the "/" partition also lured me to let down my guard. I left this value as it is, and clicked "OK".

After the installation succeeded, I first booted into Windows, to test my primary OS. It booted into the splash screen with the word "Windows" on the black background, then the blue screen of death.
I tried to select the 3rd HDD from Dell boot manager, I saw the word "GRUB" on the screen, then the system stopped.

I am a software engineer. I develop web applications in Windows and deploy them to CentOS or RHEL. In the past I have installed all kinds of Linux systems to the Windows PC, on partitions of the same disk, or on separate disks, without any problem. The earliest one is RedHat 7, all the way to FC6 and CentOS 5. The installation never gives me problem. The system problems became more and more pronounced with later distros, culminated in this Feisty that cannot get installation right.
Well, OpenSuse 10 is worse in software terms. It cannot find a file early in the installation. But at least it did not proceed on its bad ways to corrupt my other systems.
Now I would appreciate any suggestions that can help me to set up Feisty correctly so I can access my files in Windows partition, or help me to rescue my WinXP.

---

### Post by easygoing on 2007-06-10
What I found out is that Dell WinXP Recovery CD is amazingly good. Although I wasted some time in trying recovery mode without success, I went straight to install a new copy of WinXP in the existing partition. After 1 hour, I have everything back in perfect working order, along with all my settings and installed software. Even the latest games work right away.
Of cause, dot Net framework gave several warnings. The cause is that WinXP registry has reference to .Net Framework 1.1 functions, but the Recovery CD only installed .Net Framework 1.0. I researched this problem online and solved it easily by upgrading to .Net Framework 3.0.
Since I have some coding projects in mind and some software and framework only work under Linux, I do not feel the desire to spend too much time on the Linux OS itself. So I re-installed CentOS 5, and tolerate the problem of startx every time I log in. Now at least I can work and play.
As for GRUB installation directory, CentOS has one screen dedicated to this task. The default is the device that / is on. That is why I did not have trouble. Linux only sees 3 devices sda, sdb, sdc, and my decision to set / on sdc1. So I think the problem of Kubuntu is that the developers did not expect people to use hardware boot managers to select which device to boot from, and was lazy to show the GRUB installation device in a consistence way as the partitions. I felt that this is a broken feature.

---

