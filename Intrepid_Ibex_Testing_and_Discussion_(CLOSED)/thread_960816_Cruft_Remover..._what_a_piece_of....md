---
title: "Cruft Remover... what a piece of..."
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-10-27
I'm going to say this in rather simple words: I think this shouldn't be installed as default, this is crap!

As someone said on IRC:

<Daisuke_Ido> it's even worse for someone who comes over from windows and installs software from outside sources.  they go to clean things up and all of their custom-installed software is gone.

But that's not all. You open the system-cleaner and you see a bunch of packages marked. No info is displayed, you don't know what the "marked" status mean, and if you decide to press the cleanup button, bye bye packages! no warning, no nada, cero.

Is there a bug report open for this crap?

---

### Post by andrewabc on 2008-10-27
Is it normal when I open it for it the mouse to show it "thinking" and for me to have no options to do anything? Nothing listed?

---

### Post by FlyingIsFun1217 on 2008-10-27
> **andrewabc said:**
> Is it normal when I open it for it the mouse to show it "thinking" and for me to have no options to do anything? Nothing listed?

Thats what I get...

FlyingIsFun1217

---

### Post by surfed on 2008-10-27
> **danf_1979 said:**
> I'm going to say this in rather simple words: I think this shouldn't be installed as default, this is crap!

As someone said on IRC:

<Daisuke_Ido> it's even worse for someone who comes over from windows and installs software from outside sources.  they go to clean things up and all of their custom-installed software is gone.

But that's not all. You open the system-cleaner and you see a bunch of packages marked. No info is displayed, you don't know what the "marked" status mean, and if you decide to press the cleanup button, bye bye packages! no warning, no nada, cero.

Is there a bug report open for this crap?


I strongly agree with this post.

---

### Post by exploder on 2008-10-27
This tool does nothing more than to offer to remove packages that I have installed locally. If the tool offered to clear my apt cache it might have some value but in it's current state it is pretty useless.

---

### Post by Polygon on 2008-10-27
[[IMG]http://img260.imageshack.us/img260/9761/screenshotip4.th.png[/IMG]](http://img260.imageshack.us/my.php?image=screenshotip4.png)[[IMG]http://img260.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

why are the bluetooth and linux-headers marked as cruft?

and why does this package remove custom installed software anyway? i thought it would remove stuff like temporary files...cache....etc....not actual software O.o

and look at some other stuff...libgnuutils? im pretty sure thats important....

---

### Post by danf_1979 on 2008-10-27
Here is the package description, and the package mantainer:

-------->
Maintainer: Lars Wirzenius <lars@ubuntu.com>

Description: clean up a system so it's more like a freshly installed one
system-cleaner finds and removes cruft from a system. Cruft is (currently) packages that apt marks as automatically removable, or that Ubuntu no longer supports.

Homepage: [https://wiki.ubuntu.com/CleanupCruft](https://wiki.ubuntu.com/CleanupCruft)
<--------

If people agree, I think we should open a bug report for this. This software creates more problems than it solves.

---

### Post by jfernyhough on 2008-10-27
Synaptic->Status
Auto-removable->Select, Mark for Complete Removal
Not Installed (Residual Config)->Select, Mark for Complete Removal

In the immortal (and misquoted) words of John C. Dvorak: I GET NO CRUFT.

Apart from extra packages foisted on me by ubuntu-desktop... like cruft remover. It could /at least/ do an 'aptitude clean' or a localepurge which by itself saves at least 20MB (I don't remember exactly, could have been 100MB) on a standard install.

j@t7200:~$ aptitude search cruft
p   cruft    - Find any cruft built up on your system    
j@t7200:~$

---

### Post by danf_1979 on 2008-10-27
After reading the wiki, I think the basic idea of the software is ok, but it is NOT the right time for it now, it is not ready! At this stage, this kind of software is not what you would expect from a mature distro. This package should be removed from ubuntu-desktop.

---

### Post by tuxxy on 2008-10-27
hehe I agree, removed it already :)


Please post link to bug report if make one

---

### Post by andrewsomething on 2008-10-27
[https://bugs.edge.launchpad.net/bugs/285746](https://bugs.edge.launchpad.net/bugs/285746)

Bug #285746   System cleaner removes explicitly installed third-party packages

----

[https://bugs.edge.launchpad.net/bugs/285952](https://bugs.edge.launchpad.net/bugs/285952)

Bug #285952:  request: allow system to clean other unused file like thumbnails, cache

---

### Post by danf_1979 on 2008-10-27
Thanks Andrew :)

---

### Post by FuturePilot on 2008-10-27
> **andrewsomething said:**
> 

----

[https://bugs.edge.launchpad.net/bugs/285952](https://bugs.edge.launchpad.net/bugs/285952)

Bug #285952:  request: allow system to clean other unused file like thumbnails, cache

Yeah that's what I thought it would do in the first place but when I tried it out all it wanted to do was remove my third party packages. I hope that gets integrated into the program soon, it would be nice to clean the temporary cruft files, not just software packages.

---

### Post by pferraro on 2008-10-27
I agree with the poster.  I was hoping the result of this blueprint would do something like clean out the orphaned kernel directories in /lib/modules/*.
Instead, this utility is pointless.  It offers nothing that I can't do more intuitively in Synaptic.  It is also an unsafe assumption to equate "local" packages with "cruft".
In summary, anyone clueless enough to find this tool useful is not the type of person who knows how, when, or why to upgrade their system, and would therefore have no local packages ... and therefore have no need for this tool.

---

### Post by FuturePilot on 2008-10-27
> **pferraro said:**
> I agree with the poster.  I was hoping the result of this blueprint would do something like clean out the orphaned kernel directories in /lib/modules/*.
Instead, this utility is pointless.  It offers nothing that I can't do more intuitively in Synaptic.  It is also an unsafe assumption to equate "local" packages with "cruft".
In summary, anyone clueless enough to find this tool useful is not the type of person who knows how, when, or why to upgrade their system, and would therefore have no local packages ... and therefore have no need for this tool.

Even more about using Synaptic, I noticed that the Cruft Remover doesn't even use the --purge option when removing packages, so even after you use Cruft Remover there's still cruft...

---

### Post by danf_1979 on 2008-10-27
Guys, please post opinions in the LP bug page, so the maintainer see what people thinks about this awesome addition to ubuntu-desktop :)

[https://bugs.edge.launchpad.net/bugs/285746](https://bugs.edge.launchpad.net/bugs/285746)

---

### Post by ciscosurfer on 2008-10-27
> **Polygon said:**
> [[IMG]http://img260.imageshack.us/img260/9761/screenshotip4.th.png[/IMG]]("http://img260.imageshack.us/my.php?image=screenshotip4.png")[[IMG]http://img260.imageshack.us/images/thpix.gif[/IMG]]("http://g.imageshack.us/thpix.php")

why are the bluetooth and linux-headers marked as cruft?

and why does this package remove custom installed software anyway? i thought it would remove stuff like temporary files...cache....etc....not actual software O.o

and look at some other stuff...libgnuutils? im pretty sure thats important....Could it be those packages are no longer needed or have been superceded by others your system has upgraded/downloaded via update manager?  This is my understanding from the man page and the wiki.  To test, you could uncheck everything but say the adobe-flashplugin .deb package, let mr cruft run, and then see if you can still view flash on the web...8-[

Edit: Ah.  After checking on [launchpad]("https://bugs.edge.launchpad.net/ubuntu/+source/system-cleaner/+bug/285746"), I see that this is indeed an issue.

---

### Post by amano on 2008-10-28
They should demote Cruft Remover to universe again for Intrepid, because of its current shortcomings:

1) The "Cruft Remover" string is not translated currently
2) There is no icon.
3) All different kinds of cruft are mixed together without giving you any clue for what is what. There should be sections like "Old kernels (if the current kernel works for you, removing the old ones should be save)", "Old configurations (programs were removed which left their configurations on the system)", "Unused packages (programs that depended on these packages were removed)", "Unknown packages (probably manually installed by yourself)"
4) The "probably manually installed packages should be unticked by default.

Only if all those bugs were fixed, I would consider this ready to be unleashed in main.

---

### Post by phenest on 2008-10-28
> **jfernyhough said:**
> Synaptic->Status
Not Installed (Residual Config)->Select, Mark for Complete Removal

This area is a must for cleaning (I found loads of stuff there). Also:

[LIST]
[*]Wastebasket
[*]/Temp folder
[*]Downloaded cache files
[*]Old kernel versions
[/LIST]

But it should not list any other installed software. This tool should not be used for uninstalling stuff except Kernels.

---

### Post by wgrant on 2008-10-28
system-cleaner has just been removed from the default Ubuntu desktop installation, but it remains in main.

---

### Post by amano on 2008-10-28
Well, that sounds like a sensible decision. Currently more harm can be done with it than it helps making things simpler.

But I can see its future uses and I hope that it gets developed further.


EDIT: Here is the relevant change: [https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009392.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/009392.html)

---

### Post by andrewabc on 2008-10-28
> **wgrant said:**
> system-cleaner has just been removed from the default Ubuntu desktop installation, but it remains in main.

Good, It didn't look good not having an icon and having its own menu.

---

### Post by autocrosser on 2008-10-28
It has been decided to not ship it with 8.10 by default----https://bugs.launchpad.net/ubuntu/+source/system-cleaner/+bug/274714

OPPS--already noted...

---

### Post by BCurtisWX on 2008-10-28
this is good, because i have a mounted backup drive and it tried to remove that with the cruft cleaner.  Not exactly a smart piece of software

---

### Post by sdowney717 on 2008-10-28
I tried it and lost out on a lot of stuff
Now I cant install 

googleearth-4.3-data:

Package googleearth-4.3-data has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by xebian on 2008-10-28
> **tuxxy said:**
> hehe I agree, removed it already :)




Did you use cruft-remover?  It would be interesting to see if it can remove itself.

---

### Post by FuturePilot on 2008-10-28
> **xebian said:**
> Did you use cruft-remover?  It would be interesting to see if it can remove itself.

#-o lol

---

