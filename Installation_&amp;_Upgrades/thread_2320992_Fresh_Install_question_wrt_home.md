---
title: "Fresh Install question wrt /home"
date: 2016-04-19
forum: Installation &amp; Upgrades
---

### Post by pfeiffep on 2016-04-19
I've always preformed fresh installs vs upgrading. I think I may be missing a time saver. 

If I import the contents of /home into my new installation will all the Thunderbird and Firefox configurations be imported also?

I don't use /home for general data - in my situation self generated data is stored an a NAS accessible by Ubuntu, Win 7, Mac OSx.

TIA

---

### Post by sammiev on 2016-04-19
Hi,

I keep my /home in its own partition and whenever installing a new version of Ubuntu use something else in the install.

When selecting /home make sure the check mark is not there under format.

This way all your config files for FireFox and other things will still be there.

Works great for having more than one OS as you can share the same /home partition.

---

### Post by grahammechanical on 2016-04-19
You may not need to import the entire contents of /home just .mozilla & .thunderbird folders.

I also think that Firefox & Thunderbird have options to backup certain stuff or to sync to a Firefox account or something like that.

Regards.

---

### Post by oldfred on 2016-04-19
I regularly move my Firefox & Thunderbird profiles around and back them up. Usually in my /mnt/data (ext4) partition, but I started when still using XP and had them in a NTFS shared partition, so no matter which system I booted I had same Firefox & Thunderbird data.

They are in . (hidden) folders in /home, so if you restore /home or use a common /home then you will have the same profile. But you may have to reset profile.ini if you start either before it sees the saved /home or data as it will create a new profile.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by howefield on 2016-04-19
> **pfeiffep said:**
> If I import the contents of /home into my new installation will all the Thunderbird and Firefox configurations be imported also?

I don't use /home for general data - in my situation self generated data is stored an a NAS accessible by Ubuntu, Win 7, Mac OSx.

TIA

Another option is to put the Thunderbird and Firefox configurations on the other drive and tell the freshly installed Thunderbird and Firefox where they are. I do this with a number of config files to ease re-installation, I also think it relieves the SSD which houses the OS of a little wear and tear. I have a Data_Store folder on the secondary drive containing the profiles for a few applications including the 2 that you mention.

On re-installation it is simply a case of using the terminal 

```
thunderbird -p
```

and create the new profile pointing it to the existing folder on the secondary drive which contains the profile, likewise for Firefox.

If you use Chromium you would..

```
sudo nano /usr/share/applications/chromium-browser.desktop
```
and edit the line "*Exec=chromium-browser %U*" to make it say..
```
Exec=chromium-browser %U --user-data-dir=/path/to/chromiumprofile
```

I also have a few small (in size) config files zipped up ready to extract to the new /home folder, things like mutt, weechat and tmux.

---

### Post by pfeiffep on 2016-04-19
Thanks to all for great advice.

While searching I found [Aptik]("https://launchpad.net/apt-toolkit") - any additional thoughts?

---

### Post by Bucky Ball on 2016-04-19
Not sure Aptik will backup Thuderbird and Firefox profiles though. Best confirm. You may need to do that manually. ;)

---

