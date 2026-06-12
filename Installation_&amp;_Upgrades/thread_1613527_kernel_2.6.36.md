---
title: "kernel 2.6.36"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by kr651129 on 2010-11-04
Not really a question, just an obervastion so if this is not in the right forum mods please move.

I just wanted to let everyone know that my nm-manager (using the bcmwl STA) was slugish and my graphics (intel) card wasnt 100% and things seemed to be freezing a lot, I did a source compile of 2.6.36 on my 10.10 system and my laptop is blazing fast now, nm-manager is connected with an ip before the desktop is done loading, the graphics seem to be supersonic, and I'm having no issues with slow applications.

Just to let you know this is on an intel system, running 10.10 desktop 64 bit, thought it was worth letting everyone know that 10.04+ and 2.6.36+ is a one two punch, though there is not much difference between 2.6.36, 2.6.37-rc1, 2.6.37-rc1-git3, and the latest snapshot, defintaly worth the time I spent upgrading!!!

---

### Post by coffeecat on 2010-11-04
I know that compiling your own kernel can be very satisfying (I ran Gentoo for a couple of years), but just to let you know that the Ubuntu compiled 2.6.36 kernel is in the Ubuntu repositories in preparation for 11.04, although you won't find it in Synaptic in Lucid or Maverick. But you can download it from archive.ubuntu.com and install it manually if you want.

Because there was a regression for me with the 2.6.35 kernel causing the Fn-key brightness combinations to stop working on my particular Sony laptop, I tried the 2.6.36 kernel in Maverick and was pleased to see it solved that particular problem. I have since done a fresh install of 10.10 in order to upgrade it to 11.04 to be ready for pre-release testing. I'm posting from the pre-alpha Natty now on my Sony with the 2.6.36 kernel.

There will, of course, be numerous minor point upgrades to the kernel during the testing phase - we're on 2.6.36-1 at the moment - but you might be interested in trying this kernel to compare with your home-grown one.

---

### Post by solnyshok on 2010-11-09
Hi, where can I get Linux kernel source for version 2.6.36 with Ubuntu patches? I see 2.6.36 debs on kernel.ubuntu.com alongside with 3 .patches files. Are those patches that need to be applied to vanilla source?

---

### Post by dino99 on 2010-11-09
im pleased with 2.6.37

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by solnyshok on 2010-11-09
I need source of this 2.6.36 or 2.37 with Ubuntu patches. This is due to the fact that I have toshiba laptop, and toshiba_acpi compiled in Maverick doesn't work properly. However, there is a patch that worked on Maverick 2.6.35 and if I could get sources of Maverick 2.6.36 or 2.6.37, this patch might work too. It doesn't patch properly with vanilla 2.6.36 sources.

---

### Post by dino99 on 2010-11-09
here you go :)

[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by solnyshok on 2010-11-09
Thanks, but those are vanilla kernel sources, i.e. without any ubuntu customizations.

---

### Post by Jimbro727 on 2010-11-16
Hey, did you ever find out where to find the 2.6.36 source?  I installed the kernel here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/) , but realized that I need the source to enable something.  I'm really trying to avoid downloading the vanilla source and going from there...

Thanks,
Jim

---

### Post by solnyshok on 2010-11-18
nope, but still hope that somebody will help us

---

### Post by Alterax on 2010-11-24
Actually, I think I can help you out here.  I'm currently working on a problem with this same tree and the bcmwl kernel module.

The recommended method for getting the kernel sources with Ubuntu customizations are by using git.  And here's how it's done:

[B][I]sudo -i
cd /usr/src[/I][/B]
***git clone git://kernel.ubuntu.com/ubuntu/ubuntu-natty.git***

(This is going to take a while.  If it's not done in 20 minutes, wait longer)

What that gives you is the entire kernel tree for Natty.  Which isn't good since we want a specific one.  You can see which ones are available by doing the following:

[B][I]cd ubuntu-natty

git tag -l Ubuntu-*[/I][/B]

Which gave me the following options:

Ubuntu-2.6.36-0.1
Ubuntu-2.6.36-0.2
Ubuntu-2.6.36-0.3
Ubuntu-2.6.36-0.4
Ubuntu-2.6.36-1.6
Ubuntu-2.6.36-1.7
Ubuntu-2.6.36-2.8
Ubuntu-2.6.37-2.10
Ubuntu-2.6.37-2.9
Ubuntu-2.6.37-3.11
Ubuntu-2.6.37-4.12
Ubuntu-2.6.37-5.13
Ubuntu-2.6.37-5.14
Ubuntu-2.6.37-6.15
Ubuntu-2.6.37-6.16

Of those, I chose Ubuntu-2.6.36-2.8.  So I need to tell it I want to strictly work with THIS particular version rather than the generic tree:

***git checkout -b temp Ubuntu-2.6.36-2.8***

...and there you have it!  The Ubuntu kernel source code.

---

### Post by kr651129 on 2010-12-13
> **Alterax said:**
> Actually, I think I can help you out here.  I'm currently working on a problem with this same tree and the bcmwl kernel module.

The recommended method for getting the kernel sources with Ubuntu customizations are by using git.  And here's how it's done:

[B][I]sudo -i
cd /usr/src[/I][/B]
***git clone git://kernel.ubuntu.com/ubuntu/ubuntu-natty.git***

(This is going to take a while.  If it's not done in 20 minutes, wait longer)

What that gives you is the entire kernel tree for Natty.  Which isn't good since we want a specific one.  You can see which ones are available by doing the following:

[B][I]cd ubuntu-natty

git tag -l Ubuntu-*[/I][/B]

Which gave me the following options:

Ubuntu-2.6.36-0.1
Ubuntu-2.6.36-0.2
Ubuntu-2.6.36-0.3
Ubuntu-2.6.36-0.4
Ubuntu-2.6.36-1.6
Ubuntu-2.6.36-1.7
Ubuntu-2.6.36-2.8
Ubuntu-2.6.37-2.10
Ubuntu-2.6.37-2.9
Ubuntu-2.6.37-3.11
Ubuntu-2.6.37-4.12
Ubuntu-2.6.37-5.13
Ubuntu-2.6.37-5.14
Ubuntu-2.6.37-6.15
Ubuntu-2.6.37-6.16

Of those, I chose Ubuntu-2.6.36-2.8.  So I need to tell it I want to strictly work with THIS particular version rather than the generic tree:

***git checkout -b temp Ubuntu-2.6.36-2.8***

...and there you have it!  The Ubuntu kernel source code.

I have the vanilla kernel installed from the website, are these ubuntu stream lined kernels really any faster?

---

