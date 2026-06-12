---
title: "Triple boot, under Places have lost Karmic and Windows 7 OS's"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-02-24
Under Karmic install have Lucid and Windows 7 OS's under Places. In Lucid only Computer and cdrom0 but no Karmic and Windows 7 OS's. Is this a Lucid thing or a Alpha glitch in my Lucid install? Or in fact does anyone else have same? Inconvenient not to be able to access other OS's installed on machine. Triple boot 7/karmic/lucid. Any help appreciated.

---

### Post by Ibidem on 2010-02-24
Are the partitions being mounted? if so, you could add the locations.

---

### Post by garvinrick4 on 2010-02-25
Can boot to all 3 partitions but in Lucid only the partitions do not show up Under Places. Have tried to mount by Terminal and does not recognize they exsist. 
 
Disk utility under System/Admin comes up saying Null. 

fdisk -l is fine.

blkid is fine.

cat /etc/fstab is fine.

With Storage Device Manager (pysdm) can configure and mount other two partitions so can now at least get to
my karmic and Windows 7 from Lucid. Would of course rather see them under Places when Lucid boots.

Any idea's out there?

---

