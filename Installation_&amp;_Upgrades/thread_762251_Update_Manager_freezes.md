---
title: "Update Manager freezes"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by Jugney on 2008-04-21
I wanted to try the Hardy RC and entered

```
update-manager --devel-release
```

at a terminal. But I made the mistake of not installing other upgrades first. (The only upgrades available were firefox, another one related to firefox, and one for opera).

Now the process is frozen at the "Distribution Upgrade" window, the one that comes up after confirming the distribution upgrade. It almost got to Downloading files for package, I think. The window is simply blank and it became grayed out almost immediately. 

I force quitted it once before and came back to it and the same thing happened. And now if I go to Update Manager it shows a long list of possible upgrades and says I need to do a partial upgrade to fix the interrupted distro upgrade. But since it doesn't seem to go anywhere when I select this option, I don't know what to do. 

I'm wondering if I'll need to reinstall from a full installation of 8.04. My only question about that would be, since a have /home on a separate partition, will all my programs be kept intact, or will I need to reinstall them but all my settings will be maintained? Hopefully this step wont be necessary, but I thought I would think ahead and ask anyway.

Can anyone help??

Jugney

---

### Post by Rocket2DMn on 2008-04-21
Try running
```
sudo dpkg --configure -a
```
Then do the partial upgrade, then the full distro upgrade.

If you do end up reinstalling fresh, you should be able to keep your /home partition, though I'm not sure what configuration issues may come up with the differences between the configs you have for current programs and the newer versions that come with Hardy.  I don't think it will be too much of an issue, if any.

---

### Post by moon2js on 2008-04-24
I have the same problem. But this is with the final release.

My update-manager says a new dist is available, and after I click, it goes and downloads two things ("Upgrading Ubuntu to 8.04 LTS"), but hangs at "Preparing to upgrade." The windows just greys itself out and doesn't do anything for hours (until I give up and restart the system). With the system restarted, it's just Gutsy with no updates needed, and I try to dist-upgrade again.

Is this what would happen if the repos are overloaded? Or do I have some other problem?

Also, can anyone point me to commandline instructions to upgrade the dist to Hardy? I'm gonna see if I can do this (troubleshoot) remotely.

I tried "sudo dpkg --configure -a" but that didn't seem to do anything whatsoever (but maybe there is a verbose setting I should have used).

---

### Post by moon2js on 2008-04-24
I just tried upgrading the distribution from a Hardy alt cd. Updater still hangs at the same place, so it's not a problem with overloaded repos, methinks.

---

### Post by Rocket2DMn on 2008-04-24
Did you make sure you fully updated your Gutsy first?
Just for kicks
```
sudo apt-get update
sudo apt-get upgrade
```
Then do your alternate cd upgrade - [https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

If you get errors from the first 2 commands, post them here, and if the update still fails, post a screenshot.

---

### Post by moon2js on 2008-04-24
Know how I can force quit the update-manager to release the lock?

I don't know another way other than rebooting, and that takes my slow computer like ten minutes (it seems).

I did check to make sure my Gutsy was fully updated each time before I started the distribution upgrade. And it reports fully up-to-date, but that darn dist-upgrade hangs. I should try from the commandline so I can see at what precise point it's hanging.

---

### Post by purplenite on 2008-04-24
As far as I know these problems are related to overloaded repos. Many people cannot access us.archive.ubuntu.com right now. When update manager attempts to access the repos there it freezes. Should be fine once the rush to upgrade is over.

---

### Post by moon2js on 2008-04-24
I thought the same thing, but I tried the distribution upgrade that pops up when you insert an alt CD, and it hangs at the same point -- without trying to access overloaded repos.

---

### Post by jedimasterk on 2008-04-24
At what point does it hang?.

---

### Post by moon2js on 2008-04-24
It hangs early on, soon after entering admin password, on the first item in the checklist: "Preparing to upgrade."

I'm trying to figure out how to try upgrading from the commandline because maybe there will be some clue as to what is choking.

---

### Post by anuban on 2008-04-24
It just doesn't start.  I was running FF3 on a clean install Hardy.  I needed a Java 5.0 plugin.  I tried to install it that requires 6 downloads.  But it didn't even start at one.  Finally I had to cancel it.  It showed me errors being not able to fetch data from the servers specially the one mentioned above.
I think it is because of overloaded servers.
Hope that much information helps someone to fix this.

Thanks

---

### Post by denham2010 on 2008-04-24
Do you have any 3rd party repositories in your sources.list?

The update process will crash with 3rd party repo's.

I had this problem upgrading to Gutsy, and again trying to get the Hardy upgrade going.

Once I backed up my sources.list and then changed it back to just the default repo's (don't just inactivate them, you need to delete them from your sources.list) the upgrade process stopped locking up.

My updater is downloading the new packages now.....1168 or 1603...and counting.....

---

### Post by cayhorstmann on 2008-04-25
FWIW, here is a screen shot of an upgrade just before it hangs. I invoked it with  gksu "sh /cdrom/cdromupgrade"

---

### Post by moon2js on 2008-04-25
@cayhorstmann: that's exactly where my upgrade hangs.

And the visual effects grey out that window within a second or two.

I tried disabling all the third-party repos in synaptic, then I tried upgrading from the alt CD: same hanging at same place.

Next I tried removing third-party repos from synaptic, and now I'm trying to upgrade from the alt CD and it didn't hang at that same place. It asks if I want to check for the lastest online updates online and I click NO. But at the very next item on the checklist (as pictured in the above screenshot), it gave me the error message:

[INDENT]Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
[/INDENT]

OK, and upgrade continues. Next time I see the screen, and all the signs of upgrade are gone, no windows or messages or alerts of completion though. But I see hundred of updates are available with the little star. I disable all online repos and force it to grab packages from CD. Now it's working on that, and once they've been installed, I'll switch back to online repos for the rest and hope it all works.

*crossed fingers*

so in short, totally removing those third-party repos has let me get further in the upgrade with hiccups. It may even work now. I'll let you know once everything's installed and I restart the system.

---

### Post by moon2js on 2008-04-25
...and no dice.
```

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 124154 files and directories currently installed.)
Preparing to replace human-theme 0.9 (using .../human-theme_0.18_all.deb) ...
Unpacking replacement human-theme ...
dpkg: error processing /cdrom//pool/main/h/human-theme/human-theme_0.18_all.deb (--unpack):
 trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver
Errors were encountered while processing:
 /cdrom//pool/main/h/human-theme/human-theme_0.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I feel like it's getting my leftover gutsy packages confused with the hardy ones.

---

### Post by cayhorstmann on 2008-04-25
Following [this bug report]("https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/152296"), I got a bit further with this procedure:
[LIST=1]
[*]As superuser, ```
cd /tmp ; rm -rf tmp*
```
[*]Insert the alternate CD ROM
[*]If the autorun dialog comes up, select the upgrade option. Otherwise, run ```
sudo sh /media/cdrom/cdromupgrade
```
[*]The program hangs in step 1. (If it doesn't hang for you, 
then that's great, and you can stop reading this.)
[*]```
cd /tmp/tmp*
```
[*]```
sudo ./hardy --frontend=DistUpgradeViewText --cdrom=/media/cdrom
```
[/LIST]
You'll get this **text** output:
```
Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Include latest updates from the Internet? 

The upgrade process can automatically download the latest updates and 
install them during the upgrade. The upgrade will take longer, but 
when it is complete, your system will be fully up to date. You can 
choose not to do this, but you should install the latest updates soon 
after upgrading. 

```
At this point, there presumably should have been a prompt, but I didn't get any. I boldly hit the ENTER key, and got
```
Yes
```
Then the program proceeded. It might have been better to try to answer No because the internet download is so slow right now. Maybe someone can try this and report how it works.

---

