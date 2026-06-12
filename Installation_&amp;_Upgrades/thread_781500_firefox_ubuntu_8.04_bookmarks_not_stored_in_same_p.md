---
title: "firefox ubuntu 8.04 bookmarks not stored in same place anymore"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by vermoos on 2008-05-04
I upgraded to 8.04 and found that firefox bookmarks are now stored in sessionstore.js instead of bookmarks.html

bookmarks.html is still there in .mozilla/xxx.default but is not used for the same purpose: don't know if its used at all in 8.04 because bookmarks data is now saved in sessionstore.js 

Anybody know a way of migrating urls from bookmarks.html to sessionstore.js, preferably without manual editing?

other than that small annoyance, ubuntu keeps on getting better and better (albeit slowly) 

all unames are put in the fuse group now - handy if you use encfs to encode a partition

rock on ubuntu!

---

### Post by Pumalite on 2008-05-04
You can still copy bookmarks.html to Firefox

---

### Post by vermoos on 2008-05-04
yeah - i know, the point is, when i copy bookmarks.html to the usual location, firefox does not pick up on them, because it now stores the urls in the .js file (mentioned above) and does not 'look' at bookmarks.html

easiest way around it i have found is to open my old .html file in firefox and search it, then migrate each bookmark one by one, but its not ideal

'instant email verification' is fantastic!

---

### Post by Pumalite on 2008-05-04
I keep a copy of bookmarks.html in my /home, I then use Firefox>Organize Bookmarks>Import>Open. That's it.

---

### Post by DJ_Peng on 2008-05-04
Firefox 3 actually stores the bookmarks in a database. If you have a file of bookmarks that you want to bring into Firefox 3 you can simply use **Bookmarks > Organize Bookmarks > Import and Backup > Import HTML**. You can get some more info on the new Places method of storing bookmarks from [http://starkravingfinkle.org/blog/2007/05/firefox-3-bookmarks-on-places-lands/](http://starkravingfinkle.org/blog/2007/05/firefox-3-bookmarks-on-places-lands/) and the links on that post.

---

### Post by vermoos on 2008-05-04
Thanks guys - works a treat; job done

i just can't get my head around how integrated ubuntu is, when you scratch the surface...

---

