---
title: "I am at my wit's end with Ubuntu 12.04 install on a AMD64"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2012-05-04
This time, I went throught the entire lengthy installation process and received absolutely **no error messages whatsoever.**

It said that 12.04 was installed, and I followed the prompts to reboot and did not remove the installation disk until I was told to do so. It rebooted, and what came up?

[SIZE="4"]**My old Ubuntu 11.10!!!**[/SIZE] I suppose that I should be grateful that I didn't delete 11.10, but ---

Where does one go from here?

---

### Post by darkod on 2012-05-04
If you have more than one hdd, it might be booting the grub2 from your 11.10 which is not even aware of the new 12.04 so it boots 11.10 directly.

Do you have only one disk?

---

### Post by papibe on 2012-05-04
Hi Oldhacker.

Do you see the grub menu or do you go directly to 11.10?
If you don't see it, keep pressed shift while booting to get into it.

My guess is there, but not as the default OS.

In case is not there, boot normally, then run this and try again:
```
sudo update-grub
```
Regards.

---

### Post by mips on 2012-05-04
Post output of **sudo fdisk -l**

---

### Post by Oldhacker on 2012-05-04
I have three physical hard disks. During the installation, I was only given the choice of ONE hard disk, which is not the one that contains my previous boot menu. I saw no other choices in the boot menu, but shall try the sudo update-grub to see if anything changes.

Thanks for the input. I shall keep you posted.

---

### Post by Oldhacker on 2012-05-04
The 12.04 did show up when when I did the sudo update-grub (twice, because of an aborted previous attempt to install 12.04) but it staill booted into 11.10

Here is the output of sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097b98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   613093375   306545664   83  Linux
/dev/sda2       613095422   625141759     6023169    5  Extended
/dev/sda5       613095424   625141759     6023168   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005237f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   295965165   147982551+  83  Linux
/dev/sdc2       295966718  1953523711   828778497    5  Extended
/dev/sdc5      1009207296  1484585807   237689256   83  Linux
/dev/sdc6      1941479424  1953523711     6022144   82  Linux swap / Solaris
/dev/sdc7       530333696  1005017087   237341696   83  Linux
/dev/sdc8      1005019136  1009203199     2092032   82  Linux swap / Solaris
/dev/sdc9      1484587008  1941471231   228442112   83  Linux
/dev/sdc10      295966720   530331647   117182464   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   353703104   176851521   83  Linux
/dev/sdb2   *   353703105   574869959   110583427+  83  Linux
/dev/sdb3       608783299   625137344     8177023    5  Extended
/dev/sdb4       574869960   608783174    16956607+  83  Linux
/dev/sdb5       614020428   625137344     5558458+  82  Linux swap / Solaris
/dev/sdb6       608783301   613666934     2441817   83  Linux
/dev/sdb7       613666998   614020364      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by darkod on 2012-05-04
You can also try to set the second or the third disk as first boot option in BIOS. That should boot grub2 from 12.04.

Even if the update-grub works you have to have in mind that most probably that's the grub2 from 11.10. If in future you start using 12.04 more and decide to delete the 11.10 partition, that will break grub2 from 11.10. Have that in mind. You need to know how you are booting your system to avoid being surprised after deleting some OSs/partitions.

---

### Post by mips on 2012-05-04
> **darkod said:**
> You can also try to set the second or the third disk as first boot option in BIOS. That should boot grub2 from 12.04.

This ^^

I think you are booting of the wrong drive at the moment as grub was installed to a different drive.

---

### Post by Oldhacker on 2012-05-04
Thanks to all who have given their generous knowledge to help.
Now, I was able to boot into Ubuntu 12.04 from the other physical disk. After some guessing as to which entry was Ubuntu 11.10, I am now back there as well.

To further impose upon your good will, how can I best edit the grub2 menu to delete the plethora of confusing entries from distributions past that I didn't even know were still present?

Besides an overly long list in the grub menu, Ubuntu 11.10 was not even identified as such, which is why I had to try several entries.
I am only interested in keeping Ubuntu 12.04 and Ubuntu 11.10

Thank you again

---

### Post by darkod on 2012-05-04
Unfortunately, for the linux OSs it doesn't say the version number in the boot menu. But it will state the partition, something like (on /dev/sda5) for all OSs except the primary ubuntu OS (in this case 12.04 now).

So, right now I would say remember the partition where 11.10 is, and select according to that. Also, the kernel number for 11.10 starts with 3.0.0 and for 12.04 with 3.2.0. That is one more sign.

As for all the extra ubuntus there, the thing is that ubuntu will never install over existing installation unless you specifically tell it to. Otherwise it might delete an installation you don't wanna delete.

So, when trying to solve some problem, spend some time first and ask for advice because installing again will probably not make that problem go away (depending what it is), and it will create one more ubuntu unless you know to install over the current one.

You can delete all unneeded ubuntus, but be careful what you select to delete. You can literary delete those partitions, including any swap partition (again, that are not used), and later create single bigger partition from that space and use it for data.

After deleting ubuntus, just run sudo update-grub again and all deleted systems will be gone from the boot menu too.

---

### Post by oldfred on 2012-05-04
With multiple drives and/or multiple installs, I like to run the boot info script. It will tell you versions installed and which boot loader is in which MBR. It is good just to document partitions in case you have to do recovery or just to understand what is where.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

Housekeeping:
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by drdos2006 on 2012-05-04
Run the LivCD, use gparted to see if you have the boot flag ticked on more than one harddrive.

Untick the one you do not want to be booted from.
Tick the one you want to boot from.

regards

---

### Post by oldfred on 2012-05-04
Grub does not use boot flag. 

Windows has to have boot flag on a primary NTFS partition that you boot from. But not the chainload from grub2.

Some BIOS will not let you boot at all without a boot flag, so it normally is a good idea to have one, but often not essential.

---

### Post by mips on 2012-05-05
> **Oldhacker said:**
> 
To further impose upon your good will, how can I best edit the grub2 menu to delete the plethora of confusing entries from distributions past that I didn't even know were still present?

I am only interested in keeping Ubuntu 12.04 and Ubuntu 11.10


Dude you have so many linux installations across those three drives it confuses the hell out of me :)

I would start off by identifying which partitions are used by 11.10 & 12.04. boot into those two and write down which partitions they use for /, /home & swap. Once you have that info fire up gparted and deleted the other linux & swap partitions you are not using. Once this is done upgrade grub so you have less entries in the menu. If it's possible you could try changing the description in grub to reflect 11.10 & 12.04, not sure if this can be done though as i have never had the need to try.

What you do with the space you freed up on all the drives is up to you to decide.

---

