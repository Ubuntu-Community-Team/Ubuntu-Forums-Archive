---
title: "making your own install?"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by uberlinux on 2005-02-03
I have many computers that I use and would like to know if there is a way to make a copy onto CD-R of the installation after I finish configuring things like additional packages and customized settings...kind of like knoppix? 
 I would like to only set up one pc, then put it to cd-r for all the other cds, which will have varying hardware.

---

### Post by kassetra on 2005-02-03
From a friend of mine: 

1. Get partimage.
2. Load the partimage 2 floppy system (boot/root) if you haven't got a way to make partimage load from another distro or disk. 
3. Make backup images of partitions (can be bzipped, split so it fit's on cdr's, etc etc) to a storage partition. 
4. Fdisk new disk so the partitions are the same in size, or larger. Smaller won't work. 
5. Boot, load partimage and "restore" the partitions. 
6. Boot the restored OS by means of rescue floppy/cdr/whatever, install lilo again, and off you go.

Does that help?

---

