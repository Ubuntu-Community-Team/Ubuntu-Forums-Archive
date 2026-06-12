---
title: "Expected consequences of upgrading Ubuntu 18.04 -&gt; 20.04"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by keijo-kukka on 2020-05-21
Hello Gurus!
I consider myself as a rookie in Linux and have started using Ubuntu 18.04 (Gnome) as my default OS only few months ago. So far I've hardened my system, configured and customized it a bit and installed over 40 applications. Most of them are well-known FOSS and many are security oriented.

I'm now thinking to upgrade from 18.04 to 20.04.

My question is that, is upgrading Linux (Ubuntu) "business as usual" or should I expect any problems with e.g. any configurations I've done so far? How about with any installed applications? Should I expect any critical errors or conflicts, e.g related to booting etc.? I'm going to backup my configurations and system files with Timeshift and I don't have any personal files stored (e.g. videos, photos etc.).

My configurations include:

Enabling default disk encryption during installation
Configuring IPvanish VPN
Firefox customization
Enabling Night Light feature
Installing Curl
Tweaking with Gnome Tweaks and Unity Tweak Tool
Installing exFAT support
Setting static IP
Installing Kali VM in Virtualbox
Configuring Wazuh HIDS
Forwarding syslogs to my NSM
Enabling GNOME "minimize" icons feature
Enabling backups with Timeshift

My installed apps are following:

pCloud
KeePass
Veracrypt
Timeshift
GUFW
GParted
GVM (OpenVAS)
Wireshark
Authy
Signal
Brave
Tor browser
Nmap
ClamTk
Lynis
VirtualBox
Testdisk
gWakeOnLan
Pinta
Etcher
Viber
Gnome Tweaks
Unity Tweak Tool
Fast
VokoscreenNG
VLC
Kdenlive
Steam
Avidemux
Stacer
Shutter
Audio Recorder
youtube-dl
Caffeine
my-weather-indicator
TeamViewer
Synaptic
Gdebi
Flatpak
PlayOnLinux

Thanks a lot guys!!

---

### Post by Perfect Storm on 2020-05-21
Upgrading can be tedious, a lot of things can go wrong. Personally I'll backup and go for a clean install.

---

### Post by ajgreeny on 2020-05-21
I largely agree with AI, but it depends on how close your system is to a default install and how many PPA repos etc you have added; anything that does not come from the usual Ubuntu repos will probably cause problems to you.

Try it if you wish but ***make sure everything is backed up*** in case things go wrong, then you can start again from scratch.

---

### Post by TheFu on 2020-05-21
Good advice above.

If you stay with the core Canonical repos, things will be easier.
If you added a few PPAs, those will be removed during the 18.04-->20.04 move. Some PPAs may not have 20.04 packages ready.
If you installed using AppImage, Flatpak, or Snaps, I don't know what will happen. Snaps would probably be handled. Don't know about the others.
If you installed by downloading a .deb file, all bets are off. Those can break APT. Those can add a PPA. Those can swap the .deb for a snap.  No way to know unless you carefully paid attention during the install.

I have doubts about veracrypt making the transition, just due to the nature of that tool.  Whenever encryption is involved, excellent backups are mandatory.  Would much rather see you using LUKS-based encryption, but if you need cross-platform encryption, LUKS isn't a choice.

I know that the youtube-dl packages provided by Ubuntu are almost always out of date.  There are very few packages where I'd say to avoid any package systems, but youtube-dl is one where the source and self updates should be used instead.

Settings for the system are almost always kept in /etc/  Back that up, but don't just restore the entire thing. You'll need to be highly selective about which config files get restored post-migration.

Individual userid settings are 100%, always, stored in the HOME for each userid.  Conflicts between versions of tools can happen especially when the versions change.  Gnome2 and Gnome3 based tools can conflict.  Firefox versions too.  If this happens, the easy way to check whether it is system-wide or just 1 userid, is to create a new userid, login to the that new user, run the program, see whether the problem continues or not.  Then rather than wiping all settings, you'll know specifically which 1 program setting is causing problems.

Also, what happens if the timeshift versions between 18.04 and 20.04 aren't compatible?  Will you be able to restore the necessary parts?

I ran into that with rdiff-backup. Ended up having to build the older version of the tool, including all the dependencies, myself for 20.04.  I would make the packages, if I knew how.  With 15+ systems, I'm unwilling to change my backup server to a different version of the backup tool we've been using for years just to support 1, new, 20.04 system.  Very disappointed with the rdiff-backup team. They knew the client and server were incompatible due to the change from python2 to python3.  A method of compatibility for all supported releases really needs to be maintained while the releases.

Do you have an nvidia GPU?

Lastly, read the generic Ubuntu 20.04 release notes and the release notes for your specific flavor.  I found some of the information to be woefully understated for snaps.  There need to be a number of warnings about snap packages since they can break workflows to the point that there isn't any workaround.  Mandatory snaps are pushing me to look at Debian, CentOS and Fedora. Hopefully, your needs won't be impacted by snaps negatively.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)
At the bottom of that page, are links to the DE/flavor specific release notes.

Little things like how Canonical has been slowly swapping more and more systemd sub-systems in without really saying it is also concerning.  They do mention chrony and systemd-timesyncd ... on Ubuntu-Mate, chrony doesn't seem to be installed. We are left with systemd-timesyncd which isn't particularly accurate, though still 1000x better than what Windows provides.

There is good news. Read that exFAT is part of the base in 20.04 now.  I don't have any exFAT storage and my 20.04 system is a virtual machine, so doubt I'll use it for months, if ever.

---

### Post by SeijiSensei on 2020-05-21
I've rarely had problems upgrading with do-release-upgrade, however all my systems have a separate partition for /home.  This preserves my personal settings.  If you end up installing a fresh version of 20.04, I'd choose the manual disk configuration option and set up separate partitions devoted to / and /home.

---

### Post by keijo-kukka on 2020-05-22
Thank you very much for all of your helpful answers!! O:)O:) Especially huge kudos to TheFu for such comprehensive answer. I really appreciate all your help and I will also try to contribute when I   have something to share. Based on your answers I've decided not to upgrade my Ubuntu to 20.04, but instead consider clean install when I'm ready.

---

