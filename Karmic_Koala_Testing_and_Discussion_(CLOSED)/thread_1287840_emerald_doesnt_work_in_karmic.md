---
title: "emerald doesnt work in karmic"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by libihero on 2009-10-10
my emerald isnt working in karmic. i put "emerald" as the command in compiz and rebooted, but nothing changes.  did compiz change or does it just not work?

---

### Post by OpenGuard on 2009-10-10
In Terminal:
```
emerald --replace

```

Still nothing ?

---

### Post by howefield on 2009-10-10
Better to press Alt + F2 keys and type the command in the run box, using the terminal means accidentally closing the terminal will stop emerald and revert to the previous window decorator. 

I have the same issue as the OP, you've prompted me to find the fix :)

---

### Post by OpenGuard on 2009-10-10
> **howefield said:**
> Better to press Alt + F2 keys and type the command in the run box, using the terminal means accidentally closing the terminal will stop emerald and revert to the previous window decorator. 

I have the same issue as the OP, you've prompted me to find the fix :)

Alt+F2 for testing purposes is not such a good idea - you'll not see app's output ( in case of errors ).

---

### Post by libihero on 2009-10-10
my emerald isnt working in karmic. i put "emerald" as the command in compiz and rebooted, but nothing changes.  did compiz change or does it just not work?

---

### Post by MegaJim on 2009-10-10
You'll probably find more help here: [http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

---

### Post by muteXe on 2009-10-10
Has Karmic been officially released yet?

---

### Post by howefield on 2009-10-10
Starting in terminal is useful if you have an error/problem, but not so much if you don't.

---

### Post by howefield on 2009-10-10
> **muteXe said:**
> Has Karmic been officially released yet?

October 29th

[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

---

### Post by OpenGuard on 2009-10-10
> **howefield said:**
> Starting in terminal is useful if you have an error/problem, but not so much if you don't.

And he have a problem :rolleyes:

---

### Post by howefield on 2009-10-10
Yes he does, but my money is on the problem being the way the OP is starting emerald, and not with the app itself. I guess we'll find out when the OP returns...

To the OP, you can also place emerald --replace in the "Command" field within System > Preferences > CompizConfig Settings Manager >  Window Decoration.

This will enable emerald automatically at boot up.

---

### Post by cariboo on 2009-10-10
Please don't double post on the same subject. Please post Karmic questions in the proper place. Moved to karmic testing & Discussion

---

### Post by other guy on 2009-10-10
Emerald works in Karmic.

terminal 

```
emerald --replace
```Then in Compiz settings manager. Look for the Window Decoration.

Once you are in that. Find the box labeled command. 
It will have:
```
/usr/bin/compiz-decorator
```Replace it with this:

```
emerald
```Close out the terminal. Now if you close it out before, no decorator. So do it afterwards. You might have to hit return in the Window Decorator command box thing, in Compiz after you type emerald. To get it going.  Emerald works for me doing this. Not saying it is bug free on your setup, but I find it stable and works great. Just not perfect to get going.

---

### Post by libihero on 2009-10-16
i tried that, and emerald works while the terminal is open.  once i close the terminal, there is no window border at all
even if i go again and type emerald in compiz

---

### Post by liveforfunnow on 2009-10-25
> **libihero said:**
> i tried that, and emerald works while the terminal is open.  once i close the terminal, there is no window border at all
even if i go again and type emerald in compiz

I am having the exact same problem. How can we get Karmic to start Emerald as the default window manager?

---

### Post by other guy on 2009-10-26
I lost track of this thread. My apologies. The forum software did not notify me of new posts.

Ok, first thing did not work got you... Now lets try something I tested and worked.

Instead of using the terminal. Let's use the Run Application. Which is Alt+F2


Then type emerald --replace into that, hit run - and it should make it work for you.. It was persistent past rebooting for me. Instead of it closing with the terminal.

Hope this work for you that are having issues with it, as it did traditionally.

---

### Post by dentaku65 on 2009-10-26
I suggest to use fusion-icon as launcher for windows manager in general and/or for windows decorator like emerald
```
sudo apt-get install fusion-icon
```

---

### Post by 6205 on 2009-10-26
> **libihero said:**
> my emerald isnt working in karmic. i put "emerald" as the command in compiz and rebooted, but nothing changes.  did compiz change or does it just not work?

Try to run Compiz Config Settings Manager(if you don't have it, install it) and go to properties of Window Decoration plugin..

There should be somewhere decorator command with path like /usr/bin/compiz-decorator

Replace with [COLOR="DarkGreen"]/usr/bin/emerald[/COLOR] then logout and log back in. Worked for me in Jaunty, should also in Karmic... hopefully

---

### Post by libihero on 2009-10-26
the fusion icon worked! :)

---

