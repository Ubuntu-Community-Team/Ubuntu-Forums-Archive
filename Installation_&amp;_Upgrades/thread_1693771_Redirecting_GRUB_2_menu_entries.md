---
title: "Redirecting GRUB 2 menu entries"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by NJPinator on 2011-02-23
Hi there!

This is my first post, so go easy on me :D

I'm familiar with Ubuntu and the like, and have GRUB 2 installed as my boot-loader. I was wondering if there was any way to get one menu entry to be re-directed to another. Specifically, whenever I select my third menu entry, I want it to execute the code on menu entry 10.

My reason for doing this would be that after customising my GRUB 2 menu, I came into the problem of updated kernels. Basically I would like a single "Ubuntu, Latest Kernel" entry that always redirected to menuentry 10, where my latest "Ubuntu, linux 2.6.xx-x-generic" entry is.

P.S. In order to temporarily solve my issue, I've set my "/etc/default/grub" file's "GRUB_DEFAULT" to "9", although I'd rather not do this; My sister gets confused with GRUB...This is her ---> :confused:

---

### Post by dino99 on 2011-02-23
the solution is to set your pref into 06-custom; see grub2 link below

---

### Post by oldfred on 2011-02-23
If you follow dino99's suggestion of 06_custom and then add this type of entry, it will boot the most current kernel.

Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Ubuntu puts a link into root to the most current kernel and updates it with each kernel update.

---

### Post by NJPinator on 2011-02-23
Thanks for help from the both of you, I really appreciate it!

@oldfred My Ubuntu partition is the first logical partition on my extended partition (/dev/sda5), however my "set root=" is "(hd0,**msdos**5)". Would I keep that as is or change it to "(hd0,5)"?

My current menuentry in full is:
```
menuentry "Ubuntu 10.10 Maverick : Latest Kernel (not really)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,**msdos**5)'
	search --no-floppy --fs-uuid --set **My UUID**
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=**My UUID** ro quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
```

I assume what you're telling me to do is change it to:
```
menuentry "Ubuntu 10.10 Maverick : Latest Kernel" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	**set root='(hd0,msdos5)'**
	search --no-floppy --fs-uuid --set *My UUID*
	[B]linux /vmlinuz root=UUID=*My UUID* ro quiet splash
	initrd /initrd.img[/B]
}
```

Correct me if I'm wrong...I don't want to go messing up my MBR!!! [-o<

P.S. My custom files are...pretty complex, if you ask me; I've got about seven! And what's "Ranch Hand"?

---

### Post by oldfred on 2011-02-23
Ranch Hand is a user. He was the one that showed me  how to do this so I credited him. I think he was using it for an alpha/beta partition that was constantly getting updated.

You do not change your existing boot stanza's, unless you want to totally turn off the automatic updates and just use the example to boot the most current kernel.

They have added the msdos to highlight whether it is msdos or gpt. It is currently optional as I use both, do not know about future.

Just copy this into your 06_custom and run sudo update-grub. If it works then we can discuss eliminating other entries.

menuentry "Daily on sda5" {
    set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 ro quiet splash
        initrd /initrd.img
}

If set root is correct the search for UUID is not required. That is for the devices that may change like USB drives or mixed IDE/SATA which are not always consistent in drive numbers. All the ismod files  are new. Many are currently built in defaults already (which may also change, do not know). The above should be the minimum required to work. 

I have in my notes also:
From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

Lots more on customizing grub2 & any of the links in drs305 signature in his posts:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

---

### Post by NJPinator on 2011-02-23
Don't get me wrong, I've fully customised GRUB to the full extent I feel possible using the GRUB 2 article on the Ubuntu Community Help pages, but I just wanted to know how to go around doing this specific thing. Thanks for the info anyway, I should be back to say if it works by tomorrow morning ;) (My time zone's GMT). I'll get a screen shot of what my GRUB menu looks like by the morning as well...

---

### Post by NJPinator on 2011-02-24
So, I've successfully modified my 08_custom file and it works perfectly! Thanks for the tip. Even though it takes a little longer to boot... Is there any way to take a screenshot of GRUB? I don't want to use a virtual machine or a camera.

---

