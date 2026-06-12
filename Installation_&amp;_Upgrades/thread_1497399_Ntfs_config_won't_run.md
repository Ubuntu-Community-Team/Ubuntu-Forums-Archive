---
title: "Ntfs config won't run"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Danno2468 on 2010-05-30
I am trying to run ntfs config to auto mount my hard drives, but it won't run I keep getting an OSError.  Here is the teriminal output.


h:~$ sudo ntfs-config
Traceback (most recent call last):
  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'


Any help or suggest would be much appreciated:)

---

### Post by Sef on 2010-05-30
How did you download it?

---

### Post by Danno2468 on 2010-05-30
I used 

sudo apt-get install ntfs-config

But then I got that error.  So I went into the software center and uninstalled it and then re-installed it and it still doesn't work.

---

### Post by Danno2468 on 2010-05-30
I think what I need to do is creat that /etc/hal/fdi/policy' file.  I don't have that dir, and then I would need to find what ever is supposed to be in there.

---

### Post by efflandt on 2010-05-30
10.04 does not use hal.  Although, during updates I saw something added related to hal.  All that /etc/hal/fdi/policy contains is a preferences.fdi file with some commented out examples.

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->
</deviceinfo>
```I did not have to do anything special in 9.10 or 10.04 to mount internal ntfs partitions using Places, or automount USB ntfs partitions.  Just make sure that your user has permission to "Access external storage devices automatically", and maybe "Mount user-space filesystems (FUSE)".

---

### Post by Danno2468 on 2010-05-30
Okay...  So how do I make it so my hard-drives are mounted, after I log on?   What do I need to run?

---

### Post by drs305 on 2010-05-30
You can manually add the entry to your /etc/fstab file.

Note the UUIDs of the partitions you want mounted:
```
sudo blkid
```

Create the mount point(s):
```
sudo mkdir /media/yourmountpoint1  /media/yourmountpoint2
```
Mount points in /media will show in Places. Mountpoints in /mnt will not.

Backup /etc/fstab and open as root for editing. The following entry mimics what ntfs-config would have created. Change the text in bold to match your system. I've added "uid=1000" to make you the owner of the mountpoint:
```
sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab
```

> 
UUID=**7A982427132BCF9C**	/media/**yourmountpoint1**	ntfs-3g	defaults,uid=1000,locale=en_US.utf8	0	0


Save the file, then run 
```
sudo mount -a
```
If things were done properly you will get no messages and the partitions will be mounted.

---

### Post by Danno2468 on 2010-05-31
That worked Splendid!  Accomplished exactly what I was trying to do:)  You laid it out very clearly what I need to Awesome.  Thank you so much:KS

---

### Post by Danno2468 on 2010-05-31
ya

---

### Post by Sciesch on 2010-11-09
> **Danno2468 said:**
> That worked Splendid!  Accomplished exactly what I was trying to do:)  You laid it out very clearly what I need to Awesome.  Thank you so much:KS

Worked fine for me, too. 

any Thanks! :)

---

### Post by Elcid247 on 2010-12-04
> **Danno2468 said:**
> I think what I need to do is creat that /etc/hal/fdi/policy' file.  I don't have that dir, and then I would need to find what ever is supposed to be in there.


i created an empty file in that path and it just worked fine for me :D

---

### Post by theuean on 2011-02-13
Didn't work for me, I screwed up my fstab by mounting it incorrectly. If you happen to do that, you'll be unable to restore your fstab.bak due to being in read-only mode. Get to read-write mode with the following:

mount -n -o remount,rw /

You'll be in, then sudo mcopy /etc/fstab.bak fstab and you're good to go.

As for getting ntfs-config working (10.10 here) I also received the same error message. Since I didn't want to screw up my fstab again, just did this:

Open terminal
cd /etc
sudo mkdir hal
cd hal
sudo mkdir fdi
cd fdi
sudo gedit policy
...save and exit, close terminal, and launch ntfs-config and it'll work.

---

### Post by dushy4 on 2011-03-06
> **Elcid247 said:**
> i created an empty file in that path and it just worked fine for me :D

thanks a lot,,,,
anyone having the same problem,,create empty directry as written and create an empty file as policy,,,worked for me...

---

### Post by m.nour on 2011-05-18
Hi,
instead of creating an empty file, install "hal" from synaptic or "sudo apt-get install hal" from terminal to solve the issue.

---

### Post by TiloBunt on 2011-12-09
> **m.nour said:**
> Hi,
instead of creating an empty file, install "hal" from synaptic or "sudo apt-get install hal" from terminal to solve the issue.

same issue. somebody opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/ntfs-config/+bug/889070](https://bugs.launchpad.net/ubuntu/+source/ntfs-config/+bug/889070)

the hal install workaround did the trick for me. 

thx.

---

### Post by xcesarfrancox on 2011-12-12
The bug report states that you just need to create an empty dir with this command:

```
sudo mkdir -p /etc/hal/fdi/policy
```

---

### Post by LambertH on 2012-01-02
I can confirm that. Simply creating the empty folder /etc/hal/fdi/policy as described gets ntfs-config running.

Happy New year :P

---

