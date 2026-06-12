---
title: "Can't install activinspire. Promethean board software."
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2013-06-19
I need to install this and preferably without creating a windows partition. I need to use a Linux specific software with this board...

All the online and official instructions are: > sudo apt-get install libjpeg62

Then: > deb [http://activsoftware.co.uk/linux/repos/ubuntu](http://activsoftware.co.uk/linux/repos/ubuntu) precise oss non-oss

Then: > wget [http://www.activsoftware.co.uk/linux/repos/Promethean.asc](http://www.activsoftware.co.uk/linux/repos/Promethean.asc) &amp;&amp; sudo apt-key add Promethean.asc

and finally: > sudo apt-get update
sudo apt-get install activinspire activtools activdriver

Now, the problem is that apparently the repos don't work anymore, I tried changing them to raring, but no success. These instructions are for 12.10. What can I do to successfully install this?
Please help!

---

