---
title: "Nicotine can't start"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by kanyi on 2007-01-09
Hi, I have problem with the Edgy and the Nicotine:

(the Python version is 2.4, all requied package is installed. But isn't  working :-(  )

-desktop:~$ nicotine
Traceback (most recent call last):
  File "/usr/bin/nicotine", line 147, in ?
    from pynicotine.gtkgui import frame
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/frame.py", line 23, in ?
    from downloads import Downloads
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/downloads.py", line 5, in ?
    from transferlist import TransferList
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/transferlist.py", line 12, in ?
    class TransferList:
  File "/var/lib/python-support/python2.4/pynicotine/gtkgui/transferlist.py", line 50, in TransferList
    status_tab = [
  File "/var/lib/python-support/python2.4/pynicotine/utils.py", line 39, in _
    tr_cache[s] = gettext.gettext(s)
  File "/usr/lib/python2.4/gettext.py", line 568, in gettext
    return dgettext(_current_domain, message)
  File "/usr/lib/python2.4/gettext.py", line 532, in dgettext
    codeset=_localecodesets.get(domain))
  File "/usr/lib/python2.4/gettext.py", line 480, in translation
    t = _translations.setdefault(key, class_(open(mofile, 'rb')))
  File "/usr/lib/python2.4/gettext.py", line 177, in __init__
    self._parse(fp)
  File "/usr/lib/python2.4/gettext.py", line 301, in _parse
    plural = v[1].split('plural=')[1]
IndexError: list index out of range

---

### Post by 23meg on 2007-01-09
Is it Nicotine 1.2.4 from the Ubuntu repositories?

---

### Post by kanyi on 2007-01-10
Yes, it is the Nicotine 1.2.4.1-1 from the ubuntu repository.

---

### Post by dunomous on 2007-07-09
Please try this for your fix. It worked for me:

Delete *.db (all files ending with .db) files from your ~/.nicotine/ directory. Back up your files just in case!!

This fix was found from [here]("https://bugs.launchpad.net/ubuntu/+source/nicotine/+bug/93251").

---

### Post by dixelpixel on 2007-07-10
HI,

Thanks for all helpful suggestions so far. Now for the completely noob question:
Where, on a typical Feisty installation do I find the Nicotine directory?

Sorry to dumb down the discussion, but all help will be immensely appreciated.

..dxpx..

---

### Post by dixelpixel on 2007-07-10
OK, I get it. You meant the download directory for nicotine.

Sorry about that. :-)

..dxp..

---

### Post by dunomous on 2007-07-10
Don't worry about dumb questions, all of  us had them and asked them enough for us to have no room to judge!  :D

Anyway, here's the step by step to help you out:

> 

**1)** Places -> Home Directory (or folder).

**2)** Press Ctrl+h to show hidden folders (folders that have a dot in front of them). 

**3)** Find the ".nicotine" folder and enter it.

**4)** In that folder, you'll find a bunch of files ending with ".db" as well as perhaps a config.old file and an actual  config file. If you don't see a config file, that's trouble and should be told to us since that file is critical. If you don't see a config.old file, then don't give it a second thought.

**5)** Create a folder on your desktop called "PlaceHolder" without the quotes.

**6)** Make sure Nicotine is turned off.

**7)** Select (just select all of them, then by pressing and holding the Ctrl button, click all files that **are not** .db files to unselect them) all the .db files and move them to the PlaceHolder folder. This should leave the .nicotine folder with only the config file(s) remaining.

**8)** Start Nicotine.



If all starts well, then go ahead and delete the PlaceHolder folder. The fix has worked! If not, repost back here so we can further asses the problem. Thanks!

---

### Post by dixelpixel on 2007-07-10
Thanks!!

OK, I followed the guide and deleted all the .db files. 

However, I still cannot get up and running before I can solve the problem described in [this thread]("http://ubuntuforums.org/showthread.php?t=484310&highlight=nicotine+help")

Someone suggested a solution that didn't work for me so I hope perhaps you could have a look at the thread as well?

Many thanks,

..dxp..

---

### Post by dunomous on 2007-07-10
> **dixelpixel said:**
> Thanks!!

OK, I followed the guide and deleted all the .db files. 

However, I still cannot get up and running before I can solve the problem described in [this thread]("http://ubuntuforums.org/showthread.php?t=484310&highlight=nicotine+help")

Someone suggested a solution that didn't work for me so I hope perhaps you could have a look at the thread as well?

Many thanks,

..dxp..

Ah. First, the guy who gave you the "suggestion" is a spammer. So please either change emails or just expect a lot of spam soon. I'm sorry :( *The mods have removed him though. I much appreciate their quickness in response!*

Anyway, about your problem.

Apparently, Nicotine was having errors when the config file's settings were set as "none." So, the developer went back and made some settings to fix the problem.

What this means to you is that you may want to either enter in configure settings (like which server you connect to, mainly) or just do a fresh install of nicotine+ again so you are sure that it is making a clean and correct config file. When you uninstall, make sure both the Nicotine folder and the .nicotine folder have been removed/deleted. This is really the long and almost unnecessary way of doing it, but it has the greatest chance of making sure everything is in working order.

Does Nicotine load now for you? I forgot to ask if you are using Nicotine+ 1.2.8.

---

### Post by csabimeta on 2007-08-03
> **dunomous said:**
> Don't worry about dumb questions, all of  us had them and asked them enough for us to have no room to judge!  :D

Anyway, here's the step by step to help you out:



If all starts well, then go ahead and delete the PlaceHolder folder. The fix has worked! If not, repost back here so we can further asses the problem. Thanks!

Nicotine won't start up for me. I launch it, and nothing happens. I installed 1.2.8, but I experienced the same problem. I'm using Kubuntu edgy. In my home folder isn't any /.nicotine folder. Where is it then? Please help me!

---

### Post by toolazy2work on 2008-04-15
> 
1) Places -> Home Directory (or folder).

2) Press Ctrl+h to show hidden folders (folders that have a dot in front of them).

3) Find the ".nicotine" folder and enter it.

4) In that folder, you'll find a bunch of files ending with ".db" as well as perhaps a config.old file and an actual config file. If you don't see a config file, that's trouble and should be told to us since that file is critical. If you don't see a config.old file, then don't give it a second thought.

5) Create a folder on your desktop called "PlaceHolder" without the quotes.

6) Make sure Nicotine is turned off.

7) Select (just select all of them, then by pressing and holding the Ctrl button, click all files that are not .db files to unselect them) all the .db files and move them to the PlaceHolder folder. This should leave the .nicotine folder with only the config file(s) remaining.

Start Nicotine.



That worked like a charm.  thx for the info.

---

