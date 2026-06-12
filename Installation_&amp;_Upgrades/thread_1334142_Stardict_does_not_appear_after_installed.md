---
title: "Stardict does not appear after installed"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Alanbuntu on 2009-11-22
I installed Stardict thru Synaptic. After installed, there was no indication showing it was successfully installed and I couldn't find the application to open. (no stardict under Applications>Accessories). i reinstalled it but the result was the same.

please help, thank you.

---

### Post by dcottingham on 2009-11-22
What was the exact name of the package you asked synaptic to install?

---

### Post by Kevbert on 2009-11-22
Go to Applications-Accessories-Terminal and type ```
stardict
```
If StartDict is displayed then you've lost the shortcut. To generate the shortcut menu item right-click on 'Applications' and then select 'Edit Menus'. Now click on Applications-Accessories in the new 'Main Menu' window that is displayed. Look in the righthand box to see if StarDict is displayed and if so make sure the box is ticked. If not click on new item and enter the following:
Type (select) - Application
Name - StarDict
Command - stardict
Comment - Lookup words
Now click on 'Close' and 'Close' again the Main Menu.
You should now be able to run the application from the menu.

---

### Post by Alanbuntu on 2009-11-22
after i typed 'stardict' ,it asked to install stardict , it showed the message:

  The program 'stardict' can be found in the following packages:
    * stardict-gnome
    * stardict-gtk
    Try: sudo apt-get install <selected package>

i followed the instruction, the shortcut appeared.

Thank you for all the replies!!

---

### Post by HeadHunter00 on 2009-11-22
sudo apt-get install stardict-gnome

Its more stable than gtk version.

---

### Post by HeadHunter00 on 2009-11-22
Remember, if you can't find something, terminal is always there for you.

---

