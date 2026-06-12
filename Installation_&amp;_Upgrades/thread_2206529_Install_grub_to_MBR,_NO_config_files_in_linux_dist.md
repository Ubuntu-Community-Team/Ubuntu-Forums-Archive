---
title: "Install grub to MBR, NO config files in linux distro partition"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by rexineffect on 2014-02-19
[COLOR=#333333][FONT=sans-serif]I thought I was installing grub to my MBR. Now I have found out some of grub's files are located on my linux boot / partition. Im wondering if there is a way to have all my grub files stored on my MBR.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]It seems like all the google searches for install grub to MBR return the same thing, some grub files to MBR but then still the grub conf files in your /boot/.... of linux install.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]What I would like is:[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]All grub files to MBR
os-prober to MBR
Able to have all partition erased on disk and still boot to grub
able to issue mkconfig / update-grub command and point it to proper location - MBR - to create grub.conf file.[/FONT][/COLOR]

[COLOR=#333333][FONT=sans-serif]So say I have grub installed to MBR, totally empty paritions, then install arch linux, I dont install a bootloader with it, then I restart and get into grub. I use grub terminal to boot into my linux. Then from arch I will issue a mkconfig command and use os-prober to automatically write my grub.conf file (which should be in my mbr partition, not in /boot/......)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]I understand grub cannot write from its own terminal, only read...otherwise I would say to just run mkconfig command straight from grub boot menu....but i dont think that will be possible.[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Im not sure if this is really unusual, not possible, or will cause many problems, your thoughts/ideas and help is appreciated.[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-02-19
How much space is there in the MBR? Not enough for what you want. 

The utilities of os-prober and grub-mkconfig run on Linux. They do not run on the limited Grub command line. MBR is not a partition. If you do not install a bootloader when you install Arch Linux then how can a reboot bring you to a grub terminal? Grub has not been installed, remember?

Doing this

> [COLOR=#333333][FONT=sans-serif]Able to have all partition erased on disk and still boot to grub[/FONT][/COLOR]

is impossible without setting up a special boot/grub partition at the start of the hard disk. And even then you will still need the same few Bytes of Grub code in the MBR. In Ubuntu we can set the boot images and the Grub files to install into a /boot partition.

---

### Post by oldfred on 2014-02-19
In the old days with grub legacy you could create a grub only partition. With grub2 that is rarely used a you want the advantages of os-prober.
But if you want to create a grub only partition with grub2, you can. But then you have to manually create and maintain your own grub.cfg file. I do this on all my flash drives, to boot ISO and chain to MBR of hard drives.
With Ubuntu you can create all the boot stanza's you need for every install, but I do not know if other distributions do similar things.
Ubuntu has in / (root) links to the newest kernel, so if you boot link you always boot current kernel.

       I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

