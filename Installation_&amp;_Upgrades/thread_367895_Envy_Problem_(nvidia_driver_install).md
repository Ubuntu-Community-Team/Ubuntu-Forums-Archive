---
title: "Envy Problem (nvidia driver install)"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by MgNate on 2007-02-22
I keep getting errors when i try to install the invidia driver with envy. I've been trying to do this for the last two days! Is there a way to change the compiler so i can install it and then change it back?

Here's the error:

> The compiler used to compile the kernel (gcc 4.0) does not exactly match the
current compiler (gcc 4.1). The Linux 2.6 kernel module loader rejects kern
el modules built with a version of gcc that does not exactly match that of t
he compiler used to build the running kernel.

If you know what you are doing and want to ignore the gcc version check, sel
ect "No" to continue installation. Otherwise, select "Yes" to abort install
ation, set the CC environment variable to the name of the compiler used to c
ompile your kernel, and restart installation. Abort now? (Answer: Yes)
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux

---

### Post by MgNate on 2007-02-22
I tried to install it with the invidia-glx from the repository and i got this error:
> X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.


I could really use some help please!

---

### Post by dannyboy79 on 2007-02-22
we need info, what kernel are you using. uname -r
what card are you using? have you read this for troubleshooting? what repo were you trying to install nvidia-glx from?
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)
there's a part that talks  about switching the compiler to do the install, it uses an example of the gcc3.3 but that you would just change to 4.0 cause that's what the installer wants. try that before doing th install again.

CC=gcc-4.0 
export CC

or during the error you cvould just pick no, to the gcc check, did you try that? not sure if that would be ok or not though!

---

