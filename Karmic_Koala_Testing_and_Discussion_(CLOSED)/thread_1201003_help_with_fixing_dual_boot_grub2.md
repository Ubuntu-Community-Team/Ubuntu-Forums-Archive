---
title: "help with fixing dual boot grub2"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-06-30
just decided to bite the bullet and install karmic cause I want it bad, ya know. so set up another partition and installed....but....

grub2 isn't seeing my other ubuntu partition and update-grub or update-grub2 isn't finding it either....

and for those that automatically assume i used the whole disc, i didn't.  this isn't my first rodeo, well it is with grub 2. I checked and everything is still as it was in partition 1, just need to be able to select boot option for it.

anyone?

---

### Post by descendent87 on 2009-06-30
yeah I've got Fedora 11, Fedora rawhide and Ubuntu Karmic installed, grub2 doesn't find either of the fedora installs and nothing I've tried has worked so haven't been able to boot into them since grub2 was added, apparently dual booting will be fixed by alpha 3 (end of july)

---

### Post by Polaris96 on 2009-06-30
I couldn't make grub2 work at all.  I went back to 1.5 for now.

---

### Post by descendent87 on 2009-06-30
> **Polaris96 said:**
> I couldn't make grub2 work at all.  I went back to 1.5 for now.

Mind explaining exactly how you went back to 1.5, would like to be able to boot back into fedora before alpha 3 :p

---

### Post by buzzmandt on 2009-06-30
> **descendent87 said:**
> Mind explaining exactly how you went back to 1.5, would like to be able to boot back into fedora before alpha 3 :p

ditto

---

### Post by Polaris96 on 2009-06-30
ok.  The real answer is "I'm not sure exactly"

This is what I THINK happened.

after I installed grub2 package and it ran the grub2-config scripts, I rebooted and got some message on the grub menu like "confirm the boot loader is operating and then type [some command] to complete grub2 installation"

So, I tried to select one of my Os's and it totally crashed.  Then, I rebooted into a live cd and used kate (i'm on kde) to reconstruct my original menu.lst.  I think there was some data left from it in /boot/grub but i'm not sure, anymore.

When I saved the reconstructed menu.lst file over the new one, I rebooted.  Grub loaded as grub 1.5 and ran the menu like it should.  everything worked again.

I still show the grub2 package on my system, but it seems to boot as 1.5.

I apologize for the extreme sketchiness of the directions.  All of this happened in a blur and I was so freaked out getting my OS back that I didn't take good notes.  Hope this helps a little and good luck to all.


I DID NOT do this, but maybe you could boot into a live cd, chroot into your hdd "/" directory, purge grub2 and then install grub?  I don't know if it would work but it might ...

Also if you use the alternate cd and enter manual install mode you could try just installing the bootloader.  again, no promises - I'd copy everything before I tried any of these...

---

### Post by descendent87 on 2009-06-30
ah right, when it was first updated it chainloaded from grub-legacy then once you confirmed it worked you could replace it. I did a fresh install from alpha2 so only have grub2 installed

---

### Post by ronacc on 2009-06-30
here's something you can try , make a copy of your /boot/grub/grub.cfg file and put it in a safe place , working on another copy of it clone the boot stanza for your karmic install and change the root= ,the uuid and kernel name to the proper ones for your fedora install(s) , save it and then as root go to /boot/grub and rename gurb.cfg to something else ( I use grub.cfgo  ( o for original ) ) and then copy your modified file to there . that should let you boot your other install(s) . of course have a live cd handy for dammage repair.  note , right now might not be the best time to try this the last update took out my xserver ( nothing to do with grub2) but an unstable system isn't the best place to play around .

---

### Post by jerrylamos on 2009-06-30
Apparently Grub2 is eventually supposed to have some sort of graphical interface, see the thread Grub2 Theming.  Might take a while to debug...

Meanwhile, here's a simplified entry I use for intrepid on Grub2 karmic on this quad boot:

```

menuentry "Ubuntu 8.10 sda5 test, kernel 2.6.27-11-generic" {
	set root=(hd0,5)
	linux /boot/vmlinuz-2.6.27-11-generic root=/dev/sda5 ro quiet splash acpi=noirq
	initrd /boot/initrd.img-2.6.27-11-generic
}

```

Obviously I don't much care for UUID's.

Good luck, 

Jerry

---

### Post by autocrosser on 2009-06-30
If you don't care for UUID you can also go into Gparted & Label your drives--then refer to the drive by label--I do use UUID & have done so from its start in Ubuntu---but here is a example of my modded grub.cfg file that boots the rest of my installs...

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04" {
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 527253c9-7db5-458b-85b9-1aba8bb85955
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sdb1  quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu Karmic (9.10)" {
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 356e0a23-302e-4054-9bdf-025cc85f1089
    linux /boot/vmlinuz-2.6.30-4-generic root=/dev/sdc1
    initrd /boot/initrd.img-2.6.30-4-generic
}
menuentry "Foresight Linux (2.6.29.2-3-fl.smp.gcc4.1.x86.i686) (on /dev/sdd1)" {
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set ee8a98fc-463e-4118-99cf-6742975f674c
    linux /boot/vmlinuz-2.6.29.2-3-fl.smp.gcc4.1.x86.i686 quiet ro vga=0x317 splash root=LABEL=Foresight2.11
    initrd /boot/initrd-2.6.29.2-3-fl.smp.gcc4.1.x86.i686.img
}
menuentry "Ubuntu 9.04 64bit" {
    set root=(hd3,3)
    search --no-floppy --fs-uuid --set 358ac090-55d8-4b7d-93ee-eb02fa538ca5
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sdd3
    initrd /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/30_os-prober ###
```

---

