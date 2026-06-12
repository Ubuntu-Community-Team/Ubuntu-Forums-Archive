---
title: "Problem to boot with 12.10 and EasyBCD"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by player16 on 2012-12-19
Guys;

I followed the steps of these tutorial to install Ubuntu 12.10:

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/)

However, when i try to boot Ubuntu, this message appears:


GRUBA4DOS 0.4.5b 2011-11-27, Mem:634k/511m/3070m, End: 35560D

minimal BASH like line is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filaname.
 
Here is the description of my Ubuntu entry on EasyBCD:

Name: Ubuntu 12.10 BCD ID: {cca6db02-4a45-11e2-ad5f-9a4a408f2e85} Drive: C:\ Bootloader Path: \NST\AutoNeoGrub1.mbr
 
What should I do know?
What have i done wrong?

---

### Post by oldfred on 2012-12-20
You will probably do better on the EasyBCD forums. EasyBCD uses grub4dos as the work around to get Windows to chain boot to grub in a partition.

We suggest grub2 as the boot loader as it is designed for multi-booting. EasyBCD is a way to make Windows which is not designed for multi-booting multi-boot.
Also you have to force grub2's boot loader into a PBR or partition boot sector. Grub2's code is normally too large and it converts to blocklists or hard coded addresses. That will work until grub is updated or some change moves a file on the drive and the address is wrong. Be sure to have working live ISO on DVD or flash drive to reinstall grub2's boot loader.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by player16 on 2012-12-20
> **oldfred said:**
> You will probably do better on the EasyBCD forums. EasyBCD uses grub4dos as the work around to get Windows to chain boot to grub in a partition.

We suggest grub2 as the boot loader as it is designed for multi-booting. EasyBCD is a way to make Windows which is not designed for multi-booting multi-boot.
Also you have to force grub2's boot loader into a PBR or partition boot sector. Grub2's code is normally too large and it converts to blocklists or hard coded addresses. That will work until grub is updated or some change moves a file on the drive and the address is wrong. Be sure to have working live ISO on DVD or flash drive to reinstall grub2's boot loader.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I see, i tried to use Easy because I heard of problems Windows caused to Grub and Ubuntu, making Ubuntu unable to boot.

However, after all these problems, i give up EasyBCD !

Is there a way to use Grub now? Or should I just delete and reinstall Ubuntu?

---

### Post by darkod on 2012-12-20
If you installed ubuntu EXACTLY as in that link, you can boot with the cd in live mode, open terminal and just add grub to the MBR with:
```
sudo mount /dev/sda6 /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

That will add it to /dev/sda instead of /dev/sda5. Reboot and see if you get the grub boot menu.

If you DID NOT install on the same partitions as that tutorial, the above commands will need to be changed slightly, but you can still only add grub without reinstalling all of ubuntu.

---

### Post by konedima on 2012-12-20
I don't know how applicable it is in your case, but when I install Ubuntu using Wubi, it dumps me to the same GRUB prompt. I found it's because Wubi puts wubildr and wubildr.mbr on the Windows C: drive, when the bootloader is on the G: drive - so GRUB can't find the file (or something). I don't know exactly. I just copied the files Wubi made into the root folder of my G: drive and it works.

If you have more than one hard drive (or possibly partition that can be read by Windows), open up EasyBCD and see what drive the bootloader is on (should say next to "EasyBCD Boot Device"), then find AutoNeoGrub.mbr - probably in the root folder of C:\ (and if there's an AutoNeoGrub without an extension in the same folder, that too) and copy it to the drive the bootloader is on.

Of course, if you only have one hard drive - that's probably not applicable. Sorry for possibly wasting your time.

---

### Post by oldfred on 2012-12-20
Boot-Repair will automatically reinstall grub2's boot loader for you or you can manually do it from your live ISO DVD or flash drive that you used to install. You can install Boot-Repair into the Ubuntu live system or download a full repair ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemic](https://help.ubuntu.com/community/UbuntuSecureRemic)

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by player16 on 2012-12-22
&#7764;roblem solved, I installed the newest version of EasyBCD and now I can normally boot.

The problem was that EasyBCD tried boot Ubuntu from the C:/ partition, and not from the "/boot" Ubuntu partition.

---

