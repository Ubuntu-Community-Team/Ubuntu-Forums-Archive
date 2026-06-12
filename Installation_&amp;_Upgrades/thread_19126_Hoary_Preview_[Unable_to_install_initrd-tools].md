---
title: "Hoary Preview [Unable to install initrd-tools]"
date: 2005-03-10
forum: Installation &amp; Upgrades
---

### Post by thomas.uhde on 2005-03-10
Hi,

during Hoary Preview Installation the following error occurs:
> Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.

Check /var/log/messages or see virtual console 3 for details
tty3 says:
> Preparing to replace linux-restricted-modules-2.6.10-4-386 2.6.10.3-5 (using ...
/linux-restricted-modules-2.6.10-4-386_2.6.10.3-5_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.10-4-386 ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in
copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
E: Sub-process /usr/bin/dpkg received a segmentation fault.

I have to say that I am booting with noapic nolapic. If I don't - my cd-rom recognition fails.
Thanks for help!

Thomas Uhde

---

### Post by behemot on 2005-03-18
Same problem here.

---

### Post by Happysin on 2005-03-18
I get this as well.  Same everything except that I'm using defualt install.  Verified installation media, swapped out drives an memory just in case, but no dice.

---

### Post by Happysin on 2005-03-18
Update, Warty works fine on the same hardware, if anyone is looking.

---

### Post by Nnyan on 2005-05-02
5.04 cd burned from ISO downloaded recently, getting the same thing.  Don't have the complete error but its mostly this:

E: sub-process /usr/bin/dkpg returned an error code 1
dpkg: error processing ubutu-base (--configure):
dependency problems  leaving unconfigured
Errors were encountered while processing:
Python2.4
Python
report-bug
ubuntu-base

Any ideas?

---

