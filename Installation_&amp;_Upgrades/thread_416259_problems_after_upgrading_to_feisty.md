---
title: "problems after upgrading to feisty"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by SomeGuy on 2007-04-21
hey
after upgrading from 6.10 to fiesty using the update program
which all ran fine no errors

now i have 2 problems
the computer takes  a long time to boot where it gets jammed on atempting to load some things
and more importantly my 2nd issue where once the computer boots the cpu goes 100% and it takes about 10mins to login 10mins to bring up system monitor 10mins to type a command

in system monitor it showed klogd as well as a number of ohter processes starting with k using up all my cpu
orignaly i thought these were kde releated programs as i had konqueror installed
so i removed knoqueror and the kde files then after rebooting to the same problem i found out that those processes were kernel log deamoe among ohtert nessary things

when i uninstalled konqueror and the other kde files i didnt remove anything else that i didnt knw for sure was a kde file i used synaptic
apon rebooting X fails to load at all now

however X still does load in single user recovery mode which i am in now, and my cpu usage is normal

X problem i get is
Fatal server error:
xf86OpenConsole: Cannot open virtual console 7 (Input/output error)

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

i have no idea wats causing the lag problem
but hte proceses taking my cpu time were
events/0
watchdog/0
kblockd/0
dd
ksoftirqd/0
syslogd
klogd

if this problems is gona be difficulti to diagnose let alone fix, is there a way i can redo the upgrade thru a cd or osmething and reinstall all the programs w/o lossing all my files and config files?

---

### Post by SomeGuy on 2007-04-22
nevermind i managed to backup all my files so i just reinstalled edgy

---

