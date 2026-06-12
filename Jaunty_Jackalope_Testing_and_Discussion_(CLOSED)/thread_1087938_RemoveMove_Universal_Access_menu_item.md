---
title: "Remove/Move Universal Access menu item"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-05
I'm guessing this was brought up before, and I'm pretty sure it was brought up in Intrepid development.

It is a waste of space having
applications->universal access->orca screen reader
all by itself. Move orca screen reader to accessories.
Universal access makes the menu wider, so with its removal it should waste less space as well.

I'm guessing this happens because it is gnomes default and has not been changed by ubuntu devs yet?

Yes I know it can be removed in
system->preferences->main menu
but it would make a much better default installation to remove the menu item.

Using alpha 5.
Hmm, it seems March 5 is user interface freeze. I really hope this happens.
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by forumache on 2009-03-05
This is known as a bug: [https://bugs.launchpad.net/ubuntu/+source/orca/+bug/288648](https://bugs.launchpad.net/ubuntu/+source/orca/+bug/288648)

I identified the solution. Please subscribe to the bug, to get developers attention.

---

### Post by andrewabc on 2009-03-19
Now with latest updates CD/DVD creator has a menu in
Applications &#9656; System Tools &#9656; CD/DVD Creator
Will that be moved as well?

---

### Post by rockin_goliath on 2009-03-19
> **andrewabc said:**
> Now with latest updates CD/DVD creator has a menu in
Applications &#9656; System Tools &#9656; CD/DVD Creator
Will that be moved as well?

I don't think so. That was a Gnome decision. Check out the [Gnome 2.26 Release Notes]("http://library.gnome.org/misc/release-notes/2.26/").

---

### Post by Mr. Picklesworth on 2009-03-19
I think they should just install more universal access stuff by default, like Dasher, Workrave and an on-screen keyboard. Everyone loves universal access :P

Otherwise, I agree it should be hidden, but it has to appear automatically when "Assistive technologies" is enabled in Preferences. (On which topic, why the heck is that menu still titled "universal access"?!)

---

### Post by andrewabc on 2009-03-27
I'm running the beta and the menus are still bad.

Applications->system tools->cd/dvd creator
This is not needed if 
applications->sound and video->brasero disc burner
is there.

Also
applications->universal access->orca screen reader

Waste of a menu.

These have to be fixed before final release.

---

### Post by chrisccoulson on 2009-03-27
> **andrewabc said:**
> I'm running the beta and the menus are still bad.

Applications->system tools->cd/dvd creator
This is not needed if 
applications->sound and video->brasero disc burner
is there.

That is for the people (like me) who like to open a Nautilus window, drag files in to it and hit burn (just like with nautilus-cd-burner), without having to create a new project in Brasero first. This menu entry used to be in Places, but that really doesn't make any sense.

And I don't think having a CD burning application in Sound & video makes any sense. Sound and video is the only thing I don't use Brasero for.

---

### Post by andrewabc on 2009-03-27
Fine but having a menu for a single item is stupid. Move them to other menus, or create a menu and put a bunch of related stuff under it.

---

### Post by tom56 on 2009-03-27
It's not for a single item. If you installed other assistive applications (for example an on screen keyboard), they would be there too. If you moved all of those to "accessories" that menu would be far too long (aside from the fact that those applications aren't accessories).

EDIT: Though I agree that if you haven't turned on assistive technologies it should hide those items.

---

### Post by andrewabc on 2009-03-27
> **tom56 said:**
> It's not for a single item. If you installed other assistive applications (for example an on screen keyboard), they would be there too. If you moved all of those to "accessories" that menu would be far too long (aside from the fact that those applications aren't accessories).

EDIT: Though I agree that if you haven't turned on assistive technologies it should hide those items.

True, as more programs are installed they will go into certain menus.
But for a default install it doesn't make sense to have one item under a menu. :/

---

### Post by tom56 on 2009-03-27
> **andrewabc said:**
> True, as more programs are installed they will go into certain menus.
But for a default install it doesn't make sense to have one item under a menu. :/

Why not if it's the only category it fits into? I understand what you mean - it looks like a waste of space. But you have to imagine that there may be a hundred other applications that go in that category, and that's where they'll go once they are installed. The way this works is that an application defines what category it wants to be put in, and the menu itself displays those categories if there is anything that wants to be put there. There's not really any other category this belongs to.

---

### Post by andrewabc on 2009-03-27
Ok.

Can we agree that there doesn't need to be 2 cd burning shortcuts under two different menus? Move one to the other menu. I would think that would be confusing to users wondering why there are two different programs to burn cds. One under sound and video, and the other under system tools.
Does sound and video brasero only burn sound and video, while the one under system tools only burns files?

---

### Post by tom56 on 2009-03-27
> **andrewabc said:**
> Ok.

Can we agree that there doesn't need to be 2 cd burning shortcuts under two different menus? Move one to the other menu. I would think that would be confusing to users wondering why there are two different programs to burn cds. One under sound and video, and the other under system tools.
Does sound and video brasero only burn sound and video, while the one under system tools only burns files?

Yeah, I agree that that's dumb. Would make much more sense for the one under system tools to be accessible in nautilus under File->Create CD

Certainly doesn't help that they have the same icon as well!

---

### Post by forumache on 2009-03-28
Orca in Universal Access is a bug: [https://bugs.launchpad.net/ubuntu/+source/orca/+bug/288648](https://bugs.launchpad.net/ubuntu/+source/orca/+bug/288648)

It is not a matter of opinion, the file describing the position of the items in the menu is wrong, it has a typo inside. See the bug.

It is not fixed because it did not get the developers attention. Developers don't read this forum, so your complains are missed.
If you want to do something about this, subscribe to the bug.
The most subscribed bugs get the developers attention.

Otherwise, do nothing, just complain, be sad, be ignored :)

P.S. Thanks all who subscribed (Andrew you are one). I subscribed too, but my user forum name is different from the one registered with Launchpad :)

---

### Post by tom56 on 2009-03-28
I've found the culprit file and am trying to write my first ever patch! :)

EDIT: Ok, patching a patch is way too confusing - hopefully a dev will take a look at the bug though

---

