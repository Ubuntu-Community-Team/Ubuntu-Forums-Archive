---
title: "Java + Sound = FAIL"
date: 2010-03-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-03-03
There is no sound with java, ie, limewire, frostwire etc. or maybe it is flashplayer, who knows.

```
:~/Desktop$ limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_18]
Configuring environment...
Loading LimeWire:
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-installer/npwrapper.libflashplayer.so 
[/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
```

---

### Post by Ibidem on 2010-03-03
That last bit (wrong ELF class: ELFCLASS64) looks to me like you have a 32-bit Java (Sun Java, not the default openjdk/jre) installed on x86_64, along with a 64-bit Flash.
What happens with openjdk6?  Does Limewire fail to run?

---

### Post by tad1073 on 2010-03-03
> **Ibidem said:**
> That last bit (wrong ELF class: ELFCLASS64) looks to me like you have a 32-bit Java (Sun Java, not the default openjdk/jre) installed on x86_64, along with a 64-bit Flash.
What happens with openjdk6?  Does Limewire fail to run?

It doesn't fail to run, there is just no sound, everything else works fine.

The same behavior happens on a 32-bit machine also but I haven't started limewire through the terminal on that machine.

---

### Post by Ibidem on 2010-03-03
The problem looks to be something about the Flash plugin not working.  I assume that Flash is where you get sound.  But I don't know why Flash isn't working with Java.
I was asking if openjdk6 would run Limewire.
I presume that sound, in and of itself, is working?

---

### Post by tad1073 on 2010-03-03
> **Ibidem said:**
> The problem looks to be something about the Flash plugin not working.  I assume that Flash is where you get sound.  But I don't know why Flash isn't working with Java.
I was asking if openjdk6 would run Limewire.
I presume that sound, in and of itself, is working?

yes, sound is working, just not with limewire

---

