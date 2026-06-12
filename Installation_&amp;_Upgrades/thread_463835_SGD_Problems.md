---
title: "SGD Problems"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2007-06-04
Well, I'm trying to get the Super Grub Disk to work, but I just can't. I followed [this tutorial](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob) and it just doesn't work. I set my BIOS to boot from it (it's not a USB Stick, it's a memory card, so I set my BIOS to boot from "Removable Dev.") but it just goes to a black screen with a cursor blinking.

I want to use this SGD to restore Ubuntu after reinstalling WinXP. Please help.

---

### Post by mifi on 2007-06-04
> **Znupi said:**
> Well, I'm trying to get the Super Grub Disk to work, but I just can't. I followed [this tutorial](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob) and it just doesn't work. 
This link is broken.
mifi

---

### Post by Znupi on 2007-06-04
> **mifi said:**
> This link is broken.
mifi
It works for me :|.

---

### Post by adrian15 on 2007-06-05
> **Znupi said:**
> Well, I'm trying to get the Super Grub Disk to work, but I just can't. I followed [this tutorial](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob) and it just doesn't work. I set my BIOS to boot from it (it's not a USB Stick, it's a memory card, so I set my BIOS to boot from "Removable Dev.") but it just goes to a black screen with a cursor blinking.

I want to use this SGD to restore Ubuntu after reinstalling WinXP. Please help.

Which tar.gz did you use / download ?

Are there any errors when setuping the memory card ? Was the memory card already formated and with data?

Does this memory card have an MBR?

adrian15

---

### Post by Znupi on 2007-06-05
> **adrian15 said:**
> Which tar.gz did you use / download ?
The one for USB sticks.
> **adrian15 said:**
> Are there any errors when setuping the memory card ? Was the memory card already formated and with data?
No errors. I didn't format the memory card, I just Shift+Deleted everything that was on there
> **adrian15 said:**
> Does this memory card have an MBR?
I have no idea. It should? How do I create one? (I must tell you that I haven't got the slightest clue about how something boots.) (Yes, I do know, vaguely, what a MBR is)

---

### Post by adrian15 on 2007-06-05
> **Znupi said:**
> The one for USB sticks.

No errors. I didn't format the memory card, I just Shift+Deleted everything that was on there

I have no idea. It should? How do I create one? (I must tell you that I haven't got the slightest clue about how something boots.) (Yes, I do know, vaguely, what a MBR is)

Maybe with the mbr command ?

It's so sad. I do not know even how to detect an existent MBR.

adrian15

---

### Post by Znupi on 2007-06-05
> **adrian15 said:**
> Maybe with the mbr command ?
```

$ mbr
bash: mbr: command not found

```
Are you sure it has to have a MBR?

---

### Post by adrian15 on 2007-06-06
Yes, it's the mbr command, I suppose you have to install it. However I think that the mbr needs an existant mbr.

So... I do not know.

Sorry.

Can you please try to delete everything and copy-paste again and then try to boot from the flash card again ?

adrian15

---

### Post by Znupi on 2007-06-06
> **adrian15 said:**
> Can you please try to delete everything and copy-paste again and then try to boot from the flash card again ?
I did that quite a few times already...

---

### Post by adrian15 on 2007-06-06
> **Znupi said:**
> I did that quite a few times already...

Does the flash card boot emulated inside qemu ?

Something as:

qemu -boot c -hda /dev/sde # where /dev/sde is the flash card

adrian15

---

### Post by Znupi on 2007-06-06
> **adrian15 said:**
> Does the flash card boot emulated inside qemu ?

Something as:

qemu -boot c -hda /dev/sde # where /dev/sde is the flash card

adrian15
Umm... The card is mounted at /media/disk
```

$ qemu -boot c -hda /media/disk
qemu: could not open hard disk image '/media/disk'

```
:(

Maybe I should just go and burn a CD? :(

---

### Post by mifi on 2007-06-07
> **Znupi said:**
> Umm... The card is mounted at /media/disk
```

$ qemu -boot c -hda /media/disk
qemu: could not open hard disk image '/media/disk'

```
:(

Maybe I should just go and burn a CD? :(
That is not the same thing. Have you tried unmounting /media/disk and accessing it with the previous line?

mifi

---

### Post by adrian15 on 2007-06-07
> **Znupi said:**
> Umm... The card is mounted at /media/disk
```

$ qemu -boot c -hda /media/disk
qemu: could not open hard disk image '/media/disk'

```
:(

Maybe I should just go and burn a CD? :(

Let's see. Type mount as root.

You will see a line with the /media/disk string and also with the device string something as /dev/sde or /dev/sdf I suppose.

Then type:

umount /media/disk

once it is unmounted

run the qemu command as I had already told you (but with the device string you see when running mount command)

If qemu boots it then it's a problem from your bios I suppose.

adrian15

---

### Post by Znupi on 2007-06-07
```

$ sudo mount
# blah blah tons of stuff...
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
$ sudo umount /media/disk
$ qemu -boot c -hda /dev/sdc1
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

```
And then the QEMU window pops up with this:
```

# some stuff...
Booting from Hard Disk...

```
And it just stays like that. Any other suggestions?

---

### Post by adrian15 on 2007-06-08
> **Znupi said:**
> 
And then the QEMU window pops up with this:
```

# some stuff...
Booting from Hard Disk...

```
And it just stays like that. Any other suggestions?

I think I know how to fix this. This is the same problem that happens when generating floppies.

You should download SGD source code, inside dev_grub run ./configure and make 


then you should run

./util/grub # still inside the dev_grub folder

grub>device (hd0) /dev/sdc
grub>root (hd0,0)
grub>setup(hd0)
grub>exit
sync

and try to boot it from qemu

and then from real system.

adrian15

---

