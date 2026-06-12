---
title: "smp support lost after edgy upgrade"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by brujoand on 2006-11-03
hey, i just upgraded for dapper to edgy. I had the 686-smp kernel wivh supported my intel core duo..  no there is no support smp and. I tryed reinstalling the 686 kernel but grub wont let me boot it.. What do i do to get smp support in edgy? pleas help;)
tnx

---

### Post by bulldog on 2006-11-03
Please give us the output of```
uname -a
```

---

### Post by RFScheer on 2006-11-03
Same here...

uname -a gives:

Linux Ferdoom 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

CPU is Athlon 64 X2 dual core 3800

I tried selecting 2.6.17-10-generic in grub list but that hung at blinking cursor.

---

### Post by digimars on 2006-11-03
I've got the same problem, I'm trying to install a k7 kernel, but it doesn't show up in grub.  I've updated grub and double checked synaptic and it says that I have a k7 kernel installed.  But when I reboot, the only thing that shows up is the default i386 kernel.

Is this something they plan on fixing?

---

### Post by RFScheer on 2006-11-04
I decided to download the AMD 64 iso and do a clean install.  EVERYTHING works great... zero problems!

---

### Post by brujoand on 2006-11-05
"
anders@tindheim:~$ uname -a
Linux tindheim 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux
"

$ cat /proc/cpuinfo
gives only one cpu ( 0 )..  And the system monitor shows only one cpu
frustrating stuff... and also, edgy was said to boot faster than dapper, this si not at all the case on my laptop.
any help is greatly apreciated.
anders

---

### Post by brujoand on 2006-11-05
clean install solved everything.. upgrade sucks;(

---

### Post by aev on 2006-11-09
All the same problems with the upgrade. :( 

I don't have time and the nerves to make a clean install but may be I should.:-k

---

### Post by seyon on 2006-11-11
had you try with -generic kernel ? i don't think that 386 has support to smp on edgy :P

---

