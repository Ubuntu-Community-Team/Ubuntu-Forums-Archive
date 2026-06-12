---
title: "Can't apt-get update!!!"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by i.tJunKie on 2007-12-10
Hi everyone! I am very new to Linux, and I've managed (after a long painful ordeal) to install Ubuntu 7.10 on my PC. 

After the install, I opened the terminal and typed sudo apt-get update and it gets stuck on 43%. When it gets stuck it shows the following...

Err [http://archive..blah](http://archive..blah) blah
     Could not connect to archive..blah, connection timed out

Then it carries on trying to connect to other archives but fails. I'm not sure why I can't download and install anything from terminal- including the plug-ins for Firefox. I can't sudo apt-get update, or apt-get install anything in the terminal. Whenever I use apt-get install (e.g. java5)I get a message saying:

E: Couldn't find package sun-java5-plugin

I can browse the net fine - although it would only go to google and a few other sites when I first booted it. Upon searching through this forum, I found that I had to disable IPv6? It seems to be working, I have an internet connection but can't use terminal...I'm soooooo stuck! Any help is greatly appreciated...:)

---

### Post by Partyboi2 on 2007-12-10
go to System>Admin>Software Sources
(enter password)
then when Software Sources open up make sure that under the 'ubuntu Software' tab that  they are all ticked except 'source code'
then change tab to 'updates'
then make sure the first 2 are checked (security updates and recommend updates)
after that close Software Sources.
Then try again

---

### Post by PmDematagoda on 2007-12-10
You could also try changing the location of the servers by going to the Software Sources as Partyboi2 mentioned.

---

### Post by i.tJunKie on 2007-12-11
Whoa you guys are fast...:)

Thanks for the quick replies...but unfortunately...it's still stuck on 43%. 

[COLOR="RoyalBlue"]"go to System>Admin>Software Sources
(enter password)
then when Software Sources open up make sure that under the 'ubuntu Software' tab that they are all ticked except 'source code'"[/COLOR]

Yup! Everything was check EXCEPT source code..

[COLOR="RoyalBlue"]"then change tab to 'updates'
then make sure the first 2 are checked (security updates and recommend updates)"[/COLOR]

Yup! These were already checked- and I even tried changing my download server to see if that would make any difference...but sadly, it didn't. 

Any more ideas?? Could I be missing files or something? Hmmmmmmmmmm

---

### Post by PmDematagoda on 2007-12-11
I think it may be an issue with your internet connection.

Have you tried configuring your internet connection using a static IP address, a DHCP or using Roaming Mode in System>Administration>Network?

---

### Post by Rocket2DMn on 2007-12-11
Can you post the output of this command for us:
```
cat /etc/apt/sources.list
```
Then we can see what sites are being checked during the update command.

---

### Post by i.tJunKie on 2007-12-11
Hey thanks for all the help guys :)

Ok. First thing is first...

[COLOR="RoyalBlue"]**Have you tried configuring your internet connection using a static IP address, a DHCP or using Roaming Mode in System>Administration>Network?**[/COLOR]


Now I tried all of the above and after all the configuration, the only setting that seemed to let me surf the net was DHCP (which I am using now). Static IP didn´t like me much (although I may have set that up wrong :/ ) and Roaming Mode was severely allergic to me.,,,at least Static IP would load a lil bit and give me some hope that it might work...Roaming Mode just straight out rejected me and I swear it&#347; error message was glued to the screen.


[COLOR="RoyalBlue"]**cat /etc/apt/sources.list**[/COLOR]

Well here goes!...


digital-angel@ubuntu:~$ cat /etc/apt/sources.list
# 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security main restricted multiverse
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
digital-angel@ubuntu:~$ 

Thanks again guys! Much appreciated :)

---

### Post by Rocket2DMn on 2007-12-11
Using System->Administration->Software Sources try changing your download servers to   the Main server rather than your nz server.  You should probably also disable the cdrom sources as this can create problems.

---

### Post by i.tJunKie on 2007-12-11
In my very first post I had my server on Main Server, then I changed to NZ Server midway through...now I´m back to Main Server again.

I tried apt-get update in the terminal after changing back to Main server and it has made a difference!!! Instead of being stuck on 43% I now get stuck on 30%! Lol

So I went back into the sources list and disabled the CD Rom sources then tried in terminal again and...Nup..still stuck on 30%!

I have absolutely no idea what&#347; going on here...:(

---

### Post by Rocket2DMn on 2007-12-11
Do you have any Third-Party Software sources?  Check under Software Sources app, there is a tab to check.  Disable them if you can.
If this doesn't work, I would image there are just servers that are down and you should try again in a few hours.
Can you copy and paste the output you see when it gets stuck?

---

### Post by i.tJunKie on 2007-12-11
Okie Dokie,,,I unchecked the software sources in the ´Third Party Software´ tab and tried apt-getting in the terminal again and after a long painful wait - produced the following results..and it is a long one!...


Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_NZ
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_NZ
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg           
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_NZ
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_NZ.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_NZ.bz2)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
digital-angel@ubuntu:~$ 




and breathe....

any ideas?

---

### Post by PmDematagoda on 2007-12-11
I still believe that your problem is your internet connection, once you fix that your problems will be solved.

---

### Post by i.tJunKie on 2007-12-11
Well now that you mention it, the internet connection can be funny at times. I think I need to tell it to straighten up and be serious,,,So would you have any hints, tips or how to&#347; for checking my internet connection, or setting it straight????

Thanks again for your help :)

---

### Post by Partyboi2 on 2007-12-11
Are you behind a proxy server/firewall?

---

### Post by i.tJunKie on 2007-12-11
[COLOR="RoyalBlue"]**Are you behind a proxy server/firewall?**[/COLOR]

Nope aaaaaaaand nope. 


*sigh* Maybe I´m the first person this has happened to??!!! :)

---

### Post by Rocket2DMn on 2007-12-11
The only thing I can still think of is that your DNS is acting funky.  After a little research, it seems that Ubuntu doesn't keep the cache itself, but rather your router does.  You can try resetting your router to clear its DNS cache, or you could even try using different DNS servers.
DNS servers can be changed under System->Administration->Network and select the DNS tab.  You can look up some DNS servers online to try, but do write down your old ones in case the ones you try flop.
If DNS MASSIVELY fails you can always reach the English google site from your browser by putting 216.239.51.99 as your URL so you can search for the fix or navigate your way back here.

---

### Post by i.tJunKie on 2007-12-11
Well thanks guys! Because of all of your help, I have managed to fix my problem :)

> The only thing I can still think of is that your DNS is acting funky. After a little research, it seems that Ubuntu doesn't keep the cache itself, but rather your router does. You can try resetting your router to clear its DNS cache, or you could even try using different DNS servers.

Yes Rocket2DMn you were absolutely right. I logged into my router and disabled the DDNS setting, and also changed the DNS Selection setting to 'Use User Discovered DNS Server Only'.. Upon changing to User Discovered, The router presented me with a Preferred DNS Server address which I then added into the DNS Tab under System->Administration->Network.

I opened terminal with my fingers crossed that apt-get anything would work...and it did! Yay! 

Thanks to you all for your help...keep up the awesome work :)

---

### Post by shafi on 2007-12-11
mmmmmmm, I think there is something wrong with your sourcelist
go through your source list and check for this  [http://archive..blah](http://archive..blah) blah, maybe this is not a correct address, put a # at the begining of that line as follow
#[http://archive..blah](http://archive..blah) blah
then save and close your source list then try your update again,

to open your source list use the following commands:
[html]
sudo gedit /etc/apt/sourcelist
[/html]

---

