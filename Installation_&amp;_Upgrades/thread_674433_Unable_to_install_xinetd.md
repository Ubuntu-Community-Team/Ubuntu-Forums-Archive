---
title: "Unable to install xinetd"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by jlsf2 on 2008-01-21
Ok, I feel like I'm missing something very obvious here...

For the VMWare Server install, I need to have xinetd installed first.

Great, should be easy:
   sudo apt-get install xinetd

Instead, I get the error message:
---
Package xinted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
---

Any ideas on what I'm doing wrong?

Desktop v7.10, VMWare Server v1.0.4

Thanks.

---

### Post by Partyboi2 on 2008-01-21
sudo apt-get install xinetd should have done the trick. Check Software Sources (System>Admin>Software Sources) and make sure you have on the first tab all the boxes ticked except source code.
Another way is to go [here]("http://packages.ubuntu.com/gutsy/net/xinetd")
and download the package and manually install it by double clicking on it.

---

### Post by jlsf2 on 2008-01-22
> **Partyboi2 said:**
> sudo apt-get install xinetd should have done the trick. Check Software Sources (System>Admin>Software Sources) and make sure you have on the first tab all the boxes ticked except source code.
Another way is to go [here]("http://packages.ubuntu.com/gutsy/net/xinetd")
and download the package and manually install it by double clicking on it.

Yeah, they weren't checked. Thanks a lot that fixed all my (current) problems.

---

