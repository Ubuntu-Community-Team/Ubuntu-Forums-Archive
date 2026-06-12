---
title: "[SOLVED] KDE4.1 or KDE4.2"
date: 2008-11-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xebian on 2008-11-12
I'm just wondering if JJ will stay at 4.1 or move to 4.2 ?  4.2 beta 1 is set to release this 18th of NOV.

---

### Post by ghindo on 2008-11-12
When is the final KDE 4.2 release scheduled for?  If it's before the feature freeze, then it might be included.

---

### Post by GeneralZod on 2008-11-12
> **ghindo said:**
> When is the final KDE 4.2 release scheduled for?  If it's before the feature freeze, then it might be included.

End of Jan '09 :

[http://techbase.kde.org/Schedules/KDE4/4.2_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.2_Release_Schedule)

---

### Post by JACooks on 2008-11-12
Looks like KDE 4.2 should be out by end of January, per [http://techbase.kde.org/Schedules/KDE4/4.2_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.2_Release_Schedule), so it looks promising.  Not sure what the Kubuntu plans are though.

---

### Post by xebian on 2008-11-12
The Jan release is well before the Feb feature freeze.  So it's promising indeed.  

But my point is do we have to wait till then, or the upcoming JJ alpha should start right off the bat with 4.2 ?

---

### Post by jsmidt on 2008-11-12
Each Gnome release happens after the feature freeze and yet is always included.

I think, to be fair to the KDE fan base, Ubuntu/Kubuntu should always install the latest KDE, even if it is released only a month before the final is shipped, just like Gnome.  (Unless it is an LTS release and KDE is making as crazy of an upgrade as 4.0 was.)

---

### Post by ccw on 2008-11-15
[https://launchpad.net/ubuntu/jaunty/+source/kdebase-runtime/4:4.1.73-0ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/kdebase-runtime/4:4.1.73-0ubuntu1)

There's your answer. Development versions of KDE 4.2 are showing up in jaunty.

---

### Post by xebian on 2008-11-15
> **ccw said:**
> [https://launchpad.net/ubuntu/jaunty/+source/kdebase-runtime/4:4.1.73-0ubuntu1](https://launchpad.net/ubuntu/jaunty/+source/kdebase-runtime/4:4.1.73-0ubuntu1)

There's your answer. Development versions of KDE 4.2 are showing up in jaunty.

Not in the repo yet but that's a good sign.  :)

---

### Post by edajai on 2008-11-16
jaunty is definitely gonna have KDE 4.2

---

### Post by ccw on 2008-11-16
> **xebian said:**
> Not in the repo yet but that's a good sign.  :)

"Status: Dependency wait"

They'll be coming soon enough.

---

### Post by awakatanka on 2008-11-16
If KDE 4.2 is hitting the repo's i switch to testing again. Hope they also keep everything in and don't remove things because it may confuse users.

---

### Post by xebian on 2008-11-19
> **awakatanka said:**
> If KDE 4.2 is hitting the repo's i switch to testing again. Hope they also keep everything in and don't remove things because it may confuse users.

Just upgraded a while ago, and KDE 4.2 is in the repo.  :guitar:

---

### Post by awakatanka on 2008-11-19
Great switching again, let the test begin again :guitar:

---

### Post by super.rad on 2008-11-19
Looks like it hasnt all come into the repo's yet
```
The following packages have unmet dependencies.
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
E: Broken packages

```

---

### Post by xebian on 2008-11-19
> **super.rad said:**
> Looks like it hasnt all come into the repo's yet
```
The following packages have unmet dependencies.
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
E: Broken packages

```

I don't have kubuntu-desktop but kdebase-workspace-bin is still at 4.1.3

Here are the pkgs that are now at 4.1.73 (4.2) installed from the repo.

```
root@jaunty:~# dpkg -l | grep 4.1.7
ii  kde-icons-oxygen                     4:4.1.73-0ubuntu1              Oxygen icon theme for KDE 4
ii  kdebase-runtime                      4:4.1.73-0ubuntu1              runtime components from the official KDE 4 r
ii  kdebase-runtime-bin-kde4             4:4.1.73-0ubuntu1              core binaries for the KDE 4 base runtime mod
ii  kdebase-runtime-data                 4:4.1.73-0ubuntu1              shared data files for the KDE 4 base runtime
ii  kdebase-runtime-data-common          4:4.1.73-0ubuntu1              shared data files for the KDE 4 base runtime
ii  kdelibs-bin                          4:4.1.73-0ubuntu5              executables for all KDE 4 core applications
ii  kdelibs5                             4:4.1.73-0ubuntu5              core libraries for all KDE 4 applications
ii  kdelibs5-data                        4:4.1.73-0ubuntu5              core shared data for all KDE 4 applications
ii  kdepimlibs-data                      4:4.1.73-0ubuntu1              core shared data for KDE PIM 4 applications
ii  kdepimlibs5                          4:4.1.73-0ubuntu1              core libraries for KDE PIM 4 applications
ii  khelpcenter4                         4:4.1.73-0ubuntu1              Help Center for KDE 4
root@jaunty:~#

```

---

### Post by super.rad on 2008-11-19
hopefully the rest of it will be in soon, looking forward to testing 4.2

---

### Post by xebian on 2008-11-19
> **super.rad said:**
> hopefully the rest of it will be in soon, looking forward to testing 4.2

Definitely.  Alpha 1 will be out tomorrow (11/20) anyway.  :grin:

---

### Post by super.rad on 2008-11-19
Installing 4.2 now, looks like everything is in the repos now as I've had no errors

---

### Post by xebian on 2008-11-19
> **super.rad said:**
> Installing 4.2 now, looks like everything is in the repos now as I've had no errors

:guitar::guitar::guitar:

---

### Post by awakatanka on 2008-11-20
Don't have all plasmoids like folderview, and also i can't change the desktop containment to folderview containment because it simply isn't there. Effect don't work the right way if i select a border point like right side for desktop grid. And also not all packages are there, kate won't install still depends on kde 4.1.x same for kwrite but it works. But i also see they still updating the repo so it will be oke later on.

---

### Post by Progressive on 2008-11-20
I am having the same issues with 4.2 on Jaunty. Folder View isn't available.

Yet, I really do like the new Oxygen panel theme, the new theme-able Kickoff, and the extra panel features.

I wonder when we will get a new Kernel? Right now it is basically intrepid + kde 4.2 + OOo3

---

### Post by Changturkey on 2008-11-21
Is it better right now to use UbuntuGnome/Minimal+KDE or Kubuntu? I want to test 4.2; I would also like to know if there is a minimal+KDE remaster out there somewhere..

---

### Post by awakatanka on 2008-11-21
You can use server edition and install kde4 most minimal there is i think

---

### Post by hardhu on 2008-11-22
I am experiencing this problem trying to upgrade to 4.1.73 packages:

Unpacking replacement kdebase-runtime-data ...                                  
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.1.73-0ubuntu1_all.deb (--unpack):                                                     
 trying to overwrite `/usr/share/kde4/apps/ksmserver/windowmanagers/openbox.desktop', which is also in package kdebase-workspace-data                           
dpkg-deb: subprocess paste killed by signal (Broken pipe)                       

Has anybody else the same problem?

---

### Post by Mazza558 on 2008-11-22
4.2's working great for me, apart from the fact that it doesn't work with the Open Source ATI drivers for me.

---

### Post by hardhu on 2008-11-22
I am wondering how has some people been able to upgrade to 4.1.73 packages without having the same error I mentioned above. Can anybody of them post the version of the two packages kdebase-runtime-data and kdebase-workspace-data they have installed?

---

### Post by jlacroix on 2008-11-22
For me, I am unable to install the plasma addons package. That's probably why some of the widgets are unknown and appear as red boxes. :(

---

### Post by awakatanka on 2008-11-23
There are still many files 4.1.3 not everything is updated to 4.1.73.

Do the people that upgrade use update-manager our CLI and apt-get?

They recommend update-manager its some where on the forum to lazy to search it :)

---

### Post by Progressive on 2008-11-23
Plasma and kdebase are fixed... Anyone who wants to upgrade Kubuntu to try out KDE 4.2 should go for it now.

---

### Post by Changturkey on 2008-11-23
Is there a loss of usability between Ubuntu and Kubuntu? Haven't used KDE 4.x yet.

---

### Post by caryb on 2008-11-24
Since upgrades yesterday I cant logon to KDE I logon & it starts to load KDE then goes back to the logon screen! I can logon to failsafe mode:confused:


Cary

---

### Post by hardhu on 2008-11-25
> **Progressive said:**
> Plasma and kdebase are fixed... Anyone who wants to upgrade Kubuntu to try out KDE 4.2 should go for it now.

Sure? I have still the same problem and cannot upgrade:

Preparing to replace kdebase-runtime-data 4:4.1.3-0ubuntu1~intrepid1 (using .../kdebase-runtime-data_4%3a4.1.73-0ubuntu1_all.deb) ...                           
Unpacking replacement kdebase-runtime-data ...                                  
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.1.73-0ubuntu1_all.deb (--unpack):                                                     
 trying to overwrite `/usr/share/kde4/apps/ksmserver/windowmanagers/openbox.desktop', which is also in package kdebase-workspace-data

---

### Post by trashxx on 2008-11-25
> **hardhu said:**
> Sure? I have still the same problem and cannot upgrade:

Preparing to replace kdebase-runtime-data 4:4.1.3-0ubuntu1~intrepid1 (using .../kdebase-runtime-data_4%3a4.1.73-0ubuntu1_all.deb) ...                           
Unpacking replacement kdebase-runtime-data ...                                  
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-data_4%3a4.1.73-0ubuntu1_all.deb (--unpack):                                                     
 trying to overwrite `/usr/share/kde4/apps/ksmserver/windowmanagers/openbox.desktop', which is also in package kdebase-workspace-data

Same error here for the last 4 days or so; apt-get -f install or apt-get -f dist-upgrade (after apt-get upgrade) doesn't fix anything.

---

### Post by Slug71 on 2008-11-25
> **Progressive said:**
> I am having the same issues with 4.2 on Jaunty. Folder View isn't available.

Yet, I really do like the new Oxygen panel theme, the new theme-able Kickoff, and the extra panel features.

I wonder when we will get a new Kernel? Right now it is basically intrepid + kde 4.2 + OOo3

OOo3???

2.4 is still in Jaunty.

---

### Post by Progressive on 2008-11-25
Yes, my mistake. 2.4 is currently in at the moment. I had just assumed 3.0 was in, seeing as how it is out and all...

KDE 4.2 alone is cool enough to make testing worthwhile, if you are nerdy enough to care. (hint: if you are reading this you probably are.)

---

### Post by xebian on 2008-11-26
KDE 4.2 beta 1 has been released yesterday.  New version is now 4.1.80 but jaunty is still at 4.1.73.  Would be nice to play with them this long holiday weekend.

---

### Post by hardhu on 2008-11-27
> **xebian said:**
> KDE 4.2 beta 1 has been released yesterday.  New version is now 4.1.80 but jaunty is still at 4.1.73.  Would be nice to play with them this long holiday weekend.

I try to ask again: could anybody who has been able to install 4.1.73 packages explain me how did he manage with the kdebase-runtime-data problem I mentioned above?

---

### Post by super.rad on 2008-11-27
> **hardhu said:**
> I try to ask again: could anybody who has been able to install 4.1.73 packages explain me how did he manage with the kdebase-runtime-data problem I mentioned above?

I had no problems at all, i just did sudo apt-get install kubuntu-desktop

---

### Post by hardhu on 2008-11-27
> **super.rad said:**
> I had no problems at all, i just did sudo apt-get install kubuntu-desktop

So maybe this is the point: kubuntu-desktop doesn't install kdebase-workspace-data and kdebase-runtime-data, that's why a lot of people doesn't have problems.

---

### Post by awakatanka on 2008-11-27
did it with update-manager, and have both installed to. no problems here atm. Only missing some applications that are not 4.1.73 our higher yet.

---

### Post by xebian on 2008-11-27
> **hardhu said:**
> I try to ask again: could anybody who has been able to install 4.1.73 packages explain me how did he manage with the kdebase-runtime-data problem I mentioned above?

This is a packaging error so you should file a bug report.  But usually you can get around it by removing the other package which has the file being overwritten, and then re-install it later after the successful install.

Or you can pass the -f (force) option to aptitude.

---

### Post by hardhu on 2008-11-28
> **xebian said:**
> This is a packaging error so you should file a bug report.  

I already did a week ago, but, sadly, nobody cared about it, and this shouldn't be a bug difficult to fix

> **xebian said:**
> 
But usually you can get around it by removing the other package which has the file being overwritten, and then re-install it later after the successful install.

Or you can pass the -f (force) option to aptitude.

Ok, I followed your first suggestion, thanks.

---

### Post by FarJumper on 2008-11-28
> **xebian said:**
> This is a packaging error so you should file a bug report.  But usually you can get around it by removing the other package which has the file being overwritten, and then re-install it later after the successful install.

But that's the point. Are there ways to remove packages while we are in "software index os broken" state?

```
box@box-linux:~$ sudo apt-get remove kdebase-runtime-data kdebase-workspace-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdebase-runtime-data (>= 4:4.1.73-0ubuntu1) but it is not going to be installed
  kdebase-workspace: Depends: klipper (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: ksysguard (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: kde-window-manager (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: systemsettings (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Recommends: kdm (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
  kdebase-workspace-bin: Depends: libplasma3 but it is not going to be installed
                         Depends: kdebase-workspace-data (= 4:4.1.73-0ubuntu3) but it is not going to be installed
  libplasma2: Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by hardhu on 2008-11-28
> **FarJumper said:**
> But that's the point. Are there ways to remove packages while we are in "software index os broken" state?

```
box@box-linux:~$ sudo apt-get remove kdebase-runtime-data kdebase-workspace-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdebase-runtime-data (>= 4:4.1.73-0ubuntu1) but it is not going to be installed
  kdebase-workspace: Depends: klipper (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: ksysguard (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: kde-window-manager (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: systemsettings (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Recommends: kdm (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
  kdebase-workspace-bin: Depends: libplasma3 but it is not going to be installed
                         Depends: kdebase-workspace-data (= 4:4.1.73-0ubuntu3) but it is not going to be installed
  libplasma2: Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

I did 
```
sudo dpkg -r --force-all kdebase-workspace-data kubuntu-desktop
```
and then I upgraded and then reinstalled those two packages.

---

### Post by xebian on 2008-11-28
> **FarJumper said:**
> But that's the point. Are there ways to remove packages while we are in "software index os broken" state?

```
box@box-linux:~$ sudo apt-get remove kdebase-runtime-data kdebase-workspace-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kdebase-runtime: Depends: kdebase-runtime-data (>= 4:4.1.73-0ubuntu1) but it is not going to be installed
  kdebase-workspace: Depends: klipper (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: ksysguard (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: kde-window-manager (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Depends: systemsettings (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
                     Recommends: kdm (>= 4:4.1.73-0ubuntu3) but 4:4.1.3-0ubuntu1~intrepid1 is to be installed
  kdebase-workspace-bin: Depends: libplasma3 but it is not going to be installed
                         Depends: kdebase-workspace-data (= 4:4.1.73-0ubuntu3) but it is not going to be installed
  libplasma2: Depends: kdebase-workspace-data (= 4:4.1.3-0ubuntu1~intrepid1) but it is not going to be installed
E: Unmet dependencies. [COLOR="Red"]Try 'apt-get -f install' with no packages[/COLOR] (or specify a solution).

```

Yours should not be that difficult.  It's just a newer version issue which is resolved by doing what it wants you to try above.  Anything left unresolved is fixed by forcing it.  But be warned it could led to more.

Or better still is to install a fresh one.  Upgrading from an older version release is sometimes flaky especially if you have installed other apps that devs didn't anticipate.

---

### Post by viikinki on 2008-12-01
I (barely) managed to install 4.1.73 while waiting 4.1.80 packages. I wonder if someone knows when they will be available in Jaunty?

---

### Post by kernelhaxor on 2008-12-01
I am sure 4.2 ..

---

### Post by awakatanka on 2008-12-02
> **viikinki said:**
> I (barely) managed to install 4.1.73 while waiting 4.1.80 packages. I wonder if someone knows when they will be available in Jaunty?

THey starting to roll in atm but its not the time to upgrade it it will break kde4 atm, i have white screen because of version conflicts between packages.

---

### Post by Progressive on 2008-12-03
I also have this white screen in my virtualized jaunty. Yet, I am able to do an Alt+F2 and access certain programs

It must be a kdebase-workspace package. I hope we get an update soon.

---

### Post by xebian on 2008-12-04
Finally, everything is now at 4.1.80, and everything seems to work now.):P

---

