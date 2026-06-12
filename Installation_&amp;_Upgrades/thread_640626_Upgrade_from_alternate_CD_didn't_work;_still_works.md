---
title: "Upgrade from alternate CD didn't work; still works now but update problems"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by stevecro on 2007-12-14
Hi,
1) Downloaded the alternate CD and checksummed it, 2) burned it to a CD with K3B (from a SuSE/KDE machine, where I verified it on burn), 3) brought CD to other machine with a Ubuntu installation (where it checked good with with the check cd menu choice from Ubuntu when i started to boot it), 4) inserted it while up in Ubuntu (7.04) and the "upgrade volume detected" box came up, and here is where it gets interesting. 

Box said that a distribution volume with software packages had been detected and asked me if I wanted to a) start package manager or b) run upgrade (or cancel). Regardless of which one I choose, I get a similar outcome. After telling it that it may search internet for latest files, it searches disk for index files and then error messages come up saying things like: a) "Cannot add CD", b) unable to locate package files, c) that I should check whether or not I have a real Debian or Ubuntu CD, and d) update is aborting and original state will be restored. (When doing it the Package Manager way it says no packages selected.) 

Tried running the CD in both of my CD drives but that doesn't help. (Tried this because error message started with a strange "E:".) I'm puzzled why the system would detect that I have something usable for upgrade when the CD first spins up but then doesn't recognize it any more and can't find what it needs on it when it goes to do the upgrade, but that's not the end of it.

Now when I go to do the daily updates for my (still) 7.04 (never having gotten this upgrade to work), instead of saying that I have the normal 2 or 5 or whatever updates waiting, now it says I have 581 (which it wants to do for me with a 241 meg download) (just what I wanted to avoid in the first place from this machine by making the CD). It says not all updates can be installed, run a partial upgrade to install as many updates as possible, and that this could have been caused by (among other things like unofficial software (?) (all I've ever done is regular Ubuntu update and package manager downloads)) -- "a previous upgrade which did not complete"

Have tinkered with various Linux installs and upgrades now and then for several years now (just got done upgrading a SuSE 10.0 to 10.3 from disks with no problems at all), but this one I cannot figure out. Any help is appreciated. Thanks!

---

### Post by Pumalite on 2007-12-14
Upgrading using the alternate CD/DVD

Use this method if the system being upgraded is not connected to the Internet.

   1. Download and burn the alternate installation CD.
   2. Insert it into your CD-ROM drive.
   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4. Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesu "sh /cdrom/cdromupgrade"

---

### Post by stevecro on 2007-12-14
Hello and Yes,

I've already read what you've posted here on Ubuntu's pages. At step 3. the upgrade dialog/box did come up and that's exactly what I did ("follow the on-screen instructions"); which caused it to churn for a minute or two ("Preparing upgrade", "Modifying software channels", then "Searching for index files"...) until it bombed and gave me the error messages I described above. (Didn't use one of the last two commands because the upgrade dialog/box did come up.) Thanks anyway for your reply! S

---

### Post by Pumalite on 2007-12-14
Do md5sum on your iso, burn a new CD, download a new iso if necessary.

---

### Post by stevecro on 2007-12-14
I did md5sum my iso when I downloaded it and it matched the value from Ubuntu's web page; will try burning again with different machine and software and will try upgrade again tonight and post my result tomorrow; thanks...S

---

### Post by stevecro on 2007-12-15
Replying to myself (?) or to the thread, I guess... Just wanted to post progress and say thanks for suggestions received. I did burn a new CD from my md5sum'd iso, with different machine and burning software; got exactly all the same errors. Concerned that now my daily updating was broken, decided to try internet upgrade (that I had been trying to avoid). Had no idea how long my download would be on my entry-level DSL. Ran and checked periodically overnight. Best estimate is that download (only?) took about 5 hours (sigh of relief!). Everything seems to have worked as I write this, including extra Nvidia driver install. (Even prompted me to keep my already-customized ntp conf file!), I guess I was fortunate; thanks again all who read my posts...S

---

### Post by Pumalite on 2007-12-15
Good for you!

---

