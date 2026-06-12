---
title: "after update, only grub command line"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by asynchronous13 on 2010-09-29
I recently updated, and now when I boot it only goes as far as grub command line. There is no grub menu.

The computer is a Dell Inspiron 8600 laptop with only Ubuntu installed -- no dual boot, no weird partition schemes. Originally installed Ubuntu 09.04 on this computer, upgraded a couple times and it currently has (had) 10.04.1 LTS running. The update should have upgraded from kernel 2.6.32-23 to 2.6.32-24.

I can boot with a live CD and mount the hard drive. The drive seems fine, so it appears to be simply a grub config issue.

I have to boot with live cd to get online to check for potential solutions. So I'm taking some notes on how to use grub. I'll try a couple things and check back here to see if anyone has suggestions. I'll post a followup if I do find my own solution.

---

### Post by asynchronous13 on 2010-09-29
Ok, on bootup I have GNU GRUB version 1.98-1ubuntu7.

I kept getting the error message "unknown command 'kernel'" -- apparently the 'kernel' command has been changed to 'linux' -- who knew?

```
grub> root (hd0,1)
grub> linux /vmlinuz root=/dev/sda1
grub> boot
```

This works, and I'm back in my system again. Now, what do I need to change so that it boots automatically again? (and why did the latest update break it?)

---

### Post by drs305 on 2010-09-29
> **asynchronous13 said:**
> 
Now, what do I need to change so that it boots automatically again? (and why did the latest update break it?)

Run "sudo update-grub" and see if that fixes the /boot/grub/grub.cfg entry.

---

### Post by asynchronous13 on 2010-09-29
Yep, that did it.

```
sudo update-grub
```

Now the laptop is booting like normal again. Guess I'll mark this one as solved.

Now, if I could only figure out why it says "Error: out of disk." every time I boot....

---

### Post by drs305 on 2010-09-29
> **asynchronous13 said:**
> Now the laptop is booting like normal again. Guess I'll mark this one as solved.

Now, if I could only figure out why it says "Error: out of disk." every time I boot....

The "Error: out of disk" seems to be one of the hardest grub errors to pinpoint. However, if your computer is booting that's not one I'd prefer to tackle tonight!  ;-)

Thanks for marking it SOLVED, but don't forget - it's reversible...

---

