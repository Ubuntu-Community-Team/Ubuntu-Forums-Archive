---
title: "evolution and gnome-do questions"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2009-04-08
it would seem jaunty broke my evolution "back-end process" and did some "funny" stuff to gnome-do.

evolution will connect, download messages for offline view, and seem to function perfectly until i notice the yield sign in the bottom-left; apparently the backend process always fails in the new version. is anyone else getting the same error?

gnome-do works, but with a twist now. if i'm just on an empty desktop, gnome-do works fine with my keyboard shortcut (in my case, ctrl+space); however, if i'm on the window of *any* program (even those with no keyboard shortcuts), it takes *exactly* three ctrl+space hits to bring-up gnome-do... weird. any ideas on that one, too?

---

### Post by go7Ul1ai on 2009-04-08
> **moore.bryan said:**
> it would seem jaunty broke my evolution "back-end process" and did some "funny" stuff to gnome-do.

evolution will connect, download messages for offline view, and seem to function perfectly until i notice the yield sign in the bottom-left; apparently the backend process always fails in the new version. is anyone else getting the same error?

gnome-do works, but with a twist now. if i'm just on an empty desktop, gnome-do works fine with my keyboard shortcut (in my case, ctrl+space); however, if i'm on the window of *any* program (even those with no keyboard shortcuts), it takes *exactly* three ctrl+space hits to bring-up gnome-do... weird. any ideas on that one, too?

If you are using Compiz, go to the settings manager. On general settings, put "focusing" to off and it should work, I created a topic on this a few days ago..

Lee

---

### Post by moore.bryan on 2009-04-08
thanks, lee; that seems to have solved my gnome-do issues. any clues about evo?
;-)

---

### Post by Aenima99x on 2009-04-08
> **moore.bryan said:**
> it would seem jaunty broke my evolution "back-end process" and did some "funny" stuff to gnome-do.

evolution will connect, download messages for offline view, and seem to function perfectly until i notice the yield sign in the bottom-left; apparently the backend process always fails in the new version. is anyone else getting the same error?
Yes, I'm having the exact same problem. It's really annoying to have to close/re-open evolution several times a day when I'm working. I'm hoping the Exchnage MAPI functionality gets fixed also.

---

### Post by moore.bryan on 2009-04-08
it would seem many are having the same problem, aenima99x; do you have any idea how to check if the exchange server has mapi enabled in the first-place without asking the it department?

---

### Post by Aenima99x on 2009-04-08
> **moore.bryan said:**
> it would seem many are having the same problem, aenima99x; do you have any idea how to check if the exchange server has mapi enabled in the first-place without asking the it department?

Hahaha I am the IT dept. ;)
I'm not really much of an Exchange guy, but I'm fairly confident that if you have OWA, then your Exchange server is setup for MAPI. I'm pretty sure OWA uses MAPI over RPC.

---

### Post by moore.bryan on 2009-04-08
> **Aenima99x said:**
> Hahaha I am the IT dept. ;)
I'm not really much of an Exchange guy, but I'm fairly confident that if you have OWA, then your Exchange server is setup for MAPI. I'm pretty sure OWA uses MAPI over RPC.
that *is* funny... my it guys are "less-than-happy" with my ubuntu-ing, so the less i ask, the better. it is owa, so i can assume mapi is good. i haven't seen many able to use the evolution-mapi connection; any insight as to why?

---

### Post by Aenima99x on 2009-04-08
I had been having the issue that most other people had  - when trying to setup MAPI, evolution would completely crap out when you tried to do the authentication portion during the acct. setup wizard. I just tried it again right now and I DID get it working *somewhat*. (It's pulling my folders, but has dropped the connection a couple times).


Here's how I got it to work -
1. Launch the wizard to add a new email acct.
2. Receiving email - in the server type, leave it at none 
3. Sending email - leave server type as SMTP and put in anything as the server (I just put in 1)
4. Finish the wizard and close evolution
5. Re-open evolution and go back and edit the acct. you just created
6. In the receiving email tab - set your correct server name, username and domain - DO NOT HIT AUTHENTICATE
7. Receiving options tab - enter your Global catalog server name if you know it
8. restart evolution and see if it works for you

---

### Post by Aenima99x on 2009-04-08
Ughhh....looks like I spoke to soon. It's pulling my folders, but gets stuck scanning them and retrieving messages. Guess it's back to the OWA method for now.

---

### Post by moore.bryan on 2009-04-08
that seems to be what happens to most people. i have no problem with using the owa method for now, i just wanted to try and understand why it would sometimes work and sometimes not on the new evo.

---

