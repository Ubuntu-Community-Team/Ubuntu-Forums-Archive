---
title: "kernel.org checksums"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by SOMDdan on 2011-07-08
I recently downloaded a kernel from kernel.org and I wanted to do a checksum, but I could not find one on the download page. I used ***wget*** to get the download, and I was wondering if it does a checksum automatically, or performs any other kind of verification.

---

### Post by MAFoElffen on 2011-07-08
> **SOMDdan said:**
> I recently downloaded a kernel from kernel.org and I wanted to do a checksum, but I could not find one on the download page. I used ***wget*** to get the download, and I was wondering if it does a checksum automatically, or performs any other kind of verification.
I've never seen a checksum from them... though they do use an OpenPGP-signed signature to verify / certify that the file is from them.

I usually try / test / use kernel already built int debain packages from 
**[Index of /~*kernel*-*ppa*/mainline]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBgQFjAA&url=http%3A%2F%2Fkernel.ubuntu.com%2F%7Ekernel-ppa%2Fmainline%2F&rct=j&q=kernel%20main%20ppa&ei=938XToXZNobSsAODlsDnDQ&usg=AFQjCNHH0Rk4RLsC0SWaJb-pEepOMDaS3w&cad=rja")**

Using and installing them is a whole lot easier and a whole lot less work!

Note on trying out the new 3.0.x kernels-- There's also some code changes you would have to do to get packages to update or install with the new numbering scheme.  I have written some instructions for that if thats what you are trying to do...

---

### Post by SOMDdan on 2011-07-09
> **MAFoElffen said:**
> I've never seen a checksum from them... though they do use an OpenPGP-signed signature to verify / certify that the file is from them.

I usually try / test / use kernel already built int debain packages from 
**[Index of /~*kernel*-*ppa*/mainline]("http://www.google.com/url?sa=t&source=web&cd=1&sqi=2&ved=0CBgQFjAA&url=http%3A%2F%2Fkernel.ubuntu.com%2F%7Ekernel-ppa%2Fmainline%2F&rct=j&q=kernel%20main%20ppa&ei=938XToXZNobSsAODlsDnDQ&usg=AFQjCNHH0Rk4RLsC0SWaJb-pEepOMDaS3w&cad=rja")**

Using and installing them is a whole lot easier and a whole lot less work!

Note on trying out the new 3.0.x kernels-- There's also some code changes you would have to do to get packages to update or install with the new numbering scheme.  I have written some instructions for that if thats what you are trying to do...

thanks. I normally wouldn't create a kernel from scratch, but I am studying for a RHCT certification and need to know how to do a kernel from the ground up.......

---

### Post by Gyokuro on 2011-07-11
gpg --verify linux-2.6.39.3.tar.bz2.sign linux-2.6.39.3.tar.bz2

---

