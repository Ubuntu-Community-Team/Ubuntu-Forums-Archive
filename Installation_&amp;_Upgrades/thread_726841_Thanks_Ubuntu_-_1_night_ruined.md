---
title: "Thanks Ubuntu - 1 night ruined"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by JK0l1day on 2008-03-17
So I finally went to my parents house to get my XP installation disk. I have 2 identical seagate hard drives. I want one with windows for games, and one for ubuntu.

For a few months now I have had ubuntu on one harddrive. I plugged in another harddrive now that I was ready to install windows.

Boot up after hardware change:
Verifying DMI pool hang
Boot from CD/DVD when told not to
Hangs hangs hangs

I tried to recover with the ubuntu live CD but that even fails. I feel like it had something to do with grub. This is ridiculous.

Adding a new harddrive should be simple.

For the pretentiousness that Ubuntu brings, it sure fails in the most important areas.

---

### Post by blueturtl on 2008-03-17
Are you using SATA or PATA drives? Possibly mix the two? The thing is with PATA drives you have to make sure they are properly set as master and slave. If you plug in PATA hard-disk with cable select enabled the drives might change their logical roles and thus the Ubuntu root partition might get shifted to a different hardware address.

Since apparently Ubuntu does start loading(?) but hangs the above might not be the case but some kind of hardware error. Are there old partitions on the disk you were trying to add? Is the disk positively recognized by the BIOS?

With that said you should also *install Windows prior to installing Ubuntu* because Windows can only be installed on the master hard-disk and because installing Windows after Ubuntu will make Ubuntu un-bootable (Windows will erase your Grub boot menu).

---

### Post by thinkdez on 2008-03-17
Don't get discouraged.  Its a learning opportunity. Now I am not entirely clear but from what I gather your problems are happening during the POST process which would indicate that this is a BIOS problem not a problem with Ubuntu however if I am wrong about this please let me know.  The reason I say this is because you mention that its trying to boot from the CD/DVD when you told it not to.

What kind of drive did you add?  Was it a SATA? or an IDE?

Depending on how you plugged the drive in you may have changed the way the system recognizes the drive and now the boot order is lost.  I had this happen to me when I plugged in a new SATA drive on an earlier SATA port.  As a result the system didn't know where to find Windows or Ubuntu.  A few changes to the boot.ini file and grub changed that but I could have simply swapped the SATA cables so it would boot properly.  Try removing the new drive and see if it boots properly.

---

### Post by ajgreeny on 2008-03-17
A bit unfair, I think.  If you had read a bit more about what you are trying to do you would quickly find that it is the wrong order to do it for ease, not impossible, but more problematical.  It is also probably the case that adding another disk to your system, depending on their settings, has totally confused your BIOS about the disk devices, and grub may be looking for the wrong disk, or if the new disk is the boot device there will be no bootmanager to find at all.

Tell us a bit more about the detailed problem and any errors you get and it may be quite easy to help; just moaning about the state of affairs is not going to help at all.

---

### Post by Arthur Archnix on 2008-03-17
Ubuntu probably realizes that you're trying to install Windows and is trying to protect you. 

:P

Seriously though, you need to give more information if you want help. Did you try reversing the disks? Unplugging the new one and booting? Chaning boot order in bios?
Etc..

---

### Post by JK0l1day on 2008-03-18
I apologize for acting so rash. I digress:

1) I had an IDE drive with windows XP installed already. I then installed a new SATA drive with Ubuntu on it. Windows XP became damaged so I decided that I didn't need to go back even though the opportunity was still in the grub menu.

2) I had another identical SATA drive unused for RAIDing. I wanted to buy a RAID controller first. Linux would not play one of my favorite games(Cedega nor Wine had caught up yet). Deciding to install Windows over RAID, I plugged in the new SATA HDD and nothing would boot. There is no BIOS problem involved here. [COLOR="Red"]EDIT: The IDE windows was on an old dying drive, better to have on a new SATA.[/COLOR]

3) I got angry.

4) I posted this thread.

5) Afterwards, I unplugged the drive linux was on and plugged the one in Windows was on. I installed Windows successfully. After I update the drivers I'm going to see if I can get into linux and somehow Reset Grub and if not - copy/paste all my important files from linux to windows and reinstall ubuntu. Hopefully Windows will recognize the file system the same way Linux recognized the windows drive for data.

Is this the only way to get linux working again?'

---

### Post by Cresho on 2008-03-18
hmm...  Gutsy identifies windows xp just fine on my end.  Your hardware needs tweeking.  Have you navigated in bios and does it see the 2 hardrives?  Which disk is set to boot up first?  after you have the initial hardrive setup and bootup from the cd, if you use gnome partition editor, what drives does it see and which one is windows xp?  keep note of the disk names.

---

### Post by JK0l1day on 2008-03-18
> **Cresho said:**
> hmm...  Gutsy identifies windows xp just fine on my end.  Your hardware needs tweeking.  Have you navigated in bios and does it see the 2 hardrives?  Which disk is set to boot up first?  after you have the initial hardrive setup and bootup from the cd, if you use gnome partition editor, what drives does it see and which one is windows xp?  keep note of the disk names.

My bios shows both harddrives now that I plugged the other one in. The only problem is that they're identical in every way and the only way to tell them apart is by file size. I decided that the file size is untelling because it is still identifying one harddrive as completely free.

I'm assuming Windows is set up to boot first as it, well, boots. Unless that isn't proper evidence.

Under rescue on the liveCD under the partition options it identifies both harddrives in the form of SCID(sp?)0 and 1. Claiming 0 is 100% unused and SCID1 is 137 used(as per the max hdd memory an unmodified xp will let you use). I'm not sure if the free given is 138 or 183. 183 would make sense because it is a 320 GB HDD.

I don't believe they have any specific disk names other than the IDs 0 and 1

---

### Post by Cresho on 2008-03-18
The first time I did an install of ubuntu, I played with my one disk.  I completely unplugged windows xp hardrive.  I made sure ubuntu hardrive was my main boot through bios and also absolutely made sure everytime I needed to reinstall, that the live cd would install grub onto ubuntu hardrive.  In anycase, after installing the operating system, I simply turned pc off, and plugged in windows xp.  Of course, the hardrive does not (sometimes) automount when it boots up so in the terminal, I....

Just to note and this is important, before installing windows xp, I was able to configure this.  Because my system did not hang at boot, i was able to identify my blank ntfs partition.

sudo gedit /etc/fstab

then I added to where my windows xp is located like this. do a df in a new terminal  to see drive names before labling like this.

note that i placed this at the end of the page.  the hdb5 is an extra disk i have laying around.

/dev/sdb1       /media/WinXP       auto    defaults,user,rw               0 0
/dev/hdb5       /media/Pictures        auto    defaults,user,rw               0 0

this next step is important.

In the Terminal, I did a sudo nautilus and created Pictures and WinXP directories under media.

Now for bootup.  I noticed my operating system hung.  It would not boot and found out that windows xp loves to be ontop and not on the bottom so I did this.

forgive this part since this is just my notes.

sudo gedit /boot/grub/menu.lst
sudo fdisk -l to find drives.  sata1 is hd2

then I added this part after end debian automagic because if you do it before, it will erase.  this modification needs to be because windows loves to be ontop.  It hates being number 2


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


my pc has 2 sata drives. and anything other would be hda or hdb
on my machine, sda1, sda2 sda3 is my first hardrive with root being 1 swap 2 and home 3.  the second hardrive is sdb1 which is windows xp.  of course these are sata drives.  Now in grub, it sees sda1 as hd0 and sdb2 as hd1.

If you have your hardware correctly installed to begin with or identified, ubuntu will automatically do this for you but since we are doing it the hardway, this is needed.

---

### Post by Cresho on 2008-03-18
> **JK0l1day said:**
> So I finally went to my parents house to get my XP installation disk. I have 2 identical seagate hard drives. I want one with windows for games, and one for ubuntu.

For a few months now I have had ubuntu on one harddrive. I plugged in another harddrive now that I was ready to install windows.

Boot up after hardware change:
Verifying DMI pool hang
Boot from CD/DVD when told not to
Hangs hangs hangs

I tried to recover with the ubuntu live CD but that even fails. I feel like it had something to do with grub. This is ridiculous.

Adding a new harddrive should be simple.

For the pretentiousness that Ubuntu brings, it sure fails in the most important areas.

yes this is a problem.  windows likes to be ontop.  make sure you read my post above this one.  IT tells you exactly why and what you really need to do.  I was exactly on your boat heading over the edge.  you need to read specifically the part of.....sudo gedit /boot/grub/menu.lst

---

