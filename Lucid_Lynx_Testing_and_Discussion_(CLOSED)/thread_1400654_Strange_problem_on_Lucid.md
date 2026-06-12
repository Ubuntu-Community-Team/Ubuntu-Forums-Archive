---
title: "Strange problem on Lucid"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2010-02-07
Problem: I see no users in my GDM login screen or under 'Users and Groups' (apart from root)

Situation:
I had installed Karmic on an HP HPG61110SA laptop(Intel T4300, 4Gb RAM) alongside the W7 it came with.

I used update-manager -d to go to Lucid.

All worked. I then decided to synchronize the clock to time servers. During this I (obviously) had to install NTP. During the install (or immediately after - I can't remember which) the machine switched off completely - no logoff messages, no nothing just straight to black screen, no lights.

On rebooting I had normal GDM with users listed but whenever I selected my user and entered the password the machine would freeze - still on the GDM screen, immediately after pressing enter in the password field. No mouse/touchpad response, no keyboard response.

After a couple of iterations of that I tried the other user I had set up (fortunately!) which worked. Hooray

Next boot, GDM has lost all users, but you can still login by clicking the login button, entering username and then password.

To investigate this I went to system>admin>users and groups. The only user which shows there is root. If I try to add another users it prompts for the current user password, allows entry of name, allows entry of password, but then no new user appears in the list after the new user dialog finishes.

Using 'sudo adduser test' I got
adding user 'test' ....
adding new group 'test' (1003) ....
and some more stuff then a prompt to Enter new UNIX password:

done that and machine has just frozen again

Any clues?

Sorry for the less than crystal clear post - things are changing on a 'per boot' basis at the moment!

Last I looked I had the original two users' folders in /home,
and when I tried to add a user from command line yesterday I got a complaint about userid 1002 not being unique (makes sense)

Any one interested in seeing if we can figure this out or shall I just do a clean reinstall - I don't use the Ubuntu on the lappy for anything important / haven't got any data on it?

---

### Post by ubername on 2010-02-07
Weird!

I was rebooting the lappy when I submitted the post above.

Now GDM show the original two users again (hooray!) I can login as my 'proper' user again, and I see the two users ('default' and 'test') which I set up in trouble shooting this. However system>admin>users and groups still just shows 'root'. I will reboot again to let you know what happens next (I bet you are on the edges of your seats, huh?)

---

