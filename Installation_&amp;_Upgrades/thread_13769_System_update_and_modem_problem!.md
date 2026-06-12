---
title: "System update and modem problem!"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by recmar on 2005-02-02
I've just updated my ubuntu and system has automatically added new boot option to menu.lst grub conf file. Now I can boot in two different kernels vmlinuz-2.6.8.1-**3**-386 and  vmlinuz-2.6.8.1-**4**-386. Unfortunately when I'm booting newer kernel my sl-modem connection stops working (after pon command system replies - "/dev/modem doesn't exist" ). What to do?

---

### Post by az on 2005-02-02
You are using the driver for the out-of-the-box kernel.  There were security issues with that kernel and it not only was updated, but upgraded.  Had it only been updated, you would still be able to use the driver.  Since it is upgraded (new version number) the driver needs to be compiled for that new kernel.

You can do it yourself, using the linux-headers for your new kernel.  You would need to boot back into your old kernel to get onto the net.  If you can wait, I will make the modules for the newest kernel available.  If someone else wants to jump in and do it, too, that would be great!


Yes, proprietary hardware drivers are a piss.

---

### Post by az on 2005-02-02
Go here.

[http://www.ubuntuforums.org/showthread.php?p=62021#post62021](http://www.ubuntuforums.org/showthread.php?p=62021#post62021)

---

### Post by recmar on 2005-02-03
Well, when i'm trying to install modules system is complaining about unexpected version number. I've tried install sl-modem-modules using both kernels - same result.

---

### Post by az on 2005-02-03
"I've tried install sl-modem-modules using both kernels - same result"

What do you mean by this?

You installed both packages.  The first one worked for your old kernel and the second one was for the second.  And it is not working?  Did the package fail to install?
what does
sudo apt-get -f install
do?

What kernel are you using?

uname -a

I really want to solve this.  But, the vulnerabilities in the -3-386 version probably exposesyou to much less risk since you are on dialup.

---

### Post by recmar on 2005-02-03
This is what i get:
sudo dpkg -i sl-modem-modules-2.6.8.1-4-386_2.9.9-1_i386.deb
dpkg-deb: unexpected end of file in version number in sl-modem-modules-2.6.8.1-4-386_2.9.9-1_i386.deb
dpkg: error processing sl-modem-modules-2.6.8.1-4-386_2.9.9-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 sl-modem-modules-2.6.8.1-4-386_2.9.9-1_i386.deb

---

### Post by recmar on 2005-02-04
Hi!
First of all I didn't know that I could install modules using apt-get. They just don't appear in my repository.
When I said: *I've tried install sl-modem-modules using both kernels - same result*, I meant that I was booting in both kernels. Now I know that I should try to install new modules on new kernel. Anyway result is as above.

---

