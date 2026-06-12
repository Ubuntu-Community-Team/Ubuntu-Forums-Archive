---
title: "fluxbuntu prob :problem with cd-rom configuration during installation"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by bow on 2008-05-01
hey guys 
I hope it's not inappropriate to ask about fluxbunutu , but because it seems to me that they don't have time to answer my question , I'll ask it here:
I'm trying to install fluxbuntu on my old laptop( as a rescuer!) which is Toshiba Satellite 1710XCDS , (64mb ram) , and during the installation at I think step 4 it says that it can't find the cd-rom module , and I have to choose between inserting my cd-roms driver floppy disk or choosing between modules , and because I dont have the floppy , I choose to select from the modules and type the cdrom path , and there when I choose any module , it doesn't work.I suppose it's because I dont choose the right path for my cdrom, the default is dev/cd but I dont know how to find mine.
 please answer in general terminology cause I'm totally newb in Linux.
thanks

---

### Post by Pumalite on 2008-05-01
First of all, burn a new cd. Do md5sum, burn at 4x or less in good quality CD-R, check CD integrity before install.
OTOH, it's convewnient to have CD-ROM as 2nd Master in BIOS.
Clean the lens in your burner, just in cas.

---

### Post by bow on 2008-05-02
thanks for reply , but I've checked everything's u said , and still it can't find my cd-rom during installation. 
can you tell me how can I find my cdrom path relative to "/dev" ?

---

### Post by Pumalite on 2008-05-02
/dev/scd0

---

