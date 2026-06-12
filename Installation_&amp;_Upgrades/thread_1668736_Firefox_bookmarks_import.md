---
title: "Firefox bookmarks import"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by buteobuteo on 2011-01-16
Where does Firefox expect to find a bookmark file to import?  I've done a clean instal but if I try to import bookmarks it says none found but doesn't give the chance to browse to the file (I've dropped bookmark.htm onthe desktop for now). 
Thanks in advance.

---

### Post by presence1960 on 2011-01-16
Follow the screenshots, at the last step find your HTML file backup and click Open. Your bookmarks will be imported.

---

### Post by lovinglinux on 2011-01-16
If you have just copied the boomkark.htm from your old profile, then you are out of luck,  because Firefox doesn't use that file to store bookmarks since version 3.

Firefox stores bookmarks in the database file places.sqlite. However it can still import bookmark.html files, if you have generated such file manually, via export or other method. 

To import, you need to access the bookmark "import and backup" feature of the Bookmark Manager. Firefox also creates regular backups, saved as json files, that you can restore using the same tool.

---

### Post by buteobuteo on 2011-01-17
Will try that later, thank you both for nicely detailed info.

---

### Post by ProNux on 2011-04-29
I have Firefox 4 under Natty.  There is no "Organized Bookmarks" menu.  How to do?  I have done this in Windows 7, now I cannot on Ubuntu.

---

### Post by lovinglinux on 2011-04-29
> **ProNux said:**
> I have Firefox 4 under Natty.  There is no "Organized Bookmarks" menu.  How to do?  I have done this in Windows 7, now I cannot on Ubuntu.

Click "Bookmarks >> Show All Bookmarks" in Firefox menu.

---

### Post by ProNux on 2011-04-29
> **lovinglinux said:**
> Click "Bookmarks >> Show All Bookmarks" in Firefox menu.
Ah now I see the elusive "Import and Backup" menu on top.  Thanks man.

---

### Post by Sezmeralda on 2011-06-22
> **ProNux said:**
> Ah now I see the elusive "Import and Backup" menu on top.  Thanks man.

This stymied me for a good five minutes 'till I realised I had to maximise the window in order to see the menu options!

---

