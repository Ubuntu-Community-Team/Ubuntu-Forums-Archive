---
title: "Disk boot failure after Ubuntu install"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by SPK201 on 2012-10-18
Hello,

I got an really old pc (512mb ram) from  an friend to set it up new. It took 2days to boot, but worked lol. Windows XP was on it, but after backuping all data I trashed it.
Now I booted into CloneZilla and installed my prepared image of Peppermint OS. I tested it beforehand on another PC and the image is working. It finished cloning without problems.

Now, when I boot it says "disk boot failure insert system disk and press enter". Great.

I removed the bios battery, load the defaults and tried different configurations in my bios. Checked the cables. Everytime I get the same error.

So maybe the MBR is defect. I booted into Ubuntu Live CD. My HDH is recognized just fine, I can browse my files perfectly. 
I ran boot-repair, but no change.

Here's the report: [http://paste.ubuntu.com/1286752/](http://paste.ubuntu.com/1286752/)


I'm clueless.

---

### Post by Starcruiser322 on 2012-10-18
> **SPK201 said:**
> 
maybe the MBR is defect. I booted into Ubuntu Live CD. My HDH is recognized just fine, I can browse my files perfectly. 


Did you try running grub-install from the live cd? This installs the bootloader into the mbr and fixes many start issues:

sudo su
mkdir /media/host
mount -t ext4 /dev/sda1 /media/host
grub-install --root-directory=/media/host /dev/sda

then restart, try to boot from primary hard drive

---

### Post by SPK201 on 2012-10-19
Hello,

thanks for your reply.

No, I didn't. I'll try that later today. 

The PC only has one harddrive. The harddrive definitely works, it boots fine on another PC. What else could it be? The HDD is recognized by the old PC, but just won't boot, so I guess the motherboard isn't guilty either... maybe it's because the BIOS is too old?

---

### Post by SPK201 on 2012-10-19
> **Starcruiser322 said:**
> Did you try running grub-install from the live cd? This installs the bootloader into the mbr and fixes many start issues:

sudo su
mkdir /media/host
mount -t ext4 /dev/sda1 /media/host
grub-install --root-directory=/media/host /dev/sda

then restart, try to boot from primary hard drive

Yo,

thank you... now it enters grub2 command line!!! One big step in the right direction.

I tried to boot as described here:
[http://ubuntuforums.org/showpost.php?p=9786657&postcount=4](http://ubuntuforums.org/showpost.php?p=9786657&postcount=4)

But it fails at point 7. If I ls the directory (hd0,1)/ it shows vmlinuz, but it's no directory. 
It keeps telling "Error: file not found.".


Guess, I will fire up my live cd once again, even though it takes hours because it's so freaking slow. Repairing grub from their seems easier.


UPDATE: Installing Fedora 17 works ootb. I don't know why, but I don't really care... it's working and that's good.
Thanks for your help anyway!

---

