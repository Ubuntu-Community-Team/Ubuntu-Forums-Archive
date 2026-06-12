---
title: "Net-based install behind proxy leaves flash in a weird state"
date: 2012-07-20
forum: Installation &amp; Upgrades
---

### Post by dlpartain on 2012-07-20
Greetings,

Rather than repeat it here, you can find the description of how I install my Ubuntu boxen here: [http://ubuntuforums.org/showthread.php?t=2029774](http://ubuntuforums.org/showthread.php?t=2029774) 

In short, it's a mini.iso-based installation using preseeding.  This is generally working well but with a couple of annoying glitches that I'm hoping to get help with here.  The above link describes one, and this is the second :-)

During the preseed-based installation, I run a script that installs ubuntu-restricted-extras, which includes flash.  That script has:

export http_proxy="http://my-corp-proxy:8080"
export https_proxy="http://my-corp-proxy:8080"
export no_proxy="localhost,127.0.0.0/8,my-install-server"
apt-get -y install ubuntu-restricted-extras | logger

(since I live behind a corporate firewall)

When the installation is finished and I log in, I get a popup that has:

<popup>
Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
</popup>

The fascinating thing about that is that flash is working :-)  I go to [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) and the version information has "You have version 11,2,202,236 installed".  Videos on youtube are fine, too.

So, when I look in /var/log/installer/syslog (which has the log of the installation), I see:

logger: Processing triggers for update-notifier-common ...
logger: flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz)
logger: Installing from local file /tmp/tmpuVg4JP.gz
logger: Flash Plugin installed.
in-target: debconf: unable to initialize frontend: Passthrough
in-target: debconf: (Failed to open fd 3: Bad file descriptor at (eval 24) line 3)
in-target: debconf: falling back to frontend: Noninteractive

I have no idea what the debconf errors mean...

If I do, after installation:

# export http_proxy=http://my-corp-proxy:8080
# python /usr/lib/update-notifier/package-data-downloader
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.236.orig.tar.gz)
Installing from local file /tmp/tmpbsTgmB.gz
Flash Plugin installed.

it works.  HOWEVER, the popup appears for all users who log in on the machine, whether that's been run or not.

It may be worth noting that the ttf-mscorefonts-installer, which does something similar to get the fonts installed, prints the same messages about debconf, but it's installed and I get no warnings or popups about it.  That may be because I have

ttf-mscorefonts-installer msttcorefonts/http_proxy string [http://my-corp-proxy:8080](http://my-corp-proxy:8080)

as a debconf option, so the installer honors the proxy setting and it just works.

So now I'm stuck with a situation where

- I want to do a fully-automated install (and it's almost there!)
- I'm behind a corporate proxy
- flash is clearly installed correctly, but update-notifier doesn't think it did, so I'm getting the popup.
- Even running 'python /usr/lib/update-notifier/package-data-downloader' doesn't prevent the popup appearing for other users.

[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/983559](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/983559) may be related, but I am not using kind of APT proxy setting since my ubuntu mirror is on the inside of the corporate proxy.

Can anyone offer suggestions about how I might solve this or what else I might look for?

Cheers,

David

---

### Post by tokarbol on 2012-07-23
Hello,

I do not know about your company's policy regarding some proprietary software, but we are actually using the Canonical partner archive, which contains "adobe-flashplugin" package. Not -installer, it just contains Adobe Flash. If you use the partner repository in the preseed file:

d-i apt-setup/partner boolean true

Then I believe you need to do nothing else as ubuntu-restricted-extras depend on ubuntu-restricted-addons which in turn recommends "adobe-flashplugin | flashplugin-installer", so I guess it would automatically resolve to the former.

Oh, you could also put adobe-flashplugin to your local repository, but that requires you to fill out and sign Adobe distributor license (it's somewhere on their website).

The bug report for your issue itself is here (I believe):
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/977178](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/977178)

I hope this helps.

Cheers,
Ballock

---

