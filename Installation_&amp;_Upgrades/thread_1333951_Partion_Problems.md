---
title: "Partion Problems?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by dashpilot79 on 2009-11-21
I'm trying to Install Ubuntu 9.10 Server Edition 64 Bit.
   during the install orginally i tried to create the following partions 

/dev/sda1	/boot		10 GB
/dev/sda2	/swap		10 GB
/dev/sda3	/		100 GB

/dev/sda4  is a extended partion that holds the following logical partions

/dev/sda5	/home		31 GB
/dev/sda6	/usr		40 GB
/dev/sda7	/var		40 GB
/dev/sda8	/tmp		10 GB


It ended up hanging at about 83% each time, i finally wondered if it was a partion problem so i ended up doing only the first three and leave the rest of the hard drive as free space.  The install worked just fine.  I then tried to manual use Fdisk to create the extended partion and the 4 logical partions and on reboot Gurb hung and never booted.  So i'm guessing there is some type of issue with my choice of partions any thoughts?


Dashpilot79

PS One thing i thought was odd that its a 250 GB HD but it was letting me partion 251.1 GB, not sure if thats normal for Ubunutu or not.


There seems to be an issue with 9.10 and the paritions, as i revered to 9.04 and it worked just fine.  Problem Solved

---

