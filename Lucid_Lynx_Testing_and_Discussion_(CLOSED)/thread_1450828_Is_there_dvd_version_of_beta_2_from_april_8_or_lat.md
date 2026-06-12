---
title: "Is there dvd version of beta 2 from april 8 or later?"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-09
every site i check it said beta 2 but april 6 so what is going on here?
 
thanks in advance.

---

### Post by aviramof on 2010-04-10
still no news about dvd version of beta 2? i'm currently using windows seven just because there is no updated dvd version.

---

### Post by cariboo on 2010-04-10
Just out of curiosity, if you are running Beta 1 and you are fully up-to-date, why do a complete reinstall, as you've already got Beta 2.

---

### Post by jocko on 2010-04-10
April 8 or later? Most of the isos are dated april 6:th, because that's when they were actually made. The beta freeze was between  april 1:st and 8:th, so the final images could have been produced at any time during that period and still contain the same versions of all packages.

---

### Post by aviramof on 2010-04-10
ectually i formated everything because i had a problems with ati "Restricted [Hardware] Driver" not apperaing maybe because i tried to install fglrx source before or because of something eles i did. 
 
also i started heaving problems with the metacity update all the windows buttons dissapear the close and minimize and expend because i removed metacity and i was unable to reinstall it without uninstalling compiz. 
 
and also i wanted to see if you fixed the ubiqutity problem i had in the past the problem is that he create my partitions as sda5 and sda6 even thoughe i only have one more partition in this drive which is sda1 my windows server 2008 and just for the recored xubuntu ubiquity didn't had this problem when i tried it not long ago.
 
and since i already formated everything and erased the ext4 and swap partition i wanted to try and test the dvd version but 
i am not about to download and burn 4GB of dvd if it's 4 days old and it's date is before beta 2 was released at all.

---

### Post by grandtoubab on 2010-04-10
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by aviramof on 2010-04-10
thanks but this version is still 06-Apr-2010 23:04

---

### Post by Crunchy the Headcrab on 2010-04-10
It doesn't matter what the date of the install media is.  Nothing is going to be as up to date as a:

sudo aptitude update
sudo aptitude safe-upgrade

:guitar:

---

### Post by aviramof on 2010-04-10
yes it can it's called ubiquity and this is the ubuntu installer and because i want the dvd version there could a lot of other pacages updates and beside i want the most updated dvd version before i download and burn 4GB i don't want to have to update the installer via the live cd.
 
and i want to ensure as much as i can that the installer want create me sda5 and sda6 partitions again but sda2 and sda3 partitions.

---

### Post by Eib on 2010-04-10
> **cariboo907 said:**
> Just out of curiosity, if you are running Beta 1 and you are fully up-to-date, why do a complete reinstall, as you've already got Beta 2.

The problem is, some people can't even install beta1, because it simply freezes during boot. This image of beta2 hangs up as well on my main PC(works well on notebook). :(

---

### Post by jocko on 2010-04-10
> **aviramof said:**
> and also i wanted to see if you fixed the ubiqutity problem i had in the past the problem is that he create my partitions as sda5 and sda6 even thoughe i only have one more partition in this drive which is sda1 my windows server 2008 and just for the recored xubuntu ubiquity didn't had this problem when i tried it not long ago.
 
and since i already formated everything and erased the ext4 and swap partition i wanted to try and test the dvd version but 
i am not about to download and burn 4GB of dvd if it's 4 days old and it's date is before beta 2 was released at all.
"also i wanted to see if you fixed the ubiqutity problem"? Do you see any developer here? If you have a problem, file a bug report, that's where you'll get in contact wth the developers, not here.
But are you sure it's really a bug that the partitions are named sda5 and sda6 instead of sda2 and sda3?

When you want three partitions on a hard drive, there are basically two ways of doing it:

1. Make three primary partitions (which will be named sda1, sda2 and sda3).
**Problem:** A drive can only have a limited number of primary partitions (three or four, I'm not sure). So if you later decide you need to have one more partition when you already have the maximum number, it will be impossible to accomplish.

2. Make only one primary partition (sda1) plus one extended partition (sda2). In the extended partition, make two secondary partitions (sda5 and sda6). If you later decide you want to take some of the space from sda5 and/or 6 and make one (or how many as you like) more partitions, it will not be any problem.

So which way do you think is the default?  The one that creates problems or the one that just works?

If you think this is wrong, I think you just have to learn to live with it. Or partition your drive manually with only primary partitions if you are sure you will never need any more partitions.


> **aviramof said:**
> yes it can it's called ubiquity and this is the ubuntu installer and because i want the dvd version there could a lot of other pacages updates and beside i want the most updated dvd version before i download and burn 4GB i don't want to have to update the installer via the live cd.
 
and i want to ensure as much as i can that the installer want create me sda5 and sda6 partitions again but sda2 and sda3 partitions.

If you haven't read my earlier posts (in this thread and the beta 2 release thread):
The Beta 2 images were released on april 8:th, but they were produced on april 6:th.
Anything you find with a date that is newer than april 6:th is NOT a beta 2 cd/dvd, but rather an automatically built "daily" image that has undergone ZERO testing.

The beta 2 cd/dvd images has at least been tested for two days prior to their release, and the people that tested them found no serious problems with booting or installing on their machines (but I'm sure quite a few of the candidate images that were produced during the beta 2 freeze were rejected due to some serious problem).

So if you want a dvd image that is likely to not boot at all, not install properly or to have any other more or less serious problem, wait for a newer "daily" dvd and roll the dice. Or you can play it safe(r) and get the beta 2 dvd, which has at least been tested and is known to both boot and install properly for the few people who bothered to help testing it. During development "newer" does not always mean "better".

---

### Post by grandtoubab on 2010-04-10
> **aviramof said:**
> thanks but this version is still 06-Apr-2010 23:04
i am sorry too but here what I see
 Parent Directory                               -   
 MD5SUMS                   10-Apr-2010 13:43  107   
 MD5SUMS.gpg               10-Apr-2010 13:43  189   
 SHA1SUMS                  10-Apr-2010 13:44  123   
 SHA1SUMS.gpg              10-Apr-2010 13:44  189   
 SHA256SUMS                10-Apr-2010 13:45  171   
 SHA256SUMS.gpg            10-Apr-2010 13:45  189   
 lucid-dvd-amd64.iso       10-Apr-2010 13:33  4.0G  Install/live DVD for 64-bit PC (AMD64) computers (standard download)
 lucid-dvd-amd64.iso.zsync 10-Apr-2010 13:42  8.1M  Install/live DVD for 64-bit PC (AMD64) computers (standard download)
 lucid-dvd-amd64.jigdo     10-Apr-2010 13:33  248K  Install/live DVD for 64-bit PC (AMD64) computers (jigdo download)
 lucid-dvd-amd64.list      10-Apr-2010 13:34  174K  Install/live DVD for 64-bit PC (AMD64) computers (file listing)
 lucid-dvd-amd64.manifest  10-Apr-2010 13:08   69K  Install/live DVD for 64-bit PC (AMD64) computers (contents of live filesystem)
 lucid-dvd-amd64.template  10-Apr-2010 13:33  1.2G  Install/live DVD for 64-bit PC (AMD64) computers (jigdo template)
 lucid-dvd-i386.iso        10-Apr-2010 13:40  4.0G  Install/live DVD for PC (Intel x86) computers (standard download)
 lucid-dvd-i386.iso.zsync  10-Apr-2010 13:42  7.9M  Install/live DVD for PC (Intel x86) computers (standard download)
 lucid-dvd-i386.jigdo      10-Apr-2010 13:40  248K  Install/live DVD for PC (Intel x86) computers (jigdo download)
 lucid-dvd-i386.list       10-Apr-2010 13:41  174K  Install/live DVD for PC (Intel x86) computers (file listing)
 lucid-dvd-i386.manifest   10-Apr-2010 12:52   69K  Install/live DVD for PC (Intel x86) computers (contents of live filesystem)
 lucid-dvd-i386.template   10-Apr-2010 13:40  1.1G  Install/live DVD for PC (Intel x86) computers (jigdo template)
 report.html               10-Apr-2010 13:41  366

---

### Post by new_tolinux on 2010-04-10
> **grandtoubab said:**
> i am sorry too but here what I see
 Parent Directory                               - 
.....
+1

Maybe you need to refresh the page, your browser-cache.

---

### Post by QLee on 2010-04-10
[QUOTE=aviramof]
and i want to ensure as much as i can that the installer want create me sda5 and sda6 partitions again but sda2 and sda3 partitions.[/QUOTE]

[http://ubuntuforums.org/showthread.php?p=9103099#post9103099](http://ubuntuforums.org/showthread.php?p=9103099#post9103099)

---

### Post by aviramof on 2010-04-10
this version was just releasd a few hours ago it didn't existed and here it's still april 6
[http://cdimage.ubuntu.com/releases/10.04/beta-2/](http://cdimage.ubuntu.com/releases/10.04/beta-2/)
 
bare in mind that are several sites one or more for beta 2 and one or more for daily build.

---

### Post by psyke83 on 2010-04-10
> **aviramof said:**
> this version was just releasd a few hours ago it didn't existed and here it's still april 6
[http://cdimage.ubuntu.com/releases/10.04/beta-2/](http://cdimage.ubuntu.com/releases/10.04/beta-2/)
 
bare in mind that are several sites one or more for beta 2 and one or more for daily build.

The April 6th build *is *beta 2. Just because the release date was later does not matter. In other words, the April 6th release candidate was free of show-stopper bugs, and therefore declared as beta 2.

---

### Post by psyke83 on 2010-04-10
> **aviramof said:**
> also i started heaving problems with the metacity update all the windows buttons dissapear the close and minimize and expend because i removed metacity and i was unable to reinstall it without uninstalling compiz.
 
Because you ran a partial upgrade. If you put aside a mere 10 minutes of your time to properly read (and not skim) the sticky threads for the development release, you will a) understand the mistake you made, b) know how to fix the problem without re-installing, and c) realize the proper way to administer your system in order to prevent future mistakes.

> 
and also i wanted to see if you fixed the ubiqutity problem i had in the past the problem is that he create my partitions as sda5 and sda6 even thoughe i only have one more partition in this drive which is sda1 my windows server 2008 and just for the recored xubuntu ubiquity didn't had this problem when i tried it not long ago.I can immediately recognize the problem: user error. Your drive most likely has an extended partition, and you don't seem to understand the way in which logical partitions are assigned within extended partitions; jocko has explained this for you in detail.
 
> and since i already formated everything and erased the ext4 and swap partition i wanted to try and test the dvd version but 
i am not about to download and burn 4GB of dvd if it's 4 days old and it's date is before beta 2 was released at all.Explained already. April 6th build = beta 2. If you still don't believe us, take a look at the dates for the [desktop CD version]("http://releases.ubuntu.com/lucid/") - they're also from April 6th.

---

### Post by ezsit on 2010-04-10
aviramof wrote:
> yes it can it's called ubiquity and this is the ubuntu installer and because i want the dvd version there could a lot of other pacages updates and beside i want the most updated dvd version before i download and burn 4GB i don't want to have to update the installer via the live cd.

and i want to ensure as much as i can that the installer want create me sda5 and sda6 partitions again but sda2 and sda3 partitions.

If you are having this much trouble with the concept of partitions, wait until the final release, betas are not for you. Better yet, do some reading up on partitioning, filesystems, etc. If you have reached the max limit on primary partitions, then you are forced to use logicals. Otherwise, the creation of primary partitions that will be called sda1, sda2, etc. is ENTIRELY within the user's control (maybe not "your" control, that is why you need to do some homework first, before you complain about mythical bugs in the installer).

---

### Post by aviramof on 2010-04-11
the fact that i removed metacity via synaptic doesn't mean that in order to reinstall it i need to remove compiz but still i already had several other problem so format was a good idea any way.
 
and no i don't have an extended partition i have just one primpary partition on this hd which is sda1 so there should not be a problem with that and yet the installer create sda 5 and 6 when i chose use the free space option i must point out that when i tried xubuntu 10.04 not long ago it did not had this problem and just to let you i do know a thing or two about partitioning and file systems and etc and about a host of a lot of other things after all i managed to handle most of the problmes alpah versions througe at me didn't i? so trust me it's not a mythical bug when i created partitions via ubiquity 
with beta 1 or alpah 2 manually or otherwise it gave them them names sda5 and sda6 
despite the fact i only had sda1 and also it had problems installing grub 2 at all so i had to do that manually to sda and sdb.
 
any way i'm about to install latest daily dvd version soon then will see if everything will work better now.

---

