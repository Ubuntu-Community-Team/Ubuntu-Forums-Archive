---
title: "Program chooser needs to be easier - at least sorted alphabetically"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yfrwlf on 2009-06-26
The program chooser isn't sorted at all.  This is more of a paper cut.  Browsing for a program to open a file needs to be made easier, and alphabetically sorting the available programs is one way to make it easier.

[IMG]http://farm3.static.flickr.com/2565/3661963761_8da753faf6.jpg?v=0[/IMG]

---

### Post by handaxe on 2009-06-26
I believe this is a paper-cut being attended to in the current round.........

HA

---

### Post by deathsshadow77 on 2009-06-26
yes it is

---

### Post by JanDM on 2009-06-26
And [it's already fixed](https://bugs.launchpad.net/hundredpapercuts/+bug/360553) :)

---

### Post by durand on 2009-06-26
Uhm, does anyone else have a problem with multiple entries for the same program?

[IMG]http://files.getdropbox.com/u/336801/Screenshot-Open%20With.png[/IMG]

Brasero is there 5 times but it's not the only one.

---

### Post by EMR on 2009-06-26
Yeah, and that is when it actually shows the list of programs, rather then a random directory.

---

### Post by durand on 2009-06-26
I'm not even sure why it's like that. There should only be one .desktop file for brasero.

---

### Post by Yfrwlf on 2009-06-28
> **durand said:**
> I'm not even sure why it's like that. There should only be one .desktop file for brasero.

I just checked and I am seeing this problem as well, specifically with Brasero, too.  Perhaps it's a problem with Brasero or some other program creating another .desktop file because it failed to check if one existed already?

Any way, I searched for the original issue and didn't find it, funny that it was already marked as a paper cut and fixed.  Thanks all. :)

---

### Post by steeleyuk on 2009-06-28
I could be wrong, I've deleted the entries for Brasero (because of that very reason) but isn't the command run on each on different? I think each of the different "Disc burner" icons relates to a different action within Brasero (i.e. Audio Project, Data Project, Video Project).

It needs fixing one way or another...

---

### Post by Yfrwlf on 2009-06-28
> **steeleyuk said:**
> I could be wrong, I've deleted the entries for Brasero (because of that very reason) but isn't the command run on each on different? I think each of the different "Disc burner" icons relates to a different action within Brasero (i.e. Audio Project, Data Project, Video Project).

It needs fixing one way or another...

Well I don't know if I really like having multiple entries for different actions, but you may be correct about some of them being for different ways of the same program to use the file.  However, many of them *are* real duplicates.  Here is my current list of Brasero entries:

Disc Burner
Brasero Disc Burner
Disc Burner
Disc Copier
Disc Burner

So obviously there should only be one of all of the "Disc Burner" ones, but Disc Copier?  Is that one of the things you were referring to perhaps?  There might be different actions you can perform on a file that is provided by the same program, that would be somewhat understandable, but going back to my above comment this could be done in three different ways that I can think of:

1. Define each different function that could be performed on a file by a program as a new program entry in "Open With".

2. Only have one entry in "Open With", and leave it up to the program to have the options for the user as to what the user would like to do with the file.

3. Have any program which can perform multiple actions on a file add something to the right-click menu, installing that Nautilus plug-in for the user or whatnot.

I love File Roller's Nautilus shortcuts in the right-click menu to do things like "Extract Here" etc.  I like options 2 and 3 myself, but at least with option 1 the "Open With" programs that the user prefers to associate with that file type are quickly available via the right-click menu, so it's context-sensitive which really makes all of the above options work OK.

What I'd suggest though is if you do want to have multiple "Open With" entries for one program, you might want to lump them into an expandable list where you have the little arrow, like what is in "keyboard shortcuts".  So each program would have a little arrow if it had multiple actions, that way you wouldn't clutter up the list too much.

---

### Post by yelo3 on 2009-06-28
No: there are multiple .desktop files
the problem is that every one has the same name.

But they are not the same, since they use different options when calling brasero

---

### Post by Yfrwlf on 2009-06-28
> **yelo3 said:**
> No: there are multiple .desktop files
the problem is that every one has the same name.

But they are not the same, since they use different options when calling brasero

Then obviously they should have renamed the entries that show up in "Open With", otherwise they are 100% pointless for the user since it's impossible for the user to know which is which.

That's an incredibly easy "paper cut" to fix.

---

### Post by yelo3 on 2009-06-28
I've just filed a bug (also to banshee)
[https://bugs.launchpad.net/bugs/393115](https://bugs.launchpad.net/bugs/393115)
[https://bugs.launchpad.net/bugs/393106](https://bugs.launchpad.net/bugs/393106)

---

### Post by Yfrwlf on 2009-06-28
> **yelo3 said:**
> I've just filed a bug (also to banshee)
[https://bugs.launchpad.net/bugs/393115](https://bugs.launchpad.net/bugs/393115)
[https://bugs.launchpad.net/bugs/393106](https://bugs.launchpad.net/bugs/393106)

Yay! ^^  Thnx

---

### Post by chrisccoulson on 2009-06-28
> **Yfrwlf said:**
> Then obviously they should have renamed the entries that show up in "Open With", otherwise they are 100% pointless for the user since it's impossible for the user to know which is which.

That's an incredibly easy "paper cut" to fix.

This is already a well known issue, and it isn't as simple to fix as you suggest. The issue is that the desktop files are used for mimetype handling. Because you might want to launch an application with different options depending on the mimetype, this dictates that you have multiple desktop entries with different mimetypes, different execute options, but the same name.

Generally, only one of these desktop files will be shown under the Nautilus "Open With->" sub-menu (accessed from the context menu), depending on the mimetype. If you had a different name for each desktop file for the different mimetypes, then the names under "Open With->" would always be different depending on the type of file you clicked on, and that would be *even more* hideous for every day use.

---

### Post by Yfrwlf on 2009-06-28
> **chrisccoulson said:**
> This is already a well known issue, and it isn't as simple to fix as you suggest. The issue is that the desktop files are used for mimetype handling. Because you might want to launch an application with different options depending on the mimetype, this dictates that you have multiple desktop entries with different mimetypes, different execute options, but the same name.

Generally, only one of these desktop files will be shown under the Nautilus "Open With->" sub-menu (accessed from the context menu), depending on the mimetype. If you had a different name for each desktop file for the different mimetypes, then the names under "Open With->" would always be different depending on the type of file you clicked on, and that would be *even more* hideous for every day use.

I see.  Clearly then the .desktop file standard or Nautilus (or both) need to be made more intelligent to compensate for this very simple problem.

Perhaps there needs to be two different systems, one for known and the other for unknown types.  Or, you simply add an extra line to the .desktop file standard which gives a detail about that specific .desktop file.  Then, when dealing with "known" files, you disregard the detailed metadata line, but when browsing for programs for unknown mimetypes, you state the "detailed info" line so that users will see the difference between them.  I'd say in that case you should implement my above idea with having those programs that have multiple startup options be in expandable menus (with the arrows to expand them).  The final option would be to simply show users the "base" option for programs while browsing for programs to use with unknown mimetypes, and get rid of all the specific custom option entries, but I like the previous idea better.

All problems have solutions, and I don't think this one would be that difficult to deal with to improve GNU/Linux.

---

### Post by yelo3 on 2009-06-28
Well, it's a papercut as long as you can append a description near the name, such as:
Brasero Burner (open as disc image)
Brasero Burner (open as multimedia playlist)
Brasero Burner (open as brasero project)

---

### Post by Yfrwlf on 2009-07-02
> **yelo3 said:**
> Well, it's a papercut as long as you can append a description near the name, such as:
Brasero Burner (open as disc image)
Brasero Burner (open as multimedia playlist)
Brasero Burner (open as brasero project)

Agreed, and that's one way to fix it, tho I don't think it's the most awesome solution that could be thought up, but a temporary patch at least.

---

