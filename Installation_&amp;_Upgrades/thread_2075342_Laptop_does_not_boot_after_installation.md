---
title: "Laptop does not boot after installation"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by anirudh215 on 2012-10-23
I tried installing Ubuntu 12.10 over an Archlinux system on a Lenovo Ideapad Z560. I let it use my entire harddrive, essentially removing Archlinux. I picked the automatic install mode. At the end of the Installation process, it rebooted and now it won't get past the Lenovo splash screen. I've tried getting to the BIOS menu and the BOOT menu but nothing responds. I am unable to type anything as the computer doesn't recognise anything. What do i do?

---

### Post by oldfred on 2012-10-23
Does not liveCD boot anymore.

Sometimes systems seem to get lost and BIOS info on drive is confused. Often a full power down or cold boot works. With a laptop you may have to remove battery for a few minutes.

If hard drive does not boot then boot into liveCD and run this:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by anirudh215 on 2012-10-24
No no. Perhaps I wasn't clear. I get the Lenovo splash screen after which I cannot do anything. It doesn't go past that screen to any point where I can interact with it.

---

### Post by oldfred on 2012-10-24
Did you try the full power down or cold boot?

---

### Post by anirudh215 on 2012-10-24
Since I have a laptop, I removed the battery and re-inserted to no avail. The only way I can see of interacting with this system is to do so via the hardware. What do you think I ought to do next?

---

### Post by oldfred on 2012-10-24
Are you able to get into BIOS?

Does manual have any further info on resetting system?

---

### Post by anirudh215 on 2012-10-26
No, I can't find anything.

---

### Post by oldfred on 2012-10-26
You should be able to specify in BIOS to boot CD, unless CD was damaged between install and now. Or did you use USB and install the boot loader to the USB and not leave USB plugged in?

BIOS has to see a bootable device to continue.

---

