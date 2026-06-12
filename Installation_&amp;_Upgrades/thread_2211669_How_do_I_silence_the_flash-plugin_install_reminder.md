---
title: "How do I silence the flash-plugin install reminder"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by arch0njw on 2014-03-17
Every time I start up I get a reminder that some software could not be installed.  I am going to guess that this is due to a past failure to install the flashplugin.  I have two accounts on my machine: 1 for work (which uses a proxy), and 1 for non-proxy Internet access.  This is so that I can install things like the flashplugin and have it complete.

I have successfully installed the plugin under my non-proxy account.  However, the primary account I use keeps pestering me about the flashplugin install not succeeding.

Is there a way I can silence this reminder?  It's inaccurate, annoying, and an aggravating reminder that the flashplugin-installer doesn't play nicely with proxies.  (Yes, I've tried every suggestion I can find in these here forums and none work for me.  boo...)

**Edit** with some additional information:
---
The dialog I get is the following:
* Update Information -- KDE Daemon
* There are two "?" items on the left:  (1) Failure to download extra data files, (2) Data files for some packages could not be downloaded.
* Text for the first item:  "The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed...flashplugin-installer .. The download will be attempted again later, or you can try the download again now. Running this command requires an active Internet connection."
* Text for the second item:  "The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed...flashplugin-installer .. This is a permanent failure that leaves these packages unusable on your system. You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem."
---
**Update**: Now that I have the exact text to search on... I found this thread:  [http://ubuntuforums.org/showthread.php?t=2134888](http://ubuntuforums.org/showthread.php?t=2134888) .  I'll give that a try and see what happens.
---
**Update**: Well that didn't work.  I removed the flashplugin-installer.failed file and then the same dialog started complaining about ttf-mscorefonts-installer.  I then removed the ttf-mscorefonts-installer.failed file and now the dialog is complaining about the fonts AND the flash plugin.  It's be so super marvy if these installers would play nicely with a proxy.
---


Help is appreciated.
This community is awesome!

---

### Post by westie457 on 2014-03-19
Have you tried installing or reinstalling the 'kubuntu-restricted-extras' package accepting the defaults for any pop up questions that appear.

IMH(umble)O using a proxy connection should not make any difference to this installation.

---

### Post by arch0njw on 2014-03-21
I tried reinstalling the kubuntu-restricted-extras package with no difference.  I followed the suggested steps at the following thread, and the msft fonts installed as did the adobe plugin.
[http://ubuntuforums.org/showthread.php?t=2134888](http://ubuntuforums.org/showthread.php?t=2134888)

Maybe THIS is the end of these silly messages...! ...?

---

### Post by z_mikowski on 2014-06-22
This was driving me insane.  I purged flashplugin-installer, I installed adobe-flashplugin.  I deleted the file in var. And still the notification came **up every frick'n time I logged into my !@#$ account**.  ARRRGH!

So I resorted to a little sys-admin snooping:

[FONT=courier new]  sudo su
  cd /var
  grep -r 'flashplugin-installer' *

  # and later to revert to normal user...
  exit; 
[/FONT]This shows a surprising number of files.  I found a couple that looked highly suspect and removed them:

[FONT=courier new]
  sudo \
    rm lib/update-notifier/user.d/data-downloads-failed-permanently \
    lib/update-notifier/user.d/data-downloads-failed

[/FONT]
And praise the Lord almighty, the !@#$ PITA stoopid message **went the *redacted* away.**  Out, damn spot!

I hope others find this useful.

---

### Post by arch0njw on 2014-06-23
> **z_mikowski said:**
> [FONT=courier new]
  
cd /var
[/FONT][FONT=courier new]sudo \
    rm lib/update-notifier/user.d/data-downloads-failed-permanently \
    lib/update-notifier/user.d/data-downloads-failed[/FONT]

EH MAH GAD
EH MAH GAWD
EH MAH GOD
OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG OMG 

You are my facking hero today!!!

This totally worked.  HOOOORAAAAAAAAYYYY!!!!!!!

---

