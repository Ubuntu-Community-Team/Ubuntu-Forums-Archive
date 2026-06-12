---
title: "Kernel Panic - not syncing: machine check"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by Chris107 on 2005-07-20
I'm installing Ubuntu on my new computer but I get 
```
Kernel Panic - not syncing: machine check
```

Anyone know what's wrong with it?  I get the error and then it just locks up.

---

### Post by hod139 on 2005-07-31
I'm not sure what could be causing this, but one common answer I seem to read when people have strange installation problems is: 
download a new iso
burn at a slower speed
try again

If it happens again, you should give more details, at the least what stage of the install you are in when it panics.

---

### Post by Mudhoney on 2005-08-01
[QUOTE=Chris107]I'm installing Ubuntu on my new computer but I get 
```
Kernel Panic - not syncing: machine check
```

Anyone know what's wrong with it?  I get the error and then it just locks up.[/QUOTE]
 I had this problem with FC4, too.  I ended up switching from i386 to x86_64 (for Intel 64 bit CPU) and also try with install option acpi=off
eg. at the prompt type "linux acpi=off"

---

### Post by Chris107 on 2005-08-01
Oh....x86_64 is for Intel 64 bit processors?  That may be what my problem is  :neutral:

I have an AMD Athlon 64

---

### Post by hod139 on 2005-08-01
You will want the AMD64 install for the Athlon 64 if you want a 64 bit OS.  Note, the backports and extras are still lacking for the AMD64 version.

Or you can install the Intel x86 version, which an Athlon 64 can run, and you will have a 32 bit OS.

I would recommend the AMD64 version, as the backports and extras are slowing beginning to gain popularity, and it isn't easy to upgrade from a 32 bit version to a 64.

---

### Post by Mudhoney on 2005-08-01
[QUOTE=Chris107]Oh....x86_64 is for Intel 64 bit processors?  That may be what my problem is  :neutral:

I have an AMD Athlon 64[/QUOTE]
 You shouldn't *need* to install the 64 bit version.  I think it was actually the "acpi=off" option that fixed it for me.  The 64 bit version seems good although I've been having a few java issues since I installed it.  Btw, the x86_64 is for both AMD64 and Intel EMT64 which is basically the same thing.

---

### Post by hod139 on 2005-08-01
[QUOTE=Mudhoney]You shouldn't *need* to install the 64 bit version.  I think it was actually the "acpi=off" option that fixed it for me.  The 64 bit version seems good although I've been having a few java issues since I installed it.  Btw, the x86_64 is for both AMD64 and Intel EMT64 which is basically the same thing.[/QUOTE]

While true that an Athlon64 doesn't *need* to install the 64 bit version, why wouldn't you want to?  Also, the phrase x86-64 has been dropped in favor of AMD64 (someone correct me if I'm wrong), and the name on the install cd is AMD64.  (EM64T (not EMT64) is compatible with AMD64, but IA64 is not).  

What java issues are you having, I haven't been having any.  Have you seen the [ AMD64 backports](http://ubuntuforums.org/showthread.php?t=48905)  containing:
[list]
[*]sun-j2re1.5 - Java(TM) 2 RE, Standard Edition, Sun Microsystems(TM)
[*]sun-j2sdk1.5 - Java(TM) 2 SDK, Standard Edition, Sun Microsystems(TM)
[*]blackdown-j2sdk1.4 - Java(TM) 2 SDK, Standard Edition, Blackdown
[*]blackdown-j2re1.4 - Java(TM) 2 RE, Standard Edition, Blackdown
[/list]

---

