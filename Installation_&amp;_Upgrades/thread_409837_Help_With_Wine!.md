---
title: "Help With Wine!"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by alexnb185 on 2007-04-15
Ok, so i am trying to get my wireless network adapter to work. I have tryed a lot of stuff... nothing yet... but i have the drivers and appearently wine will make them load and work.. but i can't get wine.. this is the problem.. i type in the commant "audo apt-get install wine" and all is well until this:


alex@alex-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
        Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is to be installed
        Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
        Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
        Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
        Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed
        Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages
alex@alex-desktop:~$



does anyone have any idea.. i went and reinstalled some of them in the systematic thing whatever.. and it stillhappened.. post or email me at [email]alexnbryan@gmail.com[/email] .. please ...please.. help if you have any idea or sugestion.

---

### Post by YokoZar on 2007-04-15
1) You cannot install Windows drivers with Wine, they won't work.
2) You are attempting to install the Edgy (6.10) Wine packages into Dapper (6.06).  Use the Dapper ones.

---

### Post by zvacet on 2007-04-15
Look at Ubuntu wiki for answer,and i you don´t find any google the net.You have to know exact name of your adapter.

---

