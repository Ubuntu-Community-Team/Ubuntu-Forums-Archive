---
title: "bootstrap install server Ubuntu from OpenSuSE 10."
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by vak on 2008-09-22
Hi All

I've got a 64bit OpeSuSE 10 that I'd be happy replace with Ubuntu 8.04 LTS Server Edition (64bit).

I have a remote console in case my networking is crap, I have a rescue reinstall of OpenSuSE 10

and **I need my 64-bit Ubuntu 8.04 LTS Server Edition now**

I think to use a Debootstrap and procedure described [old docu](https://help.ubuntu.com/6.10/ubuntu/installation-guide/hppa/linux-upgrade.html)

Here is my fdisk output:

```
linux:~ # fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          66      530113+  82  Linux swap / Solaris
/dev/hda2   *          67       10011    79883212+   f  W95 Ext'd (LBA)
/dev/hda5              67       10011    79883181   fd  Linux raid autodetect

Disk /dev/hdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          66      530113+  82  Linux swap / Solaris
/dev/hdc2              67       10011    79883212+   f  W95 Ext'd (LBA)
/dev/hdc5              67       10011    79883181   fd  Linux raid autodetect

Disk /dev/md0: 81.8 GB, 81800265728 bytes
2 heads, 4 sectors/track, 19970768 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
```

Midnight is close, any gurus to guide this craziness?


**STATUS UPDATE:**

No one with me? OK, I am alone ;)

So, what I went through:

1. I've token mandriva's debootstrap containing setting for Hardy distro and it sat OK into openSuSE 10 (the openSuSE's rpm of debootstrap has magic dependencies).

2. I've swappoff'ed the swap partition OK

3. I've "infected" the swap partition with Hardy. Yep, I mean debootstrap went OK.

4. I've made essential configurations and successfully chroot'ed into Ubuntu Hardy.

5. I've got Ubuntu to boot from Ubuntu's kernel

6. I've got swap partition mounted during boot

7. the last what I have seen in boot log: my network/interfaces file has a syntax error (well i am a human being) and in a few lines boot freezes like this:

```
 * Starting MD monitoring service mdadm --monitor                        [ OK ]
 * Running local boot scripts (/etc/rc.local)                            [ OK ]

```

Console is not responding.

Now I am trying figure out why Debian Systems can freeze after this line 
```
Running local boot scripts (/etc/rc.local)
```
Most of roots with this symptom seem to be X- and video-related.

But I am still not sure... Waiting for a serviceman that will come finally to my box and will push the reset button. Then I could try more :D

any advices?

---

