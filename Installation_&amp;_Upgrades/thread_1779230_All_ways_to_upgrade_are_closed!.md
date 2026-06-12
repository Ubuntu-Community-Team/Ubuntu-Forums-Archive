---
title: "All ways to upgrade are closed!"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by Boplo on 2011-06-10
Hi,
I am using 10.10 and want to upgrade to Natty but all ways i tried failed:

- I got desktop version (at 28 April :( ) and try to boot via it but there was no option to Upgrade! just "Install alongside" and "reinstall".

- I got alternate version. i did same as Wiki but nothing happend. it means i ran
```
sudo mount -o loop ~/Downloads/ubuntu-11.04-alternate-amd64.iso /cdrom
```
and
```
gksu "ssh /cdrom/cdromupgrade"
```
It opens a terminal window and close it very fast!

- I try to upgrade via update-manager. When Update Manager loads, It shows me some upgarde (about 550MB) and dialog asking "Partial Update". When try to cancel dialog and simply Install updates, nothing happens it means button doesn't work and when i try to using Partial Upgrade, it checks packages, confirm to download about 1150MB (!!) and then shows me errors, something like: Some packages can not be authenticated...

- When i try to "Add Volume" CD from "Software Sources" i got Not-Found error. It checks /cdrom/ while my CD data is placed in /media/cdrom/ . i try to 
```
sudo mount -o loop ~/Downloads/ubuntu-11.04-alternate-amd64.iso /cdrom
```
But no scence.

- I tried to Using "Add CD-Rom" option from Synaptic but its same as "Add Volume" also Synaptic resets /cdrom/ everytime and obviously will find nothing in /cdrom/ 

I had cdrom option in "software sources > Other sources" which asked me CD to /cdrom/ and i tried "sudo mount -o loop..." and it was OK! I got many packages by it from DVD but i got Wrong CD error while upgrading. Someone told me install all available upgrades for 10.10 first and then try again. It seemed well but i missed cdrom option from "software sources > Other sources" and don't know how to bring it back to request CD again and hope that Wrong-CD is fixed and other packages will be installed.

I had no problem with semi-upgraded 10.10 but from yesterday some buttons (such as "Install Updates") doesn't work and i missed "Connection Manager" from taskbar so i can't connect to my VPN. New problems made me to try again to upgrade.


Please Help me fix my Ubuntu
Thanks
Boplo

---

### Post by Boplo on 2011-06-11
Anyone any idea? :neutral:

---

### Post by quequotion on 2011-06-12
There is another way.

I've been working on a method of upgrading Ubuntu based on the Debian method for a while now. I got much of the work done in transition to Natty.

If you have experience using apt-get, and dpkg to resolve dependency problems, you could give my method a try.

**It isn't fully automated;** you'll have to get into a terminal and do some command line magic with apt-get and dpkg.

Before running these scripts, read them thoroughly and Google anything you don't understand.

For me, it was impossible to upgrade by any of the Ubuntu methods because I use a lot of PPAs.

phaseone.sh covers the main upgrade from the official repos.
phasetwo.sh covers the upgrade from PPAs and other repos.

**Don't just run them!**

Also, be warned: a successful upgrade does not mean Natty will work the way you expect it to. I had to make a lot of changes to compiz, unity, and gnome to get Natty working.

---

