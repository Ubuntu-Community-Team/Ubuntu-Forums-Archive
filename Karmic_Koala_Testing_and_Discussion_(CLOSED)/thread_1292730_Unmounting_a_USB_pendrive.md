---
title: "Unmounting a USB pendrive"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by damava on 2009-10-16
I just installed a current Karmic build and was quite surprised when I wanted to unmount my USB pendrive after the installation.
Have a look at the attached screenshot - this pretty much looks like a usability bug to me. Has this already been reported?

---

### Post by trulan on 2009-10-16
Wow!  It looks like they really want to make sure we can unmount these things!

FWIW, choosing 'unmount' is functionally different than the other two.  If you choose unmount, the drive still shows up in file manager, and can easily be mounted again with a click.  If you choose 'Eject' or 'Safely remove', the drive needs to be physically unplugged and replugged to mount.  I could not tell a functional difference between these two options. Even if there is a difference, it seems very redundant to have all three options there.

---

### Post by meborc on 2009-10-16
eject should only show up it it is a cd/dvd drive... at least for me it seems like a bug

---

### Post by damava on 2009-10-16
> **trulan said:**
> FWIW, choosing 'unmount' is functionally different than the other two.  If you choose unmount, the drive still shows up in file manager, and can easily be mounted again with a click.

Yes that's what I thought.

> eject should only show up it it is a cd/dvd drive... at least for me it seems like a bugI get "Unmount" and "Eject" for the CD drive and yet I believe that doesn't really make a difference for the average user.
But 3 options is just confusing when you just want to remove some media...

(Oh and it's "Unmount" and "Detect Media"(?) for mounted HD-partitions)

Edit:
I tested all three variants and there is indeed a difference:
- unmount just unmounts; as trulan already suggested the device can be remounted
- eject unmounts (i guess...) and removes the drive from nautilus
- remove safely powers down the usb-device altogether

Still I think this is a usability bug that should be addressed.

[s]But there's more. Karmic mounts the pendrive as an USB device as well as a CD-Rom. Now that can't be right... tested this multiple times and it seems to be reliably reproducible...[/s]
Turns out that this is because of the U3 partion (it's a sandisk cruzer)

---

