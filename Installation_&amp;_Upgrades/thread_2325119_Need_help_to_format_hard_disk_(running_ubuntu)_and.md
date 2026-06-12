---
title: "Need help to format hard disk (running ubuntu) and reload with Ubuntu 14.04"
date: 2016-05-19
forum: Installation &amp; Upgrades
---

### Post by ashok19 on 2016-05-19
Hello, 
I am thinking to format (zeo filling) the hard drive, currently running 12.04 and reload the Ubuntu 14.04. Also, i m not going to flash from USB or Live CD. I would like to install the Ubuntu from ISO image located on NFS.
so basically i want to wipeout /dev/hda. Someone told me i can run my OS on RAM and create an Pivot_root , make a partition and umount pivot and install OS image form NFS. Can anyone elaborate and please provide me instruction how to do so. 

I would be really grateful.

thanks

---

### Post by ajgreeny on 2016-05-19
You can boot to a ubuntu .iso file directly using grub 2, but it will be much easier, I suspect, to use a USB flash drive rather than the NFS that you have.  I am not sure how you would point grub 2 to the NFS drive, but others may be able to help with that.

If you choose to use the USB route as I have many times, here is how to make the USB drive and copy the files needed.

The first step is to install Grub2 on the USB flash drive. Be careful that you don't put a number behind the device name because you want to install Grub2 into the MBR of the device and not into a partition. Execute the following command in a terminal.
```
sudo grub-install --root-directory=/media/USBFolderName /dev/sdx
```
where sdx is the USB drive.

After that you should see a new folder &#8220;boot&#8221; on your USB flash drive which contains another folder named &#8220;grub&#8221;. In the "boot" folder you create a new folder &#8220;isos&#8221;. In this folder you can copy supported LiveCD ISOs to boot from.

Create a "grub.cfg" file in the "boot/grub" folder of your USB drive and add the matching menu entry for your iso file. You may also need to modify the path to your ISO file.
[I]This is where you may be able to point to the iso file on the NFS but I know nothing about that, I'm afraid, so wait for others if you wish to try doing it that way.
[/I]
The entry you need to boot the live Ubuntu 14.04 will be similar to this stanza if you copy the iso file to the USB boot/isos folder.
```
menuentry "Ubuntu 14.04.1 64bit" {
    set isofile="/boot/isos/ubuntu-14.04.1-desktop-amd64.iso" [COLOR="#0000FF"]#make sure this points to the correct name and path of your iso file.[/COLOR]
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}
```

Now if you boot to the USB you will see a grub menu listing just "Ubuntu 14.04.1 64bit" and you should be able to boot to that iso very quickly and install to your hard disk in the normal manner.

You do not need to zero the disk before installing as the new OS will format the disk and remove everything on it.  You can also choose to reuse partitions if you choose "Something Else" at the partitioning stage of installing; come back again if you want to know more about that.

---

### Post by ashok19 on 2016-05-19
That's a nice way to reload OS through USB. However, at this I'm testing to install OS using NFS only. 
As mentioned, there should some way to do this. Once zero filing is performed, kernel will be running on RAM (Make sure no reboot is performed). Someone told me we can create a new root and do partition and check the Network and install OS from NFS. I've never done and i am looking for possibilities to do so.

---

