---
title: "Ok I really need help"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by shayaleigh on 2008-06-22
[SIZE="1"]Ok so you know how Ubuntu has a thing where you click on it to update your system?

well mines not working anymore. And now I cant install or update programs.

Help me? what do I do?
[/SIZE]

---

### Post by bubba_169 on 2008-06-22
System -> administration -> Update Manager  will get you your updates...

Is that what you're trying?

---

### Post by shayaleigh on 2008-06-22
Ok I have 85 updates and it wont let me update

it keeps saying there is an error and that I need to manually update or something like that...

yes thats what im trying, and its just not working

:'(

---

### Post by shayaleigh on 2008-06-22
this is exactly what it says to me when I try and update:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by bubba_169 on 2008-06-22
Try opening a terminal and typing:

```
sudo dpkg --configure -a
```

Usually you have to run this command if something went wrong with a past install e.g. it got interrupted before it could finish

---

### Post by shayaleigh on 2008-06-22
that didnt work :(

---

### Post by bubba_169 on 2008-06-22
Did you get an error message from running that last command?

---

### Post by shayaleigh on 2008-06-22
well,
I opened the terminal, I put in the code, but nothing happened

ill try it again

---

### Post by shayaleigh on 2008-06-22
ok it worked this time! thanks for your help!

---

