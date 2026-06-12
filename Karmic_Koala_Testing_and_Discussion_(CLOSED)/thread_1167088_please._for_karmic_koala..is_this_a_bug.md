---
title: "please. for karmic koala..is this a bug??"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by drjackal on 2009-05-22
i cant seem to unlock the user account from the system > administrator>users and groups panel.

another user also found it not to be working. please check all ye testers.

---

### Post by super.rad on 2009-05-22
Working fine for me

---

### Post by davideotape on 2009-05-22
> **super.rad said:**
> working fine for me

+1 ):p

---

### Post by drjackal on 2009-05-22
then please help me :)

---

### Post by davideotape on 2009-05-22
do you get to the authorization screen where you can input your password or not?

---

### Post by drjackal on 2009-05-22
sorry wasnt online..power cut due to loadshedding....


well no..the panels requesting my username or password dont come up... that has been my problem..and well now i am facing another problem... i cant seem to be able to add another user using

adduser loginname admin 

in the recovery mode!!!!

---

### Post by drjackal on 2009-05-22
my original login name is failing too!!! i cant even log onto my desktop any longer!!!


okay update- i changed my password and accessed the terminal

---

### Post by drjackal on 2009-05-22
okay i think we have a small teeny tinsy little bug.

when once u create a new user and add it to admin and then change sessions midway as if you were logging out and changing the user..welll

this came up :

/home/loginname could not be created..

*some error panel drop down that was simply too fast!* remember seeing X server somewhere though.

finally

"could not update ICEAuthority file /.ICEauthority

"there is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

---

### Post by ranch hand on 2009-05-24
That was interesting.  I just tried this on mine.

Was told that it could not be opened.  Clicked OK  and it closed.  Tried it again and the normal box came up, gave password, clicked on main account -> properties -> privilages and added one.  Closed normally.

---

### Post by inportb on 2009-05-24
There seemed to be a problem with getting root access. It might help to run systemsettings via kdesudo.

---

### Post by drjackal on 2009-05-26
i think that is exactly the problem...in the gnome mode i cannot unlock anything..but in the terminal i can be root..using sudo -i

but i still think it has to do with root access..please help me!

i reinstalled kk...and well :) it is still there!! all i can think is ..i'll download it again and then try it out!

otherwise please help!!

---

### Post by inportb on 2009-05-26
Well, it seems to follow naturally that you should do your root configuration with root access ;)
This might warrant a bug report if there isn't one already.

---

### Post by drjackal on 2009-05-26
thanks! i will try out the new things i learnt from the two threads.
will post a new thread as soon as i am ready.. :)

---

