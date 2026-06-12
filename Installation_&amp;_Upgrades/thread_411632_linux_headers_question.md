---
title: "linux headers question"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by lukemack on 2007-04-17
Hi,

Can someone offer an explanation of what linux headers are in relation to the kernel and Ubuntu? After installing updates from the update manager a while back and possibly as a result of commands run while following tutorials to get x or y working, i have options in the GRUB loader for 2.6.17-11 -generic, -server and -386.

Why is this? What does it mean? Does it matter? I am running 6.10 server with the gnome desktop installed. I am aware of the arguments for / against installing a desktop on a server. It is a testing / learning machine.

Many thanks,

Luke.

---

### Post by rmemm on 2007-04-17
It sounds to me like you've installed multiple kernels.  It's possible to have multiple kernels -- ones tweaked for different applications installed at the same time.  Since the kernel is really the core of the operating system -- you can use only one of these at a time.  At boot time you choose which kernel to start.  It's even possible to build your own custom kernel.

Kernels typically are different in what modules that were built into them (what features are supported) in terms of hardware, file systems, etc -- and perhaps things like target system too for example -- meaning is it a 32 bit or 64 bit machines.

As far as I know -- only the one that you choose at boot time matters.

Another way to look at this is how the Linux system is built.  When you start linux a sequence of events happen to layer software into the running systems --  your bios/firmware is loaded , that starts grub, grub then loads the kernel, the kernel loads and init's and starts process zero which loads basic software listed in the /etc/inittab file, one of which runs the system startup procedure which does various inits including starting system servicies, between inittab and the system startup procedure you load a variety of serivices two of these servicies is gdm or kdm and another is an Xserver which in the end is what you see when you login -- and is the base software that will load user desktop system software when the time comes.  I say all this to give you an idea of where the kernel fit's into the scheme of things.  The kernel is the the lowest level of the OS -- and it's really the only thing that's Linux -- this is why the Free Software Foundation likes to call the system GNU as they really developed the whole concept of an open source GNU os and did a lot of the work and since in fact the GNU system can run a variety of kernels -- Linux, Hurd, various versions of BSD etc.  Linux in terms of volume of code is actually a small but very critical part of the whole GNU system -- and it's also come a good trademark to refer to the whole combination.

Rob

---

### Post by thelinuxguy on 2007-04-17
To add to rmemm's explanation above, Kernel headers are the header files used to compile the kernel - and other applications which depend on the symbols / structures defined in these header files, like kernel modules. An example can be graphic card drivers; if the driver does not have a binary matching the running kernel and needs to be compiled.

---

### Post by lukemack on 2007-04-17
thanks loads for the detailed replies! i will leave things alone until feisty is out and stable i think.

<L>

---

### Post by lukemack on 2007-04-24
A further question:

Can I safely remove the kernels I am not using? If so, how do I....

- tell from the terminal which one I'm using
- remove the others

I am using Ubuntu 6.10 Server with gnome Desktop installed.

many thanks,

<L>

---

### Post by mac.ryan on 2007-04-24
> **lukemack said:**
> Can I safely remove the kernels I am not using? If so, how do I....

My experience is positive with that, although in some other thread I remember somebody was advocating not to, in order to have a "backup" solution ready all the times...

> tell from the terminal which one I'm using

```
uname -r
```

> remove the others

From Synaptics, you can search for the packages which name begins with "linux-". Some of them are the kernel images (linux-generic, linux-amd-...).

---

