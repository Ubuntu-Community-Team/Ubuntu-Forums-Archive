---
title: "Luks based harddisk encryption on Gutsy Gibbon"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Birnenstein on 2007-10-25
The Luks based harddisk encryption (see [https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller](https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller)) worked fine for me under Feisty.

I built now a system from scratch following the procedure accurately and all looks fine to me. menu.lst in /boot/grub looks ok.

After booting fine and enter the correct password after the Luks passphrase prompt I get:

[ 11.140000] device-mapper: ioct1: unable to remove open device temporary-cryptsetup-2321
key slot 0 unlocked
Command successful
Done.
Begin: Waiting for root file system... ...

Done.

Check root=bootarg cat /proc/cmdline
or missing modules, devices: cat / proc/modules ls /dev
ALERT! /dev/mapper/root does not exist. Dropping to a shell !

After that I get the busybox


Any help appreciated.
Thanks

---

### Post by kuadra on 2008-02-11
Hi Birnenstein,

I've used the same howto today, and have encountered the same problem.
There seems to have been a change of terms between **root** and **cryptroot**.

When you've been dropped to the shell after an unsuccessful mount, you can take a look into */dev/mapper/*, and if you also see */dev/mapper/cryptroot*, then you've encountered the same problem as I have. That means that the partition has successfully been opened, but that the boot process is looking for */dev/mapper/root* instead.

In my case, I had to change **root** to **cryptroot** in */etc/crypttab* and in */etc/initramfs-tools/conf.d/cryptroot*.
After that, the system boots (almost) flawlessly.

The only strange behavior is that I have to hit the Enter button when the system wants to decrypt the remaining partitions, because at the moment I've only an additional swap which is been encrypted with a random key on every boot (just like in the original howto).

Hope it helps! (if it's not to late :) )

---

### Post by ericus on 2008-03-23
I have the same problem as the first poster, and I've tried what the post above me suggested, but it's not working.

Any ideas? This has been giving me a headache for several days now.

---

### Post by xivor on 2008-03-27
Hi ericus,

I followed the same howto, and then the advices from kuadra, and it worked for me.
There is only one thing kuadra did not mention. I needed to change the "root=" in Grub from */dev/mapper/root* to */dev/mapper/cryptroot* as well.

I did it at boot time, the first time, and then updated the Grub install once in the system.

---

### Post by honeydew on 2008-03-27
is there a reason for not using the ubuntu method of luks encrypting your hard disks? it is available when you are partitioning either with the alternate.ISO or the server.ISO...

quick reference: [http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml)

---

### Post by xivor on 2008-03-28
No, except that at the time of my test I only had the desktop 64bits ISO, and a very bad/overloaded connection to the Internet.

Actually, the Ubuntu method is better as it doesn't break the boot spash.

---

