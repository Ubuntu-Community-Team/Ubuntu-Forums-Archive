---
title: "Thunderbird - can't get at old, V2 folders from Tbird 3.1"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by 2912pwil on 2011-06-17
Greetings:

Recently moved to 11.04, Natty (fresh install), all seems OK, Libre Office usable etc...

Had been on 9.10 so was out-of-maintenance, been using Thunderbird for years, migrated from OutlookExpress.  I used to keep TBird folders (with years of emails for business etc..) on a separate DATA disk (partitioned system, Windows, Ubuntu, Data).  

I've got Thunderbird 3.1 running, can read & write emails etc.. but I've been very very unsuccessful in seeing/getting access to the old folders.

I've read through the Thunderbird 3 Gmail help..
[http://mail.google.com/support/bin/answer.py?answer=180189](http://mail.google.com/support/bin/answer.py?answer=180189)
and played around (hours) with account setting, folders etc ..

Can anyone kindly point me to a guide for how to do this or are the TBird 2 folders not usable from 3.1?? Any hints & tips gratefully received...

Alternatively, any way of running "Old" Thunderbird on 11.04 Natty please??

Cheers!

2912pwil

---

### Post by SeijiSensei on 2011-06-17
> **2912pwil said:**
> Alternatively, any way of running "Old" Thunderbird on 11.04 Natty please??

You can download the Linux binary for 2.0.0.9 from here:
[ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/](ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.9/linux-i686/)

Choose your language, then download the tar.gz file to the top of your home directory.  In a terminal run the following:

```

cd ~
mv .thunderbird .thunderbird3
mkdir .thunderbird2
ln -s .thunderbird2 .thunderbird
tar xzvf thunderbird-2.0.0.9.tar.gz
thunderbird/thunderbird &

```

This will start you with a fresh configuration so the old TBird doesn't mess up your current settings.  When you're ready to return to TBird3, just do:

```

cd ~
rm .thunderbird
ln -s .thunderbird3 .thunderbird

```

and run TBird3 from the menus as you normally do.

There's probably ways to configure two menu entries that use the different binaries with their associated .thunderbird files.  If you intend to keep both versions around, you might look into that.

---

### Post by amanchesterman on 2011-06-17
I haven't faced this exact same issue, but I have migrated all my Thunderbird mail folders from a Windows laptop to this Ubuntu one, and I think the issues are probably similar. There is no suggestion on the Mozilla site that Thunderbird 3 'can't read' Thunderbird 2 mail folders, on the contrary the transition is supposed to be seamless.

The key (from what I have read and from my own experience) is not to try to save individual mail folders or copy them one-by-one. Instead, you
a) have all your Thunderbird 2 emails, settings, addresses etc. saved within a single 'profile' folder (Thunderbird creates this by default);
b) install Thunderbird 3, which automatically creates a new blank profile folder;
c) replace the new blank profile folder with the old Thunderbird 2 profile folder (with all its contents).

I found clear instructions on how to do this on the Thunderbird site, just search for 'profile'.

Alternatively, there is a way to run Thunderbird with more than one profile, so you could access all your old emails in one profile and continue your new correspondence in another: you can switch between them when you want. (A bit like different 'identities' in some other email clients.) Again, instructions for this are on the Thunderbird site.

Good wishes
John

---

### Post by oldfred on 2011-06-17
When I started with Ubuntu we had all the emails & Firefox settings in XP. My wife would always want to do something with email or web and I had to reboot to get into mail or web with correct settings. I then found I could put both profiles into a shared NTFS partition and did not have to reboot. Cut way down on dual booting into XP. I have migrated from TB2 to 3 and many versions of Firebird without issue. I also copy entire profiles from desktop to portable when we travel.

I think with TB3 they moved location of profile slightly. New version copies it.

Update to tb3
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by colin.p on 2011-06-18
Actually it's quite simple. All I did was copy my "mail" folder from the old TB and copy the folder into my new TB "default" folder. I removed the redundant stuff and put the stuff from my POP accounts into a "local folder". I have all my saved emails from 1999. I use gmail and my account is imap, so anything new, I copy into the "local folder" and since I regularly use lucky backup, I have all my TB mail backed up to that.
I still have my original invoice for winzip from 1999, of all things.

---

### Post by 2912pwil on 2011-06-19
Thanks all of you for your advice & pointers, especially Colin.P.  Running with old folders on V3 thanks!! Yippee!!


Ah, winzip: Yup, I musta bought a licence sometime also.,. Sad end to the guy behind PKZIP etc...


Thanks again.. Ain't Ubuntu (& other..) forums wonderful!!

---

