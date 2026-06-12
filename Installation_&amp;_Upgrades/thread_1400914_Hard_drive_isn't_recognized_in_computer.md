---
title: "Hard drive isn't recognized in computer"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by MWhitman on 2010-02-07
Hello I am building a new computer and everything has went fairly smoothly but I can't seem to get my second hard drive to show up in the computer folder.  It is recognized by hardinfo and it is recognized in the bios.

It's a 1.5T seagate hdd.

I am running 9.10 amd64 on an i7.  I have the operating system installed on a 40 gb solid state.

Any ideas tips?

I've been running ubuntu for a while but this is my first post in the forums.  

thanks!

---

### Post by pirateghost on 2010-02-07
> **MWhitman said:**
> Hello I am building a new computer and everything has went fairly smoothly but I can't seem to get my second hard drive to show up in the computer folder.  It is recognized by hardinfo and it is recognized in the bios.

It's a 1.5T seagate hdd.

I am running 9.10 amd64 on an i7.  I have the operating system installed on a 40 gb solid state.

Any ideas tips?

I've been running ubuntu for a while but this is my first post in the forums.  

thanks!
have you run gparted to see if it shows up?
does it have a partition on it?
has it been formatted with a filesystem yet?

---

### Post by darkod on 2010-02-07
Yes, Gparted should show it even if it's brand new unpartitioned.
Otherwise, if you expect to see it in Places I think it must have partitions on it (filesystem). You can create them with Gparted.

On a side note, how are you satisfied with the SSD? I'm considering getting one. Can you share the model please. Put it in PM if you want, or here.

---

### Post by MWhitman on 2010-02-07
[FONT=Arial][SIZE=2]I just ran gparted and the 1.5T drive does show up.  I just spent a few minutes working with gparted but still can't seem to get the drive into my file system.

As far as the SDD model number goes-
[/SIZE][/FONT]**[FONT=Arial][SIZE=2][COLOR=Black]Intel X25-V SSDSA2MP040G2R5 2.5" 40GB SATA II MLC Internal Solid State Drive (SSD)[/COLOR][/SIZE][/FONT]**

I starting building this machine last weekend and just got it running on Thursday night but so far so good with the SSD.  My two worries were that it would be too small, and that it would have too short a life span.  Boot time is great, I haven't had time yet to run benchmarks but I can send you some of that info when I do.

---

### Post by darkod on 2010-02-07
If you're not used to Gparted, take into account the following: All actions you select are only scheduled at first. You can see them pile up at the bottom. Nothing is executed until you click the big green tick mark button in the toolbar. To give you a chance to change your mind.
So, for example if you try to create a partition and you just close Gparted, nothing will happen.
Also, depending which actions you select, do them in two stages sometimes. For example, I always delete partition first, and execute with the green button, and then create a new one, just to make sure Gparted won't mess anything up deleting a partition and creating a new one in the same place. Although it should be able to do it in one step too.

After you create at least one partition on the hdd (ntfs or ext4, doesn't matter), you should be able to see it in Places. You will have to mount it first in order to use it. Just clicking on it in Places will ask your ubuntu password and mount it.

---

### Post by MWhitman on 2010-02-07
Thanks for the help I got the HDD up and going.  I appreciate it

---

### Post by root23 on 2010-02-13
I have a similar problem. I'm booting Xubuntu off of a flash drive, and my main computer hard drive doesn't show up. It is formatted, with a filesystem. It would show up no problem when booting Fedora 12 off the flash.

It also shows up in Gparted... 

Ideas?

---

### Post by darkod on 2010-02-13
> **root23 said:**
> I have a similar problem. I'm booting Xubuntu off of a flash drive, and my main computer hard drive doesn't show up. It is formatted, with a filesystem. It would show up no problem when booting Fedora 12 off the flash.

It also shows up in Gparted... 

Ideas?

If you are NOT running raid, boot the live desktop and in terminal do:

sudo fdisk -l

first to check if your hdd is /dev/sda. If it is, proceed with:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

If it's called other than /dev/sda just use the hdd name what ever it is. That should get rid of raid settings on the hdd which is most often the reason for this.

If you ARE running raid DON'T run these commands because they will destroy the array.

---

### Post by root23 on 2010-02-13
Thanks for the quick reply.

I tried this with no luck. It told me no RAID existed on sda, but I continue with the apt-get remove dmraid anyways. The HDD still wasn't showing up, so I rebooted. Instead of booting me back into Xubuntu, it booted XP off the hard drive instead.

-edit-
I couldn't access the flash drive when booted into Windows. It would show up in My Computer, but wouldn't open when clicking. After unplugging, and then reinserting it everything is back to normal. I booted back into Xubuntu, but the HDD still isn't showing.

> **darkod said:**
> If you are NOT running raid, boot the live desktop and in terminal do:

sudo fdisk -l

first to check if your hdd is /dev/sda. If it is, proceed with:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

If it's called other than /dev/sda just use the hdd name what ever it is. That should get rid of raid settings on the hdd which is most often the reason for this.

If you ARE running raid DON'T run these commands because they will destroy the array.

---

### Post by MWhitman on 2010-02-13
Are the file systems formatted the same for Xubuntu and Fedora?  The issue that I was having turned out to be a formatting issue.

---

### Post by root23 on 2010-02-13
Well... Fedora was on the flash drive previously. And when booting Fedora from that my computer hard drive (With WinXP) would show up in Places.

Now I've replaced Fedora with Xubuntu on the flash drive, but I can no longer see the computers hard drive in Places.

The hdd partition is formatted ntfs, and I'm not sure what the Xubuntu is. I used the Live USB creator to make it, and don't remember what file system I chose.

---

