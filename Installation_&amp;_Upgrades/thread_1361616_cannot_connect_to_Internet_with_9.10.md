---
title: "cannot connect to Internet with 9.10"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by ianinsuffolk on 2009-12-22
have successfully used Ubuntu for years and just upgraded to 9.10.  For the first time I have a problem.  Use a wired connection into a D-Link 4 port router, which works two PC's (one wondoz) and a Skype phone. Latter two working fine but have tried everything I can think of to get 9.10 to connect.

The Ubuntu PC tells me I'm connected, the tests say I'm connected, but not true....

I've attached the system report file in the hope that someone can get me onto the ne!  I hate using windoz, even with Firefox,as it's so leaky!!!!

Ian

---

### Post by elliotbeken on 2009-12-22
the zip does not work that you attached..

have you made sure the ip address is in the correct range.

the best bet is to add a static address and dont use the dhcp (auto) setting...

hope this helps

---

### Post by coffeecat on 2009-12-22
> **elliotbeken said:**
> the zip does not work that you attached..

Worked for me but you get a 17,000+ word document. :shock:

@ianinsuffolk, I couldn't wade through that lot - life is too short! But I found this from your lspci output:

> 

00:05.0 Bridge [0680]: nVidia Corporation CK8S Ethernet Controller [10de:00df] (rev a2)
        Subsystem: ASRock Incorporation Device [1849:00df]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0 (250ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        Region 1: I/O ports at ec00 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: forcedeth
Kernel modules: forcedethThere shouldn't be a problem with a nvidia ethernet controller and the forcedeth driver. Unfortunately that output from checkbox didn't include some information that would be helpful here. Or if it was there, I couldn't see it. Open a terminal and post the output of these two:

```
sudo lshw -C network
iwconfig
```Please paste the output into [noparse]```

```[/noparse] tags and not into an attachment.

---

### Post by ianinsuffolk on 2009-12-23
[QUOTE=coffeecat;8541907]Worked for me but you get a 17,000+ word document. :shock:

@ianinsuffolk, I couldn't wade through that lot - life is too short! But I found this from your lspci output:

There shouldn't be a problem with a nvidia ethernet controller and the forcedeth driver. Unfortunately that output from checkbox didn't include some information that would be helpful here. Or if it was there, I couldn't see it. Open a terminal and post the output of these two:

```
sudo lshw -C network
iwconfig
```Please paste the output into [noparse]```

```[/noparse] tags and not into an attachment.[/QUOTE

As these ideas did notseem to work, I put on 9.04 again.  This worked perfectly.  I then used the update programme, to put a dual boot system, with 9.04 and 9.10.

As you might have guess, 9.04 works on the internet but 9.10 does not.  So, until a definitive answer is forthcoming (I am a business, not an enthusiast) I will continue to use 9.04.

Regards Ian

---

### Post by coffeecat on 2009-12-23
> **ianinsuffolk said:**
> As these ideas did notseem to work, I put on 9.04 again.

Well no, they wouldn't. :| They were commands to get more information to try to see why your ethernet wasn't working.

---

### Post by SuperEngineer on 2009-12-28
In case it helps...
this is a very common problem with USB wireless adaptors in 9.10 and is solvable in less than five minutes - maybe someone could suggest a similar for hard wired....?

                 Workaround discussed in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460323) has provided a fix for now but ... this issue is still a bug for correction prior to next release to maintain Ubuntu's good reputation.
 workaround details...
 Fixed with:
 Step1: add "blacklist rt2800usb" to:
           /etc/modprobe.d/blacklist.conf
Step2: add "rt2870sta" to:
           /etc/modules
Step3: Reboot.
 Connectivity now working as per Jaunty.

---

### Post by SuperEngineer on 2009-12-28
...btw, it might also be worth checking the 'Networking & Wireless' forum.

Good luck.

---

### Post by ianinsuffolk on 2010-01-02
Thanks for this helpful reply.  I have been 'doing Christmas' so can now get back to business work.  I am using a hard wired connection.

I have just installed a new router so all should be interesing....

Ian

---

