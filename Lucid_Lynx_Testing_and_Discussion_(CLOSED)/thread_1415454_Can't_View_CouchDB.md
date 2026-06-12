---
title: "Can't View CouchDB"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by skierkyles on 2010-02-24
When I try to access my couchDB in Lucid, I get greeted by a prompt asking for my username and password, and It wont accept my username and password :confused:

In Karmic, I went to: 
file:///home/<your username>/.local/share/desktop-couch/couchdb.html

and then clicked on the link and it didn't ask me for anymore information.. So did something change that I'm not aware of?

Thanks Kyle

---

### Post by skierkyles on 2010-02-26
Anyone please :(

Im pretty sure that the password is in your gnome key ring under Desktop Couch User Authentication, it seems to be just a bunch of random numbers.. 

But I still can't figure out what username to use, Ive tried Localhost, my username, administrator, all with no luck.

---

### Post by CoolGoose on 2010-02-27
Same issue here.

/le
Managed to "fix" this
In gnome-keyring select Desktop couch user authentication -> click the plus from the password -> check show password

The text before the : is your username, the text after is your password.
Ta-da! it WORKS!

---

