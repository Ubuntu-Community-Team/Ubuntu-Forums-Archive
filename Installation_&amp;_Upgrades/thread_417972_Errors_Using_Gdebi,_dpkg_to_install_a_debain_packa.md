---
title: "Errors Using Gdebi, dpkg to install a debain package in Feisty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Felix-the-Cat on 2007-04-22
**Instead of upgrading to feisty I decided to just format and start over. everything went fairly smooth. I have programs which i want to install that are not in the repository. they are debian packages and were installed smoothly with the GDebi Installer under edgy. I was a little suprised when i realized that the feisty ubuntu-desktop did not have GDebi by default, but nontheless i installed it with synaptec. When i try to install the package with gdebi i get this error message:**
[IMG]http://www.geocities.com/natnsink/GDebi_gtk.png[/IMG]
**So I changed the permissions and still the same error message. And i know the file isn't corrupted because I have installed it in edgy. I noticed that it did not prompt me for a sudo password as it did in edgy so i decided to run it as sudo in the terminal and here is what i got:**
[IMG]http://www.geocities.com/natnsink/gdebi_bash.png[/IMG]
**Then i decided to try using dpkg and i got this:**
[IMG]http://www.geocities.com/natnsink/dpkg_bash.png[/IMG]
:confused: :confused:

---

### Post by loell on 2007-04-22
as suggested in the command prompt in the screenshots,    


The File is corrupted , it cannot be installed because it does not see it as binary but rather just ascii file.

---

### Post by Landser on 2007-04-22
Something is wrong with the postinst/preinst scripts in the Deb archive. you can still unpack the package manually though

---

### Post by Felix-the-Cat on 2007-04-22
I know the file isn't corrupted because I used it to install in edgy and every .deb that i try to inistall gives me this message. 
I'm wondering if its not working because it itsn't using sudo privlidges. Could that be the problem?
A final question could could compressing a .deb with the archive manager possibly corrupt it?

---

### Post by loell on 2007-04-22
but in the screenshots, your already using sudo. compressing a deb files like putting it in tar.gz or zip , will not affect the structure of the deb file after decomperssing it. if all deb file that your installing will prompt you with this error, then something could be wrong with your installation/packaging system.

---

### Post by Felix-the-Cat on 2007-04-24
Thanks for the help that install was messed up in more than more ways than one due to a corrupted disk so i scraped that and started over and redownloaded all my .debs. After that everything went fine. Again, Thanks

---

