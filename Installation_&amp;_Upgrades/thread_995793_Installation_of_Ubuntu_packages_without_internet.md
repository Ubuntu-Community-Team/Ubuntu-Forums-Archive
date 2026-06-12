---
title: "Installation of Ubuntu packages without internet"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by sammyzz on 2008-11-28
Hello !
 I am new to Ubuntu (old guy... was used to red hat few years back).
 We have to install Ubuntu on a new PC in our office.
 Problem is that office network does not allow apt-get kind of automated install over internet.
 Please suggest how to install Multiple packages (how to get dependencies on .deb packages) on my PC ?
Thanks,
samant

---

### Post by albandy on 2008-11-28
You can do something like install a mirror of the repositories

Or if your network requires a proxy you can configure it in apt.

If you are using NTLM authentication you will need to configure a NTLM proxy parser.

You can modify /etc/apt/sources.list to use other repositories

Or you can use UCK (Ubuntu Customization Kit) to make a custom CD/DVD with the required packages.

---

### Post by PryGuy on 2008-11-28
APTonCD, pal... \\:D/

---

### Post by mirex on 2008-12-21
Hi. Here is my how-to if I want to install fresh Ubuntu with all programs without need to download them. You need: some PC with Ubuntu where all these programs are already downloaded and installed.

- Go to directory /var/cache/apt/archive - this is directory where all packages are stored when downloaded. Copy all files from here somewhere on new Ubuntu's disk drive, not necessarily to the apt/archive.
- If you don't have list file ( Packages.gz ) in 'archive' directory then create it like:
dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
which you have to run in directory containing the packages. You can put "Packages.gz" anywhere you like.
- Run Synaptic Manager and go to Settings / Repositories and unselect all the repositories.
- Add new 3rd party repository - a "Packages.gz" list file of the packages you want to add with syntax:
deb file:/directory-where-you-have-the-package-file ./
- Click on 'Reload' icon in synaptic
- run Synaptic, go to 'status' selection section, and choose 'Not installed' list. There you see list of all packages which you copied on your hard-drive, and you can install them.

---

