---
title: "Is it too late to back out?"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Nesaskewatch on 2012-05-12
Good day.  I started installing 12.04 over 11.10 and realised I forgot to make a note of the precise spelling of the user name so I retain all of the emails, accounts, settings etc in my separate /home partition.  I got to the point where the installer asks for a computer and user name before I caught on.  I have tried to simply back out using the "back" button but it will not go any further back than the time zone selection.  Is it possible to quit the install and go back or is it too late now?

I am still running the installer and hoping someone can tell me of a way to either back out of the install or maybe just find the previous user name and most importantly whether I used capital letters or not.  Does the user name have to match the spelling exactly, complete with upper and lower case letters, or does the installer reduce it to all lower case so all I have to do is match the spelling properly to retain my settings etc?

Thanks a ton folks.

---

### Post by Tanker Bob on 2012-05-12
I don't know about backing out, but the user name must match exactly. Upper case counts.

You can always guess, and if you guess wrong, you can add the real user with all appropriate rights once the installation is done. I'm not sure if you can go back and delete the installation user at that point, though. At worst, you'll wind up with an empty, useless user directory under /home.

---

### Post by flemur13013 on 2012-05-12
Look at /etc/passwd - on your original install.

---

### Post by Nesaskewatch on 2012-05-12
I have to confess that I did something very similar last time I upgraded which makes me a blithering idiot really.  I will press on then, and if I flub the spelling I will come back and ask about correcting things as you mention.

Thanks very much for the quick response!  Hopefully I can match it first time...

---

### Post by Nesaskewatch on 2012-05-12
> **flemur13013 said:**
> Look at /etc/passwd - on your original install.

I'll give that a try!  Stand by a tic.

---

### Post by Nesaskewatch on 2012-05-12
I am unable to open any of the other file systems.  They are shown but nothing happens if I click on them or select mount.

---

### Post by Nesaskewatch on 2012-05-12
I was wrong.  The filesystem is not listed when I click on the home folder.  How would I open the filesystem currently being upgraded?  I am currently using ubuntu off the thumb drive and the installer is still running.

---

### Post by Tanker Bob on 2012-05-12
> **Nesaskewatch said:**
> I was wrong.  The filesystem is not listed when I click on the home folder.  How would I open the filesystem currently being upgraded?  I am currently using ubuntu off the thumb drive and the installer is still running.

AFAIK, you cannot view or access the file systems while an installation is running.

---

### Post by Nesaskewatch on 2012-05-12
> **Tanker Bob said:**
> AFAIK, you cannot view or access the file systems while an installation is running.I guess I will proceed then and maybe nail the spelling?  Like you say, the worst case scenario isn't all that bad.

Thanks!

---

### Post by Nesaskewatch on 2012-05-12
At least my brain retains *some* usefull info, sometimes.  I got the spelling correct and the upgrade went fine.  Thanks for your help!

---

