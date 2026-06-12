---
title: "Graphical tool to repair the PC"
date: 2015-09-15
forum: MINT
---

### Post by eric.lapoint on 2015-09-15
Hi -- First off, apologies if this info is already on this thread.

Trying to have GRUB working. I have a dual boot system, Linux Mint and Windows 8 for work purpose. Windows 8 got corrupted and since I dislike it, I installed Windows 10. I knew that installing Windows _after_ Linux I would need to repair GRUB. I did try repairing it with the recommended repairs of Boot Repairs, without success. Windows 10 is working. I did try to remove Windows 8 but still have Windows boot loader with the two options. Anyhow, I would like to fix GRUB.

When I try the last command of the recommended repairs: [INDENT]sudo chroot "/mnt/boot-sav/sda5" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic 
[/INDENT]
I get this:
[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-signed-generic : Depends: linux-headers-generic (= 3.13.0.63.71) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/INDENT]
Here's the link to my output:[[COLOR=#1155cc]http://paste.ubuntu.com/[/COLOR]12391692/]("http://paste.ubuntu.com/12391692/")

Thanks in advance,

Eric

---

### Post by oldfred on 2015-09-15
Do not know Mint and versions. But you should not need signed kernels if you have Secure Boot off.

Script showed an empty grub.cfg in your install? Is that correct?
Do you get grub> or grub-rescue> which would indicate that you have no grub.cfg.

I might try just the chroot & sudo update-grub or the full uninstall/reinstall of grub. The reinstall of grub does try to install the latest kernel, so that may still be an issue.

---

### Post by howefield on 2015-09-16
Thread moved to the "*MINT*" forum.

---

### Post by eric.lapoint on 2015-09-17
Thank you for your post oldfred. I tried many things afterwards to be able to figure it out and reinstall it.

P.S. I had [COLOR=#000000]grub> [/COLOR]

---

