---
title: "dpkg error"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by shojo on 2005-10-15
Hi all-

upgrading to Breezy, i had a power outage (ouch).  Continued the download through apt-get once power restored.  Rebooted and now I have a few problems. (intel centrino, dell inspiron 600m, ATI card)

1)  Gnome doesn't work.  I tried apt-get update and dpkg-reconfigure xserver-xorg.  Comes back saying xserver-xorg is broken or not fully installed.

2) Tried "apt-get -f install" come up to the Y/n prompt and get an error message:  
[B]dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-ubuntu8_i386.deb (--unpack):
   Trying to overwrite 'usr/share/libofx/dtd/opensp.dcl'\dpkg-deb: subprocess paste killed by signal (Broken pipe)

E: Sub-process /usr/bin/dpkg returned error code (1)[/B]

What are my possible steps?

Thanks

---

### Post by shojo on 2005-10-15
Add to that:

I tried 

1)apt-get clean

2) Apt-get -f dist-upgrade
    apt downloaded a few programs

3)Result: Errors encountered processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb

How can a move on if i can't fix broken packages?  What is the reason for this error message?:confused: 
Is my question too specific or not specific enough to get a reply?

---

### Post by shojo on 2005-10-16
well, **** it.  Out of the whopping 43 people who looked at this post, No one helped.  Sure I could have been patient.  Sure if I had six weeks to figure out a problem then it would have gone better.  But I'm not a geek.  I linux for the politics.  I think that's what this distro is going for, no?  

Clean reboot.  Wipe the slate.  What i miss about Debian was the expertise of its user base.  Is that lacking with Ubuntu?

Breezy is so far, so good, from the CD.  But if I have to go through this shit again in six months, i'm out.  

If you post now, after my problem has been solved, you suck.

---

### Post by kperkins on 2005-10-16
Try :
apt-get clean
atp-get update
apt-get dist-upgrade

---

### Post by shojo on 2005-10-16
Thank you for your advice.

In deference to anyone having the same problem, I tried exactly that.  It did not work.

The error message was one that is similar to that if you've ever downloaded the packages into a /var partition and the partition was too small.  I took the steps you prescribed, but all that did was put me in the position to download packages that were essentially broken or incomplete.  Resulting in the same erroor.

I'm not complaining about the problem.  I'm complaining about the community that doesn't have the know-how to walk people through problems.  Ubuntu is easier than most Linux distros, ergo less sophisticated communities.  No?

what are the rates of success with an apt-get upgrade, I wonder?

---

### Post by kperkins on 2005-10-17
have you tried:
dpkg -r libofx2 (and any other one you're having trouble with)
then apt-get update, etc.? (I suppose upgrade wouldn't work if you removed the, already, installed package, but obviously you can install the new one since you shouldn'thave to do a dist-upgrade for a few packages.)
There really shouldn't be any packages broken by an interrupted download, since partial packages are kept in a separate folder than completed downloads.
Also you might try running: 
dpkg -i force-overwrite /var/cache/apt/archives/libofx2*.deb

---

### Post by kperkins on 2005-10-17
[QUOTE=shojo]Thank you for your advice.

In deference to anyone having the same problem, I tried exactly that.  It did not work.

The error message was one that is similar to that if you've ever downloaded the packages into a /var partition and the partition was too small.  I took the steps you prescribed, but all that did was put me in the position to download packages that were essentially broken or incomplete.  Resulting in the same erroor.

I'm not complaining about the problem.  I'm complaining about the community that doesn't have the know-how to walk people through problems.  Ubuntu is easier than most Linux distros, ergo less sophisticated communities.  No?

what are the rates of success with an apt-get upgrade, I wonder?[/QUOTE]

And probably instead of bitching that nobody helped you after a 1 day on a very strange problem, that doesn't happen that often, you might have tried a google on your error message. (If I had read the whole of your 3rd post I never would have even bothered trying to help you.)
For the record--I've never had a problem with an apt-get upgrade/dist-upgrade (on my debian machine), and none doing the same with Synaptic on Ubuntu.  Shit happens, don't piss at the community for something that's not their fault (your power outage), if you hada power out trying to upgrade Windows, you'd have even more problems.

---

### Post by 11hjpphty76lkjj on 2005-10-17
You can try "sudo apt-get install ubuntu-desktop"  that will fix your desktop if it's missing files, etc.  In theory.  Honestly whenever I do an install I always do expert, then install the base, and then install ubuntu-desktop after the base system is setup.  Then I'm always getting the newest files from the repos.  But that's just my own way.

Aaron

---

### Post by dickohead on 2005-10-19
if you remove gnucash and gnucash-common before trying an apt-get dist-upgrade fisrt you may have more succes, if you also bothered to find out what lobofx2 is, you would have realised what it's for and found a bug report with the solution above.

---

### Post by skirov on 2005-11-23
Remove the conflicting package with dpkg -r kmymoney2 (for example).
Then apt-get -f install and your X should be up.
Now try to install whatever needs liboxf2.
Hope this helps

---

### Post by RickKnight on 2005-12-03
[QUOTE=kperkins]have you tried:
dpkg -r libofx2 (and any other one you're having trouble with)
then apt-get update, etc.? (I suppose upgrade wouldn't work if you removed the, already, installed package, but obviously you can install the new one since you shouldn'thave to do a dist-upgrade for a few packages.)
There really shouldn't be any packages broken by an interrupted download, since partial packages are kept in a separate folder than completed downloads.
Also you might try running: 
dpkg -i force-overwrite /var/cache/apt/archives/libofx2*.deb[/QUOTE]

Thanks kperkins, this helped me solve my upgrade problems. Glvc would not over write gtk-vlc. I removed gtk-vlc manually and also the old version of gvlc, ran 'sudo apt-get -f dist-upgrade and got back on track.

Thanks again for your postings.

Rick Knight

---

