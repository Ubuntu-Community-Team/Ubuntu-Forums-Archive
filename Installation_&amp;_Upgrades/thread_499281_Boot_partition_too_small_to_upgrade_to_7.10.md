---
title: "Boot partition too small to upgrade to 7.10"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by dlridings on 2007-07-12
My boot partition is 32mb.

I tried to upgrade from 6.10 to 7.04 but it stops because my boot partition is too small (what on earth is needed in the boot partition to require so much?)

Anyway, could someone tell my how I can move the partition /boot back into the root / filesystem so it is just a directory under root rather than its own partition?

Thanks!

Daniel

---

### Post by BobbyBionic on 2007-07-12
Hi

It's not very useful to have a boot partition with our new computers (and for a desktop use).

You can copy all the content of the /boot (keeping good rights !) on the boot directory, but don't forget to delete the line about it on the fstab.

Do it from a live cd or another OS.

---

### Post by Wim Sturkenboom on 2007-07-12
My Xubuntu Dapper boot partition is already 35MB, so you were lucky that 6.10 fitted.

Maybe I'm thinking to simple (not tested):
unmount /boot and mount under another (temporary) mountpoint
create directory /boot and copy
modify /etc/fstab to reflect the change

---

### Post by dlridings on 2007-07-12
> **BobbyBionic said:**
> Hi

It's not very useful to have a boot partition with our new computers (and for a desktop use).

You can copy all the content of the /boot (keeping good rights !) on the boot directory, but don't forget to delete the line about it on the fstab.

Do it from a live cd or another OS.

Isn't it a little more complicated than that?

What about line like this in menu.lst:

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-386 root=UUID=5577f929-b60f-4d78-880c-34f37d12812b ro quiet splash
initrd          /initrd.img-2.6.17-11-386
savedefault
boot


(hd0,2) points to the boot partition.

If I move the boot directory to the root partition, how do I change menu.lst that grub uses?

And ... my root partition is in a logical partition, that is partition 4 is a logical one and with it, I have a couple more paritions. One of them is the root.

Seems a bit more complicated.

Thanks again,
Daniel

---

### Post by dlridings on 2007-07-12
> **Wim Sturkenboom said:**
> My Xubuntu Dapper boot partition is already 35MB, so you were lucky that 6.10 fitted.

Maybe I'm thinking to simple (not tested):
unmount /boot and mount under another (temporary) mountpoint
create directory /boot and copy
modify /etc/fstab to reflect the change

Thanks, but that doesn't take menu.lst under /boot/grub into account.

I guess the 35mb of your boot contains older kernals and things like that. I don't keep them around once I know a new one works.

Daniel

---

### Post by BobbyBionic on 2007-07-12
That's true, be careful with grub, you may have to modify the menu or, easier, to reinstall it ;-)

---

### Post by dlridings on 2007-07-12
> **BobbyBionic said:**
> That's true, be careful with grub, you may have to modify the menu or, easier, to reinstall it ;-)


Thanks!

I guess that is what my question was: how do I reinstall GRUB?

---

### Post by Bothered on 2007-07-12
I would resize the boot partition using gparted on the Live CD (resizing the next partition on the disk to make room). It's probably a less troublesome solution that moving grub onto the root partition.

---

### Post by dlridings on 2007-07-12
> **Bothered said:**
> I would resize the boot partition using gparted on the Live CD (resizing the next partition on the disk to make room). It's probably a less troublesome solution that moving grub onto the root partition.

Is that really possible? From what I understand it is not.

If you resize the next partition to make room, you don't really make any room. The next partition leaves more room at the end of it and the partition before that can't get to the extra room.

No, I want to get rid of the boot partition and just have boot reside in the root partition. There is no reason to have a separate partition.

I guess the only thing that can be done is to blow away everything and install from scratch.

I still can't figure out why ubuntu needs more than 32mb for a boot partition. Not that much stuff needs to be there.

Daniel

---

### Post by Bothered on 2007-07-13
The partition can be resized using gparted to make room. However, as you don't want to do that you can use the alternative approach of moving the /boot directory onto your root partition and reconfiguring grub to boot from the root partition. I don't know the exact procedure for doing this, so I'll leave that for someone else to post, but I know that it can be done and that this does not require a full reinstall.

---

### Post by BobbyBionic on 2007-07-13
> **dlridings said:**
> Thanks!

I guess that is what my question was: how do I reinstall GRUB?

I do not know a lot this website, but I am sure there is a big documentation ;-)

Quickly, from a live cd for example, launch grub as root, search the stage1 with "find /boot/grub/stage1", then "root (hdx,y)" with correct x and y, and finaly "setup (hdz)" with the correct z.

Numbers of website explain it (you also have the horrible grub-install).

---

### Post by Wim Sturkenboom on 2007-07-14
> **dlridings said:**
> Thanks, but that doesn't take menu.lst under /boot/grub into account.

I guess the 35mb of your boot contains older kernals and things like that. I don't keep them around once I know a new one works.

DanielYou're right about menu.lst; forgot that one. And you're also right about the 'old' kernels; there are (indeed) two kernels. The 35M was, by the way from *df*; *du* only reports 20M.

---

### Post by dlridings on 2007-07-22
Thanks for the tries, but I guess no one knows. I was hoping someone did.

Best,
Daniel

---

### Post by dlridings on 2007-07-22
> **BobbyBionic said:**
> I do not know a lot this website, but I am sure there is a big documentation ;-)

Quickly, from a live cd for example, launch grub as root, search the stage1 with "find /boot/grub/stage1", then "root (hdx,y)" with correct x and y, and finaly "setup (hdz)" with the correct z.

Numbers of website explain it (you also have the horrible grub-install).

I can follow that if x and y are disk and partition, but when I go from having boot as its own partition to having boot as a directory under the root partition, then what does y become?

I understand x and y as referring to x = harddisk and y = partition. But if boot is a directory living under a partition, does that affect things (in contrast to boot being mounted onto its own partition.)

Daniel

---

### Post by dlridings on 2007-07-22
> **Bothered said:**
> The partition can be resized using gparted to make room. However, as you don't want to do that you can use the alternative approach of moving the /boot directory onto your root partition and reconfiguring grub to boot from the root partition. I don't know the exact procedure for doing this, so I'll leave that for someone else to post, but I know that it can be done and that this does not require a full reinstall.

You described exactly what I want to do. That's comforting to know that I have at least expressed my question in a way that someone understands it.

It's not, however, a question of not wanting to resize the partition, it is a question of it not being possible. Once again, from what I understand you can shorten the partition after the boot partition, but you cannot expand boot. Because boot needs to grow and when you shorten the following partition, you free up space at the end of the partition, not at the beginning of the partition where the previous partition could use it.

Just my understanding. I'd be happy to find out I'm wrong.

Daniel

---

### Post by Bothered on 2007-07-24
gparted allows you to change the start position of a partition. This can be used to resize the partition, and leave room at the start.

---

### Post by darenw on 2007-08-05
I have this same problem as dlridings - from ubuntu 6.10 upgrading to 7.10, the process stops and gripes about /boot too small.  Mine is about 50MB.  Cleared out two old kernels, leaving just the latest one.  df says /boot is 20% full, with about 10MB of stuff, 40MB free.   What on earth is 7.10 planning to put into /boot that's so big?  I can only guess this is a bug in Upgrade Manager or tools it depends on.

My plan is to boot up in Knoppix, mount cp -a /mytinybootpartition/boot  /mybiggerpartition/,   and i would have rebooted but thanks to this thread, i know to muck around with grub before rebooting.

---

### Post by darenw on 2007-08-05
um, actually it's ubuntu 7.04 not 7.10.   seven-something, anyway.

---

### Post by darenw on 2007-08-05
Total failure!    

I did like i said, in Knoppix copied the contents of the boot partition to the main one, edited /etc/fstab and the grub menu file, and tried various things in grub, believing that it stalled a new MRB   Ubuntu doesn't start.  After BIOS, i get a black screen with a cursor at the top. The cursor drops down a line or two, then nothing at all  happens.  ctrl-alt-del still causes a reboot, otherwise computer acts dead.

Giving up, i restored fstab, copied back the original menu.lst, and ran grub again to restore (i hoped) the MRB.   
GRUB> root (hd0,2)  
GRUB> setup (hd0)
GRUB> quit

The idea was to restore things back to working condition, but still it won't boot, same problem.  Looking for a workaround other than booting Knoppix or some other live CD.

Is there a document for fixing an arbitrarily messed-up bootup for Ubuntu?  Assuming nothing about whether the MRB is correct, the kernel is found or not, grub or lilo, the version of ubuntu, whether or not it was a Human or a monkey who  last reconfigured anything, ...    A how-to document that could be followed to diagnose and fix any trouble anywhere in the boot-up process.   That would be a fine project.

---

### Post by darenw on 2007-08-06
update: giving up on GRUB, trying LILO now.....

---

### Post by darenw on 2007-08-06
woo-hoo!!   LILO boots up just fine.   Straightforward lilo.conf,  written and installed  in knoppix.   

btw, had weird troubles all day with knoppix live CD which would start x windows only about one in five times, usually hanging the system instead.   

It's too late at night to try another run of Update Manager  to see if it's now happy with my partitions, and tomorrow i'll be away until later, but soon...

---

