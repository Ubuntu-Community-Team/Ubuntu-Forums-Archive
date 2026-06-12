---
title: "Installing 6.06 over 5.10, how?"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Chappy7777 on 2007-03-15
I installed 5.10 because that's the version I had. being on dialup I was not into downloading Dapper. Then I bought a book so I could start using Breezy, and in the book was a CD with 6.06 on it. 

Question: what is the easiset way for a noob to install 6.06? I don't suppose it's as easy as inserting the CD and clicking on install. Or is it?

Please let me know asap since there is not much point in working on 5.10 just because it's the version I have. I am assuming that Dapper is worth the install, since it's a year or more newer than Breezy. 

Again, whatever is the quickest and easiest, since I am real new to this. But now that I have gotten online, I feel like I've jumped a hurdle, and am enjoying learning this OS!

Thnx all,

Chappy

---

### Post by Kateikyoushi on 2007-03-15
If downloading is troublesome you could wait one month that's when the newest version of ubuntu comes out.

To upgrade you can do it with the updatemanager via internet must take a while with dialup, or with the alternate install cd which will upgrade only the packages it contains. Could also reinstall the whole system from thhe 6.06 cd or 6.1.
Then I would recommend to make a /home partition so you do not loose any of your settings while you upgrade, more info about how to do this can be found here. [LINK]("http://www.psychocats.net/ubuntu/separatehome")
If you have an almost unchanged install cd proceed to reinstall without it, as you loose nothing.

---

### Post by Kateikyoushi on 2007-03-15
Sorry Double post.

---

### Post by Chappy7777 on 2007-03-16
Bump

---

### Post by esaym on 2007-03-16
Well I don't know how you have your partitions setup but I have a separate partition for root (/) and home (/home).  Although I have not done an upgrade yet I plan on deleting the user directory out of home (/home/yourusername) and then formating the root partition.  Make sure not to format your home partition because this is where all your data files  (music,pics,videos) *should* be.  Then just install as normal.

All this can be done with the live cd.  Boot live cd.  Mount the hard drive.  Delete the user directory from /home.  Start the installer.  Point the installer to the proper partitions.  Format root.  DONT format home.  Install.  Ta da!

Thats how I am going to do it.  Anyone feel free to comment.  That will give you a FRESH new version.  No bugs or anything from upgrading.  :KS

Of course with that method the draw back is you will have to reinstall any apps that you might have downloaded from the internet.

---

### Post by zvacet on 2007-03-17
[https://help.ubuntu.com/community/DapperUpgrades?highlight=%28dapper%29%7C%28upgrades%29]("https://help.ubuntu.com/community/DapperUpgrades?highlight=%28dapper%29%7C%28upgrades%29")
Or maybe you can wait for month and download(or get from friend,or...)Fiesty.

---

