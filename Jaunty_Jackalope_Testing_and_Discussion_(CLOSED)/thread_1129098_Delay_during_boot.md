---
title: "Delay during boot"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bluenova on 2009-04-18
Hello,

I have a pause of about 6 secs just after grub, I installed bootchart but don't really know how to read what is causing the delay.

Grub finishes
It says: 'Starting Up...'
then pauses for 6 secs before the usplash displays

Bootchart attached.

p.s. I'm using EXT4

---

### Post by MacUntu on 2009-04-18
> **bluenova said:**
> Hello,

I have a pause of about 6 secs just after grub, I installed bootchart but don't really know how to read what is causing the delay.

Grub finishes
It says: 'Starting Up...'
then pauses for 6 secs before the usplash displays

Bootchart attached.

p.s. I'm using EXT4

Start without the "splash" and "quiet" kernel boot parameters. Maybe you can see an error message then.

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by jmmL on 2009-04-18
I'm pretty sure the blank space is not actually a delay as such. I think it's just other more important bits of the system initialising first, then bootchartd is started once the very critical stuff is finished with.

Out of curiosity I booted without quiet and splash, and shaved a full 0.3s off my boot time! :P

Edit: @bluenova
Did you do a fresh install of jaunty? Only, to me, it looks like you have the old version of bootchart, that has less time resolution. Also, your hard drive is much faster than mine, which again makes me wonder if you did a clean install. Surely you should be booting more than 2 seconds faster than me? </speculation>

Edit 2: Whoops, I uploaded the wrong chart!

---

### Post by MacUntu on 2009-04-18
> **jmmL said:**
> I'm pretty sure the blank space is not actually a delay as such. I think it's just other more important bits of the system initialising first, then bootchartd is started once the very critical stuff is finished with.

Sure, but there shouldn't be a long delay before Usplash starts.

---

### Post by bluenova on 2009-04-19
Clean install of Jaunty beta but I have installed some services since then which is probably why it's slower than yours jmmL.

I tried booting without quiet and splash and it would seem jmmL is correct, the system was very busy straight after grub with no delay, yet my boot time was the same as before (18 sec). I guess I'm just used to Intrepid where usplash would start a split second after grub, and it seems the usplash seems to start later in the boot process with Jaunty, which doesn't look very aesthetically pleasing to just see text stating 'Starting up...' for 6 seconds before the splash screen.

---

### Post by MacUntu on 2009-04-20
Usplash should start right after GRUB. Compare the output of 

```
cat /etc/initramfs-tools/conf.d/resume
```

to the output of

```
blkid
```

Does the UUID in the resume file match the UUID of the swap partition?

---

### Post by bluenova on 2009-04-20
> **MacUntu said:**
> Usplash should start right after GRUB. Compare the output of 

```
cat /etc/initramfs-tools/conf.d/resume
```

to the output of

```
blkid
```

Does the UUID in the resume file match the UUID of the swap partition?

Yup :?

---

