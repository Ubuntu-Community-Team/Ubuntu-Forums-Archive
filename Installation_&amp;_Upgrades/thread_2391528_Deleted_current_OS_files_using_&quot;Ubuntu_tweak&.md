---
title: "Deleted current OS files using &quot;Ubuntu tweak&quot; app + hard disk partition encrypted"
date: 2018-05-10
forum: Installation &amp; Upgrades
---

### Post by clovisdecruz on 2018-05-10
I reckon I have buggered up my Ubuntu (16.04 64bit) running laptop. I ran the Ubuntu Tweak application and I must have deleted the current OS files because now under "Advanced  Options" option in GNU GRUB I can only select:

Ubntu, with Linux 4.4.0-124-generic
Ubntu, with Linux 4.4.0-124-generic (upstart)
Ubntu, with Linux 4.4.0-124-generic (recovery mode)

And to make matters ****ing worse, I had enabled encryption on the hard disk partition.

 Is there any point in downloading the 16.04 OS and trying to boot from it and install it on my laptop? Or should I just replaced the HDD and buy a copy of Windows 10 because I too ****ing stupid to use Linux?

---

### Post by Impavidus on 2018-05-10
So... 4.4.0-124 is the current kernel for Ubuntu 16.04. You don't have a spare one, like 4.4.0-122, but if 4.4.0-124 works, that's no immediate problem. You may have uninstalled an old kernel too many. Can you boot Ubuntu using kernel 4.4.0-124?

---

### Post by clovisdecruz on 2018-05-10
I have the 122 as well. When I select the "[COLOR=#000000]Ubuntu, with Linux 4.4.0-124-generic" option I get the:

(initramfs) prompt[/COLOR]

---

### Post by oldfred on 2018-05-10
If encrypted be sure to manually mount the encrypted partition. Otherwise report or any repairs will not work as some necessary info is inside the encryption.

 Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

If using encryption with either Ubuntu or Windows you must have a very good backup plan. And run it regularly as once encryption gets an issue, you may not be able to repair it.
And reinstalling Ubuntu is very quick, Reinstalling Windows is a long process with many reboots.

---

### Post by clovisdecruz on 2018-05-10
Do you know how I should "manually mount the encrypted partition" or disable the encryption using the command line? 

I'm not sure if I should "repair" the boot as I'm not sure if it is "broken". As said before I ran the "Ubuntu tweak" application with the intention of freeing up space as my software updater required. The software update message dialog box did display the suggested line command to free up space but I preceded to use the application as I has done previously. I have been using this laptop after 3 or 4 years and I think I forgot the guideline when using the "Ubuntu tweak" app.

Should I try booting the laptop from an newer Ubuntu 18.04 LTS bootable CD or 16.04 CD and try installing the OS instead of concentrating on disabling the partition encryption or trying to recover the 16.04 OS which I believe to be deleted?

Edit: when I try to run the:

**cryptsetup luksOpen /dev/sda5/ crypthome**

as suggested in [https://evilshit.wordpress.com/2012/10/29/how-to-mount-luks-encrypted-partitions-manually/](https://evilshit.wordpress.com/2012/10/29/how-to-mount-luks-encrypted-partitions-manually/)

I get the reply 

[B]/bin/sh: cryptsetup: not found


[/B]so it looks like the cryptsetup program is not available in this BusyBox v1.22.1... thingie

Latest Edit:
I have downloaded the Ubuntu 18.04 LTS and burned the .iso file on a DVD. I have booted from it and am currently installing 18.04. Right now the setup program is Copying files...

---

### Post by oldfred on 2018-05-10
By installing a new system, you probably have destroyed any chance of recovering data.
Encryption uses LVM which is volume management, and advanced partitioning system.

---

### Post by clovisdecruz on 2018-05-10
Well I took the chance because I did not keep any "important" data on the laptop containing the Ubuntu OS. I do have another computer, a desktop running Windows 10 with One Drive and Google drive so I have already "protected" my important files. I am using Ubuntu on this laptop because I transferred the Windows 7 license that came with it to my dad's computer replacing his old Windows XP license.

Since I am not well versed with Ubuntu (being raised on the comfortable Windows OS GUI) I don't use it for important work just casual browsing mostly. Also I am bit of an imbecile. I cannot tell now what is the status on my laptop i.e. has the so called encrypted partition been deleted. Clearly all the files from my previous home folder is no more. I can't tell because I am used to using Microsoft file explorer to view folders... permanent noob.

Anyways the problem that started this was the Ubuntu OS updater declaring that there is no space and (as I stated before) the culprit that started this mess was the Ubuntu tweak utility which allows an inexperienced imbecile to delete his currently running OS.

---

### Post by Impavidus on 2018-05-11
Most likely you ran out of space in your unencrypted /boot partition. Encrypted systems need an unencrypted /boot partition, which contains amongst other things the code necessary to decrypt the rest of the system. The installer can create this /boot partition automatically, but may make it a bit small. Without adequate cleaning, it may get full.

When you try to do things the developers hadn't foreseen, you may be either an imbecile or a genius. In Linux, it's policy to assume the latter and allow you to proceed. If you are, in fact, not a genius, that may break your system.

Making a fresh install is a common way to solve problems. Could you mark this thread as solved? Tread tools (near top of page) &#8594; mark as solved.

---

