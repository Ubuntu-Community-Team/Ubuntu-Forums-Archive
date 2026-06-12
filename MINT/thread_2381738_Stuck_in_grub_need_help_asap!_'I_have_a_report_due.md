---
title: "Stuck in grub need help asap! 'I have a report due tomorrow.'"
date: 2018-01-04
forum: MINT
---

### Post by kyzitemelos93 on 2018-01-04
I just installed linuxmint on my computer last night it was a night mareto install and it hasn't ended yet
I tried installing in safe mode with the NOMODESET infront of splash and when I rebooted everything went great except it continued to crash because I couldn't get the drivers installed in time and now I'm stuck in GRUB and I tried deleting the partition and reinstalling but I can't seem to excape the wrath of GRUB. can anyone help me with this I saw that I'm suppose to install the boot repair disk and go from there but I'd like a little more help I don't have another OS to do any repairs from there. 
Also my computer is an Alienware 17 R4.

---

### Post by howefield on 2018-01-04
Thread moved to the "*MINT*" forum.

---

### Post by virgosun on 2018-01-04
You should boot from your installation media, then chroot to the installed partition, then do grub-install

---

### Post by yancek on 2018-01-04
What specifically happens when you now try to boot Mint?  Black screen, grub prompt,...?
Is Mint the only OS?  Which version of Mint?
Is it a UEFI or MBR install?
You can boot the Mint install media and go to the boot repair site below.  Select the 2nd option to download from the :ppa and when you run boot repair, do not try to make any repairs but select the option to Create BootInfo Summary and post a link to the output here and someone should be able to suggest something.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

