---
title: "openoffice 3 has no graphical buttons (pic)"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-02-21
can anybody help me with this one? 

I did not have it installed previously and added it using adept (after my package problems and resizing partitions) and this is what I get when I open writer or any of the suite.  

Notice the buttons:


I wonder if I broke something earlier today...


Thanks!

---

### Post by damis648 on 2009-02-21
> **halfsane said:**
> can anybody help me with this one? 

I did not have it installed previously and added it using adept (after my package problems and resizing partitions) and this is what I get when I open writer or any of the suite.  

Notice the buttons:


I wonder if I broke something earlier today...


Thanks!

This happens when using certain themes (namely dark ones) as far as I've seen.

---

### Post by BwackNinja on 2009-02-21
Change/Set the icon theme for openoffice. In Tools > Options, OpenOffice.org > View.

---

### Post by halfsane on 2009-02-21
I logged into Gnome and all was well.  Still can't get it right, or get it to do anything in KDE.




> **BwackNinja said:**
> Change/Set the icon theme for openoffice. In Tools > Options, OpenOffice.org > View.

I assume under '3D view' or 'graphics output' there is suppose to be a preview of the theme/icons selected in the dropdown? 

I don't have anything there for any selection.




EDIT:  NVMD, checked in Gnome.  I don't have any of the rendering options with KDE.   Any idea what could cause that?

  Doesn't sound like a theme or icon issue anymore.

---

### Post by halfsane on 2009-02-21
another pic of the 'view'menu

---

### Post by todak on 2009-02-21
Try [this]("http://ubuntuforums.org/showthread.php?p=6726763#post6726763") :)

---

### Post by BwackNinja on 2009-02-21
do you have openoffice.org-style-crystal installed?

---

### Post by halfsane on 2009-02-21
> **todak said:**
> Try [this]("http://ubuntuforums.org/showthread.php?p=6726763#post6726763") :)



I thought that would do it, but 'icons only' was already selected.  I changed it around to all the options and no luck still

---

### Post by halfsane on 2009-02-21
> **BwackNinja said:**
> do you have openoffice.org-style-crystal installed?

you friend are a genius! 

somehow I had _none_ of the 'style' packages installed (not even galaxy, the default)?  =D>



Are they dependencies, how would they have been missed, and is that a bug?

---

### Post by calc on 2009-03-04
If you install Ubuntu it automatically installs openoffice.org-style-human, Kubuntu installs openoffice.org-style-crystal. I'm not sure what the other *buntu's do. So if you had neither you did something weird... ;)

---

### Post by halfsane on 2009-03-04
> **calc said:**
> If you install Ubuntu it automatically installs openoffice.org-style-human, Kubuntu installs openoffice.org-style-crystal. I'm not sure what the other *buntu's do. So if you had neither you did something weird... ;)

your exactly right,

I had some odd installer issues and part of my version of fixing it was going through synaptic and ridding myself of all things openoffice. 

of course nothing worked until i removed the packages in question from the file /var/lib/dpkg/status 


Then I re-installed OOo, but the icons did not come with and hence the problem.  I never put it all together.

---

