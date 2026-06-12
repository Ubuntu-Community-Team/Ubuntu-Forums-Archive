---
title: "Upgrade woes: 10.04 to 11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Dark Shinobi on 2011-10-19
I have been using 10.04 since it was released and have been and will continue to be very happy with it. So today I decided to try to upgrade (figured it was time after a year and a half) so after a backup I went ahead and upgraded to 10.10. So far so good so I ran the package update and then the distro update to 11.04. Everything went smooth until after login. I get my gnome desktop, but no internet access, no taskbar, no application, terminal wont open, alt+F2 fails to bring up anything. In fact, no key shortcuts work except ctrl+alt+del. I'm not sure if it's because gnome is no longer the default, but it didn't install unity so I couldn't use it. Got similar problems with KDE and ENLIGHTENMENT, they would load but no update manager, no ethernet or wifi, and very few applications would run. Does anyone know what might have caused this problem? Or what I might be able to do to resolve it? I am interested in bringing this computer up to date, and other distros are out of the question :p

---

### Post by sammiev on 2011-10-20
Hi Dark Shinobi, I prefer a clean install. Some people had great luck upgrading but if you have a backup of what is working for you why not try a fresh install of another version. However, you should always try it with a live CD/DVD or USB first to make sure it's compatibly with all your hardware. :)

---

### Post by Dark Shinobi on 2011-10-20
Yeah probably should have done that, its from a laptop anyway. I would prefer not to clean install with all the applications I have accumilated over time. I downloaded a copy of both versions I need to get to 11.10 (Im on 10.10 and it works great) And see if the upgrade works better via CD. If not, then I might just bite my lip and go for fresh. Feels great, but it gives me horrible flashbacks of my windows days

---

### Post by jacob.david on 2011-10-20
Hi Dark Shinobi, I'm having almost exactly the same problem as you. 10.04 to 10.10 went OK. But it hung while upgrading from 10.10 to 11.04. I restarted the lap top and continued with the upgrade. Now it didn't install unity (because of hardware incompatibility) and having many problems with Gnome. Any further upgrade throws up a Partial upgrade option, which is not recommended. I'm also planning to do the upgrade from DVD. Let me know how it goes.

---

### Post by tehowe on 2011-10-20
> **Dark Shinobi said:**
> Yeah probably should have done that, its from a laptop anyway. I would prefer not to clean install with all the applications I have accumilated over time. I downloaded a copy of both versions I need to get to 11.10 (Im on 10.10 and it works great) And see if the upgrade works better via CD. If not, then I might just bite my lip and go for fresh. Feels great, but it gives me horrible flashbacks of my windows days

This might help ease your transition a bit, it's a way to save off a list of what you've installed so you can feed it back into a package manager on your new install. I found it elsewhere in these forums

```
dump all your installed packages into a file this way:

sudo dpkg --get-selections > packagelist

then copy 'packagelist' over to the machine on which you want to restore them this way:

sudo dpkg --set-selections < packagelist

and finally, make it happen with:

sudo aptitude dselect-upgrade
```

---

### Post by Dark Shinobi on 2011-10-20
Thank you very much Tehowe, I'll give it a shot tomorrow if the cd upgrade fails. Its already taken all day between backup, upgrades, then subsequent restoration and I am tired.

---

### Post by Dark Shinobi on 2011-10-21
Well tried the CD upgrade with the same results. Guess I shall take tehowe's advice and do a clean boot. Thank you all for your support :)

---

### Post by jacob.david on 2011-10-22
I tried the upgrade using Ubuntu 11.10 DVD and it seems to have completed successfully. However I have numerous problems after that. The desktop is ugly, some of the menus in the launcher are invisible (when I hover the mouse pointer I can see the text) etc. Probably I'll post a separate thread about these problems.

---

### Post by Dark Shinobi on 2011-10-23
Have you tried to login using the Unity 2d desktop? Its different..... but you can get used to it. You can also try installing Gnome 3 or KDE and see if you have better luck with those. So far no problems on my Dell Inspiron 1545, except the wifi drivers which was quick and painless to install. Good luck Jacob.david

---

### Post by Dark Shinobi on 2011-10-23
Ok, got one more small, tiny, almost unimportant question. How do I update my profile to say I run 11.10? Says I don't have permission to when I go to "edit profile". Seriously doesn't matter, but it would be nice if the Ubuntu community knew what version I'm running.....

---

### Post by jacob.david on 2011-10-27
> Have you tried to login using the Unity 2d desktop? Its different..... but you can get used to it. You can also try installing Gnome 3 or KDE and see if you have better luck with those. So far no problems on my Dell Inspiron 1545, except the wifi drivers which was quick and painless to install. Good luck Jacob.david 
Yes, I have now updated to Gnome 3 which seems to have solved the display problem.
About the profile update, I also have the same problem. Seems very wierd.

---

### Post by Dark Shinobi on 2011-11-08
It would seem that you have to accumulate 50 posts to edit certain data on your profile? It says I don't have permission. Its seriously a non issue, I'm just nit-picking lol

---

