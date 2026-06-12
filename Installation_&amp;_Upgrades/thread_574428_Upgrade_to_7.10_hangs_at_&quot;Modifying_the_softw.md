---
title: "Upgrade to 7.10 hangs at &quot;Modifying the software channels/Checking package manager&quot;"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by cayhorstmann on 2007-10-12
I am running Feisty and thought I'd try to update to the Gutsy beta. I followed the instructions 

update-manager -d

A bunch of stuff got downloaded, and then the "Distribution Upgrade" program hangs at "Modifying the software channels/Checking package manager".

I didn't get any dbus error, but I figured I might as well try that other approach on [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades). I edited /var/lib/update-manager/meta-release and ran

sudo apt-get update
gksudo "update-manager -c -d"

The app started exactly as before and hung at the same place. 

This time I got an enigmatic message in the console:

GTK Accessibility Module initialized
warning: could not initiate dbus
extracting '/tmp/tmpm0wy0S/gutsy.tar.gz'
authenticate '/tmp/tmpm0wy0S/gutsy.tar.gz' against '/tmp/tmpm0wy0S/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GTK Accessibility Module initialized

I'd appreciate any suggestions. 

Thanks,

Cay

---

### Post by cicoandcico on 2007-10-13
i have the same proble, filed a bug here
[https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296](https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296)

---

### Post by SammyBoy247 on 2007-10-13
... and me

---

### Post by Schroeder on 2007-10-13
Same here...I guess. I confirmed the dialog that certain packages are not supported anymore and then Distribution Upgrade just hangs. The window seems frozen. 

The update manager however reports that there are new packages available which can be installed...didn't do that however since the figured the distribution upgrade manager has modified the sources to include gutsy packages.

Anybody any idea what's wrong here?

---

### Post by cayhorstmann on 2007-10-13
I have no idea what the problem is, but I did make progress by upgrading the old-fashioned way, running sudo apt-get dist-upgrade. (I had to first kill a "gutsy" process that locked the package repository.)

---

### Post by Schroeder on 2007-10-13
> **cayhorstmann said:**
> I have no idea what the problem is, but I did make progress by upgrading the old-fashioned way, running sudo apt-get dist-upgrade. (I had to first kill a "gutsy" process that locked the package repository.)

How did that go? Is this method equivalent to the update-manager?

---

### Post by cayhorstmann on 2007-10-13
It went just fine. It literally installed a thousand packages, and rebooted into the new kernel. The usual festering mess of X11 issues followed, but I am sure that would have been the same as with the graphical installer. Unless someone who knows better says otherwise, I think this is a viable way of getting past the hanging graphical installer.

Cheers,

Cay

---

### Post by Schroeder on 2007-10-14
Hmmm...I don't know. I will probably wait and see if anybody fixes the problem with the installer.

BTW, I tried upgrading again this morning and now I am getting the same dbus could not be initialized error...strange.

---

### Post by klausner on 2007-10-17
This is still happening with the 7.10 Release Candidate. Did anyone ever find a fix? :frown:

---

### Post by KCPokes on 2007-10-17
> **klausner said:**
> This is still happening with the 7.10 Release Candidate. Did anyone ever find a fix? :frown:

Good question.  I tried the upgrade just now and I'm hung at "Modifying the Software Channels" with the same error as above:

```

warning: could not initiate dbus
extracting '/tmp/tmpTHpOiW/gutsy.tar.gz'
authenticate '/tmp/tmpTHpOiW/gutsy.tar.gz' against '/tmp/tmpTHpOiW/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by KCPokes on 2007-10-17
Just an update to my last post, I searched around and tried some other suggestions....

Ran ```
gksu "update-manager -c -d"
```

The upgrade is running now.  Was afraid I'd get no farther but went on through.

---

### Post by SammyBoy247 on 2007-10-18
I guess the best things come to those who wait....

I want it NOW NOW NOW!  :)

---

### Post by flarkit on 2007-10-18
I believe the authentication problem is probably caused by the Gutsy data on the hosts not being complete yet. Either that, or there really was some problem with the authentication keys, which I doubt.

I was having this problem on Tuesday when I tried useing *"update-manager -d"* and gave up after an hour of struggling. Then I tried again last night and it worked fine, with no changes on my part.

So I would also recommend some patience and waiting a few hours for the servers to complete their updates or downloads.

---

### Post by Schroeder on 2007-10-18
> **flarkit said:**
> 
So I would also recommend some patience and waiting a few hours for the servers to complete their updates or downloads.

Patience and waiting alone doesn't fix bugs tough. ;)

And it IS a bug. update-manager does not execute in a certain feisty configuration (unfortunately that's my configuration) and apparently others have the problem too. The bug report is filed and after some investigation and code debugging last night I was able to trace the error in one of the update-manager files. I am waiting to hear back from the developer about my findings. 

Until then I will stick with Feisty...:-({|=

---

### Post by era_new on 2007-10-18
I thought I'd chime in to say that this exact issue is affecting me on five separate computers.

I hope this gets upgraded from "Importance: Undecided" at least.

---

### Post by Buendia on 2007-10-18
Any changes? Any cures? Now ubundu upgrade tool sound like windows installer to me.

---

### Post by Schroeder on 2007-10-18
> **era_new said:**
> I hope this gets upgraded from "Importance: Undecided" at least.

I hope so, too.

---

### Post by themusicwave on 2007-10-18
I have the very same issue...

I'll try using the command line to dowload it.

---

### Post by ekravche on 2007-10-19
> **KCPokes said:**
> Just an update to my last post, I searched around and tried some other suggestions....

Ran ```
gksu "update-manager -c -d"
```

The upgrade is running now.  Was afraid I'd get no farther but went on through.

so gksu "update-manager -c -d" did the trick? I'll give it a shot later on...

---

### Post by Schroeder on 2007-10-19
> **ekravche said:**
> so gksu "update-manager -c -d" did the trick? I'll give it a shot later on...

Didn't work for me...

---

### Post by era_new on 2007-10-19
> **ekravche said:**
> so gksu "update-manager -c -d" did the trick?
It didn't work for me.
I encountered the same problem as just clicking through with the mouse.

---

### Post by ddcc on 2007-10-19
Same thing occurs here for both my 32-bit and 64-bit machines. Do we all have firestarter installed or iptables configured?

Also do we all have ubuntu-desktop or the equivalent?

---

### Post by era_new on 2007-10-19
> **ddcc said:**
> Same thing occurs here for both my 32-bit and 64-bit machines. Do we all have firestarter installed or iptables configured?

Also do we all have ubuntu-desktop or the equivalent?
firestarter: Not installed on any.
iptables: Haven't touched it on at least 3 of these computers.
ubuntu-desktop: Installed on all.
moblock: Disabled on one; not installed on the others.
watchdog: Not installed.

Any more usual suspects?

---

### Post by Schroeder on 2007-10-19
> **ddcc said:**
> Same thing occurs here for both my 32-bit and 64-bit machines. Do we all have firestarter installed or iptables configured?

Also do we all have ubuntu-desktop or the equivalent?

firestarter: installed yes, but wouldn't I see a hit in the log if it prevented anything from happening? I tried again without firestarter running and it still does not work.

ubuntu-desktop: I did not have it installed until I saw in the log that update-manager complained. I installed it and still have the problem.

---

### Post by Buendia on 2007-10-19
This buggy bug forced me to switch to sabayon, it's smooth and beautiful. I found gutsy not too different and boring to be honest.

---

### Post by el_sombra on 2007-10-19
Hi, there... I was trying to upgrade my Kubuntu box and I'm having this problem, as many people. But I've checked the process table and there's a dist-upgrade.py active process which is locking my list directory and doesn't let me execute apt-get.

Some data:

- The installation process hung at file 38 of 52 ("Modifying the software channels" step - 99%).
- My sources.list file was modified (feisty to gutsy repositories).
- /var/log/dist-upgrade/main.log last line:```
2007-10-19 04:33:34,514 DEBUG entry '# deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets' was disabled (unknown mirror)
```
- /var/log/dist-upgrade/main_pre_reg.log: <empty>
- I waited for this upgrade from 4:30 am to 9:30 am and nothing has changed in five hours.


What should I do? Should I kill the process and start everything over?

Thanks in advance.

---

### Post by holomorph on 2007-10-19
yes, kill the process. It's not going anywhere. 

You can try starting over, but I doubt that'll help anything.  I've been struggling with this for two days and as of yet haven't been able to upgrade, despite trying at least 4 different ways.  Besides, at this point the repositories are probably pretty busy, so upgrading over the net is going to be a bit slower. You may just want to wait a few days and maybe this issue will get fixed.

It would be nice to know what else the upgrade scripts do besides change the sources list and do an apt-get dist-upgrade, then we could work around this with a bit more confidence.

---

### Post by ddcc on 2007-10-19
I've removed all of my third party repositories, so I know that's not the issue. What I have noticed, however, is that whenever I do sudo apt-get update (as well as using the GUI), it always stops on file 15 for a whole minute, which is contacting us.archive.ubuntu.com. Has anyone else noticed the same thing recently?

---

### Post by Schroeder on 2007-10-19
> **ddcc said:**
> What I have noticed, however, is that whenever I do sudo apt-get update (as well as using the GUI), it always stops on file 15 for a whole minute, which is contacting us.archive.ubuntu.com. Has anyone else noticed the same thing recently?

I guess that's because the servers are overloaded. I have the same problem with a regular apt-get (without dist-upgrade). Normal a day after the official release of Gutsy I guess.

---

### Post by PCZahra on 2007-10-19
I have the same problem. I left it overnight to download the files and this morning it "unexpectadly closed" with 20 minutes remaining. Since then I've restored the old sources.list and run the upgrade several times and it crashes on "preparing the upgrade" or hangs on "modifying software channels" and restores the previous configuration on its own. as a matter of fact, it's hanging on the first step right now.

---

### Post by ddcc on 2007-10-19
I did a sudo apt-get clean and autoremove, as well as install ubuntu-desktop and prune off some unnecessary packages, and after restarting, it's going fine for me today. It's now started to download the new packages on my 32-bit machine, I'm going to go see if my 64-bit machine updates now.

---

### Post by gaiterin on 2007-10-19
Same problem in a new installation of Ubuntu 7.10 in a HP nx7300 Laptop :(

---

### Post by el_sombra on 2007-10-19
I finally killed the process, opened a konsole and executed "sudo apt-get dist-upgrade". It's still upgrading (6 hours approx. with 4 hours ETA).

Let's hope this works.

---

### Post by PCZahra on 2007-10-19
> **ddcc said:**
> I did a sudo apt-get clean and autoremove, as well as install ubuntu-desktop and prune off some unnecessary packages, and after restarting, it's going fine for me today.
apt-get clean eh? I think I'll try that one.

---

### Post by PCZahra on 2007-10-19
you know, it occurs to me, everyone in this thread probably downloaded the whole thing several times trying to get this to work right. I know I did. I think it would've been a lot faster and less strain on the servers if they'd provided an ISO of all the essential packages to upgrade with, and send that out on a torrent.

---

### Post by Schroeder on 2007-10-19
> **PCZahra said:**
> you know, it occurs to me, everyone in this thread probably downloaded the whole thing several times trying to get this to work right. I know I did. I think it would've been a lot faster and less strain on the servers if they'd provided an ISO of all the essential packages to upgrade with, and send that out on a torrent.

Or somebody could fix the bug...:)

---

### Post by PCZahra on 2007-10-19
> **Schroeder said:**
> Or somebody could fix the bug...:)

yeah... that'd work too.

---

### Post by gaiterin on 2007-10-20
Hi!
I had got the same problem.

TO FIX:
Go menu: System / Administration / Software Sources.

I checked in the first tab:
Canonical-supported open....
Community-maintained open...
Propietary driver....
Sofware restricted by copyright....

I checked in the second tab:
Third-party....

I unchecked in the first tab:
Source code.....
Cdrom with Ubuntu 7.10.....

It works now perfect :D

Marquinos.

---

### Post by el_sombra on 2007-10-20
After a very struggling battle, I _think_ I'm running my Gutsy upgrade :P

What did I do? In a konsole:

sudo apt-get dist-upgrade
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f

And several sudo apt-get update/upgrade more until apt-get just didn't update the remaining 44 (or so) packages left to update... So I rebooted. Everything seemed to be ok...

So I executed Adept Manager and the infamous "Version Upgrade" appeared again. I did what I had done before according to the "official upgrade method" and it just worked like a charm! :) (of course I didn't have to wait 11 hours to download everything again :P)

Cheers!

/el_sombra

PS: By the way, there's a snort process eating almost 170 MB of memory... Any info on this?

---

### Post by Domhnull on 2007-10-20
I fixed my error with it hanging by going to System | Administration | Software Sources and switching the server to the US server instead of the 'Main Server'.  After it reloaded the sources I ran the Update Manager and clicked the Upgrade button as recommended.  It didn't hang then.

---

### Post by Schroeder on 2007-10-20
> **Domhnull said:**
> I fixed my error with it hanging by going to System | Administration | Software Sources and switching the server to the US server instead of the 'Main Server'.  After it reloaded the sources I ran the Update Manager and clicked the Upgrade button as recommended.  It didn't hang then.

Doesn't solve the problem that the OP (and the filed bug) were referring to. Your update-manager was hanging because of a timeout from an update server (which you solved by going to another server). My update-manager gets all the lists of source packages from the servers and still hangs.

---

### Post by PartisanEntity on 2007-10-20
Hi I have the same problem:

When upgrading from web it will hang at 'reading cache'.

When upgrading from the alternate cd it will hang at 'checking package manager'.

I tried changing source servers but that did not help.

This same issue has also been reported here:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153984](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153984)
[https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296](https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296)
[http://ubuntuforums.org/showthread.php?t=582922](http://ubuntuforums.org/showthread.php?t=582922)
[http://ubuntuforums.org/showthread.php?t=582927](http://ubuntuforums.org/showthread.php?t=582927)

---

### Post by SammyBoy247 on 2007-10-21
I removed all third party software sources, simply by editing the "Third Party Software" tab in "System - Admin - Software Sources"

then 

gksudo "update-manager -d -c"

Click, click, Smiles

---

### Post by ddcc on 2007-10-21
It looks like removing 3rd party repositories is a key fix.

---

### Post by PartisanEntity on 2007-10-21
Hmm, I tried removing third party repos, unfortunately it didn't work.

---

### Post by ddcc on 2007-10-21
> **PartisanEntity said:**
> Hmm, I tried removing third party repos, unfortunately it didn't work.

I'm not sure if this will work for you, but here's what I did.
sudo apt-get update
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install ubuntu-desktop
removed 3rd party repositories and their gpg keys
restart
sudo apt-get upgrade (install the tzdata upgrade)
sudo apt-get update
sudo /etc/init.d/tor stop
sudo /etc/init.d/privoxy stop
close pidgin
update-manager > "Update"

---

### Post by PCZahra on 2007-10-21
I believe I have a solution. It's currently running and almost finished, so I'm not sure yet if this is a definite fix (but it certainly looks like it)

*run all commands as sudo, just to be sure

1. Download the Ubuntu 7.10 **alternate cd** for upgrading computers without an internet connection.
2. I have a directory for mounting iso files without burning them to cd. If you don't
```
mkdir /media/iso
```
3. Mount the image
```
mount -t iso9660 -o loop Desktop/ubuntu-7.10-alternate-i386.iso /media/iso
```
3. Use <Alt>F2 to run
```
gksu "sh /media/iso/cdromupgrade"
```
4. Turn off the internet. I tried the next step with the internet on and it crashed as usual, so I'm thinking the appearance of the Update Manager is interfering with the process. With the internet off, the software channels are changed to Gutsy properly because the Update manager does not appear and screw it up. This must be where the bug lies - Upgrade needs to suppress the scheduled Update.
5. Follow the prompts and let the Upgrade Manager do its thing. Remember that if it asks you to use the internet for anything say NO. You can do that later.

now it's cleaning up. gotta post this before it restarts, no time to spell check, bye!

---

### Post by PCZahra on 2007-10-21
now I have no screen :(

---

### Post by PartisanEntity on 2007-10-21
I gave up on the upgrade and did a fresh install. Everything is working, no issues.

---

### Post by PCZahra on 2007-10-21
I don't have a cd burner. bootup seems to work, but then the monitor goes into powersave mode and the whole thing stops. I'm running off the Feisty live cd now. any ideas? that iso file of the alternate cd is supposed to mount on startup. here's the fstab: ```
/home/zahra/Desktop/ubuntu-7.10-alternate-i386.iso /media/iso udf,iso9660 user,loop 0 0
```
(just noticed no line break at the end. does that need to be there? )

---

### Post by ArNegro on 2007-10-21
Hi everybody,

> **PartisanEntity said:**
> I gave up on the upgrade and did a fresh install. Everything is working, no issues.

I'm about to do the same. Could you post a short summary of what you did to set up your new system? I'm wondering which folders I should backup to keep using them in the new system. I read it would be good to make a backup of /etc and /usr, but what do I do with them? Do I just copy them back into my new installation?

---

### Post by holomorph on 2007-10-21
I'd make sure you have your /home/ directory backed up.  /etc/ not a bad idea as well, but I wouldn't just copy it back over; that's bound to cause trouble.  I would just use the /etc backup as reference in case something doesn't work that used to work.

I never did get the upgrade to work for me using any of the upgrade scripts, but I suspect PCZahra's suggestion about mounting the iso and turning off the internet is a good one (I tried similar, but didn't turn off my connection).  Also ddcc's 'apt-get' song and dance should help clearing things out.  I would suggest trying that, and then mount the iso thing.

What I ended up doing in the end was mounting the iso, adding it as the only repository in my sources list, and then doing 'apt-get dist-upgrade'.  After that finished I re-enabled the net repos and did it again.  That's gotten my system upgraded, but things were severely broken for a bit.  Most notably, the kernel was not booting giving 'dev-mapper:table:252:3:linea:dm-linear:Device lookup failed' over and over.  Seems having the evms package installed was the problem there, so unless you know you need it, uninstalling that is a good idea if you go the dis-upgrade rout.  The only other thing I've really had a struggle with is my X setup - but then I've got a dual head setup, so it's a bit less straight forward.  Hopefully most people have less hassle with this.

I'm not sure what else those scripts are doing besides the dist-upgrade, but I guess if you're ready to do a fresh install anyway, it probably won't hurt anything :P.  Then again, a fresh install definitely gets you a cleaner system.


Oh, and if you do a fresh install and don't want to have to manually re-pick all your other apps to install (that don't come installed by default) you can get a list of what's currently installed before you re-install by 'dpkg -l' (or if you want just the package name w/o other info ```
dpkg -l | cut -f3 -s -d' '
```, you should be able to feed this list back to apt-get after you do your install)

---

### Post by PartisanEntity on 2007-10-22
> **ArNegro said:**
> Hi everybody,



I'm about to do the same. Could you post a short summary of what you did to set up your new system? I'm wondering which folders I should backup to keep using them in the new system. I read it would be good to make a backup of /etc and /usr, but what do I do with them? Do I just copy them back into my new installation?

I use rsync to make backups of my entire home partition, so I made sure I had an up to date backup before installing. I don't bother backing up any other files or folders on the system.

---

### Post by Schroeder on 2007-10-22
For those who don't want to do a fresh install:

From user Kim Sullivan in the bug commentaries on launchpad:

"Since this seems to be a bug only with the GTK frontend, I simply circumvented it by using a different frontend, instead of hacking the scripts. This has the addidional benefit that you actually get the confirmation dialog, and can have a look which packages will be removed.
 

cd /tmp/tmpXXXXXX (temporary directory where gutsy updater was downloaded)
./gutsy --help
sudo ./gutsy --frontend=DistUpgradeViewText --have-prerequists --with-network
 

You might also want to try DistUpgradeViewKDE (even if you're on Ubuntu) to get a graphical frontend (but I haven't tested it)."
 

Worked for me...upgrading now.

:guitar:

---

### Post by Schroeder on 2007-10-22
Update went fairly well. The only thing that didnt work out was the upgrade of openoffice 2.2 to 2.3. For some reason the update manager failed upgrading the openoffice package. I had to manually update it. Other than that I am up and running. Liking it so far. Seems a little bit snappier on my hardware than Feisty. :)

---

### Post by Cowloon on 2007-12-07
Edit: Okay I get it, those lines are similar to what the cdromupgrade script does, but the frontend is changed. What does --have-prerequisites mean?







> **Schroeder said:**
> 
cd /tmp/tmpXXXXXX (temporary directory where gutsy updater was downloaded)
./gutsy --help
sudo ./gutsy --frontend=DistUpgradeViewText --have-prerequists --with-network


Did you manage to upgrade? Can you elaborate? How are you getting /tmp/tmpXXXXX containing a gutsy updater?

I am trying to go from edgy to gutsy. I used upgrade manager to upgrade from edgy to feisty and had no problem other than it taking incredibly long to do. So, for feisty to gutsy I'm trying to use cdupgrade, but it hangs while trying to get package information.

About apt-get lines. The log has lines like:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)

If I try to look at that address in my web browser, there is no directory called "i18n" below "restricted". Should there be?

I tried switching sources from US to Main and it han's getting package information for feisty. So I switched back to US.

---

### Post by nerips on 2008-01-12
Hi there,
i've got the same problem with several archive servers (gb, us, main)
None of the solutions from this thread did help.
Opening "Software sources" selecting "other.." and then letting ubuntu propose the best server - i could upgrade without any problem.
I suppose the problem was a sort of time-out, constantly hanging on some file while "preparing the upgrade" or "modifying the software channels".

---

### Post by diablo75 on 2008-04-04
I am having the same problem, even after disabling all third party sources.

Now my update manager says I have a "partial upgrade" available, and about 645 megs worth of downloads.  I don't think I should just click "Partial Upgrade", should I?

How might I reverse the effects of what I originally did, which was type sudo update-manager -c -d ?

---

### Post by litmos95 on 2008-04-25
I think I know the remedy, try to change the "Download from" in the System>Administration>Software Sources to any server near you. It should work then.

---

