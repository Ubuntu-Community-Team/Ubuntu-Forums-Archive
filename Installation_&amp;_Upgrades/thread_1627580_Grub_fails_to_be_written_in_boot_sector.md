---
title: "Grub fails to be written in boot sector"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by objet petit a on 2010-11-21
Hello everybody, I am a complete noob at this and I need a hand. I was about to throw my computer out of the window when I decided to throw the windows out of the computer so to speak. So, I downloaded Ubuntu 10.10 and tried to install. I had a grub rescue after the installation (file system unknown), which I have seen discussed here. Being the noob that I am I decided to try 10.04 because it said it had full support. With this install I get a similar error during installation: grub cannot be installed in boot sector. 

So, basically there is an issue with grub and the boot sector. I checked in my BIOS options to see if there was an option that prevented the writing of a boot sector or something, but I have not been able something like that. So, I am wondering if it is possible that Ubuntu does not really erase/format the selected disks or something, leaving any difficulty there.

Does anybody know? Or better yet: what exactly do I need to do a manual grub install? Or anything else that springs into your thoughts concerning this might also be helpful. Thanks in advance.

---

### Post by sikander3786 on 2010-11-21
Welcome to Ubuntu and the Forums :-)

Which system is it? Please refer to the system documentation regarding boot sector lock up.

If Grub was not able to get installed during the installation process, it might well fail yet again while doing a manual install.

Please post your System specs so we can try and might eventually find something useful regarding the MBR problem.

---

### Post by objet petit a on 2010-11-21
[SIZE=2]I am working on an Asus P6T Deluxe V2, with an INTEL I7 920 (2,66GHz Quad, Socket 1366) and two 64GB [/SIZE][SIZE=2]OCZ Vertex 2 SATA II 2.5" SSD's. 

Good point concerning the manual install failing again btw.

--edit--
Thanks for the warm welcome and the speedy reply btw.
:)
[/SIZE]

---

### Post by lmarmisa on 2010-11-21
This page shows the instructions for installing Ubuntu 10.04. Maybe it could help you:

[http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

If your problems continue and _ONLY in the case you wish to get rid of your Windows operating system_, you can try this procedure in order to delete the loader of the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record"). 

Boot your system from an Ubuntu Live CD, open a terminal (Applications -> Accessories -> Terminal)  and type this command:

```

sudo dd if=/dev/zero of=/dev/sda bs=446 count=1

```

You can check if the MBR was deleted with this command:

```

sudo dd if=/dev/sda bs=446 count=1 | xxd

```

NOTE: if you change 446 with 512, you will delete all the information of the MBR including the partitions defined in your hard drive.

---

### Post by objet petit a on 2010-11-22
Thanks imarmisma,

2 more questions though:
1) Do you know of a way to reformat the entire disk(s) from a boot of a live cd? I would greatly appreciate it.
2) Do you think a previous mbr entry can indeed prevent the grub install?

Thanks.

p.s. Yes, windows must go.
:)

---

### Post by lmarmisa on 2010-11-22
> **objet petit a said:**
> Thanks imarmisma,

2 more questions though:
1) Do you know of a way to reformat the entire disk(s) from a boot of a live cd? I would greatly appreciate it.
2) Do you think a previous mbr entry can indeed prevent the grub install?

Thanks.

p.s. Yes, windows must go.
:)

1) This command will write all your hard drive /dev/sda with zeros (of course, all the information stored on the disk will be deleted!!!):

```

sudo dd if=/dev/zero of=/dev/sda bs=16M

```2) I seriously doubt it. But I had an experience about problems installing XP due to the GRUB loader code stored in the MBR.

---

### Post by objet petit a on 2010-11-22
Okay, I have formatted both disks and formatted the MBR.

The result is an installed Ubuntu 10.04!
:)

Thanks a lot!

However, what is now the case is that I am using one of the disks for my OS, but the other one is not in use. I think it was formatted as a raid in the past, which may have been the problem, or indeed a format had to take place for some reason of compatibility. Personally I would guess the problem was the raid though.

Anyway, if I understand correctly I should be able to format the second disk and mount it in a folder or something, but how does that work exactly?

I hope I&#7743; not pushing it with this one.
:)

---

### Post by dino99 on 2010-11-22
what to do ?

first, remove raid : sudo dmraid -rE

then its how your installation should be:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by drs305 on 2010-11-22
For the second drive:

Make one or more partitions and format (ext3, ext4, ntfs if you want to share with Windows).

Make a mount point in your Ubuntu partition:
on /media it will show on your desktop
on /mnt it won't
```
sudo mkdir /media/my-new-mountpoint
```
Make yourself the owner:
```
sudo chown -R $USER: /media/my-new-mountpoint
```

Check the new UUID and add it to fstab - *noauto* if you always expect this partition to be available during boot:
```

sudo blkid
gksu gedit /etc/fstab &
```


Sample fstab entries:
Ext3:
> UUID=<newUUID> ext3 /media/my-new-mountpoint defaults 0 2

Ext4:
> UUID=<newUUID> ext4 /media/my-new-mountpoint defaults 0 2

NTFS (Sample options, see here for more: [_Understanding fstab_]("http://ubuntuforums.org/showthread.php?&t=283131")):
> UUID=<newUUID> ntfs /media/my-new-mountpoint auto,users,uid=1000,gid=1000,utf8,umask=027 0 0

Test fstab entry:
```
sudo umount -a  # You will get 'busy' messages for partitions currently in use.
sudo mount -a  # If fstab is happy with your entries, no message will appear and the partition is accessible.
```

Take a look at the link to fstab if the partition won't always be available at mount (noauto) or if you want different permissions for an ntfs partition.

---

### Post by objet petit a on 2010-11-22
Hi drs305 and dino99,

Thanks for the information. For now I am planning to go ahead and just mount the 2nd disk without raid. With Ubuntu it is fast enough regardless. However, I am going to need a little more information to understand what each step drs305 has taken down means exactly. Apologies people, but I am really new at this and am used to winblows so, that is the plug and play system and not having to know how things actually fit together.

So, directly I want to know:
1)
sudo mkdir /media/my-new-mountpoint/media would be the folder and /my-new-mountpoint only a name?

2)
sudo chown -R $USER: /media/my-new-mountpointOkay, change owner and USER is my username I presume?

3)
> 
Check the new UUID and add it to fstab - *noauto* if you always expect this partition to be available during boot:

UUID?? 
Add the comman &#324;oauto'to fstab I presume?

4)
sudo blkid
gksu gedit /etc/fstab &This must be the code to execute the above. Should I insert the 'noauto' after the '&'?



I&#314;l halt here because I bet I can make more sense of the below after the above.....I bet...
[-o<

---

### Post by drs305 on 2010-11-22
> **objet petit a said:**
> 
1)
sudo mkdir /**media/my-new-mountpoint** would be the folder and /my-new-mountpoint only a name?
It's a folder called whatever you want (for example, my-new-mountpoint, or mydata, or songs, etc.)

> 
2)
sudo chown -R $USER: /media/my-new-mountpointOkay, change owner and USER is my username I presume?

It is, but that is a universal shortcut for the current user's name, so you can leave it just as it is, or change it to  john: (or whatever).

> 
3)
UUID?? 
Add the comman &#324;oauto'to fstab I presume?
'noauto' as a option if you didn't plan on having the partition available every time you boot. Any options, such as 'noauto' would go after 'defaults' - for example: defaults,noauto

I didn't really want to get into the details in the post, but most of the info is contained in the 'understanding fstab' link.

---

### Post by objet petit a on 2010-11-23
Okay, One last question before I start fiddling with it:
If I mount my second SSD , will it be available to all folders? Imean: I think that UNIX does not treat the disks as separate, but as storage devices, ready to be filled from any folder, right?

---

### Post by sikander3786 on 2010-11-23
> **objet petit a said:**
> Okay, One last question before I start fiddling with it:
If I mount my second SSD , will it be available to all folders? Imean: I think that UNIX does not treat the disks as separate, but as storage devices, ready to be filled from any folder, right?
You can mount your intended partition in any of the desired folders.

See here for details on mounting permanently.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by lmarmisa on 2010-11-23
If you mount a new hard drive, you will find the files and directories of this new drive in /media/yourseconddrive.

But maybe you think that is not the best idea to store your data in two separate directories: /home/youruser and /media/yoursecondrive. I am sure you would prefer to be able to access all your files inside the directory /home/youruser.

You can use [symbolic links]("http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html") for integrating the new drive (or one or more folders of this new drive) within /home/youruser.

This is very simple:

```

cd ~
mkdir mydata
ln -s /media/yoursecondrive mydata

```Now all your files and directories of the new drive can be accessed in the path /home/youruser/mydata (of course also in /media/yourseconddrive). 

This is really interesting.

You can define as many symbolic links as you want, locating the links in any folder (for example, in the desktop):

```

cd ~/Desktop
mkdir MyMusic
ln -s /media/yoursecondrive/music MyMusic

```I hope this help you.

---

### Post by objet petit a on 2010-11-23
Hi everybody, thanks for all of the advice. I am sort of getting there. This is what I have done so far:
```

$ sudo mkdir /media/mountSSD2
#/media$ 
#/media$ 
#/media$ 
#/media$ sudo chown -R $USER: /media/mountSSD2

```
As drs305 said. If I am correct now the actual mounting should take place. If I am correct I should :
1) First assign a UUID. If I understand that correctly it should be a random number, format: xxxxxxxx-xxxx-3xxx-xxxx-xxxxxxxxxxxx (for version 3).
2)Then create an fstab entry.

Questions:
1) Do I choose/name a number for the UUID, or is it already present in the UUID list? Now my list looks like this (without the actual numbers):
```

/dev/sda1: UUID="######" TYPE="ext4" 
/dev/sda5: UUID="######" TYPE="swap" 
/dev/sdc1: LABEL="DATA" UUID="######" TYPE="ntfs" 

```
I think sda5 is the same disk as sda1, but I do not know for sure. And if it isn't how do I list it exactly, it&#347; intended name being SSD2, with mount point /media/mountSSD2 and intended filesystem ext4?
2)I have got absolutely no clue what this should look like. Let&#347; get back to this after the UUID mixup. I find the fstab article very unclear by the way. It may be clear once one knows the general idea, but there are too many unaddressed issues for me to get past it, especially concerning the UUID.

Thanks for bearing with me everybody.
:)

---

### Post by drs305 on 2010-11-23
> **objet petit a said:**
> 
Questions:
1) Do I choose/name a number for the UUID, or is it already present in the UUID list? Now my list looks like this (without the actual numbers):
The UUID comes from the command "sudo blkid -c /dev/null". You use the one listed for the specific partition you want to use in fstab.

> I think sda5 is the same disk as sda1, but I do not know for sure. 

Each drive is identified by a letter: a,b,c  So any "sda" partition is on the same drive (sda1, sda2, sda5, etc).

---

### Post by objet petit a on 2010-11-23
Hi drs305,

When I use the command 'sudo blkid -c /dev/null', I see only the three references listed above. The second SSD is not visible here. Where do I get that UUID? And is it possible to check if the disk is even properly formatted now? Or: "Is there a reason why devices would not be listed in that blkid?"

---

### Post by drs305 on 2010-11-23
> **objet petit a said:**
> Hi drs305,

When I use the command 'sudo blkid -c /dev/null', I see only the three references listed above. The second SSD is not visible here. Where do I get that UUID? And is it possible to check if the disk is even properly formatted now? Or: "Is there a reason why devices would not be listed in that blkid?"

I have never used a SSD. Running "sudo fdisk -l" (lowercase L) should show all the partitions the system sees. You can try running "sudo blkid" to see if you get a result for the second drive.

You could also use Gparted to look to see if the SSD is listed there (System, Administration, Gparted).

Perhaps someone with more knowledge about SSD's can offer better suggestions.

---

### Post by objet petit a on 2010-11-23
Okay, this is what the fdisk shows:
```

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

```
Should I use 0x00000000 for fstab?

---

### Post by sikander3786 on 2010-11-23
> Should I use 0x00000000 for fstab?

No, it is not showing the partition/s. Are you able to access the partition/s on your SSD? Which filesystem?

I haven't used SSD either but I have read somewhere that ext2 is a better filesystem for SSDs. Wait for some more opinions though.

---

### Post by objet petit a on 2010-11-23
The first works great under ext4. How can I check if there are partitions?

---

### Post by sikander3786 on 2010-11-23
The output of fdisk -l doens't suggest if there is any partition on the SSD.

Were there any partitions previously? And does it contain some data?

---

### Post by objet petit a on 2010-11-23
Okay, so there was no partition :oops:....now I did make one I get the following from fdisk:
```

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029baa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7783    62516916   85  Linux extended

```
From blkid I get:
```

#$ sudo blkid
/dev/sda1: UUID="#######" TYPE="ext4" 
/dev/sda5: UUID="#######" TYPE="swap" 
/dev/sdb1: LABEL="SSD2" UUID="#######" TYPE="ext4"  

```
I mounted the disk in the mount point, made no 'noauto' mentions. After I had saved the edited fstab the new disk disappeared and I could create files in the mount point. Does this constitute a full success? Or: "How do I check if my created files really do arrive on the second disk"?




Thanks so far everybody!!
:)

---

### Post by objet petit a on 2010-11-24
I am having a related problem, but I&#314;l start a new topic since the original problem has (long since) been resolved.
:)

Thanks a lot everybody!

---

