---
title: "Amarok 1.4 problems."
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by Taintedhero on 2006-10-22
I have been using Songbird as my primary Music player for some time now.  However I decided that Sonbird Crashes is simply not stable for Daily Use.  So I decided that Amarok was my next option having used it before on SUSE.  So after trying to install it through Synaptic I started the program.  Immediatly I got an error Message and a splash screen.  The error told me dcopserver was not started. However the program continued loading. Then loaded another errors telling me

"Malformed URL
file:///"

Oh well. 
From there it sent me to the First-Run Wizard.  Ok. Now my folder view was empty but. Oh well right.  I breezed through the Wizard and clicked finish.  Finally. Amarok should be starting! 

But it dident.

Instead I got this final error message.

"
Amarok could not find any sound-engine plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.
"

I have no idea what to do from here. 

Please. Help!

I am running Dapper Drake 6.06 btw.

---

### Post by Gryphin on 2006-10-23
Well, I am running Egdy Eft RC, and I have the same problem. The temporary solution seems to be running Amarok in terminal with superuser privileges. This way works for me, still I'd like to know how to run it 'regular' way:-k

---

