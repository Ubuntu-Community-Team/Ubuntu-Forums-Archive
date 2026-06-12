---
title: "Not allowed to access problem report?"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-10-19
Since I upgraded to Kubuntu 12.10, every time I reboot I get a crash notification.  It also seems to occur every couple minutes.  But when I click on the explosion icon in the task bar to view the problem, a window pops up saying "You are not allowed to access this problem report".  What is this?  How can I bypass it?

[img]http://www.pictureshack.us/images/60583_screenshot1.png[/img]

---

### Post by bra|10n on 2012-10-19
FYI,
```
update
           update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.

       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
```[QUOTE=Stonecold1995]Since I upgraded to Kubuntu 12.10...[/QUOTE]

Hence this should read, "Since I updated to Kubuntu 12.10...

---

### Post by Stonecold1995 on 2012-10-19
> **bra|10n said:**
> Hence this should read, "Since I updated to Kubuntu 12.10...

```
DO-RELEASE-UPGRADE(8)                                                                                                                                                                                                                              DO-RELEASE-UPGRADE(8)

NAME
       do-release-upgrade - upgrade operating system to latest release

SYNOPSIS
       do-release-upgrade [options]

DESCRIPTION
       Upgrade the operating system to the latest release from the command-line.  This is the preferred command if the machine has no graphic environment or if the machine is to be upgraded over a remote connection.

OPTIONS
       -h, --help
              show help message and exit

       -d, --devel-release
              Check if upgrading to the latest devel release is possible

       -p, --proposed
              Try upgrading to the latest release using the upgrader from Ubuntu-proposed

       -m MODE, --mode=MODE
              Run in a special upgrade mode. Currently "desktop" for regular upgrades of a desktop system and "server" for server systems are supported.

       -f FRONTEND, --frontend=FRONTEND
              Run the specified frontend

       -s, --sandbox
              Test upgrade with a sandbox aufs overlay

SEE ALSO
       update-manager(8), apt-get(8)

                                                                                                                              October 2009                                                                                                         DO-RELEASE-UPGRADE(8)
 Manual page do-release-upgrade(8) line 1/38 (END) (press h for help or q to quit)

```

[http://lolsnaps.com/upload_pic/TheGrammarNaziIHatedMost-25867.jpg]("http://lolsnaps.com/upload_pic/TheGrammarNaziIHatedMost-25867.jpg")

---

### Post by Stonecold1995 on 2012-10-25
bump

---

### Post by oldos2er on 2012-10-26
Do you have apport enabled? If so you can turn it off. see [http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport](http://askubuntu.com/questions/93457/how-do-i-enable-or-disable-apport)

---

### Post by drmrgd on 2012-10-26
From what I've seen so far, Apport is an absolute mess. I don't think I've ever gotten it to work correctly, and the last time I had a problem (Nepomuk constantly crashing), I just gave up and turned Nepomuck off.  They really need to work on the bug reporting system as it doesn't seem to work all that well.  

You might be best off following Anne's advice (as sad as it is), and just turning off Apport.

---

### Post by oldos2er on 2012-10-26
Supposedly apport is disabled by default (see [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)), but the "You are not allowed to access this problem report" error sure sounds a lot like apport.

---

### Post by Stonecold1995 on 2012-10-27
Yeah, I know it's apport, but I don't want to turn it off unless I need to.  I'm just wondering why upgrading to 12.10 made it so that it won't let me access the problem report when it use to never have this problem.

---

### Post by robtygart on 2012-10-27
I have not experanced this problem, is there anyway I can recreate it to see what happens to mine?

---

### Post by Stonecold1995 on 2012-10-27
> **robtygart said:**
> I have not experanced this problem, is there anyway I can recreate it to see what happens to mine?
Not sure.  All I did is (a while ago) upgrade from Kubuntu 11.10 to 12.04 (upgrade, not clean install).  And recently I upgraded to 12.10.

Where can I get more information on this?  Where are Apports' error log?

---

### Post by dino99 on 2012-10-27
look at /var/crash/ to know if you are the owner of that crash. If not then:

sudo chown myuser:myuser /var/crash/*

---

### Post by drmrgd on 2012-10-27
> **dino99 said:**
> look at /var/crash/ to know if you are the owner of that crash. If not then:

sudo chown myuser:myuser /var/crash/*

I'm not sure if the re-organized 12.10 (I'm still on 12.04 until VMware gets their client patched for 12.10...can't live without it at the moment!).  But in 12.04, there is an apport log in /var/log in addition to the reports in /var/crash.  I think the /var/crash reports are the "final" versions that apport is supposed to publish to the bug tracking system.

---

### Post by Stonecold1995 on 2012-10-27
> **dino99 said:**
> look at /var/crash/ to know if you are the owner of that crash. If not then:

sudo chown myuser:myuser /var/crash/*

That seemed to work, several of the crash logs were owned by root.  Thank you!

How come upgrading to 12.10 caused some of the logs to be owned by root?

---

