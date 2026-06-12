---
title: "can't install or upgrade to 12.04"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2012-04-28
I spent all day yesterday trying to upgrade to 12.04. The same failure happens with ubuntu or xubuntu and with CD or USB.First I tried the option from update manager and no upgrade option would show. I currently have 11.10 ubuntu 64 bit and it is all updated daily. Then I tried alt+f2 command ```
sudo update-manager -d
```. No luck then I tried live CD and USB nothing. Then I booted from Knoppix and clean formatted sda1 to ext4 and boot flag and used "boot repair" cd to install grub to sda1. I have my /Home on /sda2 so for now at least that is safe. I also have a 2GB swap partition.Now I get the install options none of which do anything and then eventually the Ubuntu screen with dots under it. That sits and does nothing. I have waited even hours to be sure. I am pretty fed up. Do I have to give up on Ubuntu or is there something else to try? Both Puppy Linux live CD and Knoppix live cds boot fine.I also tried making the iso USBs from both Unetbootin and the Ubuntu startup disk creator.I am using the 12.04 desktop 64 bit desktop verson of Ubuntu and Xubuntu to upgrade with.

---

### Post by darkod on 2012-04-28
The grub bootloader shouldn't be on a partition (sda1), instead it should be on the MBR of the disk, /dev/sda. That is, if you are using it as the main bootloader.

When you try to boot into live mode first, does it load correctly? Or there is some problem?

If there is a problem loading live mode, you will see the same when installed so don't even try to install until you figure out what the issue is. Very often it is video driver issue especially with nvidia cards.
In these cases you can try adding the 'nomodeset' boot parameter.

When you boot with the cd/usb, immediately at the first purple screen hit Esc. That will show the older style main menu. Hit F6 for advanced options, select nomodeset. From the main menu select Try Ubuntu and see if ot loads OK.

If it does, you can start the install but you will have to use nomodeset again at first boot so it can load correctly. After that you should be able to install the video driver and it should be fine.

Lets see what the issue is, and if you need help using nomodeset at first boot we can give you instructions.

---

### Post by cmcanulty on 2012-04-28
No as I said I can only get a puppy or knoppix live CD to boot.Any of the ubuntu types freezes at the Ubuntu logo. This laptop was running 11.10 fine.I will try to do as you say from the puppy CD or knoppix though as I am not as familiar with those I may have trouble.OK I got to 
nomodeset and got it checked but then if I hit enter again it unchecks so how do I get to try Ubuntu?Wait, I got the nomodset checked then hit escape and got to the Ubuntu with the dots but again everything is frozen. I would be willing at this point to wipe everything and repartition but am afraid that will make it even worse. Now I am stuck on an error about the "b43/ucode5.fw" not found though I am connected with eth anyway.

---

### Post by cmcanulty on 2012-04-28
No as I said I can only get a puppy or knoppix live CD to boot.Any of the ubuntu types freezes at the Ubuntu logo. This laptop was running 11.10 fine.I will try to do as you say from the puppy CD or knoppix though as I am not as familiar with those I may have trouble.OK I got to nomodeset and got it checked but then if I hit enter again it unchecks so how do I get to try Ubuntu? I have checked the nomodset but then I am frozen at the install method screen and nothing I select does anything.Now the knoppix and boot repair CDs won't mount.

---

### Post by darkod on 2012-04-28
Please format your replies better, they are very difficult to read and follow.

So, after you activate nomodeset, you can't select Try Ubuntu from the main menu? It can't even try to continue booting into live mode?

---

### Post by cmcanulty on 2012-04-28
No I can't ever get into live mode. Now I am using ubuntu rescue cd 9.10 and can get to a ubuntu@ubuntu: ~$ prompt but have no idea what to type.I could call you if that would be easier or you can call me.OK I got gparted live to run and have clean formatted sda1 to ext4 with the / flag. Now I guess I have to install grub but not sure how as sda1 is the first drive listed and you said I need to put it /dev/sda

---

### Post by cmcanulty on 2012-04-28
No I can't ever get into live mode. Now I am using ubuntu rescue cd 9.10 and can get to a ubuntu@ubuntu: ~$ prompt but have no idea what to type.I tried from the gparted cd ```
sudo grub-install /dev/sda
``` and get ```
grub-probe: error: cannot stat 'aufs"
```twice and then ```
Could not find device for /boot: Not found or not a block device

```My partitions in gparted are /dev/sda1 ,label, / 14GB, /devsda2 label, /Home 96GB, and /dev/sda3 label,linux-swap

---

### Post by darkod on 2012-04-28
Don't try to install grub like that, you can't from live mode. Besides your problem is not grub.

You need to try booting into live mode with 12.04 not 9.10. Since you are trying to install 12.04 you need to make that work.

Lets go step by step.
1. When you hit Esc during boot you can get the main menu to show, right?
2. Pressing F6 open the advanced options. You can select nomodeset from there.
3. When that submenu closes you are back in the main menu. With the up/down arrows you can select what you want to do in the menu and select Try Ubuntu.

It should at least try to boot it even if it doesn't succeed. It shouldn't remain frozen on the main menu.

---

### Post by cmcanulty on 2012-04-28
If I could ever get it to live mode I wouldn't have a problem. It freezes with the list of install, try, etc. I was using 12.04 I just have now tried about 10 other CDs trying to get it fixed and I can run gparted live cd but the Ubuntu CD won't ever run. I have tried several versions on CDs and USBs different 10.04,9.04 12.04 xubuntu, knoppix etc.I keep saying the problem is I can't get live mode to run If I could it would be easy to install.I read this and that is why I was trying installing from live a live CD unfortunately only gparted or knoppix live cds will run
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")
and
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files")
sda1 is now newly formatted to ext4
I can install puppy linux and knoppix I have knoppix and grub installed now but still Ubuntus won't install. This is very weird.

---

