---
title: "Error 17 after first stage installation"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by Xian81 on 2005-06-19
Hi all, I was previously using windows xp and have no knowledge of linux decided to try out ubuntu but i got a error 17 after the first installation stage.
Managed to finish with the first stage of installation of ubuntu and after that the systems reboots to continue but  then i get this error
GRUB Loading stage1.5.

GRUB loading, please wait
Error 17

previous installation of windows xp on my primary hdd
and ubuntu is installed on a partition on my slave hdd
hope i can get some help with this error

---

### Post by gez on 2005-07-04
I have seen this message too; in my case it was because I had not completed the installation proccess, and more specifically not got to the stage where GRUB* is installed, so it couldn't even give me the option of going into Windows.

I think you need to complete the installation first before rebooting.

*GRUB is the program that lets you choose which operating system to boot.

---

### Post by virtualXTC on 2005-07-12
I thought that my installation may not be complete, and tried several more times and had the same Error 17 issue.

The same install, however, worked fine when the drive was swapped to another machine.  Thus I'm assuming its a bios problem despite the definition of a grub error 17 (taken from: [http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable](http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable) ):

5. Grub Error 17

Situation

Code Listing 5.1: Grub Output

root (hd0,0)
filesystem type unknown partition type 0x7

Error 17 : Cannot mount selected partition

Solution

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

Be sure to check your root(x,y) settings in your grub.conf.

Also, if you are trying to boot Windows, make sure that your grub.conf file has the root (hdX,Y) (or rootnoverify (hdX,Y)) and chainloader (hdX,Y)+1 in it.

---

### Post by adlitinc on 2005-07-13
I had the same problem but I changed the bios setttings for all the ide's to automatic. Everything went smooth from there on

---

