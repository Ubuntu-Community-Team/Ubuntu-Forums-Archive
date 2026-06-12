---
title: "Hardy - no updates..."
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Vegar on 2008-05-02
The day hardy was released, i ran sudo-apt get update (I had hardy beta) and downloaded the full version. (I think. It works like that, right?)
Well, after that i havent been able to get any more updates.
I've tried  sudo apt-get update and the update manager. sudo apt-get update gives the following output:
```
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://no.archive.ubuntu.com hardy Release.gpg
Ign http://no.archive.ubuntu.com hardy/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://no.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://no.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://no.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://no.archive.ubuntu.com hardy-updates Release.gpg
Ign http://no.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://no.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://no.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://no.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release                          
Hit http://no.archive.ubuntu.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://no.archive.ubuntu.com hardy-updates Release              
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://no.archive.ubuntu.com hardy/main Packages
Hit http://no.archive.ubuntu.com hardy/restricted Packages
Hit http://no.archive.ubuntu.com hardy/restricted Sources            
Hit http://no.archive.ubuntu.com hardy/main Sources                  
Hit http://no.archive.ubuntu.com hardy/multiverse Sources            
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://no.archive.ubuntu.com hardy/universe Sources
Hit http://no.archive.ubuntu.com hardy/universe Packages
Hit http://no.archive.ubuntu.com hardy/multiverse Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://no.archive.ubuntu.com hardy-updates/main Packages
Hit http://no.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://no.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://no.archive.ubuntu.com hardy-updates/main Sources
Hit http://no.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://no.archive.ubuntu.com hardy-updates/universe Sources
Hit http://no.archive.ubuntu.com hardy-updates/universe Packages
Hit http://no.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Reading package lists... Done

```
And in update manager i dont got any avalible packages.

I'd really like to keep up to date with the newest upgrades, but atm i can't.

All help appreciated.

---

### Post by vishzilla on 2008-05-02
We're all in the same boat. Still waiting for some updates. Wondering why it's taking so long.

---

### Post by bobnutfield on 2008-05-02
I don't believe there have been any updates since the stable release of Hardy.  All looks fine to me.

Bob

---

### Post by Vegar on 2008-05-02
Oh, i thought it had been, hehe :D
Well, i got no problem then =)
Thanks ^^

---

### Post by Kilz on 2008-05-02
> **bobnutfield said:**
> I don't believe there have been any updates since the stable release of Hardy.  All looks fine to me.

Bob

There have been updates. [This page lists the following packages releases]("http://feeds.ubuntu-nl.org/HardyChanges")
1. The 23rd - 5 packages released
2. The 24th - 4 packages including the gnome file system and compiz plugins that I have installed.
3. The 25th and 26th 1 package released per day
4. The 28th 4 packages released including gtk that I know is installed for my Gnome desktop.
5. The 29th 17 packages released including evolution and the update manager that I know are installed on my system
6. The 30th 7 packages including hal, sudo, nautilus, gnome-desktop, and gnome-control-center that I know are installed on my system.
7. May 1st 6 updates including the linux kernel, linux-ubuntu-modules, update-manager that I know are installed on my system

So far I have not seen upgrades since the release either.

---

### Post by Quicky on 2008-05-02
I've had all those updates listed above. However, I had to run the Update Manager and hit Check to find them. The notification area on my desktop does not seem to do anything unless I actually run the Update Manager.

---

### Post by Kilz on 2008-05-02
I just manually clicked check, still no updates.

---

### Post by dasunst3r on 2008-05-02
I just got an update for *devscripts*, but my mirror lags the main one by about a day.

---

### Post by Kilz on 2008-05-02
I have filed a bug report on launchpad.

[https://bugs.launchpad.net/ubuntu/+bug/225734](https://bugs.launchpad.net/ubuntu/+bug/225734)

---

### Post by OrangeCrate on 2008-05-02
Confirm no updates since release on 32bit Hardy.

---

### Post by alligoodw on 2008-05-02
Same here.  No updates since 8.04 release.

---

### Post by Jonie on 2008-05-02
It seems there ain't any. What was listed above, are the proposed updates, kind of beta, not official ones.

---

### Post by thetankftc on 2008-05-02
Ok, from what I can tell this an error updating lists. If I do a sudo apt-get update I end up getting a bunch of these:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

I can however run a successful apt-get update when I'm at home on a Comcast connection. The errors that I'm seeing are at work and I'm behind a Sonicwall Pro 2040 on a Qwest t-1. I have access to the Sonicwall and checked the logs. The SW doesn't appear to be blocking anything so I'm wondering if there is something about the SW or the ISP that is causing the repository to reset the connection. 

If anyone has any insight please post. 
Thanx

---

### Post by adredz on 2008-05-02
no updates since the release. what's taking it so long?

---

### Post by Quicky on 2008-05-02
There have been updates. I've just this second finished installing today's, although stupidly I failed to make a note of what they were. I can confirm that one of the updates was for Update Manager.

I don't believe the 'no updates' issue can be affecting all Hardy users.

---

### Post by RichJacot on 2008-05-02
I ran sudo apt-get update and then sudo apt-get upgrade this morning and found no updates.  

After reading this thead I just went through the update manager and it found two.  I canceled out and did update and upgrade again and it found the same two now. :confused:  Interesting.

---

### Post by celdar on 2008-05-02
> **RichJacot said:**
> I ran sudo apt-get update and then sudo apt-get upgrade this morning and found no updates.  

After reading this thead I just went through the update manager and it found two.  I canceled out and did update and upgrade again and it found the same two now. :confused:  Interesting.

Same here, exactly.

I've had no other updates since my initial upgrade on Monday of this week. Not that I was really expecting any yet though...

---

### Post by OrangeCrate on 2008-05-02
**Update to my last post above...**

Update Manager just coughed up three:

Libldap-2.4.2
Libldap2-dev
Ishw

At least Update Manager is working, but it's hard to believe that's all there's been since 4/24...

---

### Post by sports fan Matt on 2008-05-02
I had 2 today when I awoke (roughly 9:15 AM CST) to Update-Manager and Update-Manager Core

---

### Post by lswest on 2008-05-02
well...if you're desperate for updates (like me) enable the hardy proposed sources, i've gotten a few updates from there lately ;)

---

### Post by rolnics on 2008-05-02
> **OrangeCrate said:**
> **Update to my last post above...**

Update Manager just coughed up three:

Libldap-2.4.2
Libldap2-dev
Ishw

At least Update Manager is working, but it's hard to believe that's all there's been since 4/24...

Hmmm, that's strange Update Manager found those after running apt-get update and apt-get upgrade?! But it didn't find anything before??

---

### Post by OrangeCrate on 2008-05-02
> **rolnics said:**
> Hmmm, that's strange Update Manager found those after running apt-get update and apt-get upgrade?! But it didn't find anything before??

Correct.

---

### Post by BigSilly on 2008-05-02
Just to add my tuppence-worth, I've had no updates whatsoever since installing last week either. I've got Medibuntu enabled etc, and thought I might have seen something by now, but no. Not sure what this means.

---

### Post by dasunst3r on 2008-05-03
Remember the Windows mentality with respect to updates: The more updates are being pushed, the buggier the program was to begin with.  This is a bad thing for open-source developers because open-source developers like to fix every little problem they find before it becomes an exploit and push them out as quickly as possible.  I like the peace and quiet, but it's going to take a good bit of time to get used to.

---

### Post by BigSilly on 2008-05-03
> **dasunst3r said:**
> Remember the Windows mentality with respect to updates: The more updates are being pushed, the buggier the program was to begin with.  This is a bad thing for open-source developers because open-source developers like to fix every little problem they find before it becomes an exploit and push them out as quickly as possible.  I like the peace and quiet, but it's going to take a good bit of time to get used to.

As far as I could tell, this wasn't the point of this thread (though I take your meaning). I think the point was that there are updates available, but the update manager isn't working as it should, so you're not getting them. Correct me if I'm wrong please.

---

### Post by ugm6hr on 2008-05-03
I've only tried the 32-bit and AMD64 LiveCDs so far (no time for messing about with a new install at the moment).

But the notification area didn't recognise any updates either.

Hmm.... Will try Terminal next time I boot the LiveCD to play with.

---

### Post by Rhenthalin on 2008-05-04
I got my manager to spit up those three updates you mentioned but for some reason I'm getting this failure to fetch cd error anyone know what this is about I've done the apt- get upgrade and update things and I get a similar error when I hit update.

____________error_________
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080414)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080414)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
___________________________
Any help would be appreciated

---

### Post by dasunst3r on 2008-05-05
> **Rhenthalin said:**
> I got my manager to spit up those three updates you mentioned but for some reason I'm getting this failure to fetch cd error anyone know what this is about I've done the apt- get upgrade and update things and I get a similar error when I hit update.

____________error_________
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080414)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Daily Build amd64 (20080414)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
___________________________
Any help would be appreciatedWhy are you using a daily build?

---

### Post by Skip Da Shu on 2008-05-05
What are the translation-en_US errors I am getting and that are in the original post?

Then at the end I get error box with:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http //apt-cacher.ip.address.here hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http: //apt-cacher.ip.address.here/ us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ccouch82 on 2008-05-06
When I hit the check button it list 29 new updates, it works fine.

---

### Post by Glugglug on 2008-05-06
I've had updates to the final release when I open update manager to check first time it just says system up to date and then click on the check button it asks for your password .  The first update was   2 updates and yesterday I think was 27 updates they were only recomended updates not security .    They were mainly evolution updates.

---

### Post by bartong on 2008-05-07
I too am having issues.  I know this is a problem because there were 28MB worth of updates which I downloaded in a VM install of Hardy at work today (hadn't run the VM for 5 days prior), but at home I have had none of those updates come up despite using all the same sources.  Here is the output of an apt-get update:

```
$ sudo apt-get update
Hit http://packages.medibuntu.org hardy Release.gpg
Hit http://archive.canonical.com hardy Release.gpg
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Hit http://archive.canonical.com hardy Release                                 
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:1 http://archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy-updates Release                       
Err http://archive.ubuntu.com hardy-updates Release                       
  
Hit http://archive.ubuntu.com hardy-security Release                      
Hit http://archive.ubuntu.com hardy/main Packages                         
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Get:2 http://archive.ubuntu.com hardy-security/universe Packages [7522B]
Hit http://archive.ubuntu.com hardy-security/multiverse Packages          
Fetched 192B in 3min6s (1B/s)                        
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

I can only think that something is definitely wrong with the signatures on the update repos!  Is someone listening who can fix this???

---

### Post by bensode on 2008-05-07
Having problems with installation and updates as well on 7.10 64 bit server.  It seems that security.ubuntu.com (91.189.88.37) is extremely slow and suffering from time outs.  My installation had barked that security sources were going to be commented out.

edit: Results of manually adding them in and the output of apt-get update

Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

Fetched 58.7kB in 2m7s (459B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by pauljoseph on 2008-05-07
I am having the same problem. Any solution so far?

---

### Post by brigux on 2008-05-07
kinda slow but working now. (although you might have to retry once or twice). Probably just a load issue. will resolve in time.

---

### Post by sports fan Matt on 2008-05-07
I had I think 7 updates today..Download speeds were very painfully slow yesterday (note: these updates are proposed)

---

### Post by bartong on 2008-05-07
Well it appears the issue has been fixed for me, now i get updates coming thru without any problems, and a "sudo apt-get update" doesn't output any errors anymore (although it IGNs the Translation bits as it always does). Can anyone confirm for sure (ie: not speculation) what was going on? Was it just a server load problem or was there an issue with the GPG signatures on the update server?

---

### Post by dugb on 2008-05-08
I too am having issues with the updates. I successfully upgraded to HH and the next day installed some updates. The day following the list of updates will not install; I select to install from Update Manager and it just hangs, for hours, nothing happening. The PC is not locked and otherwise works correctly. I used 'sudo apt-get update' which worked the second time. However, the updates continue to appear in Update Manager awaiting installation. Any ideas?

---

### Post by bartong on 2008-05-08
Try

```
sudo apt-get update && sudo apt-get upgrade
```

That should update the package lists and then proceed to upgrade any packages that need upgrading.

---

### Post by Skip Da Shu on 2008-05-08
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.
GPG error: [http://apt-cacher](http://apt-cacher) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://apt-cacher:3142/us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://apt-cacher:3142/us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

5 min ago

---

### Post by bartong on 2008-05-08
Seems like the issue might be on-and-off then.

Anyone listening?

---

### Post by Umang on 2008-05-08
I had a similar problem, but then I went to Synaptic, and I clicked refresh. After downloading 48 files it said I had 90 odd updates possible. I haven't updated all as yet.

---

### Post by bazzieb on 2008-05-08
I have had updates but the second lot of updates, which are labeled as proposed updates, hangs the update manager and i have to forcefully close update manager.

---

### Post by pauljoseph on 2008-05-09
Now my Hardy can update. Yesterday, I still failed to update.

today I changed the server to local nearer through Adept, and then it has 9 updates. When I switched back the server to Main server, I got 80 updates.

well just wondering whether this is due to the server or something? will this happen again?

---

### Post by dugb on 2008-05-09
> **bartong said:**
> Try

```
sudo apt-get update && sudo apt-get upgrade
```

That should update the package lists and then proceed to upgrade any packages that need upgrading.

I tried this as suggested and the process ran through completely. However, it indicated, as before with an earlier post by someone else here, some sites and packages could not be accessed and the process failed.

Edit: as Bartong explained earlier.

---

### Post by Skip Da Shu on 2008-05-09
I'm getting the updates but still getting various flavors of:

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

I'm not behind a proxy.

---

### Post by dugb on 2008-05-09
This is getting worse now. Anything I try to open that requires System Administration fails to work. The icon for System Administration appears in the bottom bar briefly, and then just disappears with the application I am trying open not opening. This has happened for Synaptic Package Manager, Update manager and Automatix. HH is making Windows look better.

---

### Post by dugb on 2008-05-09
I believe the problem has been identified and solved. I followed the instructions as per the following links and Update Manager now works correctly; all updates downloaded and installed.

For your information please read the following links to fix this identified bug:

[http://ubuntuforums.org/showthread.php?t=784111&highlight=system+administration](http://ubuntuforums.org/showthread.php?t=784111&highlight=system+administration)

or

[https://answers.launchpad.net/ubuntu/+question/29446](https://answers.launchpad.net/ubuntu/+question/29446)

---

### Post by nomizzz on 2008-05-21
Because there seems to be infinitely many variations of the update manager bug, I've picked this thread to post on because these issues seem to be closest to my problem.

After upgrading to 8.04 via the official update manager, everything works fine except that the update manager constantly says that my system is up to date while it never actually downloads or even displays the recommended package lists.  I did a clean install of 8.04 on another desktop and the update manager has had several update packages between now and the 8.04 release on that computer.

As dugb suggested, I read the full discussions of
> [http://ubuntuforums.org/showthread.p...administration](http://ubuntuforums.org/showthread.p...administration)

or

[https://answers.launchpad.net/ubuntu/+question/29446](https://answers.launchpad.net/ubuntu/+question/29446)

and played around with the Hosts IP Address settings but nothing changed.

It doesn't seem possible that the updates have been running in the background without my knowledge or consent, but even utilizing
```
sudo apt-get update && sudo apt-get upgrad
```

displays:

```
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any help would be appreciated as I'm feeling less and less secure as I see each security update go by on my desktop, exactly the opposite of what I should be feeling.

---

### Post by bartong on 2008-05-21
> **nomizzz said:**
> Because there seems to be infinitely many variations of the update manager bug, I've picked this thread to post on because these issues seem to be closest to my problem.

After upgrading to 8.04 via the official update manager, everything works fine except that the update manager constantly says that my system is up to date while it never actually downloads or even displays the recommended package lists.  I did a clean install of 8.04 on another desktop and the update manager has had several update packages between now and the 8.04 release on that computer.

As dugb suggested, I read the full discussions of


and played around with the Hosts IP Address settings but nothing changed.

It doesn't seem possible that the updates have been running in the background without my knowledge or consent, but even utilizing
```
sudo apt-get update && sudo apt-get upgrad
```

displays:

```
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Any help would be appreciated as I'm feeling less and less secure as I see each security update go by on my desktop, exactly the opposite of what I should be feeling.
This looks like you don't have the update or security repos enabled in your software sources.

Can you post the content of your /etc/apt/sources.list file here?

---

### Post by Skip Da Shu on 2008-05-21
> **bartong said:**
> This looks like you don't have the update or security repos enabled in your software sources.

Can you post the content of your /etc/apt/sources.list file here?

**Good catch bartong!**

nomizz - *minimally* should have something along these lines (well I guess multiverse is debatable):

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to newer versions.

## MAIN - Release v8.04, Hardy
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## UPDATES MAIN - Major bug fix updates produced after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## UNIVERSE
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## MULTIVERSE
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## SECURITY
deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by Pumalite on 2008-05-21
You can go to System>Administration>Software Sources>And enable all of them. Especially partner, backports, proposed and updates.

---

### Post by nomizzz on 2008-05-22
> **bartong said:**
> This looks like you don't have the update or security repos enabled in your software sources.

Can you post the content of your /etc/apt/sources.list file here?

Bartong you're a genius (or more likely, I'm just an Linux N00b).  Check out what the content of my sources.list file was prior to your suggestion:

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy main universe multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

After a whole lot of uncommenting, I now have 155 updates eagerly awaiting download :) !

Thanks to all for the suggestions.

My last issue is that it seeps somewhat suspicious that my security update server was pretty much blocked by the installer; that seems like a good time for someone to hack my machine.  Does anyone know if my case was singular, or are my suspicions of foul play just a product of cyber paranoia?

---

### Post by bartong on 2008-05-22
I wouldn't be too concerned about this, most security bugs that get fixed in these updates are fairly minor, and usually the condition leading to a hacker being able to exploit the bug is so unlikely as to make the threat level extremely low.

It was just unfortunate that when you did your install the security and updates servers were having problems (which I guess is what caused most of the posts on this thread).  I don't honestly beleive any foul play has occured here.

As an aside, this is probably the first time I have managed to help someone in these forums.  Usually its me asking for help!

---

