---
title: "No mobile internet, installer does not finish and several errors."
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hugh Mulqueen on 2009-10-23
Iam trying to install the latest ubuntu 9.10 RC on my laptop. 
I will outline my experience:

I booted up alright and got to the desktop.
I ran through the wizard with no problems. This is the output of fdisk -l:

```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7422a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1149     9229311   83  Linux
/dev/sda2            1150        1270      971932+  82  Linux swap / Solaris
/dev/sda3   *        1271        3028    14121135    7  HPFS/NTFS
/dev/sda4            3029        4864    14747670    5  Extended
/dev/sda5            3029        4864    14747638+  83  Linux

```

I thought Step 7 looked a bit out of the ordinary. It said that the migration assistant was not found. I have windows XP installed on my ntfs partition. 
I took no notice and pressed the dialog box to start the installation.
It climbed along to 80% done and the window closed unexpectedly.
The "Application problem" box popped up. 
Sorry the program "ubiquity" closed unexpectedly.

I cant connect to the internet because my Huawei E220 does not seem to work very well with the DeviceKit deamon. DeviceKit deamon crashed. 

I cant send the report because there is no internet on my laptop. So im fiddled...

I have a question:
How do I submit a bug report without an internet connection?

---

### Post by CbrPad on 2009-10-23
Check this thread...

[http://ubuntuforums.org/showthread.php?t=1285294](http://ubuntuforums.org/showthread.php?t=1285294)

I've found I can get my modem working by using 

sudo rmmod usb-storage
sudo modprobe usbserial vendor=0x12d1 product=0x1003

But it's an incredible hassle, took me over an hour to get it working this morning.

---

### Post by Hugh Mulqueen on 2009-10-24
Thats fine but I still can't even finish the installation. Theres only 5 days to the release date. They're going to have to have *some* hackathon before then.

Thanks for the suggestion though.

---

