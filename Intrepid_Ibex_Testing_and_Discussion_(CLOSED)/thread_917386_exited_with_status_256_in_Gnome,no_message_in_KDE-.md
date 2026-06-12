---
title: "exited with status 256 in Gnome,no message in KDE-4"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by propwashz on 2008-09-11
I upgraded Intrepid last night.The upgrade finished,and said to reboot.I did.Then....on reboot,my gnome desktop never loads,gives a "/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256" message.When I click "ok" on the message box,the computer hangs.
So..I reset the computer to force a reboot.When the error message ("/usr/lib....exited with status 256") I don't click ok, I ctrl-alt-F1 to get to the console.I installed Kubuntu from there (figuring it was a gnome problem).Reboot again.Change session to KDE. Try to log in. Starts loading KDE,then just exits back to login.No error,nothing.
So then,being desperate,I changed sessions again to E16-Gnome.Works like a charm.Log back out,change sessions to E16-KDE.It works like a charm too.
My question is--does anybody know what "status 256" is? Or why both Gnome and KDE desktops work fine as long as they are loaded with the E16 window manager,but not on their own?
Or how to fix any or all of the above?

---

### Post by Slug71 on 2008-09-11
Im getting the same message after log-in, also after doing updates last night.
Im still able to use Ubuntu fine though. 
I have filed a bug report for this #269215. Please add to this bug.

---

### Post by propwashz on 2008-09-11
ok,I will

---

### Post by jzerbini on 2008-09-12
Confirmed, same here.

Didnt test KDE, though.

Also, compiz was enabled automatically. If I disable it and logoff && login, compiz is there once again.

Thanks !

---

### Post by ronacc on 2008-09-12
I have been getting the same message after last nights update however when I clicked ok the first time my box went on to gnome desktop ok aftter hessitating for a minute or so , later reboots still give the message but get to the desktop much faster .

---

### Post by Slug71 on 2008-09-12
Dont forget to add to my bug report guys.

---

### Post by ronacc on 2008-09-12
I did and attached my xsession-errors also changed status to confirmed .

---

### Post by Slug71 on 2008-09-12
Where do i find the xsession.errors?

---

### Post by ronacc on 2008-09-12
xsession-errors is in your /home/<you>  dir, it is a hidden file (has a . infront of it ) in nautilus go to view (in the menubar) and check show hidden or else just hit ctrl+h while the mouse is in the window to see hidden files .

---

### Post by jzerbini on 2008-09-28
Quick fix:

```
sudo chmod 755 /etc/gconf/gconf.xml.system/
```

Worked here.

---

