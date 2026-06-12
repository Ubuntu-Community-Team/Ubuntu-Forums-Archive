---
title: "kernel configuration?"
date: 2004-11-04
forum: Installation &amp; Upgrades
---

### Post by Slovak on 2004-11-04
Where is my current kernel configuration saved to? I want to make some changes with make menuconfig so I need to load my current one. I am going to try something to see if I can get ATI support

---

### Post by ubuntu-geek on 2004-11-04
This might help direct you in the right direction.
 
 [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)

---

### Post by diebels on 2004-11-04
Or short answer```
/boot/config-`uname -r`
```Not sure how you will get better ATI support by configuring the current kernel though.

---

### Post by Slovak on 2004-11-05
How? By compiling ati agp INTO the kernel instead of as a module. It has worked for others on the debian forums getting the same mysterious entries in various log files. Especially the one I have about ATI tainting the kernel.

---

### Post by Slovak on 2004-11-05
[QUOTE=ubuntu-geek]This might help direct you in the right direction.
 
 [http://www.ubuntulinux.org/wiki/KernelCompileHowto](http://www.ubuntulinux.org/wiki/KernelCompileHowto)[/QUOTE]

I know how to configure my kernel, I want to look at my current configiration and just make adjustments as necessary. You knw when one compiles a kernel they can load that later with 'make menuconfig' and make adjustments to their existing kernel instead of starting from scratch. the kernel file gets saved as a .conf file. Where is mine from my original install located?

---

### Post by Slovak on 2004-11-05
[QUOTE=diebels]Or short answer```
/boot/config-`uname -r`
```[/QUOTE]

That does not work for me, even from a root terminal, says 
root@john:/ # /boot/config-`uname -r`
bash: /boot/config-2.6.8.1-3-386: Permission denied

---

### Post by Slovak on 2004-11-05
type ATI taints the kernel into google and find the hit for linuxquestions and read that post and you will see what I mean by compiling it into the kernel instead of having agp load as a module at boot

---

### Post by piquadrat on 2004-11-05
[QUOTE=Slovak]That does not work for me, even from a root terminal, says 
root@john:/ # /boot/config-`uname -r`
bash: /boot/config-2.6.8.1-3-386: Permission denied[/QUOTE]

That's because you're trying to execute a text file, which doesn't work. Just type

cp /boot/config-`uname -r` /usr/src/linux/.config

and you're done. Maybe you have to adjust the path to your kernel source (the "/usr/src/linux/" part)

---

### Post by gc1 on 2005-03-05
[QUOTE=Slovak]I know how to configure my kernel, I want to look at my current configiration and just make adjustments as necessary. You knw when one compiles a kernel they can load that later with 'make menuconfig' and make adjustments to their existing kernel instead of starting from scratch. the kernel file gets saved as a .conf file. Where is mine from my original install located?[/QUOTE]
 I don't know how to configure MY kernel which is NOT in /usr/src/linux. Would like to know where it is, cd to the directory and then use make xconfig.

---

