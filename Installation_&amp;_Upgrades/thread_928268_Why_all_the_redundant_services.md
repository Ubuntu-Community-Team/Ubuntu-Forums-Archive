---
title: "Why all the redundant services?"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by anars on 2008-09-23
Hi there

Can anyone please shed some light on why a default Ubuntu installation has two sysloggers and two cronjob daemons?

atd and anacron.
klogd and sysklogd.

Thanks!

---

### Post by anars on 2008-09-27
Bump.. anyone?

---

### Post by anars on 2008-12-03
Bump again. There must be a logical explanation for this :-)

---

### Post by ajcham on 2008-12-04
If I've understood what I've read correctly, sysklogd expands on the functionality of syslog and klogd, and is dependent on both.

As for anacron and atd, they are used for scheduling recurring and one-off jobs respectively. (anacron is merely an extension for cron). In the future, atd's functionality is expected to be merged into cron.

I hope these answers are satisfactory - I see this has been bugging you for some time!

---

### Post by lunchlady55 on 2010-02-19
RE: anacron / cron: You can view /etc/anacrontab for a list of jobs that will be run.  It *seems* that the only entries in mine (Ubuntu 9.04) are to run cron.daily, cron.weekly and cron.monthly, so if you don't usually shut off your machine or don't care if the jobs get skipped if your machine is off, you can disable this service (at your own risk).

---

### Post by random.manifestation on 2010-03-02
It may be a little bit off-topic but is there a karmic specific summary for what which service stands? i can't find half of my services and it seems a lot for a notebook.

```

acpi-support              0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on 
acpid                     0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on 
alsa-utils                0:off  1:off  2:off  3:off  4:off  5:off  6:off       
anacron                   0:off  1:off  2:off  3:off  4:off  5:off  6:off       
apparmor                  0:off  1:off  2:off  3:off  4:off  5:off  6:off       
apport                    0:off  1:off  2:off  3:off  4:off  5:off  6:off       
atd                       0:off  1:off  2:off  3:off  4:off  5:off  6:off       
avahi-daemon              0:off  1:off  2:off  3:off  4:off  5:off  6:off       
binfmt-support            0:off  1:off  2:off  3:on   4:on   5:on   6:off       
bluetooth                 0:off  1:off  2:off  3:off  4:off  5:off  6:off       
bootlogd                  0:off  1:off  2:off  3:off  4:off  5:off  6:off       
brltty                    0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on 
console-setup             0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on 
cron                      0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on 
cryptdisks                0:on   1:off  2:off  3:off  4:off  5:off  6:off       
cryptdisks-early          0:on   1:off  2:off  3:off  4:off  5:off  6:off       
cryptdisks-enable         0:off  1:off  2:off  3:off  4:off  5:off  6:off       
cryptdisks-udev           0:off  1:off  2:off  3:off  4:off  5:off  6:off       
cups                      0:off  1:off  2:off  3:off  4:off  5:off  6:off       
dbus                      0:off  1:off  2:off  3:off  4:off  5:off  6:off       
dirmngr                   0:off  1:off  2:on   3:on   4:on   5:on   6:off       
dkms_autoinstaller        0:off  1:off  2:on   3:on   4:on   5:on   6:off       
dmesg                     0:off  1:off  2:off  3:off  4:off  5:off  6:off       
dns-clean                 0:off  1:on   2:on   3:on   4:on   5:on   6:off       
epos                      0:off  1:off  2:off  3:off  4:off  5:off  6:off       
exim4                     0:off  1:off  2:on   3:on   4:on   5:on   6:off       
failsafe-x                0:off  1:off  2:off  3:off  4:off  5:off  6:off       
firestarter               0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on 
grub-common               0:off  1:off  2:on   3:on   4:on   5:on   6:off       
hal                       0:off  1:off  2:off  3:off  4:off  5:off  6:off       
hwclock                   0:off  1:off  2:off  3:off  4:off  5:off  6:off       
hwclock-save              0:off  1:off  2:off  3:off  4:off  5:off  6:off       
kdm                       0:off  1:off  2:off  3:off  4:off  5:off  6:off       
kerneloops                0:off  1:off  2:off  3:off  4:off  5:off  6:off       
keyboard-setup            0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on 
killprocs                 0:off  1:on   2:off  3:off  4:off  5:off  6:off       
laptop-mode               0:off  1:off  2:on   3:on   4:on   5:on   6:off       
module-init-tools         0:off  1:off  2:off  3:off  4:off  5:off  6:off       
mysql                     0:off  1:off  2:off  3:off  4:off  5:off  6:off       
networking                0:on   1:off  2:off  3:off  4:off  5:off  6:off  S:on
ondemand                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
pcmciautils               0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
policycoreutils           0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on
policykit                 0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
polipo                    0:off  1:off  2:on   3:on   4:on   5:on   6:off
portsentry                0:off  1:off  2:on   3:on   4:on   5:on   6:off
pppd-dns                  0:off  1:off  2:off  3:off  4:off  5:off  6:off
preload                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
privoxy                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
procps                    0:off  1:off  2:off  3:off  4:off  5:off  6:off
rc.local                  0:off  1:off  2:on   3:on   4:on   5:on   6:off
rcS                       0:off  1:off  2:off  3:off  4:off  5:off  6:off
rsync                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
rsyslog                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
rsyslog-kmsg              0:off  1:off  2:off  3:off  4:off  5:off  6:off
saned                     0:off  1:off  2:on   3:on   4:on   5:on   6:off
screen-cleanup            0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on
selinux                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
sendsigs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
stop-bootlogd             0:off  1:off  2:off  3:off  4:off  5:off  6:off
stop-bootlogd-single      0:off  1:off  2:off  3:off  4:off  5:off  6:off
tor                       0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on
udev                      0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on
udev-finish               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevmonitor               0:off  1:off  2:off  3:off  4:off  5:off  6:off
udevtrigger               0:off  1:off  2:off  3:off  4:off  5:off  6:off
umountfs                  0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountnfs.sh              0:on   1:off  2:off  3:off  4:off  5:off  6:off
umountroot                0:on   1:off  2:off  3:off  4:off  5:off  6:off
unattended-upgrades       0:on   1:off  2:off  3:off  4:off  5:off  6:off
urandom                   0:on   1:off  2:off  3:off  4:off  5:off  6:off  S:on
usplash                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
virtualbox-ose            0:off  1:off  2:on   3:on   4:on   5:on   6:off
virtualbox-ose-guest-utils  0:off  1:off  2:on   3:on   4:on   5:on   6:off
wicd                      0:off  1:off  2:on   3:on   4:on   5:on   6:off  S:on
winbind                   0:off  1:off  2:on   3:on   4:on   5:on   6:off
wpa-ifupdown              0:on   1:off  2:off  3:off  4:off  5:off  6:off  S:on
x11-common                0:off  1:off  2:off  3:off  4:off  5:off  6:off  S:on

```

thanks in advance,
RM

---

### Post by SnickerSnack on 2010-03-02
> **lunchlady55 said:**
> RE: anacron / cron: You can view /etc/anacrontab for a list of jobs that will be run.  It *seems* that the only entries in mine (Ubuntu 9.04) are to run cron.daily, cron.weekly and cron.monthly, so if you don't usually shut off your machine or don't care if the jobs get skipped if your machine is off, you can disable this service (at your own risk).

I think he's figured it out by now. ;)

> **random.manifestation said:**
> It may be a little bit off-topic but is there a karmic specific summary for what which service stands?

I'm half guessing that you mean "what are the shorthand names for my services?"  If that's right, then I'd try googling the name of the service you want, or look at the list of processes and guess at which ones might be what you want, then google for those to see if you can find one that matches.

> **random.manifestation said:**
> i can't find half of my services and it seems a lot for a notebook.

I'd think that a notebook would have even more services if there were any difference at all. :neutral:

---

### Post by Sef on 2010-03-02
Necromancing. Locked.

---

