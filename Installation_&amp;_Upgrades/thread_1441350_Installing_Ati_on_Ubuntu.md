---
title: "Installing Ati on Ubuntu"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by Scris101 on 2010-03-28
so i just installed ubuntu today and i want to install ati, i have an ati radeon HD 3850 256 mb of video memory. how do i install. i looked elsewhere and its telling me to do all of this stuff i have no idea how to du? its a .run file

---

### Post by quadproc on 2010-03-28
> **Scris101 said:**
> so i just installed ubuntu today and i want to install ati, i have an ati radeon HD 3850 256 mb of video memory. how do i install. i looked elsewhere and its telling me to do all of this stuff i have no idea how to du? its a .run file
I am not sure just what your situation is, but I suspect that you have downloaded the correct driver for your hardware and software from the ATI web site.  If this isn't correct then please post with more details.  If it is correct then please read on.

If you have previously installed the fglrx driver then you should uninstall it; Synaptic is a convenient way to do this.  Find fglrx and mark it for complete removal.  But since you just installed Ubuntu then you probably haven't previously installed the driver.

I would suggest creating a temporary directory for the new installation, something like "ati_drivers", and moving the downloaded file into that.  Then change to that directory and type in this:
```
./the_file_name --keep --install
```
substituting the name of the downloaded file for "the_file_name".

When the installation is complete you will have a directory which contains all of the files and directories used by the installation; you can study these if you like, and you can remove the entire directory and everything in it after the installation is finished.  Or you can leave it there for future reference.

If you use System > Administration > Hardware Drivers then be advised that this utility does **not** necessarily tell you correct information.  The system that I am using right now has two HD4870 cards in it and is using the fglrx driver but the utility says that it is not in use.

quadproc

---

### Post by jmillsy on 2010-03-29
Download the 10.3 driver from ati:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

and follow the install instructions.

it will be something like

sudo sh ./path-to-downloaded-file/file_name

then the driver install window will open,, choose your options and away you go.

Josh

---

