---
title: "Thunderbird in 10.04....problem"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Rodhill on 2010-05-04
I have done a clean install of Ubuntu 10.04 on my laptop. However I don't like Evolution mail client and installed Thunderbird from the repositories. It installed fine and comes up with the wizard to fill account details in but for some reason you can't input anything from the keyboard - it seems greyed out.
I tried uninstalling and re-installing but it's still the same.
Everything else is fine and working.
Any ideas anyone?

Rod

---

### Post by Mice Elf on 2010-05-06
Hi, i´m also experiencing the same problem with my laptop after a new 10.04 installation, at the moment i´m using Evolution but  i would rather use Thunderbird....

Somebody help!

---

### Post by gkseifert on 2010-05-06
I have the same problem. At first I thought it might have been a bad DVD, but i have since found the same problem installing from either CD or DVD on one machine and from DVD, but not from CD, on another. I don't think it is either disk, but something flaky in the communication between Thunderbird and the OS related to input dialogs. 
  I have found that I can actually input my account info by counting tabs and characters even though I can not see any reflection of my input at the time. The data is getting in, but the system is not reflecting anything back to the input dialog window. Later, reentering the same dialog will display what i had previously entered but could not see at the time.
  After getting the account info in, the 'new message' screen has the same problem. Input is not displayed, although it is being accepted. 
  Hope someone more familiar with reporting problems in Ubuntu runs into this and reports it so it can be fixed. I too want to use Thunderbird. It is my chosen email client in all systems. 

  Gord

---

### Post by gkseifert on 2010-05-06
I should have mentioned in my previous post that the machine that had the problem when installing from both CD and DVD is a Toshiba Tecra S1 laptop with ATI graphics and the other machine, which did not have the problem after installing from CD has an ASUS P5Q Pro Turbo MB and a GeForce GT240 video card. Clean format and install in both cases. No other modifications or installations prior to installing Thunderbird.

  Gord

---

### Post by Rodhill on 2010-05-10
> **Rodhill said:**
> I have done a clean install of Ubuntu 10.04 on my laptop. However I don't like Evolution mail client and installed Thunderbird from the repositories. It installed fine and comes up with the wizard to fill account details in but for some reason you can't input anything from the keyboard - it seems greyed out.
I tried uninstalling and re-installing but it's still the same.
Everything else is fine and working.
Any ideas anyone?

Rod

Just want to bump this one up as it is still an issue. If anyone can help the two likewise posters I would be grateful.I've tried a clean install of Thunderbird but it's still the same

---

### Post by John Bean on 2010-05-10
Very odd indeed. Thunderbird was almost the first thing I installed from a clean installation of Lucid, but in my case I copied my profile from my existing Jaunty installation before I ran it. Everything "just worked".

Since then I've amended accounts without issue, so I can only conclude that the problem seen here is either hardware related (unlikely) or something to do with Thunderbird's default profile - which of course I had overwritten before the first run.

---

### Post by tilwell on 2010-05-31
Hi,
I have the same problem. (I have an IBM R50 8 years old - no idea what grafic is in there)
I could at least see the fields if I enlarged the windows to maximum. And after blindly entering the text click into another field and magically the entered text appeared.
But that's not how I want to work with Thunderbird.
Anyone any ideas?!

---

### Post by Rodhill on 2010-06-13
Well I've managed to install Thunderbird ok by switching off 'Visual Effects' to 'none' and it works as it should, however if you apply advanced effects it plays up again:confused:

This appears to be a bug or something so might there be a cure?

Rod

---

### Post by shewolf on 2010-06-13
I have also a problem with Thunderbird in Ubuntu 10.04 LTS and I can;t send email only received email. Please help me.

Regards,

Shewolf

---

### Post by Rodhill on 2010-06-14
> **shewolf said:**
> I have also a problem with Thunderbird in Ubuntu 10.04 LTS and I can;t send email only received email. Please help me.

Regards,

Shewolf

It's bound to be a setting somewhere. The best thing to do is to go to your ISP's site and there probably will be a 'how to' to set up Thunderbird. I had to do that for my TalkTalk ISP. You only need an incorrect spelling or full stop in the wrong place and it won't work.

Rod

---

### Post by gkseifert on 2010-07-05
> **Rodhill said:**
> Well I've managed to install Thunderbird ok by switching off 'Visual Effects' to 'none' and it works as it should, however if you apply advanced effects it plays up again:confused:

This appears to be a bug or something so might there be a cure?

Rod


  Your mention of setting visual effects to none sounds very much like this known and verified bug. Unfortunately they have not seen fit to assign it to anyone yet. I won't move to Lucid until they fix this.

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/555382](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/555382)

   Gord

---

### Post by JohnsonMR on 2010-07-07
Same problem here.  It stopped working with the Thunderbird upgrade within the last couple of days.  I'm running 10.04LTS and Thunderbird 3.0.5.

Visual effects was already set to None.

---

