---
title: "Trouble Installing Ubuntu 20.04 LTS On Dell Inspiron 5515"
date: 2021-09-11
forum: Installation &amp; Upgrades
---

### Post by kirewelle on 2021-09-11
I'm still somewhat of a Linux noob, I am having trouble with trying to resolve a kernel panic while attempting to install Ubuntu 20.04 LTS on my new Dell Inspiron 5515. Relevant image below:

[https://i.imgur.com/5bN4zy6.jpg](https://i.imgur.com/5bN4zy6.jpg)

I've tried a couple things to attempt to solve this issue such as disabling secure boot and updating my BIOS and firmware to the latest version, but I always run into this no matter what I try to do. I've tried other distributions as well and cannot install them either (attempted Fedora 34 and MX Linux). I cannot seem to find anyone else with similar issues, especially with this laptop. The Windows 10 install that came with this laptop does have BitLocker enabled, but I don't see how that could cause this issue (let me know if I'm wrong). Could it be my USB drive or the software used to create my image (I used Rufus).

Let me know if there are other things I should try to resolve this.

Thank you for any help you can lend me.

---

### Post by ubfan1 on 2021-09-11
Try booting with the kernel param acpi=0 to see if boot finishes (maybe with drastic issues like only using one cpu core).  If that works try acpi=ht to keep the hyperdthreading but shutting down most other acpi items.  Failure to unpack the initramfs might be an install problem, but test the acpi switches first.

---

### Post by kirewelle on 2021-09-11
Forgive me for being a noob at this but you mean going into the grub command line and typing in acpi=0, correct? Doing that still resulted in the screen above.

---

### Post by ubfan1 on 2021-09-11
Right, so back to the ISO, did you hashcheck it?  After burning to a USB(?), does the grub screen offer a "check media"?  Does the media boot successfully in "try" mode?  Doesn't seem like a missing bootloader issue, like you might get if trying to boot in wrong mode (legacy vs UEFI). Ever run a memory check?  Disk check (I know, but new machines sometimes have issues).

---

### Post by kirewelle on 2021-09-12
Alright I finally solved this issue, I'm pretty sure at this point it was my install medium I was using. Oddly enough, I saw someone on the Manjaro forums talking about how they got their install medium working with an SD card instead of a USB drive. I kind of ran out of options so I decided to install Manjaro linux with a spare SD card and oddly enough it worked!

Of course, when I did install Manjaro, the suspend function was not working properly and would basically freeze my whole laptop and force me to hard reset the entire device (this is why I don't mess with Arch distros, never had good luck with them). As of right now I am typing this from the Ubuntu 21.04 LiveCD and currently figuring out how to get touchpad gestures working since I will be making a lot of use of them.

Thanks for the help mate.

---

### Post by ubfan1 on 2021-09-12
Good!  You can use the thread tools drop down at the top to mark this as "Solved".

---

### Post by kirewelle on 2021-09-12
This is off topic from this thread but I also noticed that Ubuntu had the same issue as I had with using Manjaro after installing it. After digging around and messing around with grub, screensaver settings, etc., I found that my issue with being unable to wake from suspend is kernel related, oddly enough. I've noticed that installing and switching to kernel 5.14 resolved this issue, figured I'd mention this here in case others with the same laptop as mine are having the same issue (I noticed someone on stackoverflow had this exact issue with this exact Dell laptop).

It could potentially also do with updating my Dell BIOS to version 1.4 but that would be for another thread.

---

