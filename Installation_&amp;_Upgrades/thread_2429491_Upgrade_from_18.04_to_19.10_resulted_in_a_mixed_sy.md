---
title: "Upgrade from 18.04 to 19.10 resulted in a mixed system"
date: 2019-10-18
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2019-10-18
I attempted an upgrade from 18.04 to 19.04 (anticipating going to 19.10 a week from now) using "sudo apt dist-upgrade" and it had problems with over 500 broken packages. ...unfortunately I am not sure what went wrong here and do not have those error messages. I was hoping synaptic would resolve the package issues but when I tried to install synaptic I get lock errors and I can't get synaptic installed (is their another program I can use?).  

Then I tried to run various versions of apt update with -f, --fix-missing, ...etc and sudo dpkg --configure -a   ...following the suggestions at: [https://www.maketecheasier.com/fix-broken-packages-ubuntu/](https://www.maketecheasier.com/fix-broken-packages-ubuntu/) ...and [https://www.itsmarttricks.com/fix-dpkg-error-dpkg-frontend-lock-is-locked-by-another-process/](https://www.itsmarttricks.com/fix-dpkg-error-dpkg-frontend-lock-is-locked-by-another-process/)  ....and [https://www.maketecheasier.com/fix-ubuntu-update-errors/](https://www.maketecheasier.com/fix-ubuntu-update-errors/)  I even attempted a partial upgrade when the package manger offered the message (probably not a good thing to do considering over 500 packages were identified as issues. The partial upgrade ran a bit and then failed and along with dpkg and apt all return various error messages such frontend is locked by another process, missing dependencies, lock errors, python errors. directories not found..etc.  I can't do anything to manage the packages or deal with the package  issues.  Things are very strange.

The odd part is **the system operates normally as a user** Libre office, browsers, skype  ...etc. all work normally but the desktop icons are not configured so they are on the desktop default greyed out but clickable and operate normally. 

**I believe I have mixed version of the system** because the system shows a tools symbol of a wrench and screwdriver from 18.04 and when I click on it, it will not load the settings ...but lsb_release -a says I am 19.04. Is there something I can do to salvage the system such as command that resets all the package information and gets things cleaned up enough that apt or dpkg operate correctly.  If so please suggest a plan of attack. I'd like to save the system but I am confused on where to start to straighten out the packages mess. I appreciate any assistance.

---

### Post by #&amp;thj^% on 2019-10-18
NOTE: It was just released yesterday so might need some time to place everything in the Repos.
I use a few tools with a pre-exisiting install (Point release to Point release)
Another good habit which makes the upgrade easier (and shorter) is to tidy your installed packages and keep only the ones that are really needed. Helpful tools to do that include **aptitude**, **deborphan.**
```

# deborphan | xargs aptitude --schedule-only remove debfoster
```
If all is well, Then I next run:
```
sudo aptitude full-upgrade
```
Now before proceeding I carefully check the proposed actions from the terminal.

---

### Post by jgwphd on 2019-10-18
I am not familiar with these commands. I believe, the first one will identify and remove packages I don't need. Is that correct? If true and assuming the first command completes successfully, will the second command get me to 19.04 or 19.10?

---

### Post by #&amp;thj^% on 2019-10-18
> **jgwphd said:**
> I am not familiar with these commands. I believe, the first one will identify and remove packages I don't need. Is that correct? 

yes that's correct.
> **jgwphd said:**
>  will the second command get me to 19.04 or 19.10?

That remains a mystery. :p In all seriousness it should just up-grade your existing OS, but we are not sure what you have yet. ;)

---

### Post by jgwphd on 2019-10-18
I can't install either of the programs I am getting similar errors as when I run the package manager or apt dkpg ...etc. 
[ATTACH=CONFIG]284207[/ATTACH][ATTACH=CONFIG]284211[/ATTACH][ATTACH=CONFIG]284212[/ATTACH]

---

### Post by #&amp;thj^% on 2019-10-18
I don't fare well with pictures, Copy and paste (in code tags) is so much better.
1. Do you now have a good back-up?!
2.Try to remove "hplip" it seems to be stuck there.
3.Next Run "sudo apt autoremove" and post back the return for that please no pictures, copy and paste only.

---

### Post by jgwphd on 2019-10-18
I tried again to install deborphan with sudo. It seems when ever i have to run the package manager I get python error that kicks off a string of other errors. The attached clearly shows the issues with "560 not fully installed or removed" then it fetches "package deborphan", then unpacks it, sets up python3, then runs some python hooks, then can't create a directory message - notice hplip in the directory it's trying to create. - this is the HP printer driver. All the installs follow this pattern. My GUESS is it starts to install what you asked for but sees the other 560 packages sitting there needing attention and decides to do them first and HP is first on the list (my guess). Is there a way to get rid of this "not fully installed or removed" stuff?

[ATTACH=CONFIG]284215[/ATTACH]

---

### Post by jgwphd on 2019-10-18
My previous post crossed in the mail with yours. My concern is that HP is a symptom and just happens to be first of the 560 packages to be installed listed and if I delete it then I'll just get to the next one and get stuck there ...but then I won't have a printer. Your thoughts. But I am willing to try.... if I get the system functional again I can always reinstall it.

---

### Post by Frogs Hair on 2019-10-18
One of your images displays disco dingo repositories which is 19.04. Typically upgrades go in order , but with 18.10 being unsupported the process may change. If you have good backups it may be worth performing a clean installation. If you do end up with a clean upgrade to 19.04 you still have another upgrade to get through.

---

### Post by #&amp;thj^% on 2019-10-18
> **Frogs Hair said:**
> One of your images displays disco dingo repositories which is 19.04. Typically upgrades go in order , but with 18.10 being unsupported the process may change. If you have good backups it may be worth performing a clean installation. If you do end up with a clean upgrade to 19.04 you still have another upgrade to get through.
+1 :D

> **jgwphd said:**
> but then I won't have a printer. Your thoughts. But I am willing to try.... if I get the system functional again I can always reinstall it.

We need a stable OS before we can add features, Right?
I'm not saying this will fix it, IJDK, There is no magic bullet, or one liner that will magically fix the system.
This may take a lot of trial and error. :(

---

### Post by jgwphd on 2019-10-18
FYI ....I did the sudo apt autoremove and got the same sequence of a python error that kicks off a string of other errors and the hplip directory is the first python and subsequent error messages again. hplip seems to be involved in what I do with packages. Before I remove hplip from the system (if I can) I just want to get your thoughts about my prior two posts. Thanks for you assistance and patience!

---

### Post by Impavidus on 2019-10-18
Now I'm wondering with what command you actually started. I know **sudo apt-get dist-upgrade**, I know **sudo apt upgrade**, I know **sudo apt full-upgrade**, I even know **sudo do-release-upgrade** (which is the one that should have upgraded to 19.04), but no **sudo apt dist-upgrade**. The random commands you ran next may have made things worse.

Anyway, your package management is screwed up and you want to get to another release. What about a clean install of that new release? It's the fast way out of your problem.

---

### Post by jgwphd on 2019-10-18
Again, our posts crossed in the system. I was hoping you had a magic command   LoL!  ....I guess I'll remove the printer and see where things go from there and do some trial and error ...and when sufficiently frustrated then do a fresh install. I keep thinking that if I could purge that list of 560 packages waiting in the background somewhere that might do it. That's where the magic command comes into play  :-)

---

### Post by jgwphd on 2019-10-18
I used the command "sudo apt dist-upgrade" which was recommended here: [https://linuxhint.com/upgrade_ubuntu_1904/](https://linuxhint.com/upgrade_ubuntu_1904/)

---

### Post by #&amp;thj^% on 2019-10-18
FWIW:apt full-upgrade performs the same function as apt-get dist-upgrade.
> 
man apt

   full-upgrade (apt-get(8))
       full-upgrade performs the function of upgrade but will remove currently installed packages if this is needed to upgrade the system as a whole.
Forgot to add: for Ubuntu 16.04 and forward is "apt" instead of "apt-get"
You can do either apt dist-upgrade (I just tried it) or you can do apt full-upgrade. (They tried to remove the confusion of a newer version OS being installed)

---

### Post by rsteinmetz70112 on 2019-10-18
I'd recommend not doing anything else until you have a stable system. 

Run:
```
sudo dpkg --configure -a 
sudo apt install -f
```

The first command configures and packages install and not yet configured it will also provide information of the status of the package management system, missing dependencies and other information.

If they both run cleanly you are good to go.

Post any output from the commands and we can see what needs to be done.

---

### Post by mc4man on 2019-10-19
I would suspect the method you choose , editing release-upgrades & then a do-release-upgrade command skipped 18.10  because it's no longer a release..
If so then you attempted  a 'dist-upgrade' on 18.04 with a 19.04 sources list. This is the likely cause of all your broken packages, some of which are fairly significant like some python3*  packages..

There is no magic command to fix this mess.

You could eventually 'resolve' by muddling thru either replacing  all of the existing 18.04 packages with their 19.04 equivalents or more realistically by doing the opposite.
The work could be lessened by first removing all unnecessary involved packages that can be removed.
This will likely take you quite some time, (hours, maybe spread out over days if requiring help) & as far as getting help - not easily done or impossible thru screenshots.

On the other hand you could be on your merry way in less than an hr. with a fresh 19.10 install

---

### Post by jgwphd on 2019-10-19
One more question: should I try to get to 19.10 (if available)?  ...and if so what exact commands or command sequence should I follow?  I'd like to try that before I give up and do a fresh install. 

FWIW, This is the third time (over the last 10 years) that I tried to upgrade an Ubuntu system sequentially from multiple releases back and got in trouble ...and finally wound up doing a fresh install. There should be a separate install command tailored for this kind of multi-release situation with the appropriate helpful instructions. I always check before I do a multi-release upgrade this to see what other suggest or have learned, but still get into trouble. I suspect many others have gotten into trouble and just gave up and did a fresh install too. 

BTW @rsteimetz70112 I tried the commands sudo dpkg --configure -a and sudo apt install -f. They don't work and result in installation errors that I previously described.

---

### Post by Impavidus on 2019-10-19
You can only upgrade to the next release if your package management is in a clean state. Upgrading never fixes package management issues.

In my experience release upgrades always work and I've done a lot of them, but always from one release to the next or from one LTS release to the next LTS release and I keep my systems clean. Even then, some home-made programs may need some changes to work on the new version of Ubuntu. Other people may be less successful.

It seems that apt dist-upgrade is an alias for apt full-upgrade, I think, but it's not mentioned in the man page. Curious. Anyway, that's to upgrade all packages to the latest version in the current release. To move to the next release, use do-release-upgrade (or use the gui).

---

### Post by jgwphd on 2019-10-19
I am closing this problem and doing a fresh install (I am done with this multi-release upgrade attempt ...sigh). That's four times I have had major issues. There must be a better way to help or instruct people how to attempt this kind of upgrade. It seems it is way too easy to screw up your system with the wrong command. ...so ...how about a warning message that says "are you sure you want to do this' or simply prevent this with an error message if you are trying to upgrade beyond the next release. I am sure I am not the only one that feels that way  :-)

---

### Post by mc4man on 2019-10-19
> **jgwphd said:**
> I am closing this problem and doing a fresh install (I am done with this multi-release upgrade attempt ...sigh). That's four times I have had major issues. There must be a better way to help or instruct people how to attempt this kind of upgrade. It seems it is way too easy to screw up your system with the wrong command. ...so ...how about a warning message that says "are you sure you want to do this' or simply prevent this with an error message if you are trying to upgrade beyond the next release. I am sure I am not the only one that feels that way  :-)
There is a built-in method for users that don't get rid of update-notifier. They would be informed every couple of weeks that a new release, (either a next version or next lts..),  was available based on the setting in Software & Updates until they either said yes or declined (ignore.
Once declined then it's set in the ignore list, ex. 

"WARNING:root:found new dist 'bionic' but it is on the ignore list"
result of which is screen 2

But that has to be done before the next release goes EOL and is moved to Old-releases or wait for next LTS
In your case you waited too long..

Typically can be checked by running
```
/usr/lib/ubuntu-release-upgrader/check-new-release-gtk
```

If you were to run that on 18.04.x it wouldn't return anything atm as the next release (18.10) is EOL & the next LTS isn't available yet.
Running it on 16.04.x shows as in screen 1.

I believe the method you followed went ahead and switched your sources 19.04 repos.

Personally I just do fresh and copy out any files 1st. sometimes compressing them to maintain permissions. Quicker and easier..

There is a method to preserve Home when it's installed to /  , just don't format the fresh install and use same user name. Here have tried a variation which is to - 
From live system mount existing install
As root delete all folders and files in / except the Home directory
Unmount, do install via something else to the partition where previous is, no format

---

### Post by Impavidus on 2019-10-20
> **jgwphd said:**
> It seems it is way too easy to screw up your system with the wrong command. ...so ...how about a warning message that says "are you sure you want to do this' or simply prevent this with an error message if you are trying to upgrade beyond the next release.

In the Linux world, the policy is to assume the user knows what he's doing. If you're doing something the developer hasn't foreseen, it must be either something very stupid or something very clever. The software can't tell, the software only knows what the developer has built in. In the Linux world, the user has the freedom to do very clever things. The price is that you can also do very stupid things.

---

### Post by jgwphd on 2019-10-22
But, ...even very smart and very clever people make mistakes. We are human and it would be nice at times that a warning message is issued as a reminder that we are about to do something very cleaver or very stupid and help us protect us from ourselves if it is in the very stupid category   :-)     

BTW, I have 19.10 running with a fresh install. .....and FWIW I don't think this entered into the problem but my hard drive is now getting errors (enough so it only boots intermittently goes to busybox or just stalls with a blank screen). I used live USB 19.10 and GSmartControl is showing lots of read errors. I have a new one in the mail. Everything happens at once ...Murphy is alive and well   LoL!

I truly appreciate all the explanations and suggestions and I'd like to sincerely thank everyone for all their help! You guys are awesome!  MANY THANKS!!!!!

---

### Post by rsteinmetz70112 on 2019-10-22
WIndows assumes you're and idiot. 
*inux assumes you know what you're doing.

There are lots of problems with bot approaches.

---

### Post by jgwphd on 2019-10-23
One final question, since I have been into packages a lot lately (had another upgrade hang on another machine, this time, from 19.04 to 19.10 - fixed it in recovery. The system runs normally now.). My question is how can someone tell if the package manage system has been corrupted in some way ....i.e the basic question, is it healthy? When I run the command: "dpkg --configure -a" it returns no output and goes back to the command line. Is there anything else I could check? ....just to feel more comfortable about the system. Thanks for any suggestions.

---

### Post by deadflowr on 2019-10-23
Software Updater and/or apt cli will always show any issues when run.
As well as log files for apt, unattended-upgrades, and dpkg in the /var/log directory.

---

### Post by jgwphd on 2019-10-23
Thanks  ...everything looks "normal"   ....what ever that is?  LoL     I SINCERELY APPRECIATE ALL THE ADVICE AND SUGGESTIONS. AGAIN MANY MANY THANKS!

---

