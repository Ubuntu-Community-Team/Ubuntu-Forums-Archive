---
title: "eciadsl - modem hangup"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by Lifman on 2006-03-27
hi,
i'm using a "fresh" pc - only ubuntu and eciadsl stuff on it,
and i want to get online...
i've configured eciadsl according to welsh_spud's excellent guide,
and it seemed to recognize both my adsl modem (ale 130) and my
provider (Netvision).
eciadsl-start sets up and uploads firmware (steps 1+2) OK
synch phase gives me two "failed" results, but some how ends with "Synchronization successful"
but then it starts "connecting to provider" and fails 10 times.
it says "Script /usr/bin/eciadsl -pppoeci -vpi 8 -vci 48 -vendor 0x1690 -product 0x0211 -mode VCM_RFC2364 finished (pid 7435), status = 0x0
Modem hangup
Connection terminated"
any idea what i should do next? am i on the right track until now?

---

### Post by Kakistos on 2006-03-29
I've got a similar problem.  If I add it to this thread, when someone solves your problem, they might know how to solve mine.

I've got a fresh install of Dapper, eciadsl software installed.  I type in eciadsl-start and get so far, then I get an error and fail to connect.  

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is missing... trying to mount

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

Ok eciadsl-synch: success
Synchronization successful

[EciAdsl 3/5] Connecting to provider...

sh: /usr/local/adsl/pppoeci: No such file or directory
Couldn't get channel number: Input/output error
Script /usr/local/adsl/pppoeci -v 1 -vpi 0 -vci 38 -vendor 0x1905 -product 0x204 finished (pdi 5066), status = 0x7f
ERROR: failed to connect

Any ideas.  

C

---

### Post by yotam on 2006-10-06
Just failed trying to configure eci-adsl for a friennd
having ADSL-USB ALE-130 modem which connects well
under M$Windoz to NetVision via Bezeq.

Since I am away from that machine, I do not have exact data. I have installed XUbuntu-6.0 dapper
and insatleld the binary I fetched from:

[http://mirrors.dotsrc.org/ubuntu/pool/universe/e/eciadsl/eciadsl_0.11-3_i386.deb](http://mirrors.dotsrc.org/ubuntu/pool/universe/e/eciadsl/eciadsl_0.11-3_i386.deb)

I have noticed that it misses several scripts, 
such as the eciadsl-config-text
that come with
[http://eciadsl.flashtux.org/download/eciadsl-usermode-0.11.tar.bz2](http://eciadsl.flashtux.org/download/eciadsl-usermode-0.11.tar.bz2)

Can anyone puclish working configuration file(s)
that are known to work for this modem?

thanks

---

