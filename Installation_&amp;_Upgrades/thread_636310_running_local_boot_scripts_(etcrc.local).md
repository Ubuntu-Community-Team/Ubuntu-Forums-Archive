---
title: "running local boot scripts (/etc/rc.local)"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by rendon on 2007-12-09
Hello everyone,

I'm a newb to the forum here, nice to meet everyone!

Although I've used linux for years, I've never been too adept at tracing serious problems, especially when I can't find an immediate answer on google.

I'm in charge of a server in a company which I've only been working at for 3 months.  Although I could tell that the system (running Ubuntu of course) had some problems, my warnings to upgrade and backup the server were ignored, and thus we have a crashed server with 2 bad fans and no backup.

I got the machine (which I can't give you much details about) back to the office and got it running again, then upgraded to Feisty from Edgy... and everything was fine.  The problems started when I went to upgrade from Feisty to Gusty.

First Major Problem (don't know if this is the cause):
The power in the office went out during the upgrade process, and when I tried to restart server it just kept hanging on "running local boot scripts (/etc/rc.local)"

Then, I got into a prompt by hitting escape at grub startup and choosing a recovery mode of sorts.  I then continued to do the upgrade (hoping it would fix the problem) with the recommended server upgrade command "do-release-upgrade"

Then I had this error nonstop at boot:
 [ 543.856000] device-mapper: ioctl: error adding target to table
[ 543.860000] device-mapper: table: 254:0: linear: dm-linear:

I removed that error message by removing "evms" according to another thread here.

but I still hang on "running local boot scripts (/etc/rc.local)" at boot.

Other threads here mentioned it being a possible problem with X, but I'm running a server with no X, so do you have any ideas about this?

The only thing I could tell you about the server is that it has a Ultra ATA hard drive.

Any feedback appreciated!

Thanks,
Brendon

---

### Post by rexxxlo on 2007-12-25
my desktop is doing the same thing so ill bump this up in hopes of getting answer for you.

---

### Post by eduardoeltortuga on 2008-01-10
I just installed Ubuntu server. After reboot my computer hangs at "Running local boot scripts." I am trying the server because I was having problems with enabling the restricted nvidia drivers on the regular edition of Ubuntu. My computer also was hanging at the SAME point! Strange coincidence.

---

### Post by rendon on 2008-01-19
problem solved well enough for me...

in the end after removing the evms things were actually working fine, I discovered.

I only had to hit enter when it stuck at 'running local boot scripts' then a login prompt appeared.

so if you're having the device-mapper problem you might try logging in through recovery mode and doing "apt-get remove evms"

since it's a server I don't really care about it hanging without giving me the prompt since i don't see it.  And everything else is working fine anyway.  I can even do remote reboots.  Been using the server for about a month now with no problems.

hope that helps!

---

