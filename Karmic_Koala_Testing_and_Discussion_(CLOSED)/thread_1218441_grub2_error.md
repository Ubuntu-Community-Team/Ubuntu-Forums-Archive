---
title: "grub2 error"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-07-20
Hi all,
I've installed from Live CD latest Karmic but when I choose from grub menu the kernel I get the error:
```
error: no such device: xxxxx.xxxxx.xxxxx.xxxx
press any key to continue...
```
and the system goes back to the grub menu
(the xs is the UIID hard disk and it is correct.

I've tried with "e" changing from
```
set root=(0,1)
```
to
```
set root=(0,1)
chainloader +1
ctrl-x
```
but I get "invalid signature" error

Any suggestion?

---

### Post by ranch hand on 2009-07-20
I would not chainload, don't really know why.

I would suggest running "sudo update-grub" and see if that helps before doing anything else.

---

### Post by dentaku65 on 2009-07-20
> **ranch hand said:**
> I would not chainload, don't really know why.

I would suggest running "sudo update-grub" and see if that helps before doing anything else.

Thx Ranch hand,
my system does not even boot; should I try to do "sudo update-grub" with Live CD? If so how?

---

### Post by ranch hand on 2009-07-20
Just run the commands it terminal from the live CD.  If there is nothing else on the drive and you have never booted to it, and the Live CD doesn't get it done, I think that I would reinstall.  Put it on 2 partitions (/ and /home).

I assume you are using alpha2.

---

### Post by dentaku65 on 2009-07-20
> **ranch hand said:**
> Just run the commands it terminal from the live CD.  If there is nothing else on the drive and you have never booted to it, and the Live CD doesn't get it done, I think that I would reinstall.  Put it on 2 partitions (/ and /home).

I assume you are using alpha2.

I've already reinstalled.
I'll try update-grub

---

### Post by ranch hand on 2009-07-20
The command;
```

sudo grub-install /dev/sda

```
sets grub 2 on the proper drive (I runn SATA you may need "hda").

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

[http://members.iinet.net/~herman546/p20/GRUB2m%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2m%20Bash%20Commands.html)

those are helpful links

---

### Post by dentaku65 on 2009-07-20
> **ranch hand said:**
> The command;
```

sudo grub-install /dev/sda

```
sets grub 2 on the proper drive (I runn SATA you may need "hda").

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

[http://members.iinet.net/~herman546/p20/GRUB2m%20Bash%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2m%20Bash%20Commands.html)

those are helpful links

No way; I did sudo update-grub with Live CD but I get an error "there is no grub installed on ./"
I reformat my drive, reinstall but same error when I try to boot. The only thing changed is the UUID  :confused::confused:

---

### Post by wayne_cat on 2009-07-20
try to run it via chroot access:

boot the Live CD .. open a console ... mount your fresh installation to /mnt ... chroot into it

(if sda1 is the Karmic root partition)

```
mount /dev/sda1 /mnt
mount -o bind /dev /mnt/dev
chroot /mnt
```now try to run the command

---

### Post by budluva04 on 2009-07-20
instructions for recovering grub2 via livecd

[here]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by dentaku65 on 2009-07-22
The issue was the hard disk. I dunno why.
Using a different one Karmic runs ok.

---

