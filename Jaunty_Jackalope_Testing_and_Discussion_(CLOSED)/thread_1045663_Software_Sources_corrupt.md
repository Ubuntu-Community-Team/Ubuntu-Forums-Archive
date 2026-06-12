---
title: "Software Sources corrupt?"
date: 2009-01-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-01-20
Is anybody elses Software Sources list broken?
I just checked mine and i had a crap load of stuff in there which were all checked. When i unchecked them it just removed them. All the stuff under the 'Ubuntu Software' tab like Main, Universe, Restricted and Multiverse are now also unchecked and i can't recheck them?

---

### Post by Foaming Draught on 2009-01-20
Trying to look at Repositories under Settings in Synaptic returns the "The repository information has changed" message without showing any repos, and then update-apt crashes.  /etc/apt/sources.lst appears to be empty, but exiting gedit asks if I want to save changes which I haven't made.

---

### Post by MacUntu on 2009-01-20
Confirming. 

Source entries are now under "Settings > Repositories > Third-Party Software" in Synaptic.

---

### Post by Slug71 on 2009-01-20
Have filed a bug at Launchpad.
Please add to it if you encounter any such problems.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/319408](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/319408)

---

### Post by cariboo on 2009-01-21
I tried  Software Sources, it crashed, the crash reporting appliction still doesn't work. I Tried to get to the sources list in Synaptic, it gives me the message that the repositories have changed and to click the reload button. Running:

```
cat /etc/apt/sources.list
```

works, and opening /etc/apt/sources.list in nano works too.

Jim

---

### Post by Slug71 on 2009-01-21
An update just came through for python-apt which i think may have fixed this. All the stuff under the 'Ubuntu Software' tab in Software Sources is now checked. Not sure if they are all suppose to be?
The update also cleared my Sources list under the 'Third-Party Software' tab though which is no biggy.




Update: So i guess its not fixed. Cant add Sources to the empty list. You can now check and uncheck the stuff on the first  tab though.

---

### Post by Slug71 on 2009-01-22
Got more python-apt and Update Manager updates, restarted and tried to check for more updates and i get this:

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 68 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

The Update icon in the top right of the panel shows that there is updates though.

Terminal output of:
```
sudo apt-get update
```

gives me
> 
E:Malformed line 68 in source list /etc/apt/sources.list (dist parse)

???

---

