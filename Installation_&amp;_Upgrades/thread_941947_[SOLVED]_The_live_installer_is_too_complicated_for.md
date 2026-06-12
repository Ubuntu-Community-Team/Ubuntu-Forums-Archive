---
title: "[SOLVED] The live installer is too complicated for me...setting up dual boot?"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-10-08
I always use the alternate cd and I have already set up a dual-boot. However all I have right now is the desktop CD and wanted to set up a dual boot with my new Acer laptop that came with windows preinstalled. However, I get to the partitioner and it only gives me the option of manual partitioning, or guided-use entire disk. What happened to the Guided-resize option? Is it gone in hardy heron or what? I'm honestly stumped because I don't want to wipe windows off.

---

### Post by BetterSense on 2008-10-08
I just tried using thed manual partitioning, and I can't even see an option to resize the ntfs partion that is there. I can only edit the partion and choose whether I want to 'use as' swap, ext2, etc. There is no option to resize. All tutorials I read on the ubuntu documentation claim there is a 'guided...resize partitnion and use freed space' option, and I remember there being one before. What happened? Is something wrong with my CD?

---

### Post by Rebelli0us on 2008-10-08
Yeah, Ubuntu installer is not very intuitive, the possibility of trashing your windows partition is very real. It took a few installs before I figured it out. I created an empty partition *after* windows and used the option "use largest contiguous space". That installs Ubuntu in the 2nd partition and also creates a dual-boot menu. I would much prefer to explicitly specify the installation partition.

---

### Post by snowpine on 2008-10-08
+1 use the Live CD (or a Gparted live cd) to resize the partition first, then your install into the empty space should be a breeze.

ALways a good idea to back up first, just in case. :)

---

### Post by Sodbuster on 2008-10-08
I'm having this same problem...  I absolutely must keep my Windows installation since there's some stuff within Windows that is not available in Linux (yet).  I run the live CD and when I get to the part about resizing my partition it only gives me 3 options:

-Use Entire Disk
-Use Free Space
-Manual

I'm going to try burning the gparted live CD to see if it will allow me to resize my Windows partition.  I've backed up all my critical data so that's taken care of... but I'd prefer not to have to go through doing all the Windows re-installation stuff.

---

### Post by Sodbuster on 2008-10-08
Well I ran the Gparted Live CD and it said the NTFS partition had a bad sector so it couldn't do anything with it.  Then it said to go into Windows and run "chkdsk /f /r" and reboot twice to fix that.  So I'm going to do that and see what I get.

---

### Post by oldos2er on 2008-10-08
> **BetterSense said:**
> I always use the alternate cd and I have already set up a dual-boot. However all I have right now is the desktop CD and wanted to set up a dual boot with my new Acer laptop that came with windows preinstalled. However, I get to the partitioner and it only gives me the option of manual partitioning, or guided-use entire disk. What happened to the Guided-resize option? Is it gone in hardy heron or what? I'm honestly stumped because I don't want to wipe windows off.

 If you don't have enough free contiguous space available on your hard disk, you won't see that option.

---

### Post by BetterSense on 2008-10-09
Ok I made a new USB stick with the alternate CD and I tried to use the 'resize and use free space' option and it 'failed to write to the devices' and the screen went all red. So i went to manual mode in the alternate CD and selected the NTFS partition and said to resize it to 80GB, and got the same red screen and same error.

---

### Post by BetterSense on 2008-10-09
I stole an IDE-to-usb adapter and booted a Xubuntu liveCD. I run Gparted. I tell it to resize the NTFS partition. It attempts, and fails. "an error occurred while applying the operations". Clearly something is wrong here if I cannot resize the partition with the live installer, the guided Alternate, the manual Alternate, or Gparted from a LiveCD. TF?

---

### Post by Sodbuster on 2008-10-09
Does Gparted say you have a bad sector?  It said I did, then I ran the Windows chkdsk like it said and now it says I have two bad sectors.  So it still can't resize the NTFS partition.

---

### Post by abhilashm86 on 2008-10-09
u better make a separate disk drive for ubuntu linux,coz when u open windows ur linux drive becomes "lost+found"...........so u cannot make windows and linux in same drive............even i had a same problem,so install in separate drives.............

---

### Post by BetterSense on 2008-10-09
You mean entirely separate drives, or different partitions? Cause I'm fairly certain it's possible to resize the windows partition and install onto a new partition in the free space. In fact that's what I did with the computer at work.

---

### Post by BetterSense on 2008-10-09
I solved the problem my booting windows, removing the pagefile, and defragmenting. Then Gparted allowed me to resize the ntfs partition. Very strange but there you go.

---

### Post by Mike.lifeguard on 2009-04-08
> **oldos2er said:**
> If you don't have enough free contiguous space available on your hard disk, you won't see that option.

To get enough contiguous space (curse you, NTFS!) I should do what? defrag a few times (done already, but will do again)... what is pagefile and how do I disable or shrink that? and... anything else?

(I suppose some chkdsk wouldn't hurt since I have bad sectors too)

---

### Post by Mike.lifeguard on 2009-04-10
> **Mike.lifeguard said:**
> To get enough contiguous space (curse you, NTFS!) I should do what? defrag a few times (done already, but will do again)... what is pagefile and how do I disable or shrink that? and... anything else?

(I suppose some chkdsk wouldn't hurt since I have bad sectors too)

None of that was strictly necessary -- see [https://lists.ubuntu.com/archives/ub...il/180136.html](https://lists.ubuntu.com/archives/ub...il/180136.html) (& possibly my previous posts in that thread) for my solution here.

---

