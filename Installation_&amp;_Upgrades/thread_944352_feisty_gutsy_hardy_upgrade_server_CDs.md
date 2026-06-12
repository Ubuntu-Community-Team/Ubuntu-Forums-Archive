---
title: "feisty gutsy hardy upgrade server CDs"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by ptolemytoo on 2008-10-11
Hi all

I'm trying to upgrade my Feisty Server 7.04 to 8.04. I've just received my copy of Hardy Heron on CD. Out here in the Third World, we don't have unlimited bandwidth so doing a apt-get dist-upgrade is not an option. That's why I ordered the disk.

I discovered that I could not upgrade directly from Feisty to Hardy when I ran the "cdromupgrade" shell script. Fortunately I had a copy of Server 7.10 so I tried to run the same script thinking I will upgrade to Gutsy and then to Hardy. Well, there was an error as follows:
---Start---
root@plato:~# /mnt/cdrom/cdromupgrade
can't load DistUpgradeViewGtk (No module named pygtk)
can't load DistUpgradeViewKDE (No module named qt)

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log ur
report. The upgrade aborts now.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

File "/tmp/tmp.XIUHlx4761/gutsy", line 59, in <module>
app.run()

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1346, in run
self.fullUpgrade()

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1234, in
fullUpgrade
if not self.prepare():

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 320, in
prepare
'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)
---End---

There is no file called: /etc/apt/sources.list.distUpgrade

The file: /var/log/dist-upgrade/apt.log is empty.

The file /var/log/dist-upgrade/main.log reads as follows:
---Begin---
2008-10-10 20:07:58,128 INFO release-upgrader version '0.81' started
2008-10-10 20:07:58,203 WARNING can't import view 'DistUpgradeViewGtk' (No module named pygtk)
2008-10-10 20:07:58,274 WARNING can't import view 'DistUpgradeViewKDE' (No module named qt)
2008-10-10 20:07:58,555 DEBUG lsb-release: 'feisty'
2008-10-10 20:07:58,557 DEBUG _pythonSymlinkCheck run
2008-10-10 20:07:58,757 DEBUG checkViewDepends()
2008-10-10 20:07:58,771 ERROR not handled expection:
Traceback (most recent call last):

File "/tmp/tmp.XIUHlx4761/gutsy", line 59, in <module>
app.run()

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1346, in run
self.fullUpgrade()

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 1234, in fullUpgrade
if not self.prepare():

File "/tmp/tmp.XIUHlx4761/DistUpgradeControler.py", line 320, in prepare
'Yes'

TypeError: askYesNoQuestion() takes exactly 3 arguments (4 given)
---End---

Any advice will be appreciated.

Regards

Harry

---

### Post by ptolemytoo on 2008-10-12
Does this mean nobody has a solution to my problem? Can anyone advise me as to where I can go for help?

I'm stuck

Thanks

Harry

---

