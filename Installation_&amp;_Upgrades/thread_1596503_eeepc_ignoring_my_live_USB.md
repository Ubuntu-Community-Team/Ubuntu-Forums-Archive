---
title: "eeepc ignoring my live USB"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by frazerr on 2010-10-14
I have an eeepc with ubuntu 9.04 and i want to upgrade to 10.04

I also have a mac. My eeepc does not have net access due to a bug in connecting to WPA networks.

I created a usb boot drive on my mac using the instructions on [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download). 

ie.  create an .img from the .iso  and then use dd to copy it to my usb.

However my eeepc just ignores this drive at boot time. And yes, I have made my usb the first boot option in the bios.

I have also tried pushing esc/tab at boot and selecting to boot from USB

Once booted my eeepc can see the usb drive, and labels it 'Ubuntu-Netbook 10.04 i386', so I dont know why it wont boot from it.

I thought perhaps I should make a boot drive from within ubuntu, on my eeepc, as one being created on a pc might work better than one created on a mac.
I also used dd within ubuntu.
It was still ignored.

For some reason my install of 9.04 does not have 'Startup Disk Creator'. And my eeepc doesnt have net access.  I also dont have syslinux, or lilo.

I dont even know how to get started with figuring out why it ignores this boot disk.  Any suggestions?

Thanks for your help

---

### Post by Cobracommand0 on 2010-10-14
I've always been successful with Unetbootin in creating USB boot sticks for my 701 Eee.  I'm assuming you are using the Universal USB Installer as suggested by the Ubuntu documentation? I've never used the Universal, but I've seen a lot of people have problems using it..

Go here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I'm not sure if it is compatible with your mac, but you should be able to run Unetbootin in linux if it will not work in the mac environment.  If that fails, try running it from a Windows box.

Basically you need to get the Ubuntu .ISO, then run Unetbootin and select ISO.  From there, just point Unetbootin at your .ISO file, and then your USB stick.

---

### Post by frazerr on 2010-10-14
thanks.  

my eeepc does not have net access.

I want to find out why it is ignoring the live usb

---

### Post by Cobracommand0 on 2010-10-14
I realize you were unable to use the Eee for this process from your original post, but you still have a computer with the ability to utilize the Internet, correct? I assumed you would use that computer to utilize Unetbootin.

I would assume the Eee is ignoring the live USB because of an flawed live USB creation.  Hence my suggestion of Unetbootin.  In my experience, the Ubuntu documentation makes the live USB more difficult by suggestion the Universal installer..

---

### Post by dabl on 2010-10-14
> **frazerr said:**
> 

I want to find out why it is ignoring the live usb

Probably your process did not make the USB stick bootable -- hard to say exactly why not, but you can examine it with GParted and maybe learn something.  Also, in a terminal

```
sudo fdisk -lu 
```

might reveal something. If you really want to dive in deep and examine the contents of the Master Boot Record (mbr), then

```
sudo dd if=/dev/sdx of=mbrsave.bin bs=512 count=1
```

where "x" is the letter designation of the USB stick, will save it in a file for you.

---

### Post by frazerr on 2010-10-14
thanks, UnetBootin does not run on mac.  I appreciate the suggestion

---

### Post by Cobracommand0 on 2010-10-14
> **frazerr said:**
> UnetBootin does not run on mac.

I was suggesting transferring both the .ISO file and Unetbootin to the Eee via USB/SD after using the mac to download the files.  You would be able to utilize 9.04 to run the USB creator, after transferring the downloaded files from the mac.

Apologies for the confusion.

---

### Post by frazerr on 2010-10-14
thanks dabl.

sudo fdisk -lu : 

disk /dev/sdc doesnt contain a valid partition table.

so I fixed that with 
fdisk /dev/sdc

and now I am trying to put the .img on again with dd...  is that correct?

ok, I guess not, because afterwards it again says that /dev/sdc does not contain a valid partition table.

any suggestions?

---

### Post by dabl on 2010-10-14
I'm not a Mac user, but if you have GParted (also available on Parted Magic or GParted Live CD), then you choose "Device > New Partition Table", and you make damn sure you select the right device.  The default table type is "MS-DOS" and that is correct for a USB stick that is intended to boot Linux.

After the partition table is created, then you must create a partition on the "unallocated space", i.e. the default partition table will be empty and so you must create a new partition.  Filesystem can be FAT32 or ext2 -- I think "usbcreator" requires FAT32.

---

### Post by frazerr on 2010-10-15
so i tried this, and it says it needs mtools  and  p7zip.

*expletive*...  it shouldn't be hard to make a freaking USB drive.

---

### Post by xzero1 on 2010-10-15
I'm guessing that your 9.04 netbook version doesn't have 'Startup Disk Creator' but the standard 9.04 live cd should. If you can download *that* iso, burn it to a cd then boot off of it and use its 'Startup Disk Creator' for creating your usb drive, you should be ok.

---

### Post by frazerr on 2010-10-15
thanks xzero,

the eeepc doesnt have a cd drive.  If it did, I wouldnt need the usb.

---

### Post by xzero1 on 2010-10-15
I have one myself, but cant you boot the live cd off your mac? BTW, don't bother, unity runs like crap on my eepc.

---

### Post by frazerr on 2010-10-16
thanks.  So I have been able to make a clean partition,
but then unable to create the boot usb.

actually,
I just noticed fdisk reporting that 

Partition has different physical/logical endings
phys=(102,254,63)  logical=(247,209,63)

---

### Post by frazerr on 2010-10-19
I ended up taking my computer to a friends house with an ethernet cable, and just installing usb creator.  It worked fine.

I cant believe I wasted so much time messing around with it

---

### Post by mabac on 2011-11-15
I had the same problem. It didn't matter if I made the USB stick with unetbootin, Ubuntu's Startup Disk Creator or dd. The problem was that BIOS ignored the USB altogether, even though I set "Removable device" to have first priority in the boot order. However in another forum I found the solution. When the BIOS bootscreen appears, press ESC then a boot menu will appear and you can choose the USB device!

Good luck

---

