---
title: "HDD partition and grub"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by bigbird on 2008-02-11
After installing Kubuntu on top of a working Ubuntu install I broke the K and want to remove it and re partition my Hdd to original and remove it from grub start menu.
What would have been the original partitions 1,3 5,6swap
is there a good program for that like PM

---

### Post by Herman on 2008-02-11
:) Hello bigbird,
What do you mean you installed Kubuntu 'on top of' Ubuntu and what is it you are trying to do?

If you need specific help, please boot the Ubuntu Live CD and post the output from 'sudo fdisk -lu',
```
sudo fdisk -lu
```We use GParted, also called Gnome Partition Editor, or any of the 'Parted family of hard disk partitioners. You'll find GParted in the Gutsy Gibbon Live CD in 'System'-->'Administration'-->'Partition Editor'.

If you mean you're deleting Kubuntu but you still have a good Ubuntu install, you'll need to re-install GRUB.
If you're new and you're not too sure about using the command line yet, you can do that with [Super Grub Disk.]("http://sgd.benjamin-butschko.de/")
Or, you can do it with the Ubuntu Live CD or almost any Linux Live CD with the command line, here's how, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

If you mean you already overwrote Ubuntu with your Kubuntu install, and you're leaving and going back to Windows, you'll need to re-install Windows boot loader to MBR. There are lots of ways to do that, here is a whole page with illustrations explaining several methods, just pick one that looks easy for you, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Regards, Herman :)

---

### Post by bigbird on 2008-02-11
Both are still there No Win anything on drive,  only Ubuntu still works let me work on these resources and figure it out Thank you Herman.:p):P

---

### Post by Herman on 2008-02-11
Okay, you're welcome bigbird, if you have any problems that you need help with just ask and I or someone around here will try to help you.
Regards, Herman :)

---

### Post by bigbird on 2008-02-12
Thank you Herman.
I am new the command line is a scary thing I have had a run in or two.
I appreciate the help very much I remember trying to get help with Lindows If someone answered they basically told you to go back to MS land.

Thankfully nothing is sacred here, I travel for a living and play with my laptop with a spare drive to train myself to deal with it. so if I kill it dead - format "C" reinstall more practice..

Right now I have  a running 7.1 Ubuntu HP Pavilion zv6000.

I wanted to play with KDE4 so I burned a Kubuntu 7.1 disc loaded it up and it worked out fine,,, but while upgrading to KDE4 from the 3.5 ?? desktop in gusty-k it failed to up-grade and the Kubuntu wont work at all any more I want to apologize I did not document the failure.

Basically I want to have a opportunity to try out the K version but I am Totally hooked on Ubuntu 7.1.
very happy with every install I have done so far for friends and our babysitter all desktops this laptop is the first I have tried and to my knowledge the only thing that does not work is the media card reader; Texas Instruments PCI (TI-PCI) 6xx1/7xx1 Cardbus.

Thank you again.
Regards,  Chauvin.

---

### Post by DavidTangye on 2008-02-12
>  I wanted to play with KDE4 so I burned a Kubuntu 7.1 disc loaded it up and it worked out fineIt sounds like this did not actually work out fine. This is not the way to get Kubuntu onto a Ubuntu machine. It a bit confusing at first, but here is the key info:

Ubuntu and Kubuntu are different editions. Each has common core packages, plus Ubuntu has package 'Ubuntu Desktop', and Kubuntu has 'Kubuntu Desktop'. These are 'meta-packages': they simply refer to a bundle of real and alternative packages. If you install Ubuntu you get the core stuff plus the Ubuntu Desktop (package set). If you then want to try Kubuntu you shuold either:

 - Install Kubuntu edition into a FRESH partition, (then you can boot one or the other system) or
 - Install Kubuntu Desktop meta-package into the Ubuntu system using the Synaptic package manager.

You installed one edition over the other, so your system will have problems.

---

### Post by bigbird on 2008-02-12
It was installed on new partitions but I broke it trying to go from 3.5 to 4.0 KDE.
I never finished, Up-grade failed. when I try to start it form Grub I get a Processor confused message tonight I will put in HDD and try to get exact info.
I prefer the Ubuntu version myself trying to get more experience so if someone wants to use KDE I can help.
Thank you for your assistance. Chauvin.

---

### Post by Herman on 2008-02-12
Hmmm, the way I interpret your posts I was guessing that you did install Kubuntu to some other partitions. 
I'm not sure what you mean about upgrading from KDE 3.5 to KDE4 though. I'm not well read on the latest KDE news. 
If you mean you downloaded that from the KDE site and installed it then I can well imagine you'd have problems. You'd need to be an expert to do that. I don't think I would be able to do that. 
I always just get all my software from the official Ubuntu repositories and accept the automatic updates when they are offered to me. That's the easiest way.  
Installing software from anywhere other than the official Ubuntu repositories isn't generally recommended, and is a well known way to bork your system. I know, I tried it too when I was first getting started.  :)

I like to try out Kubuntu sometimes, but Ubuntu is my favourite. Did you know you can install the KDE desktop in Ubuntu? Here's a link about that, [Install KDE Desktop in Ubuntu]("http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html")
```
sudo apt-get install kubuntu-desktop
```There's no harm in having an extra Ubuntu or Kubuntu though, I always like having a few operating systems in each computer.
I like to have one system for regular use and one for experimenting with, something like what you're doing I guess. That's the best way to learn.

You'll get used to the command line pretty soon and after a while you'll get to like it, believe it or not. I was the same when I was first getting started with Ubuntu too. 


I don't know anything about media card readers, I always plug my digital camera in with a USB cable. Maybe someone  who can provide some info will come along. I'll keep it in mind and if I see anything useful I'll report back here.

It's great to be able to install Ubuntu for family and friends! Cool :cool:
I think everyone should have Ubuntu in their computers! Ubuntu RULES! :)

Regards, Herman :)

---

### Post by DavidTangye on 2008-02-14
The ubuntu folk spend a lot of energy customising software for ubuntu, so it will not break the system, and then put them into the repos so you can get it effortlessly. If you install software outside of what ubuntu provide via their package repositories you are asking for trouble.

---

