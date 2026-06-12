---
title: "Help!!! install locking up"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by risen75 on 2008-10-31
Ok here's the situation... I've tried installing both 7.10 and 8.10 and niether one gets as far as attempting to install...

I get the initial startup screen options 
[LIST]
[*]launch
[*]install
[*]safe mode
[*]etc.
[/LIST]
 
They both go through the Ubuntu splash screen with the orange pong type loading bar. This is where things get funny...

7.10 immediately goes to a command prompt (initramfs) 
it mentions busybox at the top.
This is very wierd for me because i've installed off of the exact disk on this exact computer before with no issues.

8.10 
after going through the initial loading the video just goes nuts... shows 4 ubuntu logo's (well sort of, it's like an old rear-projection screen tv that's not alligned) with a bar underneath each of them, but locks up at that point.. only way to get it to do anything is to hard reset the computer using (dare i say it... the power button) 

Now niether one will let me even get to the point of partitioning, installing, configuring, etc...

---

### Post by lelmo85 on 2008-10-31
Q; Have you downloaded/burned iso's for both? Have you run the disk integrity check on both? ( I assume you are using latest 8.10 build.)Did grub install? If it did, when you see the splash screen, hit any key, highlight distro of your choice,,go to kernel line,hit "e" for edit,should say "/boot/vmlinuz (etc} ro UUID=(etc)where ever you see "quiet" erase it with the editor (enter "e")Do you have IDE disk? anyhow add to end of line "all_generic_ide" (no ")Then "b" for boot.See what the print out says. If says "check proc/cmdline" Type "cat /proc/cmdline' check against kernel command line - correct if necessary. ( Happened to me - one number out of place =screwed the works.

"No warranties, no guarantees!" Les

---

