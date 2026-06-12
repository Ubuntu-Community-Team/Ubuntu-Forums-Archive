---
title: "Ubuntu with own target"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by maddis on 2008-10-30
I need to install Ubuntu for multiple computers. I wouldn't want manually do the package selection for every computer so I was thinking how could I make my own target for Ubuntu. Now there is Desktop and Server version. 

My version could be derived from Desktop version, but the list of  packages that are installed by default need to be altered. Some other changes might be needed too, but that's later.

Is it documented anywhere how to make new target for Ubuntu and perhaps generate new installation media for it?

---

### Post by Zalbor on 2008-10-30
I don't really know about that, but perhaps you could choose which ones to install and then make an "apt-get install" line including all of them, and run is as a script from each system?

---

### Post by maddis on 2008-10-31
That would require me to install something first to those computers so that I would be able to run the script. 

Also, later there are coming more computers, so I would make the package more maintainalable(is that a word?). Maybe small changes are needed etc.

---

### Post by Ng Oon-Ee on 2008-10-31
I believe 8.10 has this feature about putting your Ubuntu install on a USB drive to be installed on another computer?

I was just glancing through the promotional material, of course, but I think it mentioned that you could install some packages which you want first and then put your install (with those packages) on a USB drive.

From then on, cloning the drive may help. This, of course, requires that you have quite a lot of USB drives :)

---

### Post by Partyboi2 on 2008-10-31
maybe [[COLOR=Blue]remasterys[/COLOR]]("http://www.remastersys.klikit-linux.com/") might be useful.

---

### Post by maddis on 2008-10-31
Remasterys seems good. I'll give it a try. Maybe later I'll check that Ubuntu 8.10 too.

---

