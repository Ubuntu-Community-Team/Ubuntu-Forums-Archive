---
title: "error: the symbol 'grub_puts_' not found"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by refo on 2010-03-27
Hello,

I am running Ubuntu both native and on virtualbox on windows XP host.
The problem apeared when upgraded from Ubuntu 9.10 to 10.04. System boots perfectly WinXP and Ubuntu. But the problem appears when I try to boot linux on virtual box. Following is the grub error:

GRUB loading.
error: the symbol 'grub_puts_' not found
grub rescue> _

I've  tried to boot from alternate CD and "update-grub2" but the problem still appears.

On my office Notebook (which is absolutely the same HP nc6320) I've  installed ubuntu 10.04 from scratch and it is working.

Could anyone suggest me what this message means?

Thanks in advance

Refo

---

### Post by stlsaint on 2010-03-27
Though i have not done it myself it sounds as if you need reinstall grub in wubi. This may help some.
[Grub2]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by refo on 2010-03-27
> **stlsaint said:**
> Though i have not done it myself it sounds as if you need reinstall grub in wubi. This may help some.
[Grub2]("http://ubuntuforums.org/showthread.php?t=1195275")

10x for replay but I am using virtualbox on WinXP host and Ubuntu on virtial mchine
I don't thing there is something related to wubi.

---

### Post by stlsaint on 2010-03-27
OK but have you tried reinstalling grub on the vbox machine ubuntu guest.

---

### Post by refo on 2010-03-27
I've tried update-grub2

---

### Post by stlsaint on 2010-03-27
updating and reinstalling are two different procedures. Please see the grub2 link on my signature for full step-by-step to re-install grub.

---

### Post by refo on 2010-03-27
Yes, thanks a lot.
I've just reinstalled it using alternate CD and it boots fine.

---

### Post by stlsaint on 2010-03-27
Glad to help.

---

