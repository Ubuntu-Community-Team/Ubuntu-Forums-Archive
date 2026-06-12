---
title: "Grub 2 in Ubuntu 10.10?"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by apanton06 on 2011-03-20
So I've been using Ubuntu 10.10 for a while now, chainloading to Grub 2 from the Windows boot manager (using Neosmarts EasyBCD) on my laptop for some time now. I decided to try out Mint 10 KDE the other day properly (tried it before for a few days).

After installing, I booted to Grub 2 in Ubuntu and noticed I still had Fedora listed (I removed Fedora a while ago). So I used the command: sudo update-grub to update the grub menu.

The problem is, both Ubuntu and Mint use Grub 2. What happened is when I chose to chainload to Grub 2 on the Ubuntu partition, it boots up the Mint one. They look different and I am not fond of the Mint boot background, as well as the fact the resolution is not correct: [http://beginlinux.com/images/desktop/linux-mint/linux-mint-install1.jpg](http://beginlinux.com/images/desktop/linux-mint/linux-mint-install1.jpg)

Also, in EasyBCD, to select Grub 2 it choses (automatically configured) and you are unable to manually select the partition. Is there a way to fix it, so I can select Ubuntu from windows boot manager and boot in to the Grub 2 in the Ubuntu partition without reinstalling any OS?

---

### Post by wilee-nilee on 2011-03-20
Quite simply the easybcd is your problem here to be honest. If you want the grub menu from Ubuntu to show if you didn't have the MS bootloader in the mbr you would just reinstall grub to the mbr from Ubuntu.

Easybcd is a good program when needed, but otherwise is a waste of time; an extra link in the boot chain I wouldn't like in my setup and I have MS as well.

I did find this though, basically mints setup is the same grub2 wise, besides this you have burg as well.Loading burg will change the mbr so make sure you know how and have a disc to reload the MS bootloader.
[https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming](https://help.ubuntu.com/community/Grub2#Splash%20Images%20and%20Theming)

---

### Post by apanton06 on 2011-03-20
Thanks for the help.
As I was only testing out Mint 10, I removed the partition in Gparted, removed it from the boot menu and updated grub 2 in Ubuntu. This fixed the problem.

I was thinking of using Burg but I am still unsure. I think I will use a different bootloader as EasyBCD has its limitations.

---

### Post by wilee-nilee on 2011-03-20
> **apanton06 said:**
> Thanks for the help.
As I was only testing out Mint 10, I removed the partition in Gparted, removed it from the boot menu and updated grub 2 in Ubuntu. This fixed the problem.

I was thinking of using Burg but I am still unsure. I think I will use a different bootloader as EasyBCD has its limitations.

Burg is a variation of grub2 just a little earlier in grub2's development. You could probably get it working.

---

### Post by apanton06 on 2011-03-20
I looked over and it seems quite straight forward. I assume you specify your different OS (and the partitions they are installed on) in the program?

---

### Post by wilee-nilee on 2011-03-20
> **apanton06 said:**
> I looked over and it seems quite straight forward. I assume you specify your different OS (and the partitions they are installed on) in the program?

I don't quite understand exactly what you mean here, in this area I'm really careful I understand.;)

Looking at this page it looks as though you can install it and not have it overwrite the mbr. When I have seen instructions for easybcd it usually I believe is a matter of reloading the MS bootloader back to the mbr, after a Ubuntu or grub based install though.
[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

I assume here that if you install burg and point esaybcd at it you will be okay.

The nice thing here is if you bork the Ubuntu loading you can chroot into it from a live cd and purge and reload all the stuff if needed. Just remember what was installed and the commands. There is also supergrub which can get you into all the OS's if needed to work from inside rather then getting in from a live Ubuntu cd. Just more tools for your toolbox to make life a little easier.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

The one in the middle will boot you into windows or your Ubuntu in case of problems most likely.

---

### Post by apanton06 on 2011-03-20
> **wilee-nilee said:**
> I don't quite understand exactly what you mean here, in this area I'm really careful I understand.;)

Sorry, I was looking at a site which reviewed a program to install BURG and customise it in a GUI rather than CLI.

I assume you have set it up using the documentation you posted?

---

### Post by wilee-nilee on 2011-03-20
> **apanton06 said:**
> Sorry, I was looking at a site which reviewed a program to install BURG and customise it in a GUI rather than CLI.

I assume you have set it up using the documentation you posted?

Yeah just did out of curiosity, I have used it before. I installed and was asked for the grub=burg placement I put it in the mbr as I'm using grub for the main boot. In the past I have removed grub completely as burg is grub2 with bling, this time I'm leaving it just for fun. 

So I messed with the screen resolution and lost the menu altogether and just pulled out the supergrub I have on a thumb and it got me straight into Maverick, where burg was installed. I went to the file for editing grub, only using burg and reset the resolution ran update-burg and was set.

---

