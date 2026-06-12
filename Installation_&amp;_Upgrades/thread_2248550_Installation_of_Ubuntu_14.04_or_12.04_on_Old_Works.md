---
title: "Installation of Ubuntu 14.04 or 12.04 on Old Workstations for use as a contact center"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by Murphy1138 on 2014-10-15
Hello all, not sure this is the right section to ask for help on this but its would be great to have some response and help and how to.

I'm working for a new start up company that has bought the old assets of a company that went into administration. 

I'm running in a 2012 R2 Domain with the main office PCs running Windows 7 and Windows 8.1, these are fine for the general office. 
I have approx 300 Dell Optiplex 620 P4 3.0GHZ with 4GB of ram which I would like to use for our contact center workstations. ( we are trying to save money as a startup) 

The aim is that the contact center staff will have no pens/paper/personal phones or access to anything on the workstation other than a WebBrowser (Firefox).

I need the Ubuntu Install to only allow Firefox to run and only access a specific web url of our contact center system.
Nothing else, not other programs are allowed to run or should even be installed, I would ideally like the workstations added to the domain so that I can add the users of the contact center to AD and centrally manage them from there.

Has anyone got any experience in setting up this type of locked down environment?
If so any help would be really appreciated.

Thanks,
Tom

---

### Post by slickymaster on 2014-10-15
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by mörgæs on 2014-10-16
Interesting project. I have not tried myself and can't guide you in detail, but you could begin studying Ubuntu as a kiosk, for example 
[http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/](http://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/)

---

### Post by Murphy1138 on 2014-10-16
Thanks for the link, I have managed to setup a kiosk build, trying to work out how to lock down the browser and looking at an open source proxy so i can restrict access from the Contact center users. Good thing I have a few months to get this sorted.

Might even approach Canonical for advice and pay them if i cant sort it, or put a bounty out there

---

