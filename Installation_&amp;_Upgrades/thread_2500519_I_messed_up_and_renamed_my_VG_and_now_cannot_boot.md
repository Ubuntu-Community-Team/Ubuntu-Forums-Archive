---
title: "I messed up and renamed my VG and now cannot boot"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by garnold on 2024-09-04
I made a noob mistake and renamed my vg.

Now I get the following error
[h=1]ALERT! /dev/mapper/ubuntu--vg-ubuntu--lv does not exist. Dropping to shell![/h]Is there a way to rename this back? In the shell I only have the vgchange command and not the vgrename command so I'm not sure what to do?

Thank you

---

### Post by garnold on 2024-09-04
Fixed

First thing I needed to do was create a bootable USB. I grabbed the Ubuntu Desktop iso and burnt it to a stick than booted from that.
Once booted I picked the option to test out Ubuntu off the stick and not install.

Next I opened up terminal and I ran this command to get the list of volume groups

pvdisplay -C --separator '  |  ' -o pv_name,vg_name

This gave me the name of the vg that I should have never created. 

Then I ran the following command to rename the vg back to what was needed to boot

vgrename WHATEVERYOURVGNAMEIS ubuntu-vg

Did a reboot and all is well ;-)

---

