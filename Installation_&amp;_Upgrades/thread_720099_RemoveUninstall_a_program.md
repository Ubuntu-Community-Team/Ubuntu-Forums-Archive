---
title: "Remove/Uninstall a program"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by mushin77 on 2008-03-09
I was attempting to install vtigercrm-5.0.3.bin and ran into a problem. During the install it created a folder on my desktop because this is where I had the .bin file located. I now want to delete the folder that was created on my desktop called vtigerCRM_linux but when I try to delete I get an error saying that I do not have permission. So I have a few questions.

1.) How do I uninstall the program? (It may not have even be installed not sure since I did not complete the whole install)
2.) How do I delete the folder that was created on my desktop as part of the install process.

Since I am learning would you mind providing a brief explanation of what the commands are. IE SUDO means run as a super user I think.

Thanks
Phil

---

### Post by Tatty on 2008-03-09
Im not quite sure how you would go about uninstalling something you have installed from a .bin - i should imagine the software should include instructions to tell you this.

But i can explain how to delete a folder you dont have permissions for:
If you do not have permission to delete that folder then you have two options..  you could chown the folder to give yourself the permissions for it...
... or the way i would do it is to open nautilus as root, navigate to the desktop and delete it that way.  To open nautilus as root, run this from a terminal:

```
gksudo nautilus
```

Explanation:
1. The problem is that you dont have permission to access that folder - it is probably owned by root.

2. Nautilus is the name of the file browsing software in Ubuntu. Whenever you are navigating folders graphically you are using nautilus. You can also launch it from a terminal by typing "nautilus".

3. To be able to modify things owned by root, you must have root permissions.

4. To run a command/application with root privilages you must add the word "sudo" to the start of the command - eg. "sudo halt" shuts down the system or "sudo gedit" opens gedit with root privilages.

5. So running "sudo nautilus" will give you root privilages from within the file browser that pops up.

6.  However, there are a few issues which can be created by using "sudo" for a graphical applications... so for graphical applications you should use "gksudo".

---

### Post by mushin77 on 2008-03-10
Awesome Reply! Your explanation was great and I was able to delete the folder with the steps you provided. Plus!!!.... I learned something in the process. Thanks for the help!
:)

---

