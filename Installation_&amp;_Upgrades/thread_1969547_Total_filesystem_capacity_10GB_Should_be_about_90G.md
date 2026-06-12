---
title: "Total filesystem capacity 10GB? Should be about 90GB"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by TheTeamFromMars on 2012-04-30
Hi 

I have just installed ubuntu 12.04 using a USB. 
I have been using 10.04 for a couple of years and I'm dual-booting with Win7. 
When starting the installation I chose the option to **remove 10.04 completely and replace it with 12.04**. 

Everything appears to be working ok except **that I should have around 90GB of disk space for ubuntu - but I only appear to have 10GB.** 

This is what I see for ubuntu space when I look in disk utility:
Device: /dev/sda5 - Swap Space (4.1GB)
Device: /dev/sda7 - 10GB ext4 (Capacity 10GB) Mounted at /
Device: /dev/sda6 - 82GB ext4 (Capacity 82GB) Not mounted

I can see a 'Mount volume' button that I can click but I want to make sure that I'm not gonna mess anything up...  

Can anyone help? 
 
I'm using the 64bit version of 12.04.

---

### Post by albandy on 2012-04-30
You have /dev/sda7 mounted as / (root) (10GB)
But /dev/sda6 is not mounted (82GB)

Total = 92 GB

It seems that you were using a /home partition in your old distribution.

---

### Post by TheTeamFromMars on 2012-04-30
Thanks for the quick reply, albandy.
Is this something that I can fix easily?

---

### Post by albandy on 2012-04-30
> **TheTeamFromMars said:**
> Thanks for the quick reply, albandy.
Is this something that I can fix easily?

How do you want to use this partition?
You can use it as /home (no reinstall)
or
delete both: / and the free space partition and reinstall ubuntu using all the space.

---

### Post by TheTeamFromMars on 2012-04-30
I think I'd prefer to use all of the space.
 
Not sure what the /home partition was for in the first place. 
I didn't know anything about linux and installed ubuntu by following the steps in a youtube video - so I just did whatever it told me to do :)

So, how do I go about deleting / and the free space partition and reinstalling?

---

### Post by darkod on 2012-04-30
It's much better to keep /home as separate partition. That allows you to make clean installs in future and keeping all your documents and settings in Home untouched.

But when you do the install you have to tell it to use sda6 as /home. If that is what it was. I would expect the installation to make this happen for you if sda6 was /home before. But maybe it wasn't, or it didn't take care about it.

You don't remember the procedure you followed, what partitions did you set up?

---

### Post by albandy on 2012-04-30
> **TheTeamFromMars said:**
> I think I'd prefer to use all of the space.
 
Not sure what the /home partition was for in the first place. 
I didn't know anything about linux and installed ubuntu by following the steps in a youtube video - so I just did whatever it told me to do :)

So, how do I go about deleting / and the free space partition and reinstalling?

The easiest way is to resize the partition using the liveCD and then reinstall erasing the old installation.

You can use gparted an utility similar to Partition Magic.

If gparted is not installed in the live cd you can install it by using apt:
sudo apt-get install gparted

---

### Post by darkod on 2012-04-30
> **albandy said:**
> The easiest way is to resize the partition using the liveCD and then reinstall erasing the old installation.

You can use gparted an utility similar to Partition Magic.

If gparted is not installed in the live cd you can install it by using apt:
sudo apt-get install gparted

Actually, if you want to reinstall using the whole space, and you have no data to keep, the easiest is to boot into live mode, open Gparted, delete sda5, sda6 and sda7, and then also the extended partition that was holding them. Make sure you don't delete any windows partitions.

After that simply start the install and it will use that unpartitioned space.

Note that to delete swap you will probbaly need to right-click it and select Swapoff. That will make the keys symbol go away in Gparted, so you can manipulate the partition.

---

### Post by TheTeamFromMars on 2012-04-30
Ok so if it's better to keep /home as a separate partition then I'll do that.

darko: I think I found the youtube clip that I originally followed when first installing ubuntu and I would have set it up like this: 

/dev/sda5 - Swap Space - (4.1GB)
/dev/sda7 - Root - 10GB ext4 (Capacity 10GB)
/dev/sda6 - /home - 82GB ext4 (Capacity 82GB)

So I think what happened during the install of 12.04 is that it just didn't use the /home partition. If I can get that back in business then that's all I want to do...

---

### Post by btindie on 2012-04-30
Have you still got access to your files that were in your old home directory? Do you want access to them?? It may be that they're still intact on sda6, you'd just need to manually mount it to check. You should be able to get at it from Nautilus, the file manager, by clicking on the drive or you can use the mount command.

Presumably there's nothing of any importance in your new home directory so you'd be quite happy to delete it?

Reboot Ubuntu into [Recovery Mode ]("https://wiki.ubuntu.com/RecoveryMode")to a root shell.

Now type "rm -rf /home/*" to remove your new (empty) home directory.

Type "blkid -s UUID -o value /dev/sda6 >> /etc/fstab" to get the UUID of that partition. If you're familiar with vi/vim you could run ":r!blkid -s UUID -o value /dev/sda6" to run the command directly within the editor.

Next edit the line, with nano / vi, so it looks something like
```
UUID=11111111-2222-3333-4444-555555555555 /home            ext4    defaults        0       2
```replacing the UUID value with yours for /dev/sda6.

Save the file and reboot. You'll then have access to your old home partition.

---

### Post by TheTeamFromMars on 2012-04-30
> **btindie said:**
> Have you still got access to your files that were in your old home directory? Do you want access to them?? It may be that they're still intact on sda6, you'd just need to manually mount it to check. You should be able to get at it from Nautilus, the file manager, by clicking on the drive or you can use the mount command.

Presumably there's nothing of any importance in your new home directory so you'd be quite happy to delete it?  


Reboot Ubuntu into [Recovery Mode ]("https://wiki.ubuntu.com/RecoveryMode")to a root shell.

Now type "rm -rf /home/*" to remove your new (empty) home directory.

Type "blkid -s UUID -o value /dev/sda6 >> /etc/fstab" to get the UUID of that partition. If you're familiar with vi/vim you could run ":r!blkid -s UUID -o value /dev/sda6" to run the command directly within the editor.

Next edit the line, with nano / vi, so it looks something like
```
UUID=11111111-2222-3333-4444-555555555555 /home            ext4    defaults        0       2
```replacing the UUID value with yours for /dev/sda6.

Save the file and reboot. You'll then have access to your old home partition.

I just checked and all of my files are still there. 
So yes - I'd be happy to delete the new home folder and replace it with the old one.

The rest of this looks a bit too complicated for me but this is exactly what I want to do. I'll give it a go... not familiar with vi/vim or anything like that I'm afraid.

---

### Post by btindie on 2012-04-30
> **TheTeamFromMars said:**
> The rest of this looks a bit too complicated for me but this is exactly what I want to do. I'll give it a go... not familiar with vi/vim or anything like that I'm afraid.
If you're not familiar with vi then you may want to give nano a go, quite straight forward and only a few key combinations to learn.

Edit the file with "nano /etc/fstab"
Use the cursor keys to move around...
Ctrl+O then enter to write the file.
Ctrl+X then enter to exit.

Reboot and you should be back in your old home directory.

---

### Post by TheTeamFromMars on 2012-04-30
Hi again btindie, 
that didn't go according to plan at all I'm afraid.
I rebooted into recovery mode, selected drop to a root shell and typed "rm -rf /home/*" (without the quotes). As the screen began to scroll up, it appeared that there were quite a lot of things that could not be removed.

I then typed "blkid -s UUID -o value /dev/sda6 >> /etc/fstab" and hit enter. This didn't give me a UUID for the partition. It just said something along the lines of "read only disk". 

Any ideas? Should I just try reinstalling from the beginning again?

---

### Post by darkod on 2012-04-30
> **TheTeamFromMars said:**
> Hi again btindie, 
that didn't go according to plan at all I'm afraid.
I rebooted into recovery mode, selected drop to a root shell and typed "rm -rf /home/*" (without the quotes). As the screen began to scroll up, it appeared that there were quite a lot of things that could not be removed.

I then typed "blkid -s UUID -o value /dev/sda6 >> /etc/fstab" and hit enter. This didn't give me a UUID for the partition. It just said something along the lines of "read only disk". 

Any ideas? Should I just try reinstalling from the beginning again?

Try to do everything from live mode. When doing this kind of procedures it's best to do it from live mode since you are not booted from the disk in that case.

And be careful with the rm command, that is the delete command. Before you manage to confirm you have all your data mounted correctly in /home, do not remove anything.

To work from live mode you will have to mount your root partition like:
sudo mount /dev/sda7 /mnt

From that point on, the startting point is /mnt, so to edit the fstab you would do:
sudo nano /mnt/etc/fstab

You can read the UUIDs of all partition with:
sudo blkid

---

### Post by btindie on 2012-04-30
> **TheTeamFromMars said:**
> Hi again btindie, 
that didn't go according to plan at all I'm afraid.
I rebooted into recovery mode, selected drop to a root shell and typed "rm -rf /home/*" (without the quotes). As the screen began to scroll up, it appeared that there were quite a lot of things that could not be removed.

I then typed "blkid -s UUID -o value /dev/sda6 >> /etc/fstab" and hit enter. This didn't give me a UUID for the partition. It just said something along the lines of "read only disk". 

Any ideas? Should I just try reinstalling from the beginning again?
That may have been because it mounted the root "/" filesystem read-only. You can remount it read-write with "mount -o remount,rw /" once you're in recovery mode. That would also explain the problem with the blkid command.

It won't print anything to the screen, it'll redirect output to the file ">> /etc/fstab" so you then don't have to type in the UUID value!

---

### Post by TheTeamFromMars on 2012-04-30
Thanks for taking the time to help me with this.
After my other attempt, the system wasn't working properly and the screen resolution was all messed up so I have reinstalled 12.04 fresh again. 
I'll try to change the /home folder again but I need to take a break from this for a while first :)

---

### Post by darkod on 2012-04-30
> **TheTeamFromMars said:**
> Thanks for taking the time to help me with this.
After my other attempt, the system wasn't working properly and the screen resolution was all messed up so I have reinstalled 12.04 fresh again. 
I'll try to change the /home folder again but I need to take a break from this for a while first :)

No problem, take your time. Sometimes it's best to let new knowledge sink in.

But again, during your new install you had a perfect chance to attach the existing /home. That's when it's done best.

Not to install, and then try to attach it. You can do it now, only it was lot easier during the install.

---

### Post by TheTeamFromMars on 2012-04-30
> **darkod said:**
> No problem, take your time. Sometimes it's best to let new knowledge sink in.

But again, during your new install you had a perfect chance to attach the existing /home. That's when it's done best.

Not to install, and then try to attach it. You can do it now, only it was lot easier during the install.
Ok thanks. 
So if it's easier to attach the existing /home folder during installation, maybe I should just install it again. 
It doesn't take that long. 

So how do I attach it during the install? 
I had a look earlier at the "Allocate drive space" - "Something else" option but wasn't sure what to do when I got there...

---

### Post by darkod on 2012-04-30
You need to use the Something Else option.

Now, the main thing to note when the list of partitions shows, is that linux doesn't reuse any partition automatically. I guess this is to prevent overwriting something important.

Many people think it will install over the same partition. No. Unless you specifically tell it to.

So, when you enter this manual method of installation (Something Else), all linux partitions are marked as Do Not Use. You need to tell the installer what partition to use for what.

You need to click on the root partition, and the button Change below. In the small window that opens, you change the Do Not Use into the filesystem that partition has, for example ext4. You select the mount point to be / (root). You tick the format box. That's it, close that window.

Then you click on the /home partition. You change the Do Not Use into the filesystem used, like ext4 (be careful, it needs to be the same, the list shows the filesystems detected on all partitions). Select the mount point /home. DO NOT tick the format box (this is very important not to lose the data in Home).

Usually the swap partition should be reused automatically, but it doesn't hurt to double check. So do the same procedure for the swap, only that you change the Do Not Use into swap area. Swap doesn't use mount point, so nothing to select there. Just click OK and that's it.

Below the partitions list is the drop down menu for the bootloader destination. Usually it would be the MBR of the disk, for example if we are talking about /dev/sda, it will be /dev/sda. There should not be a number in it.

Continue with the install. When it asks you to create the first, main user, create the same first user as you had in the original install. You will create the other users later when ubuntu is running.

---

### Post by TheTeamFromMars on 2012-04-30
Thanks everyone for your excellent help - and your patience. 
I re-installed using Darko's easy to follow steps. 
After a shaky start on first login (a theme that I haven't seen before and system crash after a few seconds) I think it's working now since I restarted and installed updates. 

I have my original /home folder back again and disk space of 92GB instead of the 10GB that I had earlier. 
Thanks again.

---

