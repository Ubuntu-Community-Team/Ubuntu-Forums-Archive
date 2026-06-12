---
title: "The application &quot;touchpad-indicator&quot; is not working"
date: 2015-10-27
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2015-10-27
I just installed 14.04.3 in a Toshiba Portege R900. Everything went well, except for the application that I installed called "touchpad-indicator". When I click on Accessories->touchpad-indicator nothing happens. Furthermore the icon shown is just a red "ban" (or whatever is called) and not the usual icon. I have exactly the same version of the program running on a Dell M90 and there are no problems. I tried reinstalling but no avail. Any suggestions?

Thanks,

Daniel

---

### Post by danielsender on 2015-10-28
> **danielsender said:**
> I just installed 14.04.3 in a Toshiba Portege R900. Everything went well, except for the application that I installed called "touchpad-indicator". When I click on Accessories->touchpad-indicator nothing happens. Furthermore the icon shown is just a red "ban" (or whatever is called) and not the usual icon. I have exactly the same version of the program running on a Dell M90 and there are no problems. I tried reinstalling but no avail. Any suggestions?

Thanks,

Daniel

bump

---

### Post by jawilljr2 on 2015-10-28
Are you affected by [this bug.?](https://bugs.launchpad.net/touchpad-indicator/+bug/1482039)

If so the workaround is in that thread.

---

### Post by sudodus on 2015-10-28
In Lubuntu and Xubuntu you can also simply use the following commands

```
synclient touchpadoff=1
```

to turn off the touchpad, and

```
synclient touchpadoff=0
```

to turn it on again.

You can make aliases for the commands to make them more convenient to use, or put them into autostart.

---

### Post by danielsender on 2015-10-28
yes, same bug. when I get home I'll try the fix.

Thanks a lot.

---

### Post by jawilljr2 on 2015-10-28
> **sudodus said:**
> In Lubuntu and Xubuntu you can also simply use the following commands

```
synclient touchpadoff=1
```

to turn off the touchpad, and

```
synclient touchpadoff=0
```

to turn it on again.

You can make aliases for the commands to make them more convenient to use, or put them into autostart.

What I like about touchpad-indicator is that when you plug in an external mouse it automatically turns of the touchpad.

---

### Post by danielsender on 2015-10-28
the problem with this solution is that this machine belongs to a person who is not very good at opening terminals and such - besides, it's nice to have it working automatically. Thanks!

---

### Post by jawilljr2 on 2015-10-28
> **danielsender said:**
> yes, same bug. when I get home I'll try the fix.

Thanks a lot.

Hope it works.

---

### Post by sudodus on 2015-10-28
Yes, when it works, the Touchpad Indicator is great. :-)

---

### Post by danielsender on 2015-10-29
I just use the solution given on the given link to create the
```
~/.config/touchpad-indicator/touchpad-indicator.conf 
```
and everything works well.

Thanks guys.

Daniel

---

