---
title: "Firefox in Hardy Heron"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ellalan on 2008-06-27
Hi all,
I have messed up my Firefox when I tried to install Firefox3 in my Ubuntu 7.10 resulting in the notification as follows:
could not launch menu item. Failed to execute child process "firefox"(No such file or directory).
Then I tried upgrading Ubuntu 7.10 to Hardy Heron,even after upgrading I am getting the same message and unable to use Firefox3.
Could someone help me to rectify this please.
BTW I have noticed the Firefox is installed under Add/Remove. Thank you in anticipation.

---

### Post by Vivaldi Gloria on 2008-06-27
Try this:

Start Synaptic from System > Admins. menu at the top panel.

Search for ff. Right click and choose completely uninstall for both ff2 and ff3.

After that reinstall ff3.

---

### Post by ellalan on 2008-06-27
Thank you vivaldi Gloria
I tried your method but no luck, I have restarted after removing FF2&FF3 then restarted after reinstalling FF3 as well.

---

### Post by Vivaldi Gloria on 2008-06-27
Press Alt+F2 and start

```
firefox-3.0
```

Does it work? 

If it does then you can edit the menu item to firefox-3.0.

---

### Post by ellalan on 2008-06-27
Hi Vivaldi Gloria
Thanks a lot,it worked and you made my day.

---

### Post by ellalan on 2008-06-27
Hi Vivaldi Gloria
I spoke too soon, when I pasted the code the FF3 runs but I do not know how to edit. Could you be able to describe in detail please.

---

### Post by Vivaldi Gloria on 2008-06-27
You're welcome.

---

### Post by Vivaldi Gloria on 2008-06-27
> **ellalan said:**
> Hi Vivaldi Gloria
I spoke too soon, when I pasted the code the FF3 runs but I do not know how to edit. Could you be able to describe in detail please.

Our posts crossed there.

Right click on the menu (ubuntu symbol) and choose edit menus. Find firefox, right click on it, choose properties. Now write firefox-3.0 instead of firefox in the command box.

---

### Post by ellalan on 2008-06-27
Hi Vivaldi Gloria
Yes, I have done as you described and it's working now (ie: I can access FF3) but it opens up in Offline Mode everytime I try to open the browser and I have to go to File and untick the Offline Mode,any thoughts on that please. Thank you for solving my problem.

---

### Post by Vivaldi Gloria on 2008-06-27
> **ellalan said:**
> Hi Vivaldi Gloria
Yes, I have done as you described and it's working now (ie: I can access FF3) but it opens up in Offline Mode everytime I try to open the browser and I have to go to File and untick the Offline Mode,any thoughts on that please. Thank you for solving my problem.

What happens if you write

```
firefox-3.0 %u
```

or 

```
firefox-3.0 www.google.com
```

instead of firefox-3.0?

---

### Post by ellalan on 2008-06-27
Hi Vivaldi Gloria
I have found the solution in this link:
[http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)
However I do appreciate your help and time you spend to resolve my problem.
BTW I do like Hardy Heron,when it was released I did installed the CD version and I was not impressed then reverted back to Gutsy.
Today I installed it through upgrade(it took 3Hrs though but well worth it).
Thanks again.

---

### Post by Vivaldi Gloria on 2008-06-27
> **ellalan said:**
> Hi Vivaldi Gloria
I have found the solution in this link:
[http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)
However I do appreciate your help and time you spend to resolve my problem.
BTW I do like Hardy Heron,when it was released I did installed the CD version and I was not impressed then reverted back to Gutsy.
Today I installed it through upgrade(it took 3Hrs though but well worth it).
Thanks again.

Good find there. Have fun.

---

