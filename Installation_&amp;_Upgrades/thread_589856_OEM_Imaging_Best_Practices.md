---
title: "OEM Imaging: Best Practices?"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by VSack on 2007-10-24
Hello all!

I am currently in the middle of a minor project for work.  I have been tasked with creating mobile workstations that will access our ERP tools for inventory control and the like in our warehouses.

I have a plan that involves chromeless RDP, Wi-Fi and Ubuntu instead of creating Windows machines that would inevitably be gunked up. 

So here is my plan on installation for the six pilot machines for this project.  Questions I have are bolded below:

1. I go through the 7.10 alternate disk installation.

2. On first boot, I configure the system exactly how I want it to look for the machines.  This includes dropping in a few scripts, shortcuts on the desktop, etc.

3. Once all the changes I have made are complete and the system is ready for snapshotting, I CLI sudo oem-config-prepare.

4. **At this point, I want to burn this to a disk, so that I can duplicate this installation across the other computers.  What procedure should I use to do this?  If and when this is accomplished, should the machines all be perfect images of each other, or can I have hardware variance and Ubuntu will accomodate?**

5. I grab another workstation, slap my disk haphazardly into the machine, and click one button to install it.

6. Profit! ;)

I really have searched high and low for a definitive answer on the subject, to no avail.  Furthermore, it seems that the oem prep tool does not change the name of the computer...which poses a problem if I use the disk to image in a network. Finally, I am coming from a Windows background and know that part of sysprep is a regeneration of the computer's SID...do I have to be concerned with anything similar in Linux?

Thank you all in advance for the help!  I can't wait to start using Ubuntu Linux more and more in our environment!

- John

---

### Post by commonplace on 2007-10-25
I, too, would like to know how to do this. Any help out there?

/Kevin

---

### Post by seipherdj on 2007-10-25
Instead of CD's at work I use a DRBL server. Might be worth a check.... clonezilla is great with ntfs .... and Ive never had a problem restoring or saving a linux image.
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by commonplace on 2007-10-25
> **seipherdj said:**
> Instead of CD's at work I use a DRBL server. Might be worth a check.... clonezilla is great with ntfs .... and Ive never had a problem restoring or saving a linux image.
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

Wow, that's exactly what I wanted, but didn't think existed! The page seems to be messed up at the moment, but I'll definitely check it out. Thanks!

/Kevin

---

