---
title: "normal boot hangs, only safe boot works"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by soomon on 2011-08-24
hi all,

I installes the current ubuntu with an alternate install cd.
the installation went fine.
no errors or warnings what so ever.

when i tried to boot, grub shows up and i select the standard boot item.
all i get is a blinking cursor on the top left of my screen.
nothing happens then.
failsafe boot works. but thats not how it should be.

maybe it has sth to do with my disk setup?
i have 1 hdd in my laptop with the following partitions:

1. win7 boot partition
2. win7 partition
3. ext2 /boot
4. extended
4.1 crypto disk
4.1.1 lvm partition
4.1.1.1 swap
4.1.1.2 ext4 /
4.2 data partition ntfs

I also tried reinstallaing this way... didnt help.
but this kind of disk layout has already worked when i used ubuntu 1 year ago.

anyone got an idea?
thasnks & greets,
soomon

---

### Post by MAFoElffen on 2011-08-24
> **soomon said:**
> hi all,

I installes the current ubuntu with an alternate install cd.
the installation went fine.
no errors or warnings what so ever.

when i tried to boot, grub shows up and i select the standard boot item.
all i get is a blinking cursor on the top left of my screen.
nothing happens then.
failsafe boot works. but thats not how it should be.

maybe it has sth to do with my disk setup?
i have 1 hdd in my laptop with the following partitions:

1. win7 boot partition
2. win7 partition
3. ext2 /boot
4. extended
4.1 crypto disk
4.1.1 lvm partition
4.1.1.1 swap
4.1.1.2 ext4 /
4.2 data partition ntfs

I also tried reinstallaing this way... didnt help.
but this kind of disk layout has already worked when i used ubuntu 1 year ago.

anyone got an idea?
thasnks & greets,
soomon
When I first saw this, I said to myself that it seemed like a lot of partitions for one drive... but--

Then I see that you got to a Grub menu (which I assume is in sda3 or so) and it does boot in safe mode.  In order for it to do that, it see's the partition, see's the grub files and see's a Linux image file.

But to confirm this, 
 - Please run and post the results of the "boot info script" in my sig-line.
 - Read the trouble shooting flow chart in the first post of my sticky:
			 			**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 
There you'll also find instructions on editing the Grub Menu boot line to boot into a text console with verbose messaging turned on... That should show you what kind of errors are occuring during the boot.  If it has errors, post those.

If it boots into the text console without errors, then start the X-session using
```

sudo service gdm start

```
If it starts... Well, then tell me.  If it hangs, reboot, start in failsafe mode and post /var/xorg.1.log (which would be the log from the previous session instead of current).

---

### Post by soomon on 2011-08-24
hey,

thanks for your reply.

ok i found it removing the vt.handoff=7 did the trick.
suddenly also the propriatary nvidia driver works without issues and unity starts, too.

thanks man =)

---

