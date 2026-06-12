---
title: "How do I temporary pause scheduled Apt to prevent race conditions? (scripting, auto)"
date: 2021-06-28
forum: Installation &amp; Upgrades
---

### Post by and-account on 2021-06-28
Hi!

I'm scripting installation scripts with my favorite settings and list of software. Certain times auto-update routines scheduled by Ubuntu are preventing my scripts from doing apt-dpkg-install, as they are periodically locking package manager's db (as they are periodically doing apt update and so on).

What is a correct way to programmatically put it on hold and then enable back? What a services and schedules are sufficient to be stopped in order I can be sure nothing will try to race with Apt update and install? The question is not concerning GUI, I'm interested in unattended way to temporary turn off and on predefined Ubuntu mechanics. What a configuration files, Cron jobs, Systemd timers are responsible for the process?



As far as I see Focal Fossa 20.04 have two timers:
```
$ systemctl --no-pager --full --no-legend list-timers
apt-daily.timer
apt-daily-upgrade.timer

```

Also there are following configuration files:
```
[FONT=monospace]/etc/apt/apt.conf.d/10periodic
/etc/apt/apt.conf.d/20auto-upgrades
/etc/apt/apt.conf.d/50unattended-upgrades
[/FONT]
```

Is it sufficient to disable only these timers?
Are there anything in use with same functionality among Cron jobs, or Systemd is the only thing to be used as launcher?
Should I additionally temporary edit with sed or somehow else files in [FONT=monospace]/etc/apt/apt.conf.d/?
[/FONT]What a files should I edit in [FONT=monospace]/etc/apt/apt.conf.d/[/FONT] if any?

What is a correct way to programmatically put it on hold and then enable back? 

Is there big difference with 18.04?
Thank you!

---

### Post by TheFu on 2021-06-28
I disable all automatic APT stuff and do it manually during weekly maintenance periods.  My technique is to uninstall update-notifier-common which seems to get everything once the dependencies to that are removed too.

Why the question about 18.04?  No older releases are still supported and most 18.04 desktop releases lost support a few months ago.

Manually modifying package manager configurations if they don't support a .local config file is asking for future trouble, IMHO.

I don't know what "launcher" is.  cron, which calls anacron, is where the daily nagging happens.  I vaguely recall there's a way/setting to disable those, but even the weekly nags were too much for me.

If you do want automatic upgrades to run daily, please, please only allow security patching. Also, there really isn't much of a race condition unless you have a habit that lines up with the morning tasks in Ubuntu's daily anacron.  On my systems, those run at either 6:26am or 7:26am which could be highly inconvenient.  Nothing says you couldn't move that start time to 13:03 daily, if that is better.

---

### Post by and-account on 2021-06-28
That's script to be applied by Ansible at my lab VMs. After fresh VM has been deployed auto updates are racing against my configuration scripts with very high probability (they usually do). Later, during life cycle, it may fail occasionally, if coincided with scheduled updates launch. It seems the most atomic, fast, portable and not invasive way to do desired things programmatically is to disable schedule, wait until locks are free and start.

Well, got it - I may trace update-notifier-common dependencies and see the bonds.

18.04 is little bit smaller, little bit faster and still in use along with 20.04. It's not smth. to be in active use, but if there are few differences why not apply it for Beaver at kitchen radio too. :)

Another solution is to simply wait until locks are free. But may be it's good to have more controllable process - be sure a processes are deactivated at all for a while.

---

### Post by and-account on 2021-07-02
> **TheFu said:**
> 
Manually modifying package manager configurations if they don't support a .local config file is asking for future trouble, IMHO.

There is apt-config utilty. It's man say
```

[FONT=monospace][COLOR=#000000]    OPTS="-f"[/COLOR]
    RES=`apt-config shell OPTS MyApp::options`
    eval $RES
This will set the shell environment variable $OPTS to the value of MyApp::options with a default of [COLOR=#000000]**-f**[/COLOR][COLOR=#000000].[/COLOR]
[/FONT]
```

It seems it's a way to do reliable options switching?

Why not to do it?

---

