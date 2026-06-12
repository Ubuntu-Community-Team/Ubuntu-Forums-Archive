---
title: "dual boot with fedora?"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by jistanidiot on 2006-03-24
I'd like to set up a dual boot system.  Only I don't want the other OS to be Windows I want it to be FC5.  I'm starting with one blank hardddrive.  All the How-To's I've found want the other OS to be Windows and assume you've already got your harddrive partitioned.  Can anyone point me in the right direction?

So far I've not hat much luck.  I've tried three times.  The first time FC5 completely removed Ubuntu.  The 2nd time Ubuntu completely wiped out FC5 (argh!).  Both FC5 and Ubuntu5.1 seem to clobber each other when I install.  

My last attempt I got really close.  I first partitioned the drive, by booting with a Knoppix disk and using qtparted to create two ext3 partitions.  I then installed ubuntu on the first partition.  It booted fine.  I then attmpeted to install FC5 on the other partition.  I'm not sure exactly what happened, but some how LILO was replaced with Grub.  Grub only offered the FC5 option.  However when I took that option, something really weird happened.  FC5 began to boot, but about 1/4 of the way the boot messages started to look like Ubuntu messages then a bunch of errors happened then I ended up with the Ubuntu login screen!  Some kind of horrible merger took place I guess.

I went back into Knoppix and qtparted and reformated both partitions.  I'm not sure what to do now.  ](*,)

---

### Post by Jagot on 2006-03-24
The way I'd go about would be to let the partitioning systems from each distro to do the partitioning themselves.  

Firstly install FC5.  Use manual partitioning to allocate as much space as you would like for it.  Then install Ubuntu into the free space left after your FC5 install.  

When it comes to installing GRUB, Ubuntu's should wipe out FC5's but should also detect FC5 allowing you to select between them.

On the off-chance that Ubuntu's GRUB does not detect Fedora you should be able to add it later anyway.

Can't really see what can go wrong with that, but thats just my thought on it.

---

### Post by trorion on 2006-03-24
You will absolutely have to play with your
/boot/grub/menu.lst file.  Personally I don't like Ubuntu's format anyway so that didn't bother me.

Now, when you install do it like this:
- install your first OS on the first partition.  I suggest FC.
- install your second OS on the second partition.  I suggest Ubuntu (no, it probably won't recognize the FC.  If it does then you are good to go!  Heck, it didn't even recognize breezy when I did it once).
- log in to the second system.

Now the "tricky" part.  Navigate to your FC5 partition and find menu.lst in the  /boot area.  Open that file (read only is fine for now).  If you like gedit then you can most likely do:
```
$ gedit /media/hda0/boot/grub/menu.lst
```
**If that doesn't work and you can't figure out where your fedora is then post here and someone will figure it out**

Find the boot line (the one that is not commented (#) out.  menu.lst probably looks like this:
```
## Sample boot menu configuration file
#

#  default - boot the first entry.
default 0

# after 30 sec boot default.
timeout 30

[b]# Fedora Core 5
title  linux
root  (hd0,0)
kernel /boot/vmlinuz root=hd0s1
module /boot/vmlinuz[/b]

```

The part in bold is the important part.  you need that to be in your second install (ubuntu right?) list since the second install is where the MBR is looking for instructions.  so...open another terminal and type ```
$ su gedit /boot/grub/menu.lst
```

Copy the bold part from the first file you opened to bottom of the second file you opened.  Save the second file and close them both.

---

