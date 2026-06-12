---
title: "Install grub failed , what do i do now?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by saadghauri on 2005-10-13
Hi,
when i was installing ubuntu , i reached the step to installing grub , then it detects that i have win2000 which is correct , but when i tell it to install it hangs at 50% then gives me error that it can't install , this is a fatal error  but doesnt give any reason.
Well , i had to keep win2000 so i panicked and select skip installing boot loader. How can i use ubuntu now? can i ?

---

### Post by santo on 2005-10-17
I'm experiencing exactly the same problem:

```

Executing 'grub-install hd(0,11)' failed

This is a fatal error

```

ALT-F3 show me the following error about grub:
[CODE]
Format of install_device not recognized.

Usage: grub-install [OPTION] install_device
...
[CODE]

ALT-F4 shows this:
[CODE]
info: Installing grub on 'hd(0,11)'
info: grub-install supports --no-floppy
info: Running chroot /target /sbin/grub-install --recheck --no-floppy "hd(0,11)"
error: Running 'grub-install --recheck --no-floppy "hd(0,11)"' failed


I also tried the other notation, i.e. /dev/hda12, but this gives me the same error.

How can I solve this ?

---

### Post by MySchizoBuddy on 2005-10-21
same problem here as well

---

### Post by deltwalrus on 2005-11-05
Ditto here...

---

### Post by Xian on 2005-11-05
[QUOTE=santo]I also tried the other notation, i.e. /dev/hda12, but this gives me the same error.[/QUOTE]
Since you are not installing grub to the MBR this really doesn't matter. 
You can boot into Ubuntu using your current bootloader. 

Just skip through this step and proceed with the installation.

---

### Post by deltwalrus on 2005-11-06
But if it's hung at 50% in the installer, how do you skip that step?

---

### Post by fourbissime on 2005-11-07
Same error here. The thing hangs at 50% and then talk about a fatal error.

My system is AMD64 and a Maxtor 120GO HDD.
I'm trying to install Ubuntu 10.5 for AMD64.

It said it failed to install in MBR. When i restarted my computer, my former half broken lilo was still here.

I also tryed to install outside the MBR, but it also failed. Same for lilo. 

Definitely not something a so called human beeing can handle ... :(

---

### Post by Cannedbread on 2005-11-08
i was installing over my previous ubuntu installation when i got this error. 

i suppose the solution is going to involve a knoppix of some kind.
i had a problem with my MBR once before on another machine and knoppix was involved in the fix.

---

### Post by fourbissime on 2005-11-09
hi.

Now it works - but I don't really know why. Two days ago I booted on a win98 floppy to erase MBR and then tried to install ubuntu. It didn't work.

Yesterday I tried to install an old suze 7.0. didn't work properly.

And then I tried again with ubuntu, and it worked. i'm quite puzzled here. But it works, so it's okay :)

---

