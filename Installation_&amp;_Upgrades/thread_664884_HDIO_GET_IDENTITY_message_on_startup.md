---
title: "HDIO_GET_IDENTITY message on startup"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by ddewaele on 2008-01-11
After installing ubuntu 7 server edition , I'm getting the following message

ata_id[2377]: main : HDIO_GET_IDENTITY failed for '/dev/.tmp-0.8' 
ata_id[2379]: main : HDIO_GET_IDENTITY failed for '/dev/.tmp-0.8-6'

The system seems to be running without any problems, but I am worried about this.

I only noticed this message after installing Ubuntu for the second time. At that point, I was trying to setup my disks using the LVM Manager, and during that process,  I received an error during the creation of a logical volume. (The error occured after setting the size of the volume that the Ubuntu installation to proposed).

I had to cancel that installation as I was getting an error I couldn't recover from. I'm not able to reproduce it, but I was getting a message indicating "Only continue if you know what you're doing". At that point I could Ignore or Go Back. I chose the second option.

After that, I installed Ubuntu without LVM. The installation was successfull and the system boots fine (with the HDIO message).

I'm not sure if this message also appeared initially (prior to the LVM Manager issue)

The installation occured on a brand new Dell PowerEdge server, so I doubt that there are hardware failures.

(FYI, when installing Fedora Core, the same message appears on startup).

Now, my question is :

Should I be worried about this message
Is there any way to verify that nothing is corrupt in terms of hard disks ?

---

### Post by pgjensen on 2008-06-24
i am getting this with my SAS raid card and can't mkfs or do anything with the drives but format them.  any ideas?

---

