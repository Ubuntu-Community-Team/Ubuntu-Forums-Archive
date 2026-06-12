---
title: "Running automatic updates and reboot daily"
date: 2023-12-07
forum: Installation &amp; Upgrades
---

### Post by dimitri6 on 2023-12-07
Hi all.
I'm looking for a way to automate the update process of my shared cloud server and reboot, every day at 3am.

I'm running Ubuntu Server 20.04.6 LTS

To facilitate the update process, I have entered once the following code in my Ubuntu Cloud Server:

```
echo "sudo apt update && sudo apt -y upgrade && sudo apt -y dist-upgrade && sudo apt -y autoremove && sudo apt autoclean" > update && sudo mv update /usr/local/bin/update && sudo chmod +x /usr/local/bin/update
```

and whenever I want to update, I log-in via SSH and type in the terminal:
```
update
```

then, when update is done, I type
```
reboot
```
<enter>.

done.

I do this almost every day.

I'm running an Icecast for live radio stream, and 3 years ago I didn't reboot for something like 2+ months, and I had serious issues with connection to the streaming server (audio chopping/cutting/dropping). The problem was solved after rebooting.  So I want to reboot every night following updates.

Server is configured for local EST timezone:
```
sudo timedatectl set-timezone America/Montreal
```

QUESTION: Is there any way to automate this task (update & reboot) unattended, every night at 3am?

In my 3 years of doing that, only once I recall the update process brought up some menus. Otherwise, it's uneventful.
If automated, in the event that a menu appears that would require user input, what would happen?

Thank you for any suggestions.

---

### Post by ian-weisser on 2023-12-08
A stock install of Ubuntu will check for deb package updates twice daily, and snap package updates four times daily.

When found, deb security updates and all snap updates will be downloaded and installed automatically. deb non-security (bugfix) updates can be held or installed on a schedule you set, but unless you are waiting for a specific bugfix those don't much matter. You can install the buxfixes monthly...or not at all.

In other words, most of your mucking about with apt doesn't make any difference. The system already did it a few hours ago, and will do it again a few hours later.

Rebooting, using the existing tools, is easy. Edit the file /etc/apt/apt.conf.d/50unattended-upgrades (sudo required)

```

...
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}";
        "${distro_id}:${distro_codename}-security";
        // Extended Security Maintenance; doesn't necessarily exist for
        // every release and this system may not have it installed, but if
        // available, the policy for updates is such that unattended-upgrades
        // should also install from here by default.
        "${distro_id}ESMApps:${distro_codename}-apps-security";
        "${distro_id}ESM:${distro_codename}-infra-security";
//      "${distro_id}:${distro_codename}-updates";             <---- Uncommenting this will automate your deb bugfixes
//      "${distro_id}:${distro_codename}-proposed";           <----NEVER uncomment this. It will break your system.
//      "${distro_id}:${distro_codename}-backports";
};
...
// Do automatic removal of unused packages after the upgrade
// (equivalent to apt-get autoremove)
//Unattended-Upgrade::Remove-Unused-Dependencies "false";   <--- Uncomment and change to "true" for autoremove
...
// Automatically reboot *WITHOUT CONFIRMATION* if
//  the file /var/run/reboot-required is found after the upgrade
//Unattended-Upgrade::Automatic-Reboot "false";                <--- Uncomment and change to "true" for 3am reboot every couple weeks when the kernel gets updated

// Automatically reboot even if there are users currently logged in
// when Unattended-Upgrade::Automatic-Reboot is set to true
//Unattended-Upgrade::Automatic-Reboot-WithUsers "true";     <--- Uncomment and leave "true" for 3am reboot

// If automatic reboot is enabled and needed, reboot at the specific
// time instead of immediately
//  Default: "now"
//Unattended-Upgrade::Automatic-Reboot-Time "02:00";       <--- Uncomment and edit time to "03:00"

```

---

### Post by TheFu on 2023-12-08
Some cautionary comments:

While it seems like a good idea, having been burned due to automatic updates and having 4 hrs of downtime that impacted my users, I'll never enable unattended patching again. Never, never, never.  I do have a script that patches my 20 systems, but I manually run it and review the logs immediately.

Further, patching too often is detrimental for system stability.  I patch once a week, so it is clear when a new problem shows up, that it is most likely due to a patch problem.  A few times every year, early patches get pulled and re-released 1-2 or 7 days later.  I'd rather avoid that.

Now, if I ran wordpress on one of my systems, since php and wordpress with extensions are highly hacked situations, then I'd check for issues daily, but I still wouldn't automatically patch. No way.

Whenever scripting anything, don't trust the PATH to find the correct programs. Always specify the full path to each program and never assume what the CWD/PWD might be. Any input options that include directories or files need to be absolutely specified, never relative.  These two steps will prevent failures from the scheduling tool, cron.

Also, apt is clear that it shouldn't be used in scripts.  Use apt-get instead ... well, really you should use /usr/bin/apt-get to have the full path specified.  Were me and I'd decided to automate this stuff (still a bad idea), I'd just create the the script and put it into /usr/local/sbin (the place for admin tools/scripts), then call it from the root crontab, no sudo needed that way.  You should send the stdout and stderr output from the script to a logfile.  Again, if it were me, I'd make that logfile have a date-stamp in the name and retain at least a few weeks of those job logs.

There are different crontab files. Some have a different format.  There are example entries in /etc/crontab ... with the system crontab.  This is how anacron tasks (hourly, daily, weekly, monthly, get called). 
```
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name command to be executed
```
Put those comments in the file, if they aren't already there, as a reminder of the fields.

When a cronjob finishes, it really wants to send an email to the user account running the task.

---

