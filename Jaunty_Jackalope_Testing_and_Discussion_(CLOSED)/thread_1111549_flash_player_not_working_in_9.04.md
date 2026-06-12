---
title: "flash player not working in 9.04"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chabos9 on 2009-03-30
I just recently installed Ubuntu 9.04, and so far its been ,much better than a live CD.  One problem though: flashplayer is not working.  Sites like you tube and flash game sites don't work, and just about all other video sites as well.  On youtube, it shows the video as fully loaded, but refuses to actually play the video.  I tried installing flash from both synaptics and the adobe site, and it still wont work.  My inter net is fast enough, and flash works fine in XP.  Can anyone offer some insight into this problem?  Thanks.

---

### Post by wolfen69 on 2009-03-30
completely remove flash. then do
```
sudo apt-get clean && sudo apt-get autoremove
```
then go back to the adobe site and download the tar.gz for flash. right click the tar.gz file and "extract here". then
```
gksudo nautilus
```
navigate to the folder that unpacking the tar.gz created. copy the libflashplayer.so file, then navigate to /usr/lib/mozilla/plugins directory and paste it there. restart firefox if open.

---

### Post by chabos9 on 2009-03-30
> **wolfen69 said:**
> completely remove flash. then do
```
sudo apt-get clean && sudo apt-get autoremove
```
then go back to the adobe site and download the tar.gz for flash. right click the tar.gz file and "extract here". then
```
gksudo nautilus
```
navigate to the folder that unpacking the tar.gz created. copy the libflashplayer.so file, then navigate to /usr/lib/mozilla/plugins directory and paste it there. restart firefox if open.

The one problem with this is that I'm a bash noob, so I'm having trouble with the pasting libflashplayer.so to /usr/lib/mozilla/plugins.  I tried using this syntax: mv libflashplayer.so ~/usr/lib/mozilla/plugins/libflashplayer.so, but it didn't seem to work.  Can some one tell me the proper way to paste in bash?

---

### Post by zika on 2009-03-31
> **chabos9 said:**
> The one problem with this is that I'm a bash noob, so I'm having trouble with the pasting libflashplayer.so to /usr/lib/mozilla/plugins.  I tried using this syntax: mv libflashplayer.so ~/usr/lib/mozilla/plugins/libflashplayer.so, but it didn't seem to work.  Can some one tell me the proper way to paste in bash?
let's assume You unpacked Your libflashplayer.so on Desktop
```
cd /opt
sudo mkdir flash
cd flash
sudo mv ~/Desktop/libflashplayer.so /opt/flash/libflashplayer.so (*)
cd /usr/lib/mozilla/plugins
sudo ln -s /opt/flash/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
cd ~/.mozilla/plugins
[COLOR=DarkRed][I](create if it does not exist:
cd ~/.mozilla
sudo mkdir plugins
cd plugins)[/I][/COLOR]
sudo ln -s /opt/flash/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```this way when newer flash plugin comes You have to repeat only line with (*) on the end ...

if You want to do it with nautilus You have to start it with root privileges (Alt-F2:gksu nautilus) and click, select, copy, paste and navigate along the route given above.
**be careful, with root privileges You can make havoc ... **:)

---

### Post by jfernyhough on 2009-03-31
--edit
So i re-red the original post. What I wrote doesn't make much sense any more, but I'll leave it here just in case. ;)

***

Have you tried a simple

$ sudo aptitude purge flashplugin-nonfree
$ sudo aptitude install flashplugin-nonfree

?

It's worked for me three times when libflashplugin.so mysteriously disappeared...

---

### Post by babs51 on 2009-04-01
Hi,
I wasn't able to get flash working in firefox using the above suggestions, however, I downloaded seamonkey and it works in it.

---

### Post by pt123 on 2009-04-02
> **jfernyhough said:**
> --edit
Have you tried a simple

$ sudo aptitude purge flashplugin-nonfree
$ sudo aptitude install flashplugin-nonfree


Thanks that did it,

I am hoping this was because it was an upgrade from Ibex. That said it should really ask if you want to reinstall these proprietary applications.

---

### Post by rburkartjo on 2009-04-02
pt123 tks for the info worked like a charm for me

---

### Post by gcvisel on 2009-04-05
> **pt123 said:**
> Thanks that did it,

I am hoping this was because it was an upgrade from Ibex. That said it should really ask if you want to reinstall these proprietary applications.

Didn't work for me.  Something still doesn't work.

---

### Post by gcvisel on 2009-04-05
> **gcvisel said:**
> Didn't work for me.  Something still doesn't work.

Oops!  I tried it again (with Firefox closed!) and it worked!  THANKS!

---

### Post by psyke83 on 2009-04-06
> **wolfen69 said:**
> completely remove flash. then do
```
sudo apt-get clean && sudo apt-get autoremove
```
then go back to the adobe site and download the tar.gz for flash. right click the tar.gz file and "extract here". then
```
gksudo nautilus
```
navigate to the folder that unpacking the tar.gz created. copy the libflashplayer.so file, then navigate to /usr/lib/mozilla/plugins directory and paste it there. restart firefox if open.

Please, don't advise users to install from a tarball. This circumvents the system's package management, which will inevitably cause problems (in this case flash will be unable to update itself, and future attempts to install flash "the proper way" may fail).

Installing from the repository will ensure that Flash is maintained properly (even through distribution upgrades)... and before anyone counters with the argument "but the repository version doesn't work for me", the answer is usually because a manual installation has caused a conflict on your system.

---

### Post by zika on 2009-04-06
> **psyke83 said:**
> Please, don't advise users to install from a tarball. This circumvents the system's package management, which will inevitably cause problems (in this case flash will be unable to update itself, and future attempts to install flash "the proper way" may fail).

Installing from the repository will ensure that Flash is maintained properly (even through distribution upgrades)... and before anyone counters with the argument "but the repository version doesn't work for me", the answer is usually because a manual installation has caused a conflict on your system.
flashplugin-nonfree is still 32-bit (as far as I know) so that might be the valid reason for 64-bit users ...
I agree with You in the sense that flashplugin-nonfree is more reliable for less demanding users but You must agree that there is a difference in quality of use for more demanding users on 64-bit installations ...
we have to have a way of circumventing the fact that 64-bit plugins exists and is easily installable but is not yet offered through regular ways ...

---

