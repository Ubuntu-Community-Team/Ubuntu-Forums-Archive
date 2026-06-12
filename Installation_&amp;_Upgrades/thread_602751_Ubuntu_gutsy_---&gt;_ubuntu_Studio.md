---
title: "Ubuntu gutsy ---&gt; ubuntu Studio"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by serfcx on 2007-11-04
Hi planning to install Ubuntu Studio over Gutsy by using the packages as outlined here

[http://ubuntuforums.org/showpost.php?p=3639492&postcount=7](http://ubuntuforums.org/showpost.php?p=3639492&postcount=7)

When command is run results in following output - just the end bit 

The following packages will be REMOVED:
  ubuntu-sounds 
0 packages upgraded, 307 newly installed, 1 to remove and 0 not upgraded.
Need to get 405MB/602MB of archives. After unpacking 1441MB will be used.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ubuntu-sounds but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Downgrade the following packages:
gdm [2.20.1-0ubuntu1 (gutsy-proposed, now) -> 2.20.0-0ubuntu6 (gutsy)]

Leave the following dependencies unresolved:
gdm recommends ubuntu-sounds
Score is -51

Accept this solution? [Y/n/q/?]

I guess the score is a measure of how certain the path will be successful 

Anyone had success in this method ?

---

### Post by Drunky on 2007-11-04
The option that you have shown does not include the real-time kernel.  You probably will want the real-time kernel.

I used the Ubuntu Help wiki for [Upgrade from Ubuntu Gusty to Ubuntu Studio]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29").

Try this:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by Luxx on 2007-11-04
I have come across numerous suggestions about how to transform Ubuntu 7.04 or 7.10 to Ubuntu Studio 7.04 or 7.10 and haven't found anything that works.

First off,  most of them are carbon-copied oversimplified posts without a complete APT for the repositories and most of them don't advise to add the repositories at all. After a few go-rounds that's a little detail that's easy to forget.  Second, I have been at this for 3 days now, practically straight through, trying to figure out what has happened to the apparently most common source: 

[http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) (please note the complete lack of location or components, because after DAYS of searching and trying different possibilities I still have not found it and therefore have NO CLUE). The wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O-  | sudo apt-key add - thing only resulted in the message "gpg: no valid OpenPGP data found." whether form this source or the scarce others I found.

It doesn't appear to exist at all, and neither do the other repositories suggested. Every attempt I have made to apt-get or aptitude install ubuntustudio-desktop, ubuntustudio-audio, ubuntustudio-audio-plugins, or ubuntustudio-default-settings has been fruitless. Likewise web link searches.

Unfortunately I don't have accesss to a DVD burner anywhere near high speed internet so I can't simply download the ISO. 

Have things been moved or renamed? Is there a working mirror? I feel like I must be missing something.........besides Studio.

---

### Post by serfcx on 2007-11-05
> **Drunky said:**
> The option that you have shown does not include the real-time kernel.  You probably will want the real-time kernel.

I used the Ubuntu Help wiki for [Upgrade from Ubuntu Gusty to Ubuntu Studio]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29").

Try this:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

I have read in another post somewhere that because gutsy uses a tickless kernel (whatever that is !!!) there is no need for the rt kernel ?

There seems to be confusion everywhere you look.

---

### Post by Drunky on 2007-11-05
> **Luxx said:**
> I have come across numerous suggestions about how to transform Ubuntu 7.04 or 7.10 to Ubuntu Studio 7.04 or 7.10 and haven't found anything that works.

First off,  most of them are carbon-copied oversimplified posts without a complete APT for the repositories and most of them don't advise to add the repositories at all. After a few go-rounds that's a little detail that's easy to forget.  Second, I have been at this for 3 days now, practically straight through, trying to figure out what has happened to the apparently most common source: 

[http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) (please note the complete lack of location or components, because after DAYS of searching and trying different possibilities I still have not found it and therefore have NO CLUE). The wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O-  | sudo apt-key add - thing only resulted in the message "gpg: no valid OpenPGP data found." whether form this source or the scarce others I found.

It doesn't appear to exist at all, and neither do the other repositories suggested. Every attempt I have made to apt-get or aptitude install ubuntustudio-desktop, ubuntustudio-audio, ubuntustudio-audio-plugins, or ubuntustudio-default-settings has been fruitless. Likewise web link searches.

Unfortunately I don't have accesss to a DVD burner anywhere near high speed internet so I can't simply download the ISO. 

Have things been moved or renamed? Is there a working mirror? I feel like I must be missing something.........besides Studio.

Luxx,

A few points.

I too was having trouble with my DVD and I used the link that I posted to upgrade from fresh install of Ubuntu Gusty 7.10 to Ubuntu Studio 7.10.  I did not have any problems what so ever.

Ubuntu Studio 7.10 does not require adding any additional repositories.  Indeed, Ubuntu Studio packages are now included in the default repositories.

You can also verify my apt-get code was complete or not.  Just click the link to the Ubuntu Help wiki page for [UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/?action=fullsearch&context=180&value=studio&titlesearch=Titles").

---

### Post by Drunky on 2007-11-05
> **serfcx said:**
> I have read in another post somewhere that because gutsy uses a tickless kernel (whatever that is !!!) there is no need for the rt kernel ?

There seems to be confusion everywhere you look.

I'm not sure what a 'tickless' kernel might be.

But I believe that if you were to install Ubuntu Studio from a DVD then you find that the real-time kernel would have been installed.

Seeing that it would be installed from the DVD, then I am completely comfortable installing it with the upgrade.  Actually, for this same reason I would be a little concerned if the upgrade didn't include it.


[edit] Just in case people are not completely aware, the real-time kernel is very useful in recording music on a computer.  It help reduce latency, which in musical laymen's terms could be said to be the time difference between when you play music (say on guitar) and when the computer records it or plays it back to you through your speakers.  A larger latency is like a digital delay that really, really is confusing by getting everything out of time.

I hope this helps.

---

### Post by Luxx on 2007-11-06
For some reason I wasn't able to install Studio over Feisty Fawn. Terminal kept saying it couldn't resolve the repositories. What I finally did was upgrade to Gutsy Gibbon and then installed Studio using the following command lines:

Upgrade to Gusty Gibbon:

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade	(these didn't seem to do much of anything. I don't know how neccessary they were)

sudo aptitude install update-manager-core
sudo do-release-upgrade		(this got results, it took 1 hour and 49 minutes with DSL connection for the downloads, then some time for unpacking, etc.) Restart

Then I got Studio:
UbuntuStudio/UpgradingFromGutsy
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29)

sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

Then I changed the theme and login window:
System/Preferences/Appearance (I don't have "Theme" in my menu),
selected UbuntuStudio theme,
System/Administration/Login Window, selected login window.

Success.

Not everything was so smooth though.
I have noticed that there is a slight image problem in Firefox since I did this. Images are overlapped and some of the images don't seem to belong on the webpage at all, or sometimes blocks of black come up and cover part of the webpage I'm viewing.

I also had a dual boot setup with WinXP on the other hard drive and now when I try to access the other drive I get a message that it can't be mounted. I had disconnected the other hard drive while upgrading and then set up the dual boot as I had done it before.

---

### Post by adamgram on 2008-01-02
I am very new to this (first install of linux).  And I'm having trouble upgrading to Ubuntu Studio from Gutsy.  I started with Edgy Eft, which I had a CD for, upgraded to Feisty Fawn and again to Gutsy Gibbons, with the intention of upgrading to Studio from there using the code:

 sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

I keep getting an error message:

E: Couldn't find package ubuntustudio-desktop

and if I delete ubuntustudio-desktop from the list it just moves on to the next on the list and says: 

E: Couldn't find package ubuntustudio-audio

I would think this means I have a more basic problem than the upgrade to studio because it can't find the upgrade to even download it?  I did the other upgrades through the 'update manager' and didn't use terminal, so I have no idea what to check next since I don't know it's a setup problem or a problem with one of the upgrades I made to get to this point.

---

### Post by Partyboi2 on 2008-01-02
> **adamgram said:**
> I am very new to this (first install of linux).  And I'm having trouble upgrading to Ubuntu Studio from Gutsy.  I started with Edgy Eft, which I had a CD for, upgraded to Feisty Fawn and again to Gutsy Gibbons, with the intention of upgrading to Studio from there using the code:

 sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

I keep getting an error message:

E: Couldn't find package ubuntustudio-desktop

and if I delete ubuntustudio-desktop from the list it just moves on to the next on the list and says: 

E: Couldn't find package ubuntustudio-audio

I would think this means I have a more basic problem than the upgrade to studio because it can't find the upgrade to even download it?  I did the other upgrades through the 'update manager' and didn't use terminal, so I have no idea what to check next since I don't know it's a setup problem or a problem with one of the upgrades I made to get to this point.
Make sure you have universe repo enabled under "Software Sources" (System>Admin>Software Sources) On the first tab make sure all have a tick next to them except "Source code" then close "Software Sources" and try installing the packages again.

---

### Post by adamgram on 2008-01-02
> **Partyboi2 said:**
> Make sure you have universe repo enabled under "Software Sources" (System>Admin>Software Sources) On the first tab make sure all have a tick next to them except "Source code" then close "Software Sources" and try installing the packages again.

thanks man!  a pretty crucial piece of info to learn, huh?  haha... plenty more to come, I'm really excited to get into this stuff!

---

