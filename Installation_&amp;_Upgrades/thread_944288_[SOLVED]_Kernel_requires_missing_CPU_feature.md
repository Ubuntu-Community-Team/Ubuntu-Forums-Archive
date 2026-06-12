---
title: "[SOLVED] Kernel requires missing CPU feature"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by sipickles on 2008-10-11
Hello,

I am trying to install ubuntu server onto a little fanless WAFER-MARK pc

I tried intrepid server which installs okay, but then says:

"This Kernel requires a feature not present on your CPU:
pae cx8"

If there a workaround for this?

I was going to try Xubuntu instead. Is there a server version of this? I can't seem to find the download!

Thanks

Simon

---

### Post by wizard10000 on 2008-10-11
> **sipickles said:**
> Hello,

I am trying to install ubuntu server onto a little fanless WAFER-MARK pc

I tried intrepid server which installs okay, but then says:

"This Kernel requires a feature not present on your CPU:
pae cx8"

If there a workaround for this?

I was going to try Xubuntu instead. Is there a server version of this? I can't seem to find the download!

Thanks

Simon

Hi, Simon - 

Server versions of Ubuntu require PAE (physical address extension) support in the CPU, which your VIA processor doesn't have.  Install the desktop version and then just add or remove packages as required  :)

Hope this helps -

---

### Post by sipickles on 2008-10-11
Ok, thanks for clearing that up

---

