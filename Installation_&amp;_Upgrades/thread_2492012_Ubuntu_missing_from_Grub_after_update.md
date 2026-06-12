---
title: "Ubuntu missing from Grub after update"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by judicial1333 on 2023-10-27
Hi
I've been dual booting Ubuntu and Win 11 for a while.
I upgraded Ubuntu to 23.10 and all working fine.
Just gone and done and update in Ubuntu and rebooted and Ubuntu is missing from the Grub menu???

To be clear the Grub menu comes up as before and I can get into Windows, but the Ubuntu menu option is now missing.

Any idea what's going on, and how to get it back??

Thanks

---

### Post by ajgreeny on 2023-10-27
No idea what's happened as you haven't given us enough information.

So, please see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the **pastebin** link you will be shown which will show us a lot more about your system.

---

### Post by judicial1333 on 2023-10-27
thanks for the info.
Pastebin link is 
[http://paste.ubuntu.com/p/dQ2MB6cFCb/](http://paste.ubuntu.com/p/dQ2MB6cFCb/)

---

### Post by tea for one on 2023-10-27
[COLOR="#0000FF"]Line 324[/COLOR] - nvme0n1p5/etc/grub.d/40_custom_proxy

Have you installed grub-customizer?

---

### Post by ajgreeny on 2023-10-27
Yes you seem to have lots of proxy sufixed files normally not present amongst the grub files listed in your system.
If you do have grub-customiser installed you may have many problems that are more difficult to solve as GC replaces some default grub files with its own versions.

I understand that GC saves the old grub configuration files somewhere but I will have to search for more details of how to restore those old configs without breaking the system completely.

---

### Post by judicial1333 on 2023-10-28
> **tea for one said:**
> [COLOR=#0000FF]Line 324[/COLOR] - nvme0n1p5/etc/grub.d/40_custom_proxy

Have you installed grub-customizer?

Yes, it was to give it a more graphical type display.

I just don't see why the whole grub menu seems ok, but one item would be removed?

---

### Post by tea for one on 2023-10-28
As grub-customizer is installed, I don't know exactly what to suggest.
Have a read of this info [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

Can you boot into Ubuntu via your PC boot menu or via an EFI shell?
Then perhaps you can upgrade-grub to add the missing menu item?
(unless grub-customizer uses different commands)

---

