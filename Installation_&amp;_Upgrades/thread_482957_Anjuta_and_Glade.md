---
title: "Anjuta and Glade"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Deichgraf on 2007-06-24
Hi,

I installed Anjuta 1.2.4a and Glade 2.12.1 by selecting these applications from menu Applications -> Add/Delete. 
When I tried to establish my first project under Anjuta with Glade support I run into a number of errors which I could reduce by performing the following actions:

sudo apt-get install anjuta build-essential autoconf libtool 
sudo aptitude install libglib2.0-dev libgtk2.0-dev

After that there remained some errors which prevent the creation of the project:

No package 'libgnomeui-2.0' found
No package  'libglade-2.0' found

I tried something to install the missing packages but without success.

Any suggestions are wellcome!!

With best regards

Christian

---

