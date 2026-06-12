---
title: "Is there a way to use apt via a SD card when wireless fails?"
date: 2024-05-28
forum: Installation &amp; Upgrades
---

### Post by goemonburo on 2024-05-28
I have an interesting conundrum in that my parents' laptop's wireless has (apparently) failed, leaving the system without a way to connect to the internet.  In trying to diagnose this, I'm first trying to assess their hard drive, which I believe has reached capacity and is at 100% (df indicates this).  To do this, I am using a Lubuntu Live CD and rooting around...but the filesystem is encrypted.  To access that, I need to run ecrypt-utils.  Which I got, put on an SD card, and installed (or tried to) with dpkg.  

However of course there are dependencies and now I'm stuck in that morass of "this requires that dll," etc.  

Is there any way to use apt to download (but not install) all the packages that are required for using ecrypt-utils?  All its dependencies?  I don't mind running dpkg 50 zillion times, but just wondered if there's an easier way.  It may be that the wifi is gone for good and it's time for them to get a new laptop, but before I tell them that (I'll be the one configuring it and so on) I'd rather get this one running again.

Thank you for any help.  While I may post a separate thread, if anyone knows good ways to diagnose broken wifi (I believe it's hardware) I'd love to know.

---

### Post by grahammechanical on 2024-05-28
All this may seem obvious to you but it is not obvious to us. What version or flavour of Ubuntu is on that machine? Assuming it is Ubuntu, I ask what does system settings/WiFi show you? Is the laptop in airplane mode? Does system settings show a list of available WiFi networks. Is the WiFi adapter turned off in the BIOS/UEFI settings utility?

You are assuming that the WiFi adapter has failed. You may have come to this conclusion by already doing these checks. We should not make that assumption without knowing the answer to those questions.

Cannot you not provide clear and detailed instructions for your parents to follow? Let them write down what they see. Your parents should have no problem loading the operating system. Provide them with a Lubuntu live CD/USB and explain to them how to load the Live/Try session. Are there WiFi networks available when running the Live CD session? 

Regards

---

### Post by goemonburo on 2024-05-30
I have solved the internet connectivity issue by using an Ethernet cable and that works, so I could download ecryptfs-utils.  I still haven't figured out the wifi, but wifi does work in Windows (it's a dual boot) so it shouldn't be a hardware issue.  It's running Ubuntu 18.04LTS on the hard drive, but my LiveCD is Lubuntu 22.04LTS.  I'm unable to see anything when I "scan for wifi" in the LiveCD, and the reason I'm using the LiveCD is because the system is hanging at boot.  I will post a separate question about that, as it's a different thread.  I'd still like to know if I can get apt to put all my necessary dependency .debs onto a SD card.  That would be very useful.

---

### Post by goemonburo on 2024-05-30
Also, sorry, a bit vague:  the "apparently failed" = "does not boot."  It simply hangs after a few minutes of the "Ubuntu" logo spinny thing.  My parents are in their 80s and the idea of writing instructions is kind of absurd.  One, I don't know their system well enough to know what it would/should do, two, they aren't particularly savvy, three, the moment something's off the script, they're helpless.  So it's vastly easier to just do it for them and skip the hours of phone time and frustration.

The real issue is that as of a few days ago, their system has stopped booting.  It simply freezes in a black screen.  The keyboard can function (hitting Ctl-Alt-Del reboots it promptly) but it just gets to a certain spot in the boot and...freezes.  I've let it sit for several hours and nothing has happened.  I have tried the "failsafe" option and tried to "clean," but that did not help.  If there are other easy ways to fix this, it would be great to try, as they are not reliable about backing things up and will potentially lose a lot of data if I have to reinstall.  

I suspect what's happened is that they have filled their home drive entirely and it's simply too full to work anymore.  But it's encrypted (which is why I was trying to use ecryptfs) and the loader didn't work, so it needs a Mount Passcode that they do not appear to have anymore, if they ever did.  If there's an easy way to fix the broken boot process, such as to clear enough space to get it working again, I can go from there.  As it is, I'm unable to access the drive or fix/remove anything.  

Apologies if I haven't offered enough information.  Hopefully this helps!  And thank you in advance for the time and assistance.

---

