---
title: "Upgrading from Edgy to Feisty"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by mhenriday on 2007-03-15
Will it be possible for **Edgy** users to _upgrade_ directly to **Feisty** when the latter is released, just as they could upgrade from **Dapper** to **Edgy** ? Or will they have to download and burn the live CD, and then install ?...

Henri

---

### Post by floke on 2007-03-15
You can upgrade anytime, though clearly best to wait until the final version for stability - though I've been running Feisty since Herd 4 with no problems (except a Beryl crash that's now been fixed).

Use gksu "upgrade-manager -c -d" for the upgrade

Could take an hour or so to complete though...

Good luck

---

### Post by dreadlord_chris on 2007-03-16
> **Steve.K said:**
> You can upgrade anytime, though clearly best to wait until the final version for stability - though I've been running Feisty since Herd 4 with no problems (except a Beryl crash that's now been fixed).

Use gksu "upgrade-manager -c -d" for the upgrade

Could take an hour or so to complete though...

Good luck

lol... mine took like 4 hours w/broadband - but it works like a charm, so.....

---

### Post by mhenriday on 2007-03-16
> **Steve.K said:**
> ...

Use gksu "upgrade-manager -c -d" for the upgrade

...

Am I correct in understanding you to mean that all I have to do to upgrade from **Edgy** to the currently available (pre-release) version of **Feisty** is to write «sudo upgrade-manager -c -d» in terminal ? Can I expect my data to be preserved during the process, just as they were when I upgraded from **Dapper** to **Edgy** ?...

Henri

---

### Post by liveforfunnow on 2007-03-17
my data was preserved, but i used

gksu "upgrade-manager -c -d"

not

sudo upgrade-manager -c -d

your data should be safe. it is an in-place upgrade.

---

### Post by Aurigas on 2007-03-17
One question, it's only in english? I mean, I know that the translation is still open but... can i use other languages?

---

### Post by mhenriday on 2007-03-17
> **liveforfunnow said:**
> my data was preserved, but i used

gksu "upgrade-manager -c -d"

not

sudo upgrade-manager -c -d

...

Sorry to sound so much the doubting Thomas, but the upgrade command to be typed in the terminal is 

«gksu upgrade-manager -c -d», and _not_

«gksudo upgrade-manager -c -d» ? I had the impression that in Ubuntu, «su» is generally replaced by «sudo»....

Henri

---

### Post by kolslorr on 2007-03-20
Hi,

I used gksu "update-manager -c -d", selected to upgrade to 7.10, and it starts to run.

But, it always fails at certain stage when retrieving for the files.. something like file 70 of 72... then it stuck there for like 30 mins and finally it fails.. Saying cannot connect the server... :(


can anyone advise me what did I do wrong?

---

### Post by liveforfunnow on 2007-03-20
> **mhenriday said:**
> Sorry to sound so much the doubting Thomas, but the upgrade command to be typed in the terminal is 

«gksu upgrade-manager -c -d», and _not_

«gksudo upgrade-manager -c -d» ? I had the impression that in Ubuntu, «su» is generally replaced by «sudo»....

Henri

you can use sudo, but gksu is more suited for use when launching GNOME/GTK applications. similarly, you should use kdesu for KDE apps. sudo ought to be reserved for command-line functions. for a fantastic description of why, see:

[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by Buslova on 2007-03-20
Uhhhhh, I decided to try an upgrade to fiesty Herd 5 since I'm on vacation this week and worst comes to worst, I'll have the time to reinstall Edgy.  Well, this is what i got:

sudo: upgrade-manager: command not found

any ideas?



Thanx
-Bus

---

### Post by liveforfunnow on 2007-03-20
> **Buslova said:**
> Uhhhhh, I decided to try an upgrade to fiesty Herd 5 since I'm on vacation this week and worst comes to worst, I'll have the time to reinstall Edgy.  Well, this is what i got:

sudo: upgrade-manager: command not found

any ideas?



Thanx
-Bus

which command did you run? be sure to open a Terminal and enter:

```
gksu "upgrade-manager -c -d"
```

does that give the error?

---

### Post by Buslova on 2007-03-20
that's exactly what i typed...and just copied and pasted it from what you posted just to be sure and got the same error.

---

### Post by liveforfunnow on 2007-03-20
sorry, my limited expertise has come to a halt. does anyone else have any ideas?

---

### Post by Andruk Tatum on 2007-03-20
Are you sure the update-manager is installed (check synaptic).  Should be just called "Update Manager"

---

### Post by liveforfunnow on 2007-03-21
> **Buslova said:**
> that's exactly what i typed...and just copied and pasted it from what you posted just to be sure and got the same error.

i had another thought. try this:

```
sudo apt-get update
sudo apt-get upgrade
gksu "upgrade-manager -c -d"
```

does that fix it?

---

### Post by Buslova on 2007-03-21
Sorry ya'll for taking a bit to get back.
Also, thanx for all the responses.  So it was something weird.  I checked synaptic even tho i knew it should be installed and yep, it showed it was installed.  So i completely removed it and then resinstalled it and low-and-behold, its back.  I guess I should have tried that before posting but I figured if it was marked as installed, it was.  I hadn't run into that before with other packages.  Thanx again! 

-Bus

---

### Post by ermo on 2007-03-21
> **liveforfunnow said:**
> which command did you run? be sure to open a Terminal and enter:

```
gksu "upgrade-manager -c -d"
```

does that give the error?

Just to clarify: Perhaps you (and Steve.K) are confusing 'up***date***-manager' with 'up***grade***-manager'?

```
ermo@ubuntu:~$ which update-manager
/usr/bin/update-manager
ermo@ubuntu:~$ which upgrade-manager
ermo@ubuntu:~$ upgrade-manager
bash: upgrade-manager: command not found

```

This gives the expected result:

```
gksu "update-manager -c -d"
```

Note that [the OFFICIAL sticky regarding upgrading]("http://ubuntuforums.org/showthread.php?t=286599") actually leaves out the '-d' parameter:

```
gksu "update-manager -c"
```
Just my $0.02

 /ermo

---

### Post by liveforfunnow on 2007-03-21
oh crap, my bad. i WAS confusing the two. sorry!

---

### Post by mhenriday on 2007-03-22
> **ermo said:**
> ...

This gives the expected result:

```
gksu "update-manager -c -d"
```

Note that [the OFFICIAL sticky regarding upgrading]("http://ubuntuforums.org/showthread.php?t=286599") actually leaves out the '-d' parameter:

```
gksu "update-manager -c"
```
Just my $0.02

 /ermo

But remember, the official sticky, which is dated 27 October 2006, does not deal with upgrading from** Edgy** to **Feisty**, but rather with upgrading (presumably from **Dapper**) to **Edgy**. Could this be the reason for the extra element «-d» in the terminal command mentioned above ?...

Henri

---

### Post by liveforfunnow on 2007-03-22
> Could this be the reason for the extra element «-d» in the terminal command mentioned above ?...

Henri


yep. -d means "look for development releases."

---

### Post by mhenriday on 2007-03-23
> **liveforfunnow said:**
> yep. -d means "look for development releases."

With the release today of the beta version of **Feisty**, I thought all my problems were solved. Just follow the instructions posted on the [Feisty Upgrades]("https://help.ubuntu.com/community/FeistyUpgrades") page and all would be well ! Interestingly enough, all one was asked to do was to write
[INDENT]update-manager -d[/INDENT]
(no «gksu», no «-c») in a terminal and follow the instructions, and that **Feisty Fawn** would soon be gambolling on one's computer.

Alas, not so ! The first 117 files of 120 to be downloaded went like a dance on roses (save for a little stickiness at file 112), but files 118, 119, and 120 refused to download, and in the end I received the following message :
[INDENT]Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/Release.gpg](http://packages.freecontrib.org/plf/dists/edgy/Release.gpg) Kunde inte ansluta till packages.freecontrib.org:80 (88.191.33.6), tog för lång tid [Could not connect to packages..., too much time elapsed]
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-sv_SE.bz2](http://packages.freecontrib.org/plf/dists/edgy/free/i18n/Translation-sv_SE.bz2) Kunde inte ansluta till packages.freecontrib.org:80 (88.191.33.6), tog för lång tid
Failed to fetch [http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-sv_SE.bz2](http://packages.freecontrib.org/plf/dists/edgy/non-free/i18n/Translation-sv_SE.bz2) Kunde inte ansluta till packages.freecontrib.org:80 (88.191.33.6), tog för lång tid[/INDENT]

The second and third files above deal with the Swedish language and are perhaps not essential for running **Feisty**, but my inability to connect to «[http://packages.freecontrib.org/plf/dists/edgy/Release.gpg»](http://packages.freecontrib.org/plf/dists/edgy/Release.gpg») sounds more worrying. Anything I can do, aside from sitting tight and hoping that these file problems will be corrected in a few days ? I've been having severe stability problems in **Edgy** these last weeks, with inadvertent and undesired log outs, in particular when trying to close tabs in **Firefox**, and I was very much looking forward to upgrading to **Feisty** in the hope that there these problems would have been resolved....

Henri

---

### Post by mhenriday on 2007-03-27
The problem I described above originated in the fact that the address [http://packages.freecontrib.org]("http://packages.freecontrib.org") couldn't be reached, so when it was removed from my list of software sources, I found I could download the remaining 117 files without difficulty. Alas, after they had been installed and  my computer cleaned of surplus files and re-booted - a process which took several hours - instead of seeing a bright new **Feisty** desktop, I was confronted by the following message on my console :
[INDENT]Alert ! /dev/disk/by-uuid/93f7bf32-02f0-437d-aebb-296a48d/db9d does not exist. Dropping to a shell!

BusyBox v.1.1.3 CDebian1.1.1.3-3ubuntu3) Built in shell (ash) Enter 'help' for a list of commands.
/bin/sh: can't access tty; job control turned off
(initramfs):[/INDENT]
Writing «help», I looked through the list of available commands, but found nothing there to resolve my problem. Re-booting the computer, I asked **GRUB** to re-boot to the 2.20 kernel in recovery mode, but to no avail. I then tried to re-boot to «Ubuntu, kernel 2.6.17-11-386», which I hoped would bring me back to **Edgy**, but instead received the following error message :
[INDENT]VFS: unable to mount root fs on [   191.297921] Kernel panic - not syncing: unknown - block (0,0) [   191.297983][/INDENT]
I tried again to re-boot from the recovery mode for the 2.6.17 kernel,  with no success. In the end I was constrained to go back to my **Dapper** live CD, install **Dapper**, and then upgrade to **Edgy** in order to get my computer to function again !...

The question is whether I should report this experience to [Malone]("https://help.ubuntu.com/community/ReportingBugs") as a bug, or whether it should rather be regarded as an idiosyncratic event determined by the configuration of my computer and of no interest to anyone save myself. Here it should be mentioned that I attempted the download a couple of times, using the «update-manager -d» command, every time with the result reported above. Thus this error/bug is certainly reproducible....

I'm still determined to upgrade to **Feisty**, and am therefore grateful for any suggestions other **Ubuntu** devotees might have in this regard....

Henri

---

### Post by Malac on 2007-03-28
> **mhenriday said:**
> The problem I described above originated in the fact that the address [http://packages.freecontrib.org](http://packages.freecontrib.org) couldn't be reached, so when it was removed from my list of software sources, I found I could download the remaining 117 files without difficulty. Alas, after they had been installed and  my computer cleaned of surplus files and re-booted - a process which took several hours - instead of seeing a bright new **Feisty** desktop, I was confronted by the following message on my console :[INDENT]Alert ! /dev/disk/by-uuid/93f7bf32-02f0-437d-aebb-296a48d/db9d does not exist. Dropping to a shell!

BusyBox v.1.1.3 CDebian1.1.1.3-3ubuntu3) Built in shell (ask) Enter 'help' for a list of commands.
/bin/sh: can't access tty; job control turned off
(initramfs):[/INDENT]Writing «help», I looked through the list of available commands, but found nothing there to resolve my problem. Re-booting the computer, I asked **GRUB** to re-boot to the 2.20 kernel in security mode, but to no avail. I then tried to re-boot to «Ubuntu, kernel 2.6.17-11-386», which I hoped would bring me back to **Edgy**, but instead received the following error message :[INDENT]VFS: unable to mount root fs on [   191.297921] Kernel panic - not syncing: unknown - block (0,0) [   191.297983][/INDENT]I tried again to re-boot from the security mode for the 2.6.17 kernel,  with no success. In the end I was constrained to go back to my **Dapper** live CD, install **Dapper**, and then upgrade to **Edgy** in order to get my computer to function again !...

The question is whether I should report this experience to [Malone]("https://help.ubuntu.com/community/ReportingBugs") as a bug, or whether it should rather be regarded as an idiosyncratic event determined by the configuration of my computer and of no interest to anyone save myself. Here it should be mentioned that I attempted the download a couple of times, using the «update-manager -d» command, every time with the result reported above. Thus this error/bug is certainly reproducible....

I'm still determined to upgrade to **Feisty**, and am therefore grateful for any suggestions other **Ubuntu** devotees might have in this regard....

Henri
Feisty has numerous problems at the moment with UUID's being generated incorrectly and/or saved incorrectly. There are several threads on this forum about it and even more bugs on launchpad concerning UUID's.
A fix for the above not found and resultant errors would be to replace the UUID's with good old /dev/hd-- notation on the boot line "root=/dev/hd--" and in /etc/fstab.
This is further complicated by the fact that from kernel 2.6.20-9 to 2.6.20-11 it's /dev/hd-- but then from kernel 2.6.20-12 it has changed for some reason to /dev/**s**d-- notation even though previously hd was correct????????????

Although this too is a little complex

---

### Post by mhenriday on 2007-04-01
> **Malac said:**
> Feisty has numerous problems at the moment with UUID's being generated incorrectly and/or saved incorrectly. ...

Anybody know how far the developers have come in resolving these problems ? Dare one risk a new attempt at upgrading to **Feisty** now, or should one take the path of prudence, and wait for the release scheduled 19 April ?...

Henri

---

### Post by viper on 2007-04-01
> **mhenriday said:**
> Anybody know how far the developers have come in resolving these problems ? Dare one risk a new attempt at upgrading to **Feisty** now, or should one take the path of prudence, and wait for the release scheduled 19 April ?...

Henri

Me thinks this time i might just hang out for the 19th and do a complete fresh install,

---

### Post by Grafster on 2007-04-02
At least a few people are having semi-serious (i.e. unrecoverable) errors related to Kernel Panics and other nasty stuff.

It doesn't appear to be widespread, but it might be a good idea to hold off unless you really need to upgrade now.

---

### Post by miggols99 on 2007-04-02
Oops sorry please delete this post. I didn't read the others...

---

### Post by mhenriday on 2007-04-02
> **viper said:**
> Me thinks this time i might just hang out for the 19th and do a complete fresh install,

Do you mean a fresh install from a live CD, rather than an upgrade from **Edgy** ?...

Henri

---

### Post by RxRated on 2007-04-02
I have been trying to do an update to Feisty, but keep getting an error message "could not initiate dbus".  Does this mean the server is not available, or am I doing something wrong?

---

