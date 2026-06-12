---
title: "unattended-upgrades error: Cache has not allowed changes"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by horst on 2014-08-15
Hi,

on my parent computer (Kubuntu 14.04, x86, 2GB RAM, 15 GB free in /)  I use unattended-upgrades to install the updates during shutdown and it works normally flawless. Since some weeks (maybe since Kubuntu 14.04) I get errors if unattended-upgrades wants to update more that maybe 5 or so packages software mainly KDE updates with the error "ERROR Internal error while building a minimal partition.Cache has not allowed changes" that gives me no hint in the internet. If I do an "apt-get update && apt-get upgrade", it works flawless. Do you have any ideas?

TIA



log from: /var/log/unattended-upgrades
###########################################################################################################################
2014-08-14 16:58:21,573 INFO Starting unattended upgrades script
2014-08-14 16:58:21,573 INFO Allowed origins are: ['o=Ubuntu,a=trusty-security', 'o=Ubuntu,a=trusty-updates']
2014-08-14 17:00:57,289 INFO Packages that will be upgraded: akregator ark audiocd-kio baloo dolphin dragonplayer gwenview kaddressbook kamera kate kate-data katepart kde-baseapps-bin kde-baseapps-data kde-l10n-de kde-runtime kde-runtime-data kde-wallpapers-default kdebase-runtime kdelibs-bin kdelibs5-data kdelibs5-plugins kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-runtime kdepimlibs-kio-plugins kdoctools kfind khelpcenter4 kio-audiocd kmix knotes konqueror konqueror-nsplugins konsole kopete korganizer krfb ktimetracker kwrite libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libakonadi-socialutils4 libbaloocore4 libbaloofiles4 libbaloopim4 libbaloowidgets4 libbalooxapian4 libcalendarsupport4 libeventviews4 libgpgme++2 libincidenceeditorsng4 libkabc4 libkactivities-bin libkactivities-models1 libkactivities6 libkalarmcal2 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdepim4 libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2-0 libkdnssd4 libkemoticons4 libkfile4 libkfilemetadata4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkleo4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common libkonq5abi1 libkonqsidebarplugin4a libkontactinterface4 libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libktexteditor4 libktnef4 libkunitconversion4 libkutils4 libkxmlrpcclient4 libmailcommon4 libmailimporter4 libmailtransport4 libmessagecomposer4 libmessagecore4 libmessageviewer4 libmicroblog4 libnepomuk4 libnepomukcore4abi1 libnepomukquery4a libnepomukutils4 libnoteshared4 libokularcore4 libpimcommon4 libplasma3 libqgpgme1 libsendlater4 libsolid4 libsyndication4 libtemplateparser4 libthreadweaver4 nepomuk-core-data okular okular-extra-backends plasma-dataengines-addons plasma-scriptengine-javascript plasma-widget-folderview plasma-widget-kimpanel plasma-widgets-addons python-kde4 python3-pykde4
2014-08-14 17:00:57,290 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2014-08-14_17:00:57.289825.log'
2014-08-14 17:01:25,016 ERROR Internal error while building a minimal partition.Cache has not allowed changes
###########################################################################################################################

/etc/apt/apt.conf.d/50unattended-upgrades:
###########################################################################################################################
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
        "${distro_id}:${distro_codename}-updates";
};
Unattended-Upgrade::MinimalSteps "true";
Unattended-Upgrade::InstallOnShutdown "true";
###########################################################################################################################

---

### Post by horst on 2014-08-20
Hi,
what a pity that nobody could help me. I made a workaround not to have so much packages to be installed by removing the "-updates" repository:

/etc/apt/apt.conf.d/50unattended-upgrades:
#################################### 
Unattended-Upgrade::Allowed-Origins {
"${distro_id}:${distro_codename}-security";
#"${distro_id}:${distro_codename}-updates";
};
Unattended-Upgrade::MinimalSteps "true";
Unattended-Upgrade::InstallOnShutdown "true";
####################################

---

### Post by horst on 2014-12-03
Hi,

after updating this x86 to Kubuntu 14.10 this still does happen. I also installed Kubuntu 14.10 on another laptop (amd64) with 2 GB RAM and get the same error. So this does to seem a bug. What do you think?

---

### Post by ian-weisser on 2014-12-03
The only apparent difference between your settings and mine is you install on shutdown; I don't. I don't seem to have the problem.
Yes, it seems a bug. Please report it on the bug tracker with sufficient detail for a bug triager to reproduce it on their system.

---

