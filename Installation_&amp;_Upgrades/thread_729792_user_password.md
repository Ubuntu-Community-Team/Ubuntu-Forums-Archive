---
title: "user password"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by bulldogr2cool on 2008-03-20
How do I get past the user and password screens? I instaled on an old laptop that was given to me and I did not ever put any passwords in it. I tried the bios passwords but non worked, although I'm not sure what the User name was either
Thank you for any help you can give me

---

### Post by keratos on 2008-03-20
You need the name of the user you setup when installing. It would have asked you for a name and a password at that point. The same credentials need to be supplied here.

What distro are you using? 

Also did you "enable root login" at the install or don't you know?

---

### Post by dacorr on 2008-03-20
linux is case sensitive, with user names. if you do not remember the user credentials do you know the root credentials?

enable root login allows you login from the GUI welcome screen.

at this screen hold down ctrl & alt a press F7 or F6 or F8

is should change screen to a terminal and give you login ability as root.

once login in as root you can startx it will complain about the xserver being locked and you will need to **rm** the file it gives you in the error message, i forget the path. do a ls at in the ssae directory to make sure there is a .bck of the file you are deleting for when you reboot latter. if not create one.

then startx again and you will be logged in as root with the GUI from there you can edit user accounts from system/administration/users and groups in the menu bar.

once done shutdown and restart then it will use the backup file of the one you deleted

---

