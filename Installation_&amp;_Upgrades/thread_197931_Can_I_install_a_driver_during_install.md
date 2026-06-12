---
title: "Can I install a driver during install?"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by d.j.schroeder on 2006-06-16
I am trying to get an ethernet adapter to work right.  I think I have tracked the problem down to not having the correct driver for the hardware.  I can get the driver from the manufacturer's site but don't know how to install it.  I am new to Linux, so if this seems ridiculous that's why.

I attempted to follow the manufacturer's 8 or 10 pages of instructions to the letter which included patching and recompiling the kernel and managed to completely break the whole install.  Can't boot blah blah so I guess I'll start over.  I am wondering if there is a way when I re-install to put the right driver in to begin with rather than trying some sort of patch or fix afterward?

If that isn't possible is there any other way to install a driver without rebuilding everything, it seems like there would have to be but I can't seems to figure it out.

Thanks in advance for your help.

---

### Post by rbalfour on 2006-06-16
What NIC are you trying to install with U6?

---

### Post by d.j.schroeder on 2006-06-16
It is the integrated network adapter on an ASUS A8N-SLI board, the adapter itself is a Marvell Yukon adapter.  Just to be clear it does sort of work.  It runs at 100 Mbits/sec almost exactly even though it and all connected hardware is 1 Gbit/sec capable.  I cannot get it to respond to ethtool or other commands.

---

### Post by d.j.schroeder on 2006-06-19
Bump...

---

### Post by az on 2006-06-19
Well, install linux-headers-386 and build-essential and use that to compile the new drivers.  Youdo not need to recompile the kernel - just use the headers for your running kernel to compile an add-on module.

You should be able to tthen unpack the source for your new driver, cd into the directory and then 
sudo make
and/or 
sudo make install

It should be specified in the README.


Also, file a bug report if you do get the deive working at the full speed.  Please.

---

### Post by d.j.schroeder on 2006-06-20
First, thank you very much for your reply, I appreciate your time to help me with what is probably a simple problem for many of you.

I installed the packages you suggested and then follwed the installation instructions.  I got the following output (the "Please read this carfully!" is from the manufacturer not me):

Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel
module. This script will do this automatically per default.

Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y












Create tmp dir (/tmp/Sk98IQGNdgqgZPPUkFRAbJALa)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.15-25-386)                                 [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SP)                                               [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (i386)                                              [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (none)                                           [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (4.0.3) (Kernel:4.0.3 == gcc:4.0.3)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)   

____________________________________

So it seems that it cannot find the kernel header files, which are installed, I checked.  I created the symbollic link to both of the header folders which were installed as the output suggested and got the same error message again.  I'm sure this is something simple, where are those things supposed to be?

Thank you in advance for your time on this.

---

