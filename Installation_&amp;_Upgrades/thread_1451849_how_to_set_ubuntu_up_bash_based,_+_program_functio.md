---
title: "how to set ubuntu up bash based, + program functionality?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by Søren on 2010-04-11
Hey all,

My project is to set my ubuntu up as a command prompt based system. I want to accomplish my tasks via the prompt and emacs. So is installed ubuntu server. This worked well except i need windowing to work for a few programs, like gedit, pidgin and a couple of others. My ubuntu server wouldnt let me use any of this stuff, so I installed gnome and ubuntu desktop. Now i am back to the whole kitchen sink. 

So. what do i have to uninstall to get to where i want to be?
Or if its easier what do i install after a fresh install of ubuntu server to get it happening?

BASICALLY JUST NEED BASH + ABLE TO RUN PIDGIN AND FIREFOX :d

also on a bash operated system, how to i open multiple tabs like you can in gnome terminal? its just a huge black screen ... I want to customise in and give it functionality like gnome terminal..

thanks :p

---

### Post by Søren on 2010-04-11
ok im researching im on my own a little bit. 

as a plan i thought i might:

1) install ubuntu server
2) install x11 windowing system

would this do it?

(i also considered changing the default runlevels in ubuntu etc but is seems like come pretty scary editing config files)

---

### Post by tom4everitt on 2010-04-11
If I understand it correctly, x11 only provides core functionally when it comes to graphics. I.e drawing lines, colored areas etc. 

Most graphical applications depends on gnome, or at least the gtk+ graphics tool kit, including bars of windows, buttons, etc. 

So I think you will need gnome (which basically is ubuntu-desktop), to have gedit, firefox etc (I could be wrong). 


To have several "tabs" in a bash system like that, you want to look into the 'screen' command. Its very useful.

---

### Post by Søren on 2010-04-11
ok thanks. i dont mind having gnome installed but i dont want to be in desktop mode by default.

ideally i'd like to be in terminal mode all the time and be able to call windows from bash only when necessary to use special programs. hopefully never have to use desktop.

 i have worked out i can use use chat through command line through finch and internet access through emacs. so that solves that.

---

### Post by oldos2er on 2010-04-11
Lxde is much lighter on resources than gnome. [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

---

### Post by Søren on 2010-04-13
cheers. i ended up just setting my desktop to pure black to give it a semblance of non existence. i then set my terminal to run on start up. this gives me the aesthetic feel that i want, however knowing that the desktop is there is still gnawing at my soul.

---

