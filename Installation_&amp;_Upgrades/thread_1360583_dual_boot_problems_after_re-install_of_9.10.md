---
title: "dual boot problems after re-install of 9.10"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by scanner248 on 2009-12-21
Starting a new thread since it seems as if I have a new problem.  

Continuation of post "**v 9.10 1st install failed, 2nd ok. why no disk space?".**

On boot, I still got the option to choose which OS to boot. When selecting the ubuntu option, it stalls. Tapping on space bar brings up screen with text. Text on the screen says "gave up waiting for root device". Lists some common problems. Text at bottom of list says "ALERT! /dev/disk/by-uuid/3330ff8b-......does not exist. Dropping to shell!" command prompt is (initramfs).

I entered the directory /dev/disk/by-uuid. There's a few objects in there. one with a name as long as the one that is missing. b64fc7b7.........

Appears that information in boot loader that was built in previous install is no longer valid. How to modify the boot loader?

Currently I've booted into ubuntu using try it on the live disk.

Combed through other posts for answers.
I can't find any file named grub.cfg.
Can't find a file menu.lst.
  
Opened up a terminal window and typed in the following:
  sudo apt-get update
sudo apt-get upgrade
sudo update-grub
  update seemed to finish without error.
  Upgrade also seemed to finish without issue.
  
During the package configuration, a command line from /etc/default/grub was extracted.  Was asked to verify it is correct, but the line is empty.
  Upgrade continued through extractions, eventually stopping with the last few lines stating that there was no space left on device.
  
Update-grub errored out stating "cannot find a device for /".
Tried to view folder contents of root.  Says I don't have the permissions.

---

### Post by GodLikeCreature on 2009-12-21
Hey

Seems like you have a dual setup with a native ubuntu installation.  Is that right?  If the case, did you enable enough space on your swap partition, or did you enable one at all?

From the error messages you are getting, it looks as if you had issues during the installation.  

Can you boot from your live CD, mount your Ubuntu partition and post here the outcome from the df command?

---

### Post by scanner248 on 2009-12-21
> **GodLikeCreature said:**
> Hey

Seems like you have a dual setup with a native ubuntu installation.  Is that right?  If the case, did you enable enough space on your swap partition, or did you enable one at all?

From the error messages you are getting, it looks as if you had issues during the installation.  

Can you boot from your live CD, mount your Ubuntu partition and post here the outcome from the df command?

I am currently booted from the live CD.  

Was never asked during installation how much space to allow for swap partition.  GParted shows that there are 3 partitions built during install.  /dev/sda4 which is extended, 148.93 gb.  /dev/sda5 and /dev/sda6 are both inside /dev/sda4.  they are 146.07 gb, ext4 and 2.86 gb, linux-swap respectively.  There is 8.72 gb used inside partition /dev/sda5

firefox will not start, so I can't cut/paste the df resuslts.  (working here from my work laptop).     Not sure if I'm mounted the ubuntu partition or not.  

The results from the df command, typed in.
file system     1k-blocks        used           available     use%    mounted on
aufs           512294              512848       76                      100%         /
udev                     512924              320               512604            1%              /dev
/dev/sr0           706532              706532        0                        100%        /cdrom
/dev/loop0     684032              684032        0                        100%        /rofs
none                     512924              116                   512808   1%             /dev/shm
tmpfs                   512924              104                 512820          1%            /tmp
none                     512924               92                  512832            1%          /var/run
none                      512924                0                     512924           0%           /var/lock
none                    512924                 0                     512924            0%           /lib/init/rw

When I open up disk utility, the partition where ubuntu was installed to does not show it as being bootable.

---

