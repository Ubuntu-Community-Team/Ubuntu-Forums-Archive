---
title: "Dual boot Ubuntu 10.04 and Vista. Load grub to MBR"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by evo9 on 2010-08-17
This is a little guide on what to do if you dual boot Ubuntu 10.04, and Vista, having Ubuntu installed first, and you lose access to Ubuntu.

Having Ubuntu installed first means that when you install Vista, the Vista bootloader is going to take over and grub won't visible anymore. Which is a pain since that dosn't really make your system a dual boot, but instead just lets you load Vista. So heres what I did to get grub back and allow my system to dual boot.

Boot into Ubuntu using Live CD by putting in your Ubuntu install disk and clicking the Try Ubuntu option (You may have to change your boot device order to boot from CD/DVD if you havn't already)

Once in Ubuntu open up a terminal (Applications -> Accessories -> Terminal)

In the terminal type in the following commands:
[COLOR=Olive]     sudo fdisk -l[/COLOR]
[COLOR=Black]This is to determine which partition with the Ubuntu installation. If you are unsure which is it, look for the partition with the appropriate size, or formatting.

Next enter:
     [COLOR=Olive]sudo mount /dev/sdXY /mnt [COLOR=Black](use the Ubuntu drive and partition found in the                                                 previous command)[/COLOR]
[COLOR=Black]sdXY - the X and Y correspond to the drives and the partitions, X being the drive, Y being the partition. For example sda is most ppls HDD, while sdb would be some kind of external drive. sda1 would be the first partition where sda5 would be the fifth.[/COLOR]
[/COLOR][/COLOR]
Next enter:
     [COLOR=Olive]sudo grub-install --root-directory=/mnt/ /dev/sdX
[COLOR=Black]Example: [/COLOR][/COLOR]sudo grub-install --root-directory=/mnt/ /dev/sda[COLOR=Olive]
[/COLOR]
Now reboot from the HDD into Ubuntu and open a terminal

Enter the command:
     [COLOR=Olive]sudo grub-update[/COLOR]

You should now be able to load both Ubuntu and Vista.


I had this problem earlier today and I had to search for hours through a bunch posts until I found the answers. So I thought for once instead of asking a bunch of questions that I needed  help with that I'd actually contribute something to the forums. So I  hope this helps someone.

---

### Post by presence1960 on 2010-08-17
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

a simple search from the ubuntu help page : [https://help.ubuntu.com/](https://help.ubuntu.com/) will turn up the links above.

sorry you had to spend a lot of time looking. maybe you just looked in the wrong place. The good news is that you worked through it and found the solution. to that I say cheers! if more people would do what you just did imagine how enlightened the members of this community would become.

---

