---
title: "Could not perform immediate configuration"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by quindraco on 2012-03-22
I am attempting to upgrade from natty to oneiric on a server with no gui.  Editing my sources list and running apt-get update worked with no problems.  Apt-get upgrade errors out with:

E: Could not perform immediate configuration on 'util-linux'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

It continues to do so despite my best efforts, which I list below.

1)  sudo apt-get install dpkg
2)  sudo apt-get install aptitude
3)  sudo apt-get install apt

The above three updated with no problems, please note.

4)  sudo apt-get -f install

Output:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 564 not upgraded.

5)  sudo aptitude update && aptitude -y safe-upgrade

This had no output.

Anyone know where I should go from here?

---

### Post by 2F4U on 2012-03-22
Do you have enough free space on the partition?

---

### Post by oldfred on 2012-03-22
I just got exactly the same error message in 12.04. My search found an old post in the forums with this solution. It seems upstart does not get installed in order and this has occurred in many versions, but not too common.

sudo apt-get install upstart-job
sudo apt-get dist-upgrade -y

---

