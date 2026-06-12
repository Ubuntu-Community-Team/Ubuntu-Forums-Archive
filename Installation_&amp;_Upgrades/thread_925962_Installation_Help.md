---
title: "Installation Help"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by thomashw on 2008-09-21
I was attempting to install Ubuntu onto an IDE drive to dual-boot it with Windows XP Pro which is already installed on a SATA drive.

When I first installed Ubuntu, the option to install the boot loader came up. I wanted to replace the Windows MBR with GRUB, but there were two choices listed for the Windows XP drive. The first one was just sda, and the second one was sda1 - Windows XP Professional. I chose the sda1 option (Note - I have never partitioned this drive, it has always been dedicated to this Windows install.)

Once the install was done, I chose the SATA drive to boot first, and all that came up while booting was a DOS type command prompt such as GRUB > and it stopped there. It told me to press tab to see a list of commands if I wanted to, which I did. I couldn't really do anything, and ended up reinstalling Ubuntu on the same drive (sdc,) and chose sda instead of sda1 for GRUB this time. The actual GRUB GUI comes up now, but Windows isn't listed.

I tried adding:

title Windows XP
root (hd0,0)
makeactive
chainloader +1

but when I choose it it just brings the GRUB GUI back up again.

I then tried using Super Grub Disk, which didn't help. I did find out that it's now listing my SATA drive as drive sdc instead of sda, but in Ubuntu it still lists it as sda.

Anyone have any suggestions? I am quite lost as to what to do.

---

### Post by Bucky Ball on 2008-09-21
Probably the Ubuntu grub is reading the IDE drive as first up and the SATA as second. You might need to manipulate what you added. Try: 

title Windows XP
root **(hd2,*)**
**savedefault**
makeactive
chainloader +1

sda = hd0, sdb = hd1 so ... the * is the partition it is on so you need to know that. Try entering this command in a terminal:

**sudo blkid**

That will let you know what is in there. Post it here if you have no luck. You have added the code you posted in this file? 

**nano /boot/grub/menu.lst**

That might work. Let us know and welcome to the forums. :)

Update: After rereading, pretty sure the first install on sda1 (if it was telling you Windows XP) might have written over the Windoze MBR (master boot record) so maybe post the results of this from a terminal:

**sudo fdisk -l**

---

### Post by thomashw on 2008-09-21
I've tried editing the menu.lst file using what I wrote as well as a few other things that I found on the internet. The farthest I could get it to boot into the Windows drive was getting to to give me a "command-prompt" type thing. It would say GRUB > and that's it.

Here are the results from the fdisk -l. Note the sda drive has the Windows I'm using on it, the sdb an old Windows I don't use, and the sdc has the Ubuntu linux install.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd962968b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30473047

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0592c9c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Thank you for helping me!

---

### Post by Bucky Ball on 2008-09-21
And it looks like they are all set to boot, primary partitions possibly with MBRs or a Grub! There's that * again.

At a guess I'd say you now have your Grub on sda1 from the first install. Note how it has dropped the SATA drive last with linux on it.

sda and sdb are single partitions. To dual boot, you would normally to set up some free space for those three partitions you have on sdc1, 2 and 5 to go if you follow me. Try this - you can get to the grub menu screen, right? Where you can choose the OS. Well, arrow down to your windows one and hit 'e' to edit it.

You should now be able to exeriment with editing just the grub. Don't worry too much about the menu.lst edit cos that will make it permanent. See if you can get it from here first and if it works then change menu.lst ...

title Windows XP
root **(hd0,0)**
**savedefault**
makeactive
chainloader +1

Change it back to this. I realise now that hd2,0 would in fact be your Ubuntu partition so change that, please. Hit 'b' to boot your changes and try them out.

ps: I am assuming Ubuntu 8.0.4 and can you actually boot into Ubuntu?

---

### Post by thomashw on 2008-09-21
I edited the Windows XP selection with what you said, and when I press 'b' to boot the screen goes black  for a second and then it goes back to the GRUB menu listing Ubuntu and Windows XP.

Also note I can boot into Ubuntu just fine, but Windows I can't. I booted into Windows on a different drive and looked at the sda drive, and it said it was a Master Boot Record. Also I can't see the sda drive in Linux unless I use the fdisk -l command (can't see it in the file manager.)

---

### Post by Bucky Ball on 2008-09-21
In Ubuntu, could you go to System->Admin->Partition Editor. You can have a look in there more easily. If you can't find it, open a terminal and:

**sudo apt-get install gparted**

then:

**sudo gparted**

I'm figuring you are booting into Ubuntu from your grub on sda1 now but I could be wrong. This would mean you would need to rewrite the MBR there or fix. It also means you would need to put grub back on the Ubuntu drive. 

In a terminal:

**sudo mount /dev/sda1**

should mount your Windows partition so you can look at it. On that drive, look for a file called boot.ini

---

### Post by thomashw on 2008-09-21
For the sda drive (in gparted) it says: 

Filesystem: ntfs
Size: 298.08 GiB
Flags: boot
Path: /dev/sda1
Status: Not Mounted
First sector: 63
Last sector: 625121279
Total sectors: 625121217

There is also a warning at the bottom, stating "Unable to read the contents of this filesystem! Because of this some operations may be unavailable."

When I tried to mount it via the terminal it says, "mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab."

Thank you for the help so far!

---

### Post by thomashw on 2008-09-21
I just used a program called NTFS-config to try to mount the drive, but it isn't listed. When I go into my other install of Windows, it says the drives type is MBR (Master Boot Record.) It's not seeing my drive as an NTFS drive anymore, but it seeing the whole drive as a MBR.

BUT, when I use fdisk -l in my terminal, it says it's an NTFS drive.

What can I do?

---

### Post by Bucky Ball on 2008-09-21
Sorry, had to sleep!

Well, I would trust what Ubuntu is telling you as NTFS is a MS guarded secret from their brains trust and takes a bit of digging. You can boot into that version of Windoze that it is telling you is all MBR from memory so all good there. As I mentioned, I am pretty sure you have wiped the MBR of the first Windoze install (the one you want to use) and replaced it with Grub in an earlier step. NTFS-config is perhaps not recognising this therefore reporting that it is not a drive at all.

This is where my expertise becomes a little thin. But try this:

**sudo blkid**

in a terminal and post the result back here. If we can mount that drive we can find if it has a boot.ini file on it and then possibly fix. There is valuable data on this disk or just a neat Windoze customisation?

---

