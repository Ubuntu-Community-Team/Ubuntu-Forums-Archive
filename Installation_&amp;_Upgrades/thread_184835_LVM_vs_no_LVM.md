---
title: "LVM vs no LVM"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by nbx909 on 2006-05-30
I am going to install the final verson of dapper when it comes out on thursday but i am wondering what are the advantages of an lvm vs not having one and visa versa. Basically which is better and why? 

I asked this in the irc chat and got that the LVM was good if you needed dynamic partioning, i don't see a reason why i would need to do this. They also stated that some people believe that using an lvm with xfs speeds up their system vs xfs with out an lvm. However i don't use xfs, i use ext3 and i plan to unless somebody can prove to me that xfs is faster then ext3.
Anyway should i install dapper with a lvm or not?

---

### Post by JoWilly on 2006-05-30
[QUOTE=nbx909]I am going to install the final verson of dapper when it comes out on thursday but i am wondering what are the advantages of an lvm vs not having one and visa versa. Basically which is better and why? 

I asked this in the irc chat and got that the LVM was good if you needed dynamic partioning, i don't see a reason why i would need to do this. They also stated that some people believe that using an lvm with xfs speeds up their system vs xfs with out an lvm. However i don't use xfs, i use ext3 and i plan to unless somebody can prove to me that xfs is faster then ext3.
Anyway should i install dapper with a lvm or not?[/QUOTE]

I'll tell you the same thing. If you don't plan to ever grow your partitions in the future by adding new disks/partitions, then you don't need lvm. But if you can have a partition on at least 2 disks for this, a raid 0 for root will speed things up tremendously.

As for filesystems, I am using reiserfs (faster than ext3) on my root and work partitions, and ext3 on my 2 backup (docs, music, video, photos.. you name it) partitions as ext3 is "beleived" to be more failure proof.

---

### Post by Pausanias on 2006-05-30
Say you set aside 3GB for your /usr partition. One day you run out of space and have no adjacent partitions with free space either. Without lvm, you have to backup your harddrive, repartition, and restore/reinstall. With lvm, you can change the partition size without having to backup and restore.

The disadvantage is that you have to learn how to configure lvm and set it up. You also may need to worry about lvm when making a backup boot cd; I am not sure about this. Performance-wise, lvm is slightly (about half a percent) slower than no lvm. See [here](http://www.suse.com/en/whitepapers/lvm/lvm1.html#perf).

---

### Post by garyng on 2006-05-30
I am 80% LVM(for /home, /usr/src etc.) with a handful of partition for root fs should I need to install new distro or having them in parallel.

---

### Post by nbx909 on 2006-05-30
well what i do is set 2 gb for swap then the rest for /. So i don't need to mess with /usr getting to big and such...

---

### Post by JoWilly on 2006-05-30
[QUOTE=nbx909]well what i do is set 2 gb for swap then the rest for /. So i don't need to mess with /usr getting to big and such...[/QUOTE]

wow 2 gb swap. Do you have so little memory ?

With 1Gb ram I have been running without swap for 2 years. Its perfect and faster as the system never needs to write to the disk.

If you have 1Gb+ ram , 512Mb swap is largely enough if you do not need any specially memory intensive apps. You will never need even the 512M swap... ;)

---

### Post by s_h_a_d_o_w_s on 2006-05-30
Don't mean to sound like a n00b but, what is LVM ans SAMBA? thx

---

### Post by warpforge on 2006-05-30
[QUOTE=s_h_a_d_o_w_s]Don't mean to sound like a n00b but, what is LVM ans SAMBA? thx[/QUOTE]
Please try Google or Wikipedia before asking here.

---

### Post by Ramses de Norre on 2006-05-30
[LVM]("http://www.tldp.org/HOWTO/LVM-HOWTO/whatisvolman.html")
Samba is a program to use the windows file sharing protocol (smb).

---

### Post by s_h_a_d_o_w_s on 2006-05-30
[QUOTE=warpforge]Please try Google or Wikipedia before asking here.[/QUOTE]

Please bite me

---

### Post by floydwaferfield on 2006-05-30
[QUOTE=s_h_a_d_o_w_s]Please bite me[/QUOTE]

Gotta love some of the friendly people on here. </sarcasm>

---

### Post by SlowJet on 2006-05-30
> **Pausanias]Say you set aside 3GB for your /usr partition. One day you run out of space and have no adjacent partitions with free space either. Without lvm, you have to backup your harddrive, repartition, and restore/reinstall. With lvm, you can change the partition size without having to backup and restore.

The disadvantage is that you have to learn how to configure lvm and set it up. You also may need to worry about lvm when making a backup boot cd said:**
> here[/url].


To to promote LVM correctly, ;)

 LVM (Logicl Volume Management) is is ued to manage PV's (Phyiscal Volumes). LVM will allow a PV to be created on a partion as well as a whole volume (this is good.)

So a Patition becomes a PV. The PV is assigned to a VG (Volume Group) and there must be at least on PV-VG before you can use space.

Space is allocated in segments called LV's (Logical Volumes).
The LV is created out of PE's (Phyical Extents) usually 4MB or 32MB chuncks.
The PE size only matters in 2 ways. 
1. Bigger PE are faster for many volumes.
2. 4MB PE's can only go up to 255GB. (otherwise, not important)

This is important:
It is very easy to extend an LV (if freespace is present on the VG), but extenting the FORMATED ext3attr FS is only to a certain limt as defined by the PE and rounded up to the next unit of some limit (This is for the online expansion of the ext3attr fs). Other wise the the FS can not be grown or shruck without backing up first , adjusting the LV and reformatting the LV with ext3attr, and then recovering the backup. 

The easy part:
To extend any LV it only needs more space in the VG. To extend a VG a new PV can be added to the same VG and the LV can be extend to the new VG (as long as the last PE is available to tie the to PV's together.

However:
If the reason for extending the LV is to grow the FS, then the method above applies. But a new LV can ve defined on the extended VG , formated, and mounted as a dir under an area that needs to grow.
For example:
/home/userme  - I'm used up 95% of the /home LV
Now the girl next door comes along and wants to download the Congresstional library for rearching information to bring impreachment to the United Sates comgressmen quilty of high crimes and mysery meanness , ot to meantion treason.

So I create a PV on a second drive partion and assign it to the same logical group. I creaete a n LV and format it.
I create a mount point under home called
/home/usergnd/congresslibdata
mount /dev/mapper/VGnn-LVnn /home/usergnd/congresslibdata

chown -R usergnd:usergnd /home/usergnd/congresslibdata
chmod 0700 -R /home/usergnd/congresslibdata

to make mount rebootable
mount
<see omount for LV in list>
gedit /etc/fstab
<copy paste lv-list to fstab-file>
save and close.

Now the user usergnd has space to download the congressional library and when she is done with it -
umount /home/usergnd/congresslibdata
(now use the second disk for something else:
lvremove ...
lvcreate 

Want to save the grressional library LV to another VG
lvmove 

and so forth, never having to repartition the exiting system.

And finally it helps to plan the space usage before creating the initial partitions.
dual booting for example
hda1(boot), vgroot, vghome, hda4, hda5 (boot12).vg-root12,gvhome12, ...
VGroot can contain LV's for root, swap, var,tmp as complex as you like,
I think /var in a sepearte VG would be a good idea for htp and mysql severs, other than that /root and swap are all that is need.

And that's how I can install, remove, swith around 3 or 4 distros and users and data without re-partioning the disks.

SJ

---

### Post by SlowJet on 2006-05-30
> **Pausanias]Say you set aside 3GB for your /usr partition. One day you run out of space and have no adjacent partitions with free space either. Without lvm, you have to backup your harddrive, repartition, and restore/reinstall. With lvm, you can change the partition size without having to backup and restore.

The disadvantage is that you have to learn how to configure lvm and set it up. You also may need to worry about lvm when making a backup boot cd said:**
> here[/url].



To to promote LVM correctly, ;)

 LVM (Logicl Volume Management) is is ued to manage PV's (Phyiscal Volumes). LVM will allow a PV to be created on a partion as well as a whole volume (this is good.)

So a Patition becomes a PV. The PV is assigned to a VG (Volume Group) and there must be at least on PV-VG before you can use space.

Space is allocated in segments called LV's (Logical Volumes).
The LV is created out of PE's (Phyical Extents) usually 4MB or 32MB chuncks.
The PE size only matters in 2 ways. 
1. Bigger PE are faster for many volumes.
2. 4MB PE's can only go up to 255GB. (otherwise, not important)

This is important:
It is very easy to extend an LV (if freespace is present on the VG), but extenting the FORMATED ext3attr FS is only to a certain limt as defined by the PE and rounded up to the next unit of some limit (This is for the online expansion of the ext3attr fs). Other wise the the FS can not be grown or shruck without backing up first , adjusting the LV and reformatting the LV with ext3attr, and then recovering the backup. 

The easy part:
To extend any LV it only needs more space in the VG. To extend a VG a new PV can be added to the same VG and the LV can be extend to the new VG (as long as the last PE is available to tie the to PV's together.

However:
If the reason for extending the LV is to grow the FS, then the method above applies. But a new LV can ve defined on the extended VG , formated, and mounted as a dir under an area that needs to grow.
For example:
/home/userme  - I'm used up 95% of the /home LV
Now the girl next door comes along and wants to download the Congresstional library for rearching information to bring impreachment to the United Sates comgressmen quilty of high crimes and mysery meanness , ot to meantion treason.

So I create a PV on a second drive partion and assign it to the same logical group. I creaete a n LV and format it.
I create a mount point under home called
/home/usergnd/congresslibdata
mount /dev/mapper/VGnn-LVnn /home/usergnd/congresslibdata

chown -R usergnd:usergnd /home/usergnd/congresslibdata
chmod 0700 -R /home/usergnd/congresslibdata

to make mount rebootable
mount
<see omount for LV in list>
gedit /etc/fstab
<copy paste lv-list to fstab-file>
save and close.

Now the user usergnd has space to download the congressional library and when she is done with it -
umount /home/usergnd/congresslibdata
(now use the second disk for something else:
lvremove ...
lvcreate 

Want to save the grressional library LV to another VG
lvmove 

and so forth, never having to repartition the exiting system.

And finally it helps to plan the space usage before creating the initial partitions.
dual booting for example
hda1(boot), vgroot, vghome, hda4, hda5 (boot12).vg-root12,gvhome12, ...
VGroot can contain LV's for root, swap, var,tmp as complex as you like,
I think /var in a sepearte VG would be a good idea for htp and mysql severs, other than that /root and swap are all that is need.

And that's how I can install, remove, swith around 3 or 4 distros and users and data without re-partioning the disks.

SJ

---

### Post by mlind on 2006-05-30
I'll vote for LVM, I've had no cons using it and learning curve is low IMO.
Terminology is bit akward, but you'll get the idea when playing around with 
chunk of free space with (g)parted. Atleast that's how I started.

Now once LVM is setup, modifying your "partitions" couldn't be easier.

---

### Post by RAOF on 2006-05-30
[QUOTE=mlind]I'll vote for LVM, I've had no cons using it and learning curve is low IMO.
Terminology is bit akward, but you'll get the idea when playing around with 
chunk of free space with (g)parted. Atleast that's how I started.

Now once LVM is setup, modifying your "partitions" couldn't be easier.[/QUOTE]
I concur: LVM is really cool.  I've just moved my / (reiserfs) partition to a different drive, and extended it by 5GB, all without rebooting, or even unmounting it.

If you **ever** think you might need to change the size of your partitions, then LVM is cool.  It's not even very difficult to set up, particularly if you do it using the text-mode-installer.  Which is one of the downsides - the Live installer doesn't understand LVM.

---

### Post by pellgarlic on 2006-05-31
i've just started reading about lvm, and from what i understand, it's basically like having "virtual partitions" - 

instead of using "physically" demarcated sections of hard drive(s), lvm uses "virtual" demarcation, so that it is easier to resize or reorder the "virtual partitions" (which can be used in the same way as "physical" partitions). you can even join together multiple "physical" partitions (whether they are on the same hard drive or not!) and have them appear as one "virtual" partition. it does indeed sound very useful and interesting. 

one concern i would have about it though, is the possible complications that would arise with regard to backups and "rescues" - the physical layout of the hard drive would not represent the "virtual" layout that the operating system sees and uses. i wonder if this would make it difficult to make backups or rescues of data? 

within the operating system that uses lvm, it wouldn't be a problem, because as far as the os is concerned, the underlying physical layout does not exist - it only sees the "virtual" layout (if i understand lvm correctly... if anyone spots any errors here, please point them out). however, what happens when trying to use something like acronis true image, or norton ghost, or trying to access the data from another operating system? 

i would guess that the information lvm uses to "redirect" data requests to the correct physical location would be included in the backups, (as per something i read somewhere on [http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html) about the info being 128k and stored on the drive itself) but what if you only wanted to backup or "rescue" a particular directory, say /home for example, but lvm has split the data over multiple partitions, or maybe even multiple hard drives?

i guess my point is: when using lvm, the only way (it seems to me) to access the data in a particular directory, is _through the os with lvm active_. if there is a problem with lvm, or the os, how do you get access to the data? can you access logical volumes from "outside" the os (i.e. with a live cd or another installed os) in the same way as you can with partitions? also, what happens if a virtual directory is split over several partitions or hard drives? how do you track down files that are strewn across them? is it the case that lvm exists "below" the os, so any os will see the same thing? (i.e. the "virtual" partitions)

---

