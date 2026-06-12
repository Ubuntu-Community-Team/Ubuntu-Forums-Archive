---
title: "ALT+CTRL+DEL != taskmanager but == logout"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by jhay2 on 2014-04-20
Hi , Before at lubuntu 13.10 and older versions 

ALT+CTRL+DEL shortcut  keys  makes TASKMANAGER or LXTASK appear on screen 


but after Upgrading LUBUNTU 14.04

ALT+CTRL+DEL is now a shortcut for  LOGOUT , :(

i dont know what is the new shortcut key combination for task manager. 

Any Ideas ? 

thanks

---

### Post by grumblebum2 on 2014-04-20
Look in **~/.config/lxsession/Lubuntu/rc.xml**

Open in the text editor and search for **lxtask**.

The section in 13.10 is...
```
<!-- Launch task manager on Ctrl + Alt + Del-->
    <keybind key="C-A-Delete">
      <action name="Execute">
        <command>lxtask</command>
      </action>
    </keybind>
```

Can't find then search for the logout entry and adapt for what you want.

---

### Post by Dennis N on 2014-04-20
I got the same result here.

Open **~/.config/openbox/lubuntu-rc.xml** in text editor.

Line 379-384:

```
    <!-- Launch task manager on Ctrl + Alt + Del-->
    <keybind key="C-A-Delete">
      <action name="Execute">
        <command>lxsession-default tasks</command>
      </action>
    </keybind>

```

At this time, it looks like the command **lxsession-default tasks** is not correctly implemented.

Change **lxsession-default tasks** to **lxtask** and save. Then log out and back in and it works again.

---

### Post by jhay2 on 2014-04-20
wow it works ,thanks , it was a very simple solution :)

---

