---
title: "Grub Error 15"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by junior aspirin on 2009-10-04
Hi all.

I was using karmic since alpha 2 up to about alpha 5, then my install messed up. i reinstalled recently with the new Beta, unfortunately I now get an error from grub "error 15". Grub does not show a list of operating systems (i dual boot with xp), just goes straight to the error. I tried a chroot to update grub, but the same error occurs.

I am currently using a live cd since i cannot boot into xp or ubuntu, any ideas on how this can be fixed?

---

### Post by Joe_Bishop on 2009-10-04
How many hdds do you have?

---

### Post by junior aspirin on 2009-10-04
i have 3 as follows:

sda1 unmounted

sdb1 /mnt/downloads
sdb3 /mnt/multimedia

**sdc2 Root**
sdc1/Sdc5 extended Swap
Sdc3 windows Unmounted
**sdc4 Home**

i get the feeling grub maybe installed to the wrond disc, but i'm unsure.

---

### Post by NormanFLinux on 2009-10-04
Just do a reformat and reinstall. Its been corrupted and a fresh install should give you a new grub bootloader.

---

### Post by junior aspirin on 2009-10-04
This is a fresh reinstall. I tried with the last alpha and the recent beta to the same result

---

### Post by Joe_Bishop on 2009-10-04
It seems you've chosen a wrong disk in a boot priority sequence. Try to specify a right one.

---

### Post by junior aspirin on 2009-10-04
should have mentioned, I tried that too, I swapped to all the combinations in the BIOS, but to the same result.

---

### Post by aaron483 on 2009-10-06
My Grub error 15 came from a bad kernel upgrade.

When my Ubuntu 9.04 wanted to upgrade my kernel, it also made a bad change to my boot menu.

  Notice where it put the pound sign.

  "**uuid        40034284-0f20-4803-84e7-853a6606f15c# This entry automatically added by the Debian installer for a non-linux**"

 Just adding a space between the uuid and the pound sign fix my Grub error.

It took me 3 month figure this out. Google failed me again. 

[http://burrell-site.net/page1.html](http://burrell-site.net/page1.html) Same instruction here. Don't bother to click.

---

### Post by junior aspirin on 2009-10-06
Thanks. hut i actualy fixed it last night. I needed to chroot into my install and use grub-install to reinstall grub to the correct hard drive. It took some working out, but i founded it on google somewhere, i would give the link, except i was on a livecd and hence can't find it again!

---

### Post by Setomidor on 2009-10-28
I just installed the Ubunto Karmic Koala Daily build from yesterday (27/10) and I got the same GRUB Error 15. I'm trying to solve it as we speek, and I'll try to get back with my solution.

(This was a total reformat of my laptop, so no previous GRUB or anything)

Hope this is fixed before the release...

---

### Post by flipper9 on 2009-10-28
If the fix is known, why doesn't Grub offer to fix the problem on it's own rather than spouting off some cryptic error code?

---

