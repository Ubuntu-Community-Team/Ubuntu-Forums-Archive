---
title: "grub2 error 15 after clean install"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by steve_c on 2009-10-12
Apparently this problem isn't as common as I'd originally thought (or maybe I'm just not searching well).

I have a Dell Dimension E510 desktop. Deciding I wanted to try my hand at the beta testing thing, I downloaded and installed Karmic alpha 6. I did a clean install, formatting and attempting to create and boot from an ext4 partition. When I tried to reboot the first time after it was installed, the system goes through the BIOS, says "grub loading" then on the next line "error 15" and freezes with no way to do anything but reboot. Trying to re-install Karmic over the existing installation (so without reinstalling the boot loader or reformatting the drives) it doesn't even give me those two lines--it just goes through the BIOS then freezes on a blank screen.

I gave up and decided to try again when the beta came out. I've now tried installing Karmic beta and am having the exact same issues (tried multiple times in case it was a fluke).

Any suggestions?

---

### Post by VMC on 2009-10-12
Output:
```
sudo fdisk -l

```

```
sudo cat /boot/grub/grub.cfg

```

```
sudo blkid

```

```
lspci|grep VGA

```

---

### Post by steve_c on 2009-10-14
So I feel foolish. For no reason I can explain the time I was installing it directly after posting this for some reason it worked. 8th time's a charm I guess. Since then I've had to reinstall it four more times (the proprietary nvidia driver is killing me--or at least causing the gdm/X to lock up), and it's worked every time since then.

Thanks for the help and if I manage to replicate this error again I'll post the requested info.

---

### Post by yonkiman on 2009-10-26
> **steve_c said:**
> So I feel foolish. For no reason I can explain the time I was installing it directly after posting this for some reason it worked. 8th time's a charm I guess.

Wow!  I've tried 3 clean installs of 9.10RC and I keep getting Error 15.  Karmic Koala seems great from what I've heard, but if you google:
    "error 15" karmic OR "9.10"
there seems to be an epidemic (5000 links) of Error 15s - and 9.10 hasn't even been released yet.  I'm a little concerned that once the masses start playing with it, this is going to sour a lot of people.  Is it too late to do something about this?

I'm sure I can hack around and fix it, but it doesn't give a great first impression - previous releases worked on my hardware with no drama!

-Fred

---

