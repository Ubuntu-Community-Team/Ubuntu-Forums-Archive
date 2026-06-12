---
title: "Creating a 4tb partition on a hardware RAID 10 system"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by lloydwood on 2012-06-02
I have a ProLiant MicroServer with 4x2TB discs setup through the BIOS as a RAID 10 array giving me a 4TB volume.

I am trying to install Ubuntu server but am running into problems when it comes to partitioning. The Ubuntu server LVM only sees 2TB of the available 4TB.

At this point I have got stuck. I can't find anything that will partition the full 4TB volume.

I want to set up 3 partitions: 

1x200GB partition for the Ubuntu Server operating system
1x4GB swap
1x3795GB(apporx. remaining space) partition for data

Any help would be very much appreciated.

---

### Post by darkod on 2012-06-02
Not sure if it's related, but for above 2TB you need gpt partition table. If it's set up with msdos table, maybe that's the issue.

Also, it might be better and more efficient to run linux software raid instead of the bios raid. But in any case you will need gpt table on the raid array.

You say the LVM sees only 2TB. But is the array seen as 4TB or 2TB? Because you first select a partition(s) on the array and set it as physical volume for the LVM.

If you look at the array device, what's the size?

---

### Post by Gyokuro on 2012-06-02
Hi

You have to use the **GPT** partition scheme. Standard partition scheme is msdos and supports only 2TB for this reason you see only 2TB.

---

### Post by lloydwood on 2012-06-02
I give up. I've been trying every thing I can think of to get this working but it's just not playing ball.

I decided in to turn the hardware RAID off because it was not presenting a volume that I could create a GPT partition table on.

Then the Ubuntu Server 12.04 LTS x64 installer that was running fine before from a USB suddenly decided that it a needed a cdrom (it kept looking for a cdrom and failing to find one because it's on a USB). I couldn't persuade it otherwise so I think I'm going to look at something different.

---

### Post by darkod on 2012-06-02
The server installer is a bit stubborn expecting to be on a cd-rom. You can try this workaround when installing from usb stick:
[http://ubuntuforums.org/showpost.php?p=9705738&postcount=2](http://ubuntuforums.org/showpost.php?p=9705738&postcount=2)

It worked perfectly for me, you only need to have sufficient space to copy the ISO file on the stick too, without deleting the files already extracted there.

I am not sure if the bios raid would have limitation for gpt. You can also test that using the desktop live cd. Boot your server with that, activate the array with:
sudo dmraid -ay

After that there should be a device like /dev/mapper/blah_blah. You can open that device with parted with:
sudo parted /dev/mapper/......
mklabel gpt
quit

That should create gpt partition table on it. After that you should be able to do the server install.

PS. But I still think you are better off with linux software raid instead of the bios raid.

---

### Post by lloydwood on 2012-06-03
Thanks darkod for your pointers.

I tried to get things working with the hardware RAID but it wasn't happening. I did manage to get the installer going though so I've finally got it all set up with software RAID5 (might as well now it's software!). I get an extra 2TB from my setup this way so it's all good in the end.

---

