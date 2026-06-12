---
title: "Firefox upgrade"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by bostjanv on 2010-07-13
Hello,
I recently noted that my Update Manager downloaded (and presumably installed) some files with names containing Firefox 3.6.6. However, when I checked the About item in my Help menu item, I still get the version as 3.6.3. Furthermore, when I select Check for updates in Help, I get the answer that an update is available. How do I upgrade to Firefox 3.6.6?
Regards,
bostjanv

---

### Post by tommcd on 2010-07-13
To make sure you have all the updates, run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```

What version of Ubuntu are you using? The latest version is 10.04:
Post the output of:
```
apt-cache policy firefox
```
It should list the installed version of firefox, as well as the latest version (listed as candidate) available in the Ubuntu repos.
If you were using firefox when the update was run, you will need to restart firefox for the update to take effect.

---

### Post by bostjanv on 2010-07-16
Hello,
Thanks for replying. The reason I didn't respond to your post earlier is that I am talking about a computer that I don't use every day.  The output of the command

apt-cache policy firefox

is

bostjan@wwpecker-3:~$ apt-cache policy firefox
firefox:
  Installed: 3.6.6+nobinonly-0ubuntu0.10.04.1
  Candidate: 3.6.6+nobinonly-0ubuntu0.10.04.1
  Version table:
 *** 3.6.6+nobinonly-0ubuntu0.10.04.1 0
        500 [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
        100 /var/lib/dpkg/status
     3.6.3+nobinonly-0ubuntu4 0
        500 [http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/) lucid/main Packages

So apparently firefox 3.6.6 is installed yet when I run firefox on the command line and click Help --> About Mozilla Firefox I get version 3.6.3. I notice that there is a directory /usr/lib/firefox-3.6.6, yet when I enter /usr/lib/firefox-3.6.6/firefox on the command line and click Help --> About Mozilla Firefox, I get the same message about version 3.6.3.
Regards,
bostjanv

---

### Post by tommcd on 2010-07-16
Hmmm, that is exactly what I get when I run "*apt-cache policy firefox*", except that my Ubuntu mirror is different, since I am in the USA.
Did you try running:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
This will make sure you have all the updates.
Try renaming your *~/.mozilla* directory to *~/.mozilla.bak*. Then restart firefox and check the version number. The ~/.mozilla directory will be recreated when you relaunch firefox. This will create a new pristine firefox profile for you. Perhaps there is something wrong with your current profile or one of your addons or something.
If this doesn't help then just delete the the new ~/.mozilla and rename ~/.mozilla.bak to ~/.mozilla, and you will have your old profile back.
I don't know why you are having this problem. Other threads on updating to firefox  3.6.6 don't mention this from what I can find:
[http://swiss.ubuntuforums.org/showthread.php?t=1520842](http://swiss.ubuntuforums.org/showthread.php?t=1520842)
[http://ubuntuforums.org/showthread.php?t=1519687](http://ubuntuforums.org/showthread.php?t=1519687)
Are you using the *standard Ubuntu repos only*? Or have you added a ppa repo for firefox added to your */etc/apt/sources.list*???

---

