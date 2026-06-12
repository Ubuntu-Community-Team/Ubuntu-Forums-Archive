---
title: "[SOLVED] problem with libxine1"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by el_guazu on 2008-02-28
My first post...

I dont have Internet in the house... So to install software i cant use the apt-get install _name_, instead i use to go to rent Internet and download the program, with every single dependence for it.

The problem is that I want to install xine, but it depends on libxine1, and libxine1 depends on libxine1!!!

I dont know if is a bug, or something, but i think that is a problem if a package depends on himself to install...

THKS!

---

### Post by zvacet on 2008-02-28
If you don´t have internet use [nonetdebs.](http://nonetdebs.homeip.net/)

---

### Post by el_guazu on 2008-02-28
First answer in less than half an hour...

Great answer... I didn´t knew that existed...

THKS zvacet!

...
wait a minute... I dont like step 19 in the mini howto...

19. Click on the links and download the package you want and ** all its dependencies ** you still don't have installed on the target and a little script to install all the packages.

it means that still i have to download those dependences that i dont have?

---

### Post by zvacet on 2008-02-29
> it means that still i have to download those dependences that i dont have?

Yes,because without them program will not work.But that is a good thing about nonetdebs.With it you will download program and dependencies in one place.Easyer then download same thing from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by el_guazu on 2008-02-29
So it has the advantage to tell you what do you have to download,
and it puts all the links to download in the same page...

OK that's enough for me... THKS zvacet!

______

Just one more thing...

I´ve tried to install libxine1 with the double click process, and it throw me the self dependence that I said...
but if i install libxine1 with dpkg -i libxine1.deb it throws no problems... 

can anyone explain why?

---

