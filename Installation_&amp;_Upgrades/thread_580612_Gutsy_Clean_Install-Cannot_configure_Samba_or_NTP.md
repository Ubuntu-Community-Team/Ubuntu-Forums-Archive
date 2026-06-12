---
title: "Gutsy Clean Install-Cannot configure Samba or NTP"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mystiq on 2007-10-18
Hello all, I just did a clean install from Fiesty to Gutsy and encountered the following oddity. When I run the System > Administration > Time & Date AND Shared Folders utilities, I try to use them install "NTP Support" (from Manual to Keep Syncronized with....) and "Sharing Services" (Samba/NFS). However, when I click "Install Services", the utility thinks for a bit and then returns with no action leaving me still without NTP or NFS support. 

Further examination reveals a gksu process firing and then a synaptic process running when I click "install services". However, both of these end soon after starting. Running Synaptic from the GUI and doing searches on both 'ntpdate' and 'samba' shows both of these packages installed.

*Why can't I configure these from the utilities?* :confused: This is a very clean installation and this is one of the first things I did with the install (besides installing the restricted driver to support my wireless card). When I installed Fiesty a little more than a week ago, I had no problems with either of these features/functions.

Thanks guys.

---

### Post by mystiq on 2007-10-19
This was very odd, because I did not have to do this with the Fiesty installation, however with Gusty I had to manually change my repositories to the latest before it would properly update and (in this case) download additional packages. Once I changed them and updated the source list, the packages installed normally.

---

