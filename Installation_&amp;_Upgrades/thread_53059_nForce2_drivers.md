---
title: "nForce2 drivers"
date: 2005-07-30
forum: Installation &amp; Upgrades
---

### Post by Olrich on 2005-07-30
I am having some issues installing the official linux audio drivers for the nForce2 chipset.  I already have working sound, but I have issues with latency, and all of my speakers not producing sound, so I would like to give these drivers a go.  

I downloaded the kernel source and extracted it into /usr/src.  I tried running the driver install program specifying the source location and it seems to handle them fine.  But, in the next step I get the error


ERROR:
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the appropriate nvidia-installer command line option.

There is a command line option --kernel-output-path to specify this location, but I have not idea what to set it as.  I have tried numerous things for this location and I either get the above error, or the installer fails to install the driver.  Does anyone know where the Kernel output path is?  Do I have to recompile the kernel to create this directory?  Thanks for your help.

---

### Post by farfargoth on 2005-07-30
you have to do "make xconfig" in the kernel sources before you compile the nforce2 drivers, and  i think you have to run exactly that version of the kernel for it to work

---

### Post by Olrich on 2005-07-30
Thanks for the reply.  Ok, so I ran make xconfig and saved the .configure file.  Do I need to now recompile the kernel before running the driver installer?  I also still don't know where the kernel-output-path is.  Thanks for your help.

---

### Post by Olrich on 2005-07-30
anyone?

---

### Post by mo_x on 2005-07-31
You should install the kernel sources for the specific kernel you are using through apt or synaptic. The command "uname -r" will give you your kernel version.

---

### Post by Olrich on 2005-07-31
Thanks a lot for the reply.  To fix the problem I had to rename /usr/src/linux-source-2.6.10 to /usr/linux/src.  Then the installer worked just fine.  My 5.1 speakers now work and drivers work fine with the exception of SDL.  Most apps that need SDL sound just crash on startup, but others, like tuxracer, produce sped sound, with lots of distortion and noise.  Anyone have any ideas why all sound would work except SDL?  Thanks.

---

### Post by Olrich on 2005-07-31
[QUOTE=Olrich]Thanks a lot for the reply.  To fix the problem I had to rename /usr/src/linux-source-2.6.10 to /usr/linux/src.  Then the installer worked just fine.  My 5.1 speakers now work and drivers work fine with the exception of SDL.  Most apps that need SDL sound just crash on startup, but others, like tuxracer, produce sped sound, with lots of distortion and noise.  Anyone have any ideas why all sound would work except SDL?  Thanks.[/QUOTE]
 bump

---

