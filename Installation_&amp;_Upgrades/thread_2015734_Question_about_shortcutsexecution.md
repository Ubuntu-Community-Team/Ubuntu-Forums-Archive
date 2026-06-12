---
title: "Question about shortcuts/execution"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by Red Squirrel on 2012-07-03
How do I find out the path of a shortcut?  In windows I can right click and go propeties, and I know where the exe is.  How do I find out the location of the binary in the case of Linux?

Also  how do I create custom start menu short cuts, and how do I make a program (such as Pidgen) open at startup.

On the same subject of executables, how do I run an console based executable directly within the GUI and actually see the console?  I know I can do it from command line, but sometimes it's nice to do it right from the GUI especially for interactive command line type programs that I write in C++ and such. 

Thanks in advance!

---

### Post by cipherboy_loc on 2012-07-04
For the last question, regarding the creation of custom application icons.

Look into the creation of .desktop files ([http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)). You could also copy an existing .desktop file (from /usr/share/applications) to your desktop and try modifying it. To create a system-wide launcher, put the file in /usr/share/applications/. If you don't want everyone on the system to be able to access this application, place it in ~/.local/share/applications/. 

Disclaimer: I know nothing about xubuntu, so not sure if there are further steps you need to take.

Cipherboy

---

### Post by robtygart on 2012-07-04
> **Red Squirrel said:**
> How do I find out the path of a shortcut?  In windows I can right click and go propeties, and I know where the exe is.  How do I find out the location of the binary in the case of Linux?

Also  how do I create custom start menu short cuts, and how do I make a program (such as Pidgen) open at startup.

On the same subject of executables, how do I run an console based executable directly within the GUI and actually see the console?  I know I can do it from command line, but sometimes it's nice to do it right from the GUI especially for interactive command line type programs that I write in C++ and such. 

Thanks in advance!

If you looking for the orginal icon so you can link to it to launch the application then go to /usr/share/applications/ 

You can also find files by typing into your terminal ```
locate -i "search item"
```

---

### Post by LewisTM on 2012-07-04
> **Red Squirrel said:**
> How do I find out the path of a shortcut?  In windows I can right click and go propeties, and I know where the exe is.  How do I find out the location of the binary in the case of Linux?
Run this command in a terminal
```
which <executable name>
```
For example [FONT="Courier New"]which thunar[/FONT] will output [FONT="Courier New"]/usr/bin/thunar[/FONT]
> Also  how do I create custom start menu short cuts, and how do I make a program (such as Pidgen) open at startup.
Right-click the Applications menu, choose Properties then Edit Menu.
Startup apps can be edited in the Settings Manager/Session and Startup
> On the same subject of executables, how do I run an console based executable directly within the GUI and actually see the console? When you create a launcher, check 'Run in Terminal'

Cheers!

---

### Post by Red Squirrel on 2012-07-04
Cool thanks for the help!

So for the executable, the only way then is to create a launcher?  there's not a way to do it globally for all executable?

---

### Post by LewisTM on 2012-07-05
You can run any command in a terminal with this
```
xfce4-terminal -e '<your command>'
```
Of course you can't set every program to display in a terminal. In Linux there are dozens that run silently in the background, you would be flooded with windows.

So if you want to see the output, just enter the command in a terminal. To make it easy, there's a nice utility called **guake**. Run it a login and you will be able to popup a terminal pane on your desktop with your favorite shortcut key. Properly configured, it would hide as soon as another window takes the focus, allowing you to continue working. Also add a **&** at the end of any command to fork it to the background and return you to the command prompt.

---

