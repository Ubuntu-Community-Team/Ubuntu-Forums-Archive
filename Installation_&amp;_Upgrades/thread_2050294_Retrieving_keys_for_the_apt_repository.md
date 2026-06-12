---
title: "Retrieving keys for the apt repository"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-08-30
I'm running Kubuntu 12.04 and trying to update it. I've again been hit by a problem I had a year ago that's never been solved, illustrated by this:

```
pwa@pwa-K60IJ:~/Documents$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

The problem is not with the choice of keyserver; I've tried several, all with the same behavior.  I've opened port 11371, which some people thought might be the problem.  And I can ping any of the keyservers, so the "Host not found" message is bogus.  Apparently the line I quoted works for some people but not for others (like me).  I can painfully get the key by going to the site and retrieving it directly and then installing it explicitly, but that's hardly a satisfactory solution, particularly when I have to get several keys.

---

### Post by oldos2er on 2012-08-30
```
sudo apt-key adv --keyserver subkeys.pgp.net --recv-keys A8AA1FAA3F055C03
``` worked for me.

---

### Post by pwabrahams on 2012-08-30
That command works for many -- perhaps most -- people, but it doesn't work for me.  The question is why.  I'm beginning to think that some program I installed twiddled the invisible network settings -- the ones that don't show up in Systems Settings.  But that's just a guess.

---

### Post by oldos2er on 2012-08-30
You're not behind a proxy, are you? 

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8AA1FAA3F055C03
``` also worked, for what it's worth.

---

### Post by pwabrahams on 2012-08-30
I'm pretty sure I'm not behind a proxy server, since (a) I never set one up, and (b) System Settings says that I'm not.  But I'm wondering whether something crept into my system that makes it *appear* that I'm behind a proxy server.  Is there any way to check for that?

---

### Post by oldos2er on 2012-08-31
I don't know, I'm mostly ignorant about networking. If you don't get an answer here in a day or two, try asking your proxy question in the Networking & Wireless subforum.

---

### Post by pwabrahams on 2012-08-31
I thought I might find something revealing in the system log, so I got this:
```
pwa@pwa-K60IJ:/var/log$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03; tail syslog
gpg: requesting key 3F055C03 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Successfully made thread 2254 of process 2245 (n/a) owned by '1001'  at priority 5.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Supervising 2 threads of 1 processes of 1 users.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Successfully made thread 2255 of process 2245 (n/a) owned by '1001'  at priority 5.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Supervising 3 threads of 1 processes of 1 users.
Aug 31 20:14:48 pwa-K60IJ hp-systray: hp-systray[2308]: warning: No hp: or hpfax: devices found in any installed CS queue. Exiting.
Aug 31 20:17:25 pwa-K60IJ CRON[2707]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 20:23:48 pwa-K60IJ kernel: [  688.333041] show_signal_msg: 39 callbacks suppressed
Aug 31 20:23:48 pwa-K60IJ kernel: [  688.333050] nepomukservices[2908]: segfault at 48 ip 00007f36e9c66590 sp 0000ff6a803868 error 4 in libQtCore.so.4.8.2[7f36e9b64000+2c6000]
Aug 31 20:24:52 pwa-K60IJ kernel: [  752.801554] nepomukservices[3080]: segfault at 400000000008 ip 00007fa002e275 sp 00007fffc9219d08 error 4 in libQtCore.so.4.8.2[7fa002d25000+2c6000]
Aug 31 20:25:32 pwa-K60IJ kernel: [  792.565254] nepomukservices[3150]: segfault at 48 ip 00007f15150b0590 sp 0000ff416e1f58 error 4 in libQtCore.so.4.8.2[7f1514fae000+2c6000]

```
I don't know where nepomukservices is in the chain of causality, but it does seem surprising to find it here.

---

### Post by drmrgd on 2012-08-31
> **pwabrahams said:**
> I thought I might find something revealing in the system log, so I got this:
```
pwa@pwa-K60IJ:/var/log$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys A8AA1FAA3F055C03; tail syslog
gpg: requesting key 3F055C03 from hkp server subkeys.pgp.net
?: subkeys.pgp.net: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Successfully made thread 2254 of process 2245 (n/a) owned by '1001'  at priority 5.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Supervising 2 threads of 1 processes of 1 users.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Successfully made thread 2255 of process 2245 (n/a) owned by '1001'  at priority 5.
Aug 31 20:14:31 pwa-K60IJ rtkit-daemon[2247]: Supervising 3 threads of 1 processes of 1 users.
Aug 31 20:14:48 pwa-K60IJ hp-systray: hp-systray[2308]: warning: No hp: or hpfax: devices found in any installed CS queue. Exiting.
Aug 31 20:17:25 pwa-K60IJ CRON[2707]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 31 20:23:48 pwa-K60IJ kernel: [  688.333041] show_signal_msg: 39 callbacks suppressed
Aug 31 20:23:48 pwa-K60IJ kernel: [  688.333050] nepomukservices[2908]: segfault at 48 ip 00007f36e9c66590 sp 0000ff6a803868 error 4 in libQtCore.so.4.8.2[7f36e9b64000+2c6000]
Aug 31 20:24:52 pwa-K60IJ kernel: [  752.801554] nepomukservices[3080]: segfault at 400000000008 ip 00007fa002e275 sp 00007fffc9219d08 error 4 in libQtCore.so.4.8.2[7fa002d25000+2c6000]
Aug 31 20:25:32 pwa-K60IJ kernel: [  792.565254] nepomukservices[3150]: segfault at 48 ip 00007f15150b0590 sp 0000ff416e1f58 error 4 in libQtCore.so.4.8.2[7f1514fae000+2c6000]

```
I don't know where nepomukservices is in the chain of causality, but it does seem surprising to find it here.

I think there's a bug in nepomukservices in the most recent patch.  Since the upgrade to KDE 4.9 on my system, nepomukservices has been crashing off and on too.  I can't seem to get enough info to file a bug report, though.  At any rate, I think it's an independent problem from the key server problem you're having.

---

### Post by pwabrahams on 2012-09-01
"Host not found", the man said.  So I replaced the hostname by its IP address -- and lo and behold, the key retrieval succeeded!  Of course, this workaround should not be necessary.

---

