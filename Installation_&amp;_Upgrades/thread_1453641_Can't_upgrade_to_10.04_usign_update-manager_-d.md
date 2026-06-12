---
title: "Can't upgrade to 10.04 usign update-manager -d"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by Romanovzky on 2010-04-13
Basically, the update manager pops up and... nothing happens. It checks for updates but doesn't indicate upgrade availability.

Running other commands like apt-get distribution-upgrade also doesn't do anything.

More info:

```

mcromao@landau:~$ do-release-upgrade 
Checking for a new ubuntu release
No new release found
mcromao@landau:~$ do-release-upgrade -d
Checking for a new ubuntu release
No new release found

```

I think the problem is the fact that I've installed a bunch of software from rep's and ppa's via ubuntu-tweak that are more recent than the ones in Ubuntu's rep, but I can't been sure.

Also, I've deactivated all third party rep's and ppa's, but I still have a bunch of software installed via those sources.

---

### Post by Romanovzky on 2010-04-14
Bump!

Tested on another computer (same reps and ppas and all) and the update manager offered me the chance to upgrade distro.


any ideas?

---

### Post by oldos2er on 2010-04-14
10.04 won't be released until the 29th.

---

### Post by Slim Odds on 2010-04-14
> **Romanovzky said:**
> Basically, the update manager pops up and... nothing happens. It checks for updates but doesn't indicate upgrade availability.
...

What version are you currently using?

If you're not using 8.04 or 9.10, there is no upgrade path.

---

### Post by Slim Odds on 2010-04-14
> **oldos2er said:**
> 10.04 won't be released until the 29th.

If 8.04 or 9.10 is installed, it should offer to upgrade even though it's beta.

---

### Post by beta.tester on 2010-04-14
> **Romanovzky said:**
> Basically, the update manager pops up and... nothing happens. It checks for updates but doesn't indicate upgrade availability.

Running other commands like apt-get distribution-upgrade also doesn't do anything.

More info:

```

mcromao@landau:~$ do-release-upgrade 
Checking for a new ubuntu release
No new release found
mcromao@landau:~$ do-release-upgrade -d
Checking for a new ubuntu release
No new release found

```

I think the problem is the fact that I've installed a bunch of software from rep's and ppa's via ubuntu-tweak that are more recent than the ones in Ubuntu's rep, but I can't been sure.

Also, I've deactivated all third party rep's and ppa's, but I still have a bunch of software installed via those sources.

Hi

Have you made sure you have the latest Ubuntu Tweak? 5.3.1 for Lucid and how does it react when you try to update from within Tweak?

Works great here even the option to reposition the resizing icons :)

Keep Ubuntuing    john

---

### Post by Romanovzky on 2010-04-14
Going to try update UTweak and see if it changes anything, UTweak my have screwed the paths for update manager in some way.

BTW, yes I'm running 9.10 and yes I'm trying to go for beta.

---

### Post by Romanovzky on 2010-04-14
Well, can't get good results.

I guess it may have to do with some screwed up information in update manager or something, but apt-get autoclean, autoremove, check, update, all runs normal and any package manager complains... 

I've also tried to reinstall update-manager-* but nothing.

For those who want to be sure I'm running 9.10:

```

mcromao@landau:~$ lsb_release -vidrc
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

---

### Post by drs305 on 2010-04-14
](*,)

Edit: Guess if I'd reread the *title* instead of just the posts I would have seen that.

Have you tried "update-manager -d"?

---

### Post by Romanovzky on 2010-04-14
I've done it all.

update-manager -d/-c/-p/--dist-upgrade
apt-get dist-upgrade

By terminal and by alt-f2.

all say that I've the system up to date.

Weird isn't it?

I've searched allot in the web, I found many similar bug (I found many related to missing update-manager-* packages missing, server edition related,...) but nothing like this.

I would feel special with the fact that it seems an unique bug! But I'm quite pissed.

Come on Ubuntu Community, this is a brand new challenge for you!

---

### Post by drs305 on 2010-04-14
Are you using a standard install of Karmic or a UNR version? 

How about the repositories - are you using a UNR repository that may not contain the Lucid beta?

I've not used the UNR version of Ubuntu, so I'm hoping these aren't ridiculous questions.  ;-)

---

### Post by Romanovzky on 2010-04-14
I think you may have "solved it".

I'm using UNR, and maybe the UNR hasn't a beta release information in the repositories.

Still, the deb repositories that came by default are the same that those in a standard release, as for all other reps and ppas that I've added, but UNR may lack the path to do so in update-manager.

Is this possible? To use the same repositories but not to have the information to update to dev releases?

---

### Post by jamesjai on 2010-05-01
Dear all,

I also tried all the step mentioned here, but my update manager is not showing any upgrade option.

Please help me... I am egar to upgrade to Ubuntu Lucid, LT 10.04....

Thank you.

Best regards.

---

### Post by Slim Odds on 2010-05-01
> **jamesjai said:**
> Dear all,

I also tried all the step mentioned here, but my update manager is not showing any upgrade option.

Please help me... I am egar to upgrade to Ubuntu Lucid, LT 10.04....

Thank you.

Best regards.

A) Start a new thread
B) Give some information (like what version of Ubuntu you're currently using).

Then there is a chance that you might get some help.

---

### Post by jamesjai on 2010-05-02
I have post a thread already, please refer below my thread, 

"No upgrade option in Update Manager"

lsb_release -a && uname -r says,

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
2.6.31-21-generic

Please help me to solve this problem... :(

Thanks...

---

### Post by Slim Odds on 2010-05-02
Well... I am also running 9.10 and here is what I see (see attachment) when I open the update manager from the Administration menu....

It offers me a new release.

Something in your system must be corrupted. Have you done any special kind of customization?

---

### Post by Phkillah on 2010-05-21
I'm having the exact same problem right now....

```
phk@phk-laptop:~$ sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
phk@phk-laptop:~$ sudo do-release-upgrade 
Checking for a new ubuntu release
No new release found

```

=((

---

### Post by Phkillah on 2010-05-21
> **Phkillah said:**
> I'm having the exact same problem right now....

```
phk@phk-laptop:~$ sudo lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
phk@phk-laptop:~$ sudo do-release-upgrade 
Checking for a new ubuntu release
No new release found

```

=((

Ok, the solution...

Using VI editor tool to replace Text "Jaunty" to "Karmic" at once:
$ vi /etc/apt/source.list

Then type the following command at the bottom of the VI editor:
:%s/karmic/lucid/g

You will see the following message:
18 substitutions on 18 lines

Now save and quit.
:wq!

Now just do it.
sudo apt-get update && sudo do-release-upgrade


Cheers

---

### Post by Holzz on 2010-06-06
> **Phkillah said:**
> Ok, the solution...

Using VI editor tool to replace Text "Jaunty" to "Karmic" at once:
$ vi /etc/apt/source.list

Then type the following command at the bottom of the VI editor:
:%s/karmic/lucid/g

You will see the following message:
18 substitutions on 18 lines

Now save and quit.
:wq!

Now just do it.
sudo apt-get update && sudo do-release-upgrade


Cheers
hi
i've the same problem and if i try the above it says: "E486: Pattern not found:karmic" :confused:
i'm a total ubuntu noob and any help would be appreciated :D

---

### Post by wojox on 2010-06-06
> **Holzz said:**
> hi
i've the same problem and if i try the above it says: "E486: Pattern not found:karmic" :confused:
i'm a total ubuntu noob and any help would be appreciated :D

Open a terminal and run this

```
perl -p -i.karmic -e 's/karmic/lucid/' /etc/apt/sources.list
```

Then

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by koley on 2010-06-06
Dear All,

I have recently updated my ubuntu 9.04 to Ubuntu 10.04. Unfortunately I am not able to update my OS, since there is no connection to the repository. I tried this update since last week.  
When I do;
>sudo apt-get update
I get
--------------------------------------------------------------------------------------------
"Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (111.91.91.37). - connect (110: Connection timed out)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN
  Unable to connect to archive.canonical.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release.gpg
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http:
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-security/multiverse Sources
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
  Unable to connect to archive.canonical.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages".........................................
----------------------------------------------------------------------------------------------------

I have attached my sources.list file:
"
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
"

Can anyone help me, where is the problem,.........I know that my net is working file and the repositories are reachable.

Regards

Koley

---

### Post by oldos2er on 2010-06-06
Koley, you're more likely to get help if you start a new thread for your problem.

---

### Post by wojox on 2010-06-06
> **koley said:**
> Dear All,

I have recently updated my ubuntu 9.04 to Ubuntu 10.04. Unfortunately I am not able to update my OS, since there is no connection to the repository. I tried this update since last week.  

<snip>

Can anyone help me, where is the problem,.........I know that my net is working file and the repositories are reachable.

Regards

Koley

Works here. Try it again. Are you behind a firewall proxy?

---

### Post by koley on 2010-06-07
Thanks Ann for your info,....This was my first scrap to Ubuntu forums and hence somewhere lost where to place it

@wojox,
this I am connected through a proxy server in my institute,....but nothing happens to my old desktop ubuntu 9.04, the updates works well.

---

### Post by koley on 2010-06-08
Thanks wojox, it worked (the update) there was some problem with the in-house proxy server.
Cheers

---

### Post by Holzz on 2010-06-11
> **wojox said:**
> Open a terminal and run this

```
perl -p -i.karmic -e 's/karmic/lucid/' /etc/apt/sources.list
```Then

```
sudo apt-get update; sudo apt-get upgrade
```

thx for your answer. i tried the above but after entering the first line i get

> Can't rename /etc/apt/sources.list to /etc/apt/sources.list.karmic: Permission denied, skipping file.looks like i have no permission?

---

### Post by Slim Odds on 2010-06-12
> **Holzz said:**
> thx for your answer. i tried the above but after entering the first line i get

looks like i have no permission?

The first command needs a sudo also

---

