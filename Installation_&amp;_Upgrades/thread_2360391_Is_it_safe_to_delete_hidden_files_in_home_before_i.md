---
title: "Is it safe to delete hidden files in home before installing new version of Ubuntu?"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by aridus on 2017-05-04
My hard drive has two partitions: one on which I stall root, and a second (much larger) which contains my home folder: this allows me to install a new version of Ubuntu without having to overwrite my personal documents. I choose these options under 'Do something else' when installing Ubuntu. 

However, some items that pertain to earlier versions of Ubuntu or to other matters (such as having installed gnome shell, experimented with it, and then deleted it) seem to linger - presumably amongst the many hidden folders and files. This has resulted (in installing 17.04) in a number of niggling matters that I would like to resolve.

My question: is it safe to delete all of the hidden files and folders and then install Ubuntu 17.04? I realize that I will need to reinstall any software that I require, that any settings for Ubuntu or other software will most likely be deleted, and that any stored e-mail and settings (in my case in Evolution) will be lost. But, other than these matters, is there any reason why I should not delete all of the hidden files and folders?

Many thanks!

---

### Post by ian-weisser on 2017-05-04
It's usually safe enough.

Consider archiving (renaming/moving/backing up) the files until the replacement is running smoothly.

---

### Post by mastablasta on 2017-05-04
install with something else to root and home (in the same way as the first time) only this time do not format the home partition. this will keep all data there, while various configs will be overwritten with default ones. 

if the reis any important data on home, then backup it up first.

---

### Post by aridus on 2017-05-04
Thank you for the advice ian-weisser and mastablasta. The documents (i.e. all non-hidden folders and files) in my home partition are backed up. I will now also make a backup of all hidden folders and files, in case I need anything later, and I will then reinstall 17.04 to the root partition as usual.

---

### Post by kansasnoob on 2017-05-04
Rather than delete them I'd rename them. Some of the hidden files are app specific, like .mozilla = Firefox, .thinderbird = Thunderbird, etc. And .config contains settings for Opera, Chrome, etc that you may wish you'd kept. I either use a format like .mozilla_OLD or make them date specific like .mozilla_20170504.

---

### Post by aridus on 2017-05-05
Thank you for the various wise words of advice. I am reporting back that I successfully copied all hidden files and folders to a separate location, deleted the originals, and then reinstalled Ubuntu to my root partition. The system is now much better, with all the odd glitches gone. 

I ran into a few problems along the way, which I will report: It was not possible to delete two hidden folders (.config and .gvfs) as Ubuntu seems to need them whilst it is functioning. Upon the first reboot there were a few oddities (odd top bar icons and an old background wallpaper) but I solved this by renaming these two folders, deleting the originals, and then rebooting.

In my preparations I would have preferred to rename the previous hidden folders and files but there were a lot of them and I didn't have the patience to do it (I'm sure there is a command line way to do this but I couldn't figure it out). 

The only hidden folder that I felt the need to restore to its original location for the new installation was .zotero, which contained my installation of Zotero. I have now deleted all of the other old hidden files and folders.

---

### Post by mastablasta on 2017-05-05
it might come in handy.

bulk rename CLI in linux: [https://unix.stackexchange.com/questions/1136/batch-renaming-files](https://unix.stackexchange.com/questions/1136/batch-renaming-files)

bulk rename GUI in linux: [http://www.webupd8.org/2016/03/quickly-batch-rename-files-in-linux.html](http://www.webupd8.org/2016/03/quickly-batch-rename-files-in-linux.html)

---

### Post by aridus on 2017-05-05
Many thanks: these links are very useful, especially as I need to go through the same process with another computer!

---

