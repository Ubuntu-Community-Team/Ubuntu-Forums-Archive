---
title: "Software Updater Error"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2013-04-28
When ever I try to get the latest updates, including trying to upgrade to 13.04, I get this Internet error:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.13 80]
, W:Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

What might be causing this error? My Internet works fine otherwise.

Spike

---

### Post by ibjsb4 on 2013-04-28
Those are karmic sources, what are you running?

---

### Post by SpikeLS6 on 2013-04-28
Ubuntu 12.10 installed from upgrades.

Spike

---

### Post by ibjsb4 on 2013-04-28
Ok, you need to remove that one PPA ([http://ppa.launchpad.net/screenlets](http://ppa.launchpad.net/screenlets)), there is no 12.10 package for it.

[http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/](http://ppa.launchpad.net/screenlets/ppa/ubuntu/dists/)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Then you also need to remove all those karmic sources.  If you run into trouble doing this, please post your sources list.

```
cat -n /etc/apt/sources.list
```

---

### Post by SpikeLS6 on 2013-04-28
I do not know how to remove the PPA's. Is there a Terminal Code for it? I would rather ask than delete something I should not.

Spike

---

### Post by ibjsb4 on 2013-04-28
> **SpikeLS6 said:**
> I do not know how to remove the PPA's. Is there a Terminal Code for it? I would rather ask than delete something I should not.

Yes there is, but you should be able to do it from the above posted link.  Try this in terminal:

```
gksudo software-properties-gtk
```

Then go to the "Other Software" tab and either remove said PPA or just uncheck it.

---

### Post by SpikeLS6 on 2013-04-28
Figured out, with your last help.ubuntu.com ...Repositores how to delete the launchpad PPA's. It is still referencing Karmic, and I had already deleted anything related to Karmic.

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.14 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I have read some backport information from the forum, but see nothing in Updater or Software Updater that refers to backports. Must this be done manually through the Terminal?

Spike

---

### Post by SpikeLS6 on 2013-04-28
This is the "cat -n /etc/apt/sources.list" :

michael@michael-desktop-E:~$ cat -n /etc/apt/sources.list
     1    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     2    # newer versions of the distribution.
     3    
     4    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal main restricted
     5    deb-src [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal restricted main multiverse universe #Added by software-properties
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-updates main restricted
    10    deb-src [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-updates restricted main multiverse universe #Added by software-properties
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal universe
    16    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-updates universe
    17    
    18    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    19    ## team, and may not be under a free licence. Please satisfy yourself as to 
    20    ## your rights to use the software. Also, please note that software in 
    21    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    22    ## security team.
    23    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal multiverse
    24    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-updates multiverse
    25    
    26    ## Uncomment the following two lines to add software from the 'backports'
    27    ## repository.
    28    ## N.B. software from this repository may not have been tested as
    29    ## extensively as that contained in the main release, although it includes
    30    ## newer versions of some applications which may provide useful features.
    31    ## Also, please note that software in backports WILL NOT receive any review
    32    ## or updates from the Ubuntu security team.
    33    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    34    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
    35    
    36    ## Uncomment the following two lines to add software from Canonical's
    37    ## 'partner' repository.
    38    ## This software is not part of Ubuntu, but is offered by Canonical and the
    39    ## respective vendors as a service to Ubuntu users.
    40    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    41    
    42    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-security main restricted
    43    deb-src [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-security restricted main multiverse universe #Added by software-properties
    44    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-security universe
    45    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-security multiverse
    46    deb [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-backports restricted main multiverse universe
    47    deb-src [http://mirror.symnds.com/ubuntu/](http://mirror.symnds.com/ubuntu/) quantal-backports restricted main multiverse universe #Added by software-properties
michael@michael-desktop-E:~$

---

### Post by ibjsb4 on 2013-04-28
Ok, making good progress :)

You can solve half the problem by just unchecking "Source Code"

[ATTACH=CONFIG]241938[/ATTACH]

Then please post your sources list (post #4)

EDIT:  Ok, you read my mind :) give me a minute to figure this out.

---

### Post by ibjsb4 on 2013-04-28
Now .. In terminal:

```
gksudo gedit /etc/apt/sources.list
```

And comment out (##) line 33. 
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

 Then you should be good to go.  Check with an update.

```
sudo apt-get update
```

---

### Post by SpikeLS6 on 2013-04-28
This is what the gksudo gedit... command did in Terminal.

michael@michael-desktop-E:~$ gksudo gedit /etc/apt/sources.list

(gksudo:5139): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed

(gksudo:5139): Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed
michael@michael-desktop-E:~$ 

Not sure how to do the ## on line 33. I do see that it corresponds with the karmic backports problem, though.

Spike

---

### Post by ibjsb4 on 2013-04-28
Looking for a fast fix, try ..

```
sudo gedit /etc/apt/sources.list
```

And/or

```
gksudo nautilus
```

Either one of those work?

Gdk-CRITICAL **: IA__gdk_error_trap_pop: assertion `gdk_error_traps != NULL' failed seems to  be a bug with a questionable fix.

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/1075928](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/1075928)

---

### Post by SpikeLS6 on 2013-04-28
I put "##" in front of both lines (33 & 34)

##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
##deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

Software Updater worked! It even said 13.04 is available to upgrade.

I'll consider this issue solved and mark the first post.

Thank you very much for your help. I learned a number of things and took a bunch of notes for the future. I'll try the Upgrade tomorrow.

Thanks again.

Spike

---

### Post by ibjsb4 on 2013-04-28
Good show :D

Upgrading may even solve that bug, so good luck on that.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

