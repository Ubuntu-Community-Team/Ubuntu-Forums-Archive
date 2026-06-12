---
title: "New Istallation"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by RobertEr on 2011-09-05
I have an HP laptop with WIndows XP and I want to make it duel boot with Ubuntu 11.04. I have read about wubi but that sounds like I am only running Ubuntu only as another program  on WIndows. If I do it do I have to have the Wubi program as well as the Ubuntu 11.04 on a single or cd or can it come from an external hard drive. And I suppose I am subject to the regular windows viruses. I don't even run a wine program just because I have tried to avoid the usual Windows crap

---

### Post by sanderd17 on 2011-09-05
What is Wubi?

Wubi creates a virtual disk inside the windows disk. Windows sees this as a file, but if you boot into the wubi installation, it is seen as a file-system.

This makes it extremely easy to uninstall. You just go to "add/remove software" and you remove the wubi program. This will delete that filesystem and will change the windows bootloader to boot automatically back into Windows.

Off coarse, if you use Windows, and Windows crashes or gets a virus. Than there is a big chance that you will not be able to boot Ubuntu too.

Secondly, Windows need maintenance (installing upgrades of the antivirus, defragmenting the disk ...) and you can't do that from an Ubuntu installation. So you need to boot to windows regularly to do these maintenance tasks. Or Windows will crash, and you will lose both OS.

So in fact, you don't run it as a program, but it is installed as a program (and therefore vulnerable for Windows problems).

---

### Post by Ad1217 on 2011-09-05
to me, wubi seems like an extended live cd (I used it for a couple months, then gave up on windows enitirely).

---

### Post by sanderd17 on 2011-09-05
> **Ad1217 said:**
> to me, wubi seems like an extended live cd (I used it for a couple months, then gave up on windows enitirely).

Same here. It's just to difficult to keep Windows maintained while you're not using it. And it's too dangerous to keep it unmaintained.

Using it for up to 6 months is OK.

---

