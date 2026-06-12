---
title: "How do I create a boot CD that will boot straight into LUBUNTU on my HDD"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by Mark Fee on 2012-10-04
Hi, 

I have installed LUBUNTU on an old laptop with / mounted on /dev/sda1 and /home mounted on /dev/sda6

However the laptop will not boot from the HDD - a problem with the bios I believe. I can get it to boot successfully by booting from a linux boot cd and then choosing to boot from the HDD.

My question is how can I create a boot CD that will auto boot into the OS on /dev/sda1.

It must be a CD - the laptop wont boot from USB either and I want this to be invisible to the user (ie no menu options to pick) The laptop will be for my very newbie mother in law who will be instructed to never take out the CD!

---

### Post by 2F4U on 2012-10-04
If the boot order in the BIOS is correct, I would assume that the boot loader is not installed or configured correctly, i. e. that it is not pointing to the partition where the boot code for Ubuntu is sitting.

---

### Post by oldfred on 2012-10-04
Post link to BootInfo report so we can see details. BIOS should boot from HD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you want a CD that is bootable:
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by Mark Fee on 2012-10-08
Thanks for the advice guys - I'm afraid I'm not sure what you mean by BootInfo report

However I've worked out how to do this by myself after a bit of reverse engineering of the ubuntu install cd which gave the option boot from first HDD which I wanted to recreate.  

Here's what I did if anyone out there wants to recreate the same dumb way of getting your machine to boot from the first HDD.

```
mkdir -p bootFromHdd/isolinux
```

I created two files in bootFromHdd/isolinux
 
isolinux.bin (copied from ubuntu install CD)
isolinux.cfg which I created and edited to contain the following text:

```
default 0
prompt 0
# hd
label 0
localboot 0x80
```

I then created a bootable ISO image from these folders with the following cmd (NB must be run from the parent drectory of bootFromHDD)

mkisofs -o bootFromHDD.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table bootFromHDD

I then used Xfburn to burn the iso to CD

reboot and voila.

see [http://members.chello.at/bobby100/ILpart1.htm]("http://members.chello.at/bobby100/ILpart1.htm") if you want to know what those .cfg lines mean.

Thats it!

Now  to hide the grub menu from my Mother in Law I edited
/etc/default/grub
and uncommented / altered the lines:

```
GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=0
```

and then ran 
sudo update-grub

another reboot and the machine booted straight into lubuntu (as far as the end user is concerned)

---

