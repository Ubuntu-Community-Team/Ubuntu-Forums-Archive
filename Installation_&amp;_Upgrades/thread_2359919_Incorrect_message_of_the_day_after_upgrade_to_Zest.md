---
title: "Incorrect message of the day after upgrade to Zesty"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by steve233 on 2017-04-29
After upgrading my server to Zesty I get the following from motd every time I log in:
```
Ubuntu 17.04
zesty


Ubuntu 12.04 LTS end-of-life was April 28, 2017 -- Upgrade your Precise systems!
 $ sudo do-release-upgrade -m server


0 packages can be updated.
0 updates are security updates.


Failed to connect to http://changelogs.ubuntu.com/meta-release. Check your Internet connection or proxy settings

```

Everything seems up to date. Can anyone help me figure out how to get motd to update itself?
Thanks.

---

### Post by ian-weisser on 2017-04-29
Look in /etc/update-motd.d/

---

### Post by steve233 on 2017-04-29
Checked in there. Looks like the usual scripts are present. Running them produces the same output I see when I log in.
[COLOR=#34BC26][FONT=Menlo]**00-header  ****90-updates-available  ****95-hwe-eol  ****98-fsck-at-reboot**[/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo]**50-motd-news  ****91-release-upgrade  ****97-overlayroot  ****98-reboot-required**[/FONT][/COLOR]

---

### Post by m-d-d on 2017-04-29
I have same message after upgrading to Zesty.

---

### Post by ian-weisser on 2017-04-30
Try sudo /usr/sbin/update-motd

---

### Post by steve233 on 2017-04-30
I'm missing all of these files in Zesty:
/usr/sbin/update-motd
/etc/motd
/var/run/motd[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by steve233 on 2017-04-30
I've fixed my problem but I would love some feedback as to whether this is the correct fix.
It appears to me that /etc/update-motd.d/50-motd-news is using a cached file to read current info from.
I cleared the contents of that cached file and no longer receive the incorrect message during login.
The following will clear it:
```
> /var/cache/motd-news
```

Then you can check that it is gone by running:
```
sudo run-parts /etc/update-motd.d/
```

---

### Post by ian-weisser on 2017-04-30
> **steve233 said:**
> I'm missing all of these files in Zesty:
/usr/sbin/update-motd
/etc/motd
/var/run/motd[COLOR=#242729][FONT=Consolas]
[/FONT][/COLOR]

Reinstall the 'update-motd' package.

---

### Post by m-d-d on 2017-05-02
> **steve233 said:**
> I've fixed my problem but I would love some feedback as to whether this is the correct fix.
It appears to me that /etc/update-motd.d/50-motd-news is using a cached file to read current info from.
I cleared the contents of that cached file and no longer receive the incorrect message during login.
The following will clear it:
```
> /var/cache/motd-news
```

Then you can check that it is gone by running:
```
sudo run-parts /etc/update-motd.d/
```

Thank you! This indeed fixed incorrect message about server upgrade. BTW my update-mod package was correctly installed. This must be some artifact left from multiple system upgrades.

---

