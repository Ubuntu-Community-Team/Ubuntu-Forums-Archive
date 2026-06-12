---
title: "Remove broken nvidia driver (cannot see desktop)"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2010-02-07
I enabled the NVidia driver and after rebooting the screen is corrupted. All the colors are there but broken into horizontal lines and I can see movement when I move the mouse - it's like a sync problem, or something.

There is no option at boot up to use a safe mode anymore, so is there an easy way to fix this without reinstalling? Perhaps a keypress during boot to enter safe mode, or a terminal?

---

### Post by erik2912 on 2010-02-07
Boot to single-user mode
from the tty you can type "dpkg-reconfigure xserver-xorg" without quotes.

---

### Post by Robin Nixon on 2010-02-07
> **erik2912 said:**
> Boot to single-user mode
from the tty you can type "dpkg-reconfigure xserver-xorg" without quotes.

Thanks Erik!

How do I get into single user mode, though? :)

---

### Post by erik2912 on 2010-02-07
Ever heard of google?
I'm only using other distro's but i think it's same with ubuntu.
In your grubloader press e for edit. select the line with the kernel (kernel /vmlinuz......)
edit line
append 1 or single to it
press enter to save 
press b to boot from it

---

### Post by Robin Nixon on 2010-02-07
> **erik2912 said:**
> Ever heard of google?
I'm only using other distro's but i think it's same with ubuntu.
In your grubloader press e for edit. select the line with the kernel (kernel /vmlinuz......)
edit line
append 1 or single to it
press enter to save 
press b to boot from it

Thanks, I actually did a Google search but didn't find the information you gave.

[Edit] It appears that Grub 2 needs Shift to be held down at boot :)

---

### Post by erik2912 on 2010-02-07
Okay, but you fixed it now? :D
If yes, put [Solved] before your topic-name to indicate that problem is solved.

---

### Post by phenest on 2010-02-07
> **erik2912 said:**
> Boot to single-user mode
from the tty you can type "dpkg-reconfigure xserver-xorg" without quotes.

Boot to 'recovery' mode. You'll see this next to one of the kernels at boot.
```
Xorg -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
```
...and reboot (sudo reboot now).

---

### Post by cariboo on 2010-02-07
You don't need to type:

```
dpkg-reconfigure xserver-xorg
```

Nvidia now provides a much better tool:

```
sudo nvidia-xconfig
```

This will probe the hardware and create a new /etc/X11/xorg.conf file and backup the old one.

---

### Post by Tamale on 2010-02-08
Can someone provide a status update for this bug?  Thanks.

---

### Post by LKjell on 2010-02-08
Jockey is updated with lucid support now. So if that bug you are talking about it is fixed assuming you install the driver using jockey.

---

### Post by Robin Nixon on 2010-02-08
> **LKjell said:**
> Jockey is updated with lucid support now. So if that bug you are talking about it is fixed assuming you install the driver using jockey.

Still no luck.

I am using a fairly new Acer with Nvidia graphics and I had to reintall Alpha 2 to get the desktop back properly.

But then I accepted the latest Updates ande after rebooting the problem has returned. I cannot see anything to send a bug report, so I can only describe what happens:

The screen looks like a timing error with the scanlines being too short so it's lots of horizontal lines.

This time I didn't enable any Nvidia drivers, nut maybe the latest update did it automatically?

Right now I can't help beta testing anymore as I can only use Alpha 2 and refuse to allow updates :(

---

### Post by Tamale on 2010-02-08
That's interesting, I have the exact opposite problem. I can't use the Alpha 2 in its current state due to the same issue. I'm hoping an update will fix it.

---

