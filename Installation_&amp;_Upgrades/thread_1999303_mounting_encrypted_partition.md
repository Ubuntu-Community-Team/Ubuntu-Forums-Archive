---
title: "mounting encrypted partition"
date: 2012-06-07
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-06-07
I bought a new laptop and I'm planning to install Kubuntu 12.04 on it.  I have Kubuntu 12.04 on my old computer and I have to move the whole install to the new one (I can't start with a new install for various reasons, and simply moving /home won't transfer all my programs, configs, etc).

I'm trying to transfer all my data from one computer to another (not just /home, but other directories like /usr).  However, I set the NEW computer up with LUKS pre-boot encryption.  Because I can't change the /usr directory while the partition is in use, I have to change it from a live CD.  But I haven't been able to find one that can mount then encrypted partition.  I even tried using a live Kubuntu CD, but when I tried mounting it and I gave it the password it denied access, saying the partition was in use.  How can it be in use if it's not even mounted?!

My plan is to move /usr (and some of the other directories) from / in my old computer to / in my new computer, and they'll be named /*-new (e.g. /usr-new).  Then I'll do "mv /usr /usr-old; mv /usr-new /usr", etc. to replace the new ones with the ones from my old computer.  I can't do that while the partition is in use because in the transition state as soon as the first command is done and there is no /usr present (only /usr-old and /usr-new) the computer is unable to continue working ("mv: command not found", etc).  So I have to do it with a live CD.

Can anyone help?  I've tried following instructions from different websites but none worked for me.  The live CDs I've tried so far were Kubuntu 12.04, BackTrack 5, Tails 0.11, and PartedMagic (didn't even boot.  Apparently PartedMagic doesn't work on my computer).

---

### Post by Blackbird_13 on 2012-06-08
I am not sure what "LUKS pre-boot encryption" means. With the exception of my boot partition I have luks encrypted my hard disc . Booting from a systemrescuecd I can mount any of my encrypted partitions. My setup is slightly more complicated as I use LVM as well. I can let you have the shell commands I use to mount my partitions(s) if you think this will help.

---

### Post by Stonecold1995 on 2012-06-08
> **Blackbird_13 said:**
> I am not sure what "LUKS pre-boot encryption" means. With the exception of my boot partition I have luks encrypted my hard disc . Booting from a systemrescuecd I can mount any of my encrypted partitions. My setup is slightly more complicated as I use LVM as well. I can let you have the shell commands I use to mount my partitions(s) if you think this will help.

By pre-boot I mean I have to enter the passkey BEFORE it will even boot (as oppose to using something like TrueCrypt).

What rescue CD did you use?  And yes, that would probably help (the commands you used).

---

### Post by Blackbird_13 on 2012-06-08
I used this iso: systemrescuecd-x86-2.6.0.iso from [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage). Not sure my commands will work for you, however, this is what works for me (LVM included).

```
mkdir /mnt/mydir
cryptsetup luksDump /dev/sda3
cryptseup luksOpen /dev/sda3 crypt_sda3
    [pass-phrase]
ls -l /dev/mapper/
lvdisplay
vgchange -ay vgHOME
mount /dev/vgHOME/lvROOT /mnt/mydir/

```vgHOME is the name of my volume group and lvROOT is the name of my Ubuntu root partition

---

### Post by Stonecold1995 on 2012-06-08
> **Blackbird_13 said:**
> I used this iso: systemrescuecd-x86-2.6.0.iso from [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage). Not sure my commands will work for you, however, this is what works for me (LVM included).

```
mkdir /mnt/mydir
cryptsetup luksDump /dev/sda3
cryptseup luksOpen /dev/sda3 crypt_sda3
    [pass-phrase]
ls -l /dev/mapper/
lvdisplay
vgchange -ay vgHOME
mount /dev/vgHOME/lvROOT /mnt/mydir/

```vgHOME is the name of my volume group and lvROOT is the name of my Ubuntu root partition

I didn't set up LVM.  All I know is that sdb1 is the partition I need to access (it contains everything but /home, which is on sda1 encrypted with a different password).  So how would I change that if it isn't managed with LVM and all I know is that I need to access sdb1?

---

### Post by Blackbird_13 on 2012-06-08
As I said, my setup is slightly more complicated as I use LVM as well and I don't have pre-boot luks.

Using what works for me I would try:

```
mkdir /mnt/mydir  # directory to mount sdb1
cryptsetup luksDump /dev/sdb1 # check luks partition seen
cryptseup luksOpen /dev/sdb1 crypt_sdb1 # open luks partition
    [pass-phrase] # enter your pass-phrase
ls -l /dev/mapper/ #  if opened correctly, you should see it listed here
mount /dev/mapper/crypt_sdb1 /mnt/mydir # mount partition
```

---

### Post by Stonecold1995 on 2012-06-08
Thank you!

---

### Post by Blackbird_13 on 2012-06-09
You're welcome. I hope it worked for you.

---

