---
title: "upgrades + scripts + firefox bookmarks"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by kabanta on 2006-06-14
I'm looking for suggestions about how to automate the porting of existing firefox bookmarks when moving to a new install.

My first intuition was to do what I do for a lot of the settings I save and re-use: create a symlink to my own firefox bookmarks.html

```
ln -s /my-settings/firefox/bookmarks.html .mozilla/firefox/UNIQUE/bookmarks.html
```
This doesn't work because firefox doesn't seem to want to follow symlinks. 

Another option would be to copy rather than symlink. But this means two copies of bookmarks file - so, extra work to keep them in sync.  Also it would also require some extra work because each install of firefox generates a different value for name of UNIQUE directory.

Any suggestions for this? (Or perhaps I am missing the easiest solution: is there some way in firefox to specify a different defaut location for  bookmarks? And if so, any problems if they are not kept in the UNIQUE folder with other firefox profile files?)

thanks

---

### Post by Phlosten on 2006-06-14
Have you tried the Google Sync extension?

[http://www.google.com/tools/firefox/browsersync/index.html](http://www.google.com/tools/firefox/browsersync/index.html)

---

### Post by kabanta on 2006-06-15
[QUOTE=Phlosten]Have you tried the Google Sync extension?[/QUOTE]

No, but it's good to know about it. thanks for the pointer.

In general, I would prefer some script/solution that I make, so unless I hear other solutions, I'll probably do something with rsync, etc.

---

