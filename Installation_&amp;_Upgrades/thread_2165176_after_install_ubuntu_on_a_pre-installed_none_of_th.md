---
title: "after install ubuntu on a pre-installed none of them are recognized on restart"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by alchimista on 2013-08-03
HI, i've tryed to install ubuntu 13.04 on a toshiba c850 with pre-installed win 8. I had to choose the "something else option" and created the swap partition and installed ubuntu on the free space (with ext4), followed by boot-repair wich posted this log ([http://paste.ubuntu.com/5944101/](http://paste.ubuntu.com/5944101/)).

 After reboot it was still going to windows, so i've manually created the /root/ partition, acording to a tutorial, and ran bot-repair again. So after this final reboot, it doesn't loads anything. It shows a message telling that was unable to load /media/,or something like that, and in ubuntu live cd, i've got a gigant partition with ubuntu files, and the size of aprox the full disk. What to do now? This is a grub config problem, right? My win recovery utility isn't working, so i'm kind of stucked.

---

### Post by ibjsb4 on 2013-08-04
You have win8 and efi, I have neither, but here are some forum hits on them.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+8&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+windows+8&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-08-04
You are showing two efi partitions sda2 & sda8. That will not work as you can only have one per hard drive. efi partition is set with gparted and boot flag. So remove boot flag from sda8. sda8 is also ext2 and efi partitions are fat32, so it may not be seen anyway, but still fix it.

Boot-Repair dumps the efi variables if it can. You show this on line 902, so you should be able to go into UEFI menu and choose to boot ubuntu entry.
902 Boot0001* Ubuntu

---

### Post by alchimista on 2013-08-04
Thanks for the help, but i still have problems here. Before your answer, i've runned boot-repair on live cd, wich gave me this info: [http://paste.ubuntu.com/5949357/](http://paste.ubuntu.com/5949357/) , and this seems to be my main problem. Boot-repair is asking me to create a new uefi partition, and i allowed it, but then he gives me the message "Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again.". As you can see on the paste, and that seems to be the problem, is that after the installation i got this info [http://paste.ubuntu.com/5944101/](http://paste.ubuntu.com/5944101/) , but after the first reboot, when it didn't show any grub or windows, somewhere between those steps, windows and ubuntu got mixed on sda2, so when i run live cd, i can't see the windows files, it's just like an ubuntu fresh install. If it's not easy to fix it, how hard is it to get windows boot again? My win backup copy isn't working, so if i could at least have win working i could make a new one, and try to meet some of local ubuntu experts on my area to help me installing it.

---

### Post by oldfred on 2013-08-04
It is normal with UEFI for each operating system to have its folder in the efi partition. But you have two efi partitions. Not sure if UEFI is not working just because of that but you have to take boot flag off of sda8. Only one boot flag per gpt partitioned drive. Use gparted from live flash drive or other Linux repairCD - gparted or Parted Magic.

Not sure why Boot-Repair does not see the efi partition on your first link. But you are showing errors in FAT32 partition and may be able to fix those type of errors by running chkdsk from your Windows repairCD on that partition. You cannot run chkdsk from Linux, but some third party Windows tools may include it. 

      >   Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.

    



---

