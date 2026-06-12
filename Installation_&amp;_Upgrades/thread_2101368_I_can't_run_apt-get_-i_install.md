---
title: "I can't run apt-get -i install"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by markseger on 2013-01-04
I've seen to wrap myself around the axle and don't know what to do.

At some point awhile back I tried to do an upgrade and I had some dependency problems.  Spending a fair chunk of time with google and trying some suggestions things went from bad to worse.  When I used to run

apt-get install -f

it world generate some errors at the end telling me there were dependency problems.  Now when I run it, it tells me 

locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Preconfiguring packages ...
(Reading database ... 328164 files and directories currently installed.)
Preparing to replace libc6:amd64 2.13-20ubuntu5.1 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)
Checking for services that may need to be restarted...
Checking init scripts...
Checking for services that may need to be restarted...
Checking init scripts...
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by /usr/bin/locale)
/usr/bin/locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /usr/bin/locale)

and tells me its configuring libc6 and needs to restart 'cron atd'.  I hit return basically see the same messages following by a display that tells me it wants to restart 'cron atd' to I enter return again and it displays:

Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

and exits.

for grins I tried installing xterm just to see what it would do and I'm getting this:

mjs@blkjack:~$ sudo apt-get install xterm
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1)
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5.1)
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is to be installed
 xterm : Depends: libc6 (>= 2.15) but 2.13-20ubuntu5.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

but of course apt-get -f install doesn't work.

Any and all suggestions will be greatly appreciated

-mark

---

### Post by dino99 on 2013-01-04
missing glibc, wow, its hard to believe, as its one of the main family packages

have you tried to clean the system first ?
- clean/autoclean/autoremove
- gtkorphan

sudo rm /var/cache/apt/archives/*

then , from synaptic, desactivate all the non genuine repo(s) (if any), and update again. Then reboot in recovery mode & select the repair option.


note: hold "shift" key down at bios end process to get the grub menu on single OS system

---

### Post by markseger on 2013-01-04
I just did a clean and autoclean followed by autoremove and the third one failed like this:

mjs@blkjack:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1)
 libc6:i386 : Depends: libc-bin:i386 (= 2.13-20ubuntu5.1)
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is installed
E: Unmet dependencies. Try using -f.

but -f doesn't work.

re synaptic - I've never used it before, is it pretty straightforward or given my situation do I need to do something special?

-mark

---

### Post by markseger on 2013-01-04
I just cleaned out the cache and that didn't help either.  Tried to run synaptic but it's not installed, and since apt-get is busted...
-mark

---

### Post by darkod on 2013-01-04
When you say you "tried to do an upgrade", you mean upgrade of the ubuntu version or apt-get upgrade?

And what does "tried" mean? You either did it or not. Did the process fail?

If it was an upgrade from one version to the next one and it failed/stopped, who knows what got busted. It might be much easier to make a new clean install than to try fixing this one.
You can try booting it into recovery mode, and try the apt-get install -f in there. Probably accompanied by:
dpkg --configure -a

especially if this was a stopped upgrade process.

If it was only a failed apt-get upgrade it shouldn't leave deep problems behind but who knows...

---

### Post by markseger on 2013-01-04
when I said tried, I meant exactly that.  things got part-way though and then failed.  I've been trying to remember all I went through to get into this state, because it predates xmas and I remember explicitly not wanting to deal with this during the holidays.

my recollection is trying to update the system with a LOT of packages being out-of-date, and it not completing.  I had then manually updated a few of them but others still had problems I just couldn't get around.  it was around that time that apt-get install -f failed to run

today I got a popup asking if I wanted to upgrade to precise and figured what the hell, things can't get much worse, so I said yes.  well things do seem to have gotten worse because when I rebooted my machine it stops at the 'check battery state' message and I can only log in remotely.  that's something I've seen before and think I need to upgrade my video driver, but of course w/o apt-get I can't do that.

not a great way to start the new year...

-mark

---

### Post by markseger on 2013-01-04
here's another piece to the puzzle:

root@blkjack:/home/mjs# locale
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.15' not found (required by locale)
locale: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by locale)

and those 2 versions of GLIBC were reported in earlier error messages by apt-get

-mark

---

