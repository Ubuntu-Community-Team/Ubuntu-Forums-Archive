---
title: "kernel 686 installed, how to understand if it's working?"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by towsonu2003 on 2005-10-26
I installed the linux kernel image for 686, but I'm not sure where to look to see if it is working properly. How can I definitely fid out whether it's working?

---

### Post by cydizen on 2005-10-26
Hi there,

 Well if you are back in your system, then it should be working! You can verify what kernel you are using by running this:

```
$uname -r
```

and you should get something like this back:

2.6.12-9-686


Hope this helps!

Regards,
Bruce

---

### Post by Xian on 2005-10-26
What CPU are you using?:

$ cat /proc/cpuinfo

---

### Post by towsonu2003 on 2005-10-26
uname -r brings the correct (686) kernel. thanks. 

as for the cpu (this is like martian language to me): 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2800.425
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5554.17

thank you so much for replying so fast :)

---

### Post by Xian on 2005-10-26
You look good to go to me. Enjoy.

---

### Post by towsonu2003 on 2005-10-26
I'm happy - thank you :)

---

