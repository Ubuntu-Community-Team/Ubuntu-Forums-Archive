---
title: "Ubuntu 10.4 &quot;Your disk drives are being checked for errors, this may take some time&quot;"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Buying_Some_Time on 2010-04-19
This morning I woke up and started my laptop, and I received that message, it kept saying something like [Checking disk 1 of 1 21% complete] then it would just restart the process all over again. I finally got Ubuntu 10.4 beta 2 to boot, after at least 100 manual restarts. Anyone know what caused this and how to keep it from happening again?

---

### Post by Buying_Some_Time on 2010-04-19
Anyone?

---

### Post by uRock on 2010-04-19
Have you run updates lately? I haven't had that problem for weeks and when I did it only took one restart to get it going.

BTW, 10.04 is still in testing.

---

### Post by Jake007g on 2010-04-21
I'm having the same problem too, but it happened to me when I rebooted from a freeze. I was thinking if I could boot it with terminal access and manually run fsck it should resolve the problem, but there isn't any stage in which I can access the terminal.

Any resolution would be greatly appreciated.

---

### Post by uRock on 2010-04-21
The grub menu is before Plymouth starts, select the restore kernel from the list and once the restore menu boots you can access a terminal.

---

### Post by Jake007g on 2010-04-21
As I am booting, something appeared on screen for a few seconds before it started 'checking for disk errors'.

It said something like this:

```

/dev/sda1 contains a file system with errors, check forced.
init: plymouth main process (288) killed by SEGV signal
```

EDIT: I'm going to trying booting from a Live-CD and running fsck manually.

---

### Post by skbhat03 on 2010-04-21
I too have the same problem :(

I did a clean installation of Beta 2, but after the regular updates (via update manager), it fails to boot.
It shows the first screen with "Ubuntu" logo and says system is checking for errors and then it takes me to a black screen !

Any idea what can be the problem ?

Best regards,
Subbu.

---

### Post by El_Shrander on 2010-05-03
Just a few words to say that this issue is still up - it just happened to me this morning, and Lucid's beta stage is some days old already.

In my case, I just waited (and waited, and waited...) for the check to run its course, and all got well, finally. Now I am scared to restart my computer again, though :(

---

### Post by rajeeja on 2010-05-11
+1, I was blaming myself for tweaking somethings. Good see some more victims :P

From what it does it looks more like a virus !! than a bug. It started normally once and worked fine. On hibernating and restarting it network connection won't work. Again restarting in safe mode gets me the 

"plymouth main process 456 killed by segv"
"plymouth splash main process 2992"

Now drives checking stuck at 72%......

Rajeev

---

### Post by Oldest Bob on 2010-05-11
My firsst disk check since installing 10.04. First I tried to stop the check by pressing"C" as noted on the screen - nothing happened. My check also seemed to stop at 72% but I let it run and I found that the check did slowly [progress (about 30-40 seconds per percent gain) It is now at 86% and still slowly progressing. Maybe patience is the answer st this time. Oldest Bob:(

---

### Post by Oldest Bob on 2010-05-11
Okay - My disk check did complete It took 12 minutes to do the last 10% but it did finish and reboot. For now try a lot of patience. :P

---

### Post by rajeeja on 2010-05-11
so are you able to able to get to the internet?. My network activity is disabled and in safemode I see the failure starting AppArmor profiles, related to plymouth error again,  [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/571258](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/571258)

I get to the recovery menu, but still no network is found.

---

### Post by RJARRRPCGP on 2010-05-11
Looks like you're using ext2 and the file system got corrupted.

This behavior is NOT normal with ext3 and ext4. (Because of journaling)

---

### Post by John Aldred on 2010-05-12
I have had this disk check twice in the past 2 weeks.

The "Checking disk 1 of 2 " progress ramps up in about 10 seconds to 70 %, but the remainder of the checking takes about 11 minutes with a 2 minute pause at 90 %.

My installation was a fresh install from the Alternate CD (Intel X86).
File systems are ext3 and ext4. All updates applied.

---

### Post by rajeeja on 2010-05-12
Same here, its ext3 not ext2. @John were you able to get your network connections to work?

---

### Post by movieman on 2010-05-12
> **RJARRRPCGP said:**
> Looks like you're using ext2 and the file system got corrupted.
This behavior is NOT normal with ext3 and ext4. (Because of journaling)

Nope: my netbook's ext4 fsck (triggered by mount count after a clean shutdown) took about an hour last night on a 120GB disk.

This is a known bug with 10.04 and apparently there's a fix in the works; search on launchpad for the gory details.

---

### Post by uRock on 2010-05-12
It doesn't matter which format is being used. I hope it gets fixed soon.

---

### Post by ottosykora on 2010-05-12
I am surprised that some people think that the automatic run of fscheck is a bug or what.
So far I never have seen a linux system not doing that regularly, mostly it is set to do the fschk every 25 starts of the operating system. Even our embeded linux servers we produce do this, so sometimes if you have bad luck you have to wait untiul it is finished, but the interval can be set in fact, but should be default 25 starts.
It is not caused by 'something' , it is not a feature of ubuntu, it is simply so, it counts how many times you did start your linux and it is for the health of the file system as preventive maintenance.

---

### Post by John Aldred on 2010-05-12
> **rajeeja said:**
> Same here, its ext3 not ext2. @John were you able to get your network connections to work?

The disk check did not prevent my network connections from working  when the system finally booted up.

---

### Post by John Aldred on 2010-05-12
> **ottosykora said:**
> I am surprised that some people think that the automatic run of fscheck is a bug or what.
So far I never have seen a linux system not doing that regularly, mostly it is set to do the fschk every 25 starts of the operating system. Even our embeded linux servers we produce do this, so sometimes if you have bad luck you have to wait untiul it is finished, but the interval can be set in fact, but should be default 25 starts.
It is not caused by 'something' , it is not a feature of ubuntu, it is simply so, it counts how many times you did start your linux and it is for the health of the file system as preventive maintenance.


True. But the problem seems to be the excessive length of time ( about 12 minutes ) that this process takes on 10.04.  I'm not talking about a huge partition here, it's only 40 GB.

---

### Post by John Aldred on 2010-05-12
> **movieman said:**
> Nope: my netbook's ext4 fsck (triggered by mount count after a clean shutdown) took about an hour last night on a 120GB disk.

This is a known bug with 10.04 and apparently there's a fix in the works; search on launchpad for the gory details.

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707)

---

### Post by bumanie on 2010-05-12
The fix seemingly hasn't come to me as yet, my fsck takes about 7 minutes from 70% to 100%.

---

### Post by rajeeja on 2010-05-12
> **John Aldred said:**
> The disk check did not prevent my network connections from working  when the system finally booted up.

So, I was finally able to get my network to work. For people having the same problem, here's the link.

[http://ubuntuforums.org/showthread.php?p=9288885#post9288885](http://ubuntuforums.org/showthread.php?p=9288885#post9288885)

---

### Post by H3g3m0n on 2010-05-13
I was just wondering how long it takes for a "Fix Committed" to actually hit the repos.

[Current pending packages and their time]("http://people.canonical.com/~ubuntu-archive/pending-sru.html")
[mountall package]("https://launchpad.net/ubuntu/lucid/+source/mountall/")

Doesn't seem like there is a specific timeline, might be worth while people grabbing the package and installing it manually then giving feedback in the [bug]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707").

---

### Post by ubfu on 2010-05-16
I hope they 'll fix it via updates since the it's still unofficial fix at launchpad.Having this issue right now , it's over 10 min.
It depends on processor , if you have a slow processor , it'll take more time

Already 30 pass still stuck at 85% .I can't skip or cancel.

---

### Post by H3g3m0n on 2010-05-16
> **ubfu said:**
> I hope they 'll fix it via updates since the it's still unofficial fix at launchpad.Having this issue right now

The fix has already hit the main repos, mountall 2.15. It might take a little bit to roll out to your mirror if your not using the main one (although if it hasn't rolled out to yours by now I would probably change to a different repo).

---

### Post by Linuxforall on 2010-05-16
There was a mountall update here in India yesterday evening.

---

### Post by finngruwier on 2010-05-18
Since I upgraded to 10.04 the disk check always stops at 72%. Pressing C doesn't work. The system usually starts over without disk check if I press Ctrl+Alt+Delete. Anyway, this morning something else happened: when I pressed Ctrl+Alt+Delete I was warned about "serious errors to the file system.". I could then log into a shell as root - and it turned out that the whole /home directory had gone! Luckily I made a manual backup of my home directory just two days ago (I had to do it manually since both Sbackup and Deja Dup has been defective since I upgraded to 10.04). Anyway, before I managed to restore the backup the /home directory was suddenly back!

This is just not good enough. Ubuntu should beta test their products for a longer period before releasing them.

---

### Post by chiwi on 2010-05-19
if your HD has errors, the best thing you can do is fsck it. However you should NOT fsck the partition when it's mounted. You should boot off a live cd, and fsck from there. 

It has happened a lot of times to me. I believe it's because the torrent downloader application is screwing the HD, i don't know for sure yet.

---

