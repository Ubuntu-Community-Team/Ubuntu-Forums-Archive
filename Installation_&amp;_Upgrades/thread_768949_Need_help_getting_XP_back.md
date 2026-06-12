---
title: "Need help getting XP back"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Bob Bismal on 2008-04-26
I thought for sure third time was going to be a charm.  I tried 7.something on two different laptops with nothing but headaches.  So I thought with 8.04 I'd try it on a desktop.  Well got Ubuntu all set up and working, then tried to boot into XP and big fat nothing.  Now all I want is to get XP back again.

I tried the sudo gedit/boot/whatever to get XP to load and nothing worked.  Took out the HD and put it in another PC and deleted the Ubuntu partitions.  Put the HD back into original PC and now I get a boot drive error.  Where do I go from here.  I really really want to save my XP without having to redo everything again.

Thanks 
Bob

---

### Post by tamoneya on 2008-04-26
It isnt quiet clear what is on your harddrives to me.  The simpliest way to clarify all this would be to put the ubuntu liveCD in and type ```
sudo fdisk -l
```Then we can go about recovering windows.(hopefully without a reinstall)

---

### Post by Bob Bismal on 2008-04-26
Thanks, put the Ubuntu 8.04 cd in and got:

(initramfs) [ 106.223391] ata1: COMRESET failed (errno=-16)
[ 141.201641] ata1: comreset failed (errno=-16)
[ 146.206522] ata1: comreset failed (errno=-16)
[ 146.206562] ata1: reset failed, giving up
[ 150.005861] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[ 150.005909] 8139cp 0000:02:03.0: Try the "8139too" driver instead.

---

### Post by Slim Odds on 2008-04-26
Boot in the "Recovery Console" using your Windows CD, then type "fixmbr"

---

### Post by Bob Bismal on 2008-04-26
> **Slim Odds said:**
> Boot in the "Recovery Console" using your Windows CD, the type fixmbr

Did that.  After that's done I get a boot error.

---

### Post by Kevbert on 2008-04-26
You're halfway there. Run Fixboot from Recovery Console (Windows CD).  If this does not work, you may also need to check that Ntldr and Ntdetect.com are in the C: (root directory) - I can't remember if these two files are hidden or not.

---

### Post by janosaudron on 2008-04-26
> **Slim Odds said:**
> Boot in the "Recovery Console" using your Windows CD, then type "fixmbr"
fixmbr AND fixboot

---

### Post by Bob Bismal on 2008-04-26
> **tamoneya said:**
> It isnt quiet clear what is on your harddrives to me.  The simpliest way to clarify all this would be to put the ubuntu liveCD in and type ```
sudo fdisk -l
```Then we can go about recovering windows.(hopefully without a reinstall)

K got Ubuntu disk to run, opened terminal, ran fdisk.

disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x1549f232

  Device  Boot   Start     End     Blocks     Id   System
/dev/hda1   *       1     8403    67497066    7   HPFS/NTFS
/dev/hda2        8404     9729    10651095    5   Extended

---

### Post by Bob Bismal on 2008-04-26
Put the XP disk in and ran fixmbr and fixboot.

When I try to start now I get the Compaq screen with the:

<Esc=Boot Menu> <F1=Setup> <F10=System Recovery>

then:

A disk read error occurred
Press Ctrl=Alt=Del to restart

How now brown cow?

---

### Post by Bob Bismal on 2008-04-26
Only real difference I can see from how it was before is that now I have a 10GB unallocated chunk on my harddrive.

---

### Post by Bob Bismal on 2008-04-27
> **Kevbert said:**
> you may also need to check that Ntldr and Ntdetect.com are in the C: (root directory) - I can't remember if these two files are hidden or not.

Yes there both still on the C: drive

---

### Post by Hymyly on 2008-04-27
Seems to me your best bet is to pop in the XP-disc and choose install. Then it will hopefully tell you that it has found an existing installation and ask you if you want to repair it.

If that doesn't work, fetch the (unofficial) Windows XP LiveCD from [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) and manually backup everything you want to keep. Then wipe the disk and reinstall XP.

And I'm sorry to hear that your first Linux experience was such a bummer. Please do try again, perhaps on an unused computer or a virtual machine. Once you get past the quirky installer it is every bit as good as Vista (although still not as good as XP :)).

---

