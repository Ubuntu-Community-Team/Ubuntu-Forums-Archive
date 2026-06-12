---
title: "Simpler way to add Ubuntu mirrors (e.g. adam internet's mirror filearena)"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by ahumin on 2008-11-06
i have read many posts on adding unofficial mirrors for updates/software in ubuntu. most instruct you to edit several lines in /etc/apt/sources.list
i think this is very clunky because you can't use the interface for System > Administration > Software Sources easily after doing so. the checkboxes in the first tab don't do what you think they're doing and the second tab becomes littered with entries for your mirror.

i wanted to add my local mirror to the official list and found an easier way in the process:
[LIST=1]
[*]open terminal
[*]type ```
gksudo gedit /usr/share/python-apt/templates/Ubuntu.mirrors
```
[*]scroll to your country code (for me it was **AU**)
[*]add a line to the end of your country's mirror list (i added **[http://filearena.net/pub/ubuntu/](http://filearena.net/pub/ubuntu/)**)
[*]save the file, close the editor and terminal
[*]open **System > Administration > Software Sources** from the main menu
[*]choose your new custom mirror in the **Download from** drop-down menu, then set your preferences
[/LIST]

your sources.list file is automatically updated. the mirrors file does get overwritten with a new version during updates or something, but your preferences that were saved in source.list are preserved as if you had edited it manually.

---

### Post by alibabahck on 2009-04-17
Thanks for the tip! Worked well.

---

