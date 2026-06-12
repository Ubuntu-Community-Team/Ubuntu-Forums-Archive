---
title: "Tons of errors upgrading from 8.04 to 10.04 LTS"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by shane.gardner on 2010-05-12
I upgraded to 8.04 on AMD64 machine.  I started to upgrade to 10.04 LTS using the System -> Admin -> Update manager.  After packages started installing began getting MANY error popup windows saying dpkg exiting with errors.  Looking at the terminal window I see a lot of "cannot utime" and it appears to be some error with tar.  I saw on another forum that Lucid has a bug with tar.  Now the distribution upgrade has just locked.  What should I do?

---

### Post by zvacet on 2010-05-13
```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by shane.gardner on 2010-05-13
Thanks...  the configure seemed to work, but install failed:

"Processing halted because there were too many errors."

Looking back on the errors here is the problem:

"tar: 'file name': Cannot utime: Bad file descriptor"

At the end it gives a long list of all the .deb files in /var/cache/apt/archives that failed.

Do you think I need to upgrade tar to a newer/older version?  If so, what version is required with 10.04 LTS?  This is depressing.

---

### Post by infamous-online on 2010-05-13
I know many people hate to hear this, but why not backup your critical stuff and do a clean install?

---

### Post by shane.gardner on 2010-05-13
Yeah that is becoming an option.  It' been so long.  I am pretty sure all my data is on a separate partition.  I should have never upgraded in the first place.

---

### Post by shane.gardner on 2010-05-13
Could I try to rebuild/upgrade/downgrade tar to whatever is required for 10.04????  

tar --version:  tar (GNU tar) 1.22

Is this the correct version for 10.04?

---

### Post by GEZEN Foundation on 2010-05-13
Hi, 

we've been using Ubuntu since version 6 at GEZEN. A lot of improvements were noticable up to 8.04. 

Then we went to 9.01 which took away our options to use our scanner (HP4200 on Xsane). After trying to fix it manually for a while, we got another one (Mustek 1200UB plus) which we were able to use with the aid of someone who wrote a script that ran from an icon on the desktop. 

After installing 9.04 that option was f#!-ed up too, as was our soundconfiguration for use with Skype. I de-installed Xsane, SANE and libsane and reinstalled them fresh: result was nothing. 

After fiddling around for it for some hours, we installed 10.04 - hoping everything would get back to life again. Alas, no solutions there either.

I got another used scanner (They're really starting to pile up here now) that was officially suported but wasn't seen by Xsane as well (including fresh re-installs ofcourse). So we bought 3rd-party software Vuescan that worked instantly. (Yeah, thumbs up for the Vuescan-people! )

Audio for the USB-headset was reconfigured (way too many options in too many menus in my opinion, and without proper ID-spec of the respective hardware; what's up with that??? ) I only got the mic and main-speakers working but the headphones went out-of-order. :( It was either that, or no sound at all :confused:

Also Thunderbird can't send e-mails through our ISP's mailserver anymore, so we switched to an external provider.

It has gotten to the point where we say: " NO more updates !!!"

Our organisation moved to Ubuntu because it seemed much more dependable than the big-bad-woolf's. But that time seems to be over now. :(

I porpose an update-solution that can 100% downgrade specific parts of your system to the last working system-setup. (which  you were able to mark as such)
I mean a button/icon "downgrade" next to the upgrade on the top-right the calls up a menu where your last working setup is presented in RED CAPITALS and non-working ones presented in small caps and a confirmation-button that says: "TAKE ME BACK!!!". :guitar:

Many thanks in advance to the programmers that will provide such a solution. We don't mind paying a fair sum for it either if it's has been proven to function properly. :guitar:

I also propose that in the current update-manager individual updates will be marked as tested, supplied with links to respective page where succecfully tested configuration were reported by their users. With such a set-up, one can be more confident wether an update will bring solutions or present possible malfunctions.
In combination with this, users should be encouraged to fill out forms of their full working setup, e.g. once a month after installs & updating. :guitar:

Sincerely,

Steven

PS: We are starting to wonder if one of the big boys has infiltrated the Ubuntu programmers' community by paying them for writing defects into our systems to speed down the rise of Linux as alternative to their OS-es.

---

