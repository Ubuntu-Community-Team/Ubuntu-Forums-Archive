---
title: "admin menu missing items after upgrade to Dapper"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by concord on 2006-08-04
All my menu items were present in Breezy like the link to synaptic, etc...

Since upgrading to Dapper almost all options are missing.  I found a thread that talked about being able to get them back by adding my user to the root group but I don't really want to do that.  Is there any way to get them all back without doing this?

See the attached picture for a look at my anemic admin menu (no USERS, SYNAPTIC, etc ...)

Any help would be appreciated.

[IMG]http://concordsystems.net/admin_menu.jpg[/IMG]

---

### Post by ESPOiG on 2006-08-04
u did try alacatre or wateva (menu editor) didnt you... for just showing them...

if not...

---

### Post by Healey on 2006-08-04
Hi

I am NOT an expert but I had a similar problem that I solved with this

sudo adduser "your name" admin

Please Please do some research first because I am not sure if it does other things as well

Check First

It may be worth searching and finding out about the above command

Good luck

Healey

---

### Post by concord on 2006-08-13
Your suggestion worked fine although I actually added my user with the gui tool (Users and Groups) instead.  Once I did that things started to show up that weren't available previously.  

You have to leave the user in the admin group otherwise the options just disappear again.

Works great!

---

### Post by Healey on 2006-08-14
Hi

I am pleased you got it working

Best Regards

Healey

---

