---
title: "How to re-size partition at Gparted?"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by Ursus Maritimus on 2014-06-22
Hi,

Managed to shrink /dev/sda1 for 75g with GParted and it went fine. But it ended up unallocated, not as I tried to get it in /dev/sda6. Now, I can't unmount /dev/sda6. It will say:

The partition could not be unmounted from the following mount points:
/
Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually..

So what should I do? How can I do it manually, tried without luck..

[ATTACH=CONFIG]254153[/ATTACH]

Thanks, J

---

### Post by grahammechanical on 2014-06-22
You now need to expand sda2 to take up that unallocated space. That will create unallocated space inside sda2. Then you can expand sd6 to take up the unallocated space. sda2 is an Extended partition and sda6 is inside sda2 and also sd5 is inside sda2. They are called Logical partitions.
 
Are you running Gparted from Ubuntu installed in sda6? If so, that is why you cannot unmount sd6 and we need to unmount a partition before we can move or resize it. Run Gparted from a Ubuntu Live session.

Regards.

---

### Post by Ursus Maritimus on 2014-06-22
Yes, I'm using GParted, which I downloaded and installed to sort out this problem. Did notice, that Ubuntu live session was mentioned at other topics, but thought I could do the same with GParted, which was installed to Ubuntu. But, now I do realize that it ain't the right way to do. I will try to read the live instructions again and try to use it, so it can be solved. Was hoping, that there would have been just something, which I had missed, but I guess not. Thanks, anyhow.

---

### Post by coffeecat on 2014-06-22
Yes, you'll have to use gparted from a live session.

There are a couple of other things to consider when you do. When you boot up the live session it will automatically mount your swap partition, sda5, which will prevent gparted from resizing the sda2 extended partition, at least until you "swapoff". You'll see the key icon by sda5 and sda2. Right click on the swap partition and choose swapoff. That will enable you to resize sda2.

The other thing to remember is that resizing sda2 will be quite quick, but enlarging sda6 by about 75 GiB will likely take several hours. Backup any important data before you start. Resizing partitions always carries the small risk of something going wrong with the loss of partitions and data. A power out, for example, during partition resizing would almost certainly lead to irrecoverable damage.

---

### Post by Ursus Maritimus on 2014-06-23
Tried with live session using instructions which I got from here: [http://gparted.org/liveusb.php#linux-setup](http://gparted.org/liveusb.php#linux-setup)

Tried to set up USB properly, it was formatted and set up for FAT32. Then used Tuxboot, which got me using Clonezilla live. Didn't work. Then tried to use Unetbooting, which took forever to download and didn't help me any further..
Any ideas, where could I find decent instructions, so I would be able to resize the partition. Biggest amount of memory is backup from older version, because I had big problems to update. Power run out and was stuck with two systems, which wasn't really working or any idea anyway (12.04 - 12.10). Now I'm just trying to transfer the older things to newer version (14.04), but space is really limited at the moment..

Thanks..

---

### Post by coffeecat on 2014-06-23
I don't follow what you are trying to do. Do you still have the Ubuntu live CD/DVD or USB you installed Ubuntu with? If so, simply boot up into the live Ubuntu session and run gparted from there. Gparted is already installed in the Ubuntu live session.

---

### Post by Ursus Maritimus on 2014-06-23
OK. I will try that way as well. I don't know, what I'm exactly doing wrong, but I just can't get anywhere. As I said, only reason I'm doing this, is to fit the partitions on their use better. I've got a lot of pics, music, movies and documents on the old side. Yes, I can get them from there, but need to do a lot of extra work and can't move them, because lack of space.

---

### Post by Ursus Maritimus on 2014-06-23
Did try with live, no luck. I restarted the com from usb stick, Went through the boot and tried to use gpartd partition editor, but no result..

---

### Post by oldfred on 2014-06-23
Did you see the little keys? 
As in Post #4:
If so then still mounted and you have to click on swap and right click swap off. Swap is usually automatically mounted with live installer.

---

### Post by Ursus Maritimus on 2014-06-26
Yes, I did notice them as it was said at #4 post. But for some reason, I'm not even able to boot the system. I've tried with gparted live, unetbootin, tuxboot and startup disk cretor, but every single time it has failed, for different reasons. I've understood that partition has to be mounted or swapoff. So I would be able to resize it. But I haven't been able to boot the computer and haven't been able to get that far, that I would be able to do anything for partition. 
I don't know what I'm doing wrong. I've tried to read instructions and act exactly as it has been told, but not getting anywhere. What should I do?

---

### Post by oldfred on 2014-06-26
Some flash drives stop working, some creation tools seem to work better with some systems than others.

Did you verify that ISO was correct with md5Sum?
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM

      [/URL]
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
      [/URL]
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
SOLVED!!! Used rufus to create bootable USB and it worked! I've tried UUI and unetbootin before. 
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Common USB BIOS boot options
[URL="http://www.pendrivelinux.com/usb-bios-boot-options/"]http://www.pendrivelinux.com/usb-bios-boot-options/

      [/URL]
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)


 Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

 
    [URL="http://www.pendrivelinux.com/usb-bios-boot-options/"]
[/URL]

[URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]

---

### Post by Ursus Maritimus on 2014-06-29
Error unmounting filesystem
Error unmounting /dev/sda6: Command-line `umount  "/dev/sda6"' exited with non-zero exit status 1: umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
 (udisks-error-quark, 14)

[ATTACH=CONFIG]254339[/ATTACH]

---

### Post by oldfred on 2014-06-29
If that Disks screen shot from inside your Ubuntu in sda6? You cannot unmount the partition you boot from. 
That is why you have to use live installer and even then usually have to also manually unmount swap.

---

### Post by DaniPhii on 2014-06-29
If you can't boot any GParted Live CD/USB or similar, have you checked your CMOS configuration?

If you can, maybe the drive you're trying to partition is physically corrupted, I don't get what you may be doing wrong.

---

