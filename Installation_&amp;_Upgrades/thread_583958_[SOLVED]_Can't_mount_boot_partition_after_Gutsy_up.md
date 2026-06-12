---
title: "[SOLVED] Can't mount boot partition after Gutsy upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by thediviner on 2007-10-20
After upgrading to Gutsy, I can no longer mount my /boot partition (/dev/hda3). Grub does start just fine and I can select Ubuntu, but during boot I get the following fsck error written to /var/log/fsck/checkfs:

Log of fsck -C -R -A -a 
Sat Oct 20 16:04:10 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Device or resource busy while trying to open /dev/hda3
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8


In order to continue I have to press Ctrl-D and it finishes booting just fine. But when I try to mount it I get the following error:

mount: /dev/hda3 already mounted or /boot busy

When I try to mount it in a different folder I get the same message but /boot is replaced with the other path.

/dev/hda3 does not appear in my mtab file anywhere. Also, when I try to unmount it I get the message:

umount: /dev/hda3: not mounted

When I try lsof to see if it is actually opened exclusively by another program it comes back negative. lsof on /boot comes back empty also and the folder is empty so I don't think it's busy.

So apparently no program has it open and it's not mounted, but fsck and mount both seem to think so and won't let me use it. Any ideas?

---

### Post by meierfra on 2007-10-20
Did you check your fstab? (/etc/fstab)

---

### Post by thediviner on 2007-10-20
My fstab file has the UUID line here's the relevant entry:

# /dev/hda3 -- converted during upgrade to edgy
UUID=44967888-7c80-440f-a7b7-e834ec1c11f6 /boot ext2 defaults 0 2


I don't think it should matter though because I get the same problem when I try 'mount /dev/hda3 /mnt' or any other directory as well and fsck shouldn't depend on fstab as far as I know.

---

### Post by meierfra on 2007-10-20
Mostly I was curious whether hda3 shows up twice in fstab. 

Just another random thought:
Is /boot empty? Maybe Gutsy  installed all the boot files to  /boot on your root partition, rather than on your separate  boot partition.

---

### Post by thediviner on 2007-10-20
/boot is empty.

I tried a couple things and found that if I boot into a live cd I can run fsck and mount the partition just fine. Even after running fsck from the live cd I get the same problem when booting from the hard disk though.

---

### Post by thediviner on 2007-10-20
I was finally able to solve my issue by uninstalling all evms and libevms packages. It got rid of the recovery console issue during boot and all my /boot files are back (since it could mount again).

---

### Post by mary_poppins on 2007-10-22
> **thediviner said:**
> After upgrading to Gutsy, I can no longer mount my /boot partition (/dev/hda3). Grub does start just fine and I can select Ubuntu, but during boot I get the following fsck error written to /var/log/fsck/checkfs:

Log of fsck -C -R -A -a 
Sat Oct 20 16:04:10 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext2: Device or resource busy while trying to open /dev/hda3
Filesystem mounted or opened exclusively by another program?
fsck died with exit status 8


The same problem happens with non-boot partitions as well, see 
[http://ubuntuforums.org/showthread.php?p=3598036#post3598036](http://ubuntuforums.org/showthread.php?p=3598036#post3598036)

However, I don't understand why this is marked as SOLVED -- what is the solution???

---

### Post by gbouro on 2007-10-22
> **mary_poppins said:**
> The same problem happens with non-boot partitions as well, see 
[http://ubuntuforums.org/showthread.php?p=3598036#post3598036](http://ubuntuforums.org/showthread.php?p=3598036#post3598036)

However, I don't understand why this is marked as SOLVED -- what is the solution???

I had the same issue.  I don't think that it is really solved, but using the information in 

[New]https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123789](New]https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123789)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153144](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153144) 

and

[http://ubuntuforums.org/showthread.php?t=5644](http://ubuntuforums.org/showthread.php?t=5644)[/FONT]

I was able to come up with the following procedure:

1) Hit ^D to go on with boot even though [FONT="Courier New"]/dev/sda1[/FONT] could not be mounted on [FONT="Courier New"]/boot[/FONT] and (in my case) [FONT="Courier New"]/dev/sdb1[/FONT] on [FONT="Courier New"]/store[/FONT]

2) Once in, 

```
sudo mount /dev/evms/sda1 /boot
sudo mount /dev/evms/sdb1 /store 
sudo aptitude purge evms
``` (I don't need EVMS.  Alternately you can modify [FONT="Courier New"]/etc/evms.conf[/FONT] per [http://evms.sourceforge.net/install/kernel.html](http://evms.sourceforge.net/install/kernel.html) to exclude your boot partition from EVMS)


4) Finally,
```
sudo update-initramfs -k all -c
```
as the 2.6.22 installation script seems to not do this properly.

---

### Post by bobhenz on 2007-10-25
I haven't seen this mentioned much so I'll post it here as well...

I wasn't having trouble booting, just having trouble mounting my extra paritions/HDD.

The "sudo update-initramfs -k all -c" did not fix me.

As pointed out by gbouro I was able to "sudo mount /dev/evms/sda3 /data" where-as I used to "sudo mount /dev/sda3 /data". That old command now gives me the "Already mounted or /data is busy" error others have complained about.

I have no doubt that getting rid of evms would solve this, however that didn't seem like the right thing since the Ubuntu team went through all the work of getting it put into this distro.

So instead I changed my /etc/fstab to include the "evms" part of the file system path.

i.e.

/dev/evms/sda3  /data           ext3    defaults        0       2

instead of... 

/dev/sda3  /data           ext3    defaults        0       2

This got be back to booting and having this partition automatically mounted for use. (Yeah!)

The only thing that bothers me is that using the "UUID" method in the fstab didn't work, even though vol_id reports the UUID as being the same for both /dev/sda3 and /dev/evms/sda3 as shown below...

(Here's the fstab line that didn't work...)
UUID=**f2c9071f-9f40-4f32-ba13-ca6642713b11** /data ext3 defaults 0 2

Here's the output of vol_id...

bobadmin@linuxdesktop:/etc$ sudo vol_id /dev/sda3
[sudo] password for bobadmin:
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
[B]ID_FS_UUID=f2c9071f-9f40-4f32-ba13-ca6642713b11
[/B]ID_FS_UUID_ENC=f2c9071f-9f40-4f32-ba13-ca6642713b11
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
bobadmin@linuxdesktop:/etc$ sudo vol_id /dev/evms/sda3
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
[B]ID_FS_UUID=f2c9071f-9f40-4f32-ba13-ca6642713b11
[/B]ID_FS_UUID_ENC=f2c9071f-9f40-4f32-ba13-ca6642713b11
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
bobadmin@linuxdesktop:/etc$

---

### Post by bobhenz on 2007-10-26
Actually I take back what I said above... it works, but after reading this post...

[https://wiki.ubuntu.com/Evms]("https://wiki.ubuntu.com/Evms")

It sounds like the proper fix is to remove evms from your system and keep your /etc/fstab like is used to be (with the UUID etc.)

To remove EVMS I just went to System->Administration->Synaptic Package Manager

Searched for evms.
Marked it for complete removal.

I then reverted my /etc/fstab back to how it was before I messed with it (as I described above)

Then I rebooted.

Now all my partitions mount and everything seems to be working. Sorry for the (original) misdirection.

---

### Post by jejones3141 on 2007-10-27
Hmmm.... just upgraded my wife's computer to Gutsy and had the problem with fsck at boot as described here. ctrl-D let it proceed and boot normally. After reading this thread, I fired up synaptic to get rid of evms... only thing is, synaptic says it's not there! Did it get removed, but not removed completely, as part of the deletion of obsolete packages during the upgrade? I can in theory tell my wife to just hit ctrl-D, but I'd like the boot to be clean. Any advice would be greatly appreciated.

P.S. An ironic addendum: when fsck complains, it gives me the option of entering the root password.... on Ubuntu?!

P.P.S. The removal done as part of upgrade doesn't suffice; it has to be complete removal to do the trick. Synaptic let me do that, and now the boot is uneventful, like good boots should be.

---

