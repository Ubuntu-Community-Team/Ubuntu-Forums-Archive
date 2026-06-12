---
title: "Compile Kernel With UINPUT"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2008-04-23
Hi,

I've had to compile a new Kernel to get sound working on my PowerPC for hardy but once I do so I get an error loading that insists that I compile the kernel with CONFIG_INPUT_UINPUT. I'm compiling the kernel from [http://www.kernel.org](http://www.kernel.org) - version 2.6.25, and this does not appear to have the option for this.

Does anyone have any ideas?

---

### Post by ryanhaigh on 2008-04-23
I just did a ```
cat /boot/config-2.6.22-14-generic | grep UINPUT 
#and got this:
CONFIG_INPUT_UINPUT=m
```. You can do the same to check whether the option exists in the config file you are using (note that your kernel version will be different as I am using Gutsy).

---

### Post by mikeym on 2008-04-23
No sorry I don't get anything for that on my compilled kernel but I knew this as I had done the same with my .config file when I was compiling. What I want to know it how to enable this on a kernel from the link above.

---

### Post by mikeym on 2008-04-29
Bumpity bump bump bump

---

