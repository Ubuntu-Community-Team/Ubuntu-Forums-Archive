---
title: "Thank you Irwan!"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by ecofeco on 2014-04-23
Irwan, your solution to the grub install failure and failure to load after a Linux dual boot install on a Win PC and then unable to boot to either OS, was just the magic fix I was looking for!

Thank you so much!

For those of you who may be having the same issue, here is the fix:

You can use the Bootrec.exe tool in the Windows Recovery Environment  (Windows RE) to troubleshoot and repair the following items in Windows  Vista or Windows 7:

To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:
Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
Press a key when you are prompted.
Select a language, a time, a currency, a keyboard or an input method, and then click Next.
Click Repair your computer.
Click the operating system that you want to repair, and then click Next.
In the System Recovery Options dialog box, click Command Prompt.
Type "Bootrec /fixmbr" and then press ENTER

---

