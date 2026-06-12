---
title: "[ubuntu] Why does a Live USB with wrong time change it on the system?"
date: 2022-02-14
forum: Installation &amp; Upgrades
---

### Post by breakdaze on 2022-02-14
I did a raw write of the 21.10 iso to a USB flash drive, and when I booted Ubuntu, the time was off because of the time zone, I guess. But then I booted to Windows 7, and the time is now off on Windows 7. So interesting. Somehow the system time got updated. The BIOS actually got updated from Linux? Hmm. It's 8:30p.m. or so, but the time on the Linux was 4:30a.m., and now the same for Windows 7. I think I've seen this once before long ago... Of course a quick update using an ntp server fixed it.

---

### Post by MAFoElffen on 2022-02-15
I have not seen that before between when going between my dual-boot between 20.04.3 and Windows 10. Though every once in a while (maybe months between) I do have to reset the time in Windows 10 just by unchecking the "Set by Network" and rechecking  that same box. Then all returns to normal.

I honestly have not used Windows 7 in years, except on VM's.

---

### Post by breakdaze on 2022-02-15
Maybe something ACPI... Ah well, no matter.

---

### Post by spjackson on 2022-02-15
As I understand it, and in my experience, this is normal behaviour. Linux reads from and writes to the system clock as UTC. Windows does this using Localtime (all versions including WIndows 10 - I don't know about Windows 11 but expect it to be the same). There is a Windows registry setting to force it to use UTC for this. See for example [https://superuser.com/questions/1336303/how-can-i-stop-linux-from-changing-windowss-clock/1336321#1336321](https://superuser.com/questions/1336303/how-can-i-stop-linux-from-changing-windowss-clock/1336321#1336321) . I think it's the same with both legacy BIOS and UEFI systems.

---

### Post by breakdaze on 2022-02-15
Ah ha! Thanks.

---

### Post by C.S.Cameron on 2022-02-16
It is super easy to make Windows use UTC time or switch back and forth to Local Time.
See: [https://www.howtogeek.com/wp-content/uploads/2017/08/Make-Windows-Use-UTC-Time.zip](https://www.howtogeek.com/wp-content/uploads/2017/08/Make-Windows-Use-UTC-Time.zip)
For background see: [https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/](https://www.howtogeek.com/323390/how-to-fix-windows-and-linux-showing-different-times-when-dual-booting/)

---

### Post by breakdaze on 2022-02-16
Just fired up Lubuntu Live session on an old 2011 Acer PC, and it did not switch to UTC, it used my PC firmware system time. So, I dunno, maybe not always the case.

---

