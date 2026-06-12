---
title: "New installationprocess in ATI Drivers"
date: 2008-06-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olskar on 2008-06-19
The installation process have been updated for ATI drivers. Could this be used to make installing atidrivers even easier in Ubuntu?

> 
As is the case almost every month, the distribution packaging scripts for ATI's driver build / installation process have been updated. This month, however, Catalyst 8.6 brings their second-generation API for this installer. Version 2 of this driver package builder contains a number of enhancements, which will benefit both the package maintainers and end-users. Packaging script maintainers can now utilize an option for automating the installation process. On supported distributions, the user can simply run driver-title.run --buildandinstallpkg and it will not only build the driver package(s) but will proceed to install them using your distribution's package management system.

With version 2 of this API, end-users can now just call --buildpkg (or --buildandinstallpkg) without having to supply the distribution name/release and Catalyst suite will automatically attempt to determine this info. The main distribution to already have updated packaging scripts that comply with this new API is Ubuntu. Over the coming months, more of these packaging scripts should be updated as well.

---

