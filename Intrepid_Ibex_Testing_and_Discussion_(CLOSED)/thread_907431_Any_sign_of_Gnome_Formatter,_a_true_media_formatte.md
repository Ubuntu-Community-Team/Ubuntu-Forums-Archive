---
title: "Any sign of Gnome Formatter, a true media formatter ?"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olskar on 2008-09-01
Hi, 
A feature planned for gnome 2.24 was GNOME Formatter that would replace the old and not very useful GFloppy.

Is there any sign of this, by me, long awaited feature?

From roadmap:

> GFloppy

    * Replace with the GNOME Formatter, a true media formatter 

---

### Post by ato on 2008-09-01
/usr/bin/gloppy
It is a part of gnome-utils

---

### Post by olskar on 2008-09-01
Gloppy? Sounds like a fish.

Anyway thanks for answering, any screenshots? :)

---

### Post by olskar on 2008-09-01
Oh, gfloppy? Isn't that the same crappy program that we had for some time now that only works with floppydisks? It sounds like it : /

---

### Post by rondackcpu on 2008-09-01
I could have used a format program on a USB stick today.  I'm sad to say I had to put it in one of the Windows machines to get the job done.

CRS

---

### Post by olskar on 2008-09-01
Yes this is really needed, I really do hope its in or will be in soon

---

### Post by Nullack on 2008-09-01
Have you looked upstream to see how they are tracking against the gnome schedule for .24?

---

### Post by pofigster on 2008-09-01
Can't you just use Gparted to make a new partition on the drive thereby erasing everything (sort of) and doing the same thing (other than naming)?

---

### Post by olskar on 2008-09-02
> **Nullack said:**
> Have you looked upstream to see how they are tracking against the gnome schedule for .24?


Hm they had their feature freeze at 4 August and final release soon, 24 september.. :/


> Can't you just use Gparted to make a new partition on the drive thereby erasing everything (sort of) and doing the same thing (other than naming)?

Sure that is a way to go but its not even installed by default, it would be a bit easier to just right click and format

---

### Post by damoxc on 2008-09-02
Could probably make a nautilus script and utilise one of the mkfs.*?

---

### Post by olskar on 2008-09-03
Got  this from the developer:

> It was basically done and I gave it to the GNOME utils maintainer and he didn't do anything with it. I can't work on it anymore because of my job, but the code is still available - let mr know if you or anyone on that thread want to get involved writing it and I'll be glad to explain how it works. Thanks!

Well, that sucks. Who is the GNOME utils maintainer?

And..yeah..anyone able to work on it? :)

---

### Post by andrewsomething on 2008-09-03
Doesn't seem to be done. There is a working version in SVN apparently: 

[http://live.gnome.org/gnome-format](http://live.gnome.org/gnome-format)

---

### Post by olskar on 2008-09-03
Nope..svn is down 

No repository found in 'svn://paulbetts.org/gformat'

---

### Post by xpaulbettsx on 2008-09-03
Try:

git clone git://paulbetts.org/gformat

or

[http://paulbetts.org/projects/gformat-20080903.tar.bz2](http://paulbetts.org/projects/gformat-20080903.tar.bz2)


Note that it's been over a year since I've done *anything* with this code, and I don't make any guarantees that it will compile, run and won't destroy your data (this *is* a formatting tool!). It never did for me, and I was quite careful, but no promises.

---

### Post by olskar on 2008-09-23
Any news on this?

---

### Post by gnomeuser on 2008-09-23
DeviceKit-disks and the accompanying libraries as well as (and I know I am going to spell this wrong.. damn you davidz for picking such a hard project name) palimpset will solve it once and for all, along with allowing integration of SMART status messages in your desktop and other cool disk related functionality. 

(you have got to love Red Hat for flipping the bill for this work).

So this will be solved in Ibex +1 if they elect to integrate it, Fedora 10 already has it if you want to play with it today.

---

### Post by olskar on 2008-09-23
> **gnomeuser said:**
> DeviceKit-disks and the accompanying libraries as well as (and I know I am going to spell this wrong.. damn you davidz for picking such a hard project name) palimpset will solve it once and for all, along with allowing integration of SMART status messages in your desktop and other cool disk related functionality. 

(you have got to love Red Hat for flipping the bill for this work).

So this will be solved in Ibex +1 if they elect to integrate it, Fedora 10 already has it if you want to play with it today.

I will try it in a virtual machine (love that invention) right away, thanks!

---

### Post by gnomeuser on 2008-09-23
> **olskar said:**
> I will try it in a virtual machine (love that invention) right away, thanks!

for reference the packages you need to install are:

DeviceKit-disks and gnome-disk-utility, then you need a reboot of your system (to start up DeviceKit correctly)

---

