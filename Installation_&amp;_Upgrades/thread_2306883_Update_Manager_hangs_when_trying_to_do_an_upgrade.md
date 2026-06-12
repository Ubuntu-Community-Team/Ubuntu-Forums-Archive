---
title: "Update Manager hangs when trying to do an upgrade"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by pce-accesswave on 2015-12-19
I'm trying to upgrade from 10.04.4 LTS to 12.04 LTS. Following the instructions here:

 [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

I start up the update manager. Before anything appears in the update manager window, I get a modal window on top with the text "Your Ubuntu release is not supported anymore. You will not get any further security fixes or critical updates. Please upgrade to a later version of Ubuntu Linux."

I click the close button in this window and nothing happens - not even any disk activity. If I then click the window close button ("X" in title bar) I get "Metacity is not responding" etc and have to kill the process.

Any suggestions on how I can update my system?

Thanks

Peter

---

### Post by deadflowr on 2015-12-19
I think your sources are out of whack,
but to determine that, you'll need to run
```
sudo apt-get update
``` 
from a terminal and post the results.

---

### Post by Topsiho on 2015-12-20
10.04 is not supported anymore, so can probably  not be upgraded from 10.04 to 12.04.

12.04 is not the newest LTS version, 14.04 is newer, and the upcoming 16.04 will be ... also newer.
As it is (to my opinion) better not to install a version before it is out for some time, I think you'd better install the newest point version 14.04.3 (or is it 14.04.4?), and install that.
You can, if you want to, upgrade that to 16.04, if you don't wait until after April 2019 :)

Topsiho

---

### Post by pce-accesswave on 2015-12-20
I get a couple of dozen lines of the form

> Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid (varies from here on)

followed by

> Reading package lists...

and that's it.  I've attached the complete listing.

---

### Post by pce-accesswave on 2015-12-20
> 10.04 is not supported anymore, so can probably  not be upgraded from 10.04 to 12.04.

12.04 is not the newest LTS version, 14.04 is newer, and the upcoming 16.04 will be ... also newer.
As it is (to my opinion) better not to install a version before it is  out for some time, I think you'd better install the newest point version  14.04.3 (or is it 14.04.4?), and install that.
You can, if you want to, upgrade that to 16.04, if you don't wait until after April 2019 [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Topsiho

Thanks, but I'm following the advice on this page:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

which pretty clearly implies that the path I'm taking is the correct first step to get to the next LTS version.

---

### Post by howefield on 2015-12-20
Here is another link for you :)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Your machine, your choices, were it mine and coming from such a long way back, I'd clean install a current version over the top of the existing, not marking the destination will keep your /home folder intact. In any event, whatever you do, hope you have second copies of any important files.

---

### Post by pce-accesswave on 2015-12-20
> I'd clean install a current version over the top of the existing

That seems pretty drastic (i.e. scary!), and I'd rather go the upgrade route if at all possible. I do have lots of backups of user files, but there are non-user changes I've had to make over the years as well: Perl modules, configuring Apache and so on.

Maybe this is a red herring, but I saw somewhere that the Update Manager is written in Python. I installed Python 3.1.2 recently, and I'm wondering if that might have anything to do with this issue. When I just type "python -V" at the prompt, however, I do get version 2.6.5. I presume that's the version that the Update Manager would be using.

---

### Post by Topsiho on 2015-12-20
My post still stands, as it's not clear how old the page you refer to is.
That's the trouble with nearly all information on the internet: how old is the information? Yesterday? Last year? From the last Ice Age?

I wish you luck, and I second the clean install suggestions. And also the suggestions for backing up your precious data first.

Topsiho

---

### Post by pce-accesswave on 2015-12-20
Thanks for your advice! Is it reasonable to assume that it won't be possible to get the Update Manager working? The problem is that the particular computer I'm trying to upgrade can't boot from DVD or from a USB memory, and all recent releases are too big for a CD. This may make even a clean install difficult. I've seen one suggestion to start with the Lubuntu CD and then somehow get back onto Ubuntu, but that's getting complicated. If there was a command line way to upgrade that would be great.

---

### Post by howefield on 2015-12-20
Did you try the "old-releases" repositories as per [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) ?

I think that 12.04 will fit a CD, from 12.10 onwards the images started getting too big and required a DVD or USB, (iirc).

Just to correct something I said above "*not marking the destination will keep your /home folder intact.*" should have been "*not marking the destination **for formatting** will keep your /home folder intact.*"

---

### Post by Topsiho on 2015-12-21
You could try and install using a minimal CD.
See [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
I used to install that way Lubuntu on a very old laptop with a broken DVD-drive.

Topsiho

---

### Post by pce-accesswave on 2015-12-21
Thanks to howefield and Topsiho for their valuable advice, which I really do appreciate. However, after sleeping on this, I come back to my original goal which was to upgrade my OS in a way that preserves my local settings - to Apache, mailman, MySQL and so on. Installing a new OS on top of the existing one will put me back to zero with these, and in spite of my best efforts to preserve them there will be some that I have forgotten. So, I'd really like to focus on fixing the Update Manager. Should I perhaps be asking about this elsewhere?

---

### Post by howefield on 2015-12-21
I don't think you are getting the point of the first thing I mentioned.

By pointing your sources.list at the [old-releases repositories]("https://help.ubuntu.com/community/EOLUpgrades"), you may fix your broken Update Manager.

---

### Post by pce-accesswave on 2015-12-21
Well, I have renamed my existing sources.list and created a new one like this:

```
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
```

and I've gone so far as to enter

$ sudo apt-get update
$ sudo apt-get dist-upgrade

at the command line. The update manager GUI still hangs when I click the close button.

---

### Post by kansasnoob on 2015-12-21
> **pce-accesswave said:**
> Thanks to howefield and Topsiho for their valuable advice, which I really do appreciate. However, after sleeping on this, I come back to my original goal which was to upgrade my OS in a way that preserves my local settings - to Apache, mailman, MySQL and so on. Installing a new OS on top of the existing one will put me back to zero with these, and in spite of my best efforts to preserve them there will be some that I have forgotten. So, I'd really like to focus on fixing the Update Manager. Should I perhaps be asking about this elsewhere?

The odds of your "local settings - to Apache, mailman, MySQL and so on" being retained after performing a release upgrade are slim to none. You previously mentioned having installed at least one package from a source other than the Ubuntu repos and the odds of performing a successful release upgrade go down with each and every user tweak.

I'm curious why you can't boot from USB? Or DVD? If you're using older hardware that shipped only with a CD drive I wonder how compatible it would be with the Unity DE?

Lucid (10.04) still used the GNOME 2 DE whereas Precise (12.04) and later versions use the Unity DE. Are you aware of those changes? Precise did offer a fallback to Unity-2D but that session has now been dropped in later versions. It's possible that you might find your hardware to be incompatible with Unity, or that you may just personally prefer a different DE.

I really think it's imperative to be able to run a live session of a supported version of Ubuntu (or [one of its flavors]("http://www.ubuntu.com/about/about-ubuntu/flavours")) on any hardware that's going to run Ubuntu (or any flavor) just to perform potentially needed repair operations. So I'd first concentrate my efforts on getting a live version of Ubuntu (or some flavor) to run on that hardware. Then check compatibility of the hardware with your desired flavor.

The desktop version of Lucid (10.04) has been EOL since May 2013 and even the server version went EOL in April of this year:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You will almost certainly want to stick with LTS versions since the support cycle of interim releases has now been reduced to 9 months, whereas the LTS versions are supported for 5 years after their initial release. If you can get a live session to run via CD/DVD/USB then a release upgrade may be offered during reinstallation, but even then don't expect all previous settings to be preserved.

---

### Post by pce-accesswave on 2015-12-21
This has gotten to be a much bigger project than I expected. I'm going to leave the computer as it is - it runs and does what I need it to do. I may also explore gradually configuring an eventual replacement for this one. 

Thanks to all for your time and expertise.

Peter

---

