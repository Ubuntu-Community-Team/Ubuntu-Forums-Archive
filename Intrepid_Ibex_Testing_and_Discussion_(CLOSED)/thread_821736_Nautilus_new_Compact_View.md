---
title: "Nautilus new Compact View"
date: 2008-06-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by MaX on 2008-06-07
So what do you think about the new Compact View in Nautilus?

I think it's great but needs some work regarding whitespaces and column sizes.

What do you think?

---

### Post by Eclipse. on 2008-06-07
I like it alot along with nautilus new tabs feature, its not in intrepid yet but I just compiled nautilus from SVN and its there so it should reach intrepid soon.;)

---

### Post by olskar on 2008-06-07
Sreenshot? :)

---

### Post by talkingwires on 2008-06-07
Screenshots or links?

**[EDIT]**Nevermind. First result on Google: [http://blogs.gnome.org/cneumair/2008/03/30/compact-view-has-landed-in-nautilus-trunk/](http://blogs.gnome.org/cneumair/2008/03/30/compact-view-has-landed-in-nautilus-trunk/)

---

### Post by Eclipse. on 2008-06-07
[img]http://arstechnica.com/journals/linux.media/nautilus-tabs.png[/img]

Not my desktop but its real.

---

### Post by olskar on 2008-06-07
The tabs looks nice..what is the "Compact View"? Is it that the columnwidth adapts to the filenamelength?

---

### Post by King_Critter on 2008-06-07
I'll switch back to Nautilus when they give the user an option to display filenames to the right of the icon rather then below it, like Thunar does. For some reason I just can't live without that feature. :-/

[[img]http://kupax.com/pthumbs/small/98/Screenshot-critter%20-%20File%20Manager.png[/img]](http://kupax.com/public/view/98)

---

### Post by Bou on 2008-06-07
> **King_Critter said:**
> I'll switch back to Nautilus when they give the user an option to display filenames to the right of the icon rather then below it, like Thunar does. For some reason I just can't live without that feature. :-/

[[img]http://kupax.com/pthumbs/small/98/Screenshot-critter%20-%20File%20Manager.png[/img]](http://kupax.com/public/view/98)

That's pretty much what compact does. And yeah it IS in Intrepid :D

---

### Post by Occasionally Correct on 2008-06-07
> **King_Critter said:**
> I'll switch back to Nautilus when they give the user an option to display filenames to the right of the icon rather then below it, like Thunar does. For some reason I just can't live without that feature. :-/

[[img]http://kupax.com/pthumbs/small/98/Screenshot-critter%20-%20File%20Manager.png[/img]](http://kupax.com/public/view/98)

[See here](http://img61.imageshack.us/img61/2703/nautilustextbesideiconsji7.png) (this is in Hardy, and I'm certain it's been there for a long time). :)

---

### Post by King_Critter on 2008-06-07
> **Bou said:**
> That's pretty much what compact does. And yeah it IS in Intrepid :D

Close, but not quite.

Unless you can make the icons bigger, in which case it would be... hmm, maybe I'll check out later today.

---

### Post by plun on 2008-06-07
> **Eclipse. said:**
> 

Not my desktop but its real.

Well...cannot see any Tabs with a compiled Nautilus SVN, its 2.23.4.
Compact View is OK.


build-dep throws in a lot of stuff :confused:, autoremove after install


Maybe Eel also must be upgraded...  Testing..:)

---

### Post by Eclipse. on 2008-06-07
> **plun said:**
> Well...cannot see any Tabs with a compiled Nautilus SVN, its 2.23.4.
Compact View is OK.


build-dep throws in a lot of stuff :confused:, autoremove after install


Maybe Eel also must be upgraded...  Testing..:)

[http://svn.gnome.org/viewvc/nautilus/branches/multiview/](http://svn.gnome.org/viewvc/nautilus/branches/multiview/)

---

### Post by MaX on 2008-06-07
> **King_Critter said:**
> Close, but not quite.

Unless you can make the icons bigger, in which case it would be... hmm, maybe I'll check out later today.

Just press the + on the zoom and you'll get bigger icons.

Trouble is everything else gets bigger too.
This is what I mean when I say it needs some work.

The whitespaces are too big and whatever controls the width of the columns needs to be properly computed. If I zoom out now it just makes the columns smaller instead of filling the window and printing out the full name of the files.

Also, Could we please try to actually have people who have and can try this comment?

---

### Post by plun on 2008-06-07
> **Eclipse. said:**
> [http://svn.gnome.org/viewvc/nautilus/branches/multiview/](http://svn.gnome.org/viewvc/nautilus/branches/multiview/)

Aha... it is a branch.

Well I must also fix Eel, compile fails for the mutiview branch
> 
nautilus-autorun.c:1199: error: implicit declaration of function ‘eel_preferences_get_boolean’
nautilus-autorun.c:1199: error: nested extern declaration of ‘eel_preferences_get_boolean’
make[2]: *** [nautilus-autorun.lo] Error 1


Time to sleep....:)

---

### Post by plun on 2008-06-07
> **MaX said:**
> Just press the + on the zoom and you'll get bigger icons.

Trouble is everything else gets bigger too.
This is what I mean when I say it needs some work.

The whitespaces are too big and whatever controls the width of the columns needs to be properly computed. If I zoom out now it just makes the columns smaller instead of filling the window and printing out the full name of the files.



Yup, The same for me... broken.

---

### Post by Eclipse. on 2008-06-07
> **plun said:**
> Aha... it is a branch.

Well I must also fix Eel, compile fails for the mutiview branch



Time to sleep....:)

The plan is for it to be merged into trunk for .24.

It just need a little polish.

---

### Post by ShirishAg75 on 2008-06-08
Compact view is View > Compact View but I don't get the list . I want it to be compact but having list details, still not there :(

---

### Post by tech0007 on 2008-06-09
> **Eclipse. said:**
> [img]http://arstechnica.com/journals/linux.media/nautilus-tabs.png[/img]

Not my desktop but its real.

how did you get the tabs?

---

### Post by Gourgi on 2008-06-09
> **tech0007 said:**
> how did you get the tabs?

tabbed nautilus will be available for intrebid at september 
as written here 
[http://arstechnica.com/journals/linux.ars/2008/05/27/gnome-file-manager-gets-tabbed-file-browsing](http://arstechnica.com/journals/linux.ars/2008/05/27/gnome-file-manager-gets-tabbed-file-browsing)

maybe it available at gnome svn already

[COLOR="Red"]edit[/COLOR]
[http://svn.gnome.org/viewvc/nautilus/branches/multiview/](http://svn.gnome.org/viewvc/nautilus/branches/multiview/)

the branch if anyone is brave to build :D

[COLOR="Red"]edit2[/COLOR]
building details ... [http://ubuntuforums.org/showthread.php?t=810150](http://ubuntuforums.org/showthread.php?t=810150)

i still resist on trying it :D

---

### Post by tech0007 on 2008-06-09
not in the II repo yet? i'll try the svn build.

---

### Post by ingvildr on 2008-06-09
Good to see that they are stepping up the features of the Browser mode but since I use the default spartal mode its not really that compelling.

On the other hand, being able to hold a DnD selection over a folder and have it open it, or have nautilus open archives as actual folders instead of using File Roller, now that would be sweet.

---

### Post by Eclipse. on 2008-06-09
Heres the new tab view which will be in .24 aswell.

Finally got it to compile.;)

[IMG]http://i31.tinypic.com/6z3hwp.png[/IMG]

---

### Post by MaX on 2008-06-09
So could we split this into a thread discussing Tabbed Nautilus and let this one be about the Compact view?

---

### Post by tfm_copycat on 2008-06-22
Hello, I'm new to the forums.

I've been trying to compile the nautilus svn trunk, but I don't want to install eel2.3.x (or any of its millions of dependencies)
Do I have to make my system unstable and install all the depending packages in intrepid to be able to use the compact lists?

I love thunar, but it cannot be integrated to the system (FUSE) and for unknown reasons (even the latest build) it hangs every now and then.

Is there a way to ignore the autogen requirements?

Thanks!

PS: Tjenna MaX!

---

### Post by tfm_copycat on 2008-06-23
So, I found out a way by myself.

[I wrote a guide in my blog.]("http://www.zdi.it/?p=11")

---

### Post by soccerboy on 2008-06-23
very nice feature.  love it.  What is spatial view vs browser mode?

---

### Post by nycste on 2008-07-26
very nice thread, there are a few like it

[http://ubuntuforums.org/showthread.php?p=5463205#post5463205](http://ubuntuforums.org/showthread.php?p=5463205#post5463205)

---

