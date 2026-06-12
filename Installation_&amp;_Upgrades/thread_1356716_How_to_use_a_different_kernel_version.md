---
title: "How to use a different kernel version?"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by mahela007 on 2009-12-16
How do I use a different linux kernel with my current version of ubuntu?

---

### Post by drs305 on 2009-12-16
The kernel is determined during the boot process. Normally you do this by editing the grub menu. How you edit it depends on whether you have Grub legacy or Grub 2. You can check the version with "grub-install -v".

For Grub 0.97, using StartupManager is an easy GUI way to tweak the grub settings. See the "SUM" link in my signature line.

For Grub 2, refer to the link for "G2-Tasks".

Of course, you must have more than one kernel installed on your system to do either of these. If you don't know if you have more than one and don't know how to find out, just ask.

---

### Post by mahela007 on 2009-12-16
I'm completely new to this business of kernels. yes.. I don't know how to install a kernel.

---

### Post by snowpine on 2009-12-16
Let's back up a minute... why do you think you need a different kernel?

---

### Post by mahela007 on 2009-12-16
I just want to learn how to do it... so that I might learn something..

---

### Post by snowpine on 2009-12-16
All of the Ubuntu kernels are here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

They are in the .deb format, so you can install them simply by double-clicking (or using dpkg -i if you prefer the terminal).

---

### Post by mahela007 on 2009-12-16
what happens after that? Do I just reboot the computer and if so, will the new kernel be just 'an empty box' without any software? (From what I've read about kernels, I understand that their primary use it to manage the resources of a computer and to provide an abstraction layer over hardware. That doesn't make it sound like kernel provide and end-use applications).

PS: My next reply will take a few hours cos it's pretty late at night over here.

---

### Post by snowpine on 2009-12-16
The Linux Kernel is the most important part of Linux, way more detailed than I could type in a quick post. :)

This will get you started towards understand what it does: [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

The short answer to your question is: you install the kernel, reboot the computer, choose the new kernel from Grub. If all goes well, your system will be exactly the same as with the old kernel, except for any benefits provided by the new kernel.

---

### Post by mahela007 on 2009-12-17
I understand how complicated a kernel is and a read about 5 (-ish) articles on kernels in general.
From the wikipedia article you posted, I once again read that the GUI is separate from the kernel. So, how would the GUI work with the new kernel version? Or to be more precise, what makes the GUI start running on the new kernel?

---

### Post by snowpine on 2009-12-17
Changing the kernel should not change your GUI at all. (The GUI is started by GDM in Ubuntu.) The kernel controls your hardware, basically.

---

### Post by mahela007 on 2009-12-17
I'm afraid I don't understand. The kernel is the most basic layer of the operating system. Once that is replaced, how will there be any GUI to run on it? It's not like I'm installing a new distro with all the software that comes with it.

---

### Post by snowpine on 2009-12-17
You said your reason is to learn something, so try it and see for yourself. :)

---

### Post by Aeric on 2009-12-17
The GUI you mean is Desktop Environment.
DE such as Gnome, KDE, xfce are basically a piece of application. Linux can run without GUI or DE.
It is like you can run Windows in MS DOS mode and Windows Desktop GUI is actually call explorer.exe.
just my 2 cents. ;)

---

### Post by mahela007 on 2009-12-17
> **snowpine said:**
> You said your reason is to learn something, so try it and see for yourself. :)

haha.. you got me there.. :-). 
I meant learn something on the forums... You see,  I'm using ubuntu on a laptop so I don't want to mess around too much. So, I won't be installing the kernel just yet.. not until I NEED to do it or am proficient enough with linux.

Anyway.. Aeric, does that mean that I won't have a DE when I run my new kernel?

---

### Post by snowpine on 2009-12-17
The kernel and the GUI/DE are completely independent. 

In fact, Ubuntu users regularly get new kernels (with small bug fixes) through the Update Manager. 

Canonical does a great job developing the kernel for Ubuntu. I have never needed anything other than the default Ubuntu kernel, personally.

---

### Post by mahela007 on 2009-12-17
Yes.. that's my point (that they are independent). To me, a distribution is something which gives me a kernel and a DE (among other stuff) and the installation process tells the DE to work with the kernel. NOw what happens when I install a new kernel? What is there to tell the GUI of the previous kernel that is now has to work with the new kernel? For that matter, since the kernel is just a hardware interface, how will I even open up a command line?

---

### Post by snowpine on 2009-12-17
> **mahela007 said:**
> Yes.. that's my point (that they are independent). To me, a distribution is something which gives me a kernel and a DE (among other stuff) and the installation process tells the DE to work with the kernel. NOw what happens when I install a new kernel? What is there to tell the GUI of the previous kernel that is now has to work with the new kernel? For that matter, since the kernel is just a hardware interface, how will I even open up a command line?

You're thinking about it too hard. :)

Everything in Linux is modular; you can swap out one part for another without affecting the other parts.

---

### Post by oldos2er on 2009-12-17
During the process of installing the new kernel, it will be modified and updated to include any active hardware drivers in your older kernels. You can see this if you run the kernel install command (e.g. sudo apt-get install linux-image-2.6.31-15-generic, for example) in a terminal. There is a program called dkms whose sole purpose is to keep kernels updated. Run **man dkms** for more info.

---

### Post by Aeric on 2009-12-17
> **mahela007 said:**
> haha.. you got me there.. :-). 
I meant learn something on the forums... You see,  I'm using ubuntu on a laptop so I don't want to mess around too much. So, I won't be installing the kernel just yet.. not until I NEED to do it or am proficient enough with linux.

Anyway.. Aeric, does that mean that I won't have a DE when I run my new kernel?
Forget about what I said. As I read from somewhere, you can treat any program in Linux is actually a file (but it may be hidden). You can think Kernel is a file (maybe consists of more than 1 dependent file). Desktop Environment also the same. When the OS loaded, it will be read into the RAM. When Linux is starting Grub will read the settings so it will choose which is the default kernel to load following by loading the GUI and which DE session; whether it is Gnome, KDE or terminal.

---

### Post by Bukran on 2010-01-26
> **snowpine said:**
> All of the Ubuntu kernels are here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

They are in the .deb format, so you can install them simply by double-clicking (or using dpkg -i if you prefer the terminal).

I have a question that gets me stuck for several days. For development reasons (end-of-studies project) I need to boot a custom built Linux kernel 2.6.16.

I've tried with current version of Ubuntu (9.10), downloading the kernel from [http://www.kernel.org/pub/](http://www.kernel.org/pub/) and making pertinent changes but after compiling I receive a kernel panic message and can't boot.

I've checked the URL you wrote to find that there's no 2.6.16 version, does that mean that Ubuntu "jumped" this version and can't be used or maybe Karmic is too new for it?

Thanks beforehand.

---

### Post by snowpine on 2010-01-26
> **Bukran said:**
> I have a question that gets me stuck for several days. For development reasons (end-of-studies project) I need to boot a custom built Linux kernel 2.6.16.

I've tried with current version of Ubuntu (9.10), downloading the kernel from [http://www.kernel.org/pub/](http://www.kernel.org/pub/) and making pertinent changes but after compiling I receive a kernel panic message and can't boot.

I've checked the URL you wrote to find that there's no 2.6.16 version, does that mean that Ubuntu "jumped" this version and can't be used or maybe Karmic is too new for it?

Thanks beforehand.

I don't know for sure... maybe try your experiment with Ubuntu 6.06 (which used 2.6.15 and is still supported for servers)?

---

