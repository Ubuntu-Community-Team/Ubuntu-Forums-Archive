---
title: "NEWBIE : Ubuntu with no internet connection"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by bowmanr@mailcity.com on 2005-08-15
People,

Good day to you. I am new to Ubuntu (in fact, I've not even installed it yet!!). I've recently ordered some CDs from ShipIt -- [COLOR=Navy]BTW, **thank you** very much for that service.[/COLOR]

Anyway, down to my enquiry if someone would please be kind enough to answer ...

I do not have an internet connection on the machine that I intend to install Ubuntu on ... is there any point in using the install CD?? I basically would like OpenOffice to run, with printing to my printer. I'd like Samba to be running so I can share and see files on my Windows box. I would like Wine and Mono to be up and running, along with the GIMP and Audacity. Are these apps installed off the CD, or do they get downloaded from the internet at install time??

I guess I'm asking if there's anything more than the basic OS installed from the CD, or does everything have to come from the net.*[COLOR=DarkRed] Is there a list of applications installed with the base install and available from the CD?[/COLOR]*

I am evaluating using Linux (hopefully the Ubuntu distro) on any new machines I may aquire over time. Ubuntu will be installed on an old P2 350 for the time being.

I do have the Woody r3 complete CD set, can I install .debs from these into Ubuntu? Debian is kindof installed, but I got it in a bit of a state  [-X ! I plan to remove Debian for Ubuntu -- the nice installer is rather appealing. I can potentially obtain some installs (like the latest Wine and Mono tars, or  I guess the driver to my printer) from work and take them home on a CD to install.

Regards, and thanks for your help
Robert (a Linux newbie)

--

---

### Post by heimo on 2005-08-15
You can check .list files on mirrors - like this:
[http://se.releases.ubuntu.com/5.04/ubuntu-5.04-install-i386.list](http://se.releases.ubuntu.com/5.04/ubuntu-5.04-install-i386.list)

And this is very useful help to find correct package names:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Mono doesn't seem to come with install CD (it's in Hoary universe). I don't recommend using Debian packages in Ubuntu - sometimes it may work, but most of the time you run into dependency problems.

---

### Post by bowmanr@mailcity.com on 2005-08-15
Thanks for the information and the links.

I assume that a .udeb is similar to a .deb? Looks like Open Office 1.1.3 and the GIMP are there, but not Audacity (never mind). Samba is there however.

Can I get just the .udeb files somewhere and take them home on a CD to install the bits I specifically desire?

Robert

---

### Post by heimo on 2005-08-15
For explanation of udeb files:
[http://www.usenetlinux.com/t-457049.html](http://www.usenetlinux.com/t-457049.html)
 >  They are debs that are used in places like the
installer and do not necessarily meet all the policy requirements that a
normal deb would.
 

Yes, you can get the .deb files from Ubuntu repositories on another computer, burn to CD/DVD and bring to offline computer for install. I haven't done that myself, I guess you should try to get a whole repository on DVD(s) or use some tool or "flags" to make sure you get all the dependencies too.

---

### Post by bowmanr@mailcity.com on 2005-08-15
Thanks for the information. Plenty to investigate when the CDs arrive.
Robert

---

### Post by heimo on 2005-08-15
[QUOTE=bowmanr@mailcity.com]Thanks for the information. Plenty to investigate when the CDs arrive.
Robert[/QUOTE]

And before the CDs arrive... :)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

