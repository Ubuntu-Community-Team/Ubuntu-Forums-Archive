---
title: "Installation help..."
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by slowlearner on 2006-08-08
hi.. I'm gonna ask this again coz my last question was left unanswered...I hope somebody could help me now coz ive been trying everything already for 2 days but unfortunately, to no avail..

I have here only the ISO image of the installer, an extra HDD and a configured Grub for dos.. Is there a way to install ubuntu using these resources?:confused:

---

### Post by taurus on 2006-08-08
You need to burn that iso file (as an image file, NOT a data file) to a CD, boot from it, and install with it!!!

---

### Post by bensexson on 2006-08-08
You would need a BIOS that could mount and boot from an iso file.

---

### Post by slowlearner on 2006-08-08
If i may add.. I don't have a cd writer.. So i cannot burn it to a cd and boot from it.. I can already start the installation from the harddrive.. but still the installer looks for the cd.. does the installer have any options so that i would be able to point to where installation files are located, instead of it searching on the cdrom?

---

### Post by alecjw on 2006-08-08
I think that you'll have to get a free CD from shipit ( [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) ) if you're prepared to wait a few weeks.

---

### Post by avtolle on 2006-08-08
I don't know if you have already looked at this: [https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies) and it may not be what you are looking for. However, there are a few other methods set out in the How To the above thread is taken from, which may be helpful.

---

### Post by slowlearner on 2006-08-08
> **avtolle said:**
> I don't know if you have already looked at this: [https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies) and it may not be what you are looking for. However, there are a few other methods set out in the How To the above thread is taken from, which may be helpful.
Yup, I already tried that.
But theres a problem with the steps.
This part
> Follow the installation steps as you would any other install, until it comes to choosing a CD to install from. In the case where you have no CDrom drive:

does not appear in the installation. The installer never asks for an installation source.

---

### Post by slowlearner on 2006-08-08
> **alecjw said:**
> I think that you'll have to get a free CD from shipit ( [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) ) if you're prepared to wait a few weeks.
I need to install it ASAP. The shipping will take about 3 weeks to a month coz i live in the philippines.

---

### Post by avtolle on 2006-08-08
Sounds like you have the Desktop iso; how about downloading the Alternate Install iso, and see if its installer (being text based, not graphical) allows you this choice. If you are using the Alternate Install already, then I don't have any other ideas at the present.

---

### Post by slowlearner on 2006-08-08
I have the server iso.. I'll try downloading the alternate.. thnx.. 
I'll let u know if it works.. another question.. can i mount devices during installation? I mean,  I have the installer at hd0,4 how do i mount this during installation? coz the installer offers a  shell. but i wasn't able to mount hd0,4.. If i could do this maybe I can do some workarounds to tell the installer where to find the installation files..

---

### Post by avtolle on 2006-08-08
Sorry, don't know the answer to that question. Gotta get back to work, but if I have time, will see if a search would reveal the answer (maybe you could try, too and we'll compare).

---

### Post by slowlearner on 2006-08-08
got it already! my server is up and runnin! Just needed the right initrd.gz.. thanx.. I thought i have to download the alternate but found out i just needed the right initrd.gz for my installation type(which was hd-media) [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)
and automatically the installer scanned my harddrives for the ISO image.

---

### Post by avtolle on 2006-08-08
Just was ready to post that link; glad you found it, and all is well.

---

