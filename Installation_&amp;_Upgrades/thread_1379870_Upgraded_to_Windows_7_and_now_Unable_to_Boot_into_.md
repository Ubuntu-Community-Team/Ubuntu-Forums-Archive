---
title: "Upgraded to Windows 7 and now Unable to Boot into Ubuntu"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by kunks112 on 2010-01-12
I followed the guide as posted 2 times for an older version of Ubuntu (Hardy). I still cannot get my grub to load.

I have Ubuntu and W7 on seperate drives. When I upgraded a Vista drive to W7, it overwrote my mbr. Now I cannot seem to fix it.

Any more ideas?


Edit* When I change my bios drive to read off of the Ubuntu drive (as it was set before) I see my grub loader, however I get "Error 17:Cannot mount selected partition" For all three of my OS's

---

### Post by presence1960 on 2010-01-12
[s]Kunks112 why don't you start a thread of your own a post a link to it back here. It is hard enough sometimes to help the OP of a thread let alone multiple people with their own separate problems. We will be glad to help you so start your own thread so this one does not get confusing.[/s]

On your new thread do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Sef on 2010-01-13
> Kunks112 why don't you start a thread of your own a post a link to it back here. It is hard enough sometimes to help the OP of a thread let alone multiple people with their own separate problems. We will be glad to help you so start your own thread so this one does not get confusing.Next time, just report it and request that the post be moved to its own thread.

---

### Post by Merlijntje on 2010-01-13
I had the same problem.
Wubi in Windows 7.   After doing all the updates it went wrong en dit nog start again anymore.
It was installed in de D partition where it worked very well.
After the problem deinstalled and took away rest things that i could find.
Reïnstalled there in D.
It was not accepted.
Installed Wubi in C.
I had to do that 2 times before it was accepted and it works well now.

I accept only safty ufdates there now.

Just did all the updates in my Vista pc.  NO Problems there.

I hope that someone can do something with this information.
I am absolutely not a fan of Windows 7.

Kindest regards Merlijntje

---

### Post by presence1960 on 2010-01-13
> **Merlijntje said:**
> I had the same problem.
Wubi in Windows 7.   After doing all the updates it went wrong en dit nog start again anymore.
It was installed in de D partition where it worked very well.
After the problem deinstalled and took away rest things that i could find.
Reïnstalled there in D.
It was not accepted.
Installed Wubi in C.
I had to do that 2 times before it was accepted and it works well now.

I accept only safty ufdates there now.

Just did all the updates in my Vista pc.  NO Problems there.

I hope that someone can do something with this information.
I am absolutely not a fan of Windows 7.

Kindest regards Merlijntje

Do yourself a favor and if you like Ubuntu do a full installation to your hard disk not wubi. Wubi has some disadvantages. One being that since it is inside windows it has some quirks. Another is that wubi is not meant to be a permanent installation- although I realize quite a few are trying to do just that. Rather it is meant to be a trial to see if you like Ubuntu for those unwilling to partition their hard disk(s) until they are sure they like Ubuntu. Read [this]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/") interview with the creator of wubi and note his answer to the second question.

The last reason is the most important in my mind: it is harder to get help with wubi as most users do not use wubi and are therefore unfamiliar with it's problems and the fixes for those problems.

---

