---
title: "Wheee...posting from Ubuntu!"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-06
Thanks to everyone's help here (and liberal use of the search feature) I've managed to:

- install Ubuntu
- get connected to my wireless router
- force Mozilla to see a different Firefox version number
- install my usual extensions
- smooth out my fonts (boy they looked like crap)
- mount my two NTFS drives and find my favorite wallpaper
- POST HERE!

Thanks everyone for your help.  This is a lot of fun so far.  Now if only my Ph.D. work weren't so reliant on MS-based produts :( .

Joshua

---

### Post by varunus on 2005-08-06
Congrats on getting ubuntu working!  It always feels so...liberating.

What MS programs do you have to use?  OpenOffice can replace MS Office pretty well...at least 2.0 can.  1.1 isn't that great, but the new OO.org is nice.

---

### Post by cjoshuav on 2005-08-06
The biggest hurdle is that all of my bibliographic information is in Endnote.  Beyond that, I do some pretty sophisticated things with spreadsheets and Word documents.  Every version of OO that I've tried has bungled the more complex features I was using.

Is there a really simple primer somewhere for "Hey very experienced DOS/Windows person, here's a guide to how to set up your directory structure and how to save and install new programs in Linux?"

It sure is fun having a command line again...

-Joshua

---

### Post by varunus on 2005-08-06
Have you tried the new openoffice.org 2.0 beta?  (Not the one in synaptic, the most current version.)  There's a guide on how to install it in Hoary here:
[http://wiki.ubuntu.com/OpenOffice2Beta](http://wiki.ubuntu.com/OpenOffice2Beta)

I can answer a few of your questions for directory structure and programs.
First of all, keep all of your files in your home directory or a subfolder of it.  Everything else is designed for use by "the system" (similar to the way a mac works).  A neat trick:  If you make a folder called "Documents" in your home folder, many of your programs will automatically see it and use it as the new default folder for saving files.  You can set up your home directory however you want, and in the file-open and file-save boxes for GNOME programs, you can add shortcuts to any folder you want to the left pane.  (Similar to how Windows has My Documents, Recent, My computer, etc on the left...but this time you get to pick what goes there.)

Don't install programs the Windows way by going to the devel's website; this isn't how things in Linux are done.  First, follow these instructions:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)
Then, use Synaptic (system->Administration->Synaptic Package Manager) to install programs.  With 16,000 to choose from, this is much cleaner than manually installing and uninstalling everything.  Synaptic will also take care of dependencies for you.  If you hear about a program you like, check Synaptic for it first.  Chances are, if you follow the "extra repositories" instructions like in the link, you'll find what you want.

---

