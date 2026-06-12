---
title: "Installing 10.04 with Wubi"
date: 2012-08-05
forum: Installation &amp; Upgrades
---

### Post by Ferris on 2012-08-05
Hi,
I'd like to install Ubuntu 10.04 on my hard disk.
I already have a pre-downloaded ISO (ubuntu-10.04.4-desktop-i386.iso) in the same folder as wubi.exe (which I downloaded from [here]("http://releases.ubuntu.com/lucid/"))
The problem is, Wubi keeps trying to download 12.04 which is not good for me since I want to install Ubuntu on a netbook.

Thanks for your help

---

### Post by bcbc on 2012-08-05
it shouldn't be possible for it to download 12.04 if you got it from the location you showed. Please confirm by going to the %temp% directory and looking for the wubi log file: wubi-nn.nn-revnnn.log and post the contents here. It should be named: wubi-10.04.4-rev194.log. 

If it's named: wubi-12.04-rev256.log then you have the wrong version of wubi.exe.

---

### Post by mastablasta on 2012-08-06
i think you can put the image file in the same folder as wubi and then it should use that image instead of doing the download.
 
also what does it matter if you have a netbook? you can use gnome classic on 12.04 and if you like you can also use unity 2D to reduce it's RAM usage. you can also use Mate (old Gnome fork).additionally if that is not low enough for you, you can use Xubutnu instead (looks like the old gnome) or any other DE you want. either way unless there is particular reason that you need the 10.04 kernel it would be better to use latest Ubuntu version. it should offer better support for hardware as well as have some bugs solved (granted you might find new ones ;-) )

---

### Post by jemadux on 2012-08-06
it is not good idea to use wubi .. wubi is only for testing not for using for everyday ...

---

### Post by Ubun2to on 2012-08-06
> **jemadux said:**
> it is not good idea to use wubi .. wubi is only for testing not for using for everyday ...

+1 I learned that the hard way, and had to spend lots of time prepping for an overnight move from Wubi to a new partition.

---

### Post by bcbc on 2012-08-06
> **jemadux said:**
> it is not good idea to use wubi .. wubi is only for testing not for using for everyday ...
What is your point? The original poster is trying to install Wubi and asked for help? Your post amounts to little more than spam.

Wubi is designed to "try out Ubuntu easily and safely" i.e. without partitioning or risking your main operating system.

It's okay for users to use it for this purpose, and it's okay to post here on ubuntuforums.org to get help when they have issues.

---

