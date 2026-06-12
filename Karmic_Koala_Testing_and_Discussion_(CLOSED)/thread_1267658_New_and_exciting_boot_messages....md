---
title: "New and exciting boot messages..."
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-09-16
Ever since the updates from today which really messed me up, I now see some crazy boot messages that delay or keep xsplash from working.  Is there a way I can capture them?  I'm scouring the logs and can't pick up on anything resembling what I saw.  Something about udev rules and then something on hdparm.

---

### Post by graaant on 2009-09-16
I get the same error messages. But not too sure how to capture them. Surely there are some boot logs somewhere.

---

### Post by mariner09 on 2009-09-16
So, I stared long enough to remember that 3 of them were concerning a file /lib/udev/rules.d/40-ppc.rules.  When I looked at that file, it only pertained to iSeries equipment.  I moved it out of that directory and let's see what happens...

---

### Post by graaant on 2009-09-16
Had a look through the syslog.
Searched for udev and found these, looks like what I get at bootup.

Sep 16 10:02:16 laptop init: hal main process (1680) terminated with status 1
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:3
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:4
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:5
Sep 16 10:02:17 laptop udevd[1266]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:3
Sep 16 10:02:17 laptop udevd[1266]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:4
Sep 16 10:02:17 laptop udevd[1266]: can not read '/etc/udev/rules.d/z60_hdparm.rules'
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:3
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:4
Sep 16 10:02:17 laptop udevd[1266]: NAME="%k" is superfluous and breaks kernel supplied names, please remove it from /lib/udev/rules.d/40-ppc.rules:5
Sep 16 10:02:17 laptop udevd[1266]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:3
Sep 16 10:02:17 laptop udevd[1266]: unknown key 'SYMLINK{unique}' in /lib/udev/rules.d/50-udev-default.rules:4
Sep 16 10:02:17 laptop dbus-daemon: Reloaded configuration

---

### Post by VMC on 2009-09-16
I had the same thing happen. Something to do with bad symlinks to "/ete/udev/rules.d". I couldn't find any logs to verify the errors.

---

### Post by godhika on 2009-09-16
same thing here - but I am happy that at least booting is working again.

---

### Post by mariner09 on 2009-09-16
So, z60-hdparm.rules is a bad symlink to a non-existent file called /etc/udev/rules.d/hdparm.rules.  There is an 85-hdparm.rules in /lib/udev/rules.d/ that probably covers whatever was originally in there.

I removed the 40-ppc.rules and there's no ill effect.

The other 2 lines in 50-udev-default.rules are as follows:

SUBSYSTEM=="block", SYMLINK{unique}+="block/%M:%m"
SUBSYSTEM!="block", SYMLINK{unique}+="char/%M:%m"

I think it's these 2 lines that break you out of xsplash/usplash altogether.  I'd hate to remove them because I'm not familiar with this new upstart.

I think the migration to upstart has been a slam dunk and this kind of stuff is the residual effect.

Anyone know how to clear those 2 error messages???

---

### Post by Eestlane on 2009-09-16
It's awesome how fast it boots after these messages, though.

---

### Post by | MM | on 2009-09-16
Hrmmm, so i probably didn't need to reinstall :P.

BTW, anyone with ata drives getting DRDY ERROR's?  I am using ext4.  I did a search and there was a known kernel bug back in the hardy days with regard to some acpi kernel badness. Seems to me though that when i get an DRDY ERROR it seems to do a bit of damage to the fs, i fsck and it reports damaged files.

So its either bad ata+acpi bug in kernel or my drive is failing (it is a rather old drive).  WindowsXP does not seem to complain and goes on like a champion. I am hoping its some kind of kernel bug -- for my hard drives sake.

---

### Post by mariner09 on 2009-09-16
Unfortunately, I pulled the trigger prior to reading the forums and seeing how people recovered.  I was getting a list of errors and then a hung system.  No gdm, no nothing.  All back now after an hour or so.

---

### Post by wfp on 2009-09-16
Getting same error messages on boot. Just will not reboot until updates come down. lol

---

### Post by TDK800 on 2009-09-16
Yesterdays/todays updates totally screwed up my system, after loading grub and before displaying the screen for disk decryption password it starts giving the errors and beeping the builtin speaker insanely:

[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:3

[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:4

I was able to load the grub selector and go with kernel recovery mode, then in networked root shell do an aptitude upgrade which installed allmount that was missing before from predependencies, along with ubstart, after restart my full disk decryption password was not accepted anymore!!!

It gives the error /dev/mapper/x-root does not exist. Which I think could be related to it not being able to access the encrypted drive and drops me to the limited built-in shell (ash).

Any help or ideas appreciated.

---

### Post by TDK800 on 2009-09-16
> **| MM | said:**
> Hrmmm, so i probably didn't need to reinstall :P.

BTW, anyone with ata drives getting DRDY ERROR's?  I am using ext4.  I did a search and there was a known kernel bug back in the hardy days with regard to some acpi kernel badness. Seems to me though that when i get an DRDY ERROR it seems to do a bit of damage to the fs, i fsck and it reports damaged files.

So its either bad ata+acpi bug in kernel or my drive is failing (it is a rather old drive).  WindowsXP does not seem to complain and goes on like a champion. I am hoping its some kind of kernel bug -- for my hard drives sake.

Was getting disk related errors also running ext3 fully encrypted, fsck reported damaged files too... then full efsck crashed, after that isn't accepting decryption password anymore.

---

### Post by xArv3nx on 2009-09-16
i think i had this problem too.

i had an issue yesterday where the boot just basically wouldn't work. turns out after updating from alpha 4 (or alpha 5, not sure) sreadahead wasn't installed because of a missing dependency (that dependency wasn't built and in the repos yet because of build errors -- so sreadahead wouldn't install and im assuming this is crucial to the boot process).

for all those with errors: try an apt-get dist-upgrade and see if sreadahead is there as held back. if it is, do an apt-get install sreadahead and see what its holding back.

---

### Post by Jim March on 2009-09-16
After today's fiasco of non-booting-ness, at this point I could care less about what it does during boot, so long as the damnthing does in fact boot.

It play Metallica backwards the whole time while the screen has an epileptic fit.  Screw it.  Just boot, dammit.

:)

---

### Post by Funnnny on 2009-09-16
Lol, today when I'm at my class, ubuntu suddenly shutdown ( it was suspended and maybe I was running out of battery ) and playing some rock-music.

---

### Post by Leighman on 2009-09-16
Yeh, my boot is fricked up as well.  No partial upgrade or packages held back or anything tho.
Started by doing recovery and just waiting for quite a while :P

---

### Post by moviemaniac on 2009-09-16
> **wfp said:**
> Getting same error messages on boot. Just will not reboot until updates come down. lol

Same here. I finally got the machine recovered from yesterday's updates, now dbus is acting crazy. There's no way I'll reboot my machine until I can update it with fixed packages.

However, I have to say one thing: I love Linux as far as bugs are concerned - you can reach the developers and the whole thing is an open, community-driven, transparent process. Try getting a microsoft (or insert any other closed source company here) programmer on the phone :D
In fact, it's FUN to fix bugs/broken systems on Linux - because you CAN and you learn lots of stuff about how your machine works in the process of fixing and investigating :guitar:

---

### Post by cyberkilla on 2009-09-16
I upgraded today, WITHOUT a "partial" upgrade. It worked, but I do get those weird errors before the computer boots.

I'm just thankful that it boots at all:P

---

### Post by waspbr on 2009-09-16
no cake for me either, at least not in my desktop, neither the main or the recovery modes will boot, they both seem to hand after the line:

```
init:/etc/init:Unable to load configuration: input/output error
```


I can't seem to get to the cli, so if this goes on I may have to reinstall... luckily I have a separate home partition, though reinstalling is still a chore.

---

### Post by hgergo on 2009-09-16
The error is nice for bootscreen :P
I have this problem too

---

### Post by Meriadok on 2009-09-16
I have same problem too.
Apt-get upgrade doesn't help at this moment.
Does anybody know a related bug on launchpad to subscribe?

---

### Post by hasinasi on 2009-09-16
> **Meriadok said:**
> 
Does anybody know a related bug on launchpad to subscribe?

Try 430125: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/430125")

---

### Post by hasinasi on 2009-09-16
> **waspbr said:**
> 
I can't seem to get to the cli, so if this goes on I may have to reinstall... luckily I have a separate home partition, though reinstalling is still a chore.

I had the very same problem and was finally able to fix it. One problem was that even in recovery mode, the screen went (and stayed) black. I finally got it to show again. I believe I hit Ctrl-Alt-F2 and then again Ctrl-Alt-F1. Once you have the screen working, you need to update all packages. If you ended up in a console without network, you need to bring up network by doing ```
sudo dhclient eth0
```. 

After updating, your system should boot again. These package updates sucked!
Good luck.

---

### Post by FuturePilot on 2009-09-16
Same problem here. I keep getting lots of these unknown key SYMLINK messages

```
[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:3

[udevd 963] unknown key SYMLINK{unique} in /lib/udev/rules.d/50-udev-default.rules:4

```

---

### Post by trulan on 2009-09-16
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654)

Here's the bug.  Looks like it's nothing to worry about, should be gone next week.

---

### Post by VMC on 2009-09-16
> **trulan said:**
> [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654)

Here's the bug.  Looks like it's nothing to worry about, should be gone next week.
Thanks for finding this. I was just going to search for error. Looks like LP Post#12 explains the reasoning.

---

### Post by blakamin on 2009-09-17
I get all this *and* fsck needs running due to sync times being a day ahead (or some such biz). Annoying. 
How can this be being fixed *next week* when alpha 6 is due anytime in the next 24 hours? :confused:

---

### Post by neferty on 2009-09-17
so, anyone fixed the udevd errors on boot?

---

### Post by trulan on 2009-09-17
The udev errors will go away on their own, don't try to fix them - see the bug I linked above.

the fsck issue and the sync times being in the future are unrelated to these udev errors.

---

### Post by wfp on 2009-09-19
Wiped out alpha 5, and downloaded alpha 6, Just did a fresh install same error messages.

---

### Post by amano on 2009-09-19
THose are upstream udev problems. They are supposed to be fixed within next week. Scott James Remnant knows of them already, thus there is no need to confirm them any more. Just wait and they will get fixed...

---

### Post by trulan on 2009-09-19
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/430654)

Just wanted to bump this thread to the top so people will quit posting about the udev/bad symlink error messages.

Do not try to fix these!  They will be gone soon enough!  Patience, people!

---

