---
title: "gparted error on deleting partition from macosx (cannot delete)"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by frafu on 2006-08-26
Hello,

I have installed a maxtor 300GB harddisk in my i386ubuntu/celeron box. The harddisk was previously installed in a Powermac G4 and was partitioned and formatted to hfs+ with the disk utility shipped with MacOSX.

Using gparted, I was able to delete all partitions on the harddisk, except the first one called hdb1 with a size of 0.3MB. 

When I try to delete it, I get an Error-Window; but there is no text in the window. Maybe, the last lines of syslog can be helpful: 

```
 
Aug 26 18:16:28 localhost kernel: [17196564.932000] cdrom: open failed.
Aug 26 18:16:28 localhost kernel: [17196564.936000] cdrom: open failed.
Aug 26 18:16:28 localhost kernel: [17196564.992000] cdrom: open failed.
Aug 26 18:16:28 localhost kernel: [17196565.076000] cdrom: open failed.

``` 

As I did not do anything with the cdrom at the time I suppose they are related to the partitioning error. Strange. 

Thanks in advance for any help. 

frafu

---

### Post by frafu on 2006-08-26
Hello, 

The actual LiveCD of GParted is also unable to delete that partition. 

There is a warning sign in the line of that partition in gparted. How can I find out what it means? 

Thanks in advance.

---

### Post by frafu on 2006-08-26
Problem solved with gparted 0.1 shipped with ubuntu. Here is what I did (for the case someone has the same problem): 

After seeing that gparted said that the LabelType of the disk was set to mac (the disk was previously in a powermac), I decided to make a new disk label of type msdos (see Device menu in gparted). 

Setting a new disk label seems to erase all the partitions on the harddisk. 

frafu

PS: WARNING:
If the disk is the first harddisk, you will render the computer unbootable by changing the disk label because you will destroy the bootloader; even if ubuntu is installed on another harddisk. (As far as I could understand, that is what happened to me.)

---

