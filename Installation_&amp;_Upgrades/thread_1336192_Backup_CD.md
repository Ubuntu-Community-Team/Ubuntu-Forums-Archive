---
title: "Backup CD"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by pactroclo on 2009-11-24
hi
[LEFT]well, this is my first post in the forum and i have a question, hope you can help me 
I've been using ubuntu  for 3 months now, but i'm still new at this.

For my carreer, i usually "play :p" a lot with the computer (changing between linux distros and windows, add/remove or change software/hardware, etc), and when something goes wrong, having a backup disc it's very helpful.

With ubuntu the problem is installing all the packages over and over again, everytime something goes wrong, i tried using "AptonCD", but it's almost the same , and partitions are not an option.

is it possible to create an ubuntu disc with the actual configuration and downloaded packages, so the next time i format my computer (or something else happens), i'd have the option for just inserting my disc and have everything in order again (all the packages installed)??

i'd appreciate the help


[/LEFT]

---

### Post by dhavalbbhatt on 2009-11-24
I think what you are looking for is "clonezilla". I haven't personally used it, but I see a lot of posts in here that talk about creating an image and using that image to re-boot/reinstall using Clonezilla.

---

### Post by phillw on 2009-11-24
> **pactroclo said:**
> hi
[LEFT]well, this is my first post in the forum and i have a question, hope you can help me 
I've been using ubuntu  for 3 months now, but i'm still new at this.

For my carreer, i usually "play :p" a lot with the computer (changing between linux distros and windows, add/remove or change software/hardware, etc), and when something goes wrong, having a backup disc it's very helpful.

With ubuntu the problem is installing all the packages over and over again, everytime something goes wrong, i tried using "AptonCD", but it's almost the same , and partitions are not an option.

is it possible to create an ubuntu disc with the actual configuration and downloaded packages, so the next time i format my computer (or something else happens), i'd have the option for just inserting my disc and have everything in order again (all the packages installed)??

i'd appreciate the help


[/LEFT]


I use a script based on this thread to 'photo-copy' my installation before any major updates  [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

It's an excellent discussion on backing up and restoring.

Keryx can produce a cd with all your apps on it.[http://keryxproject.org/](http://keryxproject.org/)

Getting a list of packages etc can be done via  [http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager](http://ubuntuforums.org/showthread.php?t=1057608&highlight=synaptic+package+manager)

FFox bookmarks can be exported, if you use FFox to save passwords, then PasswordExporter is a plug-in for FFox that will look after them for you.

Those should keep you busy for a while ;)

Me ? I save my passwords seperately then just use the backup script to 'photo-copy' my machine. But, that's just the way I do it - you choose which ever method suits you.

Regards,

Phill.

---

### Post by Mark Phelps on 2009-11-24
If you just want a simple, easy to use image backup/restore app, check out PING at windowsdream.com.  

This is a front-end to Partimage, that comes as an ISO file, can be burned to CD, or installed on the hard drive, and provides a basic GUI for saving and restoring partitions.  

It's also relatively fast -- can backup or recovery my Ubuntu installation in under 10 minutes.

---

