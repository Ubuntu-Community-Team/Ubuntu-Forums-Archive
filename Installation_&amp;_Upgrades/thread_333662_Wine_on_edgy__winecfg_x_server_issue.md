---
title: "Wine on edgy  winecfg x server issue"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by HerrGray on 2007-01-07
Hi,

Linux noob here..... I have a 866 pentuim III running on ubuntu 6.10 
nivida drivers are installed and running 
I have installed the latest wine release using apt-get

when I attempt to open winecfg in shell I get this error:

err: imagelist: ImageList_ReplaceIcon no color!
err: imagelist: ImageList_ReplaceIcon no color!
err: imagelist: ImageList_ReplaceIcon no color!
err: imagelist: ImageList_ReplaceIcon no color!

Application tried to create window, but no driver could be loaded make shure your X server is running and check your $DISPLAY is set correctly

I have been fighting with this for two days..... ](*,) 

any help would be greatly appeciated

Thanks

Gray

---

### Post by HerrGray on 2007-01-08
Hi,

found the answer here: 

> **runkidrun said:**
> I just installed WINE through Automatix. Here are some steps to reaching the directory to which it was installed:

1.Click Places, then select "Computer"
2.Once a window pops up select "File System"
3.The you will see lots of folders...select "usr"
4.Then you will see more folers...select "bin"
5. Then you will have a ton of files and folders in this directory....scroll down until you see "winecfg"...then double click it and select run.
6. this configures wine.
7. then click "winefile" and select run.
8. from there you can navigate to the directory you have the file stored....
**Tip**: you might want to create a shortcut on the desktop to make it easier (right click create launcher) then browse to the directory that was shown above..

:rolleyes: 

worked like a charm....


Gray

---

