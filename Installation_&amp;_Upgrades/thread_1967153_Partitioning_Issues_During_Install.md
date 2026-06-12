---
title: "Partitioning Issues During Install"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by worksofcraft on 2012-04-27
I had a corrupted Ubuntu installation on one partion of my hard drive. All my user account was in a separate partiton and I also a backup partition and a separate drive with Microsoft Windows.

I installed 12.04 and since I didn't want to keep the corrupted Ubuntu 10.4 what I selected to delete it and replace it with 12.04.

What I really did NOT want is for it to reformat and repartion my whole drive loosing all my data and my backup partitions.

Another thing I did not want it to do was to crap all over my windows boot partition because I use the bios boot priority to select which one I want. This is actually quite important because I want my system to restart on the chose OS when there is a power failure.

I think it is high time that Cannonical go have a really serious think about the upgrade procedures and boot loaders because this amateurish crap has no business remaining in the IT industry.

---

### Post by hno3 on 2012-04-27
Let me understand this correctly - You had one partition for / and all the ubuntu system files and you had mounted /home on a separate partition?

If this is correct, then I believe that you can Format the / partition of 10.04 and then install 12.04 in it. You won't be loosing data in your windows and /home partition. Besides you wrote that you had backed up both of them.

---

### Post by ewsmith on 2012-04-27
@worksofcraft:
  Did you select "Delete Disk" on the installer?  If so, then that is completely your fault.  The installer specifically states that it will erase your whole disk, ie: hard drive.

If you need help you can email me.  If you want extremely detailed instructions, I will need to know specific hardware details (hard drive capacity, existing partitions, ram, etc...).
{email deleted}

---

### Post by oldfred on 2012-04-27
@ewsmith
It is good to want to help another user, but the forum is regularly scanned and you would get tons of spam. You can use PM and communicate that way, but we are a forum where we all contribute and try to make for better solutions. As a forum then others can search and find those solutions to help on their own.

@worksofcraft
Are you looking for help or just complaining? We are not the developers but volunteers to help others with Ubuntu. If you have a specific bug you really should report it to the developers.

bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

If you want help, post boot info script from this:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

