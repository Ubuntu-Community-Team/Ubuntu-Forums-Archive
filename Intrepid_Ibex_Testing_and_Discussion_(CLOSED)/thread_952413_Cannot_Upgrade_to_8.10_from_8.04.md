---
title: "Cannot Upgrade to 8.10 from 8.04"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Hangwire on 2008-10-19
Hi all.
Well, i have read a lot about the new 8.10 and i want to install it, although this way [http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-804-hardy-heron-to-ubuntu-810-intrepid-ibex-beta.html) Doesnt work for me. I tried everything, messed around with the software sources options, but still it downloads some 69 Updates (doesnt install anything) and it tells me that my system is up-to-date. 
Please help me. Also, I have another problem. 

> Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Does this have anything to do with me not being able to upgrade to 8.10? 
I fix the above when i disable the CD from software sources but i thought it had something to do with the upgrade problem... 

Any help will be appreciated.

---

### Post by Pumalite on 2008-10-19
To upgrade; you first have to have your OS fully updated; 2nd, remove all third parties from /etc/apt/sources.list
If you want to upgrade with a CD; you need the Alternate CD.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Hangwire on 2008-10-19
I have my OS fully updated. Atleast thats what the update manager says...
What do you mean to remove all third parties, please explain :]

---

### Post by overdrank on 2008-10-19
Moved to  Intrepid Ibex Testing and Discussion :)

---

### Post by sethvath on 2008-10-19
> **Hangwire said:**
> I have my OS fully updated. Atleast thats what the update manager says...
What do you mean to remove all third parties, please explain :]


Goto SYSTEM>ADMINISTRATION>SOFTWARE SOURCES

Under the third-party software tab, uncheck everything. including the one with cdrom

---

### Post by ronacc on 2008-10-19
that method should work if you followed the instructions correctly . did the term say anything that might indicate why it failed ?

---

### Post by Hangwire on 2008-10-19
Thanks for moving.

@ronacc

nothing actually failed, it just checked for updates and showed that it didnt have any available. or do you mean the second problem? Nope, just that which i have pasted.

@sethvath

Thank you, i will try that now.

---

### Post by Hangwire on 2008-10-19
Nope... didnt work. Again, downloaded some files, refreshed the list, read package info, and no updates available what so ever. I unchecked the three under third party thing.

---

### Post by Hangwire on 2008-10-19
bump. 
come on people, its a serious issue.

---

### Post by ronacc on 2008-10-19
the method described by ubuntugeek is the method officialy recomended by ubuntu , see here [http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04](http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04)   and here  [http://ubuntuforums.org/showthread.php?t=936696](http://ubuntuforums.org/showthread.php?t=936696)   . So if it isn't working file a bug giving as much info as you can . With that said if you are in a hurry and are willing to destroy your system , maim your children and kill your dog you can try the method I use . edit your /etc/apt/sources.list  change ALL instances of hardy to intrepid (including 3rd party if you want ) then from term "sudo apt-get update" then "sudo apt-get dist-upgrade " (without the quotes) . this is no longer the recomended method and really could destroy your hardy install but "should" work .

---

### Post by Hangwire on 2008-10-19
*chills*

File a bug? Show me where, i would be happy to. :)

Eeeh... yeah, im willing to try that. Will come back with a result soon. :D

---

### Post by ronacc on 2008-10-19
report your bugs here  [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)  and don't expect to be back too soon ,it takes longer than a fresh install from cd , go plant a garden or something while its chugging away :lolflag:

---

### Post by GavinZac on 2008-10-19
The method in your original post should work. Don't forget the " -d" at the end.

---

### Post by Hangwire on 2008-10-19
I think im going to wait 11 more days until the official release of 8.10

update-manager with -d or without -d  - doesnt matter. it still doesnt work.

---

### Post by ronacc on 2008-10-19
probably a good choice . however you should still file a bug on launchpad if its broke it needs to be fixed .

---

### Post by Hangwire on 2008-10-19
Yup, did that.
Thank you for the information and support all.

---

### Post by themooncat on 2008-10-21
Hi All

I had the same problem where the dist-upgrade did not show as available all I did to fix this problem is run the update manager as sudo.

To upgrade from Ubuntu 8.04, press Alt+F2 and type in "sudo update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by linux6994 on 2008-10-21
I have upgraded several PCs and Laptops using "update-manager -d" from alt-f2.

---

