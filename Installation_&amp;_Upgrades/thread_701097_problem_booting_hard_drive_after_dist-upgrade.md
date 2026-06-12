---
title: "problem booting hard drive after dist-upgrade"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by plong0 on 2008-02-19
I just did a dist-upgrade and now I can't seem to boot /dev/hda1

It's weird, because it boots grub off /dev/hda1 then when I select the default option (new kernel), but then an error in my xorg.config kills the boot (I have the working one backed up) and I end up on my ubuntustudio install on /dev/sdb1 (which I half expect because my dual boot config is a bit quirky - but I think it's because of my BIOS - but it does work. :))

Ok, so I know that if I was able to access my /dev/hda1 drive, I'd be able to repair the config files and be good to go.  Problem is this:

```
$ sudo mount -t ext3 /dev/hda1 primary/
mount: special device /dev/hda1 does not exist
```

ls -l /dev/hda1 shows no love... in fact there's actually no /dev/hd* listings at all, and /dev/disk/by-uuid/ only lists my sata drives (/dev/sd*)

Anyone know anything I might try to mount (or detect) /dev/hda1?

Thanks!

---

### Post by jan de beuker on 2008-02-19
When you type this command

sudo less /etc/fstab

This shows the content of fstab are all your disks listed there?

---

### Post by plong0 on 2008-02-19
> **jan de beuker said:**
> When you type this command

sudo less /etc/fstab

This shows the content of fstab are all your disks listed there?


no... my primary drive is not listed here.  I tried adding the entry (copying the UUID from a backup of my /boot/grub/menu.lst) but then when I reboot I get an error saying it can't find the UUID.

So then mounting the file system fails - and I wind up in a little recovery console with only linux core-commands (kind of funny seeing an error message apt is not found, please install it using apt-get install apt, followed by one saying could not find program apt-get lol).


Is it possible that my harddrive's UUID might have changed?  Is there a way that I would be able to find out the new one?



Here is also some new information from last night.

Without the bogued entry in fstab (so I can actually boot properly)...
when I do
[HTML]dmesg | grep hda[/HTML]
It actually does show something like
hda: Maxtor 6Y080L0, ATA HARD DISK drive
which is my primary hard drive.

I also noticed in the dmesg, that after it detects my sata drives (sdb) it mounts them... after it detects hda... there is nothing in the lines following it about mounting it or failures or anything... It just goes right into some IEEE1394 stuff.

---

### Post by jan de beuker on 2008-02-20
ok ypu could

---

### Post by jan de beuker on 2008-02-20
ok ypu could try this.
Make a compleet new entry in fstab something like this.

/dev/hda1/............./...........ext3............defaults,errors=remount-ro.. 0.......1

After this open /boot/grub/menu.lst en change the UUID to /dev/hda1
Don't know it will work but it is what I should try
You could also try make a new entry using the old UUID but you have to do that also in fstab and not only in grub

---

### Post by plong0 on 2008-02-21
Thank you for the tip jan de beuker ... I tried that, but got the same results (failed to boot).  I may have something else wrong in the fstab entry, I'm not an expert and I didn't spend a lot of time playing with it.

I think I might try reinstalling GRUB... think it will help?

---

### Post by JESii on 2008-02-26
I had the same problem (still working on it), but I found out how to mount my hard drive under similar circumstances.  My research shows that the fstab is used to make it easy to automount stuff at boot or to make mounting easier since the details are stored in fstab.

However, you can still mount pretty much anything as long as you know all there's a device entry in /dev.  Enter the command
```
ls /dev
```and you'll see a bunch of entries, and I'm guessing that your hda1 will be there.

If so, then just mount your hard drive by entering the command
```
mount -t ext3 /dev/hda1 /mnt
```and you should see your hard drive mounted (I'm guessing that the filesystem was of type "ext3fs" -- if you know differently, change the type in the command). I used the directory /mnt to avoid tromping on any other directory that's already there.

Now that I have my hard drive mounted, I'm going to try searching the logs to see what went wrong during the boot...

HTH...jon

---

### Post by plong0 on 2008-03-10
Thanks for the reply Jon, but the problem is that my hda1 is not listed under /dev so I can't mount it.

Going to try reinstalling grub pretty soon I guess... Once I get a new ubuntu CD burned (all the copies I have are all scratched up and won't read properly).

---

### Post by plong0 on 2008-03-18
Woot. Finally got a new ubuntu 7.10 CD to boot and was able to mount hda1 again!

After that, took me about 10 minutes to fix up my /boot/grub/menu.lst and everything is peachy now.

For some reason when I updated the kernel, my menu.lst got overwritten to use hd2 (sdb1 - ubuntustudio) as the root for all the entries instead of hd0 (hda1 - ubuntu)

---

### Post by Saponsky09 on 2008-03-18
I had the same problem a few  months ago, but  I noticed soon tanx God, for some reason at the kernel update, menu.lst is automatically edited and some options are kept intact but some others (specially the ones I add for my boot options) never gets restored. So I always make like 2 backups for my menu.lst and always revise them after any upgrades.

---

