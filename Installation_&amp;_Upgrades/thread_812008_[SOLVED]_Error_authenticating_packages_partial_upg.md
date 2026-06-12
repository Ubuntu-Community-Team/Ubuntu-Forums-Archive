---
title: "[SOLVED] Error authenticating packages partial upgrade"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2008-05-29
Update Manager has for two or three days in a row, offered new packages. When I click "install", I get the

Not all updates can be installed

Run a partial upgrade . . .

when I click Partial Upgrade I get another "error authenticating some packages" message. 

What can I do to fix this?

---

### Post by viljun on 2008-05-29
Reboot and try again. Sounds like a windows thing but has worked for me few times.

---

### Post by sayakb on 2008-05-29
Goto System->Administration->Software Sources
Click Updates tab and **uncheck **the last 2 update sources (ie. **uncheck** proposed and unsupported updated). Then do: 
```
sudo apt-get update
```Check/enable these sources only if you intend to use beta/unstable releases. Checking all of them together also sometimes creates conflicts between stable and proposed packages.

---

### Post by Mark_in_Hollywood on 2008-05-29
To: viljun

This computer has no M$/Windows software on it and never has had any software other than Ubuntu. Well I don't count WINE/Apps.

To:

LinuxIsInnovation

My Software Sources/Updates did NOT have the two boxes you mentioned checked. See screenshot, attached.

Anybody else?

---

### Post by Oddgeir on 2008-05-30
I have the same problem i think...

first error message i get is:

"Not all updates can be installed"
_________________________________________________________________

The secund one is when i try to do partial upgrade:

"an unresolvable problem occurred while calculating the upgrade"


I need some help here, i'm totaly noob and i want my Linux to be at 100% , my install is the RC 8.04 Hardy heron thingy:)

---

### Post by Oddgeir on 2008-05-30
here is the last part of my apt.log file :

Considering openoffice.org-l10n-nb 10000 as a solution to language-support-translations-nb 10000
Done
ERROR:root:Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

---

### Post by bcom on 2008-05-30
When I first upgraded, I think I got a message indicating that the upgrade would change the repositories.

Then, I too received a similar message about a partial upgrade after I upgraded from 7.10 to 8.04.  

I went to System - Administration - Synaptic Package Manager.  I clicked on Settings - Repositories - Third-Party tab.  On the Third-party tab, I put a check in Unsupported updates, Important security updates, and [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partners.

I no longer rec'd the partial upgrade message after I did this.

---

### Post by Mark_in_Hollywood on 2008-05-30
bcom said:

"I put a check in Unsupported updates, Important security updates, and [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partners."

I don't have that line in my 3rd party window.

---

### Post by bcom on 2008-05-30
Unsupported updates, Important Security updates and the one for the archive are all separate repositories; they do not all appear as one on one line.  So there is a check next to each of them, not one for all of them.

In the listing for the Third-party software repositories, these repositories are all found by scrolling down towards the bottom of the list.

I upgraded from Ubuntu 7.10 to 8.04 so perhaps your system and list of respositories is different.

---

### Post by Mark_in_Hollywood on 2008-05-30
I have found my solution and I hope it could work for others.

I had tried to follow the Ubuntu Geek's

 How to Install Firefox 3 RC1 in Ubuntu 8.04 (Hardy Heron)

[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

and it was after all the package mods that I started having the authentication problems.

I went back to Ubuntu Geek's page and found the following in the Comments section:

#  asac Says:
May 26th, 2008 at 4:09 pm

Please dont send users to unofficial PPAs. If you want to get it now for hardy, use the “semi-official” ubuntu mozillateam archive:

[https://edge.launchpad.net/~mozillateam/+archive](https://edge.launchpad.net/~mozillateam/+archive)

Please update your blog post content.

Thanks!

I surfed to: [https://edge.launchpad.net/~mozillateam/+archive](https://edge.launchpad.net/~mozillateam/+archive) and copied the following line into my Synaptic repository:

deb [http://ppa.launchpad.net/mozillateam/ubuntu](http://ppa.launchpad.net/mozillateam/ubuntu) hardy main


I next did a reload. I was offered new updates, chose that and VOILA, I no longer have authentication and partial upgrade problems.

---

### Post by VMC on 2008-05-31
This is the first time I've ever seen this. All my previous updates installed okay. Not sure if anyone else has come across this before. Any help would be appreciated.
Thanks.

[IMG][[IMG]http://img231.imageshack.us/img231/2038/screenshotupdatemanageroq3.th.png[/IMG]](http://img231.imageshack.us/my.php?image=screenshotupdatemanageroq3.png)[/IMG]

---

### Post by Mark_in_Hollywood on 2008-05-31
I just had this problem with Firefox R.C. 3.0 not installing as well as F-Stop.

double check either via System/Administration/Software Sources/Third Party Software has all the necessary lines "checked". And by necessary since I can't know what isn't downloading, you will have to figure that yourself.

Also, if it's the same problem I'm having, see my thread:

[http://ubuntuforums.org/showthread.php?t=812008](http://ubuntuforums.org/showthread.php?t=812008) at post #10. #10 is where I solved the problem.

If that works for you, please find the Thread Tools link at the top of this page, and mark the thread as "SOLVED".

---

### Post by TNakos on 2008-05-31
Well the issue is... I have 8.04lts but now it won't update some things about it, openoffice. here is what happened.

tim@ubuntu:~$ su
Password: 
root@ubuntu:/home/tim# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-human
  openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
root@ubuntu:/home/tim#

---

### Post by Kosimo on 2008-05-31
Hello guys, does anyone knows what's going on with today's Hardy's Partial Upgrade error?    I know I'm not the only one experiencing this. If enabling reccomended upgrades it appears this (Partial Upgrade) witch fails when installing it.

I couldn't find any information about it.

Here the error message:   ```
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later
```

---

### Post by shifty_powers on 2008-05-31
when you run

```
sudo apt-get update && sudo apt-get upgrade
```

what is the output?

when i had this prob,it seemed to be connected to a opneoffice update...

---

### Post by Kosimo on 2008-05-31
> **shifty_powers said:**
> when you run

```
sudo apt-get update && sudo apt-get upgrade
```

what is the output?

when i had this prob,it seemed to be connected to a opneoffice update...

```
The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-style-human
  openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

Anyway, as I said, I know friends who are experiencing the same error. Looks like something is wrong with this updates

---

### Post by shifty_powers on 2008-05-31
yeah, it's definitely to do with open office.

you don't have to openoffice 3 beta installed by any chance, do you?

---

### Post by Kosimo on 2008-05-31
> **shifty_powers said:**
> yeah, it's definitely to do with open office.

you don't have to openoffice 3 beta installed by any chance, do you?

No I don't...    But the strange thing is that Hardy's keep asking to make a Partial Upgrade when upgrading from Update Manager. 
Does anyone else have the same error?  (it only happens when enabling Recommended and Pre-Release updates.)

---

### Post by Jadd on 2008-05-31
I got the same error today, but I presumed it was because I had Hardy proposed updates enabled.

---

### Post by Joeb454 on 2008-05-31
You could just wait until it's resolved - you don't *have* to update straight away.

I'd just wait - it'll go away eventually ;)

---

### Post by Kosimo on 2008-05-31
> **Jadd said:**
> I got the same error today, but I presumed it was because I had Hardy proposed updates enabled. Do you have them enabled?

Yes I do ;)

---

### Post by shifty_powers on 2008-05-31
heh, well i just uninstalled all oo components. already have oo3 beta installed. then i just installed oowriter, as that is the only bit i use ;)

got rid of the update problem for me ;)

---

### Post by Kosimo on 2008-05-31
> **Joeb454 said:**
> You could just wait until it's resolved - you don't *have* to update straight away.

I'd just wait - it'll go away eventually ;)

I know that I'll be solved... The strange thing is that a general error it doesn't usually takes that long to be solved.

---

### Post by bapoumba on 2008-05-31
> **Jadd said:**
> I got the same error today, but I presumed it was because I had Hardy proposed updates enabled.

> **Kosimo said:**
> Yes I do ;)

The -proposed repos are for testing the packages that will make it to the regular upgrades. Please expect odd things or breakages.

---

### Post by shifty_powers on 2008-05-31
funnily enough i've had that repo enabled for ages, and this is the fist thing to pop up.

personally doesn't bother me ;)

---

### Post by Majorix on 2008-05-31
I had the same problem, but I did a "sudo apt-get dist-upgrade" on the terminal and it eventually installed correctly (although it removed some packages about localization [I couldn't care less about them :p] it was ok).

---

### Post by sports fan Matt on 2008-05-31
I vhad the same thing--I thought "WHY?"  But I may try an update and see what it brings..strange wierdness though...

---

### Post by bapoumba on 2008-05-31
To the -proposed users, please read:
[http://blog.omma.net/?p=11]("http://blog.omma.net/?p=11")

---

### Post by Kosimo on 2008-05-31
> **bapoumba said:**
> To the -proposed users, please read:
[http://blog.omma.net/?p=11]("http://blog.omma.net/?p=11")

Thanks for remembering ;) 
I saw this on planet yesterday.

I know that proposed updates are not 100% official, but this is the second time I had a problem in one year. (Last one was an error with x.org witch took only a few hours to be solved)

---

### Post by bapoumba on 2008-05-31
> **Kosimo said:**
> Thanks for remembering ;) 
I saw this on planet yesterday.

I know that proposed updates are not 100% official, but this is the second time I had a problem in one year. (Last one was an error with x.org witch took only a few hours to be solved)
They are official. But these repos are to test packages on a larger user base before they hit the regular upgrades (these repos were created after some massive X breakages with a regular update, two summers ago IIRC).

---

### Post by bapoumba on 2008-05-31
BTW, I've moved this thread to I&U, and stickynated it.
The timed stickies do not work any longer from the last forums upgrade. Please report the thread once the issue is solved for everyone so that it gets un-stickified :)

---

### Post by VMC on 2008-05-31
Thanks Mark_in_Hollywood. I found a solution at your topic. It was the second post by LinuxIsInnovation  "http://ubuntuforums.org/showpost.php?p=5072269&postcount=3"

I followed and then I was able to update. I haven't changed anything since I installed ubuntu 8.04, so I don't know what happened.

---

### Post by axelsvag on 2008-05-31
Are you sure you found the solution or is it more errors in the last update. Because I can not use my language support (swedish) after update either can I have openoffice installed or the language support not both at the same time. There seems to have been some error in the testing before this update was released. I have not found any solution to this.

---

### Post by VMC on 2008-05-31
> **axelsvag said:**
> Are you sure you found the solution or is it more errors in the last update. Because I can not use my language support (swedish) after update either can I have openoffice installed or the language support not both at the same time. There seems to have been some error in the testing before this update was released. I have not found any solution to this.

For my situation, I found the solution. If you follow the link below, I had the two questionable updates ticked, "Pre-release & Unsupported updates"

[http://ubuntuforums.org/showpost.php?p=5072269&postcount=3](http://ubuntuforums.org/showpost.php?p=5072269&postcount=3)

Here is where I found my solution: [http://ubuntuforums.org/showpost.php?p=5072269&postcount=3](http://ubuntuforums.org/showpost.php?p=5072269&postcount=3)

---

### Post by VMC on 2008-06-01
There were at least 3 or 4 topics opened with same issue. I found my solution, when someone suggested that "Pre-release & Unsupported" be unticked, as shown below. 


When this gets fixed should I then tick "Pre-release & Unsupported" once again. They were that way from the beginning.

---

### Post by nickmcg on 2008-06-01
I ran the partial upgrade ```
sudo apt-get dist-ugrade
``` but now I'm stuck
```
sudo apt-get update
``` ends with ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
and this gives```
sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25
Cannot find /lib/modules/2.6.25
update-initramfs: failed for /boot/initrd.img-2.6.25
dpkg: subprocess post-installation script returned error exit status 1
```

I've disable -proposed, but cannot reload the repositories.

Any ideas?

Nick

---

### Post by bapoumba on 2008-06-01
> **VMC said:**
> There were at least 3 or 4 topics opened with same issue. I found my solution, when someone suggested that "Pre-release & Unsupported" be unticked, as shown below. 


When this gets fixed should I then tick "Pre-release & Unsupported" once again. They were that way from the beginning.
Please give me the links, they can be merged in here.

---

### Post by axelsvag on 2008-06-01
Thank you for your advice and it would probably have worked if I did not try some tricks on my own.The trouble for me is that I can not use the openoffice package together with my language support. It has to be either of them. If I uninstall  my language package or make it less powerful I get openoffice but not in my language, if I choose full language support I loose the openoffice completely. Let us hope the smart guys solv this problem soon.

---

### Post by _MiniMe_ on 2008-06-01
Hi!

 Since I could not find a full error output for this issue, I decided to post one here. This is the output from 'aptitude full-upgrade':

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  openoffice.org-l10n-de openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
The following packages are unused and will be REMOVED:
  libavahi1.0-cil 
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw 
  openoffice.org-evolution openoffice.org-filter-binfilter openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-officebean openoffice.org-style-andromeda 
  openoffice.org-style-crystal openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango 
  openoffice.org-writer python-uno 
24 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 78.6MB of archives. After unpacking 1122kB will be freed.
The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.
  openoffice.org-l10n-en-za: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.
  openoffice.org-l10n-de: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
openoffice.org
openoffice.org-calc
ubuntu-desktop

Keep the following packages at their current version:
openoffice.org-base [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-base-core [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-common [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-core [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-draw [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-evolution [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-filter-binfilter [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-gnome [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-gtk [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-impress [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-math [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-officebean [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-andromeda [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-crystal [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-hicontrast [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-human [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-industrial [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-tango [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-writer [1:2.4.0-3ubuntu6 (hardy, now)]
python-uno [1:2.4.0-3ubuntu6 (hardy, now)]

```

The most interesting part of this output is:

```

The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.
  openoffice.org-l10n-en-za: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.
  openoffice.org-l10n-de: Conflicts: openoffice.org-core (>= 1:2.4.0.1) but 1:2.4.1~rc1-1ubuntu1 is to be installed.

```

Although version "1:2.4.1~rc1-1ubuntu1" is clearly >= "1:2.4.0.1", apt seems to not agree with that, for whatever reason :confused:

---

### Post by enoughsaid05 on 2008-06-01
I am also having the same problem with partial upgrade :(

The same package that hasn't been resolved is still open office.

Strange though, normally such errors do not take too long to resolve.

Scratch head....

---

### Post by enoughsaid05 on 2008-06-01
Bad luck for you and me, I am having the same problem as well. I posted the same thing but no one replied sobz....

Anyway, think is something wrong with the repos. Might dig around within the forum look for similar posts. Till now I think the problem with the repos is yet to be resolved. Just wait and see.

For me, I am in no hurry to update. I know for a noob like me, rushing into things will only screw up my system.

Cheers.

---

### Post by bapoumba on 2008-06-01
@ _MiniMe_ and enoughsaid05: did you enable the -proposed repos to get firefox? If so, please remove these repos and reload the sources.list file (reload button from synaptic or sudo apt-get update or sudo aptitude update). FYI, I do not get these partial upgrades without the -proposed repos :)

---

### Post by housam on 2008-06-01
try this : [[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=5072269&postcount=3_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5072269&postcount=3")

---

### Post by DapperDrakeNewbieDR on 2008-06-01
Hi Folks,

I've been trying to upgrade my KDE4 installation through the Update Manager application in Ubuntu 8.04, I got the 'Run Partial Upgrade' error message, when I tried to run the partial upgrade, I got another error message (I managed to run a few upgrades, but not all of them were successfully applied), the Upgrade Manager app gave this error output:


```
An error ocurred, please run package manager from the right-click menu or apt-get in terminal to see what is wrong. The error message was: ' Error: BrokenCount > 0' This usually means that your installed packages have unmet dependencies
```

Then I went to Synaptic, when I first opened it I got a message saying I had 1 broken package. The broken package is:

```
ksysguard-kd4
``` Description: System Guard for KDE 4

I tried to fix it using the 'Fix Broken Packages' option but got this other error message in Synaptic:

```
E: /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb: trying to overwrite `/usr/lib/kde4/lib/libkdeinit4_plasma.so', which is also in package libplasma1
```

Any suggestions on what to do next?

---

### Post by bwhite82 on 2008-06-01
Open a terminal and input:

> sudo apt-get -f install

---

### Post by Joeb454 on 2008-06-01
I think either the OOo updates in -proposed have a package failure, or they are just being stubborn.

But bapoumba is correct - I don't get the partial upgrades without -proposed :)

---

### Post by mick222 on 2008-06-01
i had this error yesterday but it seems to have resolved itself

---

### Post by Kosimo on 2008-06-01
At the moment I'm still having the same error. (Of course, only happens when enabling Pre-Released updates)

---

### Post by xjgnsdof on 2008-06-01
This worked for me, as suggested by another poster above:
```
sudo apt-get dist-upgrade
```

---

### Post by DapperDrakeNewbieDR on 2008-06-01
After entering this command **sudo apt-get -f install** I got the following output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ksysguardd-kde4 linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5
  libplasma2 libqt4-webkit
The following packages will be REMOVED:
  libplasma1
The following NEW packages will be installed:
  kdebase-workspace-libs4+5 libplasma2 libqt4-webkit
The following packages will be upgraded:
  kdebase-workspace-bin kdebase-workspace-data
2 upgraded, 3 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.0MB of archives.
After this operation, 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdebase-workspace-bin kdebase-workspace-data libplasma2
  kdebase-workspace-libs4+5
Install these packages without verification [y/N]? y
(Reading database ... 259190 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.0.4-0ubuntu1~hardy1 (using .../kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/libkdeinit4_plasma.so', which is also in package libplasma1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by lanzen on 2008-06-01
Ok, I've got the same here!

I knew I should have hold back upgrading. Beside this, there was this removal of language packages that have affected Ubuntu in the past two days.

I'll try to lock kde 4 repos, and see if it gets any better.

---

### Post by bwhite82 on 2008-06-01
Alright, try this. Move that file to your desktop:

> sudo mv /usr/lib/kde4/lib/libkdeinit4_plasma.so /home/**YOURUSERNAME**/Desktop

Then rerun the command I gave you above.

---

### Post by lanzen on 2008-06-01
Removing kde 4 repo worked, and now I find myself with OpenOffice in english only, but that's another matter and if this doesn't get fixed soon (it's seems ok now in gnome) I'll have to pick up the debian s. i. package as I did on another machine.

> **Soldierboy said:**
> Alright, try this. Move that file to your desktop:

Just tried that it, but didn't work because the file could not be found! Getting kde 4 out might have to do with this.

I'll tray to add kde 4 repos again.

---

### Post by lanzen on 2008-06-01
Nope, here's the output:

```
$ sudo dpkg --configure -a
dpkg: problemi con le dipendenze impediscono la configurazione di kdebase-kde4:
 kdebase-kde4 dipende da kdebase-bin-kde4 (>= 4:4.0.80-0ubuntu1~hardy1~ppa3); comunque:
  La versione di kdebase-bin-kde4 presente sul sistema è 4:4.0.4-0ubuntu1~hardy3.
dpkg: errore processando kdebase-kde4 (--configure):
 problemi con le dipendenze - lasciato non configurato
Configuro kwrite-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...

Configuro libkonq5 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...

Configuro konqueror-nsplugins-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
Configuro dolphin-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...

Configuro kdebase-workspace-data (4:4.0.80-0ubuntu1~hardy1~ppa3) ...

Configuro libkonq5-templates (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
dpkg: problemi con le dipendenze impediscono la configurazione di konqueror-kde4:
 konqueror-kde4 dipende da kdebase-data-kde4 (>= 4:4.0.80-0ubuntu1~hardy1~ppa3); comunque:
  La versione di kdebase-data-kde4 presente sul sistema è 4:4.0.4-0ubuntu1~hardy3.
dpkg: errore processando konqueror-kde4 (--configure):
 problemi con le dipendenze - lasciato non configurato
Configuro konsole-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
Configuro kappfinder-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
Configuro kdm-kde4 (4:4.0.4-0ubuntu1~hardy1) ...

Configuro kfind-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
Configuro kdepasswd-kde4 (4:4.0.80-0ubuntu1~hardy1~ppa3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Sono occorsi degli errori processando:
 kdebase-kde4
 konqueror-kde4

```

Sorry it's not all in english. If what it says is not obvious, I could translate...

---

### Post by DapperDrakeNewbieDR on 2008-06-01
Soldierboy: I think I got the same output

> 
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ksysguardd-kde4 linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5
  libplasma2 libqt4-webkit
The following packages will be REMOVED:
  libplasma1
The following NEW packages will be installed:
  kdebase-workspace-libs4+5 libplasma2 libqt4-webkit
The following packages will be upgraded:
  kdebase-workspace-bin kdebase-workspace-data
2 upgraded, 3 newly installed, 1 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/11.0MB of archives.
After this operation, 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdebase-workspace-bin kdebase-workspace-data libplasma2
  kdebase-workspace-libs4+5
Install these packages without verification [y/N]? y
(Reading database ... 259190 files and directories currently installed.)
Preparing to replace kdebase-workspace-bin 4:4.0.4-0ubuntu1~hardy1 (using .../kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb) ...
Unpacking replacement kdebase-workspace-bin ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde4/lib/libkdeinit4_plasma.so', which is also in package libplasma1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by lanzen on 2008-06-01
I've tried again. No luck :(

```
Spacchetto il sostituto di kdm-kde4 ...
dpkg: errore processando /var/cache/apt/archives/kdm-kde4_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb (--unpack):
 tentata sovrascrittura di `/usr/share/man/man5/kdm.options.5.gz', che si trova anche nel pacchetto kdm
Sono occorsi degli errori processando:
 /var/cache/apt/archives/kdm-kde4_4%3a4.0.80-0ubuntu1~hardy1~ppa3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Oh well, that means I wont be able to use kde4... never mind, it's pretty unusable anyway so far.  ;)

I've better fix the language pack problem as kde 3 now.

---

### Post by VMC on 2008-06-01
> **bapoumba said:**
> Please give me the links, they can be merged in here.

Here's four links ,including the one I started, that was before this sticky was made:

[http://ubuntuforums.org/showthread.php?t=815067](http://ubuntuforums.org/showthread.php?t=815067)
[http://ubuntuforums.org/showthread.php?t=814198](http://ubuntuforums.org/showthread.php?t=814198)
[http://ubuntuforums.org/showthread.php?t=814091](http://ubuntuforums.org/showthread.php?t=814091)
[http://ubuntuforums.org/showthread.php?t=812008](http://ubuntuforums.org/showthread.php?t=812008)

---

### Post by Victormd on 2008-06-01
I first noticed this yesterday but I'm just waiting to see what happens (I do have the proposed repos). I thought I had broken something on my machine but it's good to know that it's not just me... hehehe :)

---

### Post by |UVI| on 2008-06-01
Same problem here
 :(

---

### Post by _MiniMe_ on 2008-06-01
> **bapoumba said:**
> @ _MiniMe_ and enoughsaid05: did you enable the -proposed repos to get firefox? If so, please remove these repos and reload the sources.list file (reload button from synaptic or sudo apt-get update or sudo aptitude update). FYI, I do not get these partial upgrades without the -proposed repos :)

Thx, but this is not a real solution! You don't get an error because the open-office packages, that cause the error, are only in the proposed repository and if you disable that repo, there is nothing to update (at least not open-office). But that doesn't change the fact that there is a problem with those updates that has to be resolved. Hopefully the maintainer for these packages will fix this soon...

---

### Post by bapoumba on 2008-06-01
> **_MiniMe_ said:**
> Thx, but this is not a real solution! You don't get an error because the open-office packages, that cause the error, are only in the proposed repository and if you disable that repo, there is nothing to update (at least not open-office). But that doesn't change the fact that there is a problem with those updates that has to be resolved. Hopefully the maintainer for these packages will fix this soon...
Yes, it should be fixed :)

Merged 4 threads in here.

---

### Post by Pumalite on 2008-06-01
I just got all my OpenOffice packages updated and I have all my repos opened.

---

### Post by forestpixie on 2008-06-01
Mine just updated as well - none of the openoffice 2 programs work - they start to start and that's it

---

### Post by Kosimo on 2008-06-01
Hey guys, just want to say that problem is solved and works great for me. After sudo apt-get update, my system doesn't offer me to do a partial upgrade anymore, and it just offers to upgrade some openoffice packages witch where downloaded and installed with no issues.

Thank you

---

### Post by forestpixie on 2008-06-01
I wonder why mine is having problems then?

Edit reported it as a bug, guess I'll find out eventually if it is or not - wish it would error enough to tricker apport though.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/236619](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/236619)

---

### Post by Pumalite on 2008-06-01
> **forestpixie said:**
> I wonder why mine is having problems then?
Sorry to hear that. Mine work fine.

---

### Post by Hiperi0n on 2008-06-01
Hello. I found the partial upgrade error too yesterday. But instead of documenting myself I "forced" the install. I now have some issues. Most important, openoffice doesn't work, it closes as soon as the loading bar ends. Second (this is what bothers me most) in nautilus, files arranged by name are not truly arranged by name. Instead, uppercase letters have priority over lowercase letters. (instead of documents before Videos, I have Videos before documents).

Is there anyway to undo the mess? Remove the installed packages, even reinstalling half ubuntu... I must have openoffice working and I don't want to reformat my hd (usually the quickest solution)

Thanks.:cry:

Note: I forced reinstall by sudo aptitude full-upgrade and then safe-upgrade. I also cant mount external drivers without sudo...

---

### Post by Habitual on 2008-06-01
> **LinuxIsInnovation said:**
> Goto System->Administration->Software Sources
Click Updates tab and **uncheck **the last 2 update sources (ie. **uncheck** proposed and unsupported updated). Then do: 
```
sudo apt-get update
```Check/enable these sources only if you intend to use beta/unstable releases. Checking all of them together also sometimes creates conflicts between stable and proposed packages.

worked for me, Thank You!:KS

---

### Post by xerxesdaphat on 2008-06-01
> **Hiperi0n said:**
> Hello. I found the partial upgrade error too yesterday. But instead of documenting myself I "forced" the install. I now have some issues. Most important, openoffice doesn't work, it closes as soon as the loading bar ends. Second (this is what bothers me most) in nautilus, files arranged by name are not truly arranged by name. Instead, uppercase letters have priority over lowercase letters. (instead of documents before Videos, I have Videos before documents).

Is there anyway to undo the mess? Remove the installed packages, even reinstalling half ubuntu... I must have openoffice working and I don't want to reformat my hd (usually the quickest solution)

Thanks.:cry:

Note: I forced reinstall by sudo aptitude full-upgrade and then safe-upgrade. I also cant mount external drivers without sudo...

Seems a bit odd -- I've run into the Nautilus case-sensitive thing before though, and this is how I solved it: [http://bbs.archlinux.org/viewtopic.php?id=34699](http://bbs.archlinux.org/viewtopic.php?id=34699) . See post #4. This upgrade issue involved several packages involved with locale settings and language packs; perhaps that upset the locale environment variables?

Now it's all sorted, have you reinstalled all those packages that were removed if you tried to force the upgrade? That might solve the problem at the source, instead of just sort of working around the issue like in the post above.

EDIT: To be clearer, when you forced the upgrade, a bunch of locale/language packages were removed. Nautilus relies on the LC_COLLATE environment variable to know to sort case-sensitive or insensitive. When these locale packages were uninstalled, LC_COLLATE might've got clobbered. Not having these packages installed is probably also killing OO.org apps from loading completely. Reinstalling the removed locale packages (see earlier in the thread for which packages were deleted, if you don't have logs yourself) should fix both problems, I'm guessing.

---

### Post by nickmcg on 2008-06-02
I am stuck with this ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```
when I try dpkg update/upgrade, so I try & fix it and get
```

~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.25
Cannot find /lib/modules/2.6.25
update-initramfs: failed for /boot/initrd.img-2.6.25
dpkg: subprocess post-installation script returned error exit status 1

```

Any ideas?

Thanks

Nick

---

### Post by StewartG on 2008-06-02
sudo apt-get update

Then accepting the updates works on both my machines.

Bugs the hell out of me seeing the update icon and not being able to do the update! Nice to see it go away. :KS

---

### Post by Hiperi0n on 2008-06-02
Thanks xerxesdaphat. I just reinstalled the previously removed packages I saw in /var/log/aptitude

Nautilus by name ordering seems back to normal case-insensitive mode. Openoffice works fine. Most of my issues are solved, however I still can't mount my external hard drive (not privileged to...), I must use sudo. It might be smthng fstab related and maybe just a coincidence it was triggered with all this update mess.

Thanks!

---

### Post by Peter09 on 2008-06-02
I seem to be stuck with a wireless=off situation on my laptop. The device is configured but I cannot switch it on, is anyone else suffering from this as part of the mess?


PC

---

### Post by bapoumba on 2008-06-03
Has this been solved for everyone ?

---

### Post by forestpixie on 2008-06-03
I got mine sorted eventually with a complete removal and reinstall- just tried to edit my post and got a databse error ?

---

### Post by bapoumba on 2008-06-03
> **forestpixie said:**
> I got mine sorted eventually with a complete removal and reinstall- just tried to edit my post and got a databse error ?

Yes, there are some issues. u-g is working on them, You (and I, and everyone else ^^) may experience more of them. Sorry for the inconvenience :)

There are also some weird things with the stickies..

---

### Post by forestpixie on 2008-06-03
> You (and I, and everyone else ^^) may experience more of them.

Kind of getting used to them - almost like old friends :)

---

### Post by VMC on 2008-06-03
> **bapoumba said:**
> Has this been solved for everyone ?

It looks like its solved from my end. I even changed Software Sources back to what they were before this all started: "Pre-released & Unsupported".

Everything appears to be normal. I get updates and they get applied. 
Thanks to all involved for fixing this.

---

### Post by bapoumba on 2008-06-03
Okay, thanks VMC. I'm not having any issues with regular repos either. 
I was asking so to unstick the thread, but there are some problems with it too. The thread looks weirdly moved and unstuck, which it has not been. Anyway, I'll look at this later, once u-g has solved the glitch in the matrix :)

---

### Post by Mark_in_Hollywood on 2008-06-03
As the originator of this thread I'm pleased to see that it has been some help. 

Here, I report that yesterday, Synaptic Pkg. Mgr. offered another distribution upgrade. That, upgrade, once running, turned around and offered a partial upgrade. I dismissed the partial, and tried the regular or ordinary upgrade. I received a partial upgrade notice again, ran that and after a few moments, the partial upgrade installed itself and uninstalled a number of programs, that are new to this installation and not important enough to me to care about. I didn't see all the uninstalled software packages, but two of them were: btnx (mouse button program) and gramps (genealogy program).

---

### Post by peakshysteria on 2008-06-04
> **Mark_in_Hollywood said:**
> Update Manager has for two or three days in a row, offered new packages. When I click "install", I get the

Not all updates can be installed

Run a partial upgrade . . .

when I click Partial Upgrade I get another "error authenticating some packages" message. 

What can I do to fix this?

Had the same problem for a week after enabling hardy-proposed. Waited it off. Now it seems to have resolved it self. Got some updates yesterday and today and both times it all went smooth as usual. No partial update error warning. Now running kernel 2.6.24-18-generic and Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008060309 Firefox/3.0 among other things. All seems smooth in my end :)

What if I now uncheck hardy-proposed? Will this make a problem for me?

---

### Post by forestpixie on 2008-06-04
> Will this make a problem for me?

Shouldn't do, just means you'll need to wait for updates - if you do find a problem - enable them again.

---

### Post by juray on 2008-06-04
After I've installed all software updates, offered by update manager, the gnome crashed.
Look at this (click on thumbinal):
[[img]http://images.superforum.sk/t/Screenshot-1_d8423.png[/img]](http://images.superforum.sk/show.php?img=Screenshot-1_d8423.png)

What can I solve this problem?
Thanx and sorry for my english. juray

---

### Post by peakshysteria on 2008-06-04
Which version of Gnome are you currently running? Last version is 2.22.2 as far as I know.

Have you checked hardy-proposed?

---

### Post by cmnduu94 on 2008-06-06
> **LinuxIsInnovation said:**
> Goto System->Administration->Software Sources
Click Updates tab and **uncheck **the last 2 update sources (ie. **uncheck** proposed and unsupported updated). Then do: 
```
sudo apt-get update
```Check/enable these sources only if you intend to use beta/unstable releases. Checking all of them together also sometimes creates conflicts between stable and proposed packages.

This one worked for me. I have Ubuntu 8.04 LTS. Thanks to LinuxIsInnovation.

---

### Post by ahickey on 2008-06-09
Did a clean install of 8.04 a few weeks ago from the liveCD
Install went fine - did a little fix to xorg.conf for nVidia support. Got a lovely wrorking system.  Connected to the internet - all fine.

Went back to the system on the 4th of June.
Still all working.
Then got the Update Notification.
125 updates to install.
Clicked to install.
Car crash time...
Got the partial upgrade problem.

Now Gnome doesn't work and I just get the CLI.  No networking option.
So, this was still a problem (if it's the same thing) a week ago.

I will be doing a new full install this week.  Unchecking the two repositories mentioned and hanging in there with a reliable desktop until all this blows over.

I assume this is the thread to check in to on occassion to see if everthing is alright.

---

### Post by Pumalite on 2008-06-09
Linux pumalite-desktop 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux
Mine is working fine.

---

### Post by ahickey on 2008-06-11
I did my fresh install of 8.04 and got the same problems. (I'm not at my system now, but I did cut and paste the errors into gedit and will post later)

Basically, install worked from the CD. Problem with resolution so modified xorg.conf with some setting taken from this forum.  Luckily they worked and now I'm running at full 1280x1024.

I unchecked the two boxes for updates and was still prompted with 22 updates.  
Click to apply and got the message that one of the servers was not responding and that at least one of the files was corrupt.

Recovered and I'm not applying any system updates until this is sorted out.  I have a working Ubuntu desktop that does what I need for now, so going with 'if it ain't broken don't fix it' for now.

Other then that happy with performance.  On my lowly system it appears a bit more nippy.

---

### Post by dgermann on 2008-06-11
Hi--

I see essentially two solutions in this thread and have done both what is recommended in post 3 and post 10. I still get the "not all updates can be installed" error.

When I click cancel on that screen the boxes not checked are linux-backports-modules-hardy and a new kernel and some other things related to those--6 items in total. Oh, tzdata and f-spot are not checked either, a total of 8.

Under third-party software, I have only one other box, unchecked: [http://planet76.com/repositories/](http://planet76.com/repositories/) ./ Yes, this is a system 76 machine.

So I am unclear what I should do next. Should I do the partial, should I do apt-get dist-upgrade, or something else?

Thanks!

---

### Post by bapoumba on 2008-06-12
@ dgermann: please post your sources.list **cat /etc/apt/sources.list**.

---

### Post by dgermann on 2008-06-12
bapoumba--

Here it is--
```
 cat /etc/apt/sources.list
## Ubuntu 7.04 System76 Repositories Listing

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

## System76 Driver Repository
deb http://planet76.com/repositories/ ./
deb http://ppa.launchpad.net/mozillateam/ubuntu hardy main

```

Thanks for helping, bapoumba!

---

### Post by bapoumba on 2008-06-12
Please remove for now the system76 repos and the mozillateam PPA.
You alos need to add the hardy-updates universe multiverse repositories and the hardy-security multiverse one.

You can do it from synaptic or by editing the sources.list:
```
sudo nano /etc/apt/sources.list
```

Have your repos look like this :
```
## Ubuntu 7.04 System76 Repositories Listing

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted [COLOR="Green"]universe multiverse[/COLOR]
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted [COLOR="Green"]universe multiverse
[/COLOR]
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe [COLOR="Green"]multiverse[/COLOR]
deb-src http://security.ubuntu.com/ubuntu hardy-security universe [COLOR="Green"]multiverse[/COLOR]

## System76 Driver Repository
[COLOR="Green"]#[/COLOR] deb http://planet76.com/repositories/ ./
[COLOR="Green"]#[/COLOR] deb http://ppa.launchpad.net/mozillateam/ubuntu hardy main
```
Add the repos and the hashes in green.
Save the file : CTRL-O (same name, hit <enter>)
Exit nano : CTRL-X

Reload the new file:
```
sudo apt-get update
```
And please paste the complete error output if any.

---

### Post by dgermann on 2008-06-12
bapoumba--

Many thanks! 

It worked! (I wonder why the repositories were wrong after the upgrade?)

Anyway, after following your instructions, the number of offered upgrades went from 103 to 122, but this time there was no “not all updates can be installed” error.

I decided to be better able to collect error info, I should work from the terminal. apt-get upgrade would only do 108, while holding back 7; so I did apt-get dist-upgrade instead, and it totaled 122 that it would install. I gave it the go-ahead.

It ended without error message. shutdown -r now and all seems well. (Except I am having a touchpad going bonkers, but that might be a different problem).

So thanks, bapoumba!

---

### Post by bapoumba on 2008-06-13
> **dgermann said:**
> bapoumba--

Many thanks! 

It worked! (I wonder why the repositories were wrong after the upgrade?)

Anyway, after following your instructions, the number of offered upgrades went from 103 to 122, but this time there was no “not all updates can be installed” error.

I decided to be better able to collect error info, I should work from the terminal. apt-get upgrade would only do 108, while holding back 7; so I did apt-get dist-upgrade instead, and it totaled 122 that it would install. I gave it the go-ahead.

It ended without error message. shutdown -r now and all seems well. (Except I am having a touchpad going bonkers, but that might be a different problem).

So thanks, bapoumba!

You're welcome, glad to see you got it to work!
"upgrade" installs all the newer packages, dist-upgrade performs a "distribution-wide-upgrade", checking for dependencies and installing or removing additional packages if needed. When they are some issues with the updates, dist-upgrade usually does a better job.
Congrats :)

---

### Post by chelovik on 2008-07-04
You won't get very far trying to use the update manager or get-apt commands if you don't fix the underlying problem.

You will need to run: sudo get-apt update to get the error messages: Take note of them. Then edit the sources.list file:

sudo vi /etc/apt/source.list

Scroll through and comment out the offending lines that were reported in the get-apt update command.

If you don't know how to use vi, use another editor, but you may not be able to save the file. VI is easy to use...
commands are  "i" - insert
              <Esc> - get out of insert
              <Up>,<Down>,<Left>,<Right> arrows to move.

Place a "#" symbol at the beginning of each line to comment out the line.

When you are finished, and all is OK, press:  ":wq!"  to save  (note the collon char  ":" before the "w" and the quote char "!"

PLEASE NOTE .... none of these commands should have the quotes, only what is inside them.

PLEASE NOTE:  If you have totally mucked up your editing, you can quit and abandon the changes by typing   ":q!"

Having made the changes, now issue the command:
sudo get-apt update

This should complete normally

---

### Post by xoroz on 2008-11-07
Cant Install OpenOffice 3.0
I get the following error:

```


The following packages have been kept back:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-gb
  openoffice.org-help-en-us openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-style-human openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.

```

Why? I have added the "universe multiserver" but to sources but did not help...
any ideas?
I have 8.04 with ooficce 2.4. I know 3.0 has just been released.

---

### Post by tracey__ on 2009-03-28
> **sayakb said:**
> Goto System->Administration->Software Sources
Click Updates tab and **uncheck **the last 2 update sources (ie. **uncheck** proposed and unsupported updated). Then do: 
```
sudo apt-get update
```Check/enable these sources only if you intend to use beta/unstable releases. Checking all of them together also sometimes creates conflicts between stable and proposed packages.

I had the same problem, and this resolved it. 
Thanks!

---

### Post by dalesd on 2009-04-08
I'm getting a partial upgrade error, and I'm pretty sure it's because I had installed KDE 4.1 on top of my Ubuntu.  (I didn't care for it and went back to Gnome.)  Now that 4.2.2 is released, I'm getting this partial upgrade error that a lot of you had with OpenOffice.

So I did a sudo apt-get dist-upgrade, and here's what it returned:
```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  adept akregator amarok-kde4 ark dolphin dragonplayer gdebi-kde
  guidance-power-manager gwenview install-package jockey-kde kaddressbook
  kamera kate kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin
  kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-workspace-bin kdebase-workspace-libs4+5 kdebluetooth
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins
  kdepim-wizards kdeplasma-addons kdeplasma-addons-libs4 kdesudo kdm kfind
  kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes kompare
  konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact
  kopete korganizer krdc krfb ksnapshot ksysguard ksystemlog ktimetracker
  ktorrent kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser
  kvkbd kwalletmanager language-selector-qt libkcddb4 libkdecorations4
  libkdepim4 libkholidays4 libkipi5 libkleo4 libkonq5 libkpgp4 libksieve4
  libkwineffects1 libmimelib4 libokularcore1 libplasma2 okular
  okular-extra-backends plasmoid-cpuload plasmoid-quickaccess
  plasmoid-system-status plasmoid-weather powerdevil python-kde4
  software-properties-kde systemsettings update-manager-kde
  update-notifier-kde
The following NEW packages will be installed:
  akonadi-server libdbd-mysql-perl libdbi-perl libhtml-template-perl libical0
  libnet-daemon-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
  nvidia-180-modaliases
The following packages have been kept back:
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdepimlibs5
The following packages will be upgraded:
  kdebase-workspace-data nvidia-common
2 upgraded, 10 newly installed, 90 to remove and 4 not upgraded.
Need to get 0B/47.8MB of archives.
After this operation, 85.1MB disk space will be freed.
Do you want to continue [Y/n]? 
```
That seems like it's going to remove a lot of stuff, as opposed to upgrading it, so I didn't continue.  I'd kind of like to try KDE 4.2.  Will I still have KDE if I do this?

---

