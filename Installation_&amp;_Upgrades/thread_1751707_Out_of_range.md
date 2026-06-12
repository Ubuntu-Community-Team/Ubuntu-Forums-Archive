---
title: "Out of range"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by jmdlcar on 2011-05-07
I just install 11.04 64 bit and when it is booting up I get out of range but it dose boot.

---

### Post by MAFoElffen on 2011-05-07
> **jmdlcar said:**
> I just install 11.04 64 bit and when it is booting up I get out of range but it dose boot.
Have you looked at the sys logs to see if the error is kernel or graphics related?

---

### Post by jmdlcar on 2011-05-07
Where will find those logs?

---

### Post by jmdlcar on 2011-05-07
Will a reinstall help or not?

---

### Post by MAFoElffen on 2011-05-07
> **jmdlcar said:**
> Where will find those logs?
The syslog is at "/var/log/syslog"

> 
Will a reinstall help or not?
Maybe or maybe not...  I'm thinking if you could reinstall... it couldn't hurt.  Something is going on / posting a syslog "before" you do. would give you a clue on what is going on.

---

### Post by jmdlcar on 2011-05-07
Here the syslog.

May  7 08:05:37 jack-D5468AT-ABA-ALONPAV rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="726" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May  7 08:05:50 jack-D5468AT-ABA-ALONPAV anacron[3247]: Job `cron.daily' terminated
May  7 08:05:50 jack-D5468AT-ABA-ALONPAV anacron[3247]: Normal exit (1 job run)
May  7 08:11:39 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 08:11:40 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 08:11:40 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1718 seconds.
May  7 08:17:01 jack-D5468AT-ABA-ALONPAV CRON[3499]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 08:40:18 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 08:40:19 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 08:40:19 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1773 seconds.
May  7 09:09:52 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 09:09:53 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 09:09:53 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1524 seconds.
May  7 09:17:01 jack-D5468AT-ABA-ALONPAV CRON[3552]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 09:35:17 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 09:35:18 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 09:35:18 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1695 seconds.
May  7 10:03:33 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 10:03:34 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 10:03:34 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1601 seconds.
May  7 10:17:01 jack-D5468AT-ABA-ALONPAV CRON[3602]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 10:30:15 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 10:30:16 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 10:30:16 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1710 seconds.
May  7 10:58:46 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 10:58:47 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 10:58:47 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1684 seconds.
May  7 11:17:01 jack-D5468AT-ABA-ALONPAV CRON[3634]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May  7 11:26:51 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 11:26:52 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 11:26:52 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1751 seconds.
May  7 11:56:03 jack-D5468AT-ABA-ALONPAV dhclient: DHCPREQUEST of 192.168.0.3 on eth0 to 192.168.0.1 port 67
May  7 11:56:04 jack-D5468AT-ABA-ALONPAV dhclient: DHCPACK of 192.168.0.3 from 192.168.0.1
May  7 11:56:04 jack-D5468AT-ABA-ALONPAV dhclient: bound to 192.168.0.3 -- renewal in 1743 seconds.
May  7 12:17:01 jack-D5468AT-ABA-ALONPAV CRON[3833]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

---

### Post by kansasnoob on 2011-05-07
After it does boot do you have a functioning display?

---

### Post by kansasnoob on 2011-05-07
> **jmdlcar said:**
> Will a reinstall help or not?

Very doubtful.

---

### Post by jmdlcar on 2011-05-07
> **kansasnoob said:**
> After it does boot do you have a functioning display?

After it boot up everything works great.

---

### Post by Hedgehog1 on 2011-05-07
Is the 'out of range' error coming up from the Monitor during boot? Is the video scrambled for a bit when this happens?

***The Hedge***

:KS

---

### Post by jmdlcar on 2011-05-07
> **Hedgehog1 said:**
> Is the 'out of range' error coming up from the Monitor during boot? Is the video scrambled for a bit when this happens?

***The Hedge***

:KS


I see it when it start to boot then it ask to login but the mouse froze up for 10 sec.

---

### Post by kansasnoob on 2011-05-08
I think there's a problem with Natty's grub2 ...... errm the way it reads vbeinfo ..... maybe the way it parses EDID info for some monitors. I wrote the following post to address what I think is a different problem but it explains how to purge and reinstall Natty's grub2, and also how to revert to Maverick's grub2:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Please ignore the rest of that thread, I just used it as a placeholder for those notes so I didn't need to redo it every time :)

Browse that and see if you have any questions before proceeding, I'll subscribe to this thread so I can hopefully answer any questions you might have.

---

### Post by MAFoElffen on 2011-05-08
> **kansasnoob said:**
> I think there's a problem with Natty's grub2 ...... errm the way it reads vbeinfo ..... maybe the way it parses EDID info for some monitors. I wrote the following post to address what I think is a different problem but it explains how to purge and reinstall Natty's grub2, and also how to revert to Maverick's grub2:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Please ignore the rest of that thread, I just used it as a placeholder for those notes so I didn't need to redo it every time :)

Browse that and see if you have any questions before proceeding, I'll subscribe to this thread so I can hopefully answer any questions you might have.
@kansasnoob. Okay- I'm trying to keep this on topic, but I have questions on what you said...

First, your notes- It's good notes for reinstalling grub.  The thread you use for reference is a guide for Repairing Grub2 with Grub2, written by drs395, whom I have the highest respect and regard of... who himself says that Natty's grub2 should be repaired not only with Grub2, but by Natty's Grub version 1.99.  1.99 has new features that natty "uses."

Simplistic explanation of graphics changes
 - 9.10 graphics modes were dealt with in xorg and the video drivers.
- 10.04 introduces KMS, (kernel mode switching) where graphics modes were set in the kernel and passed to xorg.
 - 10.10 has some more changes with this... Trying to find and set the graphics modes and pass it to Xorg.
 - Natty and Grub 1.99 have ingrained changes tied to KMS.  Grub tries to find and set the graphics, which it then passes to the kernel, which then passes in to xorg.  That's why you now have the graphics changes happening as soon as the Grub Menu...

Most of the people that I've helped correct their blank screen prroblems with Natty have been by setting the WIDTHxHEIGHTxDEPTH parameters of a mode that "their" graphics hardware supports.  (Notice that there are "3" parameters there.)  There have been a few other "instances" where there was some other things going on or the "current" kernel "did not support or lost" graphics support for... (The kernel in proposed fixes a lot of those) But the majority was...   

I have asked around... and no-one wants to talk about KMS.  I've asked in many places at Ubuntu and Conical (where I thought I could get some answers) about any kind of documentation on KMS and the -kms.conf files... but all have been ignored. There is 1 short wiki page that skims over it briefly, with no refrences for anything else.  I know that kernel boot parameters are a part of it.  I know that Grub 1.99's GFXMODE and GFXTERM are a part of it.

Reference, this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I know that the default of GFXMODE=auto is causing a lot of blank screens as it tries modes until it lands on one that deos not return an error code... even though that instance may be invalid or out-of-range.

So-- You say you have some other or additional insight into this?  I'm game.  No one else is talking about this.  Honestly,_ I "am" very interested in this_ and any other work-around's that anyone has and that may help.  Please explain how you see what is going on with this.   Or should we start our own thread to talk about that?

@ the original subject-- I've only seen 2 different things so far (still might be something new, but so far) causing an out-of-range error to be reported as that (a displayed out-of-range error) by natty:  Graphics mode out-of-range and kernel error reporting out-of-range error...  Might be different... 

Both those problems can be corrected without a complete reinstall.

---

### Post by jmdlcar on 2011-05-08
> **kansasnoob said:**
> I think there's a problem with Natty's grub2 ...... errm the way it reads vbeinfo ..... maybe the way it parses EDID info for some monitors. I wrote the following post to address what I think is a different problem but it explains how to purge and reinstall Natty's grub2, and also how to revert to Maverick's grub2:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Please ignore the rest of that thread, I just used it as a placeholder for those notes so I didn't need to redo it every time :)

Browse that and see if you have any questions before proceeding, I'll subscribe to this thread so I can hopefully answer any questions you might have.

So I need to do step1-step6. Step 4 I don't need to do. I will use step 5. Is that right?

---

### Post by kansasnoob on 2011-05-08
> **MAFoElffen said:**
> @kansasnoob. Okay- I'm trying to keep this on topic, but I have questions on what you said...

First, your notes- It's good notes for reinstalling grub.  The thread you use for reference is a guide for Repairing Grub2 with Grub2, written by drs395, whom I have the highest respect and regard of... who himself says that Natty's grub2 should be repaired not only with Grub2, but by Natty's Grub version 1.99.  1.99 has new features that natty "uses."

Simplistic explanation of graphics changes
 - 9.10 graphics modes were dealt with in xorg and the video drivers.
- 10.04 introduces KMS, (kernel mode switching) where graphics modes were set in the kernel and passed to xorg.
 - 10.10 has some more changes with this... Trying to find and set the graphics modes and pass it to Xorg.
 - Natty and Grub 1.99 have ingrained changes tied to KMS.  Grub tries to find and set the graphics, which it then passes to the kernel, which then passes in to xorg.  That's why you now have the graphics changes happening as soon as the Grub Menu...

Most of the people that I've helped correct their blank screen prroblems with Natty have been by setting the WIDTHxHEIGHTxDEPTH parameters of a mode that "their" graphics hardware supports.  (Notice that there are "3" parameters there.)  There have been a few other "instances" where there was some other things going on or the "current" kernel "did not support or lost" graphics support for... (The kernel in proposed fixes a lot of those) But the majority was...   

I have asked around... and no-one wants to talk about KMS.  I've asked in many places at Ubuntu and Conical (where I thought I could get some answers) about any kind of documentation on KMS and the -kms.conf files... but all have been ignored. There is 1 short wiki page that skims over it briefly, with no refrences for anything else.  I know that kernel boot parameters are a part of it.  I know that Grub 1.99's GFXMODE and GFXTERM are a part of it.

Reference, this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I know that the default of GFXMODE=auto is causing a lot of blank screens as it tries modes until it lands on one that deos not return an error code... even though that instance may be invalid or out-of-range.

So-- You say you have some other or additional insight into this?  I'm game.  No one else is talking about this.  Honestly,_ I "am" very interested in this_ and any other work-around's that anyone has and that may help.  Please explain how you see what is going on with this.   Or should we start our own thread to talk about that?

@ the original subject-- I've only seen 2 different things so far (still might be something new, but so far) causing an out-of-range error to be reported as that (a displayed out-of-range error) by natty:  Graphics mode out-of-range and kernel error reporting out-of-range error...  Might be different... 

Both those problems can be corrected without a complete reinstall.

I'm not sure where to start :(

Maybe from the last going backwards:

> Both those problems can be corrected without a complete reinstall.

Who's suggesting a complete reinstall? The procedure(s) shown in that post are simply a matter of eliminating a problem :confused:

> @ the original subject-- I've only seen 2 different things so far (still might be something new, but so far) causing an out-of-range error to be reported as that (a displayed out-of-range error) by natty:  Graphics mode out-of-range and kernel error reporting out-of-range error...  Might be different... 


So only two, or a few, means it's a fluke we should ignore :confused:

> So-- You say you have some other or additional insight into this?  I'm game.  No one else is talking about this.  Honestly,_ I "am" very interested in this_ and any other work-around's that anyone has and that may help.  Please explain how you see what is going on with this.   Or **should we start our own thread to talk about that?**

Yes we should discuss this elsewhere! In the meantime maybe you should offer a solution to the OP's problem :)

BTW it's drs305 not drs395, and I already made contact:

[http://ubuntuforums.org/showthread.php?t=1581099&page=17](http://ubuntuforums.org/showthread.php?t=1581099&page=17)

I'll admit that I find your response personally troubling. Why question me rather than offer a solution?

---

### Post by kansasnoob on 2011-05-08
> **jmdlcar said:**
> So I need to do step1-step6. Step 4 I don't need to do. I will use step 5. Is that right?

Since you didn't include the output of:

```
uname -m
```

I can't be sure if you need to follow the 32bit or 64bit instructions :confused:

The disc I recommend in step #1 is not needed if you can boot into your Natty but I'm very impressed with that particular disc. It seems to boot almost anything if it's bootable :)

I really don't know how I can make things more clear than I have.

---

### Post by jmdlcar on 2011-05-09
> **kansasnoob said:**
> Since you didn't include the output of:

```
uname -m
```

I can't be sure if you need to follow the 32bit or 64bit instructions :confused:

The disc I recommend in step #1 is not needed if you can boot into your Natty but I'm very impressed with that particular disc. It seems to boot almost anything if it's bootable :)

I really don't know how I can make things more clear than I have.

jack@jack-D5468AT-ABA-ALONPAV:~$ uname -m
x86_64
jack@jack-D5468AT-ABA-ALONPAV:~$

---

