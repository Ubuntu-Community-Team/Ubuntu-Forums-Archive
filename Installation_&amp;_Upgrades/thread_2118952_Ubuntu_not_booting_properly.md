---
title: "Ubuntu not booting properly"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by readypembroke on 2013-02-22
When I boot Ubuntu which is on the same HDD as Windows XP, I get a screen with a message. What can I do to fix this as I want to get Tux for Team Fortress 2. [IMG]http://i1086.photobucket.com/albums/j460/readypembroke/null_zps74933a7a.jpg[/IMG]

---

### Post by MAFoElffen on 2013-02-23
> **readypembroke said:**
> What can I do to fix this.
Says you are missing modules... because those modules define how to see devices such as hard disks, it is not able to see where the kernel is to load.

Do this:
```

cat /proc/modules

```
Which will display all the modules that initramfs uses. What we need to look for are ide, ata, sata modules, which are used to initialize disks.

If there is missing modules, then there must have been an update that updated the kernel. 

The easiest way I know to correct this would be to reboot and at the Grub menu, select the last previous kernel and boot from that one. You should be able to boot from that (It ran before the update). After boot:
```

ls -l /boot/initrd*

```
From the output of that command, you should see a file initrd.img which is linked to the most recent initrd kernel version image. Of that last version, there should be two copies- an original and it's backup copy (appended as .backup) Compare the sizes of these two files. If different, there was a problem creating it. Write that version name down (after "initrd.img-").

Using that version name, substitute that name for "version" in the following command:
```

sudo update-initramfs -c -k _version_

```

---

### Post by bogan on 2013-02-23
Hi!, MAFoElffen,

I do not have the OP's problem at the moment, but have often had it in the past; exactly the same initramfs prompt, and suggested causes, but without all the garbage filling.

In my case the causes - and cures - were either incorrect or corrupted Grub menu scripts, incorrect UUID's, or BIOS boot selection to a different drive, or a removable drive plugged into a different port, resulting in, for example, what had been sdb7 being mounted as sdf7, or just that a removable disk/USB was not plugged in, or had a bad contact.

As a matter of interest, when I entered 'cat /proc/modules', it showed 40 items but none of those you mentioned: ide, ata, sata, nor anything recognizable as disk related.

Chao!, bogan.

---

### Post by readypembroke on 2013-02-24
> **MAFoElffen said:**
> Says you are missing modules... because those modules define how to see devices such as hard disks, it is not able to see where the kernel is to load.

Do this:
```

cat /proc/modules

```
Which will display all the modules that initramfs uses. What we need to look for are ide, ata, sata modules, which are used to initialize disks.

If there is missing modules, then there must have been an update that updated the kernel. 

The easiest way I know to correct this would be to reboot and at the Grub menu, select the last previous kernel and boot from that one. You should be able to boot from that (It ran before the update). After boot:
```

ls -l /boot/initrd*

```
From the output of that command, you should see a file initrd.img which is linked to the most recent initrd kernel version image. Of that last version, there should be two copies- an original and it's backup copy (appended as .backup) Compare the sizes of these two files. If different, there was a problem creating it. Write that version name down (after "initrd.img-").

Using that version name, substitute that name for "version" in the following command:
```

sudo update-initramfs -c -k _version_

```

Thanks, I will try to do what you said to do. When I installed Ubuntu on my brothers computer, there was no problems.

---

