---
title: "Icon for firefox"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2010-03-30
It is because I have to ask these thing that I am sometimes upset with linux and ubuntu! Despite the fact that I really want to get it!

I have tried to install firefox 3.6 on my 9.10 ubuntu. it worked OK, but then I have decided that I don't like it and I rather stay with a stable version. I have uninstalled Firefox ok and reinstalled the 3.5.

There were no icons, which annoyed me as I am extremely lazy! lol, I had to create it, so now I have a new launcher pointing to "firefox", it works but the firefox icon is not present, so it is not pretty!

Where is that icon, where is the firefox program I am pointing to actually located. Should I write other things on the launcher as I seem to remember that there were extra % and stuff on the original one? What are they for.

All these questions hoping that it may help me to understand launchers and so on in ubuntu...

---

### Post by mkvnmtr on 2010-03-30
In Ubuntu gnome i open the menu, find Firefox and drag the icon to the panel.

---

### Post by gwu777 on 2010-03-30
> **mkvnmtr said:**
> In Ubuntu gnome i open the menu, find Firefox and drag the icon to the panel.

That is a solution I know, however there is no icon in the menu, and I have already checked if it was hidden in the "organize menu" option. There are no original icons present for Firefox on the system.

---

### Post by wojox on 2010-03-30
Look in **/usr/share/icons/hicolor/48x48/apps/**

---

### Post by ajgreeny on 2010-03-30
I think it's in **usr/share/pixmaps**

Yes it is, I've just checked.

---

### Post by gwu777 on 2010-03-30
> **ajgreeny said:**
> I think it's in **usr/share/pixmaps**

Yes it is, I've just checked.

Found it there, but not in 48x48. I do have a lot of icon there but not ff, any reason for that? Isn't the installation standard?

Is "firefox" the best way to start the application or should I had some parameters?

Just an extra question, where is Firefox and my programs installed? I though it was in opt, but it isn't...

---

### Post by wojox on 2010-03-30
**firefox %u** is what my original Firefox install says.

I've downloaded the .tar.bz2 file and extracted it and moved it to /opt. Don't know how that icon got into **/usr/share/icons/hicolor/48x48/apps/** ? Must have moved it myself. 

If you just downloaded it and extracted it it's probably still in your Home Folder somewhere.

---

### Post by gwu777 on 2010-03-30
> **wojox said:**
> **firefox %u** is what my original Firefox install says.

I've downloaded the .tar.bz2 file and extracted it and moved it to /opt. Don't know how that icon got into **/usr/share/icons/hicolor/48x48/apps/** ? Must have moved it myself. 

If you just downloaded it and extracted it it's probably still in your Home Folder somewhere.

Thank you for your help with looking up the info for me, I have updated my launcher! I used to install as you mentioned above, but I was told I have to get rid of my windows mentality and use the repository! It does make sense though to have the automatic update and all (I know many people keep talking about dependencies as well...) it is sometimes frustrating to wait for the updates to be available...

---

### Post by ajgreeny on 2010-03-30
You don't really need the %u in the command.  That is just there as an added option for the launcher.  Scroll to the bottom of [http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html](http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html) and you will see a long list of the possible suffixes that can be used, and what they mean.

---

### Post by gwu777 on 2010-03-31
> **ajgreeny said:**
> You don't really need the %u in the command.  That is just there as an added option for the launcher.  Scroll to the bottom of [http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html](http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html) and you will see a long list of the possible suffixes that can be used, and what they mean.

Thank you for the great link and helping me twice today!

---

