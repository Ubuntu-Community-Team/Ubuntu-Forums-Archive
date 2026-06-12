---
title: "update manager: freezes at file 30 of 48"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by dogscoff on 2008-02-27
hi,

Just got a brand shiny new Anubis laptop from [http://efficientpc.co.uk](http://efficientpc.co.uk), which came with gusty64 pre-installed. 

First thing after switching it on and pointing it to my internet connection was to run the update manager and see if it needed any updates downloaded. It said "you are up to date" but it didn't really look to me like it had checked, so i click the "check" button, just to be sure. It then starts downloading the update list, but freezes on file 30 of 48. It will sit there for ages, going no further. If I look at the detailled file view it shows that some files are "hit", some are "failed" and others are "done". There doesn't seem to be a pattern to which URLs/ servers that fail or pass. 

I've tried apt-get clean and variations thereof and that made no difference. I've treid changing it to a different mirror but it wasn't very clear whether I'd succeeded or not (I think it's now pointing at the UK server) but it still does the same thing. Rebooting the machine doesn't help either. 

Internet connection is fine and running at a decent speed, and the package manager/ add&remove seems to be OK (I've downloaded lincity, thunderbird other packages via them fine) but it's just the update checker that seems to be broken.  This seems to get called if I try to download a flash plugin from firefox, that gets stuck too. I haven't tried getting the plugin from the package manager yet though, maybe I should do that. 

I don't think it can be an ISP issue because my wife's Feisty machine and my old Xubuntu gutsy laptop both update fine on the same connection.

Has anyone else seen this wierd behaviour? How do I go back and tell it to try again on thoise files that say "failed"? Can anyone help?

---

### Post by dogscoff on 2008-02-27
OK, more info.
When adding the medibuntu repository from the command line and then refreshing the package list with the comand 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 it froze at 99% (looking up IP address 192.168.0.10) and then times out. It looks as though an awful lot of the repositories are claiming to be at this IP. 
Is it me or does this IP looklike it ought to be on my local network? COuld it be the PC manufacturer redirected the repositories to a machine on his own network for building PCs and forgot to put it back before shipping the laptop? What should I reset these IPs to and how do I do so?

WHen I click "check" now I get the message 
"E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory"

Also,and this may be unrelated but I'll mention it anyway: I had a wierd white outline of a rectangle appearing in the middle of my screen (like the border of a splash screen) whenever synaptec wais launched. disabling and re-enabling desktop effects got rid of it.

---

### Post by zvacet on 2008-02-27
**system<admin<software sources**>check all boxes under Ubuntu software and under updates tab.Reload.Go to the update manager and try again.

---

### Post by dogscoff on 2008-02-27
I got the wierd rectangle thing again. Now it gets stuck on file 88 of 105 =-/

---

### Post by dogscoff on 2008-02-27
Hmmm, it's still stuck on 88, but the orange update icon has appeared and pointed me to 30 odd megs worth of updates. Maybe on eof those will help? I'll install them and see.

---

### Post by dogscoff on 2008-02-27
installed the updates, it still gets stuck on 88 of 105 when i click "check"

---

### Post by Partyboi2 on 2008-02-27
You mentioned that you changed the server to uk, what happens when you change it to the main server?

---

### Post by dogscoff on 2008-02-28
Doesn't seem to be any difference whatever server I go to. Would it help if I posted the file that contains all the servers? Which file is that?

---

### Post by dogscoff on 2008-02-28
The PC supplier has come up with a solution. For anyone else who experiences somehting similar, here is the URL:

[https://answers.launchpad.net/efficientpc/+question/25786](https://answers.launchpad.net/efficientpc/+question/25786)

Note I'm away from the PC in question at the moment, but I will report back here later when I've had a chance to try this out.

---

### Post by dogscoff on 2008-02-29
Problem solved. I had some bad entries in the file /etc/apt/sources.list

My list is now fine and looks like this:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) gutsy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse universe main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse universe main restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted #Added by software-properties
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted #Added by software-properties

Thanks for the advice =-)

---

