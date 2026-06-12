---
title: "xubuntu hangs on startup after updating to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by qlum on 2011-10-14
xubuntu hangs on startup after updating to 11.10.
it hangs in the bootscreen after I updated, I tried the repair options in recovery mode but they also where not able to fix anything. I did get some errors when updating after which it aborted. But I was unable to fulfill the reboot after than and it keeps getting stuck on startup every time. Is there any possible way to fix this/ Google didn't help me on that account. one of my errors, the only one I can remember was regarding the flash plugin.

---

### Post by ankspo71 on 2011-10-14
Hi,
It sounds like your upgrade didn't complete successfully, so boot into recovery mode again, and choose the option that says "netroot - drop to shell with networking". The use these commands to complete the upgrade:

**Step 1:**
```
sudo apt-get update
sudo apt-get dist-upgrade

```

Now reboot and see if the problem is still there:
```
sudo reboot
```

**Step 2: (if necessary)**

**A.** If the commands in Step 1 complain about broken or missing dependencies, then run this command:
```
sudo apt-get dist-upgrade --fix-missing
```

**B.** If the commands in Step 1 complain that 'dpkg was interrupted' then run this command:
```
sudo dpkg --configure -a
```

Now repeat Step 1 again to complete the upgrade.

**Step 3:**
If your system still fails to boot, then the problem could be that something is failing to load during startup. I think you can press the "esc" key during the boot splash screen to see if there are any errors reported during the boot process.

---

### Post by qlum on 2011-10-15
I tried that before but than I got some read only like errors which I now was able to fix. I didnt see the option that did that in the menu, now that its fixed it still wont work. as I am having problems with the flashplugin not installing nor uninstalling (sudo apt-get remove flashplugin-installer) I dont know if thats the right way to get rid of it, installing flashplugin-nonfree also didnt work. The error it keeps giving me whenever I try to upgrade the distro or when I tried to remove the flashplugin is:
```
Resolving archive.canonical.com... failed: Name or service not known.
wget: unable to resolve host address 'archive.canonical.com'
download failed
The Flash plugin is NOT installed.
dpkg: error processing flashplugin-downloader (--configure):
  subprocess installed post-installation script returned error exit status 1
errors were encountered while processing:
 flashplugin-downloader
E: Sub-process /usr/bin/dpkg returned an error code (1)
```the second part of the error also happens on the command you posted in step 2.

pressing escape didnt work on the boot splash screen as the thing freezed as soon as it got there. however I was able to get it by pressing it earlier and it showed no error at all.

---

### Post by ankspo71 on 2011-10-15
Hi,
This problem is reported as a bug here:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/870643](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/870643)
There are also several duplicates of the bug on the right side of that page.


Here is another possible duplicate:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/859373](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/859373)
(See post 12, a fix is on the way in the Oneiric proposed repository)

Here are some tips to recover from this type or error:
[http://journalxtra.com/2010/03/fixing-the-dreaded-errors-were-encountered-while-processing-errors/](http://journalxtra.com/2010/03/fixing-the-dreaded-errors-were-encountered-while-processing-errors/)

---

### Post by qlum on 2011-10-15
The fix worked, thanks for all your help.

---

### Post by scania_gti on 2011-10-16
My xubuntu boot always stoping at "waiting network configuration"
Fix that with [COLOR=red]sudo dpkg-reconfigure kdm
[/COLOR]

---

