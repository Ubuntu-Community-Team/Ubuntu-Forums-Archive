---
title: "downloaded ubuntu-10.04.3-desktop-amd64.iso, but after installation it shows it is 32"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by musa-ktk on 2012-01-01
I downloaded ubuntu-10.04.3-desktop-amd64.iso, created a startup disk (USB) and installed it(ofc on a 64 bit architecture).

In terminal **getconf LONG_BIT** gives me **[SIZE=1]32[/SIZE]**

and **cat /proc/version** prints out following result

**Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010**

i think its pretty obvious that i have installed 32 bti ubuntu... so whats going on? is there something like enabling 64 bit feature after installing it?( i am sure there ain't).

Please don't tell me to double check if i have mistakenly downloaded and installed 32 bit version. I am damn sure i downloaded and installed the right version i-e  **ubuntu-10.04.3-desktop-amd64.iso.**

---

### Post by darkod on 2012-01-01
The cat /proc/version doesn't show 32/64 info. The 32 you have in your result is only coincidence. I just checked on my 64-bit version and there is no 64 included in the result anywhere.

But the getconf LONG_BIT should give 64 as result.

Do you maybe have some option in BIOS to disable 64-bit that is left enabled? I can't really think of anything else. I think I remember seeing on some machines that option in BIOS.

---

### Post by oldos2er on 2012-01-01
Or, instead of **cat /proc/version** use **uname -m** or **uname -a**

---

### Post by musa-ktk on 2012-01-01
@darkod , There is no such option in BIOS and BIOS is not causing any problem because i have installed 64 bit Windows 7 and windows 2008 server side by side with Ubuntu.

Thanks for reply.

@oldos2er , uname -m says** i868**  ( guess that means 32 bit again)

i better re-download another image, its just strange.

---

### Post by oldos2er on 2012-01-02
Do you mean i686? Yes, that's 32-bit.

If you download an *.iso again, check it with md5sum (if you haven't been doing that) [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by musa-ktk on 2012-01-05
Thanks, i just downloaded another iso.

---

