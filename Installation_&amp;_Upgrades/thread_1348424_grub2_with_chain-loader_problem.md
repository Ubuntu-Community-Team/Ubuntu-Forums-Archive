---
title: "grub2 with chain-loader problem"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by louaym on 2009-12-07
here the thing; I was having a nice and simple life for few years, then I blow it.



I was multi-booting 4 Linux distros on EXT3 and 1 Windows; with each distro Grub installed in its own partition; with chain-loaders from classic Grub installed in its own simple and small partition /dev/sda2 (it has only /boot/grub/ and installed on MBR just fine; I have set it up once 2 years back and thats it. 
(the propose was each installation/re-installation can update its won grub without affecting the others)

then came Ubuntu 9.10 with Grub2 and EXT4. and my old grub setup could not chain-load the new Ubuntu installation; 

I have searched and found most posts said its due to EXT4/grub2. and I should put grub2 in the MBR. 
I bite my finger and reinstalling Ubuntu 9.10 with grub2 on the MBR.

Now I have Grub2 with all the current installations listed in it fine (but Windows entry is missing ??!!), but any distro updates its kernel and its won grub; could not been used, as the MBR's grub2 has the first menu list when Ubuntu install it.

I want my simple life back, please help me how to create grub2 chain-loader list in same style as my old grub setup.

My setup:

```

>fdisk -l

----------------------------------
Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *       HPFS/NTFS 	--- windows
/dev/sda2            FAT32 	--- classic grub list/boot only
/dev/sda3            Extended

/dev/sda5            EXT4		--- ubuntu 9.10
/dev/sda6            EXT4		--- fedora 12
/dev/sda7            EXT4		--- mint 8
/dev/sda8            EXT3		--- mint 7
/dev/sda9            EXT4            data partition
/dev/sda10           EXT4            data partition
/dev/sda11          swap
---------------------------------------

my old classic grub menu.lst:
----------------------------
default		0
timeout		5
color cyan/blue white/blue
###
title		Linux on  sda8
chainloader	(hd0,7)+1

title		Linux on  sda5
chainloader	(hd0,4)+1

title		Linux on  sda6
chainloader	(hd0,5)+1

title		Linux on  sda7
chainloader	(hd0,6)+1

title		Windows 7
root		(hd0,0)
savedefault
chainloader	+1
----------------------------
```

---

### Post by namok on 2009-12-07
I think the easiest way for you will use Grub Legacy(grub with 'menu.lst'). You can use 9.04 livecd. Grub contained there understands ext4(It's Grub Lecacy with ext4 suport). If you do not have this version, you can use 9.10. Then you need to boot to livecd , uninstall the package 'grub-pc' and install 'grub'. It should work.

---

### Post by louaym on 2009-12-08
I have experimented a little last night with grub2 on the MBR, but I get grub error "unknkwn filesystem" or something in this meaning; and drop me to >grub rescue:

I have created grub.cfg for like this

```
#########
set default=0
set timeout=5
insmod fat
insmod ext2
insmod ntfs
set root=(hd0,2)
#########
#########
menuentry "Mint   (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set b44c7e4a-019e-44e6-aa99-f07717061fe1
	chainloader +1
}
menuentry "Fedora       (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 2c975841-72ff-494c-9052-3c241f806e9f
	chainloader +1
}
menuentry "Mint  (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 231245d2-13b6-4470-87b5-cc9e26be721c
	chainloader +1
}
menuentry "Ubuntu (on /dev/sda5)" {
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set c33883de-2568-4092-a392-d8d01a13b7ff
	chainloader +1
}
menuentry "Windows 7 (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6cc82a8cc82a551c
	chainloader +1
}
###########
```

now I put back old grub (from mint 7) in the MBR and I am back as old time (but only could use mint7 or Fedora12) it seems this 2 do not use grub2 yet.

I think Grub2 development team went a pit too much in complicating things in this one (other than that; it should be a great product)

still looking for a way to solve this grub2 thingy.:)

---

### Post by oldfred on 2009-12-08
I have somewhat the same issue as you. I find my grub2 menu too much and I do not want it scanning drives to update versions, I just want to chainboot. I had winXP and 3 versions of Ubuntu across 3 drives. When I installed Karmic alpha I forced grub2 into that partition and have gotten warning messages on every update that blocklists are "BAD". But it worked. I did a full clean install of Karmic but missed the advanced button and it installed grub2 but to the 3rd drive (where ubuntu was)? 

If you find a good solution let me know. Supposedly you can do the same in grub2:

Herman's site but scroll down to grub2 partition info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

He links to this also:
[http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg)

---

### Post by louaym on 2009-12-09
Thank you for the links.
I'm reading them now; and I will try few thing they suggest, and report back my results.
later.

---

