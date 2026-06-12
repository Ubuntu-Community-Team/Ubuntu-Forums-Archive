---
title: "Amarok not recognising media."
date: 2010-02-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Elfy on 2010-02-17
Got the update yesterday and am at version 2.2.2.90.

Local collection now fails to register any media at all. Scanning appears to be working - at least it takes as long as normal ... 

Removing the config files and the temp files has no effect either.

Physically playing a playlist does result in it playing but without the librarry it is a bit lacking to say the least.

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)

---

### Post by Elfy on 2010-02-19
bump

---

### Post by mc4man on 2010-02-19
As mentioned on lp see the same (plus it continues to not exit cleanly.

Glancing at a debug, (similar to gst debugs - if you don't know the territory, well,  there's not much to glean..

This does show up early and is repeated when trying to open coll. and or scan

> amarok:    [ERROR!] Tried to perform escape() on uninitialized MySQL 
amarok:    [ERROR!] Tried to perform query on uninitialized MySQL 

The prev. version still works fine but that's not really an option of any value.

While there's no changelog avail. on packages.ubuntu, did locate it and it was massive with a lot about collection, ect...

---

### Post by Elfy on 2010-02-20
thanks I shall leave it gathering dust in the corner for the moment ;)

---

### Post by JCoster on 2010-02-20
Yeah I have the same problem too- on exit it jumped to 100% CPU usage (although I assume that this is because it was scanning for my collection?) and it didn't exit until I killed it in top...

We'll have to wait for the devs I guess..

---

### Post by Elfy on 2010-02-20
yep :) in the meantime I am playing guadaleque

---

### Post by mc4man on 2010-02-21
Got the collection back and proper exiting by either, -  it was fixed (had it reverted to prev. ver.) or by installing the mysql-sever package. (5.1)

There was no change to the amarok package ver. so maybe the msql install did the trick.

If so, just installed it, no settings change.

(based on reading the thru the applied patches for the 2.2.2.90 source

---

### Post by Elfy on 2010-02-21
installing 5.1 made no difference here.

---

### Post by mc4man on 2010-02-21
> installing 5.1 made no difference here. 

Hmm, it's working perfectly here now, no errors whatsoever in the debug - a few clips concerning scan (small coll. on this install
> 
amarok: BEGIN: void ScanManager::startFullScan() 
amarok:   BEGIN: void ScanManager::checkTables(bool) 
amarok:     BEGIN: void DatabaseUpdater::checkTables(bool) 
amarok:     END__: void DatabaseUpdater::checkTables(bool) - Took 0.34s 
amarok:   END__: void ScanManager::checkTables(bool) - Took 0.34s 
amarok:   BEGIN: void ScanManager::cleanTables() 
amarok:   END__: void ScanManager::cleanTables() - Took 0.044s 
amarok:   BEGIN: XmlParseJob::XmlParseJob(ScanManager*, SqlCollection*) 
amarok:     BEGIN: void ProgressBar::setDescription(const QString&) 
amarok:     END__: void ProgressBar::setDescription(const QString&) - Took 0.00014s 
amarok:     BEGIN: void CompoundProgressBar::addProgressBar(ProgressBar*, QObject*) 
amarok:       BEGIN: void ProgressBar::setDescription(const QString&) 
amarok:       END__: void ProgressBar::setDescription(const QString&) - Took 0.0002s 
amarok:     END__: void CompoundProgressBar::addProgressBar(ProgressBar*, QObject*) - Took 0.0032s 
amarok:     BEGIN: ProgressBar* ProgressBar::setAbortSlot(QObject*, const char*) 
amarok:        Setting abort slot for  "Scanning music" 
amarok:        connecting to  1abort() 
amarok:     END__: ProgressBar* ProgressBar::setAbortSlot(QObject*, const char*) - Took 0.0045s 
amarok:   END__: XmlParseJob::XmlParseJob(ScanManager*, SqlCollection*) - Took 0.0099s 
amarok:   BEGIN: virtual void XmlParseJob::run() 
amarok:      Checking for batch file in  "/home/doug/.kde/share/apps/amarok/amarokcollectionscanner_batchfullscan.xml" 
amarok:     BEGIN: QStringList MountPointManager::collectionFolders() 
amarok:     END__: QStringList MountPointManager::collectionFolders() - Took 0.0003s 
amarok:   END__: void ScanManager::startFullScan() - Took 0.4s 
amarok:    Setting up database 
amarok:   BEGIN: void DatabaseUpdater::createTemporaryTables() 
amarok:   END__: void DatabaseUpdater::createTemporaryTables() - Took 0.19s 
amarok:   BEGIN: void ScanResultProcessor::populateCacheHashes() 
amarok:   END__: void ScanResultProcessor::populateCacheHashes() - Took 0.0021s 
amarok:    Skipping file with uniqueid  "amarok-sqltrackuid://0038eb231d142807cda3291cd63ab5a5"  as it was already seen this scan, file is at  "/home/doug/Music/Knockin'_On_Heaven's_Door.mp3" , original file is at  "/home/doug/Music/06 - Knockin' On Heaven's Door.mp3" 
amarok:    Success. Committing result to database. 
amarok:   BEGIN: void DatabaseUpdater::cleanPermanentTables() 
amarok:   END__: void DatabaseUpdater::cleanPermanentTables() - Took 0.0011s 
amarok:   BEGIN: void ScanResultProcessor::copyHashesToTempTables() 
amarok:     BEGIN: void ScanManager::slotFinished() 
amarok:     END__: void ScanManager::slotFinished() - Took 0.035s 


Think I may do a re-build of the source later with a few minor changes and see if it it work properly on another install where it's currently broken. ( or if not  see if installing these packages works there also

packages installed

> Commit Log for Sun Feb 21 01:11:31 2010
Installed the following packages:
libhtml-template-perl (2.9-1)
mysql-server (5.1.41-3ubuntu6)
mysql-server-5.1 (5.1.41-3ubuntu6)
mysql-server-core-5.1 (5.1.41-3ubuntu6)


exact method was revert the 3 amarok packages to 2:2.2.2-0ubuntu1, install above, run amarok once, update amarok

---

### Post by Elfy on 2010-02-21
didn't revert the 3 amarok packages - possibly that would be it ;)

I'll have another go later when I have a bit more time

---

### Post by Elfy on 2010-02-21
yep, thanks mc4man that appears to work now :)

---

### Post by mc4man on 2010-02-21
Having fought thru a fresh lucid install and full update (current live cd is borked) this is what worked

Installed amarok2 - no collection, unclean exit

Installed the packages mentioned (which also install the mysql-client) - amarok2 works fine, exits cleanly

So the positive is technically you don't need to run the previous ver. first which would have pointed to a file(s) needing to be correctly written first before the new amarok would work (with the 5.1 client/server packages installed

Why it appears to need to server installed is unclear to me (know very little about amarok 2 and less about sql ), though I guess a temp workaround would be to have the server package(s) as a recommend.

Things that could be worth checking are, - after regaining amarok to remove some packages  and see if it breaks and or build amarok in the presense of add. -devs or remove one patch that stands out.

(or just let the amarok devs/maintainer square this up...

Myself will probably just use amarok 1.4 due to some capabilities unique to it.
(or install the [pana fork]("http://ubuntuforums.org/showthread.php?t=1400314&page=2") which can co-exist with amarok 2, best of both worlds..

---

