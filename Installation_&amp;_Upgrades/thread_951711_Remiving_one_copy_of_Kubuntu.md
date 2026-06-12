---
title: "Remiving one copy of Kubuntu"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by socngill on 2008-10-18
Sorry for putting this in the Install thread, but I couldn't see one for removing/unistalling.

I currently have a dual boot system.  I have a working Kubuntu and a working XP along with a non working Kubuntu that went funny on me after a power cut while installing updates and it just get's as far at the tty login and that's it.

Not interested in fixing it anymore, just getting rid of it.  So, what is the best way to do it?

I assume just deleting the partition won't work as that will mess up the MBR - right????

---

### Post by ajgreeny on 2008-10-18
Don't worry too much about the MBR, it can easily be restored with either the windows MBR, if you want that, or with the correct grub from your current good kubuntu install.

Just go ahead and delete the dead kubuntu partition and then using the live CD do what is shown below.

If you want the windows MBR you will need the windows install CD to run the recovery module, or whatever it's called, by booting intio that and running fixmbr at the prompt.

Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```
This gets you to a simple grub command line.
Then:
   ```
 find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader from your correct install.

---

### Post by socngill on 2008-10-18
Cheers.  I shall give it a go.

I assume I have the Grub MBR as it lists the Kubuntu kernels first and then XP under the heading "other operating systems".

I'll let you knwo how I get on.....

---

### Post by socngill on 2008-10-18
It won't let me delete the dead partition.  It says I have to unmount all drives with a number higher than 5.  I have loaded up the live cd so that non are mounted but it still comes up with the same error message.

What is the best way of simply deleting the partition?

Or , how can I change the drive letter assigne dto the parition I want to keep?  I could change it to a number lower than 5 (anything from 2 to 4 is available).  I know under XP you just ell it what letter and bingo, but I can't see anything under linux that would do the same thing.

---

### Post by ajgreeny on 2008-10-19
Try booting to the live CD and using Partition Editor (Gparted) then when the application starts right click in each partition shown on your disk(s) and choose unmount to make sure they are all unmounted.  It should then be possible to delete the partition you want to.

All partitions numbered above 5 are going to be extended partitions as only 4 primary partitions are possible on a disk, and it is just possible that the extended partition in which your dead partition is located is still mounted.  Doing the above right click should work and allow you to delete.  Your partitions will be seen as UUIDs in both ubuntu and grub, so the sda# will not matter.  Also the letter naming of drives and partitions in windows does not transfer directly to ubuntu, so you can really ignore that for the time being.

---

### Post by ugm6hr on 2008-10-19
Try this to remove GRUB: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

Then reformat / delete all "Linux" partitions with GParted (on LiveCD) - as per ajgreeny's advice.

---

