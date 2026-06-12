---
title: "Problem with booting XP after installing Ubuntu as dual boot OS"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by N00bieLinuxUser on 2010-04-05
Hi guys,

I am new to this forum (and to Ubuntu, Linux in general). So please forgive me, if something similar have already been posted (I've searched this place upside down but nothing seems to be what I am looking for :( )

I was running Windows XP SP3 on my PC, and I decided to give Ubuntu a try. At first, I download VirtualBox and installed Ubuntu under virtual environment. However, I decided to dual boot it as I wanted to see how Ubuntu will truly work in a host environment.

I had a quick readup on APC website, on how to dual boot XP and Ubuntu, and basically followed the instruction (load the ISO via **boot from CD**, and installed from there; chose the option of booting side by side with Windows)

Once the installation was finished, I was prompted to reboot. When I was asked to chose which OS I want to launch (I do believe I am at the GRUB stage?? ) I chose XP. Unfortunately, after I selected XP, nothing comes up except for a blinking cursor, nothing will get launched even if I leave this screen on for 20+ minutes. I pulled out my XP installation CD, did a repair on the C:Windows (Windows XP Professional) and hope it would pick up XP again, but it didn't. So for the time being, I can only boot into Ubuntu, even though the option of booting XP is there, it just wouldn't do it.

Now I am "stuck" with Ubuntu (I am using stuck because I actually have no idea how to use this OS properly yet. :( )

It seems like a trivial thing, maybe I didn't partition the disk properly? (although XP repair can see C:\Windows )
I read somewhere how GRUB thinks itself is a better "bootloader" than Window's, and would be the default bootloader for the computer. As a result this might cause issues with booting Windows OS?


Any help would be appreciated!

note: my GRUB version is 1.97 beta 4   if that is any help

---

### Post by Naggobot on 2010-04-05
I admit that I have no experience with your particular problem. I have dual boot to XP and I did have to fix the grub at the time since I installed windows after the Ubuntu. The grub  version at the time was older. 

My main point for this post was to say: The Grub 2 (i.e. your version) is totally different from previous version so tread carefully when looking for help from the forums and web. 

Grub 2 has community documentation and you can find it from 

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

There probably is some relatively easy way to tell the Grub to locate the windows installation and repair the boot system.

---

### Post by oldfred on 2010-04-05
Usually grub2 is very good at finding other systems. Sometimes running another update finds it, or you may have an issue with windows.

sudo update-grub

If that does not work download this script to see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by N00bieLinuxUser on 2010-04-06
I will give the script a go tonight and post up the details. 
However, I have a feeling I would need to fix windows MBR for this to get Windows up and running again, and this then might cause Ubuntu not boot up properly :|

---

### Post by oldfred on 2010-04-06
How to restore all the types of boot loaders:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

