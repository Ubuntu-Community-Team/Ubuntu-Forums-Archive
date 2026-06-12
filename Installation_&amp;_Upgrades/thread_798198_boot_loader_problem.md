---
title: "boot loader problem"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by solidus636 on 2008-05-18
Hi.

I just installed Linux on a seperate partition from my Windows install, but on the same hard drive.

During the install, the installer for linux said that the GRUB loader couldn't be installed. I chose to install LILO instead.

Now I can't boot into Windows.

I've tried to remove LILO and install GRUB, but GRUB doesn't install right because LILO is still booting up linux without asking to boot Windows or not(Vista).

I want to remove Lilo, and install GRUB, or better yet, use the Original Windows Boot Loader instead of LILO or GRUB.

Please help, I've already searched, and I'm either really stupid or something is wrong with my Linux install because nothing works how it should.

edit: I just accidentally pressed shift+ctrl(i think?) and a menu for booting into Windows showed up. This is so far the only way I can boot into windows but it is still rather annoying and I want to replace it with GRUB.

---

### Post by Herman on 2008-05-18
LiLo doesn't need to be removed to install GRUB, you can have both boot loaders at the same time, they will share the same /boot directory just fine and they won't fight each other at all.

There's a backup of your Windows boot sector in your /boot directory made by LiLo, it will be in a file called /boot/boot/.(followed by a number). You can restore your Windows boot from that with a 'dd command, as per this link, [How Can I Uninstall Lilo?]("http://www.tldp.org/HOWTO/LILO-2.html#ss2.4").

If you want to install GRUB, first check if there's an exectutable for grub in /usr/sbin.
If none exists, you can install GRUB with an apt-get command or with Synaptic Package Manager, whichever you prefer.
```
sudo apt-get install grub
```Probably the above command will work, but I haven't tried it recently myself.

Then you should use the grub-install command to install GRUB somewhere. Grub will be installed to two places at once by the grub-install command.
grub-install will install the stage1 file to a MBR or else to a boot sector of your choice, (whatever device your specify), and also grub files will either be installed in /boot in your Ubuntu file system, unless they already exist there. They will not hurt your LiLo files if LiLo is already there.
However, GRUB will overwrite LiLo either in the MBR, or in the boot sector, depending on which device you decide to install GRUB to.

Before you make up your grub-install command, you will need to take a look at your partition table with 'sudo fdisk -lu' or with Gnome Partition Editor and decide what device to install GRUB to. The MBR of your first hard disk is a good choice.

For example, 'sudo grub-install /dev/sda' would install GRUB to MBR in your first hard disk, or maybe 'sudo grub-install /dev/hda', if applicable.
```
sudo grub-install /dev/sda
```

Then, since you will have no /boot/grub/menu.lst file, your computer will only boot to [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
If you want a nice GRUB menu, you'll need a /boot/grub/menu.lst file.
The quickest way to make one of those iss to run the command 'sudo update-grub', and that will make one automatically for you.
Now, you'll have a [GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#gui") when you boot up! 
```
sudo update-grub
```

You will still need to add Windows to your GRUB menu yourself, you can copy and paste an entry like this, (below) to the bottom of your /boot/grub/menu.lst file and Windows will show in your GRUB menu,
```
gksudo gedit /boot/grub/menu.lst
```
```
title        Microsoft Windows Vista
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```If that doesn't boot Vista, let me know and include the output from 'sudo fdisk -lu' here please and I or someone here will help you fix it.

---

### Post by solidus636 on 2008-05-18
alright, thanks a lot man.

---

