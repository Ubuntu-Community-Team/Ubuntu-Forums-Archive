---
title: "Email links in Thunderbird cease working"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by richardh on 2008-05-02
After installing hardy, web links in thunderbird [2.0.0.12 (20080227)] no longer open a tab in Firefox (30b5).

I cant find an editor preference to switch the function back on.

What happened and where?

---

### Post by Dale61 on 2008-05-02
I have a similar problem.

If I click on a link in Thunderbird, but have yet to open FF3.0b5, what actually opens is FF2.  However, if FF3.0b5 is already running, links will be directed to that.

As a quick (and probably lazy) fix, I always have an instance of FF3.0b5 running on at least one of my four work spaces.

---

### Post by gewitty on 2008-05-06
> **richardh said:**
> After installing hardy, web links in thunderbird [2.0.0.12 (20080227)] no longer open a tab in Firefox (30b5).

I cant find an editor preference to switch the function back on.

What happened and where?

I have exactly the same problem. After upgrading to Hardy, web links in Thunderbird no longer work. When hovering the mouse over such a link, the correct address appears at the bottom of the Thunderbird screen, but when clicked it fails to trigger Firefox to display the page.

I have explored all of the Thunderbird settings and options, looking for some way to restore the functionality, but without success.

---

### Post by rothbert on 2008-05-09
Try this thread: [http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox](http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox)
tweaking config editor in Thunderbird solved the links issue for me (with usr/bin/firefox-2, rather than usr/bin/firefox)

---

### Post by Dale61 on 2008-05-09
> **rothbert said:**
> Try this thread: [http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox](http://ubuntuforums.org/showthread.php?t=772112&highlight=thunderbird+links+firefox)
**tweaking config editor in Thunderbird solved the links issue for me (with usr/bin/firefox-2**, rather than usr/bin/firefox)

For me, I had to use /usr/bin/firefox-3.0, and now, when I click on a link in Thunderbird, Firefox 3b5 now opens.

---

