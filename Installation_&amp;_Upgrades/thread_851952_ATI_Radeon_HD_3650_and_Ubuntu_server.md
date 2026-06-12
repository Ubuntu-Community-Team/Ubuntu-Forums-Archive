---
title: "ATI Radeon HD 3650 and Ubuntu server"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by josephmo on 2008-07-07
How do I get the ATI Radeon HD 3650 driver installed on the Ubuntu server? When I download it from ATI, and I go into a terminal, then chmod +x on the file, and do sudo filename, it tells me it cannot run the command.

---

### Post by wpshooter on 2008-07-07
Are you doing:         ./filename

---

### Post by josephmo on 2008-07-07
Here's a more detailed description of the problem:

I am doing:

sudo ./ati.run --listpkg

I get the following:
[deleted for berevity]
List of generatable packages:
[]
Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
Status: *UNVERIFIED*
Ubuntu Packages:
[]
	Ubuntu/8.04

Then I do:

 sudo ./ati.run --buildpkg Ubuntu/8.04

and I get (just listing the relevant part of the message):

Generating package: Ubuntu/8.04
./packages/Ubuntu/ati-packager.sh: 347: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/fileO9j6QM': not found
Unable to install dpkg-dev.  Please manually install and try again.
./packages/Ubuntu/ati-packager.sh: 347: dpkg-architecture: not found
Error: unsupported architecture:

---

### Post by wpshooter on 2008-07-07
Those last 2 lines seem sort of interesting.

What kind of machine, i.e. processor type and 32 bit or 64 bit are you trying to install this on ?

Make sure that the driver that you are trying to install is the correct version for your machine type.

---

### Post by josephmo on 2008-07-07
> **wpshooter said:**
> Those last 2 lines seem sort of interesting.

What kind of machine, i.e. processor type and 32 bit or 64 bit are you trying to install this on ?

Make sure that the driver that you are trying to install is the correct version for your machine type.

The driver is the only driver available from ATI and it's for the 3xxx family of products. The designation is for x86 and x86_64 (it's in the file name). The machine is capable of supporting both 32 and 64 bit, but I have the 32 bit version of Ubuntu installed.

---

