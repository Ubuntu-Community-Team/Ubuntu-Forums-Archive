---
title: "Wine &amp; windows"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by prostock on 2009-11-23
Hello all,

I need help!

I install WINE for Windows to try it out and it was great! I uninstalled it a month ago due to windows issue; my questions are:

1. The partition is still there as it ask me what OS I want to run, it this partition still good?

2. Can I just download WINE for Windows again? 

3. Will it try to partition my drive again or will it use the old partition on my drive?


Thanks,

BRC

---

### Post by MelDJ on 2009-11-23
> **prostock said:**
> 

1. The partition is still there as it ask me what OS I want to run, it this partition still good?

2. Can I just download WINE for Windows again? 

3. Will it try to partition my drive again or will it use the old partition on my drive?


Thanks,

BRC

do you mean you uninstalled ubuntu?

---

### Post by prostock on 2009-11-23
MelDJ Yes, 

I uninstalled it in the add/remove programs in Windows

Thanks for relying

---

### Post by MelDJ on 2009-11-23
i see you installed with wubi. to remove ubuntu from the boot menu see: [http://ubuntuforums.org/archive/index.php/t-1222786.html](http://ubuntuforums.org/archive/index.php/t-1222786.html).

furthermore, ubuntu was not installed in a partition but it was installed as a program in windows. 

if you would like wine again, you could just reinstall ubuntu and install wine.

Hope that helps you out ;)

---

### Post by prostock on 2009-11-23
MelDJ,


Thanks, I thought Ubuntu created a partition when it was installed? Isn't that why it asks me if I want to run Windows or Ubuntu?

I if I download and install wubi it should be fine; thanks for the help!

---

### Post by MelDJ on 2009-11-23
when you install ubuntu, you can either:
a) install it on its own partition
b) install through WUBI 

see this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by JBAlaska on 2009-11-23
You need to fix the windoze MBR, like so:
1. Put the Windows Vista or Windows 7 installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr and then press ENTER.
8. Reboot without the CD

---

