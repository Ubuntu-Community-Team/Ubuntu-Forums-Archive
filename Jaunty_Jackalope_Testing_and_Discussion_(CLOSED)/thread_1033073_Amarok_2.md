---
title: "Amarok 2"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Progressive on 2009-01-07
When will Amarok 2 be coming to Jaunty? Or are we waiting for 2.1?

---

### Post by Quadchris on 2009-01-07
Hi,

If you want to use Amarok 2 use the package amarok-kde4 which is the right version.

Bye

---

### Post by Kobalt on 2009-01-07
Is MySQL 5.1 in the Jaunty repos yet? 'Cause Amarok 2 is depending on it, and it's the reason it was not inclunded in Alpha2.

---

### Post by Progressive on 2009-01-07
Mysql is 5.0.75 for me.

---

### Post by Quadchris on 2009-01-07
I'm using this line for getting amarok 2.0

deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) intrepid main

It works for me.

It's an embedded mylsq library which is needed by amarok 2 for it's backend database. The repository contains the necessary depends.

Bye

---

### Post by Progressive on 2009-01-12
The repos were updated with the new 2.0.1.1

Everything is working great... got OpenOffice.org 3 to boot

---

### Post by Vorian on 2009-01-12
I just uploaded a new revision - until it clears, you will need to install mysql-server-5.1 to avoid any errors (perl and kdebase-workspace-dev are also required)

---

