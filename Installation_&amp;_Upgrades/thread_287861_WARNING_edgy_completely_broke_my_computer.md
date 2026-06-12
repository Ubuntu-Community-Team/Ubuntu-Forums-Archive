---
title: "WARNING: edgy completely broke my computer"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by realn on 2006-10-29
1) Downloaded edgy
2) Burnt the CD
3) Booted the system
4) When the status bar almost completed - frozen screen
5) Rebooted the computer without any CD - blank screen 
6) Unusable screen (the TV and CRT connections still worked).

NOTES:
1) System: Toshiba Satellite A100 with WinXP & Suse 10.0.
2) The first time in my life when I got a piece of hardware broken because of a piece of software.
3) The first time in my life (and most probably the last time) that I ever (tried to) used Ubuntu.

Please report in this thread exactly the same problem and the sollution, too. The solution I found: get the laptop back to the store (fortunately still under warranty).

---

### Post by invalid on 2006-10-29
> 5) Rebooted the computer without any CD - blank screen
What happens if you reboot with the CD?

---

### Post by realn on 2006-10-29
Either with or without any CD - no power on the screen - totally blank (in fact black). As I said the hardware was somehow damaged. The laptop has been sent to Toshiba (I hope they can fix/replace the fault).
 A hardware damage through a software manipulaiton is quite a bad thing, I would say.

---

### Post by Catsworth on 2006-10-29
> **realn said:**
> [...]A hardware damage through a software manipulaiton is quite a bad thing, I would say.

Yup.....and just about near on impossible.....

Edgy would need to have done something to the firmware (BIOS or whatever) on your laptop.....AFAIK it doesn't have any way of doing that.

Is it possible that the death of the screen and the installation of Edgy are not linked, and that one just so happened to coincide with the other?

---

### Post by Catsworth on 2006-10-29
> **realn said:**
> 4) When the status bar almost completed - frozen screen

How did you get from a frozen screen to:

> **realn said:**
> 5) Rebooted the computer without any CD - blank screen

Is it possible that you accidently pressed the key combination that changes the output mode for the laptop?  I have a key combination on mine that switches from LCD mode to another output (CRT/TV), the reason I ask is that the other outputs on yours seem to have been enabled.....

> **realn said:**
> 6) Unusable screen (the TV and CRT connections still worked).

---

### Post by sebau on 2006-10-29
I have a Toshiba A105 and had a similar problem with Mandrake and then again with Ubuntu 6.06.  I had to unpluge the notebook and remove the battery for a few seconds to get it to work again.

---

### Post by drucer on 2006-10-29
> **Catsworth said:**
> Is it possible that the death of the screen and the installation of Edgy are not linked, and that one just so happened to coincide with the other?

I'm quite sure Edgy installer has not broken any hardware. It is _very_ unlikely that software could damage hardware, but it is possible. I've seen how installing Windows 95 corrupted BIOS on AMD Athlon computer and the computer was resurrected when the BIOS chip was changed.

---

### Post by realn on 2006-10-29
> **drucer said:**
> I'm quite sure Edgy installer has not broken any hardware. It is _very_ unlikely that software could damage hardware, but it is possible. I've seen how installing Windows 95 corrupted BIOS on AMD Athlon computer and the computer was resurrected when the BIOS chip was changed.

I am quite sure that Edgy installer DID BREAK my laptop. At booting time the status bar bar of ubuntu was almost full, then a stripe of pixels appeared in the middle of the screen and then the screen froze.
After that I did every possible modification in BIOS, I took out the battery for the whole night and still the screen is completely dead. I repeat, the TV (S-VIDEO) and external monitor (CRT) connection still worked. That's why I would say that the graphics card is not (entirely) broken.
 As for the connection between Edgy and this problem - I booted from many CD's, internal/external hard disks different operating systems. What would me a more obvious link than this one?

---

### Post by Amon_Re on 2006-10-29
> **realn said:**
> Either with or without any CD - no power on the screen - totally blank (in fact black). As I said the hardware was somehow damaged. The laptop has been sent to Toshiba (I hope they can fix/replace the fault).
 A hardware damage through a software manipulaiton is quite a bad thing, I would say.

And the odds of that being the cause are less then winning the lottery, you were just unlucky.

---

### Post by Amon_Re on 2006-10-29
> **realn said:**
> I am quite sure that Edgy installer DID BREAK my laptop. At booting time the status bar bar of ubuntu was almost full, then a stripe of pixels appeared in the middle of the screen and then the screen froze.
After that I did every possible modification in BIOS, I took out the battery for the whole night and still the screen is completely dead. I repeat, the TV (S-VIDEO) and external monitor (CRT) connection still worked. That's why I would say that the graphics card is not (entirely) broken.
 As for the connection between Edgy and this problem - I booted from many CD's, internal/external hard disks different operating systems. What would me a more obvious link than this one?

Last week i had a controller chip on an IDE drive blow up while booting from a floppy disk (the chip litterally blew apart), i don't blame the bootdisk tho, i was just unlucky.

---

### Post by realn on 2006-10-29
That I was unlucky - that's for sure. But now, here's the REAL PROBLEM: if I take back my laptop after it's been repaired (or exactly the same model) and I redo the same thing - what would be the chances that I have the same problem. My opinion is that they are quite high. If someone thinks otherwise, please, please, let us know WHY she/he thinks otherwise. 
My point is: it doesn't look at all like a power surge/leakage, faulty/weak component or a misusage of a system. It looks like a BUG.
I would really appreciate if someone from the Ubuntu team (or just someone who has a spare Satellite A100) could just do the same thing - boot from a CD (in fact it was a DVD written only with the CD image) and see what happens.
Thank you for your comments and help.

---

### Post by Jussi Kukkonen on 2006-10-29
> **realn said:**
> I am quite sure that Edgy installer DID BREAK my laptop. 
No offence (really), but it's quite possible that your hardware just broke. It might have broken at another time, but it decided to break here... 

I'm not saying it's impossible for the installer to break your laptop, but I would estimate that the chances are pretty slim...
> 
if I take back my laptop after it's been repaired (or exactly the same model) and I redo the same thing - what would be the chances that I have the same problem. My opinion is that they are quite high. If someone thinks otherwise, please, please, let us know WHY she/he thinks otherwise.
Well, for starters because there's no explanation how it even could break your display -- and if a piece of software somehow could break a modern display, the display most certainly is broken...

---

### Post by realn on 2006-10-29
> **Jussi Kukkonen said:**
> No offence (really), but it's quite possible that your hardware just broke. It might have broken at another time, but it decided to break here... 

I'm not saying it's impossible for the installer to break your laptop, but I would estimate that the chances are pretty slim...

I have to apologize, in fact. I said that "I was sure", but there are few things that we can be sure of. I said that because I was biased by my experience. Let's put it like this: if someone can confirm the same problem, then more likely there is bug somewhere. If I get back my laptop and even after this I can still reproduce the problem but on the other hand no one else reports the problem: more likely a faulty piece of harware.

---

### Post by realn on 2006-10-29
Well it might be not entirely broken (more like a hard disk of which the MBR was overwritten and it won't boot any longer - except that the disk would still be usable once is plugged to a running system). Could it be just a bit that was somewhere overwritten so that it forces only the monitor/TV output? Would it be the BIOS or the graphics card (ATI x1400)?

---

### Post by nardis_Miles1 on 2006-10-29
I also have the prejudice that it was faulty hardware, but I'm curious. 

How long had you been using this computer?
What was running on it before you tried to install edgy?

When you get the computer back, please ask the repair people what had happened. Was it the graphics card, the bios, the hard drive, or the display?

---

### Post by realn on 2006-10-29
I bought it in June and I've been using it since then. WinXP + SUSE 10.0. Yes, I'll ask them. However, the store I bought it from sent it to Toshiba service center, so I might not be able to ask them directly.
 Anyway, I still have the Ubuntu CD with which most probably I'll try to do exactly the same thing with the hope I will not get the same behaviour. If someone else reports in this thread the same problem then maybe I'll give it a second thought ;)

---

### Post by nardis_Miles1 on 2006-10-29
You might try using the ubuntu CD on another machine, just to satisfy yourself that it isn't a wierd CD. I have to say that I really can't think of a way that the software could break the screen, but my inability may be a simple case of a dearth of imagination.

---

### Post by kypez on 2006-10-29
I have a toshiba as well and when installing I usually get a fear that the software would damage the hardware(especially the graphics chip). But really, that doesn't seem very logical at all. You had a bad break for sure.

---

### Post by space_banditto on 2007-01-18
Hi All,

I installed edgy on my toshiba a100 last weekend and have exactly the same problem. After the initial restart I have no display (back-light is fine for the lcd – external monitor works fine) there is hard-disk activity however. I don't even get the Toshiba splash screen that gives me options to go into the bios. 

I have searched around the net and it seems quite a few people have this problem. I can't find any posts regarding how they fixed it - whether it was a hardware issue or a software issue.

I have also seen references to a bug in the toshiba low-level software. Not sure if its true (a bios update did not fix the problem for me).

Its been a few months now since the original post, so if anybody has any updates or had similar problems I am sure there are some toshiba users that will be glad for the update.

Thanks in advance.

---

### Post by rcrook on 2007-01-25
> **realn said:**
> 1) Downloaded edgy
2) Burnt the CD
3) Booted the system
4) When the status bar almost completed - frozen screen
5) Rebooted the computer without any CD - blank screen 
6) Unusable screen (the TV and CRT connections still worked).

NOTES:
1) System: Toshiba Satellite A100 with WinXP & Suse 10.0.
2) The first time in my life when I got a piece of hardware broken because of a piece of software.
3) The first time in my life (and most probably the last time) that I ever (tried to) used Ubuntu.

Please report in this thread exactly the same problem and the sollution, too. The solution I found: get the laptop back to the store (fortunately still under warranty).

I have a Toshiba Satellite Pro A100 and I installed Kubuntu Edgy with no problems at all.

In fact I was pleasantly surprised at how well it works. I am so happy with its operation that I no longer boot the lappy into windows. Everything works beautifully. I even got the modem working. Only thing I haven't yet been able to get to work is all of the mobo sensors.

Randall Crook

---

