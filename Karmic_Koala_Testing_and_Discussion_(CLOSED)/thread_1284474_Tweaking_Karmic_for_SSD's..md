---
title: "Tweaking Karmic for SSD's."
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by madsc89 on 2009-10-06
I have a Intel X-25M 80GB SSD on my laptop with Karmic installed.
Through Jaunty, I understood that some tweaking with SSDs in mind was beneficial. However, the guides I found was both old, and not intended for Karmic (or Ubuntu for that matter). Therefor I thought I could make one here. The problem though, is that I don't know what to do, so I am asking here as well.

What kind of settings should I change in order to increase speed and reduce the write cycles?
I will add those suggestions posted (and preferably backed up by someone with a substantial amount of beans) in this thread to this first post, so that others might find an easy guide to tune their system for a Solid State Drive.

Thank you.

Or if you know of a still valid good guide, that would be good as well.


**_First draft guide with tweaks from OZC forums _**[color=red]Do not follow this guide if you do not know what you're doing, because it might be faulty[/color]
This thread: [http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379)
Please let me know if some of the mods do not apply to Ubuntu Karmic.

_Alignment:_ [http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?p=373226#post373226)
*[color=red]Is this relevant? And what alignment size would best apply to all SSDs out there? Is this safe to do on a partition which already contains Ubuntu?*[/color]
Basically: 
1: You can use these values for H and S (replace with **) dependent on your SSD erase block size.
```
Cylinder size (Times 512k)
1024K (x2)
  -S 16 -H 128
  -S 32 -H 64
512K (x1)
  -S 8 -H 128
  -S 16 -H 64
  -S 32 -H 32
256K (x0.5)
  -S 4 -H 128
  -S 8 -H 64
  -S 16 -H 32
  -S 32 -H 16
128K (x0.25)
  -S 2 -H 128
  -S 4 -H 64
  -S 8 -H 32
  -S 16 -H 16
  -S 32 -H 8
```
Boot from live cd, then in terminal write:
```
sudo fdisk -H ** -S ** /dev/sda
```
2: ```
o
```
3: ```
n
```
4: ```
t
```
5: ```
w
```



_Noatime:_
I believe this disables the "wait for access time"-function.
1: Write this in terminal:```
sudo gedit /etc/fstab
```
2: Locate your SSD.
3: Find "atime", "relatime", or "noatime". Change to "noatime" (without quotes "").
4: Save and exit. Will be applied on restart.



_Create RAM disk and use it for tmp_ (For those with plenty of RAM):

> To create a RAM drive we're going to use tmpfs.

To mount the system temp folder in tmpfs.

    * Open /etc/fstab in your favourite text editor as root. [sudo gedit /etc/fstab]
    * Add tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0 at the end of the file.
    * Restart system.

All temporary files will now be written to your RAM instead of to your disk.
To verify this, use the command df. Search for lines begging with temps.

```
tmpfs                  1996928     23404   1973524   2% /tmp
```

This tweak could also be used to create a general purpose Ram disk.

    * Create an empty folder as a root. [sudo mkdir /media/Ramdisk]
    * Open /etc/fstab in your favourite text editor as root. [sudo gedit /etc/fstab]
    * Add tmpfs /media/Ramdisk tmpfs defaults,noatime,mode=1777 0 0 at the end of the file.
    * Restart system.
    * Optional. Create a link to your newly created folder at a place of your convenience.



_Add Fire Fox cache to Ram disk:_
> This might not be useful if you're on a very slow modem connection and restarts your computer very often.

    * Open Firefox.
    * Type about:config in the search bar.
    * Right click on any row.
    * Select New > String from the popup menu.
    * Add browser.cache.disk.parent_directory and press enter.
    * Close Firefox.

Use about:cache to verify.



_I/O Scheduler:_
This will probably give you a performance boost.
> To find out which schedulers are available on your system and which one is currently in use, use the command cat /sys/block/sda/queue/scheduler. The one in use is marked by [].
(...)
To make this change permanent you could add appropriate lines to /etc/rc.local.
(...)
find the line beggining with # kopt=root=UUID= and add the parameter elevator=noop to it. Don't ever remove the starting # from this line.
When it's done, run the command sudo update-grub.

[color=red]Are all of these tweaks relevant and correct? All of the quotes and information is taken form OZC forums. Primarily this post: [http://www.ocztechnologyforum.com/forum/showthread.php?t=54379](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379) [/color]

---

### Post by castrojo on 2009-10-06
I just use the noop scheduler for my laptop with a X25-M, no other mods.

---

### Post by madsc89 on 2009-10-07
Ive added some tweaks. I would appreciate it if someone who knows their way around could check them, and perhaps point me in direction of other relevant tweaks.

---

### Post by madsc89 on 2009-10-08
Do no one know if these are good steps?

---

