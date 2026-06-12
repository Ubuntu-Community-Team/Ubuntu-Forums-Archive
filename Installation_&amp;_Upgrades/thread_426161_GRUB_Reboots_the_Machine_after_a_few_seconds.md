---
title: "GRUB Reboots the Machine after a few seconds"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Shambler2 on 2007-04-28
Hi, 
I have just installed Ubuntu Fiesty Fawn as my first attempt at using Linux, and I must say I'm very impressed. It works great on my Thinkpad R51 Laptop, well, at least it did.
I encountered this problem when I attempted to boot back into Windows XP. 
On startup of the laptop, it starts to load the bootloader, then hangs and restarts, ending up in a loop. It gets as far as: GRUB Loading Stage1.5. After it displays that for a few seconds, it reboots. 
This is getting annoying, as I don't really want to lose the XP installation, and for that matter my Ubuntu installation. 
Windows XP was installed first, then I installed Ubuntu on the same drive, on a seperate partition. Strange thing is that GRUB was working fine before I tried to boot into Windows again. Windows DID come up with CHKDisk as it was loading, though I escaped out of that before it started.
Any help would be appreciated,
Sam

---

### Post by Shambler2 on 2007-04-29
I'm not sure if this is allowed here, but just bumping myself to see if anyone knows a solution? I still can't use my work computer, thanks for any help,
Sam

---

### Post by undecidable on 2007-04-29
You need to check that grub is trying to boot to the correct partition.

If you can boot to the Feisty live CD,
compare  /boot/grub/menu.lst 
to fdisk -l
and ensure they are pointing to the same thing. 

Also check that menu.lst does not have an entry that is pointing to itself
(the entry to boot to windows is a 'chainloader' entry,
which if incorrect can point back to grub itself)

You can also check that grub can find the system.
Normally you can get into the grub comman line from the grub menu
but as you ar not getting to the grub menu, you will have to do it from a live CD.
sudo grub
wil take you to a grub prompt, then:
find /vmlinuz
to ensure grubv is finding your linux kernel where it expects to.

Hope this helps.

---

### Post by Shambler2 on 2007-05-28
Thanks a bunch for that, I really have to start subscribing to my own posts!
I managed to solve the problem by re-installing GRUB from the live CD, however I still have to do that every time I decide to boot up windows. Any ideas as to a solution?

---

### Post by ac7ss on 2007-05-28
It sounds like MS is trying to rewrite the boot sector. Are you running any type of AV software that may be trying to re-set the MBR?

Will grub go to the menu list? or does it reboot before it gets there.

If it is not getting to the menu, ensure that the menu is turned on.

If the trouble is not with grub, but when grub is trying to start the system, one path to the solution is to change the /boot/grub/menu.lst so that 

NOSPLASH 

is in the command list for the current kernel.  while it is booting, you will be able to see where the re-boot is occuring. use the pause key to get it to slow down.

let us know where the system is re-booting.

---

### Post by Shambler2 on 2007-05-31
Hmm, I can't really think of a reason that the software I have would do that, I use McAfee at work, because of the system in place.
Yeah, there's no splash on there anyway from what I understand, it basically gets to the part where it says Grub loading stage1.5, then reboots without any error message. It won't load the menu list at all.
Thanks for your help,
Sam

---

