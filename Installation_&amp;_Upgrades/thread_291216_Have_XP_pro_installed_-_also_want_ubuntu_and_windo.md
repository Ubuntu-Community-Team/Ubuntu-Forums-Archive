---
title: "Have XP pro installed - also want ubuntu and windows 2003 server on same computer?"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by bongobongo on 2006-11-02
Hi.

Now I have XP pro installed.

I also want ubuntu SERVER version and windows 2003 server installed on the same computer, but on different disks though.

Would appreciate if someone could advice me on how to proceed to do this without loosing any XP installation/software.

Should I install Ubuntu SERVER before installing Windows server 2003?

Regards

---

### Post by taurus on 2006-11-02
You install Windows stuff first and then install Ubuntu last.  Install GRUB on MBR so it will handle booting all three OSes for you.  That's the easiest way do go about this.

---

### Post by r2debo on 2006-11-02
How do you do that?

---

### Post by taurus on 2006-11-02
> **r2debo said:**
> How do you do that?
How do you do what?  Are you talking about installing Ubuntu or GRUB?

---

### Post by r2debo on 2006-11-02
> **taurus said:**
> How do you do what?  Are you talking about installing Ubuntu or GRUB?

Talking about GRUB on MBR.  A link would be great.  Thanks.

---

### Post by taurus on 2006-11-02
If you follow the directions on the screen during the installing process, it will ask you if you want to install MBR and where would you want to install it.  Tell it to install on MBR which is usually your /dev/hda...

That's it.

---

