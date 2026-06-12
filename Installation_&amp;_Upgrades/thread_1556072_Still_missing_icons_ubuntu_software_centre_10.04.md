---
title: "Still missing icons ubuntu software centre 10.04"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2010-08-18
10.04 has been around for some time now, and I update regularly.
Strange that there is still the missing icon issue in Ubuntu Software Centre.

Does anyone have a status on this one?

---

### Post by lechien73 on 2010-08-19
Only that it seems to be a bug with the Clearlooks theme. Changing the theme solves it, apparently.

---

### Post by dreamquartz on 2010-08-25
Turns out to be more complicated than I thought.
It has to do with Icons, and not so much Themes.

When the GNOME-icons are used, as an example, it turns out that the Icons for "Fonts", icons under "Games" and under "Science & Engineering" are not present in usr\share\icons\gnome.
They should be located under 64x64\categories, but the folder does not exist.

When using Humanity, all the Icons are present under usr\share\icons\Humanity\categories\64. The naming starts with: "applications-". For the sub folder "Card Games" under "Games"  in the "Ubuntu Software Centre" the icon-name starts with "applications-cardgames".

You should be able to copy the icons you need from one folder to the other, if you are sudo for nautilus.
I realize that the icons under Humanity have the file format of svg, while the icons I want to use have the format of png, but as far as I know, that should be no problem.
Note: When I copied all the files to the folder, I removed the same name icons with the png format.

If you want to use i.e. Dropline Neu (see: [http://art.gnome.org/themes/icon](http://art.gnome.org/themes/icon)) as the icons for your theme, you can copy the icons from the 64 folder under Humanity to the installation folder called Neu (see: your name\.icons).
Note: I renamed the folder to "64x64", instead of leaving it named "64".
It appears to be working right now.

I still would like to change a couple of icons within Dropline Neu ( the one that I am using right now), but I am working on that to figure out where they are, and what they are called.
The icons are the icons for Menu (top left on the top Panel), and the icons for Thunderbird and Firefox. I would like those to be standard.

Cheers,

Dreamquartz

---

### Post by Stray Wolf on 2010-12-02
Dreamquartz - right on.  Finally have the Azenis icon theme displaying the "Font" icon in the Software Center.  I found a good "Font" icon for Azenis in the scalable/mimetypes folder, copied it to scalable/categories, renamed it applications-fonts and Voilà!  Thanks!

---

### Post by tmeehan on 2011-06-25
The solution is to edit the index.theme file in the affected theme, like:
  /usr/share/icons/gnome/index.theme

add this line in the [Icon Theme] section (I put it before the Directories and after Example):
  Inherits=Humanity,gnome,hicolor

Reference this Launchpad bug:
  [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/556335](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/556335)

This sure beats creating directories and copying files previously.

---

