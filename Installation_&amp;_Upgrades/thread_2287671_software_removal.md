---
title: "software removal"
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by Frank_Callo on 2015-07-21
Hi.

I tried to install a program called virtual DJ.  This did not come from software center.  So, the program decidededly does not work.  I open it and the whole desktop starts to blink.  The program required instalation of Wine, which I installed (trouble installing wine as well).  So, since Virtual DJ doesn't work, I want to remove it.  But since it didn't come through software center which removes programs for you, I don't know how to get this unwanted software off my box.  Any advice?

Thanks

---

### Post by howefield on 2015-07-21
What version of Ubuntu are you using ?

in any event I believe you should be able to find an "Uninstall Wine Software" link in your Ubuntu application menus or search for it in the dash if you are using Unity.

---

### Post by grahammechanical on 2015-07-21
Virtual DJ is not compatible with the Linux operating system. There are versions for Windows and MacOS but not for Linux. So, how did you install it? Did you download a compressed file (ZIP) and then extract the contents into a folder? Did you then try clicking the setup.exe file?

If we use Wine to install a Windows program, then we can use Wine to uninstall it. Not all Windows programs work well under Wine but we cannot use Wine to run a Windows program unless we use Wine to install the program.

If all you have done is downloaded a zipped file and extracted it into a folder, then delete the file and the contents of the folder and then delete the folder. If you have done something more than that, then you have to tell us so that we have a clear understanding of the situation.

Regards

---

### Post by Frank_Callo on 2015-07-21
I installed it with wine as per the "install with wine" button.

---

### Post by earruda on 2015-07-21
@Frank_Callo, look the answers in here: [http://askubuntu.com/questions/101064/uninstall-a-program-installed-with-wine](http://askubuntu.com/questions/101064/uninstall-a-program-installed-with-wine)
They might help you.

---

### Post by deadflowr on 2015-07-21
Seeing as to you also seem to have a wine problem in this case I'd suggest actually throwing the baby out with the bath water and remove wine as well.

After you remove wine, simply delete the wine folder in your home folder.
It's a hidden folder so in the Files program click ctrl + h, or Menu >> view show hidden files/folders.

Looking at winedb the app is all over the place from gold to garbage.
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=1704](https://appdb.winehq.org/objectManager.php?sClass=application&iId=1704)

Seems certain version run well only with certain versions of wine.

You might look at re-trying with something like playonlinux.
PlayOnLinux is a wine fronmtend for ease of use.
It also allows you to install different versions of wine.
Basic reference here:
[http://wiki.playonlinux.com/index.php/Main_Page](http://wiki.playonlinux.com/index.php/Main_Page)

Playonlinux is in Ubuntu's software center.

Hope this helps.

---

### Post by v3.xx on 2015-07-21
Yes, playonlinux is a nice wine gui.

What version is this?  Only one gold rating.
[https://appdb.winehq.org/objectManager.php?sClass=application&iId=1704](https://appdb.winehq.org/objectManager.php?sClass=application&iId=1704)

---

