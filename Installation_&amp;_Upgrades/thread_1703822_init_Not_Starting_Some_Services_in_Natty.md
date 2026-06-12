---
title: "init Not Starting Some Services in Natty"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by adonicus on 2011-03-09
[SIZE="2"]Recently installed Natty from a daily build (all packages now updated), and while it more or less works properly, there's a number of faults that points to init/upstart not working as advertised:

[LIST=1]
[*]`runlevel` returns "unknown"
[*]`initctl list` prints nothing, returns 0
[*]the hostname is not set at boot time
[*]no gettys are started; X runs on the first virtual TTY
[*]the CPU scaling governor is not switched to ondemand
[/LIST]

On the other hand, some `init` tasks do run, e.g. `ntpd` and `x11-common`.

Once logged in, if I execute `/etc/init.d/{hostname,ondemand} start`, those scripts work as expected.  So whatever should be starting them during boot is not doing so.

Have you (yes, you! :D) seen this problem?  Do you know what might be causing it?  In particular, what's the deal with the gettys -- how are they supposed to be started by `upstart`?[/SIZE]

---

### Post by mörgæs on 2011-03-10
You are more than welcome to try 11.04, but please remember that if using an alpha version, you are the one helping people, for example by reporting bugs, not the one asking for help. 

More on 11.04 here:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

If these are true bugs, you can report them at
[http://www.launchpad.net/ubuntu/](http://www.launchpad.net/ubuntu/)

---

### Post by adonicus on 2011-03-10
> **mörgæs said:**
> You are more than welcome to try 11.04, but please remember that if using an alpha version, you are the one helping people, for example by reporting bugs, not the one asking for help

[SIZE="2"]Thanks for the heads up.

The reason I'm asking here instead of filing a bug report is that I suspect something went wrong with my installation, so this may be affecting only me, not other people.  But I want to understand how init/upstart could be simply not starting things -- that way I can debug the issue myself instead of tying up people who don't have access to a computer exhibiting the fault.  I will file a bug report if nobody can explain this failure mode.[/SIZE]

---

