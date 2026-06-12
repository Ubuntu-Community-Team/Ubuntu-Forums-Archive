---
title: "Brl-cad"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by hansg1975 on 2010-04-18
Dear :-)

I am a new Ubuntu 9.1 User and tried to install BRL-CAD:
[http://brlcad.org/wiki/Building_from_SVN](http://brlcad.org/wiki/Building_from_SVN)

Unfortunately BRL-CAD does not start after installation.
Can you help?

I added the console-output to this thread.

Thank you for your help
Hans

---

### Post by bigseb on 2010-04-19
How did you install? I followed the installation instructions from this link: [http://openae.org/download-brl-cad](http://openae.org/download-brl-cad)

To start BRL-CAD I type: /usr/brlcad/bin/mged

Hope this helps.

---

### Post by hansg1975 on 2010-04-19
Thank you very much for you answer. It is nice to hear that brlcad is working on ubuntu. Would be nice to know what you are doing on brlcad :-) Just write me a message.

I tried the steps taken from brlcad.org. (I added the link above.) - did not work out.

Now, I tried the steps from
[http://openae.org/download-brl-cad](http://openae.org/download-brl-cad)
, too.

And yes, i downloaded *brlcad_7.10.4_ia32.tar.bz2 and* unarchived it.
After that I moved the folder to /usr/BRLCAD and tried to start mged. Did not work out :-/ The file mged is in the folder but i could not start it?

I added the text from the console to my response.
[FONT=System][/FONT] 	 	 	 	 	  [FONT=System]*No command 'mged' found, did you mean:  *[/FONT]
 [FONT=System]* Command 'mred' from package 'plt-scheme' (universe)  *[/FONT]
 [FONT=System]* Command 'mped' from package 'mped' (universe)  *[/FONT]
 [FONT=System]*mged: command not found*[/FONT]
 [FONT=System][/FONT]May be you have an answer?

Thank you
Hans

---

### Post by bigseb on 2010-04-19
Not so fast... I only installed it on Friday (3 days ago!) so I'm still getting to grips with it. As a toolmaker I intend to use it for product and mold design. I have always used Solidworks and Rhinoceros for my design work but two months ago I switched to Linux so I have to make many changes. BRL-CAD, though very different to what I'm used to, seems to be more than capable in this regard. I must now just figure out how to export my .g models in .igs... after that its easy peasy japanesey :) 

I don't know why your installation isn't working. I am not well-versed in Linux, as I said above it's only been 2 months. Perhaps it would worthwhile to sit down with a Linux expert for a while...

You may want to see here: [http://sourceforge.net/projects/brlcad/forums](http://sourceforge.net/projects/brlcad/forums) ;)

---

### Post by brlcad on 2010-04-19
> **hansg1975 said:**
> Thank you very much for you answer. It is nice to hear that brlcad is working on ubuntu. Would be nice to know what you are doing on brlcad :-) Just write me a message.

I tried the steps taken from brlcad.org. (I added the link above.) - did not work out.

Now, I tried the steps from
[http://openae.org/download-brl-cad](http://openae.org/download-brl-cad)
, too.

And yes, i downloaded *brlcad_7.10.4_ia32.tar.bz2 and* unarchived it.
After that I moved the folder to /usr/BRLCAD and tried to start mged. Did not work out :-/ The file mged is in the folder but i could not start it?

I added the text from the console to my response.
[FONT=System][/FONT] 	 	 	 	 	  [FONT=System]*No command 'mged' found, did you mean:  *[/FONT]
 [FONT=System]* Command 'mred' from package 'plt-scheme' (universe)  *[/FONT]
 [FONT=System]* Command 'mped' from package 'mped' (universe)  *[/FONT]
 [FONT=System]*mged: command not found*[/FONT]
 [FONT=System][/FONT]May be you have an answer?

Thank you
Hans

Hans,

I replied to your other .de thread, but since you've gone a different route here with the binary package installation, a few notes:

1) the installations expect to be put into */usr/brlcad* not */usr/BRLCAD*

2) I suggest some basic Linux PATH tutorials as it looks like you just aren't setting your PATH correctly.  You needed to either run ''/usr/BRLCAD/bin/mged'' or ''./mged'' from within the /usr/BRLCAD directory, or (ideally) add ''/usr/BRLCAD/bin'' to your path so that ''mged'' will work.  See point #1, though, in that BRL-CAD should be installed into /usr/brlcad so the path will need to match the directory.

Cheers!
Sean

---

### Post by hansg1975 on 2010-04-20
Thank you both for your replies.

I did the steps from
[http://openae.org/download-brl-cad](http://openae.org/download-brl-cad)
again.

When I type in the following:

ubuntu@ubuntu-laptop:/usr/brlcad/bin$ **./mged**
Initializing and backgrounding, please wait...Done

The program starts. :-)

So hopefully I will have a nice time in 3d-modeling.
Hope to hear from you soon.

Cheers
Hans

---

### Post by bigseb on 2010-04-21
Great stuff! Enjoy!

---

