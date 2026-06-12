---
title: "I have a bug during upgrading Ubuntu 12.04 to Ubuntu 12.04"
date: 2019-07-02
forum: Installation &amp; Upgrades
---

### Post by soames on 2019-07-02
I have a laptop with pre-installed Ubuntu 12.04.
Laptop is [COLOR=#000000][FONT=&amp] DELL Inspiron3521

Skype doesn't work on Ubuntu 12.04
Some internet pages don't work on it.

So I have decided to upgrade for Ubuntu 14.04 (not new intallation) and made [/FONT][/COLOR]```
[COLOR=#000000][FONT=&amp]sudo do-release-upgrade[/FONT][/COLOR]
```

[FONT=Ubuntu Beta][COLOR=#000000]In then end of upgrading, when the 50 packets should be deleted I saw a crytical error[/COLOR][/FONT]

I'm afraidding to reboot my laptop now

What I suppose to do now?

---

### Post by rsteinmetz70112 on 2019-07-02
What was the error?

It is not unusual to get errors doing a release upgrade, especially on a release that has been EOL for so long.

---

### Post by soames on 2019-07-02
> **rsteinmetz70112 said:**
> What was the error?

It is not unusual to get errors doing a release upgrade, especially on a release that has been EOL for so long.
Full Logs are in first post


```
[COLOR=#000000][FONT=&quot]Traceback (most recent call last): [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File "/tmp/update-manager-We5tth/trusty", line 10, in <module> [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]sys.exit(main()) [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File "/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeMain.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 244, in main [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]if app.run(): [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]"/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeController.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 1839, in run [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]return self.fullUpgrade() [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]"/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeController.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 1817, in fullUpgrade [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]self.doPostUpgrade() [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]"/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeController.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 1305, in doPostUpgrade [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]self._view.confirmChanges(summary, changes, [], 0, actions, False)): [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File "/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeViewText.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 187, in confirmChanges [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]res = readline() [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File "/tmp/update-manager-We5tth/DistUpgrade/DistUpgradeViewText.py", [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]line 50, in readline [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]return s.decode(ENCODING, "backslashreplace") [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]File "/usr/lib/python2.7/encodings/utf_8.py", line 16, in decode [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]return codecs.utf_8_decode(input, errors, True) [/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]TypeError: don't know how to handle UnicodeDecodeError in error [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]callback [/FONT][/COLOR]
```

---

### Post by rsteinmetz70112 on 2019-07-02
That looks like a python error. 

You said you were afraid to reboot, if you haven't and are now running 14.04 you could try to see if dpkg and apt or apt-get are working.

```
sudo dpkg --configure -a
sudo apt install -f
```

You can add the -s to apt to do a dry run.
If that works you probably will be to do -

```
sudo apt update
sudo apt upgrade
```

That will probably fix the errors.

If the python install is broken you may have to work through fixing it by reinstalling or upgrading the python packages.

---

### Post by soames on 2019-07-02
Only skype was upgraded.
This one doesn't work - [COLOR=#000000][FONT=&amp]sudo dpkg --configure -a [/FONT][/COLOR]

---

### Post by wildmanne39 on 2019-07-02
Your best option is to back up all important data and do a fresh install of an supported version like 18.04, because 14.04 is still unsupported.

---

### Post by soames on 2019-07-02
> **wildmanne39 said:**
> Your best option is to back up all important data and do a fresh install of an supported version like 18.04, because 14.04 is still unsupported.
I have also made back up before upgrading.
I know that fresh install is better but I want to make upgrading
Can I finish it?
Or I need repair my system with a litlle help of Clonezzilla and start upgrading from begiinning?

What will happen, if I reboot my laptop?

---

### Post by ajgreeny on 2019-07-02
I don't think it will be easy to upgrade to 14.04 as its repos will already have moved and not be available for upgrades or installs any more, it lost support in April this year.

If you do manage to upgrade to 14.04 from 12.04 by pointing to the moved repos for EOL versions, it will not be helpful as you will immediately have to run a second upgrade from 14.04 to 16.04.

Save yourself a lot of angst and time, and probably trouble, by doing what wildmann39 suggests above and doing a clean install of 18.04.
Be aware that Ubuntu 18.04 now uses a version of the gnome desktop which looks like but acts differently to unity which you are probably using now; you may prefer a different DE version, eg Xubuntu, Ubuntu Mate, Lubuntu or something else so why not try them in live form to see what you like best then download the 18.04 iso of the chosen version and clean install.

---

### Post by kurt18947 on 2019-07-02
ajgreeny gives good advice. Ubuntu has changed a bit since 12.04. I get along pretty well with 18.04's version of Gnome, not everyone does.

---

### Post by soames on 2019-07-03
I know that a fresh installing much faster and easier.
I have made many fresh installings on the computers which has no pre-intalled system
But I wish to save my pre-installed system, so I'm making an upgrading

Can you help me advising how I can finish it, please?

If I'll do it - it will be lovely
If I'll fail - I will make a fresh install
But I suppose to make mu mind to begin a fresh installing

---

### Post by soames on 2019-07-03
[COLOR=#6A6A6A][FONT=arial]**Reboot, or not reboot**[/FONT][/COLOR][COLOR=#545454][FONT=arial]: that is the question[/FONT][/COLOR]

---

### Post by soames on 2019-07-03
```
[COLOR=#000000][FONT=&quot]uname -a[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Linux roman-Inspiron-3521 3.2.0-39-generic #62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&quot]sudo apt-get install linux-generic-lts-wily [/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=&quot]Running depmod.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]update-initramfs: deferring update (hook will be called later)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Examining /etc/kernel/postinst.d.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/dkms 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]does not match this kernel/arch.  This indicates that it should not be built.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]update-initramfs: Generating /boot/initrd.img-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/dkms 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/alsa-hda-dkms.0.crash'[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]does not match this kernel/arch.  This indicates that it should not be built.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/oem-wireless-ath9k-3.9-rc4-2-dkms.0.crash'[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]update-initramfs: Generating /boot/initrd.img-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/pm-utils 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/update-notifier 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=&quot]Examining /etc/kernel/header_postinst.d.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]run-parts: executing /etc/kernel/header_postinst.d/dkms 4.2.0-42-generic /boot/vmlinuz-4.2.0-42-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/alsa-hda-dkms.0.crash'[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/alsa-hda/0.201207191422~precise1/build/make.log for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]does not match this kernel/arch.  This indicates that it should not be built.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/oem-wireless-ath9k-3.9-rc4-2-dkms.0.crash'[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error! Bad return status for module build on kernel: 4.2.0-42-generic (x86_64)[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Consult /var/lib/dkms/oem-wireless-ath9k-3.9-rc4-2/0.1/build/make.log for more information.[/FONT][/COLOR]
```

---

### Post by TheFu on 2019-07-03
> **soames said:**
> Can you help me advising how I can finish it, please?


Everyone else here is being too nice and it hasn't worked to make the point.  You'll need a time machine to go back to February to access 14.04 repos.  In  truth, you've waited too long by a few years to move off 12.04 - free support for it ended in 2017.

There is no network upgrade path anymore.  If you can find a 14.04 ISO and install that over the 12.04, it might do an upgrade.  IDK.  You'll probably end up with a very crufty setup where  multiple config files are incompatible.  I assume this is a desktop?  The cruft is strong in desktop installs.

If you've only installed software using apt-get, then you can make a list of the manually installed programs, backup that list, important system settings and all the end-user's HOME directories.  There are probably other places you'd want to backup too, but only YOU will know them.  DBMS data is usually stored in /var/lib/{something}.  Some virtual machines are stored there too.  Some commercial programs are installed to /opt/ ...   when I manually install programs, I put them under /usr/local/, so I backup that area too.

Then you would do a fresh install of 18.04, choosing only the minimal stuff.  Then you'll need to carefully put the system settings and data back where they belong.  Many of the settings will need to be manually migrated and manually massaged.  There isn't any automatic migration for apache2 or nginx config files, for example. Then you'll take the list of manually installed packages and reinstall those. Probably 20% will be deprecated or just unavailable.  You may or may not want to make a list so newer solutions for each missing program can be researched and installed.

If you get the config migration parts wrong, you might end up with a system that doesn't boot, so be very careful and be prepared to put any settings back manually using a "Try Ubuntu" flash boot setup.  Not having a booting system would be extreme, but it is possible.

So, how willing are you to waste that time and effort doing those manual things?

There's a reason Canonical and all of the volunteers here push staying on supported releases.  There's a reason why there are always 2 LTS releases currently supported.  Gives people like you AND me time to migrate.  I had a bunch of servers on 14.04 until early this year. Migrated them to 16.04 because, for my needs, 18.04 isn't ready.

In the end, you'll probably end up wiping the OS, moving over only data and manually configuring stuff.  We've all been there.

BTW, there are other options for voice communications. You don't need skype.

---

