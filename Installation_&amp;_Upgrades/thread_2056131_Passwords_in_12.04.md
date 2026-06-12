---
title: "Passwords in 12.04"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by inga2 on 2012-09-10
I just did a clean install of Ubuntu 12.04 on a new hard drive. 

1) I set a password for myself as administrator and would like to change it, because it's too long, but I see no way to do so. 

2) When I create another user account, there is no option to set a password, and after "Password," the screen says "Account Disabled."

I can choose automatic logon, but the system asks for a password, and the user cannot log in.  When I do not choose "Automatic logon," the same thing happens.

Please help.

---

### Post by deadflowr on 2012-09-10
Did you try to click on the account disabled bar?
 Click on it and the set password screen will appear. Then set your new password in both password fields, and select change to have it take hold. Also, if you want to only change your current user password, you should be able to by simply clicking on the old password and setting a new one, like above.

---

### Post by inga2 on 2012-09-10
Thanks much, "Flower"-- not at all dead. ;) It worked.

---

### Post by opensshd on 2012-09-10
Using the GUI for user management is severely lacking!

The CLI will give you much more joy, and turns out to be a lot easier than navigating some of the 'other' interfaces for user management. :)

Check out the following command, only takes 5-10 minutes to get the gist of it.

for adding/removing users: 
man adduser
man deluser

for adding/removing users to/from groups:
man addgroup
man delgroup

for information about groups:
man group

---

### Post by inga2 on 2012-09-10
H'mm .. what's the "CLI"?

Are those terminal commands, with "man" bringing up the Manual?

Pardon me for my ignorance. My DOS days are LONG behind me, and I got rather spoiled by GUI interfaces until Vista made me really frustrated because it seemed to be designed to prevent any intelligent person from doing something a little outside the MS box. ;) Ubuntu 12.04 is beginning to feel the same. It's way too reminiscent of Vista's  philosophy of being dummy-proof. So maybe I'll have to start learning Unix/Linux commands.

But couldn't there be a happy medium?

---

### Post by opensshd on 2012-09-11
CLI, yes command line interface - the terminal.

And yes, man is a program that displays manuals for applications you install :)

So, you could even type in:

man man

to get the manual page for the manual program :)

Ubuntu does try to be user friendly, but it is still open source! You still have access to all that low level source code that windows hides :)

Getting to know an application from the CLI is very similar to getting to know a GUI, takes a bit of time, but you can become proficient just like you did with a GUI.

You will come to the realization that Linux can be whatever you make of it. You may not like the window manager, you can change it :) Unity, Xfce, gnome-shell, kde4, enlightenment - all these alternative GUI's are just one command away :)

---

### Post by Stonecold1995 on 2012-09-11
> **inga2 said:**
> H'mm .. what's the "CLI"?

Are those terminal commands, with "man" bringing up the Manual?

Pardon me for my ignorance. My DOS days are LONG behind me, and I got rather spoiled by GUI interfaces until Vista made me really frustrated because it seemed to be designed to prevent any intelligent person from doing something a little outside the MS box. ;) Ubuntu 12.04 is beginning to feel the same. It's way too reminiscent of Vista's  philosophy of being dummy-proof. So maybe I'll have to start learning Unix/Linux commands.

But couldn't there be a happy medium?

CLI is Command Line Interface.  GUI is Graphical User Interface.

If you don't like Unity (the GUI you're using now) because it seems like it treats you like a baby or tries to be idiot-proof or whatever, you should go with KDE, which is my favorite.  KDE is both elegant, aesthetic, and has a huge amount of customization options.  Plus the current version of KDE is much lighter than the older ones, and one of the most common complaints about older KDE was that it was slow and bloated, but that's no longer true.  Just Google "KDE vs Unity" on Google Images and you'll see some impressive examples.

Unity=You can do only what Unity thinks you should
KDE=You can configure anything that the programmers could fit in (so a hell of a lot)
CLI=You can do anything the operating system is capable, but it is harder to use

---

