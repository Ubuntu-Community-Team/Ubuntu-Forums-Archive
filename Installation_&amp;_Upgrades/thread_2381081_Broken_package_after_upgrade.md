---
title: "Broken package after upgrade"
date: 2017-12-26
forum: Installation &amp; Upgrades
---

### Post by timswait on 2017-12-26
I've just upgraded my kubuntu system to 17.04. The installer seemed to finish but then quit with an error saying the upgrade hadn't been completed and the system might by unusable. The good news is that the system seems perfectly usable and lsb_release -a is showing me as being on 17.04. However I have a broken package called systemd-shim that I just can't fix. I would just ignore it, but it seems to be preventing me from doing any updates or installing anything so I could really do with getting rid of it or reinstalling it if it's necessary. I've tried apt-get upgrade (with and without -f), dpkg --configure -a, apt-get clean, apt-get autoclean, apt-get autoremove. All give pretty well the same error (shown below). What can I do now?

```
mt1tjs@mt1tjs-Precision-M4600:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  systemd-shim
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 71.7 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 317322 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by #&amp;thj^% on 2017-12-26
Just wanted to mention that 17.04 has about 1 month left for support. "April 13, 2017 to January 2018"
16.04 is supported to April 2021
17.10 is a point release supported for about 9 months till July 2018 
Now if you still want to continue let us know.

---

### Post by timswait on 2017-12-26
I'd like to get to 17.10 really, but apparently "The download of Kubuntu 17.10 is currently discouraged due to an issue on certain Lenovo laptops." (from [https://kubuntu.org/getkubuntu/](https://kubuntu.org/getkubuntu/) ) so I would really like to get the 17.04 working and then go to 17.10 when it becomes available. Thanks

---

### Post by #&amp;thj^% on 2017-12-26
Well updating an existing installation and upgrading to 17.10 is safe as it will pull in a fixed kernel. (So I'm Told)
That Said moving forward then.
When this happens to me>> Using the terminal command:

    ```
sudo mv <original file name> <new file name>
```

 **rename** /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.bak.

    Proceed to run "sudo apt upgrade" again.

Hopefully no more systemd-shim errors should appear.

Rename the file back to what it was if you have any issues.

---

### Post by timswait on 2017-12-26
Brilliant, that's worked, thank you! The updates tab is telling me my system is up to date and not telling me there's any new distribution available, which I was assuming was because 17.10 had issues?

---

### Post by #&amp;thj^% on 2017-12-26
Great glad that worked out! ;)
To error on the safe side I would wait then....Til we get a **All Clear for 17.10.**
Or if you get bored and want to experiment with 17.10...LOL
Cheers

---

