---
title: "Reinstall Ubuntu without losing data"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by sparkguitar05 on 2008-06-04
I have been having some MAJOR problems with Ubuntu lately and I want to reinstall the OS.  How can I do this without losing my data?

---

### Post by tcommbee on 2008-06-04
The obvious way is to burn it to a DVD and copy it back afterwards (which also prevents some old config-file to "spoil" the new system). Another possibility is selecting your old home-partition upon installation as new home without formatting it (which may "spoil" your new system with some broken config files).
Are you sure the problems are so big you have to reinstall?

---

### Post by sparkguitar05 on 2008-06-04
I have over 100 gigabytes of data, so I really don't want to burn all that to DVDs.

Check my other threads for more info on my problems.  I'm having some serious issues with my video and sound.  I've been trying to fix my problems for two days straight with very little luck.

All I need is for my video and sound card drivers to go back to normal, but Ubuntu makes it way too difficult.

---

### Post by tcommbee on 2008-06-04
In this case, the second method should be okay, since your user-specific files are working. You only have to take care to name the first user exactly the same again and not to format the home partition (provided your data is there).

---

### Post by sparkguitar05 on 2008-06-04
I reinstalled Ubuntu without formatting my /home partition.  I logged in and all my settings were intact.  I installed Thunderbird and all my emails were there.  Everything worked perfectly for me.

My parents also use the computer.  I re-created their accounts and when they logged in their desktop icons were there, but that was about it.  My mom uses Thunderbird and she is going CRAZY because none of her emails or address book are there.  Also, all of their bookmarks and such in Firefox are gone.

How do I get all this data back?

---

### Post by tcommbee on 2008-06-04
Did you also create them in the same order and with the same usernames as before? Look under /home/ wether there are additional users now. That they have there desktop icons but not their emails sounds very odd.

EDIT: I checked the "user-add" settings dialog and it refuses to add a new user if a home directory of the same name is already there. If you used that to create the users and didn't get an error you named the users differently.

EDIT2: did the reinstallation at least solve your sound/graphics problems?

---

### Post by sparkguitar05 on 2008-06-05
Yes, the reinstall solved my sound/graphics problems.  Here's what I did to create the new users.

My parents names are bob and sue.  To create sue, I renamed /home/sue to /home/sue2.  Then I created sue's username and copied all the data over from sue2.  I did the same with bob.

When I logged in to their names, their desktop icons were all there.  The wallpaper was the Hardy default and all their settings for programs were all default.  My settings are the only ones that remained intact.

---

### Post by tcommbee on 2008-06-05
The problem with copying is, that often permission and owners are changed. You hopefully kept sue2/ and bob2/ for now as backup. First I would check if you really copied everything, including hidden files. Next I would try
```
sudo chown -R sue /home/sue/
sudo chown -R bob /home/bob/
```
to make sure all their files belong to them. You should also check the hidden files /home/sue/.xsession-errors and /home/bob/.xsession-errors for any hints of programs complaining about permissions.

---

### Post by tcommbee on 2008-06-07
So, how's the status? Did any of the last ideas solve the problem?

---

### Post by NoVista on 2008-06-07
I think MoM took the puter away .. ..  :lolflag:

---

