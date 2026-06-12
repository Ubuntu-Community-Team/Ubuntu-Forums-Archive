---
title: "Strange grub menu"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-08-16
I noticed yesterday that when I am booting machine and grub comes up that only the boot lines are appearing. No recovery lines are showing.
I shall try to get a picture when I boot again.
Hoping I won't need, but there is no way for me to access recovery via grub menu

---

### Post by linux6994 on 2009-08-16
Same trouble here

---

### Post by bluesscream on 2009-08-16
you can carefully edit /boot/grub/grub.cfg (has replaced menu.lst) or hit "e" on boot screen, remove all "quiet" "splash" etc and add "single" (without quotas). Did not find much documentation about Grub2 til now

---

### Post by budluva04 on 2009-08-16
**DO NOT** edit grub.cfg whatever you do, all you need to know about grub2 is here...

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

---

### Post by ranch hand on 2009-08-16
> **budluva04 said:**
> **DO NOT** edit grub.cfg whatever you do, all you need to know about grub2 is here...

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")
He is talking about editing in the live grub menu.  Makes no changes in the file.

I would try going to /etc/grub.d and making a custom file (06_custom) and getting the info for the individual entries from the /boot/grub/menu.lst on your grub-legacy OS' and the /boot/grub/grub.cfg files on your grub2 OS'.

There are some problems with update-grub in grub2 in that it does not pick up everything right and some OS' just won't boot with what it does come up with (my Mandriva OS' don't).  I am sure that this will improve.  I think that grub2 is going to rock.

This is another really good source of info on grub2;

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by ronacc on 2009-08-16
> **budluva04 said:**
> **DO NOT** edit grub.cfg whatever you do, all you need to know about grub2 is here...

[https://wiki.ubuntu.com/Grub2]("https://wiki.ubuntu.com/Grub2")

regardless of the warning to not edit ,you can edit the grub.cfg and until they get it right that may be your best solution just keep a backup of grub.cfg and a live cd handy for rescue if you screw up .

---

### Post by DougieFresh4U on 2009-08-16
Just to be clear, I have put both my Karmic partitions to grub2 and both picked up my Jaunty and Windows 7 installs. All was good looking and working good until yesterday when this issue appeared (disappeared) after some update I did. And I think it was the 'os-probe' update, (maybe)?

---

### Post by ronacc on 2009-08-16
I just checked and I still have all of my recovery choices .

---

### Post by ranch hand on 2009-08-17
> **DougieFresh4U said:**
> Just to be clear, I have put both my Karmic partitions to grub2 and both picked up my Jaunty and Windows 7 installs. All was good looking and working good until yesterday when this issue appeared (disappeared) after some update I did. And I think it was the 'os-probe' update, (maybe)?
You could download "os-prober" ( separate from grub2) and run it before running update-grub.  This may help.

---

### Post by bluesscream on 2009-08-17
@ budlava04: From where do you know what I need to know?
I edited grub.cfg after each install of a new repo- or self compiled kernel on my multi boot system and had no issues. Of course I have a live-DVD if something goes wrong. Developers should not complicate manual editing config files.

---

### Post by VMC on 2009-08-17
> **bluesscream said:**
> @ budlava04: From where do you know what I need to know?
I edited grub.cfg after each install of a new repo- or self compiled kernel on my multi boot system and had no issues. Of course I have a live-DVD if something goes wrong. Developers should not complicate manual editing config files.

I find nothing wrong with direct editing grub.cfg. And besides, if you screw up just delete the file and issue another update-grub command.

I need nomodeset in the boot string of just karmic, so I need to edit grub.cfg, not other choice. And besides, I don't like the titles that the update offers or its placement.

---

### Post by ranch hand on 2009-08-17
> **VMC said:**
> I find nothing wrong with direct editing grub.cfg. And besides, if you screw up just delete the file and issue another update-grub command.

I need nomodeset in the boot string of just karmic, so I need to edit grub.cfg, not other choice. And besides, I don't like the titles that the update offers or its placement.
You really could add a custom file and have the buggers at the start of your menu including your nomdeset.  Every time update-grub is run grub.cfg is rewriten by the scripts in grub.d.

Put your custom menu entries in grub.d and they persist.  When you get a kernal upgrade all you need to do is change the number (2.6.31-5 to 2.6.31-6).  Update-grub needs to be, and will be, run for each variation of each kernal (2.6.31-6-x to 2.6.31-6-y).  Your custom menu does not need anything done to it.

This is where manual editing is supposed to take place.

I have edited grub.cfg myself.  this is why I learned to do it where it actually does something.

If you screw up grub.cfg you do not need to delete the file.  Just run update-grub and it is rewritten.  Try it.  Kind of fun.

---

### Post by VMC on 2009-08-17
> **ranch hand said:**
> You really could add a custom file and have the buggers at the start of your menu including your nomdeset.  Every time update-grub is run grub.cfg is rewriten by the scripts in grub.d.

Put your custom menu entries in grub.d and they persist.  When you get a kernal upgrade all you need to do is change the number (2.6.31-5 to 2.6.31-6).  Update-grub needs to be, and will be, run for each variation of each kernal (2.6.31-6-x to 2.6.31-6-y).  Your custom menu does not need anything done to it.

This is where manual editing is supposed to take place.

I have edited grub.cfg myself.  this is why I learned to do it where it actually does something.

If you screw up grub.cfg you do not need to delete the file.  Just run update-grub and it is rewritten.  Try it.  Kind of fun.
That's true about not needing to delete it. I realized that, but was to lazy to edit my post.

The problem with using custom entries is now I have two linux entries of the same vintage. One os-prober found and my custom with the "nomodeset" option added.

By the way, I found a glitch of sorts regarding os-prober. I have Fedora 11 partition installed. Today I had a linux upgrade. So I ran update-grub only to find out that the initrd doesn't get added. This happened twice now for Fedora. I'll do it again now just to make sure I'm not blowing smoke...

---

### Post by VMC on 2009-08-17
Sure enough. Fedora's initrd doesn't get added, running "update-grub":

vmc@vmc-desktop:~$ sudo update-grub
[sudo] password for vmc: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-6-generic
Found initrd image: /boot/initrd.img-2.6.31-6-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Fedora release 11 (Leonidas) on /dev/sda8
Found Ubuntu 9.04 (9.04) on /dev/sda9
done

[B]grub.cfg after above update-grub completion:
[/B]
```
### BEGIN /etc/grub.d/30_os-prober ###
...
menuentry "Fedora release 11 (Leonidas) (on /dev/sda8)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3
	linux /boot/vmlinuz-2.6.29.6-217.2.7.fc11.i586 root=/dev/sda8
}
...
### END /etc/grub.d/30_os-prober ###
```

[B]grub.cfg should contain it this way :
[/B]
```
menuentry "Fedora 11 Leonidas (on /dev/sda8)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3
	linux /boot/vmlinuz-2.6.29.6-217.2.7.fc11.i586 root=/dev/sda8
	initrd	/boot/initrd-2.6.29.6-217.2.7.fc11.i586.img
}
m
```

---

### Post by ranch hand on 2009-08-18
Does Fedora boot up from that?

I have 2 test drive, one 32bit and one 64bit, both have Mandriva on them.  They only boot to this type of custom entry;
```

echo "Adding Man-Gnome on sda14" >&2 
cat << EOF
menuentry " Man-Gnome on sda14(on /dev/sda14)" {
	linux (hd0,14)/boot/vmlinuz
        initrd (hd0,14)/boot/initrd.img
}
EOF

echo "Adding Man-Both on sda15" >&2 
cat << EOF
menuentry " Man-Both on sda15(on /dev/sda15)" {
	linux (hd0,15)/boot/vmlinuz
        initrd (hd0,15)/boot/initrd.img
}
EOF

```
What grub2 comes up with is;
```

menuentry "Mandriva Linux 2009.1 (2009.1) (on /dev/sda14)" {
	set root=(hd0,14)
	search --no-floppy --fs-uuid --set ac84960d-354b-4a68-b527-16b7aa09d126
	linux /boot/vmlinuz-2.6.29.1-desktop-4mnb root=/dev/sda14
}
menuentry "Mandriva Linux 2009.1 (2009.1) (on /dev/sda15)" {
	set root=(hd0,15)
	search --no-floppy --fs-uuid --set 198c1ffe-6026-4959-88dd-a0d5479ee440
	linux /boot/vmlinuz-2.6.29.1-desktop-4mnb root=/dev/sda15
}

```
changing that to look correct did not boot the buggers.

They are still working on grub2 and it shows in a bunch of little ways.  I think it is going to be great.

I haven't tried it yet but people are booting iso images in grub2.  But I can't boot mandriva on the info that grub2 comes up with.

---

