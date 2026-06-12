---
title: "Installing Ubuntu 8.04 on an external hard drive"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by phillip_peters52 on 2008-07-13
Hey guys 

Could anyone give me a few pointers on installing Ubuntu 8.04 on a LaCie 320gb external usb 2.0 hard drive, and also boot into windows Vista on a Pakard bell x3414 desktop PC.

The Bios Set up on the Pakard Bell x3414 does allow booting from an external hard drive. 

As far as I awawre the hard drive that came with the machine has a SATA interface and the external has an IDE interface will this cause any issues?

Thanks

Phill

---

### Post by Pumalite on 2008-07-13
Boot your Live CD. Connect your USB. Identify it running:
sudo fdisk -lu
Install Ubuntu. You can go Guided>Use Entire Disk (make sure you know which drive it is. In step 8, go to 'Advanced Tab' and change (hd0) for /dev/???. where ??? corresponds to your findings in sudo fdisk. Before you reboot; edit menu.lst of your external and make 'groot' and 'root' (hd0,0)
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-21-when-trying-to-boot-xp-after-installing-ubuntu-7.04-on-seperate-hdd-552043/)

---

### Post by shagy on 2008-07-20
This will work with with Ubuntu and Kubuntu cds as well. Though on Kubuntu I did not had to reboot after installation in order to modify the menu.lst file. The first step in order to accomplish what you want could be to read the following website:[http://ubuntukids.org/blog/?p=69]("http://ubuntukids.org/blog/?p=69") Why? It is more detailed that the one given at the last post. Though is valuable because it said about the problem you could create if you don't change from hdo to hd1 during instalation. In case you did not made the modification and you are still able to boot and enter Windows Vista download EasyBCD, EasyBCD is a free program that allows you fix bootloader problems and arrange dual boots using the Windows VIsta bootloader. I think it works on XP too.If you did not change hd0 to hd1 (if this is the correct location) try to find on EasyBCD where it says reinstall windows vista bootloader.

Now straight to the point. Instead of writing dev ???? I wrote hd????because according to the cited website is equivalent  .So  it seems that no matter the name as long the location is correct. The problem I had with Ubuntu is that I could not modify the file because I could not mount the hard disk after the installation. Later I reboot to Ubuntu on live cd mode. So I tried to modify the grub file but I couldn't because I needed root access and I am a rookie with the terminal. If you are like me, then check this [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg01552.html.]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-05/msg01552.html.") I think that the command that says nano worked for me. As I said on Kubuntu is easier because you can get to the file and modified prior to reboot.


Caution: After you update the system the file will restore the original values so you will be unable to boot to Ubuntu. Grub will give you some of the errors which displays if it can´t boot. To solve this you will need to select the entry that says ubuntu and press e to edit it. On the first line change hd1,0 to hdo,0 as you would edit something in a text editor.

Thanks for the two post they really helped me.:)

---

