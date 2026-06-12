---
title: "Problem with software installtion"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by Dooq on 2006-06-08
I cannot install anything in my new KUBUNTO os
WHEN I TRY to install firefox that what happen:
```

user@user-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
user@user-laptop:~$ sudo aptitude install mozilla-thunderbird firefox
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for mozilla-thunderbird
No candidate version found for firefox
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Whay the softoware didnt install ?
when try to install PHP :
```

user@user-laptop:~/Desktop$ sudo aptitude install php4
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "php4"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

any suggesting plz ? :confused:

---

### Post by taurus on 2006-06-08
Maybe you need to edit your /etc/apt/sources.list and remove the #'s for all the universe & multiverse...

And by the way, it's mozilla-firefox.

---

### Post by Dooq on 2006-06-09
Thank you fir your help.
That's right.
All the link in the file /etc/apt/sources.list has (#) before it,but how can i fix that ?
I tried to Edit it using Pico command but when i try to save the file this message appres:
    [ Error writing /etc/apt/sources.list: Permission denied ]
How can i edit the file ?  :-k 
Regards,

---

### Post by Dooq on 2006-06-09
[QUOTE=Dooq]

All the link in the file /etc/apt/sources.list has (#) before it,but how can i fix that ?
I tried to Edit it using Pico command but when i try to save the file this message appres:
    [ Error writing /etc/apt/sources.list: Permission denied ]
How can i edit the file ?  :-k 
Regards,[/QUOTE]

:cry:  Any help ??

---

### Post by Dooq on 2006-06-09
Thank you again.
I find the answer here : [http://wiki.ubuntu.com](http://wiki.ubuntu.com)
I used ( sudu -i ) command to use root shel then i have the abilite to modifi every thing.

Regaeds

---

