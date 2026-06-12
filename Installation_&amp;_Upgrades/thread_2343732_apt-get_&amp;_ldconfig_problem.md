---
title: "apt-get &amp; ldconfig problem"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by edwardLS on 2016-11-18
Running ubuntu 16.04 and having to deal with FAP (Fair Access Policy). I am not a guru, just a dedicated user.

In order to check for and download/install updates during FAP Free time, I have:
sudo crontab -e, and added the following entry -

# check/download/install at 2:00 AM
0 2 * * * (/usr/bin/apt-get update && /usr/bin/apt-get -y upgrade) > /home/edward/apt.log

This results in the following at the end of my log file:
dpkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable
dpkg: error: 2 expected programs not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin

If I run the same commands using 'sudo' in a terminal, I do not get the warnings.

I have been searching for a solution, and as best I can determine, my root $PATH is correct, and ldconfig is at /sbin/ldconfig and executable. Am I doing something obviously wrong? Can anyone give me some help?

---

### Post by Impavidus on 2016-11-18
When you run something from crontab, your environment is extremely limited. Your PATH is not defined. You can run a command as```
PATH=/your/path:/your/other/path command
```or you can put everything, including the PATH, into a shell script and use crontab to run that shell script.

---

### Post by ian-weisser on 2016-11-18
Here's another way that uses your system's already inbuilt features.

1) Remove all your prior attempts

2) Disable the /etc/cron.daily/apt-compat job to prevent apt checking for updates at the wrong time.

3) Add a root cron job at 0200 that simply runs 'exec /usr/lib/apt/apt.systemd.daily' . This, in turn, runs the unattended-upgrades application, which logs to /var/log

4) Check /etc/apt/apt.conf.d/20auto-upgrades: The unattended-upgrades flag should be '1'.

5) Edit /etc/apt/apt.conf.d/50unattended-upgrades (using sudo); Uncomment (enable) the Allowed-Origins for -updates and -backports. Add any PPAs or other non-Ubuntu repos that you want Unattended Upgrades to use.

---

