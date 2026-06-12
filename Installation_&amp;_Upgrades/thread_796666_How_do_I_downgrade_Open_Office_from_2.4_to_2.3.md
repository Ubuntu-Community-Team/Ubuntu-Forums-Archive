---
title: "How do I downgrade Open Office from 2.4 to 2.3?"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Kirunux on 2008-05-16
Hello everyone,

today I did the upgrade from Gutsy to Hardy. Everything works fine and stable so far. But there is one problem with oo2.4 which comes with Hardy.

The formatting of all my templates in Writer is screwed, so I would have to manually resolve this (which would be quite some work). Since oo2.3 was fine for me and I do not really see the benefits of 2.4 compared to 2.3, I would like to downgrade to 2.3 again.

Could someone please tell me how to do this, or is there a HOWTO on this subject? The search engine wasn't much of a help for me.

Thanks in advance! :)

---

### Post by Kirunux on 2008-05-18
Hi again,

the OpenOffice-webpage and it's forum unfortunately isn't much of a help here either :(

Since the fonts in Firefox also look ugly I suspect that the cause of the problems is some misconfiguration in some system files relating to the fonts display or the whole XServer.

Because I neither have the time nor the nerves to start fooling around with the system files (which probably will make the problems even worse, furthermore this is a business computer which I need every day) I decided to go back to Gutsy, where everything worked fine and stable.

The plan is, after backing up my files, to format the harddrive and thereafter do a fresh install of Gutsy from CD. Can I format the HDD using stuff that's already aboard or do I need special software for this? Or ... would it even work to simply start the Gutsy installation CD again and it will format the HDD and install Gutsy automatically, although there is a newer version of the OS already installed?

Thanks! :)

---

### Post by cdtech on 2008-05-18
I take it the upgrade wiped out your old kernel? All you have on the grub boot loader is the new kernel?

I was going to say that you could purge the openoffice and manually install the older version, but you have other issues as well.

WOW!

> would it even work to simply start the Gutsy installation CD again and it will format the HDD and install Gutsy automatically

You can reinstall Gutsy, it will format if you want it to.

---

### Post by Kirunux on 2008-05-18
Thank you, cdtech! :)

The issue with the strange looking fonts in Firefox seems to be a general problem which has been already discussed here:

[Example 1]("http://ubuntuforums.org/showthread.php?t=787725")

[Example 2]("http://ubuntuforums.org/showthread.php?t=765131")

However ... I will re-install Gutsy later today but will most liekely give Hardy another try when the issues are solved. :)

---

### Post by cdtech on 2008-05-18
Cool, good luck.

---

### Post by Sef on 2008-05-18
OpenOffice 2.4 is only a minor upgrade from 2.3.  Likely the upgrade caused the problem.  If a clean install had been done, then likely you would have not had this problem.

---

### Post by mackra on 2009-03-16
It's not the upgrade, I have a fresh install of 2.4 on Hardy and need to downgrade to 2.0 or 2.3.  It's something with the new build.  Work that I do in 2.0 or 2.3 is different enough in 2.4 that a 80 page paper becomes a 87 pages in 2.4.

Rich

---

### Post by sports fan Matt on 2009-03-16
At the risk of being ignorant, Why downgrade to 2.0 instead of using OOO 3.0 for Hardy?

---

### Post by telemusic on 2009-04-04
For example some .dbf files won't open in 2.4 and 3.0.

Yet they do open in earlier versions.

---

### Post by telemusic on 2009-04-08
About the .dbf's...
After apt-getting openoffice.org-base - they started to work.

---

