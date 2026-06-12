---
title: "Dual Booting with LVM"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Phasmus on 2006-07-17
I have a system with Fedora Core 5 already installed with its standard LVM setup.  I would like to install Ubuntu in the same LV.  I have the alternative install disk, for LVM support, but I haven't been able to find any documentation that indicates how to do this.  The critical information in Fedora's home directory is backed up, but this is a work system so I would really rather not risk disrupting that OS by guessing from one Ubuntu installer screen to the next.  If someone could indicate how to make the Ubuntu installer resize FC5's partition and install on the resulting free space on the LV, or point me to the relevant documentation, I'd really appreciate it.

---

### Post by Phasmus on 2006-07-17
I attempted to test this out using VMWare and two LVM-based installs of Ubuntu (rather than 1 Ubuntu on top of 1 FC as seen in the real machine).  It seems that the installer's partition editor's system for manually adjusting the LVM leads to two options.  Either the logical volumes (not the actual partition that contains them, note) can be resized like regular partitions, or volumes can be reduced/extended from a series of LVM-specific menus.  

The menu method tells me that the existing volume can not be reduced (it may need to be formatted or the kernel may require an LVM module).  It also falsely lists the volume's free space as 0.  I don't have the specific text on hand, for which I apologize.

The conventional resizing interface gives the following error after the resize operation is initiated, and then seems to have done nothing:

Error informing the kernel about modification to partition
/dev/mapper/Ubuntu-root1 -- Invalid argument.  This means linux won't
know about any changes you made to /dev/mapper/Ubuntu-root1 until you
reboot -- so you shouldn't mount it or use it in any way before
rebooting.

ERROR!!!

...

Of course, I don't know if these problems would crop up on a non-virtualized system (with Fedora instead of Ubuntu as the progenitor of the LVM system for that matter).  Nevertheless, this experiment has not increased my confidence to try it on the real computer.  If anyone has any experience or advice in this regard, please let me know.

---

