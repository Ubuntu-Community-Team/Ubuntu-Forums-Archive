---
title: "Yet ANOTHER floppy booter problem"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by vorpalpedant on 2010-08-13
I'm a newbie, so hopefully I'm not posting something silly, but I really have tried everything I can find on this forum, and I'm either lost or have an error in my install.

Need a bootable floppy for the usual reason - decade-old laptop that I'd like to keep.

Formatted the floppy, then tried variations on the following, from these forums:

sudo su
grub-mkrescue --overlay=/boot/grub GRUB2.img
which gets me the error "Unrecognized option `--overlay=/boot/grub'".  I understand from various forums that [this is the wrong format for version 1.98]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub_mkimage"), so I tried:

grub-mkrescue --output=rescue.iso /boot/grub 
which gets me the inexplicable error "/usr/bin/grub-mkrescue: 191: grub-mkimage: not found"

I went into usr/bin/ and verified that yes, the file "mkimage" is there!  It is used in the "mkrescue" package, but doesn't work for me.  

How about it guys: do I have a bug or is this my mistake?

(If it matters, I'm running Lucid 10.04 on an AMD64, and I think I remembered to get the 64 bit version...not sure how to check).

---

### Post by JBAlaska on 2010-08-13
> **vorpalpedant said:**
> I'm a newbie, so hopefully I'm not posting something silly, but I really have tried everything I can find on this forum, and I'm either lost or have an error in my install.

Need a bootable floppy for the usual reason - decade-old laptop that I'd like to keep.

Formatted the floppy, then tried variations on the following, from these forums:

sudo su
grub-mkrescue --overlay=/boot/grub GRUB2.img
which gets me the error "Unrecognized option `--overlay=/boot/grub'".  I understand from various forums that [this is the wrong format for version 1.98]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub_mkimage"), so I tried:

grub-mkrescue --output=rescue.iso /boot/grub 
which gets me the inexplicable error "/usr/bin/grub-mkrescue: 191: grub-mkimage: not found"

I went into usr/bin/ and verified that yes, the file "mkimage" is there!  It is used in the "mkrescue" package, but doesn't work for me.  

How about it guys: do I have a bug or is this my mistake?

(If it matters, I'm running Lucid 10.04 on an AMD64, and I think I remembered to get the 64 bit version...not sure how to check).

Try:
```
grub-mkrescue --overlay=/boot/grub --image-type=floppy grub_two.dsk
```

Then burn  erm I mean write the floppy:
```
dd if=grub_two.dsk of=/dev/fd0 bs=512 count=2880
```

More info [Here](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_Floppy_Disc)

---

### Post by vorpalpedant on 2010-08-14
Thanks Alaska, but that one change (adding image_type=floppy) is another illegal switch...so BOTH switches cause problems.  I have found these formulations elsewhere but they are not working on my machine: 

With your text, I get:


```
Unrecognized option `--overlay=/boot/grub'
```When I take out the "overlay" option, it says:

                                 ```
Unrecognized option `--image-type=floppy'
```In both cases, it tries to instruct me in the ways of its magic:

```
Usage: /usr/bin/grub-mkrescue [OPTION] SOURCE...
Make GRUB rescue image.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --output=FILE           save output in FILE [required]
```So by my math, this should work, shouldn't it?:

                                 ```
grub-mkrescue grub_two.dsk
```or        

                          ```
grub-mkrescue --output=grub_two.dsk
```...the latter of which gives me 

```
Enabling BIOS support ...
/usr/bin/grub-mkrescue: 191: grub-mkimage: not found

```So I think the "mkrescue" command is executing, but it's looking for a "grub-mkimage" file.  "grub-mkimage" is not in  /usr/bin (I checked with "ls"), but one letter off "mkelfimage" is there.     

Why would this be?  My suspicion is that "mkrescue" misnamed the executable it wants to load.  Is this right?   I went inside "mkrescue" and it has code to load "grub-mkimage" and "grub-mkelfimage" in different (impenetrable) circumstances.

Should I change mkrescue, or the filename?  Have I found my first bug?


VP

---

