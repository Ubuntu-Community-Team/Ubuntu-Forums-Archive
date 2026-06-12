---
title: "Did not boot to Ubuntu"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by th3gh05t on 2007-10-25
Hi,

I have Windows XP installed on my main boot boot partition, which is the G: drive.

I installed Ubuntu on the E: Drive and used the F: drive as a swap.

When I booted up my machine, it still went into Windows. How do I modify the GRUB?

I want to be able to boot into Windows or Ubuntu.

Thanks, th3gh05t

---

### Post by orange2k on 2007-10-25
Ubuntu should be able to detect other OS-es and add them automatically to the grub menu.
BTW Ubuntu doesn`t handle drives names like windows: so no E:, C:, G: etc...

The question is what appeared on the screen when you were prompted to partition the drives...

---

### Post by Officer Dibble on 2007-10-25
I have this same problem, and I have used Super Grub to no avail... it still wants to boot straight to XP...

---

### Post by th3gh05t on 2007-10-25
> **orange2k said:**
> The question is what appeared on the screen when you were prompted to partition the drives...

I recently had to fix my NTLDR. I used this guide: [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Nothing came up, it just boot straight into Windows. There has to be something that I can do so I can get a dual boot working.

---

### Post by jsonder on 2007-10-25
I think you are going to need to change the boot drive designation to from the Windows drive to the Ubuntu drive.  It sounds like grub was written to the mbr sector of the Ubuntu drive.

What you've been trying to do is what is done for a dual-boot on one hard drive with multiple partitions.

Good luck.

---

### Post by th3gh05t on 2007-10-25
Right. So how do I fix this?

I really don't even care about my Windows installation. I just want Ubuntu.

---

### Post by mrfelker on 2007-10-25
If you don't care about Windoze just install Ubuntu GRUB to the MBR and either/or kill the Windows partition using Gparted or other tool.  If you just don't want to see the M$ OS - just comment it out of menu.lst.

---

### Post by th3gh05t on 2007-10-25
> **mrfelker said:**
> If you don't care about Windoze just install Ubuntu GRUB to the MBR and either/or kill the Windows partition using Gparted or other tool.  If you just don't want to see the M$ OS - just comment it out of menu.lst.

Thanks for the tips, but this is why I am here asking for help. I don't know how to edit anything regarding the MBR or GRUB. 

How do I install Ubuntu GRUB to MBR?

How do I comment Windows out of menu.lst?

---

### Post by th3gh05t on 2007-10-25
Can someone help me out with my problem? Or point me a thread that can help?

I am really anxious to start using Ubuntu again..

---

