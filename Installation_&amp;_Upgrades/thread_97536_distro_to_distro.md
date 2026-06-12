---
title: "distro to distro"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by mszl_1 on 2005-12-01
how do you install one distro onto another ie mepis to gentoo?:???: :???:

---

### Post by taurus on 2005-12-01
You cannot install one distro on top of another without using some kind of emulator!!!  You should know that...

---

### Post by linbetwin on 2005-12-01
why don't you dual-boot?

---

### Post by kairu0 on 2005-12-01
[QUOTE=mszl_1]how do you install one distro onto another ie mepis to gentoo?:???: :???:[/QUOTE]

Why would you even want to do that?

Each operating system should have at least one partition to inhabit by itself.

---

### Post by Nana on 2005-12-01
The different Linux distros are (usually) developed independently, so although all the distros use the Linux kernel and pretty much the same software, their basic structure can differ *very much* from each other. That's why you can't usually install a different distro on top of another.

---

### Post by az on 2005-12-01
[QUOTE=taurus]  You should know that...[/QUOTE]

Not a nice thing to say.

As for the original question, do you mean you want to replace your current linux install with a different one?

It depends on the distribution's installer, but you just reformat the particular drive or partion on the drive and reinstall the bootloader and you are done.

In Ubuntu's case, you would run the installer and when it asks youabout partitioning, you would do manual partitioning and delete your mepis install.  You then use the free space to install ubuntu.  From that point it is easy since you can go back to "guided partitioning" and have it create the neccessary partitions itself.

---

### Post by mszl_1 on 2005-12-01
thanx for replies. however i know nothing about linux and some replies were somewhat off. if you dont know then ask questions, this is what im doing inorder to learn. if i knew more then i wouldnt have to ask! im witing to hear how top dual boot with xp on a hd.:mad:

---

### Post by kairu0 on 2005-12-01
[QUOTE=mszl_1]im witing to hear how top dual boot with xp on a hd.:mad:[/QUOTE]

I thought you wanted to have two Linux distributions installed?

Anyway, that's not important. Know that each operating system (or distribution) needs it's own partition and if you don't have enough partitions then you'll need to make more by manually partitioning. (AKA Follow the previous post.)

---

### Post by az on 2005-12-01
[QUOTE=mszl_1]thanx for replies. however i know nothing about linux and some replies were somewhat off. if you dont know then ask questions, this is what im doing inorder to learn. if i knew more then i wouldnt have to ask! im witing to hear how top dual boot with xp on a hd.:mad:[/QUOTE]

wiki.ubuntu.com/UserDocumentation

There is a lot of documentation there, including details about dual booting.  The nitty-gritty, however, is that the installer will detect your windows installation and offer to shrink it's partition to make room for your Ubuntu install.  All you have to do is say yes and tell it how much room to give to Ubuntu and it does all the rest automagically.  You will be offered a menu when you turn on your computer and will be able to chose which OS you boot.

It is very safe.

---

### Post by WileE on 2005-12-02
What AZZ said.  I wanted to install ubuntu over XandrOS.  I tried using the existing partitions, but it had problems.  I deleted the XandrOS paritions and then did the guided setup.  Ubuntu then asked to use the free space for the install.  It detected the existing XP install and added it to the grub bootloader.

The lesson learned is just have some free space for ubuntu to use and it will do the rest.

---

### Post by mszl_1 on 2005-12-03
thanx azz. will give it a go and see what happens. i have since got hold of fedora  core and installed it on my 2nd hd and it seems ok. the only thing that is confusing is the names of files apps etc, but i guess that willsolve itself by constant use!:)

---

