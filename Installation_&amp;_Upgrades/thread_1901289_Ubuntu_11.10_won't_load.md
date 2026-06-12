---
title: "Ubuntu 11.10 won't load"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by thenovelist on 2011-12-28
I have had to reload Ubuntu as I had a problem with a crash.  I fortunately had a copy of Windows with Macroreflect and reloaded windows from June 2011.  I wanted to load Ubuntu within Windows which I had done before onto another partition.  I had no problem last time before the crash doing this.  I loaded Ubuntu fine and restart windows.  I then let it load Ubuntu when it restarts, but when it has finished it restarts and won't go to the OS.  I try to get the cursor to Ubuntu but it won't allow me to do it, even though Ubuntu is name at the boot.  So I have no choice but to open up Windows.  I have deleted and re-started several times, but alas without success.  Has anyone any idea how I can resolve this problem.  Mean while I will keep trying but could do with some pointers if you have any.  Thanks

---

### Post by Paddy Landau on 2011-12-28
I'm not entirely clear about what you are saying.

You are using WUBI, is that right? WUBI is a different kettle of fish from a native installation.

You say, "I have deleted and re-started several times". Do you mean you uninstalled WUBI and restarted? Or did you delete something else?

---

### Post by thenovelist on 2011-12-28
I am using WUBI and not very successfully and have Win7 64bit.  I had success before the crash and used it constantly, but alas not now.  And yes WUBI is what I have been deleting and reloading.  Thank you for your reply

---

### Post by Paddy Landau on 2011-12-28
Hmm...

It sounds as though your boot entry has been corrupted after restoring Windows. I don't know Macroreflect; I'm guessing it is a way to restore a previous set-up?

Here is my suggestion.

[LIST]
[*]Uninstall WUBI (and restart).
[*]Fix your boot record using Windows. I'm not sure how to do that in Windows, but you could try [Microsoft's recommended method]("http://support.microsoft.com/kb/927392"), its [installation disk]("http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/"), or [EasyBCD]("http://download.cnet.com/1770-20_4-0.html?query=easybcd&tag=pfindersrch&searchtype=downloads&filterName=platform%3DWindows&filter=platform%3DWindows&priceFilterDL=All&category=All").
[/LIST]
Once Windows is working and booting properly *without* WUBI, then try installing WUBI again.

---

### Post by thenovelist on 2011-12-28
Thanks for your help.  I realised the cursor wasn't working and eventually changed the keyboard USB to another connection on the back of the computer and it had resolved it.  Frustrating at the time, but now resolved which is great news.  Tx for all your help

---

### Post by Paddy Landau on 2011-12-29
> **thenovelist said:**
> I realised the cursor wasn't working and eventually changed the keyboard USB to another connection on the back of the computer and it had resolved it.
Sometimes, the BIOS is set to ignore USB keyboard and mouse -- I have seen it called the "legacy" option. If you turn it on (assuming that is the problem), you'll be able to use your USB keyboard.

---

