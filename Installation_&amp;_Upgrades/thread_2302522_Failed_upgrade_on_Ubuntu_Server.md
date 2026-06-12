---
title: "Failed upgrade on Ubuntu Server"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by Laage on 2015-11-11
I have (had) a virtual 14.04 Trusty Tahr test-server which I wanted to upgrade to Wily Werewolf. This is for testing/playing purposes so I don't need it to run the LTS.

However, when I did the [FONT=courier new]sudo do-release-upgrade -d[/FONT] it jumped directly to 16.04 Xenial Xerus repositories. I thought the basic [FONT=courier new]do-release-upgrade[/FONT] should just upgrade to the next LTS if one exists and the [FONT=courier new]-d[/FONT] would just upgrade to the latest final release. And to be honest I was under the impression that Xenial Xerus wasn't even in Beta yet.

I ran the the upgrade directly from the VirtualBox console not through an SSH client. 

The upgrade completed the downloads and started running, but it stalled at one point ... This is where the tale becomes slightly muddled as I still thought I could salvage this so I didn't document these steps in any way. I was asked to hit R to reconnect or X to kill the process, and R didn't have any effect. So I killed it with X. And my system was running but not well. I believe I tried running the upgrade again, but it stalled at the same point.

I tried just running [FONT=courier new]sudo apt-get update && sudo apt-get upgrade[/FONT] combo instead and it found a large number of upgrades but failed almost immediately during installation.

I decided to test to change the repositories to 15.10 Wily Werefolf instead hoping they would be more stable.
It seemed to work out and I was able to update most software, however it would fail on Whoopsie with a number of error messages. "Package is in a very bad inconsistent state - you should reinstall it before attempting a removal" was just one of these and [FONT=courier new]sudo apt-get install --reinstall whoopsie[/FONT] didn't work.

I was able to finally fix Whoopsie with:
```
sudo mv /var/lib/dpkg/info/<packagename>.* /tmp/
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get remove <packagename>
sudo apt-get autoremove && sudo apt-get autoclean
```

After Whoopsie was fixed I got a similar error on acpid and I finally got that removed and reinstalled with a similar move as above.

Now when I do a [FONT=courier new]sudo apt-get upgrade[/FONT] it doesn't show any available upgrades, but a [FONT=courier new]sudo apt-get dist-upgrade[/FONT] shows the following: 

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  apt apt-transport-https apt-utils gcc-4.8-base gettext-base libxml2 lshw
  python-apt python3-apt ubuntu-standard
```

The one that worries me the most is ubuntu-standard.
  
Trying to install any of these with apt-get install just gets me versions of this:
```
:~$ sudo apt-get install apt
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 apt : Depends: libapt-pkg4.16 (>= 1.0.10.2ubuntu1) but it is not going to be installed
       Depends: libstdc++6 (>= 5.2) but 4.8.4-2ubuntu1~14.04 is to be installed
E: Unable to correct problems, you have held broken packages.
```

So as far as I can tell most of my system is running Wily-versions of most software, but remains of the Trusty system and the failed Xenial upgrade seems to be creating a number of conflicting dependency issues.

I have run [FONT=courier new]sudo apt-get autoclean[/FONT], [FONT=courier new]sudo apt-get install -f[/FONT] and [FONT=courier new]sudo dpkg --configure -a[/FONT] any number of times during this process. Together and separately but to no avail.

As I said, this is a virtual test server and in principle I could just nuke it and start over from scratch. But part of having this server for testing is to see if I can find ways to fix and or prevent problems on our production machines.

---

