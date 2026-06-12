---
title: "error messages on Xubuntu startup"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2015-11-08
I get the following lines of text each time I boot into Xubuntu.  The present version is 15.04 but this has been coming up for some time.
[   0.971324] ACPI  PCC probe failed.
starting version 219
error: /dev/sdd: No medium found
error: /dev/ade: No medium found
error: /dev/sdd: Mo medium found
error: /dev/sde: No medium found

Is there a way to fix this or simply stop it from coming up?  Thanks in advance for any replies.

---

### Post by matt_symes on 2015-11-08
Hi

> **archp2009 said:**
> I get the following lines of text each time I boot into Xubuntu.  The present version is 15.04 but this has been coming up for some time.
[   0.971324] ACPI  PCC probe failed.
starting version 219
error: /dev/sdd: No medium found
error: /dev/ade: No medium found
error: /dev/sdd: Mo medium found
error: /dev/sde: No medium found

Is there a way to fix this or simply stop it from coming up?  Thanks in advance for any replies.

What type of devices are /dev/sdd and /dev/sde ? Are they smart card readers or CD/DVD drives with no media in them ?

When did you start getting these messages ?

Do you have hibernation enabled currently ? Have you previously had hibernation enabled on this installation (maybe before an upgrade) ?

Can you post the output of these command.

```
cat /etc/initramfs-tools/conf.d/resume
```

```
sudo blkid
```

Kind regards

---

### Post by archp2009 on 2015-11-24
```
arch@arch-System-Product-Name:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=bd4bcbc1-1222-477c-ac94-e476dfa67387
```

 
```
/dev/sda1: LABEL="XP" UUID="785CD0D55CD08F6E" TYPE="ntfs" PARTUUID="5d7d47e1-01"
/dev/sda2: LABEL="Vistax86" UUID="E4843BCF843BA2CA" TYPE="ntfs" PARTUUID="5d7d47e1-02"
/dev/sda3: LABEL="Vistax64" UUID="449EDDDE9EDDC896" TYPE="ntfs" PARTUUID="5d7d47e1-03"
/dev/sda5: LABEL="Movies3" UUID="E666AD6166AD336B" TYPE="ntfs" PARTUUID="5d7d47e1-05"
/dev/sdb1: LABEL="Win7x64" UUID="01CF04BEB8434F30" TYPE="ntfs" PARTUUID="c4102f2e-01"
/dev/sdb2: LABEL="Win8x64" UUID="01CF04BECFD7FDD0" TYPE="ntfs" PARTUUID="c4102f2e-02"
/dev/sdb3: LABEL="Win8.1x64" UUID="34AACC96AACC55D0" TYPE="ntfs" PARTUUID="c4102f2e-03"
/dev/sdb5: LABEL="Movies 7" UUID="E888111B8810EA38" TYPE="ntfs" PARTUUID="c4102f2e-05"
/dev/sdb6: LABEL="Win10_Tech_Preview" UUID="01D049792722B1C0" TYPE="ntfs" PARTUUID="c4102f2e-06"
/dev/sdb7: LABEL="Movies2" UUID="01CF02688A26B2C0" TYPE="ntfs" PARTUUID="c4102f2e-07"
/dev/sdc1: LABEL="Mint 16 Mate" UUID="c2e3561e-43ab-4f30-8539-3af7debd3b86" TYPE="ext3" PARTUUID="2b7fa170-01"
/dev/sdc5: UUID="145d8c4a-2c75-4488-9e1c-74732e894bb4" TYPE="swap" PARTUUID="2b7fa170-05"
/dev/sdc6: LABEL="Ubuntu 14.04" UUID="f9a6f367-560c-4129-9e15-6d0db3decc82" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="2b7fa170-06"
/dev/sdc7: LABEL="Ubuntu Studio 14" UUID="ce7ca6d2-5fc5-44fe-9be1-0d47c5085462" TYPE="ext4" PARTUUID="2b7fa170-07"
/dev/sdc8: LABEL="Kubuntu 14.04" UUID="84f77526-b1f4-4f7b-90dc-01724cc58643" TYPE="ext4" PARTUUID="2b7fa170-08"
/dev/sdc9: LABEL="Xubuntu 14.04" UUID="2be260ac-82c6-4c7b-bb87-10d20c981e66" TYPE="ext4" PARTUUID="2b7fa170-09"
/dev/sdc10: LABEL="Lubuntu 14.04" UUID="957157e2-82de-446f-bb71-0970c79b26d8" TYPE="ext4" PARTUUID="2b7fa170-0a"
/dev/sdc11: LABEL="OpenSuse13_2" UUID="cfd3987e-ab29-4be1-8581-3fcc49fc707e" TYPE="ext4" PARTUUID="2b7fa170-0b"
/dev/sdc12: LABEL="Zorin 9 Ultimate" UUID="3abb653d-5db0-4ba3-a214-1507011546b6" TYPE="ext4" PARTUUID="2b7fa170-0c"
/dev/sdc13: LABEL="Edubuntu 14.04" UUID="9d37d916-0646-4309-8a7c-68e3356ee668" TYPE="ext4" PARTUUID="2b7fa170-0d"
/dev/sdc14: LABEL="Mint 17" UUID="247df315-2a74-4dbf-8995-9d69fde2290d" TYPE="ext4" PARTUUID="2b7fa170-0e"
/dev/sdc15: LABEL="Ubuntu Gnome" UUID="7e034abc-3d2a-48d4-89f4-f25d102ed149" TYPE="ext4" PARTUUID="2b7fa170-0f"
/dev/sdc16: LABEL="Ubuntu Mate" UUID="817e8910-2d7a-4189-b170-dcde1c5cb961" TYPE="ext4" PARTUUID="2b7fa170-10"
/dev/sdc17: LABEL="Deepin" UUID="e8707674-5ac9-42b6-94f3-93f13393d1de" TYPE="ext4" PARTUUID="2b7fa170-11"
/dev/sdc18: LABEL="Elementary OS" UUID="0930cbc4-4511-418c-9e43-468c89755705" TYPE="ext4" PARTUUID="2b7fa170-12"
/dev/sdc19: LABEL="Movies6" UUID="01CEE7D7530CB650" TYPE="ntfs" PARTUUID="2b7fa170-13"
/dev/sdc20: LABEL="Debian 7_8_0" UUID="89f9dff8-91dc-4dd3-a012-f78f598f71a4" TYPE="ext4" PARTUUID="2b7fa170-14"
arch@arch-System-Product-Name:~$ 
```

Gparted does not show any partition higher than sdc.  Shows can't have overlapping partitions, though.

---

### Post by matt_symes on 2015-11-24
Hi

I don't think the messages are problematic. 

I thought they might be coming from initramfs and/or systemd-udevd but i'm running 14.04 still so have not seen any issues like this. Actually not seen them on a test rig that i have been using.

> Is there a way to fix this or simply stop it from coming up? Thanks in advance for any replies. 

You could lower the kernel log level and they may disappear.

From kernel-parameters.txt in the kernel sources documentation. 

> loglevel=       All Kernel Messages with a loglevel smaller than the
                    console loglevel will be printed to the console. It can
                    also be changed with klogd or other programs. The
                    loglevels are defined as follows:

                    0 (KERN_EMERG)          system is unusable
                    1 (KERN_ALERT)          action must be taken immediately
                    2 (KERN_CRIT)           critical conditions
                    3 (KERN_ERR)            error conditions
                    4 (KERN_WARNING)        warning conditions
                    5 (KERN_NOTICE)         normal but significant condition
                    6 (KERN_INFO)           informational
                    7 (KERN_DEBUG)          debug-level messages

It defaults to 4.
```

matthew-laptop:/home/matthew:1 % cat  /proc/sys/kernel/printk
4       4       1       7
matthew-laptop:/home/matthew:1 
```

You could lower it to 3 by setting the loglevel kernel parameter using your favourite editor. 

```
sudo nano /etc/default/grub
```

# Remove quiet and add loglevel=3

```
GRUB_CMDLINE_LINUX_DEFAULT="splash loglevel=3"
```

and then 

```
sudo update-grub
```

See if that stops the messages after a reboot.

**EDIT:**

You could try a lower level than 3 but you'll start to miss important messages.

Kind regards

---

