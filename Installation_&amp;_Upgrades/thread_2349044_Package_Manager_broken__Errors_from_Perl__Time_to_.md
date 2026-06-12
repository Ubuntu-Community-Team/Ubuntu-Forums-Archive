---
title: "| Package Manager broken | Errors from Perl | Time to Chroot? | *PLEASE ADVISE*"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by r17 on 2017-01-10
After a recent update to Ubuntu, I began receiving internal error messages. I have 5 attachments (screenshots) that chronologically show the series of error messages I received, and what I attempted to do to resolve the problem - unsuccessfully, of course. I thought it might help to include these attachments so someone could take a look at exactly what I am seeing on my end. :confused:

Attachment 1:  obsolete package versions installed
[ATTACH=CONFIG]273122[/ATTACH]

Attachment 2:  continuation of the list of obsolete packages installed
[ATTACH=CONFIG]273123[/ATTACH]

Attachment 3:  package initramfs-tools 0.122ubuntu8.1 failed to install/upgrade: subprocess installed post-installation script returned error status 255
[ATTACH=CONFIG]273124[/ATTACH]

Attachment 4:  continuation from the same screen regarding the returned error status 255
[ATTACH=CONFIG]273125[/ATTACH]

Attachment 5:  the outcome of running both:  sudo apt-get check & sudo apt-get install -f (in the gnome terminal)
[ATTACH=CONFIG]273126[/ATTACH]

I sincerely thank in advance any assistance and apologize if this particular matter has already been addressed in another thread. I did a cursory check to see if I could find a relevant post, but I could not seem to locate what I was looking for. :confused:

---

### Post by Autodave on 2017-01-11
Did you do a fresh install or did you upgrade from an older Ubuntu version?

---

### Post by r17 on 2017-01-11
This was an upgrade from a slightly older Ubuntu version. I should also note that I am currently running Ubuntu off a USB drive, and have only been using Ubuntu since October 2016. Despite this minor hiccup, I have to say I only wish I'd made the switch years earlier!

---

### Post by Impavidus on 2017-01-12
You somehow installed or upgraded to the latest versions of glibc6-dbg and glib6-dev without upgrading to the latest version of glibc6. Furthermore you have 191 (!!) packages that can be upgraded and 3 packages that are partially installed, which may block your package manager. Getting all those packages upgraded may help to get rid of those errors. Finally dpkg encoutered trouble because there may be a problem with perl. One of those partially installed packages maybe?

Let's try and find out what those partially installed packages look like.```
dpkg --list | grep -Ev '^ii |^rc '
```
Maybe dpkg can get them fully installed (if that's what they're supposed to be).```
sudo dpkg --configure -a
```

And which version of Ubuntu is this?

---

### Post by r17 on 2017-01-12
Thank you for taking a look at this. I was starting to wonder if anyone would respond. I should also disclose the fact I am very new to the Linux world, and have only used Ubuntu since last October.. and this forum for only a matter of days. I need to re-review the tutorial on the basics of this forum. It's a lot to cover so please bare with me. 

I ran the first code to identify the partially installed packages, but I have not yet run sudo dpkg.  

[I]
"Let's try and find out what those partially installed packages look like."[/I]

[ATTACH=CONFIG]273152[/ATTACH]


*"And which version of Ubuntu is this?"*

As far as I can tell, I am using: 16.04.1 LTS "Xenial Xerus" - Release amd64 (20160719)

---

### Post by Impavidus on 2017-01-12
That doesn't look too bad now. Try configuring the packages:```
sudo dpkg --configure -a
```

The best way to get terminal output on the forum is to copy-paste it in your post. Use code tags, either by reply or quick reply->go advanced, highlight the terminal output in the post and click on #, or by typing the [noparse]```
code tags
```[/noparse] around it (like I did above).

To copy from the terminal, use select->right click->copy or select->(ctrl+shift+c). ctrl-c has had another function in the terminal since before copy-paste was invented.

---

### Post by r17 on 2017-01-12
Thank you. I was trying to figure out how everyone else could so seamlessly embed their output/code into the post!  Here is what came back.

```
dpkg: dependency problems prevent configuration of libc6-dbg:amd64:
 libc6-dbg:amd64 depends on libc6 (= 2.23-0ubuntu5); however:
  Version of libc6:amd64 on system is 2.23-0ubuntu3.

dpkg: error processing package libc6-dbg:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of libc6-dev:amd64:
 libc6-dev:amd64 depends on libc6 (= 2.23-0ubuntu5); however:
  Version of libc6:amd64 on system is 2.23-0ubuntu3.

dpkg: error processing package libc6-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
DebianLinux.pm did not return a true value at /usr/bin/linux-version line 22.
BEGIN failed--compilation aborted at /usr/bin/linux-version line 22.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 libc6-dbg:amd64
 libc6-dev:amd64
 initramfs-tools


```

---

### Post by Impavidus on 2017-01-12
Not looking good. I have to say I've never seen this one before...

The package manager (apt and dpkg are two interfaces to it, one on a higher level than the other) is usually quite capable of fixing itself, but this time it seems broken. The scripts handling installation of packages depend heavily on perl and now you get errors from three different perl modules from two different packages (linux-base and debconf). My first guess is that there's something wrong with perl. One of the errors suggests perl isn't properly configured. So let's try that next:```
sudo dpkg-reconfigure perl perl-base perl-modules-5.22
```
Then try again with```
sudo dpkg --configure -a
```
If that doesn't work it's time to try chroot from your live usb.

---

### Post by r17 on 2017-01-13
Here are the results/output from the commands. Although reading over all of that is basically like a foreign language to me - it doesn't look good. Just my luck! The irony here is that for the few times I've had problems with my computers in the past, they always managed to be these bizarre and weird incidents that usually had not been seen before. So I guess now I will be 'chroot-bound'..? :confused:


```
r17@R17:~$ sudo dpkg-reconfigure perl perl-base perl-modules-5.22
[sudo] password for r17: 
Debconf/Db.pm did not return a true value at /usr/sbin/dpkg-reconfigure line 11.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 11.
r17@R17:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libc6-dbg:amd64:
 libc6-dbg:amd64 depends on libc6 (= 2.23-0ubuntu5); however:
  Version of libc6:amd64 on system is 2.23-0ubuntu3.

dpkg: error processing package libc6-dbg:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of libc6-dev:amd64:
 libc6-dev:amd64 depends on libc6 (= 2.23-0ubuntu5); however:
  Version of libc6:amd64 on system is 2.23-0ubuntu3.

dpkg: error processing package libc6-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
DebianLinux.pm did not return a true value at /usr/bin/linux-version line 22.
BEGIN failed--compilation aborted at /usr/bin/linux-version line 22.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 libc6-dbg:amd64
 libc6-dev:amd64
 initramfs-tools


```

Is there anyone out there who could review 4 posts (#5,7,8,9) of this  thread - and advise as to what they think my next course of action  should be? I realize most of you are quite busy, yet still manage to be  so very generous with your time and efforts at helping those of us in  the dark. Thank you for again for giving us your time and expertise. It  means a lot to us!

---

### Post by Bashing-om on 2017-01-13
r17; Ouch !
Ouch ...

Mind ya messing about with the system file libc6 scares the pants off me - and I expect many others. Let's however poke at it from a safe perspective:
```

apt show libc6-dbg
apt show libc6-dev

``` indicates to me that it is safe to remove these from the system:
```

sudo apt purge libc6-dbg libc6-dev

```
Verify that you have no outside source for the libc6-dbg and libc6-dev packages .
( cat -n /etc/apt/sources.list ; tail -v -n +1 /etc/apt/sources.list.d/* )
If there are outside sources, of course disable them !
Keep in mind that if the system is updated while the invalid sources are active will but compound the problem . Let us not do that .

Now what results:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg --configure -a

```

Depending on what the package manager relates from the above, is the direction we go next.

Not at all comfortable messing about with the critical system file libc6.

But we got to do something ->
[INDENT][INDENT]right, wrong or otherwise[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
When I ran to see if there were any outside sources, the following came back..?  geesh!  I swear you guys are geniuses out there. I just look over all this and my eyes start to glaze over in panic. So based on what you say to that, then I will proceed forward as instructed. And thank you for offering to help me. I so appreciate it!


```
r17@R17:~$ ( cat -n /etc/apt/sources.list ; tail -v -n +1 /etc/apt/sources.list.d/* )
     1    # deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     6    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team, and may not be under a free licence. Please satisfy yourself as to
    14    ## your rights to use the software. Also, please note that software in
    15    ## universe WILL NOT receive any review or updates from the Ubuntu security
    16    ## team.
    17    deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
    18    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    19    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    27    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    28    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    # deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    36    
    37    ## Uncomment the following two lines to add software from Canonical's
    38    ## 'partner' repository.
    39    ## This software is not part of Ubuntu, but is offered by Canonical and the
    40    ## respective vendors as a service to Ubuntu users.
    41    # deb http://archive.canonical.com/ubuntu xenial partner
    42    # deb-src http://archive.canonical.com/ubuntu xenial partner
    43    
    44    # deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    45    # deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    46    # deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory


```

---

### Post by Bashing-om on 2017-01-13
r17; Well;

Were me, and I do advise so, I would enable the
41    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
and for sure you want to receive security updates !
Add these lines:
```

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse

``` at the bottom of the file " /etc/apt/sources.list " . I do not have any clue why these sources are now missing - You will have to make that apparent .

Once done I see no reason not to continue with update ......... configure -a .

We see then
[INDENT][INDENT]what tale gets told
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
..and by enabling 41, I'm assuming I was to just type out that entire line as I saw it on my screen (which is what I did, and the following came back):


```
r17@R17:~$ 411toppm # deb http://archive.canonical.com/ubuntu xenial partner
411toppm: Reading (64x48):  -


```


If that is ok, then I'll add the security lines and then proceed to run the next lines (post, and await your thoughts on what the package manager has related):

```
sudo apt purge libc6-dbg libc6-dev
```

&

```
sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg --configure -a
```


Regarding the matter of the missing sources list, I would have no idea how to make that apparent to you.

---

### Post by Bashing-om on 2017-01-13
r17; Nawwww ..

Short response to:
> 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

Do not rewrite the line, just remove that leading '#" character, As this tells the system the line is a comment ( with the # as the 1st character in the line) and will not be parsed.
And then yes add the security lines as given .

GO ahead and run the remove & update routines.

[INDENT][INDENT]we see then what happens
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
Voila..

```
r17@R17:~$ sudo apt purge libc6-dbg libc6-dev
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
 libstdc++-5-dev : Depends: libc6-dev (>= 2.13-0ubuntu6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
r17@R17:~$ sudo apt update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
r17@R17:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-dbg : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
r17@R17:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libc-dev-bin
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  build-essential g++ g++-5 libc6-dbg libc6-dev libstdc++-5-dev
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 78.1 MB disk space will be freed.
Do you want to continue? [Y/n] 


```

---

### Post by Bashing-om on 2017-01-13
r17; Yeah;

Looking hopeful ~

Go ahead and hit the y for yes ! .
Let it do it's thing ,,, and now what shows :
```

sudo apt autoremove
sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be not so YES
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
..after hitting the y, it came back and said: Abort.

---

### Post by Bashing-om on 2017-01-13
r17; Well .....

That ain't so good .
what shows :
```

dpkg -l libc6-dbg libc6-dev

```

And let us see what we can do to consider ..... consider ... RE-installing libc6 ,

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
```
r17@R17:~$ dpkg -l libc6-dbg libc6-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
iU  libc6-dbg:amd64                2.23-0ubuntu5        amd64                GNU C Library: detached debugging symbols
iU  libc6-dev:amd64                2.23-0ubuntu5        amd64                GNU C Library: Development Libraries and Header Files


```

---

### Post by Bashing-om on 2017-01-13
r17; Humm ....

Totally ubexpected " iU  " status !
What does the package manager do with :
```

sudo dpkg -P libc6-dbg

```
As a poke in the right direction .

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
```
r17@R17:~$ sudo dpkg -P libc6-dbg
[sudo] password for r17: 
(Reading database ... 213076 files and directories currently installed.)
Removing libc6-dbg:amd64 (2.23-0ubuntu5) ...
```

---

### Post by Bashing-om on 2017-01-13
r17; Ho Kay ..

That looked good to me .
Try now :
```

sudo dpkg -P libc6-dev

```

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
```
r17@R17:~$ sudo dpkg -P libc6-dev
[sudo] password for r17: 
dpkg: dependency problems prevent removal of libc6-dev:amd64:
 libstdc++-5-dev:amd64 depends on libc6-dev (>= 2.13-0ubuntu6).
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is to be removed.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is to be removed.
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is to be removed.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is to be removed.

dpkg: error processing package libc6-dev:amd64 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 libc6-dev:amd64


```

---

### Post by Bashing-om on 2017-01-13
r17; Welp;

Chasing further down the rabbit hole :
```

sudo apt purge build-essential

```

Tells us what ?

[INDENT][INDENT]and around and round we go some more
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
```
r17@R17:~$ sudo apt purge build-essential
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by Bashing-om on 2017-01-13
r17; K;

Now let's try again:
```

sudo dpkg -P libc6-dev

```

3 steps forward and only 2 back

---

### Post by mc4man on 2017-01-13
i'd either get libc6-dev downgraded to match current libc6 or get libc6 upgraded to current libc6-dev version, not try to remove libc6-dev..

---

### Post by r17 on 2017-01-13
Steps or no steps, it's all Greek to me :shock: !

```
r17@R17:~$ sudo dpkg -P libc6-dev
dpkg: dependency problems prevent removal of libc6-dev:amd64:
 libstdc++-5-dev:amd64 depends on libc6-dev (>= 2.13-0ubuntu6).
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is to be removed.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is to be removed.
 build-essential depends on libc6-dev | libc-dev; however:
  Package libc6-dev:amd64 is to be removed.
  Package libc-dev is not installed.
  Package libc6-dev:amd64 which provides libc-dev is to be removed.

dpkg: error processing package libc6-dev:amd64 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 libc6-dev:amd64


```

---

### Post by mc4man on 2017-01-13
Starting with 
```
apt-cache policy libc6  libc-dev-bin libc6-dev
```
All 3 must be exact same version

---

### Post by Bashing-om on 2017-01-13
@mc4man :)

@r17; Hey
^^ We follow where mc4man leads .

[INDENT][INDENT]not one thing
[INDENT][INDENT][INDENT]must be another
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
I feel like I should be playing "One Thing Leads To Another" by The Fixx..

```
r17@R17:~$ apt-cache policy libc6  libc-dev-bin libc6-dev
libc6:
  Installed: 2.23-0ubuntu3
  Candidate: 2.23-0ubuntu3
  Version table:
 *** 2.23-0ubuntu3 100
        100 /var/lib/dpkg/status
libc-dev-bin:
  Installed: 2.23-0ubuntu5
  Candidate: 2.23-0ubuntu5
  Version table:
 *** 2.23-0ubuntu5 100
        100 /var/lib/dpkg/status
libc6-dev:
  Installed: 2.23-0ubuntu5
  Candidate: 2.23-0ubuntu5
  Version table:
 *** 2.23-0ubuntu5 100
        100 /var/lib/dpkg/status


```

---

### Post by Bashing-om on 2017-01-13
r17; Uh Huh ^

That is the nature of dependency issues .

Let's try :
```

sudo apt install --reinstall libc6

```
with the hope it pulls in 2.23-0ubuntu5 .

else. not at all comfortable here messing about with the system files.

[INDENT][INDENT]try and see
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
I was also just about to say that perhaps we should be taking a look back at post #4: [https://ubuntuforums.org/showthread.php?t=2349044&p=13593787#post13593787](https://ubuntuforums.org/showthread.php?t=2349044&p=13593787#post13593787) where it appears I was somehow able to do something I didn't think was possible (or even aware of). #-o

Apparently [COLOR=#0000ff]'Attachment # 5[/COLOR]' from post #1: [https://ubuntuforums.org/showthread.php?t=2349044&p=13593109#post13593109](https://ubuntuforums.org/showthread.php?t=2349044&p=13593109#post13593109) could better explain what happened?  I honestly do not know what the hell happened or how I got myself into this mess. :frown:


```
r17@R17:~$ sudo apt install --reinstall libc6
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of libc6 is not possible, it cannot be downloaded.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by mc4man on 2017-01-13
> $ apt-cache policy libc6  libc-dev-bin libc6-dev
libc6:
  Installed: 2.23-0ubuntu3
  Candidate: 2.23-0ubuntu3
  Version table:
 *** 2.23-0ubuntu3 100
        100 /var/lib/dpkg/status
You need 2.23-0ubuntu5 installed & it's not even  a candidate. So make sure  xenial-security & xenial-updates are enabled in your software sources (Software & Updates app > Updates tab, screen

If they are already enabled then switch to a better mirror

---

### Post by r17 on 2017-01-13
:confused:

```
r17@R17:~$ sudo apt install --reinstall libc6
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 205 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,589 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
debconf: Perl may be unconfigured (Debconf/Log.pm did not return a true value at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 212787 files and directories currently installed.)
Preparing to unpack .../libc6_2.23-0ubuntu5_amd64.deb ...
Debconf/Db.pm did not return a true value at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2017-01-13
r17; Whowwwwww ..

> 
1 upgraded, 0 newly installed, 0 to remove and 205 not upgraded.


I can only hazard to guess what we will get into, but ..............
```

sudo apt update
sudo apt full-upgrade

```
here we get a fresh foothold
[INDENT][INDENT]and push some more
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
```
r17@R17:~$ sudo apt update
[sudo] password for r17: 
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]        
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                
Fetched 306 kB in 1s (214 kB/s)                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
206 packages can be upgraded. Run 'apt list --upgradable' to see them.
r17@R17:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]        
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                
Fetched 306 kB in 3s (84.1 kB/s)   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
206 packages can be upgraded. Run 'apt list --upgradable' to see them.
r17@R17:~$ sudo apt full-upgrade


```

---

### Post by Bashing-om on 2017-01-13
r17; Aaaannnnnddddd ....

We await the other show to drop.
What is the return from 
sudo apt full-upgrade

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
I have not run [COLOR=#0000ff]'apt list --upgradable'[/COLOR] - as Mr. Terminal recommended, because I was not sure if I should wait and have the output looked over beforehand. All of this is still very new to me - including Ubuntu.. but as the late great Jim Morrison would say, I too are ready to break on through to the other side!  I've been on a mid to late 60's music binge as of late, for some reason...  But I digress.  Based on the data below, I think we need to purge or remove/delete [COLOR=#0000ff]'2.23-0ubuntu3'[/COLOR] - because it looks as though that is still installed and creating a conflict - and then run the list of upgradable packages?..  *Good thing you're a Libra! They bring balance & patience when most just throw in the proverbial towel!* 

```
r17@R17:~$ sudo apt full-upgrade
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.


```

---

### Post by Bashing-om on 2017-01-13
r17; Uhmmm uhhhmmmm uuuhmmmmm...........

Give you an idea of the why I am so reluctant to mess with libc6 ;
FYI see the output of terminal command:
```

apt show libc6

```
In additional to this as a required package - in the correct version ! -- there is :
> 
libraries that are used by nearly all programs on
 the system.

OK, so now that the system is requesting the -f ; let's see what it will do:
```

sudo apt -f install

```

If we were to bite the big bullet and remove libc6, I just do not know what the result - or what might happen in the event we could not get libc6-2.23-0ubuntu5 installed when that required package and ALL it's dependencies have been removed from the system . ouch !

I have never been there nor directed such an action on any part . I sure do not want to break your system beyond what we can repair !

[INDENT][INDENT]difficult situation
[INDENT][INDENT][INDENT]hard choices ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r17 on 2017-01-13
Point taken!

```
r17@R17:~$ sudo apt -f install
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 205 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,589 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
debconf: Perl may be unconfigured (Debconf/Log.pm did not return a true value at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 212787 files and directories currently installed.)
Preparing to unpack .../libc6_2.23-0ubuntu5_amd64.deb ...
Debconf/Db.pm did not return a true value at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by mc4man on 2017-01-13
apt can be less than verbose as to why it won't install or upgrade a package. You could - 
1st confirm the latest libc6 package is available with apt-cache

Then if you can install aptitude do so & try upgrading libc6 with it.

Otherwise go here & download the libc6 package for your arch & use apt to simulate installing, i.e.
 sudo apt -s /path/to/libc6packagename
[http://packages.ubuntu.com/xenial-updates/libc6](http://packages.ubuntu.com/xenial-updates/libc6)

---

### Post by r17 on 2017-01-13
this post came from [COLOR=#ff8c00]mc4man[/COLOR]:

[I]"apt can be less than verbose as to why it won't install or upgrade a package. You could - 
1st confirm the latest libc6 package is available with apt-cache

Then if you can install aptitude do so & try upgrading libc6 with it.

Otherwise go here & download the libc6 package for your arch & use apt to simulate installing, i.e.
 sudo apt -s /path/to/libc6packagename
[URL="http://packages.ubuntu.com/xenial-updates/libc6"]http://packages.ubuntu.com/xenial-updates/libc6"

[/URL][/I]
[LIST]
[*]I'm assuming that when he talked about 1st trying to confirm the latest libc6 package is available with apt-cache - he is referring to running the [COLOR=#0000ff]'apt list --upgradable' [/COLOR]command? 
[*]I don't know what aptitude is, but I'm assuming that is a package or some other program that, if available, would appear on the aforementioned command? 
[*]Also, would you recommend I just download the update from the link he provided, and run an installing simulation? 
[/LIST]

Here is the return you had asked to see (with baited breath) LOL! I previously posted, but I'm not sure if you had the chance to take a look at it.

```
r17@R17:~$ sudo apt -f install
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 205 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,589 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
debconf: Perl may be unconfigured (Debconf/Log.pm did not return a true value at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 212787 files and directories currently installed.)
Preparing to unpack .../libc6_2.23-0ubuntu5_amd64.deb ...
Debconf/Db.pm did not return a true value at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 255
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.23-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2017-01-14
r17; Welpl

like unto this:
> 
1st confirm the latest libc6 package is available with apt-cache

means:
```

apt-cache policy libc6

```
so you see that "Candidate: 2.23-0ubuntu5" ?

and for aptitude:
> 
Then if you can install aptitude do so & try upgrading libc6 with it.

to install:
```

sudo apt install aptitude

```

the rest is left to go there in a bad event that even aptitude can not help resolve . 


[INDENT][INDENT]Oh my 'buntu
[INDENT][INDENT][INDENT]what have I done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by r17 on 2017-01-14
..back again for more!.. I finally fell asleep after being up for nearly 38hours.  That wouldn't be the first or last time it will happen.  :shock:   So here is what came back per your last instructions.  And thank you again for the time you spent with me thus far.

```
r17@R17:~$ apt-cache policy libc6
libc6:
  Installed: 2.23-0ubuntu3
  Candidate: 2.23-0ubuntu5
  Version table:
     2.23-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
 *** 2.23-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
r17@R17:~$ sudo apt install aptitude
[sudo] password for r17: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: aptitude-common (= 0.7.4-2ubuntu2) but it is not going to be installed
            Depends: libcwidget3v5 but it is not going to be installed
 libc6-dev : Depends: libc6 (= 2.23-0ubuntu5) but 2.23-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by Bashing-om on 2017-01-14
r17; Morning .....

I am at an impasse as to a best practice here to get the needed libc-62.23-0ubuntu5 to install .

We have some hints - but way above my skill level to follow:
one hint is:
> 
Debconf/Db.pm did not return a true value at /usr/share/debconf/frontend line 6.

line 6 points back to the debconf database :
> 
use Debconf::Db;

Now, I do happen to know that the database can be re-configured, but with the state of the system, I am not convinced this is a good thing to do.

Maybe best at this time to follow  mc4man thought process and download the ,deb file from source and then try and install it ?


[INDENT][INDENT]we done got deep
[/INDENT][/INDENT]

---

### Post by mc4man on 2017-01-14
it's looking like your issues extend well beyond just libc6. I'd consider a fresh install, it'll only take 5 - 15 min.

---

### Post by Impavidus on 2017-01-18
Sorry, didn't have much opportunity to pop in for a few days. Thanks for joining, Bashing-om & mc4man.

The line quoted by Bashing-om suggests that there's something really wrong with the package manager itself. It may be possible to reinstall and reconfigure the required pieces of software using a live disk, but I don't know exacly which packages to fix. Reinstalling is the fastest way out of your problem.

---

### Post by r17 on 2017-01-20
That's ok, no problem. Bashing-om was very helpful and patient, considering my relative inexperience with Ubuntu and the increasingly complex & mysterious nature of the problem.  mc4man was also very helpful and popped in (seemingly from out of nowhere) - and we decided to follow his lead!  I'm currently operating a Live version of 16.04 LTS from a 2GB USB key.  At the moment, still trying to figure out whether to download and create a Live version with persistence vs. a full installation on a 16GB USB key. I recently had the HD removed from my computer, so I am operating entirely off the USB's temporarily until I purchase a new computer next month.

---

### Post by r17 on 2017-01-20
I've about given up. I'm so drained at this point having spent countless hours for days now - trying to do what appears to be so basic.  I can't even figure out how to do a full install.  I've had at least 30-60 tabs open at any given time in Firefox searching far and wide all over the Internet. It's all just too complicated. I've really tried my best.  What I can say is that the hard drive in my computer has failed - and was recently removed.  I have a 16GB and 2GB pendrives.  I would prefer to do a fresh install on the 16GB pendrive (or at the very least a live edition w/ persistence) - until I am able to purchase a new computer next month. I am currently able to write this post - from the 2GB pendrive - where I somehow managed to install 16.04 LTS - and run it live (without installing).

---

### Post by Impavidus on 2017-01-21
Well, failing hardware can cause the strangest errors imaginable. This kind of problem is not common on Ubuntu systems.

---

