---
title: "Getting Grub Right"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2008-11-21
Ok So I installed Crunchbang linux onto my system that already had Windows XP and Linux Mint on it.  But after I installed crunchbang, my bootloader got all messed up.  I am able to boot back into Windows after adding this to my grub file:

title Windows
root (hd0,0)
chainloader +1

So that's fine and also Crunchbang boots good too, I just need Linux Mint back.  There is an entry in the bootloader menu but it does not boot.

Here's how my partitions looks (from gparted):

/dev/sda1 = windows
/dev/sda2 = extended, with all these under it:
    /sda5 = just storage
    /sda6 = crunchbang
    /sda8 = linux mint ( i need this back in the bootloader)
    /sda7 = swap

So what would I add to my grub menu list to get linux mint back to boot? I don't understand how the numbers work in the grub file.   Thank you.

---

### Post by caljohnsmith on 2008-11-21
So did you add that Windows entry to your Crunchbang Grub's menu.lst? In other words, is Crunchbang in charge of the booting process? If so, to boot Linux Mint, you could just add a link to Mint's menu.lst in your Crunchbang's menu.lst with:
```
title Linux Mint Grub Menu
configfile (hd0,7)/boot/grub/menu.lst

```
Give that a shot and let me know how it goes. :)

---

