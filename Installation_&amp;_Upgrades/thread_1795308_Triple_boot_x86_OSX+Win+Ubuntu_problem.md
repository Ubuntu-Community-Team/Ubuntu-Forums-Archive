---
title: "Triple boot x86 OSX+Win+Ubuntu problem"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by elfuego on 2011-07-02
I know there is a similarly named thread already, but my problem is a bit different. The question is, how to boot x86 OSX from GRUB with DSDT (boot stuff that OSX bootloader needs)?

In detail: 
I already had Win7 and Ubuntu 10.04 running nicely with GRUB 2. I created a new partition, booted from x86 OSX, formated to hsf+ and installed OSX there. Updated Grub from LiveCD and voila - all three systems are there and bootable (dont u just love grub? :) ). But OSX boots in quasi-safe-mode (no boot-info drivers, EFI, DSDT etc).

Does anyone know how to correctly set up MAC OSX entry in GRUB so that its loaded up correctly? Thanks!

---

### Post by Quackers on 2011-07-02
I used the directions below to chainload chameleon from grub.

[http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html](http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html)

---

### Post by elfuego on 2011-07-02
> **Quackers said:**
> I used the directions below to chainload chameleon from grub.

[http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html](http://jeffhoogland.blogspot.com/2011/04/howto-chainload-grub2-into-chameleon.html)

Thanks that seems promising - I'll give it a try and post the result. BTW, I also found a cheap solution. Booting up from x86 OSX live CD, pressing F8 and selecting OSX :)

---

### Post by Quackers on 2011-07-02
That method worked well for me. Check the whole thread out as there are changes recommended by Mike D (which is me :-) ) later in the thread with regard to what to edit. It works well and even allows for boot prompts to be entered, if desired.
I don't have OSX86 on here any more, so can't give any more specifics on that.

---

### Post by elfuego on 2011-07-03
And you were, of course, right about what you wrote. Its not only preferable, I even consider it necessary to write the 
```

menuentry "Mac OS X Boot Loader" {
insmod hfsplus
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ca2159244a8b0fc3
parttool (hd0,1) boot+
chainloader (hd0,5)/boot/chameleon/boot0
}

```
in /etc/grub.d/40_custom . Thats also suggested by GRUB 2 doc. Lemme try now and see if I get this right.

For the sake of other people that may experience a similar problem and in case that the original blog fails some day, the whole solution is to:

```

sudo mkdir /boot/chameleon
cd /boot/chameleon

```

Copy the file boot0 (chameleon bootloader file) to that directory and add the custom entry (customized with your own UUID and partition information) displayed above.

---

### Post by elfuego on 2011-07-03
OK I tried the solution and hit the brick wall. OSX seems to start booting but prints out:

```

boot0: testing 
boot0: testing 
boot0: testing 
boot0: testing 
boot0: error

```

After googling for the possible cause I've found out I messed up partitions and placed OSX on a logical partition instead of primary. This is what I did:
I had 2 major partitions, Win (with backup partitions) and Linux. Afterwards I resized ext4 with gparted I think and installed OSX on the cleared up space. The problem is, I didnt get the result I expected to get. Check the screenshot to see the mess.

Can anyone suggest a clean way to convert the logical osx partition to primary, or do I have to repartition the whole thing and reinstall again?

...or maybe some more editing of GRUB will help?

---

### Post by uRock on 2011-07-03
This activity is illegal and not supported on Ubuntu Forums.

Thread Closed

---

