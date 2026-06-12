---
title: "Partitioning"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by PsionicBOOM on 2013-03-18
Summary: attempted partitioning, rebooted, laptop doesn't get past power on.


[HR][/HR]
Hello and Thank You for reading this!
I have a laptop, HP Pavilion dv7-3188cl.
It has two SATA hard-drives, not solid-state.

On this laptop, I have had Xubuntu 12.04 installed since it was Beta. I installed it with the Alternate Cd, and configured LVM on it, for the first time. It was pretty easy.

I recently decided to install Xubuntu 13.04 Beta on the laptop. I used the Daily Live, March 17th, image on a Live USB, as I didn't see an Alternate Cd image. I would guess there is currently no Alternate Cd image for 13.04, as you can now configure LVM in the Live Install...

Well the Live Cd LVM configuration function doesn't seem as complete or straight-forward yet, which I could file a bug about, but that's not my main problem. You see, I was in the manual partitioning screen, on the Live Install, and marking a partition as a physical volume for encryption kept forcing me to have only one Ext4 partition, whereas I wanted multiple Ext4 partitions inside that physical volume for encryption. So I decided that I would quit the installation, go into the Live Session and pre-partition my hard-drives through an alternate means.

So I followed this [https://help.ubuntu.com/community/UbuntuDesktopLVM]("https://help.ubuntu.com/community/UbuntuDesktopLVM#Setup_hard_drive_partions")

Through fdisk, i created
/dev/sda1 Linux
/dev/sda2 Linux LVM
/dev/sdb1 Linux LVM

Pretty much exactly how it is in that link, except the sdb part...

Then I typed
xubuntu@xubuntu: sudo pvcreate /dev/sda2
xubuntu@xubuntu: sudo pvcreate /dev/sdb1

Both returned "Can't open /dev/sdxx exclusively. Mounted filesystem?"

So I googled that and found a suggestion somewhere to reboot, so that the kernel can reread the partition table...
So I tried it.

When the laptop rebooted, it just sat there on the HP logo screen which is shown immediately after powering on - the screen where I could normally push Esc to see my boot options and get into the BIOS.

If I push Esc fast enough, it says "Esc... Pausing startup", which is normal, I think, but then it just sits there anyway, like it's frozen.

So I cannot boot into my Live USB, I can't really do anything.

I tried pushing all the F keys and Del, each one at a time, to see if I could get into any other menu, but it just beeps.

I don't know what to do now... I just have a laptop that doesn't work.

Does anyone know how I can fix this?
I would appreciate any and all the help, and words of comfort, that you could give![INDENT]

I have an idea of what I could try, but I wanted to see if anyone has better information for me.

I was thinking that maybe I could disconnect the hard-drives from the laptop, then maybe I could boot the laptop from the Live USB. Then maybe I could connect the hard-drives back to the laptop while it's running, or this desktop which I'm using to write this (while it's running or not). Maybe then I could write a good partition table to them, and make them functional. 
[/INDENT]

---

### Post by tgalati4 on 2013-03-18
So you installed Xubuntu 12.04 Beta a year ago and you had a good experience--meaning the machine worked and you were able to use your machine and fix any small problems along the way.

Now you installed 13.04 Beta and you had a bad experience. It's not clear from your post if this is a dual-boot machine (12.04 and 13.04) or if you installed 13.04 over 12.04.  If you destroyed 12.04, then you don't have a working configuration to go back to.  (And this thread would be asking a different question).  So, I'm guessing that you destroyed a working linux distro, with a broken, beta and this is not a spare machine to test beta software.  

The instructions that you followed are for 12.04, and I'm not sure if there are differences in 13.04.  

Because you activated encryption, it's possible that one or both drives have an encryption switch flipped that is not working with the BIOS.  You might need to update the BIOS on the laptop to recognize the drives.  Did you use encryption on 12.04?  Try unplugging the drives and get to the BIOS or multi-boot menu and see if you can still boot your old USB stick.

---

### Post by ahallubuntu on 2013-03-18
~

---

### Post by darkod on 2013-03-18
First of all, if you already had a running LVM you could have created new LVs (or even a new VG if you want to separate the two ubuntu versions) from the running 12.04. No need to do the partitioning from live mode when you already have a working system.

Second, for partitioning in terminal I prefer parted or cfdisk, instead of fdisk. Even though there are still lots of tutorials recommending fdisk (some of them old) I have also seen people reporting issues after using it.

The previous poster is right, the computer has to be able to boot from your usb stick regardless of everything. And you can't connect HDDs while the computer is running, get that idea out of your head right away. Try to look around in BIOS or a boot menu since the computer probably has one. That could help you boot the usb.

If you are sure you were working on the correct disk, the partitioning you did shouldn't have made your 12.04 unbootable. But if you repartitioned your 12.04 disk actually, most of the data might be gone. The main thing is to get back into live mode, and if you manage to do that just look around first, and check if your data is still there. Don't try installing 13.04 yet. It's a Beta anyway so be prepared for issues.

If 12.04 and the data are there I would actually try to repair the grub2 bootloader first, and make sure it's booting on its own. After that, as I suggested above, I would create new VG and LVs for 13.04 from the running 12.04. Only then boot again with the 13.04 usb, add the lvm2 package and activate the LVM (not sure if 13.04 contains the lvm2 package by default), and install onto the prepared LVs.

---

### Post by PsionicBOOM on 2013-03-18
Thank you for your replies!

**To Clarify**[INDENT]Having backed-up personal files,
before proceeding to the 13.04 installation and partitioning,
I intentionally wrote over 12.04,
making the two hard-drives blank.
Yes, tgalati4, I used encrypted LVM for 12.04,
having set it up with the Alternate Cd.
In hindsight, I should have done it differently,
possibly reusing the same partitions.

However, my problem remains.

After following the partitioning instructions linked above,
and rebooting the laptop, it effectively locks-up immediately after power on.
It locks-up immediately, while showing the HP logo,
where I would normally press Esc to get to the BIOS,
and I can't do anything - no key has gotten me into the BIOS.
[/INDENT]
 
**After reading your replies**,[INDENT]I physically removed the hard-drives.
With the hard-drives removed,
the laptop works "normally",
I can get into BIOS, I can boot into the LiveUSB.

So I did go into the BIOS, and I reset it to the default settings,
and changed the boot order, placing the USB key above the hard-drives.

Then I put the hard-drives back into the laptop, powered it on, and it still locks-up, same spot, can't do anything.
Update: I later also tried it with each hard-drive alone, same results - it locks-up.
[/INDENT]

---

