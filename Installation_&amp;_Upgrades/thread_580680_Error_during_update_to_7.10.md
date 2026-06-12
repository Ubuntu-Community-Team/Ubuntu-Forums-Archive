---
title: "Error during update to 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by angelsneverdie on 2007-10-19
alright, i go to the update manager and tell it to do a distribution update.  everything went fine until I got past the sources part and it told me how long it would take - i had to go to class and needed my laptop for class so i told it to cancel.  

now that i have time, i try to do the update and it always stops eventually in the first step and gives me this message (see screenshot)  it won't let me copy the text of the message or make the window bigger, so sorry for the limited info.  anyone have any ideas other than downloading a live cd and updating from that?

[IMG]http://i3.photobucket.com/albums/y96/dystopias/Screenshot-gutsy.png[/IMG]

I should also add that this has happened three times now, and I am sure that it is not actually a network problem.


working now . . . fifth time's a charm

---

### Post by Arrdee on 2007-10-19
> **angelsneverdie said:**
> alright, i go to the update manager and tell it to do a distribution update.  everything went fine until I got past the sources part and it told me how long it would take - i had to go to class and needed my laptop for class so i told it to cancel.  

now that i have time, i try to do the update and it always stops eventually in the first step and gives me this message (see screenshot)  it won't let me copy the text of the message or make the window bigger, so sorry for the limited info.  anyone have any ideas other than downloading a live cd and updating from that?

[IMG]http://i3.photobucket.com/albums/y96/dystopias/Screenshot-gutsy.png[/IMG]

I should also add that this has happened three times now, and I am sure that it is not actually a network problem.

Comment/deselect/remove those links from your sources.list. Edit the file directly or go to System > Administration > Software Sources, then to Third Party Sources and uncheck those causing the problem.

---

