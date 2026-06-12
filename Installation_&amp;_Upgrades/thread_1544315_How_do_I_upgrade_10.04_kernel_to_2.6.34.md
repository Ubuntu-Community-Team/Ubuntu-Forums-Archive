---
title: "How do I upgrade 10.04 kernel to 2.6.34?"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by tentimes on 2010-08-02
Hi,

The new kernel has some features I think would be useful for me, especially the power management of ATI gaphics cores (I run crossfire 2870).

Could someone explain how I upgrade the kernel please? I did a google search, but the articles I am getting are years old and I just wanted to check that I am doing the right thing. I had intended updating with apt-get using the age old instructions.

Could someone please confirm this is ok, or even better offer some further advice?

Thanks very much.

---

### Post by Icarus315 on 2010-08-02
tentimes, first of all you should not be upgrading the kernel without an absolute solid reason to do so.  Upgrading to a custom kernel leaves you in a support position where you are responsible for security updates which may be difficult to come by.

With that said, see: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") for the latest kernels.  You are running 10.04 so this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/") is the one you will be interested in.

You need 3 files from that folder.  If you are 32-bit download the two i386 .deb files, and if you are 64-bit download the two amd64 .deb files.  In addition to those two files also download 	linux-headers-2.6.34-020634_2.6.34-020634_all.deb for the third file.

Have all three files you downloaded in their own folder by themselves.  In a console cd to that folder and type: "sudo dpkg -i *.deb" without the quotes.  It will automatically update your GRUB so that on next reboot you will boot into the new 2.6.34 kernel.

Now, back to upgrades.  That kernel is the latest given for Ubuntu 10.04 but there is actually a later one, 2.6.34.1, which is only built for the alpha Ubuntu 10.10 right now.  This highlights the problems with running your own custom kernel: you are not guaranteed to get updates for your system.  Again, you must also manually keep up with the updates yourself and install them when they become available.

So, these are the instructions to do so BUT I really recommend that you do not.

Edit: Ubuntu 10.04 kernels are called "lucid" and Ubuntu 10.10 kernels are called "Maverick."

---

### Post by tentimes on 2010-08-02
Thanks for that. On reflection I think I will hold fire for a bit - but at least it's there for someone to look up now on the forum.

---

### Post by Icarus315 on 2010-08-02
You're welcome, by the time Ubuntu 10.10 comes out hopefully your power management needs will be included by default!

---

