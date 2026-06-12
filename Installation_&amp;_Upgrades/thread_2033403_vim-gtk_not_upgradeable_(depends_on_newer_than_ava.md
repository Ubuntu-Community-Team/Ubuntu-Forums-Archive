---
title: "vim-gtk not upgradeable (depends on newer than available vim-gui-common)"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by zasran on 2012-07-26
On Ubuntu 12.04 (apt sources include precise-updates, I did not hold any packages as far as I know):

erik@jojda:~$ sudo apt-get install vim-gtk
...
The following packages have unmet dependencies:
 vim-gtk : Depends: vim-gui-common (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
           Depends: vim-common (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
           Depends: vim-runtime (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.

When I look at which version of vim-gui-common is available:

erik@jojda:~$ dpkg -l vim-gui-common
...
ii  vim-gui-common                  2:7.3.429-2ubuntu2              Vi IMproved - Common GUI files

When I look at the ubuntu web site:

[http://packages.ubuntu.com/precise/editors/vim-gui-common](http://packages.ubuntu.com/precise/editors/vim-gui-common) lists vim-gui-common (2:7.3.429-2ubuntu2)

[http://packages.ubuntu.com/precise-updates/editors/vim-gui-common](http://packages.ubuntu.com/precise-updates/editors/vim-gui-common) lists vim-gui-common (2:7.3.429-2ubuntu2.1)

When I look into /var/lib/apt/lists/* I don't see package listed at all (following command returns nothing: grep '^Package: vim-gui-common' /var/lib/apt/lists/*)

I tried sudo apt-get clean and sudo apt-get check,. even tried to remove /var/lib/apt-lists and rerun sudo apt-get update (files recreated), didn't help.

Why does apt-get think that last version of vim-gui-common is 2:7.3.429-2ubuntu2 and not 2:7.3.429-2ubuntu2.1?

Any ideas how to troubleshoot further? Thanks!

        erik

---

### Post by dino99 on 2012-07-26
[https://launchpad.net/ubuntu/+source/vim](https://launchpad.net/ubuntu/+source/vim)

download the required packages to an empty folder, then from there:

sudo dpkg -i *

---

### Post by Cheesehead on 2012-07-26
> **zasran said:**
> 
The following packages have unmet dependencies:
 vim-gtk : Depends: vim-gui-common (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
           Depends: vim-common (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
           Depends: vim-runtime (= 2:7.3.429-2ubuntu2.1) but 2:7.3.429-2ubuntu2 is to be installed
**E: Unable to correct problems, you have held broken packages.**

I suggest synaptic. Use the filter to find the broken package(s) and fix or reinstall them.

Check that your sources.list for precise-updates includes main.

---

### Post by zasran on 2012-08-08
Thanks!

Checked /etc/apt/sources.list and there is one line for precise-updates:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates restricted multiverse universe

Any ideas why main is not there? I only changed the file using software sources dialog (I get to from update-manager when clicking on Settings)

After adding main to the line above it works:

vim-gtk                    2:7.3.429-2ubuntu2.1

---

