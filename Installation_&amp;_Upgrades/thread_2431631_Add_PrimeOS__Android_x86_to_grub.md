---
title: "Add PrimeOS / Android x86 to grub"
date: 2019-11-19
forum: Installation &amp; Upgrades
---

### Post by troneleck on 2019-11-19
(i know this might not be ubuntu relatet)


Hello,

I bought a older Lenovo Horizon 27.
My plan is to run it as multiboot device, with windows, primos and ubuntu.

I installed Ubuntu as last os.
Grub doesnt make an entry for primeos.
I made this entry with grub customizer:

```

set root='(hd0,3)'
linux /android/kernel quiet acpi=off root=/dev/ram0 androidboot.selinux=permissive buildvariant=userdebug SRC=/android
initrd /android/initrd.img

```


Windows is on sda2.
Primos is on sda3.
Ubuntu is on sda6.

Primeos adds windows to grub.
Ubuntu adds windows to grub.
Primos doesnt add ubuntu to grub.
Ubuntu doesnt add primeos to grub.

It is non UEFI.





It looks like he finds the kernel and wants to start, but after some seconds the device makes a reboot.
At first there was an acpi error, but with acpi=off he is gone.

I cant see any error, because the reboot comes to fast.
Can someone help me?

---

### Post by yancek on 2019-11-20
> It looks like he finds the kernel and wants to start, but after some seconds the device makes a reboot

What are you referring to here?  Is this when you try to boot PrimeOS, when you try to boot Ubuntu or both?  Does Ubuntu not show 'PrimeOS' on screen when you run sudo update-grub?  Not being familiar with PrimeOS, I did an online search and the sites I looked at indicated it was still Beta.  These sites were not current so is it a full non-beta release.  If it's beta, I would expect these sorts of problems. 

If you haven't resolved this issue and you can boot Ubuntu or the Ubuntu install media, you could go to the site below and download and run the boot repair script by selecting the Create BootInfo Summary option and posting the link you get here for members to review and hopefully, give some suggestions.  Do not try to make any reairs.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2019-11-20
I think this was UEFI, but the grub direct boot stanza would not be different, only if chain load to an UEFI entry would be totally different.

[https://ubuntuforums.org/showthread.php?t=2415813](https://ubuntuforums.org/showthread.php?t=2415813)

---

### Post by troneleck on 2019-11-20
1. The first picture shows my handmate entry to grub.
2. The second the normal ubuntu entry.
3. The third picture shows the primeos partiton with his own grub entry and his folder structure.
4. The last one shows wat update-grub finds.

Primos kernel starts to load for a second and then there is a reboot.
It is not EFI.
It is mbr.

Any way i can make like a line by line boot to see at witch point he reboots?

---

### Post by yancek on 2019-11-20
The first 2 images show menu entries expected in Grub2.  The rest of the images show entries from Legacy Grub which has not been used by Ubuntu for 10 years.  Surprised Primeos uses it.  Is that Grub4dos or similar?  Might be best if you an the boot repair script so we have more detail.

What OS can you boot now?

---

### Post by troneleck on 2019-11-20
I can boot right now Ubuntu and Windows.

Wat boot repair script do you talking about?

Got it: [https://paste.ubuntu.com/p/BF3JKcNRT8/](https://paste.ubuntu.com/p/BF3JKcNRT8/)

---

### Post by oldfred on 2019-11-20
Grub does not use boot flag.
But Windows does and if you need to restore Windows boot loader or make Windows repairs, you need boot flag on the Windows partition with boot files, your sda1. You can use gparted to move boot flag.

I had forgotten that grub legacy used different partitioning numbering. Thought at first set root was wrong. (hd0,2) is correct for sda3 with grub legacy, but hd0,3 is correct with grub2.

Back in 2009 when I last used grub legacy to boot multiple installs, I would install grub to the PBR - partition boot sector and chainload from one master grub to all the grub installs, that I manually created.  
You used to be able to convert grub to grub2 when grub2 first came out.
While grub2 is larger & does not like to install to PBR, I might from your PrimeOS install its grub to PBR of sda3l.

If in your Prime OS.
typing "sudo apt-get install grub" is the correct way to install grub legacy (0.97).

I found my old notes, probably will not work with Ubuntu as it now does not have grub, but if Prime OS is live installer you should be able to use it.
To install grub legacy to a partition
1. Boot your computer up with Ubuntu liveCD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,6) or root (hd0,6) Look at output from #4 use (hdx,6)
6. Type "setup (hd1,6) or setup (hd0,6) to put Karmic GRUB 2 on karmic's partition 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Then see if you can chain load from grub2 to grub in partition.
This was a grub entry:

title       Ubuntu 9.04 Jaunty 64 bit @ sdc5
root        (hd2,4)
chainloader +1

This may then work as grub2 chain to hd0,3 (as grub2 sees partition), but may need to be hd0,2 as grub sees partition.

menuentry "Chainload Other Systems Grub Menu on sda3" {
set root=(hd0,3)
chainloader +1
}

---

### Post by troneleck on 2019-11-21
Thx oldfred for your help.

Unfortunately i dont understand wat you wrote.
The only way for me to got primeos run again ,with my knowledge, is to reinstall it and loose the option to boot ubuntu.
I also dont know how to open a terminal in primeos.
I dont have any skills in android...i still use an old Nokia N8 phone...because i can call people with it.....

Do you might have some easer instructions?

---

### Post by oldfred on 2019-11-21
Does PrimeOS give you the option on where to install grub? If so when you reinstall it, choose to put it in the PBR of its partition, not the MBR of the drive. That will leave grub2 from Ubuntu in MBR and not change current boot. 

Then you can boot Ubuntu and see if you can chain load to old grub in PBR of primeOS partition.

---

### Post by troneleck on 2019-11-21
No there is no option to chose where to install it. I just can make partitions but no option for grub like in the Ubuntu install prozess.

---

