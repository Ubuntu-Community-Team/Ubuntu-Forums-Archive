---
title: "Customizing"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by speedemonV12 on 2005-08-14
Hey i am told to copy files to icons....but i cannot acces the folder...how do i copy somehting from the desktop to...  usr/x11r6/lib/x11/icons

what do i do??

and how do i install a theme that is    .zip   and   .tar.bz2 

thanks

---

### Post by crane on 2005-08-14
[QUOTE=speedemonV12]Hey i am told to copy files to icons....but i cannot acces the folder...how do i copy somehting from the desktop to...  usr/x11r6/lib/x11/icons

what do i do??

and how do i install a theme that is    .zip   and   .tar.bz2 

thanks[/QUOTE]

When coping files all files are case sensitive. Plus you would need to be root to cp opy into there. so use sudo command and proper capilat letter where needed.

[color=red]sudo cp newicons /usr/X11R6/lib/X11/icons[/color]

---

### Post by crane on 2005-08-14
you also have a hidden file in your home directory to but icons in.
 
.icons

---

### Post by speedemonV12 on 2005-08-14
and how do i install a theme that is .zip and .tar.bz2



??

thanks

---

### Post by speedemonV12 on 2005-08-14
and when i try to do the sudo cp ...it says

 sudo cp blue_src /usr/X11R6/lib/X11/icons
cp: omitting directory `blue_src'


???
thanks
speedy

---

### Post by crane on 2005-08-14
[QUOTE=speedemonV12]and when i try to do the sudo cp ...it says

 sudo cp blue_src /usr/X11R6/lib/X11/icons
cp: omitting directory `blue_src'


???
thanks
speedy[/QUOTE]

sudo cp blue_src /usr/X11R6/lib/X11/icons/blue_src

you need to tell it what to name the file after it's copied

---

### Post by crane on 2005-08-14
[QUOTE=speedemonV12]and how do i install a theme that is .zip and .tar.bz2



??

thanks[/QUOTE]
This I'm not real familiar with  because I haven't installed any exrta themes. A quick search for installing themes should help.

---

### Post by Sam on 2005-08-14
[QUOTE=speedemonV12]and how do i install a theme that is .zip and .tar.bz2



??

thanks[/QUOTE]
Go to menu System, Preferences, Theme. Click on button 'Install Theme...', browse for your .zip or .tar.bz2 file.

---

### Post by speedemonV12 on 2005-08-14
ya that is what i do...but once i do it says it is not a valid theme file..but these are themes that i have seen many people use before ??!?!!!

thanks
speedy

and then when i try to do 

sudo cp blue_src /usr/X11R6/lib/X11/icons/blue_src

it still says that   blue_src ommited???
what is going on ?????


thanks 
speedy

---

### Post by crane on 2005-08-14
[QUOTE=speedemonV12]

and then when i try to do 

sudo cp blue_src /usr/X11R6/lib/X11/icons/blue_src

it still says that   blue_src ommited???
what is going on ?????


thanks 
speedy[/QUOTE]
Sorry myfault. I forgot to tell you to use the -R switch which tell it to copy evrything recursively in the folder

sudo cp -R blue_src /usr/X11R6/lib/X11/icons/blue_src

---

### Post by speedemonV12 on 2005-08-15
okay thanks

---

### Post by mcduck on 2005-08-15
I have installed all my themes by downloading them to desktop and then drag+drop the zip to theme selection window...
Works for all GTK- Metacity and Icon themes. :D

---

### Post by speedemonV12 on 2005-08-15
Ya thats what i do for most of them...but this one is   23679-Clearlooks-CleanEyes-0.6.zip.....and when i tro to put it in the theme thing it does not work..says invalid file type

---

