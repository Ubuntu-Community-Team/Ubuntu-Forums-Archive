---
title: "kpti (that switch) from above is still reading &quot;no&quot; after such a recent kernel verson"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by theazzzz on 2018-04-26
[COLOR=#252424][FONT=&quot]why kpti (that switch) from above is still reading "no" after such a recent kernel version[/FONT][/COLOR]

---

### Post by cruzer001 on 2018-04-26
```
uname -r
4.15.0-20-generic
```
```
dmesg -wH | grep 'Kernel/User page tables isolation'
[  +0.000000] Kernel/User page tables isolation: enabled
```

---

### Post by theazzzz on 2018-04-27
how to enable kpti?

I just put 4.4.0.116 generic, and the kernel included page table isolation. 
[COLOR=#252424][FONT=&quot]4.4.0-116-generic[/FONT][/COLOR]
[COLOR=#252424][FONT=&quot][    0.000000] Kernel/User page tables isolation: disabled[/FONT][/COLOR]

---

### Post by Frogs Hair on 2018-04-27
Threads *Merged*

---

### Post by deadflowr on 2018-04-27
What's the cpu?

---

