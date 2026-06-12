---
title: "Upgrade Ubuntu 12.04 amd64 to 14.04 does not work on Sony viao laptop model VPC"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by cx19642 on 2014-07-29
Someone gave me advice to upgrade my Sony viao laptop model  VPCF13Z1E with Intel I7  from Ubuntu 12.04 LTS to 14.04 when Ubuntu 14.04.1 is available.
Lately I saw on Distrowatch that Ubuntu 14.04.1 is available.
But when I start Update manager in 12.04.4 LTS I do not see 14.04.1  LTS.

I if run Ubuntu 14.04 amd64 from a 14.04 amd install CD/DVD everything works well (Wifi, audio, video, youtube etc works well).
I Also can run Ubuntu 14.04 amd64 perfectly as a guest OS from Virtualbox.

What am I doing wrong?
I can I perform a save upgrade on my Sony viao laptop model  VPCF13Z1E with Intel I7 from 12.04 tot 14.04?

Please help!

---

### Post by Bashing-om on 2014-07-29
cx19642; Hi !

As there presently exists a bug in respect to the Hardware Enablement Stack .. a lot depends on what kernel you have installed in 12.04.
Before proceeding or offering advise, we need to know if you are effected.
Post back the output of terminal commands:
```

uname -a
lsb_release -a

```

Then again, there may be other factors - for instance, phased updates are in effect .

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-07-29
cx19642; Good news !

I stand corrected, as of 7 hours ago the 2 major bugs have been squashed.

Please see/JOIN thread:
[http://ubuntuforums.org/showthread.php?t=2236514](http://ubuntuforums.org/showthread.php?t=2236514)
If you are still not able to do the release upgrade.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by cx19642 on 2014-07-30
**uname -a gives:**
Linux SonyVaioF1 3.2.0-67-generic #101-Ubuntu SMP Tue Jul 15 17:46:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

**lsb_release -a gives:**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

cx19642

---

### Post by cx19642 on 2014-07-30
**On my machine uname -r gives:**
3.2.0-67-generic

Is this the cause of the problem?

---

### Post by cx19642 on 2014-07-30
**On my machine "grep prompt= /etc/update-manager/release-upgrades" gives:**
prompt=lts

Thus, is my 3.2.0-67-generic kernel a problem?

---

### Post by Bashing-om on 2014-07-30
cx19642; Hey !

Nope, kernel " 3.2.0-67-generic" is the original non-messed with HES, so none of the bugs apply.
"/etc/update-manager/release-upgrades" is valid for the release upgrade .. 
Should workie ...->
Try:
```

sudo do-release-upgrade

```
See if from terminal it is effective // thereby bypassing the phased update structure within the update manager.

[INDENT][INDENT]we poke at it 'til
[INDENT][INDENT][INDENT]it is 14.04
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cx19642 on 2014-07-30
If i do 

sudo do-release-upgrade

I get the message no release found.

---

### Post by Bashing-om on 2014-07-30
cx19642; Yuk !

Not acceptable to say "I do not know" .

So, I say, I am actively engaged in trying to find a reason.

I will advise furthers, soonest.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-07-31
cx19642; Hey;

With some amount of uncertainty, let's try this approach:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` to insure all is up to date, and set to go;
Then do - paying close attention to what the package manager is going to do -:
```

sudo do-release-upgrade -p

```Where the "release type tag" 'p' is for proposed. See if that will not force the release upgrade to 14.04.1....

The best I can tell ->
[INDENT][INDENT][INDENT]should workie
[/INDENT][/INDENT][/INDENT]

---

### Post by cx19642 on 2014-07-31
sudo  do-release-upgrade -p

is doing something.
There are now trusty files fetches (output is seen with text like "get:nummer URL ..")
Now I have to wait, to see  it works.

---

### Post by dunn2 on 2014-07-31
I had an older sony vaio, and that thing wouldnt take to any linux distro i threw at it. I think something was up with the bios that wasnt supported. 
I dont know if this helps or not but. ;)

---

### Post by kansasnoob on 2014-07-31
> **cx19642 said:**
> sudo  do-release-upgrade -p

is doing something.
There are now trusty files fetches (output is seen with text like "get:nummer URL ..")
Now I have to wait, to see  it works.

I won't be surprised if it results in partial, or even total borkage - the Precise -> Trusty release upgrades were disabled for reasons - some of which are only partly resolved!

---

### Post by Bashing-om on 2014-07-31
@ kansasnoob;

Me too ! wanting to understand what is going on. Maybe in fixing the bugs you have reported, other mechanics have become broken ?


[INDENT][INDENT]be nice to know
[/INDENT][/INDENT]

---

### Post by cx19642 on 2014-08-01
The suggested "sudo do-release-upgrade -p" caused al lot of activity

I first got some message (someting with partial .. and someting with packages ), I did not get enouch time to write it down.
Then some process started with downloading files, configuring and installing of packages.
This process took about 3 hours to finish.
After this process was finished, I had to reboot my Sony.
After the reboot I dit not have a desktop.
Then I rebooted an other time (now in recovery mode). But Again I did not get a visual desktop.

After this, I restored my clonezilla backup with 12.04.4.

**I am still wondering why this upgrade does not work.**

I know that that ubuntu 14.04 amd64 is able to work on my Sony, because I run from an install disk or usb stick. Then everything works (audio, video, WiFi etc).
So when I do a clean install, I think it will work.
But I have a lot of software installed and configured, so I can only go tot 14.04 via an upgrade.
[B]
Is there someting wrong with my Sony and my installed 12.04.4 Ubuntu software, or is there someting wrong with the upgrade software[/B]?

I am now trying an 12.04.4 to 14.04 upgrade under Virtualbox on my Sony, to see what is process does.
It is for me quicker/easier to experiment under Virtualbox then under my native OS.

**What information do I have to give to have this solved?**

---

### Post by cx19642 on 2014-08-01
On Virtualbox my upgrade from 12.04.4 amd tot 14.04 with sudo do-release-upgrade -p

gives these messages:

(gtk-update-icon-cache:32268): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:32269): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for man-db (2.6.1-2ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-gi_3.12.0-1ubuntu1_amd64.deb
Error in function: 


A fatal error occurred 

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 



Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

dpkg: error: duplicate file trigger interest for filename `/usr/lib/gtk-2.0/2.10.0/immodules' and package `libgtk2.0-0:amd64'
dpkg-query: error: duplicate file trigger interest for filename `/usr/lib/gtk-2.0/2.10.0/immodules' and package `libgtk2.0-0:amd64'

Upgrade complete 

The upgrade has completed but there were errors during the upgrade 
process. 

To continue please press [ENTER]

---

### Post by Bashing-om on 2014-08-01
cx19642; Yuk, once more;

No, I do not think it is your system or hardware at fault. But rather the upgrade path. I do expect these difficulties to be resolved prior to the next point release ( Aug 8) for 12.04 to 12.04.5.
As you are fully updated ( no errors reported ), update manager configured for the next LTS release, and "phased updates" - with using the terminal - are not a part of the picture, then there is a problem completing the process within the upgrade system.

If in this I am in error I am open to enlightenment.

Might I suggest that you open an additional bug report to add to the pool of knowledge for the developers to hasten the fix.

Else, await the release of 12.04.5, and try the upgrade once more.

ElseIf , as I do not know of a current "fix", fresh install 14.04 if it is your earnest desire to be at release 14.04.

[INDENT][INDENT]if I knew better.
[INDENT][INDENT][INDENT][INDENT]I would say better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-01
Please read this:

[http://ubuntuforums.org/showthread.php?t=2236514&p=13085129#post13085129](http://ubuntuforums.org/showthread.php?t=2236514&p=13085129#post13085129)

Regarding [this bug]("https://bugs.launchpad.net/ubuntu/precise/+source/update-manager/+bug/1348067") the fixed 'update-manager' packages just moved from "proposed" to "updates" yesterday in the US repos. I'm only just now performing a Precise -> Trusty upgrade test again to see what happens. I was tied up with Utopic (flavors) Alpha 2 iso/upgrade testing Wednesday and Thursday - and I do actually require sleep ;)

Regarding [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964"), to which you responded, you'll notice that in addition to saying Fix released it also shows Milestone = ubuntu 14.04.2. So, will Canonical actually wait until 14.04.2 to begin offering Precise -> Trusty upgrades through the update manager? I doubt it.

When I've completed this test, sometime later today I'll try and find out when auto-notification may begin.

I would point out one additional thing - you said:

> I have a lot of software installed and configured, so I can only go tot 14.04 via an upgrade.

If you expect all of that to survive a release upgrade you'll likely be sadly disappointed, particularly if you have packages installed via PPA.

---

### Post by kansasnoob on 2014-08-01
There is still some borkage during clean-up which is also reflected post-upgrade:

```
lance@lance-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libpostproc52
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  linux-image-3.11.0-15-generic linux-image-3.11.0-26-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 310 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 171480 files and directories currently installed.)
Removing linux-image-3.11.0-15-generic (3.11.0-15.25~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-15-generic /boot/vmlinuz-3.11.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-15-generic /boot/vmlinuz-3.11.0-15-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/disk/by-uuid/9305c825-bbef-4222-a3c8-9c87483e0592'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.11.0-15-generic.postrm line 328.
dpkg: error processing package linux-image-3.11.0-15-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.11.0-26-generic (3.11.0-26.45~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/disk/by-uuid/9305c825-bbef-4222-a3c8-9c87483e0592'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.11.0-26-generic.postrm line 328.
dpkg: error processing package linux-image-3.11.0-26-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.11.0-15-generic
 linux-image-3.11.0-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now I have to study that and see if there are already bug reports, etc, etc. There are two issues, one regarding kernel clean-up and the other regarding grub.

Are you happy now :rolleyes:

---

### Post by Bashing-om on 2014-08-01
@ kansasnoob; "Are you happy now"

Put another way: I am glad you are doing all this grunt work, and keeping us informed !

Many have no problems upgrading, some do .. where the difference is, I -would like to know.

[INDENT][INDENT]people like you
[INDENT][INDENT][INDENT]make ubuntu what it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kansasnoob on 2014-08-01
One down:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1351414](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1351414)

Must eat :lolflag:

---

### Post by kansasnoob on 2014-08-01
> **Bashing-om said:**
> @ kansasnoob; "Are you happy now"

Put another way: I am glad you are doing all this grunt work, and keeping us informed !

Many have no problems upgrading, some do .. where the difference is, I -would like to know.

[INDENT][INDENT]people like you
[INDENT][INDENT][INDENT]make ubuntu what it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

It's my thing good friend :D

It beats building jig saw puzzles :lolflag:

---

### Post by cx19642 on 2014-08-01
After I rollback my Virtual my upgrade on Virtualbox I repeated the upgrade with sudo do-release-upgrade -p.
Now I discovered that after the message mention in previous replay, I now discovered the the upgrade had crashed, because I can't shutdown my Ubuntu VM.
I also can't even start a new command shell to shutdown ubuntu.

I think there is something wrong with the upgrade proces and nothing with my Sony (the same Bashing-om already said).

**Apart of to wait till august 7th for ubuntu 14.04.2 and 12.04.5,  what kind for information can I supply for a bug report?**

By my opinion in my previous post I did not give any special information (I do not have any relevant log file. Because I restored my backup, I can't give
any important log now).

**Is it worthwhile to repeat the 3 hour upgrade proces on my Sony to get important log files?** Afterwards, when I have the log files I can restore my backup.
**Which log files do I have to attach on this bug report?**

kansasnoob and Bashing-om, thanks for your help till now

---

### Post by kansasnoob on 2014-08-01
I'm using the command:

```
update-manager -d -c
```

Per QA instructions:

[http://iso.qa.ubuntu.com/qatracker/testcases/1635/info](http://iso.qa.ubuntu.com/qatracker/testcases/1635/info)

But the process is still buggy ;)

I'd bet that once the process is debugged successfully by Canonical the offer to upgrade will be offered via update manager as it should.

You can read about reporting bugs here:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by cx19642 on 2014-08-01
**Is it an idee, to remove all packages with a LP-PPA orgin?**
I just found out, that "Synaptic Package Manager" has a option (Orgin) , which I can use to find packages from a specific LP-PPA.
In this way I can remove all packages which have a LP-PPA orgin. I can register, which packages I have installed with I LP-PPA, so I can reinstall al those packages after the upgrade.

Up till now, I didn't know it wasn't smart to use LP-PPA packages from. So in future, I have to decide if I want to risk to use these packages.

[B]Is it worthwhile to try to remove all packages with a LP-PPA origin?
Or should I wait for 12.04.5 and 14.04.2, for my next upgrade attempt?
[/B]
I also have an other question about 12.04.5. I have read 12.04.5 is a release for users who are not oir can't upgrade to 14.04.[B]
So, my question is, If I upgrade from 12.04.4 to 12.04.5, can I still upgrade to 14.04.x?
[/B]What means, that I have to avoid installing 12.04.05.[B]
By the way, how can I see that I am installing 12.04.5?

[/B]

---

### Post by kansasnoob on 2014-08-01
If this is a server system the QA process is different:

[http://iso.qa.ubuntu.com/qatracker/testcases/1310/info](http://iso.qa.ubuntu.com/qatracker/testcases/1310/info)

---

### Post by kansasnoob on 2014-08-01
12.04.5 is due the end of next week

14.04.2 is not due for about six months, very little going on there yet:

[https://launchpad.net/ubuntu/+milestone/ubuntu-14.04.2](https://launchpad.net/ubuntu/+milestone/ubuntu-14.04.2)

The upgrade process is just borked ATM. Either be patient or perform a fresh install.

BTW if you wait and install 14.04.2 then you'll end up having to deal with HWE EOL later on.

---

### Post by cx19642 on 2014-08-01
I just read [https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
so I was not aware of 14.04.2 = 14.10

Because 14.04.2 is not a good option, I may give it a next try on next week with 12.04.5.

I still want to know, if it is also I good idea to remove all packages with a LPA-PPA origin, so I have an other alternative before next week to try.
**So is removing all packages with a LPA-PPA origin a good starting point for a upgrade from 12.04.4 tot 14.04?**

---

### Post by cx19642 on 2014-08-01
[B]And if I remove all packages with a LPA-PPA origin as a good starting point for a upgrade from 12.04.4 tot 14.04, should I use the command 
sudo do-release-upgrade -d -c plus the upgrade button, to start the upgrade process properly?[/B]

---

### Post by cx19642 on 2014-08-01
[B]And if I remove all packages with a LPA-PPA origin as a good starting point for a upgrade from 12.04.4 tot 14.04, should I use the command 
sudo do-release-upgrade -d -c plus the upgrade button, to start the upgrade process properly?[/B]

---

