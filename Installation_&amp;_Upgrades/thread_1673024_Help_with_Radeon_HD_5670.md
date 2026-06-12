---
title: "Help with Radeon HD 5670"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by Ckesey on 2011-01-21
I just recieved my new PC. While installing 10.10 i'm having some issue enabling visual effects. When I try anything but "None" I get an error that says "Desktop effects can not be enabled". 

When I try to run compiz from the terminal I get:

compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager



Also when I try to edit the xorg.conf file it's not there.....is this normal???

What can I do to enable effects with my Radeon HD 5670????

Thanks for any suggestions......

---

### Post by gordintoronto on 2011-01-21
Did you run Administration/Additional Drivers?

It's normal to have no xorg.conf file, but if you create one it will be used.

---

### Post by Ckesey on 2011-01-22
When I go to system>additional drivers I don't have anything listed there (as I once did). The list is empty.

Just after the install I remember this window coming up with the ATI driver listed and I clicked enabled....should it still be listed here???

---

### Post by Ckesey on 2011-01-22
I went to synapics package manager and installed several things realated to ATI graphic card.

Now when i got to additional drivers I see "ATI fire GL" which says below it's for ATI Radeon graphic accelerators. 

I still get an error when trying to active effects. 

Am I still missing something somewhere?

---

### Post by Claus7 on 2011-01-22
Hello,

this:
[http://ubuntuforums.org/showthread.php?t=1419962](http://ubuntuforums.org/showthread.php?t=1419962)

is supposed to solve all your problems...

Regards!

---

### Post by Ckesey on 2011-01-22
I guess your refering to the #13 post......I'll try this and let you know.

Thanks for all your comments so far!!!

---

### Post by Claus7 on 2011-01-22
Hello,

I should say from post #12 till 15, which (the latter) holds a tested xorg.conf that seems to do the trick. The others show (and clear) some things necessary before that.

Hope it will help you too,
Regards!

---

### Post by Ckesey on 2011-01-24
Unfortunately mine experience wasn't the same as yours.

Here is what I can gather so far.....

When I issue the perl command to check driver in use I get this:

Using driver radeon v6.13.1 by X.Org Foundation.
Using driver vesa v2.3.0 by X.Org Foundation.

When I copied and paste your xorg.conf file and crate my own with it I failed to start x (will get error message soon). 

Also when issue the "fglrxinfo" i get command not found. Does this mean that fglrtx isn't installed??? When I looked in Synapic I have all the ones you listed installed myself.

---

### Post by Ckesey on 2011-01-24
I uninstalled everything related to fglrx and reinstalled it.

Now I have the fglrxinfo at the command line but get this output:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

I'm doing several google searches for help on this error as well.......

Thanks

---

### Post by Ckesey on 2011-01-24
I finally got it.....Basically I did exactly what you recommended but  for some reason I had to reinstalled the packaged again after I removed  what you said needed to removed.

Thanks for the help on this.

**Kudos to Claus7!!!!!**

---

### Post by Claus7 on 2011-01-24
Hello,

you are very very welcome! Happy ubuntuing.. at least the time it took me in order to find out what was going on, seems to be some kind of help for others.

Regards!

---

