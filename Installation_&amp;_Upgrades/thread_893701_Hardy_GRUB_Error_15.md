---
title: "Hardy GRUB Error 15"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by src2206 on 2008-08-18
Hello

I have tried to install Hardy Heron on a separate partition inside the windows using the wbui installer provided with the CD (obtained through ShipIt- thank you). As I try to boot into Ubuntu I get an error message **[COLOR=Red]GRUB Load Error No 15, File not found[/COLOR]**.

My system specs are as follows:

There are three HDDs. **Two SATAII**, one of **160GB** ([COLOR=Blue]four partitions[/COLOR] including Windows- C: drive- [COLOR=Green]all NTFS[/COLOR]) and the other 500GB ([COLOR=Blue]Four partitions[/COLOR]- [COLOR=Green]all NTFS[/COLOR]) and the **third one is IDE 80 GB**. I installed (or tried to install that is) **Hardy on the 80GB IDE HDD** which have [COLOR=Blue]two partitions[/COLOR], both [COLOR=Green]NTFS[/COLOR]. [COLOR=Black]I used the first partition in the 80GB HDD for Ubuntu 8.04 installation.

Please help me out. :(

Thank you.
[/COLOR]

---

### Post by gjoellee on 2008-08-18
Maybe this can help you:
[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

---

### Post by src2206 on 2008-08-18
Thank you, but I am trying to install it in the Windows, and I am not really sure how I can incorporate any of these solutions in my case.

I more important thing: No matter what I try, that is whether I install it separately (formatting the partition to ext3) or install it in Windows in a separate partition (without formatting, keeping NTFS intact)- **Ubuntu installer simply corrupts the MBR and I get an error if I try to boot XP- [COLOR=Red]NTLDR not found[/COLOR].**[COLOR=Black] The only solution to this problem is to run FIXMBR command from within Windows Recovery Console.[/COLOR]

---

### Post by src2206 on 2008-08-20
Please help.....

---

