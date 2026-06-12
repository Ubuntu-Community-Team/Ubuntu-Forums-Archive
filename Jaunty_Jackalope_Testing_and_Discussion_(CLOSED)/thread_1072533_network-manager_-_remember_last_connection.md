---
title: "network-manager - remember last connection?"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phax on 2009-02-17
Hi there!

If I add in NM new wired connection with static IP everything is OK. But if I logout or reboot computer Network Manager connect again with Auto eth0. It does in Intrepid - so I tried Jaunty and it is the same...

I know how to set static IP without NM, but wouldn't be desirable for NM to remember last static connection? Or something like that? I would fill a bug...

thanks for comments and sorry my english...

Peter

---

### Post by hugmenot on 2009-02-18
Did you try to mark the checkbox "Available to all users"? If it&#8217;s marked, did you try to uncheck it?

---

### Post by phax on 2009-02-18
I tried - the icon on the Apply button changed and when I click on it nothing happened... it doesn't saved.

---

### Post by hugmenot on 2009-02-18
The question is whether it stores the connection settings and loads them on your next login or reboot.
The thing with the "Available to all users" box is that when it is checked then the connection gets saved to a file in /etc/NetworkManager/system-connections/. When it&#8217;s not checked then it only goes into your user&#8217;s gconf settings under /system/networking/connections/. You may want to check out if this happens.

---

### Post by scaine on 2009-02-18
When you check that button, the apply button changes so that you can't close the dialog.  I think there's a known bug about this - I'll see if I can find it.

I think there's another bug too whereby even if you manage to get the setting to apply, it doesn't remember it.  I'll have a check on launchpad later on.

---

### Post by phax on 2009-02-19
Well, if I create connection it is saved, but if I reboot/logout the default connection is Auto eth0 again and I must manually choose the connection I've created.

In Jaunty everything in Auto eth0 is faded (attachment) - I can't change anything. Even with gksudo nm-connection-editor.

---

### Post by phax on 2009-02-19
Sorry, attachment here:)

---

### Post by hugmenot on 2009-02-19
What happens when you create a new connection next to "Auto eth0"?

---

### Post by phax on 2009-02-19
When I create new connection everything is OK, it is created and saved. And I can switch between 'My connection' and 'Auto eth0'. So I am connected thru 'My connection', I reboot computer and when I login there is again chosen 'Auto eth0' and I must manually choose 'My connection'.

And I want NM to choose the last connection I was connected thru.

I hope you understand:) And of course thanks for help...

---

### Post by captive on 2009-02-20
I have the same problem, any chance to fix it?

---

### Post by scaine on 2009-02-21
Can someone try this?  It seems to fix a problem I was having with NM not letting me set my WIFI connection to "Apply to all users".

Open a terminal and go :
```
sudo -i
polkit-gnome-authorization

```

At the bottom of the window that opens, you should see "network-manager-settings", "system" and "Modify system connections"

Click on that last one and the right-hand side where it says "Explicit Authorisation", hit the "Grant" button, then choose your username.  No need to add any constraints - just leave it on "none".

Now, when you start up NM/Edit Connections", you'll be asked to confirm your authorisation (I choose "always").  You should now be able to tick the "All Users" box and "Apply" should now work.

I'm hoping that this might also fix the instance where Auto Eth1 is fully greyed out, but I haven't had a chance to test, and since I'm getting very, very drunk tonight, I won't be at my PC again till Monday...

Good luck!

---

### Post by phax on 2009-02-21
It works!

But:) After change in polkit I was able to click 'Apply' button so I checked 'Available to all users'. After restart the 'My connection' was chosen! But the 'Auto eth0' disappers (before reboot the options were still greyed)... so I added new connection 'DHCP' which do the same...

- It didn't ask me to 'confirm your authorisation'.

- I don't understand why the 'Auto eth0' disappear?

I hope you've enjoyed the night:)

---

### Post by scaine on 2009-02-22
Urgh.  Night was magic, but I'm running on 6 hours of sleep and my head's not in a happy place...

Anyway, I think the missing "Auto Eth0"*might* be do with with running gnome-nm-connections (or whatever the command is) as sudo?  If not, then I have no idea what would cause that...

Right.  I'm away for a lie down...  :p

---

