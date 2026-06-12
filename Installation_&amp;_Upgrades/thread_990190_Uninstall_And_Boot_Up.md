---
title: "Uninstall And Boot Up"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by amnite on 2008-11-22
I uninstalled Ubuntu because I couldnt get it to start without going to shell. But because of an error on my behalf(I installed ubuntu 2x) There was two ubuntu selections on the boot start up screen. Well i unistalled ubuntu and one is still there. How do i remove this? BTW Vista dual boot. Thx

---

### Post by Partyboi2 on 2008-11-22
Boot a ubuntu live cd and use gparted (System>Admin>Partition Editor) and delete your ubuntu partitions. Then  boot a vista disk and:
> 1. Put the Windows Vista installation disc in the disc drive, and then start the computer (set to boot from CD in BIOS).

2. Press a key when you are prompted.

3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.

4. Click Repair your computer.

5. Click the operating system that you want to repair (Vista in this case), and then click Next.

6. In the System Recovery Options dialog box, click Command Prompt.

7. Once in the command prompt, type exactly **Bootrec.exe /FixMbr** and then press ENTER. You will see "operation completed successfully."
If you don't have a vista disk you can probably use[[COLOR=Blue] super grub[/COLOR]]("http://supergrub.forjamari.linex.org/") to fix the mbr

---

