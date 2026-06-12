---
title: "Daily alternates broken?"
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moopere on 2008-12-30
Is it just me or have the daily ISO's been broken for the last couple of days?

I try to install and get:

```
can't get a pty: No such file or directory
```

and it just keeps clearing the screen and telling me the above.

I've tried everything I can think of, command line install, expert install, etc, etc

Using Sun's VirtualBox 2.1.0 which could be the problem I guess, though I've never seen this funny behavior before.

Cheers,
Craig

---

### Post by ronacc on 2008-12-30
I' getting the same here on the amd64 alternate dated dec 30 . The dec 29 daily live is also uninstallable because manual partitioning doesn't work .

---

### Post by tepsipakki on 2008-12-30
> **ronacc said:**
> I' getting the same here on the amd64 alternate dated dec 30 . The dec 29 daily live is also uninstallable because manual partitioning doesn't work .

due to recent changes in the kernel. The next daily will work though, since there was a bug in udev which prevented the installer from using unix98 ptys.

---

### Post by tepsipakki on 2008-12-30
and you can use the current one by adding 'pty.legacy_count=N' to the kernel cmdline.

---

### Post by Slug71 on 2008-12-30
Will the next daily build have the 2.6.28-4 Kernel by default?

---

### Post by tepsipakki on 2008-12-30
> **Slug71 said:**
> Will the next daily build have the 2.6.28-4 Kernel by default?

umm, the current one already has, that's why the installer was broken..

---

### Post by Slug71 on 2008-12-30
> **tepsipakki said:**
> umm, the current one already has, that's why the installer was broken..

got ya, thanks.

---

### Post by ronacc on 2008-12-30
Thanks for the info , I'll try tomorrows daily (dec 31) . I had nuked my previous install and want to start fresh , I was due anyway but was going to hold off for A3 , when I killed my upgraded from intrepid I decided to try a daily .

---

### Post by Slug71 on 2008-12-30
> **ronacc said:**
> Thanks for the info , I'll try tomorrows daily (dec 31) . I had nuked my previous install and want to start fresh , I was due anyway but was going to hold off for A3 , when I killed my upgraded from intrepid I decided to try a daily .

Yep i may need tomorrows too since im gonna mess with Grub2 now.

---

### Post by ronacc on 2008-12-30
> **Slug71 said:**
> Yep i may need tomorrows too since im gonna mess with Grub2 now.

I was troubleshooting a problem with slow internet access that had cropped up with and update to 2.6.28-4 when I somehow managed to destroy X to the point where I couldn't even save it from recovery mode  .

---

### Post by Slug71 on 2008-12-30
> **ronacc said:**
> I was troubleshooting a problem with slow internet access that had cropped up with and update to 2.6.28-4 when I somehow managed to destroy X to the point where I couldn't even save it from recovery mode  .

Sucks, the joys of testing.

---

### Post by ronacc on 2008-12-30
yeah but it keeps my hands off of my "stable" box :lolflag:

---

### Post by moopere on 2008-12-31
> **tepsipakki said:**
> and you can use the current one by adding 'pty.legacy_count=N' to the kernel cmdline.

Yep, thats it, works fine - thanks a million.

Cheers,
Craig

---

