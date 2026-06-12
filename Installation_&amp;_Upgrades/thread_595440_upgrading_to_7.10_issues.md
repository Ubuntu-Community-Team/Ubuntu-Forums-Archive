---
title: "upgrading to 7.10 issues"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Rex72 on 2007-10-28
I have installed all the latest updates for 7.04 yet when I try to upgrade via network Update Manage I get the following missing items and then it kicks me out.

Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

What must I do to fix this in order to complete the install?

Thank you
__________________

---

### Post by It_Was_Luck on 2007-10-28
Did you use the "official" upgrade method?

```
$ gksu "update-manager -c"
```

---

### Post by Rex72 on 2007-10-28
No..

I was simply following the instructions given by the install section via Update Manager.

---

### Post by Rex72 on 2007-10-28
Oh and I prefer using Update Manager as instructions says.

Any ideas?

---

### Post by tim1000000 on 2007-10-30
i get exactly the same error. all updates are installed and all i'm doing is simply following the on-screen instructions, just like the OP. any help on this would be great, google brings up nothing.

the method It_Was_Luck suggested results in the exact same error by the way

---

### Post by Rex72 on 2007-10-30
I simply gave up and did a fresh install via CD.

Im on 7.10 now..  Wasn't too hard copying my personal content over to external USB HDD before the install.

---

### Post by aaamos on 2007-10-30
I've been getting the same error since 7.10 became available. At first I figured it must have something to do with one of the distributors not having all the required files during the first rush for the upgrade, and that it would surely be fixed once it became known. I'm still not in a particular hurry to upgrade from feisty to gusty, but, come on, it's been weeks now... somebody fix this already. Pretty please.

Oh, and the error message "Error during update" says: "A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry." It's obviously not a network/connection problem, since the upgrade process downloads quite a few other bits and pieces before that error message appears and the upgrade aborts.

Seriously, please at least give us a semi-official response saying that somebody is aware of the problem and that it's being worked on, or, better yet, give us a solution/workaround.

Cheers,

aaamos

---

### Post by tim1000000 on 2007-10-31
it's just a shoddy implementation. i was originally getting two other errors which i eradicated by inserting my ubuntu cd, but nowhere during the upgrade process does it mention inserting such a cd. i guess i'll just wait for someone to fix it but it'd be nice to know for sure that it's not a problem at my end.

---

### Post by aaamos on 2007-10-31
> **Rex72 said:**
> I simply gave up and did a fresh install via CD.

Im on 7.10 now..  Wasn't too hard copying my personal content over to external USB HDD before the install.

Sadly, having to do a clean install from CD isn't really an option for me (or at least a very bad option), since I have several things installed that aren't so easy to re-install... I'd rather stick with 7.04 and hope they fix the bug (soonish).

Incidentally, I had a look through the launchpad bugs, and couldn't find the same bug (though there were a few similar ones). Hence, I reported it as [bug 158897]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/158897") - let's hope it gets some attention. There's also [this thread]("http://ubuntuforums.org/showthread.php?p=3620310") in these forums which seems to be the same problem.

---

### Post by StevenRoose3 on 2007-10-31
i just dont have an internet connection.

also HAL isn't working.

i really need help: see [http://ubuntuforums.org/showthread.php?t=598185](http://ubuntuforums.org/showthread.php?t=598185)

Steven

---

### Post by computer_user_au on 2007-10-31
As a temp fix, try command:
```
sudo /etc/init.d/dbus restart
```

The check out he fix in thread:
[http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL]("http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL")

Good luck.

---

### Post by aaamos on 2007-10-31
[Yet another thread]("http://ubuntuforums.org/showthread.php?t=588830") with the "Sub-process bzip2" Problem. Hopefully, the more users report that problem, the more attention it'll get.

---

### Post by computer_user_au on 2007-11-01
Also, check out:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")

I manually did the following on my system:

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

rebooted and the system worked, no more "Failure to initialize HAL" error messages and my network connection is working well.

---

### Post by tim1000000 on 2007-11-01
sorry, computer_user_au, do those fixes help with the original problem or is that targetted at StevenRoose3

---

### Post by ghetto2ivy on 2007-11-01
Ditto on the original post here (I dont knwo how the HAL problem got mixed up with this post.)

```
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz
```

Every single time I try to update. Same on laptop and on desktop. I don't get it. 7.04 upgrade went off without a hitch. Please don't say fresh reinstall. This is not windows --I'm trying to get out of that habit of solving everything by doing a fresh install. 

I get offered a partial upgrade and the tool has changed my sources to be gutsy sources.
I paired down my sources to the following and no further progress. 
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy universe

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-security restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe

deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security restricted multiverse
```

I tried doing an alternate cd-rom upgrade and got nowhere fast either.

---

### Post by ghetto2ivy on 2007-11-01
Not definative, becuase it isn't finished yet, but I did the following to fix the problem:

1) Launch System>Software Sources
2) Remove all third party sources (Some of them were not third party sources but I digress.) Unchecked all sources and closed,
3) Re-opened System>Software Sources
4) Checked the appropriate sources in the main and updates tabs. Closed the app.
5) began a CDrom update, though I'm sure any other one would have started fine.

---

### Post by aaamos on 2007-11-01
> **aaamos said:**
> [Yet another thread]("http://ubuntuforums.org/showthread.php?t=588830") with the "Sub-process bzip2" Problem. Hopefully, the more users report that problem, the more attention it'll get.

I have to say I'm severely disappointed with the lack of support for this issue. After searching some more, it seems this is an ancient problem with hundreds of posts in this forum alone ([http://www.google.com/search?hl=en&client=opera&rls=en&hs=aRj&q=+site:ubuntuforums.org+failed-to-fetch+%22Sub-process+bzip2%22](http://www.google.com/search?hl=en&client=opera&rls=en&hs=aRj&q=+site:ubuntuforums.org+failed-to-fetch+%22Sub-process+bzip2%22)), and hundreds more elsewhere ([http://www.google.com/search?client=opera&rls=en&q=failed-to-fetch+%22Sub-process+bzip2%22&sourceid=opera&num=50&ie=utf-8&oe=utf-8](http://www.google.com/search?client=opera&rls=en&q=failed-to-fetch+%22Sub-process+bzip2%22&sourceid=opera&num=50&ie=utf-8&oe=utf-8)). Not just about the upgrade to 7.10, but way, way before that. Apparently it's been "known" in launchpad for ages as well ([https://bugs.launchpad.net/apt/+bug/113162](https://bugs.launchpad.net/apt/+bug/113162)), and a bugreport that old with status "Incomplete" and importance "Undecided" doesn't bode well, imho.

Please, somebody tell me that I didn't make a mistake in choosing Ubuntu... this sort of issue in conjunction with the other minor and major hiccups I've seen makes me wonder whether this OS is as mature as I was led to believe. Sorry, I don't mean to lose faith at the first hurdle (I *have* crossed a few despite being relatively new to Ubuntu), but I shy away from having to read 400 posts where people report the same problem - and no solution in sight.

---

### Post by tim1000000 on 2007-11-02
yeah I've been a bit disheartened by this too. I don't want to delve into what I imagine is forum cliche (that should have an accent on but i can't work out how to do it in ubuntu :() and compare it to Windows or something, but almost every non-trivial task I've had to perform has been littered with problems and required way more effort and internet-searching than I'd have liked. Don't get me wrong, I love the idea and I'd probably be hard-pressed to find a better (free) alternative, but perhaps it needs a few more releases in order to properly mature.

I've given what getto2ivy said a try, it exited with the exact same message only there were now four errors instead of two. Also opening up "Source manager" and removing third party sources seems to have forced Ubuntu into looking for 'backport' updates, and I can't untick this box in order to turn it off. No idea why, baffling.

---

### Post by ghetto2ivy on 2007-11-03
I can officially say that I was able to upgrade to gutsy using the method I described above.

The Solution is definitely clearing out your /etc/apt/sources.list and having the Software Sources app   essentially recreate the file. Its probably due to some common non-upgraded third party repositories. It worked on two separate machines I had.

Tim100000 -- try backing up your old file, then creating an empty sources.list

```

$ sudo mv /etc/apt/sources.list sources.list.back
$ sudo touch /etc/apt/sources.list

```

Here were my exact steps to recreate the file:
Then go the System>Administration>Software Sources
Under Ubuntu Software add: Main (download from server for US)
Under Updates add: security, update(select: Check for updates)
Click close.

It should ask you to refresh your sources and all should go well. You should get the update icon, and have Upgrade distribution button.

It installed fine, and has been running fine for two days, including a reboot for the hell of it.

Hope this helps!

---

### Post by aaamos on 2007-11-05
Well, first off, thanks ghetto2ivy for pointing out your solution. I tried, albeit reluctantly, to follow your steps and did, in the end, manage to get my system both "upgraded to 7.10" and "back to normal".

Having said that, I'd recommend to others looking for a solution/workaround to the "Sub-process bzip2" problem to think twice about whether the upgrade is worth the hassle. Unless you specifically need one of the changes from feisty to gutsy, it may be easier to simply live with 7.04 for at least a while longer.

Some of the problems I had after the upgrade included:

* Having to wait forever for the upgrade to install after it was downloaded, as it kept asking, in regularly inconvenient intervals, about whether some customised config files should be kept or overwritten (you sit there for 5 minutes watching the upgrade, decide it's just going to run fine now, leave it, come back an hour later only to find that it didn't get much further than last time and is now asking the next question... and so on ad nauseum).

* Discovering that, after the upgrade and the reboot, my network connection was no longer working, having to dig through firstly my memory and secondly the Internet (on my other machine, of course, since the Ubuntu machine couldn't so much as ping anything) and finally finding (again, as I had a few months ago when I got 7.04) the link I needed to manually change a ridiculously obscure setting to re-enable my network connection. For those of you with a similar problem, here's the link (of course I've now bookmarked it, but didn't the first time since I thought it was a one-off thing): [http://ubuntuforums.org/showthread.php?t=219016](http://ubuntuforums.org/showthread.php?t=219016)

* Separately upgrading my Nvidia drivers simply to get back to my monitor's native 1280x1024 resolution, as the upgrade left the Nvidia item in the Applications > System Tools menu a useless relic and the default resolutions offered by Ubuntu maxed out at 800x600 initially and then 1024x768 once I played around with some settings.

* Finding out that the fonts I'd installed via Automatix were gone, and that I could neither start nor uninstall Automatix via the GUI menus. Interestingly, the Automatix website said that one has to uninstall Automatix *before* the upgrade, then reinstall the new version for 7.10 *after* the upgrade (if only I'd known that *before* the upgrade... *sigh*). Luckily, manual uninstallation via terminal and installation of the downloaded package worked (sort of, there were many odd quirks there that I won't go into...) and I once again have fonts installed that are readable and not quite so clunky.

Now maybe you won't encounter any of the problems that I did, and maybe the fact that I had Automatix/Nvidia drivers installed were involved in preventing me from having a "smooth upgrade experience" in the first place, but... come on, for crying out loud, these sorts of issues and this sort of time-wasting experience isn't something I'd wish on anyone.

Sure, Ubuntu has come a long way from the days when I used early versions of Redhat Linux at home and at uni, but it's still a pathetically long way from being even a semi-mature operating system I'd ever consider recommending to the average user. If, instead of version 7.10, it would call itself version 0.71b, I'd say it's decent beta software with great potential, and I might tinker around with it in my spare time or at least promise myself I'd keep an eye out for when the full version comes out and the rough spots are ironed out a bit.

Sorry to rant like this, apparently there are many users who have no such experiences, but I'm quite annoyed at having wasted so much time on such silly little details in what should have been a minor little upgrade.

---

### Post by tim1000000 on 2007-11-10
well it's downloading the update so it looks as if ghetto2ivy's solution is working brilliantly. thanks a lot for that! my ubuntu install isn't as 'customised' as aaamos' so hopefully i get a relatively hiccup-free install.

edit: everything went seamlessly. hurrah.

---

### Post by impert on 2007-11-14
Ghetto2ivy:

> Tim100000 -- try backing up your old file, then creating an empty sources.list

Code:

$ sudo mv /etc/apt/sources.list sources.list.back
$ sudo touch /etc/apt/sources.list

Here were my exact steps to recreate the file:
Then go the System>Administration>Software Sources
Under Ubuntu Software add: Main (download from server for US)
Under Updates add: security, update(select: Check for updates)
Click close.

It should ask you to refresh your sources and all should go well. You should get the update icon, and have Upgrade distribution button.

It installed fine, and has been running fine for two days, including a reboot for the hell of it.


My apt/sources.list is empty - clean  - virgin - nada - zilch

Under **software sources** main restricted universe and multiverse are ticked.
Under **updates** feisty security, feisty updates, and feisty backports are ticked.
I still get "Failed to fetch . . . " as per my post

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/156883]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/156883")


I'm still a fan of Ubuntu, but perhaps if you want total freedom from hassles, it might be best to go to dapper, and stay there until the next long term release comes out.

---

### Post by impert on 2007-12-11
Hi all,
I don't know if anyone is still bothered by this problem, but just for the record:
 Ghetto2ivy's suggestion didn't help me, but what did work for me was:

1.  Get into the /etc/apt/sources.list file using vim


         ```
 $ sudo vi /etc/apt/sources.list
```

(use pico/nano if you prefer) and replace all occurrences of 'feisty' with 'gutsy'. (Make a backup first if you like, but you probably already have one.)

In vim

         ```
%s/feisty/gutsy
```

Then
     ```
     :wq
```

to save and quit vim.

2 Then go to Software Sources, and in the tab 'Ubuntu sources', in the field 'Download from' choose 'other', and in the window which appears, click on 'Select best server', and use the server that the test program  suggests.

3 Start Update manager. It will tell you that there are seven-hundred-and-something updates available, and that you can't have them all at once. It will suggest a partial update. You can click on that, but it may well fail: it did for me. Click on the list of updates, and manually weed out (uncheck) all those over 1Mb in size. You should have a list totalling something under 100 Mb in all. (Update manager, bless its cotton socks, will take care of dependencies).

4 When you have a manageable list of files to update, click on install to do a partial update.

5 If step 4 fails, prune the list some more.

6  Repeat 3 and 4 until there are no updates.

NOTE 1: Leaving out step 2, as I did at first, can make things glacially slow. My 'Download from' box was set to 'Main' either by default or because I stupidly made it so. The download speed was down to 20 kb/s at times. Getting the best server brought this up to 900 kb/s. Moreover, using a mirror site unloads the main server and makes things better for everyone.

NOTE 2: It may be ugly and inelegant, but it worked for me,

---

