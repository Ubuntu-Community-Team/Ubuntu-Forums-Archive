---
title: "Problem using resize script"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2012-08-30
I tried to use the automated resize script, but got this message: ./wubi-resize_1.5b.sh: Unsupported - this is not a loopmounted install

However, the output of df -h tells me I'm using Wubi:

/dev/loop0 13G 12G 933M 93% /

and

/dev/sda2 108G 65G 43G 61% /host

I'd be grateful for any advice as to how to overcome this problem and increase the size of my virtual disk.

---

### Post by lesliek on 2012-08-30
I tried to use the automated resize script, but got this message: ./wubi-resize_1.5b.sh: Unsupported - this is not a loopmounted install

However, the output of df -h tells me I'm using Wubi:

/dev/loop0 13G 12G 933M 93% /

and

/dev/sda2 108G 65G 43G 61% /host

I'd be grateful for any advice as to how to overcome this problem and increase the size of my virtual disk.

---

### Post by bcbc on 2012-08-30
> **lesliek said:**
> I tried to use the automated resize script, but got this message: ./wubi-resize_1.5b.sh: Unsupported - this is not a loopmounted install

However, the output of df -h tells me I'm using Wubi:

/dev/loop0 13G 12G 933M 93% /

and

/dev/sda2 108G 65G 43G 61% /host

I'd be grateful for any advice as to how to overcome this problem and increase the size of my virtual disk.

What's the output of:
```
sudo grub-install -v
```
and
```
sudo grub-probe --target=device /boot
```

---

### Post by coffeecat on 2012-08-30
@lesliek, I've moved your post and the response from bcbc from the wiki discussion thread into the support thread that I suggested you start. You are in good hands with bcbc. :)

---

### Post by lesliek on 2012-08-30
Dear bcbc,

The output of sudo grub-install -v is:
 
grub-install (GNU GRUB 0.97)

The output of sudo grub-probe --target=device /boot is:

/dev/sda2

Thanks for taking the trouble to reply.

Leslie

---

### Post by bcbc on 2012-08-30
> **lesliek said:**
> Dear bcbc,

The output of sudo grub-install -v is:
 
grub-install (GNU GRUB 0.97)

The output of sudo grub-probe --target=device /boot is:

/dev/sda2

Thanks for taking the trouble to reply.

Leslie
Leslie,
I built the script with Grub2 in mind. And since the script is sometimes incorrectly used, it makes sure that /boot is on a loopmounted file equal to /host/ubuntu/disks/root.disk. However, with grub legacy which you have (which means that you originally installed release 9.04 or earlier), /boot is actually on the windows host partition.

So that explains why the script is telling you it's not Wubi when it is. I should fix it so that it correctly says something like 'Wubi with grub legacy not supported'. Or just make it supported... but that will require some time for me to test it.

What can you do about it? Well, short of editing the script, your other option is to use the direct resize technique described here: [https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

Hope that resolves this for you...

---

### Post by lesliek on 2012-08-30
Thank you very much bcbc.

I'll try to puzzle out using the direct resize technique at the link you've given me.

Thanks again,

Leslie

---

### Post by bcbc on 2012-08-30
> **lesliek said:**
> Thank you very much bcbc.

I'll try to puzzle out using the direct resize technique at the link you've given me.

Thanks again,

Leslie

You're welcome. Don't hesitate to ask if you have any questions.

---

### Post by bcbc on 2012-09-02
> **lesliek said:**
> Thank you very much bcbc.

I'll try to puzzle out using the direct resize technique at the link you've given me.

Thanks again,

Leslie

I've modified and tested the script to work with grub-legacy. I haven't released it yet on the wiki site (I'm waiting to see if I need additional changes for the release of 12.10), but you can download it from [here]("https://github.com/bcbc/Wubi-resize/tarball/proposed"). Note that when you extract it the script will be  called: wubi-resize.sh (not wubi-resize_1.5.sh).

---

### Post by lesliek on 2012-09-04
bcbc, happily I didn't have time to try immediately the direct resize technique, so was able to use instead your edited script, which became available at just the right time for me.

All worked well, subject to two hiccups, which I believe had nothing to do with your script.

While the script was running I got two warnings:

1. unable to get device geometry for /host/ubuntu/disks/new-disk
2. 380 blocks unused.

I'm assuming that neither of those warnings will affect my upgrading to 12.04 from 10.04.

Thanks so much for your help.

Leslie

---

### Post by bcbc on 2012-09-04
> **lesliek said:**
> bcbc, happily I didn't have time to try immediately the direct resize technique, so was able to use instead your edited script, which became available at just the right time for me.

All worked well, subject to two hiccups, which I believe had nothing to do with your script.

While the script was running I got two warnings:

1. unable to get device geometry for /host/ubuntu/disks/new-disk
2. 380 blocks unused.

I'm assuming that neither of those warnings will affect my upgrading to 12.04 from 10.04.

Thanks so much for your help.

Leslie

Leslie,

Those warnings are debug output from mkfs.ext4 - my belief is that there is no issue - but I'd prefer to investigate more fully before making that statement. 

That also made me realise that the script created your new.disk with the ext4 file system, not ext3. That's not an issue, but I'm mentioning it as you have it as ext3 in the /etc/fstab and this might cause you some confusion later (ext4 became the default filesystem with release 9.10, the same time Grub2 became the default bootloader). Personally I'd recommend changing it in /etc/fstab.

I assume by now you've booted from the new virtual disk and confirmed all is working. What I would suggest is to keep the OLDroot.disk backup for a while, especially until you have completed the upgrade to 12.04. 
If you want to reclaim the space from your hard drive, you can also move it to an external drive.

---

### Post by lesliek on 2012-09-04
I'll try to edit the entry in the /etc/fstab file to reflect the change in filesystems.

I have booted from the new virtual disk and am running the upgrade to 12.04 right now. OLDroot.disk remains on the hard drive, at least for now.

Thanks so much for your help with this.

---

