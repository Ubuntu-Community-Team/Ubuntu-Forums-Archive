---
title: "Completely clear hard drive"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by saltydogs on 2009-12-29
Hello all! Son wants to sell laptop to a college friend, but he wants to sell it without anything on the hard drive. No files, drivers, operating system, nothing! Wipe it clean.
How does he go about this?
The hard drive currently has Ubuntu 9.10

---

### Post by taurus on 2009-12-29
Boot with Ubuntu LiveCD.  Then, open gparted (System -> Administration) and unmount the swap partition (you would see a double-key in front of that partition).  Once everything is unmounted, delete all the partitions from the harddrive and format it to fat32 filesystem.  

Now, his friend can install whatever he/she wants on an empty harddrive.

---

### Post by phillw on 2009-12-29
I'm a little less trusting..

Boot with LiveCD
Mount the drive

```
ls /dev/sd?
```

that will list all devices, and partitions - **make sure you get the correct disk if you have more than one in the machine**
You're looking for **sda** if it's the only disk in the machine - if you have more than one, or it is an external disk - make sure you select the correct one !!!

```
sudo dd if=/dev/random of=/dev/sdX
```  Where X is the letter of the drive to be erased - Once issued, there is **no** second chance.

After that, you can partition it up with FAT32.

Depends how 'deleted' you want the disk to be whether you use the dd on it first.

Regards,

Phill.

---

### Post by oldfred on 2009-12-29
Why not reinstall a new copy of Ubuntu to help promote the use of Ubuntu?

---

### Post by saltydogs on 2009-12-29
Thanks for the responses! I rebooted with Live CD and chose "Try Unbuntu without any changes". I opened GParted and found 3 separate partitions:
/dev/sda1                     ext4            73.11 GiB size  3.57 GiB  69.54 GiB     boot
/dev/sda2 (double-key)  extended    1.42 GiB size 
/dev/sda5 (double-key)  linux-swap  1.42 Gib size

Under the "Partition" tab;
Unmount is not available to choose in either /dev/sda partitions, although the /dev/sda5 has Swapoff available to choose.

I am a newbie with all of this, so I don't understand what you mean with;

"Mount the drive"

or;
 	Code:
 	sudo dd if=/dev/random of=/dev/sdX 
or;

"Where X is the letter of the drive to be erased"
"After that, you can partition it up with FAT32"
What does all that mean?

I want the hard drive completely empty.

---

### Post by taurus on 2009-12-29
Swapoff is what you have to run to unmount the swap partition.  Then, click the last partition and remove it.  Then move on the next one until the whole harddrive is unallocated.

---

### Post by saltydogs on 2009-12-30
I clicked "Swapoff' and got a "Could Not Deactivate Swap" message. So that didn't work.

Am I supposed to choose "Try Ubuntu without any changes" when the computer boots with the LiveCD?

---

### Post by saltydogs on 2009-12-30
I did another LiveCD reboot and went through the hard drive cleaning process with sucess. I decided to reboot (without LiveCD) just to take a look at what was there, if anything. 
I now get a 
"Grub Loading" message, followed by 
error: no such partition
grub rescue>_ 
 
How do I remove that error message?
And how do I get the Grub loader off of the hard drive?

---

### Post by saltydogs on 2009-12-30
Another boot with the LiveCD, then to GParted resulted in 1 drive;
 
/dev/sda  unallocated  74.53 GiB
 
But I cannot do any sort of unmount, format, manage flags, etc.
 
I don't want to sell this kid a computer with anything on the hard drive, no unallocated partitions, no grub error on boot, nothing. Just a blank hard drive!

---

### Post by phillw on 2009-12-30
> **saltydogs said:**
> Another boot with the LiveCD, then to GParted resulted in 1 drive;
 
/dev/sda  unallocated  74.53 GiB
 
But I cannot do any sort of unmount, format, manage flags, etc.
 
I don't want to sell this kid a computer with anything on the hard drive, no unallocated partitions, no grub error on boot, nothing. Just a blank hard drive!

Hi

Unallocated = no partitions, no file system aka blank hard drive :)

It *is* possible to recover after deleting partitions, but it's a lot of work

You could, as previously noted allocate the entire disk as one partition of FAT32 - It'll make it a bit easier on the recipient. Don't forget to include a CD with the Version of Ubuntu you were running on the computer - That way the recipient *may* just be tempted to 'give it a go' - As you know it works with the computer.

Regards,

Phill.

Phill.

---

### Post by saltydogs on 2009-12-30
Hi Phillw, thanks for the reply.
 
*Unallocated = no partitions, no file system aka blank hard drive *:smile: I still don't understand why, when I boot the PC, the "Grub Loading" message comes up. Why is my boot sequence trying to access Grub? Is the Grub loader in my BIOS memory?
How do I remove Grub, and any access to it, from my computer? 
I would be upset if I bought a computer and a Grub error message came up before I even load any sort of Operating System. The person buying the computer has the right to install whichever OS they desire.
Do I have to go out and buy a brand new hard drive to replace the "Grub Infested" one currently installed?

---

### Post by audiomick on 2009-12-30
What you are seeing is in the Master Boot Record of the drive, as far as I know. Installing any OS will overwrite that, i.e. it will be gone as soon as the buyer installs an OS. If it were a windows machine with a wiped drive, I am pretty sure you would be seeing "I can't boot windows" errors.


The Ubuntu install, which you said was 9.10, presumably had grub 2 as a boot loader. Is this true?

You could try this. It is derived from the "uninstalling" instructions from here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Boot into the live CD

do
```
sudo apt-get purge grub2 grub-pc
```
in a terminal.

I **_do not know_** if this will really work, but my logic says it should.

---

### Post by J V on 2009-12-30
> **phillw said:**
> ```
sudo dd if=/dev/random of=/dev/sdX
```
can't you just use the shred command?

```
sudo shred -fxz /dev/sdX
```

---

### Post by jml on 2009-12-30
If you are really paranoid, you could do a full disc erase/overwrite procedure.  This process literally writes data to the entire disc then "erases" it. This renders the old data virtually unreadable except for groups like the NSA.  There are several companies that sell software to do this, along with companies that offer free versions.  Here is a link to one that I "Googled"  I also agree with including a copy of Ubuntu with the wiped computer.

[http://www.killdisk.com/features.htm](http://www.killdisk.com/features.htm)

Joe

---

### Post by audiomick on 2010-01-02
Hi.
I think this thread has gone to sleep, but I just found this
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
in another thread here. It deals with removing Ubuntu and Grub.
I thought I would add it here in case someone turns up this thread in a search.

---

### Post by Cheesemill on 2010-01-02
I always use a dban CD to wipe my hard drives:
[http://www.dban.org/](http://www.dban.org/)

---

