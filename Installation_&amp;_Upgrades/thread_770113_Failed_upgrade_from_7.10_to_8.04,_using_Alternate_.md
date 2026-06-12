---
title: "Failed upgrade from 7.10 to 8.04, using Alternate CD"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by leeyee on 2008-04-27
Hi guys,

When upgrading from 7.10 to 8.04 using 8.04 alternate CD, it gave me error info:

```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
```

I've done md5sum check, and sure the iso is OK. I just did as follows:

1, Mount iso using
```
sudo mount -o loop ubuntu-8.04-alternate-i386.iso /cdrom
```
2, Alt+F2, and type in
```
gksu "sh /cdrom/cdromupgrade"
```
3, Update Manager pop up correctly, and "Preparing upgrade"
4, Update Manager asked me whether include latest update from Internet, I chose "No"
5, When calculating changes, Update Manager pop up a error screen contains info i gave above.

Here is my /var/log/dist-upgrade/main.log file:
> 2008-04-27 15:50:40,659 INFO release-upgrader version '0.87.24' started
2008-04-27 15:50:41,060 DEBUG Using 'DistUpgradeViewGtk' view
2008-04-27 15:50:41,131 DEBUG enable dpkg --force-overwrite
2008-04-27 15:50:41,222 DEBUG lsb-release: 'gutsy'
2008-04-27 15:50:41,223 DEBUG _pythonSymlinkCheck run
2008-04-27 15:50:42,955 DEBUG checkViewDepends()
2008-04-27 15:50:43,989 DEBUG useNetwork: 'False' (selected by user)
2008-04-27 15:50:43,990 DEBUG running doUpdate() (showErrors=False)
2008-04-27 15:50:43,990 DEBUG doUpdate() will not use the network because self.useNetwork==false
2008-04-27 15:50:45,692 DEBUG doPreUpgrade
2008-04-27 15:50:48,060 DEBUG Foreign: libavformat-dev libavcodec-dev stardict-xdict-ce-gb libavutil-dev w32codecs stardict-oxford-gb libavformat1d libavcodec1d stardict-cedict-gb libdvdcss2 stardict-langdao-ce-gb libavutil1d stardict-xdict-ec-gb stardict-langdao-ec-gb stardict-cdict-gb stardict-hanzim
2008-04-27 15:50:48,061 DEBUG Obsolete: cedega-small gtk2-engines-candido
2008-04-27 15:50:48,062 DEBUG updateSourcesList()
2008-04-27 15:50:48,121 DEBUG rewriteSourcesList()
2008-04-27 15:50:48,122 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy main restricted universe multiverse'
2008-04-27 15:50:48,123 DEBUG entry 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,123 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-security main restricted universe multiverse'
2008-04-27 15:50:48,125 DEBUG entry 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-security main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,125 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-updates main restricted universe multiverse'
2008-04-27 15:50:48,126 DEBUG entry 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-updates main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,126 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-proposed main restricted universe multiverse'
2008-04-27 15:50:48,128 DEBUG entry 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-proposed main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,128 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-backports main restricted universe multiverse'
2008-04-27 15:50:48,129 DEBUG entry 'deb [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-backports main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,129 DEBUG examining: 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy main restricted universe multiverse'
2008-04-27 15:50:48,131 DEBUG entry 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,131 DEBUG examining: 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-security main restricted universe multiverse'
2008-04-27 15:50:48,132 DEBUG entry 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-security main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,132 DEBUG examining: 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-updates main restricted universe multiverse'
2008-04-27 15:50:48,134 DEBUG entry 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-updates main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,134 DEBUG examining: 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-proposed main restricted universe multiverse'
2008-04-27 15:50:48,135 DEBUG entry 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-proposed main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,135 DEBUG examining: 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) gutsy-backports main restricted universe multiverse'
2008-04-27 15:50:48,137 DEBUG entry 'deb-src [http://ubuntu.cn99.com/ubuntu/](http://ubuntu.cn99.com/ubuntu/) hardy-backports main restricted universe multiverse' updated to new dist
2008-04-27 15:50:48,137 DEBUG examining: 'deb [http://ubuntu.cn99.com/ubuntu-cn/](http://ubuntu.cn99.com/ubuntu-cn/) gutsy main restricted universe multiverse'
2008-04-27 15:50:48,139 DEBUG entry '# deb [http://ubuntu.cn99.com/ubuntu-cn/](http://ubuntu.cn99.com/ubuntu-cn/) gutsy main restricted universe multiverse' was disabled (unknown mirror)
2008-04-27 15:50:49,459 DEBUG AptCdrom.add() called with '/cdrom'
2008-04-27 15:50:49,775 DEBUG AptCdrom.add() returned: 1
2008-04-27 15:50:49,775 DEBUG running doUpdate() (showErrors=True)
2008-04-27 15:50:49,775 DEBUG doUpdate() will not use the network because self.useNetwork==false
2008-04-27 15:50:55,226 DEBUG Running KeepInstalledSection rules
2008-04-27 15:50:55,227 DEBUG Installing 'language-support-zh' (Distro KeepInstalledSection rule: translations)
2008-04-27 15:52:13,238 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'


ANOTHER SITUATION

If I chose "Include latest update from Internet" YES in above step, update manager would also crash, the only difference was that it gave no error information explicitly. After checking /var/log/dist-upgrade/main.log, it gives:
> 2008-04-27 15:57:05,275 INFO release-upgrader version '0.87.24' started
2008-04-27 15:57:05,674 DEBUG Using 'DistUpgradeViewGtk' view
2008-04-27 15:57:05,744 DEBUG enable dpkg --force-overwrite
2008-04-27 15:57:05,835 DEBUG lsb-release: 'gutsy'
2008-04-27 15:57:05,836 DEBUG _pythonSymlinkCheck run
2008-04-27 15:57:07,409 DEBUG checkViewDepends()
2008-04-27 15:57:09,043 DEBUG useNetwork: 'True' (selected by user)
2008-04-27 15:57:30,901 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmp.mtwxC13410/MetaRelease.py", line 206, in download
    uri=urllib2.urlopen(req)

  File "urllib2.py", line 124, in urlopen
    return _opener.open(url, data)

  File "urllib2.py", line 381, in open
    response = self._open(req, data)

  File "urllib2.py", line 399, in _open
    '_open', req)

  File "urllib2.py", line 360, in _call_chain
    result = func(*args)

  File "urllib2.py", line 1107, in http_open
    return self.do_open(httplib.HTTPConnection, req)

  File "urllib2.py", line 1080, in do_open
    r = h.getresponse()

  File "httplib.py", line 924, in getresponse
    response.begin()

  File "httplib.py", line 385, in begin
    version, status, reason = self._read_status()

  File "httplib.py", line 349, in _read_status
    raise BadStatusLine(line)

BadStatusLine

2008-04-27 15:57:30,902 DEBUG running apport_crash()
2008-04-27 15:57:31,522 ERROR failed to import apport python module, can't report bug: No module named python_hook


Any idea? Any information or help will be highly appreciated.
Thank you guys!

NOTE: I've done
```
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade
```
They all work fine with Gusty repositories, didn't give any error.

---

### Post by bcnaat on 2008-04-27
leeyee, when I inserted my 8.04 alternate cd, the window opened up with the files but a message box popped up asking if I wanted to use the distro off it (not those words, but something similar). I clicked on yes and then it added it to my list of cd's to work off in synaptic pkg manager (update manager as well) as a source. I did my upgrade that way without problems.

Which instructions were you following to do the upgrade? Just curious if there is something in those instructions that were wrong or maybe we missed a step? 

Maybe someone else will post that has encountered this or knows what causes the upgrade to fail.

---

### Post by bcnaat on 2008-04-27
Leeyee,

I was reading the instructions on the upgrade and you have to burn the iso to a disk. It appears that mounting the image off your hard drive doesn't work.

Kay

---

### Post by shadowkiller137 on 2008-04-27
I dont know whether burning it to a disk will change it or not but I had this happen during a standard upgrade so it might be something besides burning it to a disk

---

### Post by leeyee on 2008-04-28
Hey
I've fixed it. Burn it really can resolve the problem, but i got a better way:
```
sudo mount -o loop ubuntu-8.04-alternate-i386.iso /cdrom
sudo apt-cdrom -m -d /media/cdrom add
```
Then open Synaptic, it appears just like you insert alternate CD in.

---

### Post by Malfet on 2008-04-29
> **leeyee said:**
> Hi guys,
When upgrading from 7.10 to 8.04 using 8.04 alternate CD, it gave me error info:
```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
```

I have exactly the same problem with burned alternate CD. Is it a really burning problem?

---

### Post by leeyee on 2008-04-29
Might not be

You can try my iso image trick given above, to see if it still give the same error info?

---

### Post by sumardika on 2008-05-01
I had exactly the same problem. I have ckecked the mdsum and it's ok. Burn the iso file to a CD without error. Upgrade fail both with and without internet connection.

---

### Post by Malfet on 2008-05-05
> **sumardika said:**
> I had exactly the same problem. I have ckecked the mdsum and it's ok. Burn the iso file to a CD without error. Upgrade fail both with and without internet connection.

Same for me. I got exactly same problem with burned alternate CD on one computer. Does anyone has a clue what to do in this situation?

M.

---

### Post by tariquepark on 2008-05-05
hi all,
i too have exactly the same problem with the same stuff in /var/log/dist-upgrade/ log
maybe this is a bug and should be reported?
any devs care to venture an opinion?
luke

---

### Post by Malfet on 2008-05-06
> **tariquepark said:**
> hi all,
i too have exactly the same problem with the same stuff in /var/log/dist-upgrade/ log
maybe this is a bug and should be reported?
any devs care to venture an opinion?
luke

Looks like no one care about it. I've checked md5sum of my iso-file and burned it twice with different CDs. Everything looks fine, CD has no errors, checksum is correct but no possibility to upgrade system through alternate CD on different computers :(

---

### Post by tariquepark on 2008-05-06
hi again,
oh but i care and i dont like not winning lol
So, some success here, 
this is how things went for me, i had to first
sudo apt-get remove xubuntu-desktop
 it didn't like that being there maybe?
sudo apt-get autoclean
then i edited my /etc/apt/sources.list
and commented everything except the 8.04 cdrom entry
then in a terminal 
sudo su
then 
gksu "sh /cdrom/cdromupgrade"
and it went perfectly :)

now having said all that i'm still fairly new at this stuff so .........
Also i forgot to mention i removed my nvidia graphic drivers before i even did my backups
this may be important im not sure

i hope this may be of use for others
cheers

---

### Post by Malfet on 2008-05-07
> **tariquepark said:**
> hi again,
sudo apt-get autoclean
then i edited my /etc/apt/sources.list
and commented everything except the 8.04 cdrom entry

Unforunately, no effect for me. I follow your advice, but got the same error...

M.

---

### Post by zvacet on 2008-05-07
**Remove any third party repos before upgrade.**That can be source of problems.To upgrade with altrnate CD just put CD in drive and message should pop up telling you that you can do upgrade (not exact words but you know..).If message doesn´t show up run in terminal

```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by Malfet on 2008-05-07
> **zvacet said:**
> **Remove any third party repos before upgrade.**That can be source of problems.To upgrade with altrnate CD just put CD in drive and message should pop up telling you that you can do upgrade (not exact words but you know..).If message doesn´t show up run in terminal
```
gksu "sh /cdrom/cdromupgrade"
```

I did it, right now I even remove all repos froum sources.lst except alterntate CD and still getting message 

```
"Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.
 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu"
```

:(:(:( Md5sum is OK. Burned two CDs low speed with the same outcome.

---

### Post by tariquepark on 2008-05-07
hmmm i feel bad now cause mines good :)
um me thinks its a prob with the update manager cause its the calculating bit that errors so,um...dunno 
this is where my knowledge stops im afraid
i been looking through some threads and found a few thimgs to try

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

also try

apt-get --help and try those 
dselect-upgrade and check 

and i keep looking too
cheers

---

### Post by PCWizKid on 2008-05-07
[IMG]http://bp2.blogger.com/_ofqWS815dOE/SCCXZNH8XHI/AAAAAAAAAls/9jptnKJUWIg/s320/hardy_splash.jpg[/IMG]
Well I finally toke the plunge and upgraded my Ubuntu 7.10 - Gutsy Gibbon to 8.04 LTS, I recorded the steps and captured it for anyone that would like to see exactly what was involved in doing the upgrade in my case. [Take a look here]("http://pcwizkid.blogspot.com/2008/05/ubuntu-804-hardy-heron-upgrade.html").

Cheers
[PCWizKid]("http://PCWizKidsTechTalk.com")

---

### Post by tariquepark on 2008-05-07
i just found this thread 
[http://ubuntuforums.org/showthread.php?t=764452](http://ubuntuforums.org/showthread.php?t=764452)
cheers

---

### Post by Malfet on 2008-05-08
> **tariquepark said:**
> hmmm i feel bad now cause mines good :)

Don't worry - I'll manage :) Thanks for your support! :)


> 
sudo apt-get update
sudo apt-get dist-upgrade


I've tried update and upgrade, but in this case Ubuntu updates just one or two hundreds packages and completely screw up the whole system, so I had to just format and install from scratch. That would work, but I don't want to do it for another 9 computers and then reinstall all software for them again. Ordinary update would save so much time...
I'll have a look for log files - perhaps I'll find the solution.

Cheers,
M.

---

### Post by Malfet on 2008-05-08
> **PCWizKid said:**
> [IMG]http://bp2.blogger.com/_ofqWS815dOE/SCCXZNH8XHI/AAAAAAAAAls/9jptnKJUWIg/s320/hardy_splash.jpg[/IMG]
Well I finally toke the plunge and upgraded my Ubuntu 7.10 - Gutsy Gibbon to 8.04 LTS, I recorded the steps and captured it for anyone

Internes update cause no problems - I already did it at home. I have troubles with alternate CD and I can not download 900 Mb for ten computers each using a low-speed internet connection.

M.

---

### Post by tariquepark on 2008-05-08
sorry but im all out of ideas
you can share your downloaded upgrade files from one computer to the other 9 tho if theyr all networked by adding them in the sources.list on the other 9 systems although if you cant get one done then maybe not worth it
anyway ill keep checking in so please post with your success or failure:)
cheers

btw i have reinstalled over a previous ubuntu installation without formatting and i didnt lose anything but it left a fair few useless files and folders
just a thought

---

### Post by Malfet on 2008-05-12
Yes, i did it! :)
log file contained just "Unable to correct problems, you have held broken packages" without details and Synaptic did not show any problem packages either, but before error message log mentioned "language-support-ru"
When I removed that package by Synaptic - whole update went smoothly :)

---

### Post by tariquepark on 2008-05-15
glad to hear its all sorted
regards

---

