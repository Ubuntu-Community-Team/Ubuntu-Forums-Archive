---
title: "Tar.gz"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by Rim3nX on 2008-07-01
I have no idea how to install dictionary that is in tar.gz pack... I realy need help, please HELP me???

---

### Post by Pumalite on 2008-07-01
This might help:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Rim3nX on 2008-07-11
It doesn't help... I have download neutronium theme in tar.gz but I cant install it just by draging it to theme window or installing it, it seas it doesn't appears as valid theme... whats the deal

---

### Post by iaculallad on 2008-07-11
> **Rim3nX said:**
> It doesn't help... I have download neutronium theme in tar.gz but I cant install it just by draging it to theme window or installing it, it seas it doesn't appears as valid theme... whats the deal

Untar the file archive, and inside it, hopefully, you'll find the install file/manual.

```
cd directory_location_of_archive_file
tar -xvzf file_name.tar.gz
cd file_name_folder
ls
```

and try to read the install/readme file if it exist.

---

### Post by coffeecat on 2008-07-11
Or, if you don't want to use the terminal, double-click on the tar.gz package icon and file-roller will open. You can browse through the contents to see if there is a readme file and/or extract everything.

---

### Post by fishbulb1022 on 2008-07-22
ok try this,
1. anytime you download a .tar.gz or whatever, just save it to the desktop, its just easier.

2. extract the files by right clicking and hitting "extract here" which will extract it to the desktop.

3. open a terminal window by going to Applications>Accessories>Terminal

4. type "cd Desktop" and make sure to capitalize the D

5. now type "ls" (thats a lowercase LS just for clarity's sake)

6. this should give you a list of all the directories on the desktop, find the one you want, it should be the name of whatever program you're trying to install, but make sure you don't pick the .tar, you want the one you extracted, which will be the same thing without the extension. Highlight and copy the name.

7. Now type "cd" and paste what you just copied after it (remembering the space between cd and the file name)

8. Now type ./configure to automatically configure the program. if it stops in the middle and says it needs a package, copy the name of the package, go to the synaptic package manager (system>administration>synaptic package manager) and do a search for that package. anything that looks the same with -dev on the end is also necessary, get it to. once you've got everything checked, click apply.

9. now back in the terminal (if you closed it, you'll have to navigate back to the directory again, using steps 4-7) type ./configure again

10. repeat steps 8-9 until all the packages necessary have been installed and the configuration completes.

11. Now type "make" to compile the code

12, now "make install" to install it

I hope this helps, it should work, if it doesn't feel free to ask more questions and check out the link i gave you (you should also check the "Navigating the Terminal" link they have, it was really helpful)

if it doesn't work, post a link to the thing you're trying to install and let us try and we can tell you what we find.

---

