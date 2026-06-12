---
title: "Separate boot partition issue"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by gerryg001 on 2010-02-14
GNU GRUB 0.97
Ubuntu 8.04.4
2.6.24-26

Added an SSD (dev/sdc) and decided to move some less often changed directories there. Started with /usr and /boot, leaving / on a primary in the first drive, for now. All started ok, and my changed fstab mounted the right ones, and the system works.

However, grub is actually using the original /boot on / on sda1. I cannot see any way to change this. (Which makes it sorta hard to update the kernel:-)

/dev/sda1 /
/dev/sdc7 /usr
/dev/sdc6 /boot
/dev/sda3 /work
/dev/sda4 /home
/dev/sdb5 /store

From grub:
grub> find /boot/grub/menu.lst
find /boot/grub/menu.lst
 (hd0,0)
 (hd2,5)

Okay, since it has two choices, I tried to tell it which one to use. But,
grub> root (hd2,5)
does nothing.

Disk /dev/sda: 500GB
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  10.0GB  10.0GB  primary   ext3              
 2      10.0GB  113GB   103GB   extended                    
 5      10.0GB  13.0GB  3002MB  logical   linux-swap        
 6      13.0GB  113GB   100GB   logical   ext3              
 3      113GB   428GB   315GB   primary   ext3              
 4      428GB   480GB   52.4GB  primary   ext3  
   
Disk /dev/sdb: 1000GB
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  4195MB  4195MB  primary   fat32             
 2      4195MB  1000GB  996GB   extended                    
 5      4195MB  528GB   524GB   logical   ext3              
 6      528GB   1000GB  472GB   logical   ext3  
 
Disk /dev/sdc: 64.0GB
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  64.0GB  64.0GB  extended                    
 5      64.5kB  2097MB  2097MB  logical   ext3              
 6      2097MB  2517MB  419MB   logical   ext3         boot 
 7      2517MB  23.5GB  21.0GB  logical   ext3              
 
Searching the posts, I see some conflicting comments from others. But, from what I seem to recall, grub doesn't care about the boot flag on the disk. Nor does it care about primary vs. logical (except GNU doc says "makeactive" only works on a primary?).

The GNU doc also indicates that it looks for a directory /boot on the partition, so if you're mounting a partition as /boot, it also needs to contain a /boot directory under it. Tried that, but no change.

Is my problem the logical partition? Does that prevent "grub> root" from changing it? I'm afraid to wipe out the old /boot and find that I can't start up.

---

### Post by johnson.d on 2010-02-15
You can probably try setting the boot flag and try again.

You can set the boot flag using the following procedure
1)$ sudo fdisk /dev/sdc
2)Type a at the fdisk prompt
Command (m for help): a
partition no ( x to y): 6
Command (m for help): w

Exits fdisk after writing the information to harddisk

At the shell prompt
$ partprobe

For proper booting using the new /boot partition you need to edit the /etc/fstab suitably.

You need to have the live cd to rescue the system in case of any booting issues.

---

### Post by gerryg001 on 2010-02-15
Thanks but, as you can see in the data, the boot flag was set (by parted). And, I do not believe that grub uses that boot flag.

Running partprobe only tells the OS to scan for a partition change. It has nothing to do with grub.

The /dev/sdc6 /boot entry shows that I've updated fstab correctly. And, I do have a bootable USB flash if needed.

In the meantime, I unmounted the new boot temporarily, allowing me to update the old one for a new kernel, including changing the old menu.lst for grub. That let me rebuild vmware server so my virtual sessions are now working. At this point, everything is uptodate and working expect for this issue.

The problem appears to be either in the "grub root" command, or in boot being on a logical partition.

---

### Post by darkod on 2010-02-15
You seem to know more about grub than me, but just one thought. Did you check that device.map has a reference for hd2 after the new SSD was added.
The find commands returned (hd2,5) so it seems it does, but it's better to double check. Maybe that's why root(hd2,5) didn't work.

---

### Post by oldfred on 2010-02-15
Unless you have an old computer where the BIOS cannot go beyond a certain point, /boot should work. It does not need a boot flag and as far as I know it can be a logical partition. Did you not reinstall grub to the MBR, it is the last (setup) command:

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)

---

### Post by gerryg001 on 2010-02-15
Been reading on grub, but haven't had to play with it in years, simply because no problems. I've used LILO and written small loaders, but that's very long ago.

More checks are always good. Yes, I had verified device.map at the start.

On [HTML]https://help.ubuntu.com/community/GrubHowto [/HTML] it indicates this should work, but when grub is given two choices for partitions, nothing seems to say how to choose one, other than the root command. That howto talks about changing menu.lst, which I did, but grub's fetching the old one instead. At this point, I may need (sigh) to get the source for grub.

---

### Post by gerryg001 on 2010-02-15
> **oldfred said:**
> Unless you have an old computer where the BIOS cannot go beyond a certain point, /boot should work. It does not need a boot flag and as far as I know it can be a logical partition. Did you not reinstall grub to the MBR, it is the last (setup) command:

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,5)
root (hdx,y) #use the numbers from the previous command x is drive, y is partition
setup (hd0)

This is a new system, with no BIOS issue.
I did the setup command.
Note that "find" returns two partitions.

While I'm sure about the boot flag, I'm concerned as GNU doc says that "makeactive" doesn't work with a logical drive, and I don't understand why.

---

### Post by oldfred on 2010-02-15
The find is giving two locations as your still have grub in both partitions. If you copied all the files from in root  /boot/grub and /boot to your new /boot as /boot/grub in the new partition that should work but you have to now tell grub in the MBR to use that location. You also have to update fstab so your system knows what partition is the boot partition.

Makeactive is a grub command to turn the boot flag on (temporarily) so windows can boot. Windows only boots from the active partition which is the one with a boot flag. Windows will not boot from a logical partition*. You can install windows to a logical partition but its boot files must be in a primary partition so there is no reason to makeactive on a logical partition. (*some may have work arounds to get windows to boot from a logical partition, but is is not easy)

---

### Post by oldfred on 2010-02-15
I did this on my desktop and reinstalled grub and it worked just fine. but I decided I did not want a separate boot partition but just a separate grub partition so I moved all the boot files back except the grub files and installed grub again.

---

### Post by gerryg001 on 2010-02-15
> **oldfred said:**
> I did this on my desktop and reinstalled grub and it worked just fine. but I decided I did not want a separate boot partition but just a separate grub partition so I moved all the boot files back except the grub files and installed grub again.

Are you confirming that the partition containing /boot was a logical partition when you did this??

> Makeactive is a grub command to turn the boot flag on (temporarily) so windows can boot. 
Somewhat true. Both parted and fdisk show the boot flag. However, stopping the boot at grub and dropping to a command line, I tried to "makeactive" each of the two listed partitions, in turn. The (hd0,0) worked but the (hd2,5) gave an error. An error which did not show if done after booting (verbose on). This may be just a purposeful limitation in grub for the reason you gave, or not. This may not have any significance here.

> You also have to update fstab
Which, of course, doesn't have anything to do with grub as it's long gone before fstab mounts. As I showed initially, this was done.

Also, after a quick look at the grub source code, tracing that appears to be a very long tour...

---

### Post by gerryg001 on 2010-02-16
Ah...this is going from bad to worse. I stopped the boot at the grub menu and tried some command line entries. It broke the system, with a "grub error 15: file not found".

So, booted off a USB flash. The partitions were okay. Ran fsck and all okay. Grub was able to find its stuff. Mounted the partition and all looked okay at / /boot and /boot/grub. Tried grub's root and setup, but still "error 15".

Is this MSDOS? If it can't find a file, why not say which file?? Even LILO wasn't that bad. I've done this since before BSD2.3 and Windows 0.9 and this matches some of the early junk.

Tried install-grub also, but no change.

Finally, from the booting grub menu, I started editing the boot entries (why not?). After about a dozen failures, the 2nd time I changed the kernel entry to "/vmlinuz" the system booted. Yes, the first such try didn't boot, it tried but couldn't load the kernel. But with nothing else changed, the 2nd try worked. Why did I try that? Just in case it looked at the root instead of the /boot directory, and it did, finding that link.

Now, as this was a temp change, I ran grub's "root" and "setup" once again. Then update-grub and all looked good (as before). Rebooted, and the system came up fine, using the original entries in menu.lst.

Probably, something was broken in grub's boot data. Something that was not visible and was only fixed by some crazy sequence of attempts. Now, the original problem's still there, but at least the system works again.

So, is there anybody out there who really-really knows grub?

---

### Post by meierfra. on 2010-02-16
To get a better picture of your setup, follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt.

---

### Post by gerryg001 on 2010-02-16
> **meierfra. said:**
> To get a better picture of your setup, follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt.

Thank you. That gives a little more visibility. I found this issue discussed on [HTML]http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/[/HTML] which explained a bit, but he was later corrected by a poster. That tutorial (and the correction there) is a good example of my issue, in that this is basic top-level information that should have been in the GNU docs.

I'm going to play with this together with your script for a little while, to see if I can resolve this. Else, I'll be back.

Thanks again,
Gerry

---

