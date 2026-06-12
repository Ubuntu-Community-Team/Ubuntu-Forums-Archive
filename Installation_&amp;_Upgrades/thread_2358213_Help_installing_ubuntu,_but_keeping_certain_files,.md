---
title: "Help installing ubuntu, but keeping certain files, while can't create partitions"
date: 2017-04-10
forum: Installation &amp; Upgrades
---

### Post by m3g4-p0n1 on 2017-04-10
Hello all, first I know it`s a pretty very asked question... but I couldn't understand what I saw on other topics. Sorry if I posted on the wrong place.


   Well, I have always used windows, but recently I found that I liked linux(playing around with free mode, using a bootable usb), and I decided to install linux, and erase my crappy windows(kinda messed up some programs), I made searches and as far as I know, I have to:

[LIST]
[*]Back up my important data before installing 
[*]Run CHKDISK on windows 
[*]Defragment if I was going to use the windows partitions manager / or just run chkdisk and then use gparted to create a new partition, and also some specific partitions for linux perfomance. 
[*]Move my files to another partition for safe install. 
[/LIST]

    I choose Gparted, but it shows a red exclamation symbol besides my principal disk's name, and also does not allow me to reduce it's size over 1mb(windows partition manager does not allow over 0mb) even though I have around 300gb free on it.

I'm afraid of going forwards with the partition thing, since a lot of users say that both managers can lost data(yeah I have back up of important stuff, but I'd like to keep my fun files).

Now, I have no idea what to do =/

Any help is appreciated, and, again, sorry for somehow being inconvenient.

---

### Post by Impavidus on 2017-04-11
You want to erase Windows. Linux cannot fix Windows file systems, so if you run Linux only, you shouldn't rely on Windows partitions for long term storage. The best thing to do is erase the Windows partitions. Copy all your important files to an external drive or the cloud or whatever you like, or do it both if the files are really important to you, and disconnect the drive with the backups. Then just format the hard drive, install Ubuntu and copy the files back.

Ubuntu and Windows use different partition types, so yuo can't keep the files just where they are. Linux can read (and usually write) Windows partitions, but sooner or later you will get file system corruption and you can't rely on Ubuntu to fix it. Better transfer everything to Linux partitions.

---

### Post by m3g4-p0n1 on 2017-04-11
> **Impavidus said:**
> You want to erase Windows. Linux cannot fix Windows file systems, so if you run Linux only, you shouldn't rely on Windows partitions for long term storage. The best thing to do is erase the Windows partitions. Copy all your important files to an external drive or the cloud or whatever you like, or do it both if the files are really important to you, and disconnect the drive with the backups. Then just format the hard drive, install Ubuntu and copy the files back.

Ubuntu and Windows use different partition types, so yuo can't keep the files just where they are. Linux can read (and usually write) Windows partitions, but sooner or later you will get file system corruption and you can't rely on Ubuntu to fix it. Better transfer everything to Linux partitions.

So, if I got it right...
The most safe thing to do is move everything to external drives, and then format my pc.
But I also could do something to create a new partition to save my files, but then, when linux be installed, I could have some problems in the future?

And, let`s suppose I moved my files, should I format my pc with the linux installer? Or using windows, and then overwrite it?

---

### Post by Bucky Ball on 2017-04-11
Your files are on the Windows partition? If so, that install is broken and you don't intend to fix it, you want to get rid of it, so keeping your files on that partition is pointless. Thinking, worrying about or doing anything with Windows is pointless unless you intend to fix it. You want to get in, get your files off that partition, then get out and delete it.  

Boot to a live session (Try Ubuntu), open a file manager and backup your files from the broken Windows install to another device. Once you know you have them safe and secure, open Gparted, right-click and unmount the Windows partition then right-click and delete it.

Next, go to 'Device' in the toolbar of Gparted and 'Create new partition table'. Be warned: _*this last step will erase everything on the disk*_.

Following this your disk should be empty, unallocated space, ready to install Ubuntu. Back to the desktop and click the 'Install Ubuntu' icon. Good luck. :)

---

### Post by m3g4-p0n1 on 2017-04-11
Do you mean I need to back up my files in an external drive through linux instead of windows? Also, my hd is showing up now... looks like it wasn't mounted(I didn't know about mount/unmount) [http://imgur.com/a/sPr0A](http://imgur.com/a/sPr0A) <- one is reserved by the system, another small unalocated space is there, I don't know why.

So should I just move everything to external drives, or can I risk and create a new partition?(I have my important files backed up in case of fail)
Oh, and I also can not resize my principal hard drive, only the not allocated one.

---

### Post by Bucky Ball on 2017-04-11
> **m3g4-p0n1 said:**
> Do you mean I need to back up my files in an external drive through linux instead of windows? 

If Windows is broken, yes, this is the easiest. 

> **m3g4-p0n1 said:**
> So should I just move everything to external drives, or can I risk and create a new partition?(I have my important files backed up in case of fail)
Oh, and I also can not resize my principal hard drive, only the not allocated one.

First part is up to you. Second part I don't understand. You can not resize a hard drive, only a partition on it. Windows calls partitions 'drives' (drive C:, drive D: etc.). This is inaccurate. In Linux they are partitions. 

sda is DRIVE 1, sda1 is the first partition on the first drive. sdb2 would be the second partition on the second drive. And that's how it goes ...

Knowing this might make it easier knowing where you are in Gparted (which will show your Win partition as /dev/sd**, where '**' is the numbers of your drive and partition).

You stated at the beginning of the thread that you wanted to delete Win and install Ubuntu only. Now you are alluding to keeping Win solely for keeping these files. Why? If you're not using Win or it is broken and you're not going to fix it, waste of space and creates clutter. Don't need it. Back up and start fresh.

If you have decided you want to keep and fix Windows, best to post a new thread about fixing Windows in the 'Windows' area here or, better still, on a Windows forum where you will get better support. Good luck. :)

---

### Post by Impavidus on 2017-04-11
The small key symbol next to /dev/sda2 indicated that partition is mounted. This means you can access the files. To change the size of the partition, it has to be unmounted. You can right-click and use the menu to mount and unmount, but if you change the size of the partition, it may get damaged and if that happens you can no longer mount it. Windows can fix it, but that may not work with a broken windows.

But if you want to erase Windows, there's no need to keep that NTFS-formatted Windows partition. Just copy your files to a safe place and destroy the partition.

---

### Post by m3g4-p0n1 on 2017-04-11
> **Bucky Ball said:**
> 
You stated at the beginning of the thread that you wanted to delete Win and install Ubuntu only. Now you are alluding to keeping Win solely for keeping these files. Why? If you're not using Win or it is broken and you're not going to fix it, waste of space and creates clutter. Don't need it. Back up and start fresh.


> **Impavidus said:**
> 
The small key symbol next to /dev/sda2 indicated that partition is mounted. This means you can access the files. To change the size of the partition, it has to be unmounted. You can right-click and use the menu to mount and unmount, but if you change the size of the partition, it may get damaged and if that happens you can no longer mount it. Windows can fix it, but that may not work with a broken windows.

But if you want to erase Windows, there's no need to keep that NTFS-formatted Windows partition. Just copy your files to a safe place and destroy the partition.

Yeah I want to erase my windows, but before, I wanted to resize it's partition (sda2), to move my files(not the windows' ones), and then install linux over windows' partition, while my files are safe in another one. But if it's way too dangerous to resize it, I may spend some money on a new pendrive.

---

### Post by Autodave on 2017-04-11
No matter what what you decide, you NEED to make sure that you have backups of ALL files you want to keep!  Having the only copy of those files on a drive that you are making major changes to is not a smart thing.

Backup everything, then reboot machine into the installation media and install Linux.

---

### Post by m3g4-p0n1 on 2017-04-11
Okay I will put away the laziness and backup my stuff on external drives! Thanks for the help guys ^^

And by the way... can I format my hd through the linux installer or should I do it through gparted first?

---

### Post by Impavidus on 2017-04-11
You can format the hard drive from the installer. The simple option is to select "wipe the entire hard drive and install Ubuntu" (or something like that). It should give you a decent layout. But if you want more control, partition in advance using gparted, choose "something else" in the installer and select which partition should be mounted where. If you've got very exotic wishes, you may have to fix it after installation.

---

### Post by m3g4-p0n1 on 2017-04-11
Okay then! It's just, I saw a guy who created a partition named SWAP, he said it helped the RAM.

Anyway, thanks!(should I tag it as [Solved]?)

---

### Post by Bucky Ball on 2017-04-11
If you are happy and your original question is answered to your satisfaction, tag as solved to help others (Thread Tools at top right or see last link in my signature). 

You want a /swap partition, yes. If you choose 'Something Else', as mentioned, you can put it where you want it (and only needs to be 2Gb unless you are hibernating). 

One thing, though: there is no need to format partitions with Gparted prior to installing, particularly if you are using 'Something Else'. The partitioning section in the latter is virtually the same as Gparted and you can create partitions there (and there are a stack of default mountpoints there already, like /, /home, /swap ... you just need to select them).

Unless you're happy with 'Use whole disk' install, then make a plan and choose 'Something Else'. Create the partitions before or during install, up to you. 

But have a plan. Scribble it with a pen a paper in the analogue so you have a reference when you're doing the partitioning in the digital. :)

You want:

/
/swap

... at the very least. Good luck. ;)

---

