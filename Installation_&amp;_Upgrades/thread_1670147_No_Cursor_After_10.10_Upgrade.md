---
title: "No Cursor After 10.10 Upgrade"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by GriffinClubMerv on 2011-01-18
Last night I performed the upgrade routine from 10.04 to 10.10 on an Aspire One netbook. The netbook performed flawlessly under 10.04. Since the upgrade the computer boots fine, except no cursor ever appears. Nor is there the "ghost cursor" that I have read about. What do I do now, attempt a reinstall using an ISO image instead of the upgrade routine, perhaps?

---

### Post by Saghaulor on 2011-01-18
For starters, don't blow up the forums with redundant posts. Wait and I'm sure someone will help you.

---

### Post by Saghaulor on 2011-01-18
> **Saghaulor said:**
> For starters, don't blow up the forums with redundant posts. Wait and I'm sure someone will help you.

Sorry, I think there was something going on with the forums, so I don't think the multiple postings was your fault. My apologies for laying down the hammer.

---

### Post by drs305 on 2011-01-18
There can be a lot of reasons for this. I recently had my 10.10 boot to a completely blank screen, with no cursor. (I found I could restart by pressing CTRL-ALT-DEL twice, then pressing ENTER.)

For me, the issue was a new line in the Grub2 boot file. When booting, at the GRUB menu (or hold down SHIFT during boot to display the menu):

Press 'e' to edit the  highlighted menuentry.

Look for the following line:
> set gfxpayload=$linux_gfx_mode

If you have this line, move the cursor to the start of the line and hold down the DEL key to remove the line. 

Press CTRL-x to boot.

---

### Post by GriffinClubMerv on 2011-01-19
My GNU GRUB Reads:
 
recordfail
insmod ext2
set root= ' (hd0,1) '
search --no floppy --ff-uuid --set 65830467-851a-455f-98db-5879d6e35\
8db-5879d6e3546a ro  quiet splash
initrd /boot/initrd.img-2.6.32-22-generic
 
***
 
As you can see there is no set gfxpayload line to remove or modify.
 
Ideas?

---

### Post by drs305 on 2011-01-20
> **GriffinClubMerv said:**
> My GNU GRUB Reads:
 
recordfail
insmod ext2
set root= ' (hd0,1) '
search --no floppy --ff-uuid --set 65830467-851a-455f-98db-5879d6e35\
8db-5879d6e3546a ro  quiet splash
initrd /boot/initrd.img-2.6.32-22-generic
 
***
 
As you can see there is no set gfxpayload line to remove or modify.
 
Ideas?

Did you copy the entry? What you have posted is missing the 'linux' line, which should look something like this:
```
linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro quiet splash
```

If it was merely a typo, you could try adding 'nomodeset' to the end of the line.
```
linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 ro quiet splash **nomodeset**
```

---

### Post by GriffinClubMerv on 2011-01-21
Sorry, it was a typo - there was a Linux line, just as you described. I added **nomodeset** as suggested but it made no difference - still no cursor.

---

