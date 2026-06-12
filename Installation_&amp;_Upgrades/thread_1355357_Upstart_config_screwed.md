---
title: "Upstart config screwed"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by squarooticus on 2009-12-14
For reference, the last time I installed my system was back with Intrepid; I have since upgraded through Jaunty to Karmic.

Now it seems my startup config (meaning upstart) is completely and utterly ******.  The problem is twofold: first, it doesn't start ssh or cups or any of the gettys on the virtual consoles (among other things); second, it seems to log *nothing* useful about what it's doing, so I have no visibility into the system.  What is it executing?

Furthermore, why are there /etc/event.d turds left over?  Didn't that all move to /etc/init?  And shouldn't everything basic have been moved from /etc/init.d to /etc/init already, like ssh and cups?

I also like how the output of the runlevel command is "unknown".  That doesn't give me warm-fuzzies.

I have done nothing to touch this config: it got screwed on its own without any help from me.  Now I just want to debug what's going on.  A good first step would be for someone to give me an idea of how to know what the hell this thing is doing when I boot.  I would rather not have to reinstall to fix this problem, but Ubuntu is becoming more Windows-like as time progresses: more and more stuff going on under the covers with little in the way of human-readable information about it.

As a long-time Ubuntu user (way back from the Breezy days), I am appalled by how poorly executed this switch to upstart has been, and generally how little qualification seems to be done for each release.  Things like pulseaudio *still* don't work out of the box, even on relatively recent hardware, and again with no information indicating a failure beyond it simply not working.

Sorry for the rant, but this is completely ridiculous.

---

### Post by squarooticus on 2009-12-20
After scouring other message forums due to the lack of proper documentation, the problem appears to be that net-device-up doesn't work, at least as intended.  I went into /etc/init and replaced every instance of "net-device-up" with "net-device-added", and for kicks also replaced every instance of "IFACE=" with "INTERFACE=".  Now all services start properly on boot.

The problem with the gettys, the runlevel "unknown", and sshd were all a result of tty*.conf and rc-sysinit.conf not executing: the net-device-up IFACE=lo requirement was never met, which meant none of those services were started, nor was telinit 2 executed.

I don't see how this could have gotten out of testing.  Can someone please explain it to me?  As one of my first debugging steps, I even purged upstart and reinstalled it, and the same broken versions of rc-sysinit.conf, tty*.conf, etc. were reinstalled.  I simply don't understand how such a critical package in such a broken state could get past minimal qualification testing.  We're not talking about an obscure bug here: this is the "beaten over the head with a lead pipe" kind of bug.

---

### Post by ozonito on 2009-12-20
I have my runlevel in unknown too, i hope the urgency is very low, because i am an spanish newbee. Thank for the post anyway and excuse my poor english.

---

### Post by pallinger on 2009-12-21
> **squarooticus said:**
> After scouring other message forums due to the lack of proper documentation, the problem appears to be that net-device-up doesn't work, at least as intended.
For me, changing the mainboard (and thus some of the ethernet interfaces) triggered the error.
Purging network-manager did the trick, everything was properly configured in the old /etc/networking/interfaces. :)

> **squarooticus said:**
> I don't see how this could have gotten out of testing.  Can someone please explain it to me?  As one of my first debugging steps, I even purged upstart and reinstalled it, and the same broken versions of rc-sysinit.conf, tty*.conf, etc. were reinstalled.  I simply don't understand how such a critical package in such a broken state could get past minimal qualification testing.  We're not talking about an obscure bug here: this is the "beaten over the head with a lead pipe" kind of bug.
The worst thing was that there was no useful logging in /var/log/dmesg or syslog, only some cryptic errors in daemon.log.
I only started to suspect the whole upstart mess as I saw the 'unknown' runlevel.

---

### Post by ibuclaw on 2009-12-21
This happens because of a broken/malconfigured /etc/network/interfaces file.

[This bug report]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/461725") is the reason for updating upstart.
[This regression report]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/497299") is the consequence to some users.

I fixed mine by changing the contents of /etc/network/interfaces to:
```

auto lo
iface lo inet loopback

```
Before changing - it was empty.

Regards
Iain

---

### Post by ozonito on 2009-12-21
Hi again.

I changed my /etc/networking/interfaces to config my server, but in jaunty i not have this problem.
It is uncomfortable to have to run always #telinit X to start services, but my knowledge is also a more yet.
Finally I would like to know if there are one solution or resign myself to wait.

Thanks a lot.

---

### Post by squarooticus on 2009-12-21
> **ozonito said:**
> Hi again.

I changed my /etc/networking/interfaces to config my server, but in jaunty i not have this problem.
It is uncomfortable to have to run always #telinit X to start services, but my knowledge is also a more yet.
Finally I would like to know if there are one solution or resign myself to wait.

Thanks a lot.

We are having it out on the 497299 bug page.  Hopefully, we'll have an answer soon.

---

### Post by ozonito on 2009-12-21
I just fix it by changing IFACE=lo to IFACE=eth0 in /etc/init/rc-sysinit.conf.

hopefully a newbee. 
He posted in case anyone serves (Oh yeah!!!)

Thanks a lot again.

---

### Post by Louigi Verona on 2009-12-22
Guys, is this bug responsible for some scripts in sysf.conf and modprobe.d to be ignored during boot? I am using an ASUS laptop which has an ambient light sensor problem and I had a script that turned the sensor off on boot - after latest upgrade it stiooed working and I can only turn off the sensor manually from terminal under sudo su. Is this related?
 

Also - if it is related - can anyone please provide instructions on how to downgrade upstart? I am not a tech guy and I dunno how to do it.

---

### Post by Louigi Verona on 2009-12-22
Anyone?

---

### Post by Louigi Verona on 2009-12-23
Downgraded upstart - that fixed everything.

---

### Post by superyounan1 on 2010-05-15
> **ozonito said:**
> I just fix it by changing IFACE=lo to IFACE=eth0 in /etc/init/rc-sysinit.conf.

hopefully a newbee. 
He posted in case anyone serves (Oh yeah!!!)

Thanks a lot again.

Here I am having the same problem 5 months later with a newer release (Lucid), but this worked for me, thanks man!

I did this and I finally have my auto-services back! It was driving me especially batty since my interfaces file already had 'auto lo' and 'iface lo inet loopback' defined, but this did the trick. 

I understand the concept of run-levels and a web of scripts supporting them is a system that is proven, but this was one of those times where I just wished I could use something like the Windows Services manager and just right click on my services to choose "start automatically".

---

### Post by Kent Asplund on 2010-05-25
> **ozonito said:**
> I just fix it by changing IFACE=lo to IFACE=eth0 in /etc/init/rc-sysinit.conf.

hopefully a newbee. 
He posted in case anyone serves (Oh yeah!!!)

Thanks a lot again.

Unfortunately this is causing services to fail when you do not have your network cable connected. I think that you/we are affected by bug 543506 : [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

I suggest this workaround instead:
Change  /etc/init/network-manager.conf where the lines read:
 [FONT=Courier New]start on (local-filesystems
              and started dbus)[/FONT]
into:

 [FONT=Courier New]start on (local-filesystems
              and started dbus
              and started networking)[/FONT]
 
This is causing Network-Manager to wait for "lo" to be created and everything magically works.

---

### Post by oreodoh on 2012-02-21
> **Kent Asplund said:**
> Unfortunately this is causing services to fail when you do not have your network cable connected. I think that you/we are affected by bug 543506 : [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

I suggest this workaround instead:
Change  /etc/init/network-manager.conf where the lines read:
 [FONT=Courier New]start on (local-filesystems
              and started dbus)[/FONT]
into:

 [FONT=Courier New]start on (local-filesystems
              and started dbus
              and started networking)[/FONT]
 
This is causing Network-Manager to wait for "lo" to be created and everything magically works.

This might be bad advice for some. I did this and after rebooting, my system no longer boots!

This is a much worse problem than booting to an "unknown" runlevel. Now I have an even bigger problem on my hands. #-o

I'm running Ubuntu 10.04.3 LTS, by the way. Or at least I was.

---

### Post by oreodoh on 2012-02-21
> **squarooticus said:**
> I went into /etc/init and replaced every instance of "net-device-up" with "net-device-added", and for kicks also replaced every instance of "IFACE=" with "INTERFACE=".  Now all services start properly on boot.


Thank you thank you thank you! This worked for me when just about every other solution out there failed miserably! :)

---

### Post by oreodoh on 2012-02-21
In case anyone else gets bitten by this one, I was able to get back into the system by editing the kernel line in GRUB during boot. I appended "init=/bin/bash", which drops you to a root shell. The only other thing I had to do was make the root (/) file system writable:

mount -o remount,rw /

Then I edited /etc/init/network-manager.conf and removed the "and started networking" reference.

I am sure this solution works for some, but wow. It totally screwed me. Go ahead and try it if you like, but be prepared to roll back the changes if it renders your computer useless like it did mine.

The solution that worked for me was posted by squarooticus.

---

### Post by oldos2er on 2012-02-21
Closed, necromancy.

---

