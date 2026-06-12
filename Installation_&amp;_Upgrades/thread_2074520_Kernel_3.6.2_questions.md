---
title: "Kernel 3.6.2 questions"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Deucalion29710 on 2012-10-21
I downloaded 3.6.2 from kernel.org.  How do I actually install this?  I currently have kernel 3.5.4 installed.  Should I remove it first?

---

### Post by mikewhatever on 2012-10-21
If you've downloaded the deb packages, simply run

    sudo dpkg -i package-name.deb

If not, you may what to try [this]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.2-quantal/").

...and why not use [3.6.3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6.3-quantal/")?

---

### Post by Deucalion29710 on 2012-10-21
OK very cool.  I actually got mine from kernel.org, and it did not come in the form of the .deb files.  Looks like mine came with an extremely complicated decompression process.  

I was unaware of 3.6.3.  I knew about the beta 3.7, but using beta kernels is just asking to break an OS.  Is it advisable to uninstall the previous kernel that I had?  (3.5.4)  Or can I simply install over it?

---

### Post by mikewhatever on 2012-10-22
It's neither advisable nor not advisable, if you don't need it, then uninstall. Installing a newer kernel will not remove the old ones, in fact, you can have as many different kernels installed as the HDD space can hold.

---

