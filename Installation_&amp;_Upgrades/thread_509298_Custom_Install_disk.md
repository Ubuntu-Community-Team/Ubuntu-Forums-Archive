---
title: "Custom Install disk"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by honeydew on 2007-07-25
is there a way to place a script on the Install CD so I can change a number of settings on the server installation?  I need to install a handful of packages.  This is for a company that needs to release locked desktop laptop installations.  Now it would not be difficult for me to go and modify each one, and that is what I have done so far.  But it would be really nice if the applied patches could allready be on the CD.  I have checked out the reconstructer and UCK but neither of these seem to offer enough elbow room.    If anyone has any chipper ideas, let me know.

---

### Post by tgm4883 on 2007-07-25
[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

>  What is Reconstructor?
Image 	Reconstructor is an Ubuntu GNU/Linux CD Creator.

It uses the Desktop(Live), Alternate(Install), or Server disc as a base, and then allows for user customization.

For the Ubuntu Desktop base, you can customize the entire environment.  For instance, you can add/remove software, change the default look (splash, themes, fonts, wallpaper, etc.), add desktop links, etc. 

For the Alternate and Server bases, you can add any additional software to the disc that you would like installed.

Reconstructor is written in python and is licensed under the GNU General Public License (GPL).
 	

---

### Post by honeydew on 2007-07-26
I am looking for a way to physically add packages to the CD.. I have a list of packages that I need to get from a webserver.. and then a few special patch deb files that are not available on the repositories.. I cant seem to figure out how todo this.

---

### Post by tgm4883 on 2007-07-26
The reconstructor would let you physically add the packages to the cd.  Alternatively you could write a script to download and install them.

---

