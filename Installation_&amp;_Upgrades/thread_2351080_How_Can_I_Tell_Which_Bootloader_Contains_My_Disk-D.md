---
title: "How Can I Tell Which Bootloader Contains My Disk-Drive?"
date: 2017-01-30
forum: Installation &amp; Upgrades
---

### Post by BlacklightHalo on 2017-01-30
Hello all,

I recently upgraded to Ubuntu (actually Kubuntu) 16.04 and am unfortunately awash with bugs and malfunctions. Either this was released extremely prematurely, or it's not very compatible with my (admittedly older) computer, or something. I cannot even log out, restart, shut down, etc. The computer seems to be ignoring my commands when I click on any of these with the kickoff launcher.

In any case, I mean to install the old Ubuntu 14.04.5 and set my system back-up so it'll be stable and functional again, at least for the time-being. I have already backed-up all my important files. After that, this would normally be as simple as creating an Ubuntu 14.04 LiveCD and leaving it in the disc drive while I reboot. Thing is, at some point my bootloaders were re-prioritized so that the disc drive is no longer the default. My system is also encrypted, and asks for a password at bootup, in case that effects this process.

The way I understand it, in order to be able to install from LiveCD again, I need to set my bootloaders so that the disc drive is first-priority once again. I have downloaded Grub Customizer and am looking at a list of bootloaders, but their names do not mean much to me.

[ATTACH=CONFIG]273450[/ATTACH]

How can I tell which one contains the disc drive?

PS - am I missing something, here? If you smell a fatal flaw in my plan, I would love to have your input before I attempt this.

Thank you for anything you can tell me,

-Val

---

### Post by QIII on 2017-01-30
Hello!

It sounds like what you are talking about is the boot priority set in your BIOS/UEFI, which is not set in any OS.  It may already be set to boot from optical media first.  Try putting the optical media in the drive and rebooting.

No, by the way.  Kubuntu 16.04 was not released prematurely.  While it is unfortunate that you are having issue, you can't assume others are.

---

### Post by BlacklightHalo on 2017-01-30
> **QIII said:**
> Hello!

It sounds like what you are talking about is the boot priority set in your BIOS/UEFI, which is not set in any OS.  It may already be set to boot from optical media first.  Try putting the optical media in the drive and rebooting.

I have done this and am getting the following: 

[ATTACH=CONFIG]273453[/ATTACH]

I don't know whether this is because of what I suspected originally, or because Brasero got stuck at "creating image checksum" and had to be cancelled at the end of that process. However, that was my last blank disc with enough space for the 1GB 14.04 iso, so I'm SOL for tonight if that disc wasn't created properly. It said a bit more before proceeding into the standard OS GUI, but I didn't get a shot of it (had to use my phone because I have no screencap at that level) and can't remember what else it said.

Also, if you can't change the priority with which drives are chosen for bootloading at startup from inside the OS, then what would be the point of a program like Grub Customizer?

> [COLOR=#000000]While it is unfortunate that you are having issue, you can't assume others are.[/COLOR]

Please do not talk down to me about making assumptions especially when I haven't made any. I never said I'd settled on premature release as a final conclusion. I gave that as one possibility that came to mind based on my experiences, my observations of others reviews and discussions in forums about issues they were experiencing, and advice I received from two users [on another thread]("https://ubuntuforums.org/showthread.php?t=2334374") five months ago about Xenial's bugginess. I also qualified with "either" and "or" and also left room for the possibility that it was my hardware or something else I hadn't considered.

---

### Post by QIII on 2017-01-31
> **BlacklightHalo said:**
> I don't know whether this is because of what I suspected originally, or because Brasero got stuck at "creating image checksum" and had to be cancelled at the end of that process. However, that was my last blank disc with enough space for the 1GB 14.04 iso, so I'm SOL for tonight if that disc wasn't created properly. It said a bit more before proceeding into the standard OS GUI, but I didn't get a shot of it (had to use my phone because I have no screencap at that level) and can't remember what else it said.

That being the case, my first suspicion is that the situation is, in fact, that you have a bad image.  *That* should probably have remained your first suspicion and it should have been the first thing to rule out.

> I have done this and am getting the following: 

A further indication of an issue with the image.

> Also, if you can't change the priority with which drives are chosen for bootloading at startup from inside the OS, then what would be the point of a program like Grub Customizer?

GRUB allows the choice of OS to boot in to.  It is not a tool for choosing the boot priority of *devices*.

>  I never said I'd settled on premature release as a final conclusion. I gave that as one possibility that came to mind based on my experiences, my observations of others reviews and discussions in forums about issues they were experiencing, and advice I received from two users [on another thread]("https://ubuntuforums.org/showthread.php?t=2334374") five months ago about Xenial's bugginess. I also qualified with "either" and "or" and also left room for the possibility that it was my hardware or something else I hadn't considered.

No, you did not settle on that or any of the several other less likely assumptions of possibilites you mentioned before you made reference to what you said you thought was your first suspicion.

I have corrected your unfortunate issue with URLs appearing randomly in your post.  I would hate to have any other Staff members think you were talking down to me.  There is also a danger in assuming that finding a number of articles all over the web indicating problems is a definite proof of anything.  People tend to complain more about things that aren't working for them than things are are working well.  You get a strong bias when looking up "problems" on the web.

---

### Post by mörgæs on 2017-01-31
I have only good experiences with 16.04.1 on many different computers. What have consistently given me bad experiences is an online upgrade. Better to do a fresh install every time.

---

### Post by Impavidus on 2017-01-31
I/O errors reading the optical disk suggest a bad burn or a bad optical drive. Is your computer new enough to boot from USB? That may solve the issue.

I do think that 16.04 was relatively buggy when it was released, but those bugs have been fixed by now. If you upgrade to 16.04 now you shouldn't be affected by those bugs any more. Your problems were more likely caused by an accumulation of small configuration errors, improperly removed packages, bugs in install/uninstall scripts over a long time. I had one computer upgraded all the way from Ubuntu 6.06 to Xubuntu 14.04 and it began showing some strange malfunctions on that final system. Nothing too bad and it was used like that for another 2 years. A fresh install of 16.04 turned it back to flawless behaviour.

Chances are your computer will have no problem running a fresh install of Kubuntu 16.04. Note that Kubuntu 14.04 and Kubuntu 16.04 are both supported until April 2019.

---

### Post by BlacklightHalo on 2017-02-17
I've now gotten around to successfully creating an Ubuntu 14.04 Live CD. There appear to have been no problems burning the disc (I did it with Brasero.) I have further verified it as fully functional by trying it in my Windows laptop, with success. However, my Kubuntu computer (still running the same installation of 16.04) is ignoring that disc completely during bootup. It doesn't give me the same boot-screen error message as the last disc. It just boots straight-up into my existing OS without any sign that it's even aware of the 14.04 disc. When I'm fully booted and logged-into my desktop in 16.04, the disc shows up under devices as "Ubuntu 14.04 LTS amd64," so by all accounts I can see, there was no error recording the Live CD, but my desktop/16.04 system isn't doing anything with it when I boot-up with the disc in the drive.

---

### Post by yancek on 2017-02-17
If the DVD boots successfully in one computer but not in a second computer, make sure you have the DVD drive set to first boot priority in the BIOS.

---

### Post by BlacklightHalo on 2017-02-17
> **yancek said:**
> If the DVD boots successfully in one computer but not in a second computer, make sure you have the DVD drive set to first boot priority in the BIOS.

How do you do this?

---

### Post by deadflowr on 2017-02-18
> **BlacklightHalo said:**
> How do you do this?

That depends entirely on your machines BIOS settings.
But basically start the machine and get into the BIOS section,
(Depending on the machine it could be any number of keys, sometimes F2 or F12, I has it as the Delete key on one once.
Your start up screen should tell you. It'll probably sat something like Bios screen F2 or setting screen or something,
This is done from the very first screen to appear when you start up, the screen that'll probably show the machine model name or something.

((And if your lucky, you might even get a Boot menu option along side the Bios option , in which case you can probably even forgo changing the boot order in the bios.
Since that option would go directly to a boot menu that will allow you to choose any device that is set as a bootable device.))

Forsaking that the boot menu does not exist or the dvd drive is not enabled for it, for whatever reason.
Then navigate into the Bios section, and look through for any sections related to boot, in there it should have a section for boot order.
You will need to follow whatever directions it's side panel may have in terms of helpful hints.

(My system tells me to navigate with the arrows keys, but to move the order around I need to use the U and D keys. Other systems may need to use the pageup/pagedown keys, and others may need an entirely different set of keys)

But once you set the boot order, there is usually a section to exit the bios screen, typically called exit, in this there should be a save and exit option, use that and follow its directions.
Usually it'll ask if you want to save the settings you did, and probably post a quick warning message and whether or not you want to proceed, yes is fine. Since this is a basic setting you're changing.
(It's not like you are trying to manipulate the cpu's power settings or something?)

Hope this makes sense/helps

---

