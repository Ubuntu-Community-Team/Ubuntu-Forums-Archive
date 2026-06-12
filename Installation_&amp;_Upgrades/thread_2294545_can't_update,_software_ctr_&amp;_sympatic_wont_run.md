---
title: "can't update, software ctr &amp; sympatic wont run, VirtualBox problem"
date: 2015-09-11
forum: Installation &amp; Upgrades
---

### Post by sam_baker2 on 2015-09-11
hi,
I am trying to update my laptop and I am having several problems. 
I have a red circle icon in my panel with a horizontal white strip through it.
When I click on it it says:
```

An error occurred.Please run Package Manager
from the right-click menu or apt-get in a terminal to see what is wrong.
The error message was 'Unknown error:<class 'SystemError >' (E. The 
package virtualbox-4.3 needs to be reinstalled, but I can't find the
archive for it.)' This usually means that your installed packages have
unmet dependencies.


```


Then, when I try to start the package manager I get this error:

```

E. The package virtualbox-4.3 needs to be reinstalled, but
I can't find an archive for it.
E. Internal error opening cache (1). Please report.


```

When I try to do a sudo apt-get install virtualbox in the terminal
I get:
```

E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.


```
~also, for some reason Sympatic and the software center won't run


I have the virtualbox deb package on my laptop that was downloaded from a few months ago
```

virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb

```


 
any help appreciated

---

### Post by Bashing-om on 2015-09-11
sam_baker2; Hello;

Right off hand:
> 
virtualbox-4.3_4.3.28-100309~Ubuntu~[color=red]raring-[/color]_amd64.deb

I might suggest that you update your source from the old End_Of_Life raring to what is current.
By the way, I show for 14.04 in our software repository:
```

sysop@1404mini:~$ apt-cache show virtualbox
Version: 4.3.10-dfsg-1ubuntu5
Filename: pool/multiverse/v/virtualbox/virtualbox_4.3.10-dfsg-1ubuntu5_amd64.deb

```

[INDENT][INDENT]hey it is a thought
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-11
If you are using 13.04 Raring please update to a supported release, 12.04 LTS, 14.04 LTS or 15.04. 

Virtualbox is available from the repositories. You shouldn't need to install from a third-party.

---

### Post by sam_baker2 on 2015-09-11
I am using 14.04 LTS
How do I get VirtualBox from the repositories?
I get this
```


sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by Bucky Ball on 2015-09-11
Try:

```
sudo apt-get --purge remove virtualbox-4.3
```

... then try again.

---

### Post by sam_baker2 on 2015-09-11
I still get this :

```
sudo apt-get --purge remove virtualbox-4.3
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by Bucky Ball on 2015-09-11
Could you please run these commands and post any and all errors, please. 

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Ignore errors and carry on with the next command but remember to post the errors back here. These commands will not upgrade your current OS release to a newer one.

---

### Post by sam_baker2 on 2015-09-11
```

ella@joe:~$ sudo apt-get autoremove
[sudo] password for ella: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

```sudo apt-get update


I had no errors on this one:
```

sudo apt-get update

```




Will "upgrade" & "dist-upgrade" not change 14.04 to something else?
I want to keep 14.04 LTS if posible

---

### Post by Bucky Ball on 2015-09-11
Did you have errors on any of them apart from the 'normal' one you've been getting?

As I posted in my last, no, you won't upgrade the release ...

> **Bucky Ball said:**
>  These commands will not upgrade your current OS release to a newer one.

---

### Post by sam_baker2 on 2015-09-11
If I run

```

sudo apt-get upgrade sudo apt-get dist-upgrade

```

in the terminal, will it ~not~ upgrade the laptop to a latter version than 14,04?
I want to keep 14.04

---

### Post by Bucky Ball on 2015-09-11
See post 7 and 9.

---

### Post by sam_baker2 on 2015-09-11
sorry I didn't see your response that it will not upgrade....will do now.

---

### Post by sam_baker2 on 2015-09-11
```

sudo apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

```

```

sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by Bashing-om on 2015-09-11
sam_baker2; Hey;

IF you installed virtualbox ( raring) at some point from a PPA, maybe we can ppa-purge it to get to the version in our software repository ?

To check:
Post back the outputs - Between Code Tags -
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

@Bucky Ball; Thoughts ?

[INDENT][INDENT]I think
[INDENT][INDENT][INDENT]maybe a possibility
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sam_baker2 on 2015-09-11
```

 cat -n /etc/apt/sources.list

     1    # deb cdrom:[Xubuntu 14.04.2 LTS _Trusty Tahr_ - Release amd64 (20150218.1)]/ trusty main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main


```




```

cat /etc/apt/sources.list.d/*.list

deb http://ppa.launchpad.net/gencfsm/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gencfsm/ppa/ubuntu trusty main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main





```

---

### Post by Bashing-om on 2015-09-11
sam_baker2; Welp;

So much for that theory .. not a thing in the sources(s) to relate to virtualbox.
Bucy Ball, how 'bout we sic 'dpkg' on virtualbox ?

What have we ? 
show:
```

apt-cache policy virtualbox

```
see what else we can find to facilitate removing/re-installing virtualbox.
[INDENT] what does it take
[INDENT][INDENT][INDENT]to keep an application like you
[INDENT][INDENT][INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sam_baker2 on 2015-09-11
```

apt-cache policy virtualbox

virtualbox:
  Installed: (none)
  Candidate: 4.3.10-dfsg-1ubuntu5
  Version table:
     4.3.10-dfsg-1ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/multiverse amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/multiverse amd64 Packages
     4.3.10-dfsg-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages

```


I also found this link. Seems someone had a similar problem.
I believe did have a wi-fi disconnects, few weeks ago, when I was updating.
That may have messed something up.

```

https://answers.launchpad.net/ubuntu/+source/software-center/+question/247001

```

---

### Post by ajgreeny on 2015-09-11
I am now using VBox 5.0.4 from the VBox repository which you can add to your software-sources by using command ```
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -
```
This info is all copied direct from the Oracle VBox page at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads).

When I first tried it in Xubuntu in which I use compton compositor it gave me a problem of dark shadow over the guest screen which can be removed by adding the line ```
"n:w:*VirtualBox*",
```to the **shadow-exclude = [** section of .compton.conf in your home folder.

VBox v5 seems to be faster and better than v4.3 which I used for a long time and now the shadow problem is solved I thoroughly recommend it.

---

### Post by Bashing-om on 2015-09-12
sam_baker2; Hi !

Not really sure how to go about this:
> 
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.

virtualbox:
  Installed: (none)
  Candidate: 4.3.10-dfsg-1ubuntu5virtualbox:
  Installed: (none)
  Candidate: 4.3.10-dfsg-1ubuntu5


If the package manager thinks it is not installed, I bet the package manager can not UN-install it... but let's see what does result at a lower level:
```

sudo dpkg -P virtualbox

```
Post back the result, and we see where we go from here.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by sam_baker2 on 2015-09-15
@ Bashing-om

```

dpkg -P virtualbox

dpkg: warning: ignoring request to remove virtualbox which isn't installed


```

~also, I would mention that when I try to run "synaptic package manager" , I get this message in a window:
```

E. The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.
E. Internal error opening cache (1). Please report

```
Then when I close the window out, synaptic disappears.

The software center just briefly pops up, and then disappears also.

---

### Post by ajgreeny on 2015-09-15
I have only just noticed that you say you have the package **virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb** on your laptop at the moment.

This is the package that you must have downloaded direct from the Oracle web-site and the name happens to contain the raring name, but is not just for raring but for all later later Ubuntu versions as well; I know because I did use it in 14.04 with great success.

I do not know how you installed it, (dpkg, software-center or gdebi) but I normally use gdebi to install any directly downloaded .deb packages.

Try installing gdebi if you don't already have it with ```
sudo apt-get install gdebi
``` then right click on that vbox package and select to open it with gdebi.  With luck you may get a window like my screenshot with options to download, reinstall or remove the package.  If you remove it this way, you can then use the method I mentioned in post #18 to install the most recent VBox version from the VBox repository.

Note my gdebi screenshot is for the VBox version I have installed, 5.0.4, not the 4.3.28 version you have, but it should work just as mine did.

---

### Post by sam_baker2 on 2015-09-15
@ajgreeny:

I still get this:

```

 sudo apt-get install gdebi
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.3 needs to be reinstalled, but I can't find an archive for it.


```

---

### Post by ajgreeny on 2015-09-15
OK so let's try this.

Open terminal and mavigate to the folder where the virtualbox deb package is sited on your laptop, then try running ```
sudo dpkg i virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb
```

If that is still unsuccessful, man dpkg suggests you may need to either reinstall with dpkg or force removal
```
Package flags
       reinst-required
              A package marked reinst-required is broken and requires reinstallation. These packages cannot
              be removed, unless forced with option --force-remove-reinstreq.
```

---

### Post by sam_baker2 on 2015-09-15
```

sudo dpkg i virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb

dpkg: error: need an action option
Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

```

---

### Post by Bashing-om on 2015-09-15
sam_baker2; Hey !

A slight typo ... correct to be ' dpkg -i ' :
```

sudo dpkg -i virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb

```

That's the thing
[INDENT][INDENT]linux expects you to say what you mean
[INDENT][INDENT][INDENT]and mean what you say
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sam_baker2 on 2015-09-15
thks Bashing-om

That seemed to do it. I can now run synaptic and sotware center. Also, VB will run.
I did a software update after I did the 
```

sudo dpkg -i virtualbox-4.3_4.3.28-100309~Ubuntu~raring_amd64.deb

```
and had nearly 130 meg of updates to do. New kernel, firmware, browser, bunch of stuff.
I still received a few errors when installing the updates, but seems to be running ok for now.

After I first installed 14.04 to this machine, I was receiving annoying sporadic disconnects from the wifi and I think 
that may have caused something to get messed up. 
As an aside, I had to do this for a fix for the wifi driver, but still I am
getting wifi disconnects every once in a while:
```

sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
sudo reboot 

```

---

### Post by Bashing-om on 2015-09-15
sam_baker2; All to the good.

You have ajgreeny to thank for the solution. 

As to the WIFI problem - That one I can not help with. Open a new thread on that issue.

If the original thread issue is resolved to your satisfaction at this time
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Else:
> 
I still received a few errors when installing the updates, but seems to be running ok for now.

Show us the commands with the results . We see then what condition the condition is in. - we do not quit 'til it is whooped

[INDENT][INDENT]threads are like unto dead men
[INDENT][INDENT][INDENT]just one to the box (issue)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sam_baker2 on 2015-09-16
@ajgreeny 
Thks ajgreeny. I will see how this goes for the next week or so.

---

### Post by ajgreeny on 2015-09-16
Whoops, sorry about the typo; my fingers don't work as fast as my brain, and sometimes my brain isn't as fast as I'd like.

However, I am glad you are now up and running with updates and VBox; did you update to VBox 5.0.4 and if so, what do you think of it?

---

