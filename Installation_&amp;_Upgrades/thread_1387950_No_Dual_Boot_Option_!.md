---
title: "No Dual Boot Option !?"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by carl99fan on 2010-01-22
I am installing 9.04 on a Lenovo Think pad R61e It has a Celeron and a 60 GiG Hard drive 31 Gig is open. 

I have a USB startup disk I am using for the install. It is not giving me a dual boot option and I don't understand why. It is most important that this laptop is dual boot. Please help me.

---

### Post by darkod on 2010-01-22
What do you mean it's not giving you dual boot option?
Is that 31GB space unallocated and not belonging to any partition? If yes, just start the install process and in step 4 tell it to use Largest Available Free space. It will set up ubuntu in that 31GB unallocated space.
The dual boot is automatically created after windows is detected on the hdd and the grub menu should have option for both once the installation is done.

---

### Post by carl99fan on 2010-01-22
I have done nothing to the hard drive. I have not partitioned it at all. I am just using the menu step 4 is only giving me 2 options.
Use entire disk,
and Specify Partitions manually (advanced) 
I have installed Ubuntu im sure over 40+ time on different units and this is the first time I have run into this problem. it's missing like 2 options if I remember correctly..... Different version maybe? I am trying to install 9.04 Maybe I should try a 9.10 usb drive.

So back to your question, it's all Windows vista... ntfs and I was wrong, it's a 80 Gig with 10 hidden for a recovery for windows.

---

### Post by darkod on 2010-01-22
> **carl99fan said:**
> I have done nothing to the hard drive. I have not partitioned it at all. I am just using the menu step 4 is only giving me 2 options.
Use entire disk,
and Specify Partitions manually (advanced) 
I have installed Ubuntu im sure over 40+ time on different units and this is the first time I have run into this problem. it's missing like 2 options if I remember correctly..... Different version maybe? I am trying to install 9.04 Maybe I should try a 9.10 usb drive.

So back to your question, it's all Windows vista... ntfs and I was wrong, it's a 80 Gig with 10 hidden for a recovery for windows.

The option will appear only if available.
Use Largest Free space is not there because you have no unallocated space, that's clear.
Lately I've seen cases where Install Side-by-Side is not offered too because that option involves shrinking the vista partition in the process. If there is any error at all on that partition, ubuntu will not touch it to shrink it. Note that this error message might be displayed only in ubuntu/gparted and not vista. Can't explain it.
So that option will not show either.
To confirm this, select the Try Ubuntu option and load the live desktop. Open Gparted. If your vista partition has like a triangle mark with exclamation mark inside next to it, that's the error message.

Sometimes you need to run chkdsk (or what ever it was called) from windows.
Also, in cases like this, it's better to shrink vista with the windows disk management (since vista it can do resize) than the ubuntu installer. Boot vista and do the disk check. The shrink it by as much as you want using the disk management tool. Boot it few more times to make sure it's happy after the shrink.

Only then boot ubuntu cd, Install Ubuntu option, and this time just select Largest Space... option and that's it. :) Hopefully.

---

### Post by kansasnoob on 2010-01-22
If your "USB startup disk" allows you to run in the Live Desktop please post a screenshot of Gparted (aka: Partition Editor).

Or at least the output of this command:

```
sudo parted /dev/sda print
```

A screenshot would be great!

---

### Post by carl99fan on 2010-01-22
OK I will give it a shot.... This will take some time. :( but it's for a friend so it's good Karma. I will post after I try again. Thanks.

---

### Post by carl99fan on 2010-01-22
```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA WDC WD800BEVS-08 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  6708MB  6707MB  primary  ntfs
 2      6708MB  80.0GB  73.3GB  primary  ntfs         boot
 
```

---

### Post by kansasnoob on 2010-01-22
OK since you're using Vista and 9.04 this guide should be perfect for you:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Notice on page 2 they show how to use Vista's own tools to resize it. I recommend defragging first.

You'll notice that currently sda2 is unreadable by Gparted, that's why you got no "side-by-side" option.

Best to try and sort that out using Vista's own tools.

---

### Post by carl99fan on 2010-01-22
Thank you very much everybody.
Since I had to deal with Windows anyhow, I cleaned it all up, Defragmented, did all full scans, Told Vista to shrink, and an now Installing Ubuntu.
I am very shocked I have never come across this before. 
My friend had been turning off his computer every day without shutting it down. It seems whenever he wanted to turn it off he would just hold the button down. I am not surprised at all now that it was this much trouble this time. 

Thanks again.

---

