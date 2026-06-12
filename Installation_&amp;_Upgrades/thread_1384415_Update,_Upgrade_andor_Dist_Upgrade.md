---
title: "Update, Upgrade and/or Dist Upgrade"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by NathanAdler on 2010-01-18
Hi all,

Thanks beforehand for your support. I am begining on Ubuntu Server Management

I would like to receive your help on this doubt... In order to have my Ubuntu Server up to date and with the last security patches, is it enough to do:

sudo apt-get update
sudo apt-get upgrade

?

If not, please where I can find an easy guide in order to keep or mantain my server OK?

Also, what are the risks when we do: sudo apt-get dist-upgrade?

Thank you very much again.


Nathan.

---

### Post by phillw on 2010-01-18
Hi Nathan, welcome to the forums.

>                      **Update the Package Index**: The APT package index is essentially a database of available packages from the repositories defined in the /etc/apt/sources.list file.  To update the local package index with the latest changes made in repositories, type the following:                     [B][FONT=monospace]

[/FONT]sudo apt-get update[/B]>                  **Upgrade Packages**: Over time, updated versions of packages currently installed on your computer may become available from the package repositories (for example security updates). To upgrade your system, first update your package index as outlined above, and then type: 
                     **sudo apt-get upgrade**
                                     
                              > **apt-get dist-upgrade**
    This command installs up-to-date version of packages, and may install additional packages.

Or, put another way ..

dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages"



So, it would be update, then the dist-upgrade to keep up to date

Hope that clarifies it for you.

Regards,

Phill.

---

### Post by phillw on 2010-01-18
OOps - double post ..

---

### Post by NathanAdler on 2010-01-18
Thank you Phill. 



> **phillw said:**
> Hi Nathan, welcome to the forums.



So, it would be update, then the dist-upgrade to keep up to date

Hope that clarifies it for you.

Regards,

Phill.

---

