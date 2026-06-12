---
title: "Is it worth doing a clean install of 12.04?"
date: 2012-04-25
forum: Installation &amp; Upgrades
---

### Post by JazzPotato on 2012-04-25
Hi forum,
Just wondering if there were any disadvantages to the "upgrade" feature in ubuntu. As 12.04 comes out tomorrow and I plan to have it as my OS for the next couple of years, I wondered if it would be more stable, etc.. if I did a clean install rather than using the upgrade feature. I upgraded my 11.10 from natty with no major problems.
Live long and prosper

---

### Post by garvinrick4 on 2012-04-25
I choose to do a fresh install at all possible times. Everyone has their preference but clean seems to always
be better than 1000 packages upgraded. If you always have a /home in own partition and a maybe 10 gig size for the / it is just so much easier to not mess with /home everytime you want to do a fresh install.

---

### Post by JazzPotato on 2012-04-25
Ok thx. Being as i plan to keep this as my distro for the rest of the LTS cycle it's probably a good idea.

---

### Post by jadtech on 2012-04-25
I have an upgrade and its fine it is 12.04 the same as any fresh install though I know many who say a clean install if you have nothing to lose is better ..

the upgrade is in ways a bit more challenging I learned a lot about ubuntu through going that way ...

there is no differences in the install weather you install clean or you update its still the same million updates and patches the difference for all using the beta is more like watching the picture Image develop over time :)

---

### Post by collisionystm on 2012-04-25
I have always done a clean install because it makes me feel like I am doing spring cleaning and having a fresh start.

Although I went really fresh this time and I am using Fedora 17 ;).

---

### Post by rg4w on 2012-04-25
> **collisionystm said:**
> I have always done a clean install because it makes me feel like I am doing spring cleaning and having a fresh start.
Same here.

A few years ago I took the time to make a separate partition for Home, and now doing clean installs is a breeze.

---

### Post by techsupport on 2012-04-25
> **rg4w said:**
> Same here.

A few years ago I took the time to make a separate partition for Home, and now doing clean installs is a breeze.

Fresh installs are my recommendation as well, something like this:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

:guitar:

---

### Post by TBABill on 2012-04-25
One nice reason for a fresh install is time. Upgrades take far longer than a fresh install and it's pretty easy to copy your files to a USB drive, then copy them back to the fresh install. Literally a savings of hours of time for the machine to run an upgrade versus fresh install. Either way, have a copy you can install in case the upgrade borks...just my recommendation.

---

### Post by fbicknel on 2012-04-25
Agree with everyone here.  The reasons already stated are all excellent.  I also learn something new with each install.

---

### Post by techsupport on 2012-04-25
> **TBABill said:**
> One nice reason for a fresh install is time. Upgrades take far longer than a fresh install and it's pretty easy to copy your files to a USB drive, then copy them back to the fresh install. Literally a savings of hours of time for the machine to run an upgrade versus fresh install. Either way, have a copy you can install in case the upgrade borks...just my recommendation.

Then after you get everything installed on your freshly installed Ubuntu OS use Remastersys to take a snapshot of that, and migrate it to a USB Flash Thumb Drive to use as a resque live stick to reinstall if needed.

Here is how to install Remastersys in Ubuntu 12.04:

[http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/](http://debianhelp.wordpress.com/2012/04/20/how-to-install-and-use-remastersys-in-ubuntu-os/)

I use it daily to do freshly fully pre-loaded installs of 12.04. 

I'm surprised more users don't try it. A reinstall only takes 20 minutes when you use Remastersys, and that includes codecs, plugins, everything you added to your custom system.

:guitar:

---

### Post by More or Less on 2012-04-25
As a long time Windows user, I often found that reinstalling a program after reformatting or even reinstalling Windows presented me with a different program even though I had updated that program.  The updates were just that, not a reflection of the overall "growth" of the program.

I am not sure how Linux handles this, but my approach with Windows is to simply wait a few months after a major release (bugs need to get worked out), then I completely start new.  During that time, I make backups of anything I need and clean out the computer.

---

### Post by tomdkat on 2012-04-26
> **More or Less said:**
> I am not sure how Linux handles this, but my approach with Windows is to simply wait a few months after a major release (bugs need to get worked out), then I completely start new.  During that time, I make backups of anything I need and clean out the computer.
So, when a new version of Windows would come out, you would wait a few months then get the new version and do a fresh install of that instead of upgrade?

I frequently read recommendations here for doing fresh installs of new Ubuntu releases instead of doing upgrades.  This tells me Ubuntu isn't necessarily or particularly "upgrade friendly" even though doing upgrades can and does work.

In the Windows world, I've encountered more instances of people doing upgrades of Windows rather than fresh installs of Windows (unless they get a new machine with the new version pre-installed).  I wonder why this is... possibly because of the cost involved of a non-upgrade version of Windows vs an upgrade version?

Peace...

---

### Post by Kaput1982 on 2012-04-26
I would also recommend doing clean installs where possible.

---

### Post by tb75252 on 2012-04-26
> **Kaput1982 said:**
> I would also recommend doing clean installs where possible.
But if you do a clean install, would the process not overwrite your /home partition and thus lose all the data in it?

---

### Post by Kaput1982 on 2012-04-26
Yes, a clean install will over write your home partition (unless it is installed separately ).  I normaly just back mine up on an external harddrive and then transfer back the stuff I need.

---

### Post by tb75252 on 2012-04-26
> **Kaput1982 said:**
> Yes, a clean install will over write your home partition (unless it is installed separately ).  I normaly just back mine up on an external harddrive and then transfer back the stuff I need.
When you back up your /home directory, do you just do a copy/paste with Nautilus (from the computer HD to the external HD), or is the process more complex than that?

---

### Post by mashedbear on 2012-05-03
> **garvinrick4 said:**
> I choose to do a fresh install at all possible times. Everyone has their preference but clean seems to always
be better than 1000 packages upgraded. If you always have a /home in own partition and a maybe 10 gig size for the / it is just so much easier to not mess with /home everytime you want to do a fresh install.

Hi - on /dev/sda (an SSD) I have a / and /home partion; as well as a swap. on /dev/sdb (an hdd) I have a /mnt/data where all the data is. Using the CD how can i do a clean install of / on /dev/sda? Is there a good guide documentation for this scenario somewhere? Thanks

---

### Post by C.S.Cameron on 2012-05-03
For the last five years I have only done an upgrade of the LTS releases on each of my wife and kid's computers, never a problem.
I used to do an upgrade on both my laptop and work station every release, but now I only upgrade the LTS's as well.
Of course I do a fresh install to Vbox every release.

---

### Post by Ubu_Fester on 2012-05-21
What about more specialized versions:  such as mythbuntu or mythtv.  I've had to tweak some things in previous versions to get hardware drivers working (e.g., digital tuners).  Would a clean install still be recommended?

---

### Post by wilee-nilee on 2012-05-21
> **Ubu_Fester said:**
> What about more specialized versions:  such as mythbuntu or mythtv.  I've had to tweak some things in previous versions to get hardware drivers working (e.g., digital tuners).  Would a clean install still be recommended?

All of us tweak the OS, and you will probably find the most experienced users advising a fresh install.

You can save a list of your installed packages and the sources.list and the sources.list.d and check if the PPA's still support your release (new install) in the .d version the latter. 

Have a separate home I don't personally I keep my stuff on a external set of HD's

The experienced users as well I would speculate remember by and large what they install in general as well. Also have backups of home and possibly clones/images of the OS's, I have both.

---

### Post by Ubu_Fester on 2012-09-26
What do you use to clone/image the OS???

---

### Post by ezsit on 2012-09-27
I use remastersys to create a distributable live dvd of my installed system and keep data backed up on external hard drives. 

I never mix data backups with system backups and just copy back the data from the external hard drives when necessary. 

I also have my /home on its own partition and can just as easily install a fresh OS installation and preserve my /home.

---

### Post by Ubu_Fester on 2012-10-05
FWIW, I've spent two nights this week trying to get remastersys to create an iso of my system.  I used the manual installation procedure and believe I installed it correctly.  I am excluding my media folders (for mythtv).  But it errors out at the end of 1-2 hour compilation process.  

I still have no iso image of my system, and now I can't even login to my system.  Something broke, see thread:  
[http://ubuntuforums.org/showthread.php?p=12279045#post12279045](http://ubuntuforums.org/showthread.php?p=12279045#post12279045)

Is this REALLY the best free software out there that will create an image of my OS?

:confused:

---

