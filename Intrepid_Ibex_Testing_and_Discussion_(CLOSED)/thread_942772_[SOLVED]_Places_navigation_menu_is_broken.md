---
title: "[SOLVED] Places navigation menu is broken"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bwallum on 2008-10-09
I have just booted up Intrepid and found that Places>Documents fires up Music instead!

Any clues??

---

### Post by OO7TDD on 2008-10-09
I just recently had this problem, searched around and the following post helped me fix it: [http://ubuntuforums.org/showpost.php?p=5928263&](http://ubuntuforums.org/showpost.php?p=5928263&)

> 
go to terminal and open

```
gksudo gedit /home/"username"/.local/share/applications/mimeapps.list
```

you should find something like:

```
inode/directory="wrong_entry";
```

or 

```
inode/directory="userapp-sudo-6QT17T.desktop;userapp-sudo-3QT24K.desktop;
```

now replace that with:

```
inode/directory=nautilus.desktop;
```

and it should work


Good Luck

---

### Post by danf_1979 on 2008-10-09
Maybe you can fix it from nautilus, try selecting a directory, then properties, and go to the "Open with" tab. Once there you'll probably know what's wrong.

---

### Post by bwallum on 2008-10-09
Thanks for your help. I have been experimenting and found that if I go Places>Computer>Filesystem>Home>'my-home-folder' then Documents folder is shown. Right clicking on Documents folder produces a drop down menu which includes properties. Left clicking on properties brings up the 'Documents Properties' window. The Open With tab allows me to set the application to open folders as 'Open Folder'. I found it set to 'Rythmbox' for some obscure reason. Alls well now, thanks again, Bob

---

### Post by taavikko on 2008-10-09
> **OO7TDD said:**
> I just recently had this problem, searched around and the following post helped me fix it: [http://ubuntuforums.org/showpost.php?p=5928263&](http://ubuntuforums.org/showpost.php?p=5928263&)


Code:

gksudo gedit /home/"username"/.local/share/applications/mimeapps.list



Good Luck

You **do not** use sudo in files or folders placed inside homefolder.
It might screw something up, which is far more difficult to fix.

Other than that, overkill method to fix this issue.
Simple folder properties change would have sufficed.

---

### Post by bwallum on 2008-10-11
+1 on that

---

