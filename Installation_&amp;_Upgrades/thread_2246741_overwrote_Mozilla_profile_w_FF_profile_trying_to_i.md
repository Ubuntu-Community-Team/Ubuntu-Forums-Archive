---
title: "overwrote Mozilla profile w FF profile trying to install new FF32 AMD64"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by mkham on 2014-10-02
I only have Ubuntu 10.4 on Acer Turion AMD64 and the stores weren't giving me anything more than FF20, which probably isn't secure... so I manually installed FF32 AMD64 in the opt folder as per some instructions. I could access the folder -permission denial, so I logged in as root in file manager, and did it, opening by terminal command. In trying to migrate profiles from the old version, it somehow did it by itself (maybe when restarted as Not root it couldn't access it's new profile). But being an idiot and up 24 hours- I for some reason overwrote the MOZILLA profile (I have Seamonkey + Thunderbird, which both still work OK) with the old FF20 profile, destroying it. Now both versions of FF don't open, saying there it is already running and you must stop that first, but process manager doesn't show anything running. Should I destroy that MOZILLA profile and reinstall old FF (or is there a store I can add for the new one) to recreate the Mozilla profile (which goes back to 2008, when I installed Hardy) or what? Thanks.

---

### Post by mkham on 2014-10-02
couldn't access the folder

---

### Post by oldfred on 2014-10-02
While the server version of 10.04 is supported for a few more months, the desktop version is not. 

       "Your version of Ubuntu has reached End Of Life. It is no longer supported by Canonical and it is likely that many problems simply cannot be solved. The Staff recommends that you upgrade to a supported version. Please refer to this.
Ubuntu 10.04 (Lucid Lynx) Desktop End of Life reached on May 9, 2013
[http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/](http://fridge.ubuntu.com/2013/05/10/ubuntu-10-04-lucid-lynx-desktop-end-of-life-reached-on-may-9-2013/)
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
This command will print the exact status of your system.
ubuntu-support-status

Did you boot Thunderbird in administrative mode using sudo or gksudo in terminal. Then you may have moved profile to a new user "root" which only has root access. 
I have used same profile for both Firefox & Thunderbird since about 2006, and opened with XP and multiple Ubuntu installs over the years. Even copied to laptop & back when traveling.

But I also houseclean messages, and fully back up entire profiles on a regular basis. My backup includes a backup folder on another drive, my laptop when copied to it and quarterly copies to DVD to archive everything.

---

### Post by Dennis N on 2014-10-02
This may help to with the "already running" issue:
[https://support.mozilla.org/en-US/kb/firefox-already-running-not-responding](https://support.mozilla.org/en-US/kb/firefox-already-running-not-responding)

Start the new install from the terminal: /opt/firefox/firefox (guessing on this, but this is were a manual install usually goes) and see how it runs. Later, you have to make a new launcher for it or the old firefox will be starting.

Your profile is in ~/.mozilla/firefox and is a folder named with the extension .default preceded by some random characters. (Example: y01fj8zw.default) It contains your settings, plugins in use, bookmarks, passwords, etc. 

A new firefox install will use the same profile as the previous version, preserving your bookmarks and passwords and other settings. It may not really be deleted unless you deliberately delete it. If you did, it may just be in the trash unless you emptied the trash too.

---

### Post by mkham on 2014-10-03
You mean remove the FF32 I already installed or just delete all the files? Or it will just over write them anyway. I know where the profiles are- had to to overwrite the Mozilla profile- I backed the old main one up, but sadly neglected to do with the Mozilla profile (which I thought was some remnant- may have tried to do the same with FF31). All the junk files from FF profile won't cause problems in the Mozilla profile? And I was under the impression that unpacking (there is no install per se) the FF32 in opt DOESN'T affect anything else, that it's a stand alone install. It defaulted to the original profile cause there was an ini file saying that was the default, I guess. What the hell is in this Mozilla profile anyway- since Thurnderbird + Seamonkey don't need or use it, apparently?

---

### Post by mkham on 2014-10-03
In checking that link, I checked the profiles and both the one in .mozilla (9fa), and the FF one (5eth), are locked and the permissions say owner is ROOT (with read, write, exe checked, but only for ROOT). So can I log in to file manager as root and change ownership to ME? Should the Mozilla + FF profile be locked by default?

---

### Post by oldfred on 2014-10-03
I have both my Firefox & Thunderbird profiles in a data folder mounted as mozilla. I just moved to another drive and reset ownership & permissions.

You may also need the -R for recursion for both your  ~/.mozilla & ~/.thunderbird if they are still in default locations in /home. (~ is short name for /home/$USER)
sudo chown  $USER:$USER /mnt/data/mozilla

I did the chmod on my entire data partition with -R which is recursion and changed everything below it. Do not run on any system partition as it can destroy system. Ok on data or /home, but check mount before running.
sudo chmod -R a+rwX,o-w /mnt/data

I have run same commands on /home/fred, but once back in beginning ran on / or left a space between / & home so it was running on root and destroyed system. I had to reinstall.

---

### Post by mkham on 2014-10-03
Thanks, but I destroyed that profile in the Mozilla folder by overwriting it with the FF 6eth (that caused all the problems)- is that necessary- does that have the files to actually run or manage FF?  Or is it some remnant- does Mozilla have a default profile of it's own when FF is installed?  So then the problem isn't just unlocking the folder or files (though it probably includes that). The FF profile should NOT show as locked?

---

### Post by oldfred on 2014-10-03
It normally creates a new profile when you first load Firefox or Thunderbird. I usually do that, then copy my old profile and edit profile.ini to be my old one.

The locked may be an issue and many different software only want to be loaded once. So they open a lock file which they check and then close that when shutting down. If an abnormal shutdown then lock file may not get deleted or reset and cause issues that you have to manually clear.

---

### Post by mkham on 2014-10-03
DIdn't see your first post, OF- entered that status command, here's result:
  File "/usr/bin/ubuntu-support-status", line 105, in <module>
    (still_supported, support_str) = get_maintenance_status(cache, pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 37, in get_maintenance_status
    raise Exception("No date tag found")
Exception: No date tag found

This is an old computer 2006 (or even 2005) and am dubious the newest Ubuntu would work without needing some more advanced feature I don't have. I still can't do suspend without getting graphical insanity when I come back, though it works fine in Windows (and I've tried all those suspend parameters). But it did boot live Peppermint 5, based on Ubuntu 14.4, though it didn't seem to have my Wifi driver. Also have this on tiny partition with no space around it- 7 gb, and presume latest versions are bigger. I'll try removing the locks.

---

### Post by mkham on 2014-10-03
DIdn't see your first post, OF- entered that status command, here's result:
  File "/usr/bin/ubuntu-support-status", line 105, in <module>
    (still_supported, support_str) = get_maintenance_status(cache, pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 37, in get_maintenance_status
    raise Exception("No date tag found")
Exception: No date tag found

This is an old computer 2006 (or even 2005) and am dubious the newest Ubuntu would work without needing some more advanced feature I don't have. I still can't do suspend without getting graphical insanity when I come back, though it works fine in Windows (and I've tried all those suspend parameters). But it did boot live Peppermint 5, based on Ubuntu 14.4, though it didn't seem to have my Wifi driver. Also have this on tiny partition with no space around it- 7 gb, and presume latest versions are bigger. I'll try removing the locks.

---

### Post by mkham on 2014-10-03
This is result of attempted unlock- maybe it's got to be .mozilla ? In file manager, FileSys/mnt shows no files or folders
chown: cannot access `/mnt/data/mozilla': No such file or directory

I've got a separate mozilla-thunderbird folder and .thunderbird, why that is unaffected, but Seamonkey, in the .mozilla folder, also works fine.

---

### Post by oldfred on 2014-10-03
I posted mine,but those are not standard locations, as I was not sure you still had/have default locations. You have to change to your locations.
If defaults these will work to set ownership & permissions:

sudo chown -R $USER:$USER ~/.thunderbird
sudo chmod -R a+rwX,o-w ~/.thunderbird

For Firefox:
same for ~/.mozilla

---

### Post by mkham on 2014-10-03
Ahha, you are a prince. That ficked it, as my little nephew used to stay. It is using the old profile too. How do I make a screen launcher (10.4 gnome) for it? Terminal command is a pain.

My Opera is also ancient - 12. I downloaded Opera 25 for AMD Linux or Ubuntu- would the procedure be the same? Actually just unpacking an archive that will then completely work without installing anything is quite strange- that's like a portable version?

---

### Post by mkham on 2014-10-03
duplicate

---

### Post by mkham on 2014-10-03
I get these warnings when I start FF32. Also never got a prompt after. Know what they mean, or just how to fix them:

LoadPlugin: failed to initialize shared library /opt/real/RealPlayer/mozilla/nphelix.so [/opt/real/RealPlayer/mozilla/nphelix.so: wrong ELF class: ELFCLASS32]
1412372259505	addons.update-checker	WARN	Update manifest for [email]ubufox@ubuntu.com[/email] did not contain an updates property

(firefox32:3185): Gtk-CRITICAL **: gtk_clipboard_set_with_data: assertion `targets != NULL' failed

** (firefox32:3185): CRITICAL **: gst_app_src_set_size: assertion `GST_IS_APP_SRC (appsrc)' failed

(firefox32:3185): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `autoplug-sort' is invalid for instance `0x7f83f9c8dc00'
1412376238359	addons.update-checker	WARN	Update manifest for {972ce4c6-7e08-4474-a285-3208198ce6fd} did not contain an updates property
1412376238398	addons.update-checker	WARN	Update manifest for [email]ubufox@ubuntu.com[/email] did not contain an updates property

** (firefox32:3185): CRITICAL **: gst_app_src_set_size: assertion `GST_IS_APP_SRC (appsrc)' failed

(firefox32:3185): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `autoplug-sort' is invalid for instance `0x7f83e1f23800'

---

### Post by mkham on 2014-10-03
n

---

### Post by oldfred on 2014-10-03
I am using fallback/flashback or gnome-panel which is like the old gnome2 menus. Not sure about new gnome or other gui. I just drag menu entry to desktop and to top panel and have icons.

Most applications should be installed from repositories. I prefer synaptic, but Software center should work. If not in repository then you can use ppa or .deb for Debian type systems. If neither of those exist which is very rare then you hav eto download an archive and or recompile yourself.

---

### Post by Dennis N on 2014-10-04
If FF runs correctly, then don't worry about the scary warnings in the terminal.

You don't really need to make a new launcher, you can use the old launcher after changing the command it uses to the one that starts the FF32 version. 

On my system, which is Xubuntu, I can right-click on the launcher on the panel, click properties, edit, and fill the command box with the new command that starts the new version. You have to figure out how that is done on Ubuntu 10.04, as I don't have that version handy to look at. Do you know that 10.04 is out of date?

---

### Post by vasa1 on 2014-10-04
> **Dennis N said:**
> If FF runs correctly, then don't worry about the scary warnings in the terminal.
...
+1.

Re. scary warnings, [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

### Post by mkham on 2014-10-04
Thanks Dennis- that was easy. Just changed firefox to firefox32. Desperately need space- where are the files for FF20 to delete- an installation is usually 200-250 mb. Should be able to get 100-150mb back. The multiple warning disappeared on restart. I know Ubuntu 10.4 is old- this computer is 2006 or even 2005, newer versions demand features I don't have and are probably larger installations- I have no space and PATA drives are 6x more than SATA now. I still get the updates for it (don't know how)- till that ends I'll stick with it. Anyone know repositories for FF or Opera or Midori that work w 10.4 to get updates and latest versions? Just unpacked this version in opt, so guess updates wouldn't know where to change it. I'm so happy got a new browser.

Pretty desperate to get a version of Skype that works since they shut down everything before 4.3 (better to force suckers back into MS). Have it on XP but the vulnerabilities make me ill. Tried forcing the i386 version but that didn't work- the chumps don't make a Linux AMD64.

---

### Post by oldfred on 2014-10-04
My laptop is also from 2006 and runs 12.04 better than the older versions. Because of limited video you often cannot run the full Ubuntu, so many suggest Xubuntu or Lubuntu. I do install full 64bit Ubuntu on laptop with 1.5GB of RAM. It runs Unity so slow as to be unuseable, but I then convert to fallback/flashback/gnome-panel which is menus almost the same as the old gnome2 in your 10.04. 

       Classic, fallback, flash back explanation -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)
How to choose Display manager sessions -  by kanasnoob 
[http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682](http://ubuntuforums.org/showthread.php?t=2184682&p=12929682#post12929682)

 sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by Dennis N on 2014-10-04
> Anyone know repositories for FF or Opera or Midori that work w 10.4 to get updates and latest versions? Just unpacked this version in opt, so guess updates wouldn't know where to change it.
Having obtained your Firefox directly from Mozilla.org, you will now receive updates from Mozilla directly. If a new version becomes available, a notification will pop up while using Firefox to inform you, or you can set up automatic downloading and installation:

For update options:

**Edit > Preferences > Advanced > Update Tab**

Default is to automatically install updates - I can attest that this will work - even when its installed in /opt.

---

### Post by mkham on 2014-10-06
Thanks all. Really, if I want to go through the huge hassle of switching OS's, probably would install Peppermint 5, based on Ubuntu 14.4, small light fast. I have no space on HD either- it's a 7.5gb partition. I like the idea of getting 5 years of support. In fact I might have done it but the Live disc didn't find my wifi, which wasn't reassuring. But thanks for the tips about Gnome- I'm sure that's real handy for all the poor slobs whose old computers can't run full version and got tired of constant Win XP infections.

Where would the files be for the older Firefox 20, that I can delete. They don't share I guess- it's all in opt, except for the profile.

---

### Post by Dennis N on 2014-10-06
FF20:
There is a symbolic link **firefox** in **/usr/bin**:
```
lrwxrwxrwx 1 root root 25 Sep 24 02:28 firefox -> ../lib/firefox/firefox.sh
```
So the Firefox folder is at **/usr/lib/firefox**

(I don't like removing this manually - I would use Synaptic to keep my package records straight, but it's up to you. Using Synaptic would also remove the launcher and menu item, and maybe the icon so those would have to be manually recreated. I would back up the .mozilla folder to be safe.)

---

### Post by mkham on 2014-10-07
Hmmm, think new version 32 needs firefox-gnome-support (ver20.0 184kb), which synaptic insists on removing?

---

### Post by vasa1 on 2014-10-07
I have *32.0.3* but don't have this "firefox-gnome-support" package. This is with Firefox 32 installed in my home folder direct from Mozilla on Lubuntu 14.04.

Don't see it with an **apt-cache search**.

---

### Post by Dennis N on 2014-10-08
> **mkham said:**
> Hmmm, think new version 32 needs firefox-gnome-support (ver20.0 184kb), which synaptic insists on removing?

If you believe so, or are in doubt, you could leave the old Firefox alone. Or, let Synaptic go ahead and remove it but download the .deb package first from the Lucid repository in case something doesn't work right with Firefox 32 after removal and you need to reinstall the package.

[http://packages.ubuntu.com/lucid/firefox-gnome-support](http://packages.ubuntu.com/lucid/firefox-gnome-support)

---

### Post by mkham on 2014-10-11
Do you have it installed in Opt?  So I remove just "firefox" which is F20, simple removal??  That won't destroy anything else I need? Apparently it does need the profile in the mozilla folder, when I renamed it, did the "already running" message. That's got another 152Mb- why would it need 2 profiles? Then there was the original FF32 profile visible under root, now apparently not.

---

### Post by Dennis N on 2014-10-11
Removing FF20 with Synaptic won't touch the FF folder in /opt. Yes, the new Firefox 32 is using the same profile in ~/.mozilla. We want to keep that. So, if you use Synaptic to remove FF20, that is why I suggest backing up that folder in case the removal of FF20 removes the profile from there. Again, be aware that you are most likely going to have to make a new menu entry and launcher for Firefox 32 so be sure you know how to make those. I haven't used gnome 2 for a long time, so can't give advice on that.

I also think I would not have FF32 running when you remove FF20.

---

