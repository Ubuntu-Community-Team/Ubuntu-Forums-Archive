---
title: "Cannot format USB flash driver using Gparted"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by childintime on 2013-12-22
I cannot delete or do anything with this USB. Here is the information error in Gparted: [http://i.imgur.com/bwdxpXe.png](http://i.imgur.com/bwdxpXe.png)

First it was all good, I created new MS-DOS partition table, formatted it, but now it's not working. I cannot format it in windows either, it says it's write protected.

When I try to delete it using Gparted it says: Input/output error during write on /dev/sdb

Thanks for any help!

---

### Post by electrohandyman501 on 2013-12-22
Looks similar to the issues I had trying to re-format one of my usb sticks a while back. It wouldn't format thru anything GUI. 
I ended up getting it done thur the mkfs command in a terminal window. btw, iirc, you cannot have it mounted when trying to format it.

---

### Post by childintime on 2013-12-22
mkfs builds a linux file system? I want to format it with fat32 so I can burn Windows 8.1 iso and then install it on new pc.

---

### Post by codenine75a on 2013-12-22
did you give your application root permissions by running sudo first?

---

### Post by childintime on 2013-12-22
Which application? If Gparted, then yes, it always asks for password.

---

### Post by oldfred on 2013-12-22
Did you use an old version of gparted? Partitions now always start at sector 2048, but yours is the old start of sector 63. Windows changed to using sector 2048 with Vista and gparted changed serveral years later, but at least two years ago. Required for SSD & new 4K drives, so should not make huge difference on flash drive but old gparted may not now be correct?

---

### Post by electrohandyman501 on 2013-12-22
> **sladeinflame7 said:**
> mkfs builds a linux file system? I want to format it with fat32 so I can burn Windows 8.1 iso and then install it on new pc.

For fat32 the command would be 

mkfs –t vfat <USB-device-mount-point>

Don't forget you may need sudo with it.

There are other options in this article

[URL="http://ksearch.wordpress.com/2010/09/29/format-usb-in-linux/"]http://ksearch.wordpress.com/2010/09/29/format-usb-in-linux/

[/URL]

---

### Post by childintime on 2013-12-23
Updated all my software, when creating partition table with Gparted I get: [COLOR=#000000] Input/output error during write on /dev/sdb

When I run [/COLOR]```
sudo mkfs –t vfat /dev/sdb 
```

I get: 

```
mke2fs 1.42.8 (20-Jun-2013)
mkfs.ext2: invalid blocks 'vfat' on device '–t'

```

---

### Post by oldfred on 2013-12-23
You normally format a partition, not a drive. Some do format a drive and it is like a super floppy but they does not work as it has no partitions to mount. 

This will totally erase the boot loader and partition table of a device. Be absolutely sure you have your flash drive as if run on wrong device you then have erased it. Then you can create & format a new partition. Change sdX to your drive.

       dd if=/dev/zero of=/dev/sdX bs=512 count=1

            Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

If you have used the dd method of copying an ISO to a flash drive the dd erase is required as the image copy of a flash drive does not create a standard partition table.

---

### Post by childintime on 2013-12-23
I ran that command, and it finally allowed me to create partition table, and partition the drive. Everything was great, but then I tried to burn Win 8.1 iso to flash using Winusb and again got this error:

```
nstallation failed !Exit code: 512
Log:
Formating device...
Mounting...
mount: block device /home/mosquito/Downloads/Windows 8.1 AIO 20in1 x64 Pre-Activated v2 Nov2013/Win81AIO-20in1-x64-en-US-Nov2013-v2.iso is write-protected, mounting read-only
Copying...
Installing grub...
/usr/sbin/grub-bios-setup: error: cannot write to `/dev/sdc': Input/output error.
Error occured !
Syncing...
/usr/bin/winusb: line 78: 19428 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Cleaning...
/usr/bin/winusb: line 78: 19811 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1387819477_11222'...
Umounting and removing '/media/winusb_target_1387819477_11222'...

```

I guess I need to try different approach for burning iso.

Also now when I run your command ```
[COLOR=#000000]dd if=/dev/zero of=/dev/sdX bs=512 count=1[/COLOR]

``` again to clean the drive I still can't create new partition in Gparted, strange that it's not working now even though it worked minutes ago.

Anyways, thanks a lot.

---

### Post by childintime on 2013-12-24
Any idea how to solve it? Now I cannot do anything with flash drive. Windows XP cannot format it, says "Unable to format drive" and above program does not do anything. That's how it looks with Gparted: [http://i.imgur.com/M6WKJQI.png](http://i.imgur.com/M6WKJQI.png)

I don't need to burn iso into it anymore, all I want it to simply work.

---

### Post by oldfred on 2013-12-24
Did you change the example of sdX to your drive the second time?
Not sure what the label error is. I often assign labels to partitions with Disk Utility or Disks in new versions. What does Disk Utility show?

---

### Post by childintime on 2013-12-24
> **oldfred said:**
> Did you change the example of sdX to your drive the second time?
Not sure what the label error is. I often assign labels to partitions with Disk Utility or Disks in new versions. What does Disk Utility show?

Of course I did. I check label via Gparted every time and change accordingly.

---

### Post by oldfred on 2013-12-24
Not sure what else to suggest.

---

### Post by electrohandyman501 on 2013-12-24
By chance have you tried to format the usb drive on a different computer.

Time for a new usb drive? It is Christmas time afterall......Merry Christmas.

---

### Post by childintime on 2013-12-24
Haha :)

I tried formatting in both XP and 8.1 but it says unable to format.

---

### Post by childintime on 2013-12-26
Bumpy..

---

### Post by childintime on 2014-01-06
Bump

---

### Post by oldfred on 2014-01-06
What did disk utility show?

---

### Post by childintime on 2014-02-25
usb still not working...

---

### Post by Mark Phelps on 2014-02-25
> **sladeinflame7 said:**
> usb still not working...
How about helping us out here and RESPONDING to the question you were asked in oldfred's last post?  

If you won't provide us information we ask for, we can't really help you.

---

### Post by sudodus on 2014-02-26
Either the pendrive is failing (which is rather common with such devices), or the partition table and other general information is bad. In the latter case it might help to wipe the first megabyte (not only the first 512 bytes). This can be done directly with dd as adviced by *oldfred* (but slightly modified),

```
[COLOR=#000000]dd if=/dev/zero of=/dev/sdX bs=1024 count=1024[/COLOR]
```

or safer with ***mkusb*** according to this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

If you need a new USB pendrive, you find general information at these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

See posts #6 and #7 in [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by childintime on 2014-02-26
> **Mark Phelps said:**
> How about helping us out here and RESPONDING to the question you were asked in oldfred's last post?  

If you won't provide us information we ask for, we can't really help you.

Oh sorry didn't notice his question. Here we go: [http://i.imgur.com/hffJd0d.png](http://i.imgur.com/hffJd0d.png)

> **sudodus said:**
> Either the pendrive is failing (which is rather common with such devices), or the partition table and other general information is bad. In the latter case it might help to wipe the first megabyte (not only the first 512 bytes). This can be done directly with dd as adviced by *oldfred* (but slightly modified),

```
[COLOR=#000000]dd if=/dev/zero of=/dev/sdX bs=1024 count=1024[/COLOR]
```

or safer with ***mkusb*** according to this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

If you need a new USB pendrive, you find general information at these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

See posts #6 and #7 in [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

I tried that command, but still, I gparted says "File system unallocated". 
When I try to create new file system it says "No partition table found on device /dev/sdb". 
If I want to create new partition table (msdos) it says: "Libparted bug found! Input/output error during write on /dev/sdb"

---

### Post by sudodus on 2014-02-26
> **sladeinflame7 said:**
> Oh sorry didn't notice his question. Here we go: [http://i.imgur.com/hffJd0d.png](http://i.imgur.com/hffJd0d.png)

I tried that command, but still, I gparted says "File system unallocated". 
When I try to create new file system it says "No partition table found on device /dev/sdb". 
If I want to create new partition table (msdos) it says: "Libparted bug found! Input/output error during write on /dev/sdb"

I think you have done what is possible with gparted now. It seems that gparted cannot write to that device. But you can still see it as /dev/sdb (as read only). It is typical of a failing flash drive (it remains read-only after writing does not work. The next step is that it cannot be read either).

But the problem might also be co-operation with that particular USB port or with the computer, so try in another USB port and try in another computer, if you are able to create a partition table and make a file system ('format' it).

---

### Post by childintime on 2014-02-26
> **sudodus said:**
> I think you have done what is possible with gparted now. It seems that gparted cannot write to that device. But you can still see it as /dev/sdb (as read only). It is typical of a failing flash drive (it remains read-only after writing does not work. The next step is that it cannot be read either).

But the problem might also be co-operation with that particular USB port or with the computer, so try in another USB port and try in another computer, if you are able to create a partition table and make a file system ('format' it).

Tried other usb port but same. I guess I will try to somehow test it on another linux machine :)

---

### Post by oldfred on 2014-02-26
If you use the dd procedure to create an Intaller, it does not use standard partition table like all the other methods. And then because partition table does not exist partition tools see random data or think it is corrupted.

Sometimes then just writing 0 to MBR to totally erase boot loader and partition table info works. 
Do not use this if trying to recover any data from old partitions on flash drive.

 Erase - Make double sure you have correct drive & partition, Change X to correct drive.
sudo fdisk -l
       dd if=/dev/zero of=/dev/sdX bs=512 count=1

---

### Post by childintime on 2014-02-26
> **oldfred said:**
> If you use the dd procedure to create an Intaller, it does not use standard partition table like all the other methods. And then because partition table does not exist partition tools see random data or think it is corrupted.

Sometimes then just writing 0 to MBR to totally erase boot loader and partition table info works. 
Do not use this if trying to recover any data from old partitions on flash drive.

 Erase - Make double sure you have correct drive & partition, Change X to correct drive.
sudo fdisk -l
       dd if=/dev/zero of=/dev/sdX bs=512 count=1

Alright, I've done that, and it's still the same errors as before when doing something with Gparted.

---

### Post by oldfred on 2014-02-26
As posted before, it just may be dead. They do not last a long time and may just fail at anytime.

---

### Post by childintime on 2014-02-26
> **oldfred said:**
> As posted before, it just may be dead. They do not last a long time and may just fail at anytime.

But it was good usb until I started reformatting with gparted. If it's indeed dead then it's only because I did something, but again, what I did is just regular gparted or Windows xp format commands, I didn't even use command line.

---

### Post by sudodus on 2014-02-28
I have been doing such operations (with gparted, dd, etc) thousands times. They do not destroy the drive. They may destroy data by overwriting the partition table or (parts of) some partition, but the drive itself survives. As said before, pendrives have limited lifetime, and this one just happened to die while you were running these commands. 

-o-

This is what I think; it is hard to be sure when I cannot run the different operations myself. We have to rely on verbal conversation, and we might misunderstand each other.

---

### Post by childintime on 2014-03-01
> **sudodus said:**
> I have been doing such operations (with gparted, dd, etc) thousands times. They do not destroy the drive. They may destroy data by overwriting the partition table or (parts of) some partition, but the drive itself survives. As said before, pendrives have limited lifetime, and this one just happened to die while you were running these commands. 

-o-

This is what I think; it is hard to be sure when I cannot run the different operations myself. We have to rely on verbal conversation, and we might misunderstand each other.

Well everything was going just fine, until I used Winusb to burn Windows 8.1 to usb (1st page I wrote this) and it gave me error:

```
nstallation failed !Exit code: 512
Log:
Formating device...
Mounting...
mount: block device /home/mosquito/Downloads/Windows 8.1 AIO 20in1 x64 Pre-Activated v2 Nov2013/Win81AIO-20in1-x64-en-US-Nov2013-v2.iso is write-protected, mounting read-only
Copying...
Installing grub...
/usr/sbin/grub-bios-setup: error: cannot write to `/dev/sdc': Input/output error.
Error occured !
Syncing...
/usr/bin/winusb: line 78: 19428 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Cleaning...
/usr/bin/winusb: line 78: 19811 Terminated              while true; do
    sleep 0.05; echo 'pulse';
done
Umounting and removing '/media/winusb_iso_1387819477_11222'...
Umounting and removing '/media/winusb_target_1387819477_11222'...

```


Then I tried to run same command again which I run few minutes ago and it won't work anymore: ```
[COLOR=#000000]dd if=/dev/zero of=/dev/sdX bs=512 count=1[/COLOR]

``` again to clean the drive I still can't create new partition in Gparted, strange that it's not working now even though it worked minutes ago.

So it seems that something happened when I was burning Windows with winusb. Either way, chances of usb completely failing right at that momen without any reason are quite slim.

---

### Post by sudodus on 2014-03-01
Well, there is a reason, some important memory cell is probably locked (does not respond when you want to change it). This can happen after a number of changes of the state between zero and one. See [this link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426")

---

### Post by oldfred on 2014-03-01
If you actually used this it does not work, you have to change the sdX to your drive like sdb, sdc. But be sure to use correct drive.

 dd if=/dev/zero of=/dev/sdX bs=512 count=1

---

