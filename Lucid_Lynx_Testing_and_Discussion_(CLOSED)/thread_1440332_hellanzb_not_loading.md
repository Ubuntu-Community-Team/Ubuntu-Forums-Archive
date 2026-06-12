---
title: "hellanzb not loading"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2010-03-27
i have noticed that sinc ethe last lot of updates hellanzb has stopped working.

terminal output 
/usr/lib/python2.6/dist-packages/twisted/internet/default.py:15: DeprecationWarning: twisted.internet.default is deprecated. Use posixbase or selectreactor instead.
  warnings.warn("twisted.internet.default is deprecated. Use posixbase or selectreactor instead.", category=DeprecationWarning)
Traceback (most recent call last):
  File "/usr/bin/hellanzb", line 14, in <module>
    from Hellanzb.Core import main
  File "/usr/lib/pymodules/python2.6/Hellanzb/Core.py", line 9, in <module>
    from Hellanzb.HellaReactor import HellaReactor
  File "/usr/lib/pymodules/python2.6/Hellanzb/HellaReactor.py", line 18, in <module>
    from twisted.internet.default import _NO_FILENO
ImportError: cannot import name _NO_FILENO

any ideas to fix this

---

### Post by IanW on 2010-03-27
I used to use "Lottanzb", a frontend for hellanzb, but I switched to "sabnzbd+" a while back. It runs as a daemon you can monitor from your web browser. I understand Lottanzb has recently switched to sabnzbd+ as a backend.

It can be set to watch a directory for nzb files (or zips of nzb files), and download them to a second directory. (ie: watch /home/nzb, save to /home/downloads).

[http://www.lottanzb.org/]("http://www.lottanzb.org/")
[http://sabnzbd.org/]("http://sabnzbd.org/")

---

### Post by terry_gardener on 2010-03-27
i have taken a look at sabnzbdplus and it looks good. 

i filed a bug report for the problem in hellanzb #549652 and someone has uploaded a patch to fix the problem but i dont know how to apply the patch. 

i think it has to be done to the source code and then compiled and the installed which i dont like to do.

i am going to give this new software a go and see what it is like, by looking through the menu options there is more to it than hellanzb. 

lottanzb is only going to using sabnzbd backend from version 0.6 which isn't out yet.

---

### Post by terry_gardener on 2010-03-27
installed the deb package from debian sid problem fixed with this updated package version.

[http://packages.debian.org/sid/hellanzb]("http://packages.debian.org/sid/hellanzb")

---

