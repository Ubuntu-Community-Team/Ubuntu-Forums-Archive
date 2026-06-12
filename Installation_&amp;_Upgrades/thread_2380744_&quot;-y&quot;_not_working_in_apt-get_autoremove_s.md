---
title: "&quot;-y&quot; not working in apt-get autoremove script"
date: 2017-12-21
forum: Installation &amp; Upgrades
---

### Post by accounts0 on 2017-12-21
I have this line in a script that runs with sudo:

```
aptitude update && sudo aptitude -y upgrade && sudo apt-get -y autoremove
```

However when it comes time to do the autoremove it waits for me to press <Enter> or <Y> instead of doing a force yes like the command says to.

If I run ```
sudo apt-get -y autoremove
``` ...on its own, it proceeds without user input like it should. Just not in my script for some reason.

I tried creating a new .sh file (with chmod +x) to call from the one where its not running properly- calling it like so:

```
sudo konsole -e "~/Scripts/AptitudeAutoremove.sh"
```

But this doesn't work at all.

---

### Post by ian-weisser on 2017-12-21
unattended-upgrades will do all that (including autoremove). Do you have it installed?

---

### Post by accounts0 on 2017-12-21
> **ian-weisser said:**
> unattended-upgrades will do all that (including autoremove). Do you have it installed?


Yes, but I've never got it working right.

This is my /etc/apt/apt.conf.d/50unattended-upgrades (I think it's right):

```
[FONT=monospace][COLOR=#000000]// Automatically upgrade packages from these (origin:archive) pairs[/COLOR]
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESM:${distro_codename}";
        "${distro_id}:${distro_codename}-updates";
        "${distro_id}:${distro_codename}-proposed";
        "${distro_id}:${distro_codename}-backports";
};

// List of packages to not update (regexp are supported)
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
        "thunderbird";
        "thunderbird-locale-en"

};

// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "false";

// Split the upgrade into the smallest possible chunks so that
// they can be interrupted with SIGUSR1. This makes the upgrade
// a bit slower but it has the benefit that shutdown while a upgrade
// is running is possible (with a small delay)
Unattended-Upgrade::MinimalSteps "true";

// Install all unattended-upgrades when the machine is shuting down
// instead of doing it in the background while the machine is running
// This will (obviously) make shutdown slower
//Unattended-Upgrade::InstallOnShutdown "true";

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. A package that provides
// 'mailx' must be installed. E.g. "user@example.com"
//Unattended-Upgrade::Mail "root";

// Set this value to "true" to get emails only on errors. Default
// is to always send a mail if Unattended-Upgrade::Mail is set
//Unattended-Upgrade::MailOnlyOnError "true";

// Do automatic removal of new unused dependencies after the upgrade
// (equivalent to apt-get autoremove)
Unattended-Upgrade::Remove-Unused-Dependencies "true";

// Automatically reboot *WITHOUT CONFIRMATION*
//  if the file /var/run/reboot-required is found after the upgrade
Unattended-Upgrade::Automatic-Reboot "false";

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";

// Use apt bandwidth limit feature, this example limits the download
// speed to 70kb/sec
//Acquire::http::Dl-Limit "70";
[/FONT]
```

---

### Post by accounts0 on 2018-01-01
bump

---

### Post by ian-weisser on 2018-01-02
I recommend against enabling automatic updates from -proposed. Down that path lies breakage.
Other than that, the config looks fine.

Are you saying that automatic updates have some problem? Or are not running?
What is the problem you are having?

---

### Post by accounts0 on 2018-01-02
> **ian-weisser said:**
> Are you saying that automatic updates have some problem? Or are not running?

Exactly. Current state has no effect. I suspect something about cron not being set right. Seem to remember readibg something about enabling some sort of 'daily' preset file but am not sure.

---

### Post by ian-weisser on 2018-01-02
Please show us the complete output of the following:
```
ls -l /var/lib/apt/periodic/
systemctl list-timers | grep apt
```

The first lists the timestamps of many apt actions, a handy tool to see when unattended-upgrade last ran.
The second lists today's scheduled run time for unattended-upgrade.

---

### Post by accounts0 on 2018-01-04
> **ian-weisser said:**
> Please show us the complete output of the following:
```
ls -l /var/lib/apt/periodic/
```


```

-rw-r--r-- 1 root root 0 Jan  3 08:53 autoclean-stamp
-rw-r--r-- 1 root root 0 Jan  4 18:00 download-upgradeable-stamp
-rw-r--r-- 1 root root 0 Jan  4 18:00 unattended-upgrades-stamp
-rw-r--r-- 1 root root 0 Jan  4 18:00 update-stamp
-rw-r--r-- 1 root root 0 Jan  4 21:20 update-success-stamp
-rw-r--r-- 1 root root 0 Jan  4 18:00 upgrade-stamp

```

> **ian-weisser said:**
> ```
systemctl list-timers | grep apt
```


```

Fri 2018-01-05 06:35:21 EST  9h left     Thu 2018-01-04 18:00:37 EST  3h 22min ago apt-daily-upgrade.timer      apt-daily-upgrade.service
Fri 2018-01-05 14:28:41 EST  17h left    Thu 2018-01-04 18:00:37 EST  3h 22min ago apt-daily.timer              apt-daily.service

```

---

### Post by ian-weisser on 2018-01-05
Unattended Upgrades is installed, running, and successfully completing it's runs.

Here's how we know that:
> [COLOR=#000000][FONT=&amp]-rw-r--r-- 1 root root 0 Jan  4 18:00 unattended-upgrades-stamp[/FONT][/COLOR]
The stamp only places upon successful completion.

Next step, please show us the contents of /var/log/unattended-upgrades/unattended-upgrades.log
Edit the output so it contains output only from Jan 4.

---

### Post by accounts0 on 2018-01-05
> **ian-weisser said:**
> Unattended Upgrades is installed, running, and successfully completing it's runs.

Here's how we know that:

The stamp only places upon successful completion.

Next step, please show us the contents of /var/log/unattended-upgrades/unattended-upgrades.log
Edit the output so it contains output only from Jan 4.


Unfortunately the only content is from today it seems:

```
[FONT=monospace][COLOR=#000000]2018-01-05 06:35:34,189 INFO Initial blacklisted packages: thunderbird thunderbird-locale-en[/COLOR]
2018-01-05 06:35:34,189 INFO Initial whitelisted packages:  
2018-01-05 06:35:34,190 INFO Starting unattended upgrades script
2018-01-05 06:35:34,190 INFO Allowed origins are: ['o=Ubuntu,a=xenial', 'o=Ubuntu,a=xenial-security', 'o=UbuntuESM,a=xenial', 'o=Ubuntu,a=xenial-updat
es', 'o=Ubuntu,a=xenial-proposed', 'o=Ubuntu,a=xenial-backports']
2018-01-05 06:35:37,929 INFO No packages found that can be upgraded unattended and no pending auto-removals[/FONT]
```

I tend to not leave it on...

---

### Post by ian-weisser on 2018-01-06
Unattended Upgrades seems to be working properly on your system.

If you have reason to believe otherwise, check the systemd timer for the daily-run-time, then check the timestamp for corresponding successful compltetion, then check the log to see what packages it did.

If you identify packages that aren't getting upgraded automatically, then look to see what source they are coming from. See if that source is enabled in the config file.

Those are the troubleshooting steps that solve 90% of u-u problems.

Again, automatic upgrade from the -proposed repository is discouraged. -proposed packages are for testing, and may break your system. Yours is enabled.

---

### Post by accounts0 on 2018-01-07
> **ian-weisser said:**
> 
Again, automatic upgrade from the -proposed repository is discouraged. -proposed packages are for testing, and may break your system. Yours is enabled.


Ok, so here's how I've edited the config. Just want to post it here to double-check it's right- something about commenting with "/" instead of "#" makes me a bit worried. Assuming this is correct here?

```
// Automatically upgrade packages from these (origin:archive) pairsUnattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESM:${distro_codename}";
        "${distro_id}:${distro_codename}-updates";
        //"${distro_id}:${distro_codename}-proposed";
        "${distro_id}:${distro_codename}-backports";
};
```


> **ian-weisser said:**
> Unattended Upgrades seems to be working properly on your system.


If you have reason to believe otherwise, check the systemd timer for the daily-run-time, then check the timestamp for corresponding successful compltetion, then check the log to see what packages it did.

Is there a way to have it run every 3 hours?


At the moment I have that script I mentioned earlier running every logon, plus I have an hourly "aptitude update" cron job that switches the tray icon to red if there's anything to do. At that point I run the launcher to have that script do it.

---

### Post by ian-weisser on 2018-01-07
Your config looks good.
Unattended-upgrades is intended to run daily or weekly.
I suppose you can cronjob u-u to run more often if you really want to. I see no benefit to do such, but it's not my system.
Remember to disable the existing daily apt cronjob.

---

