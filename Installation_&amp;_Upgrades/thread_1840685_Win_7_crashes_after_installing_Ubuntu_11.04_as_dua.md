---
title: "Win 7 crashes after installing Ubuntu 11.04 as dual boot"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by Jim_in_Germany on 2011-09-08
Hi,

I had Win 7 (64 bit) installed on a 500 GB hard drive.
I then installed Ubuntu 11.04 as a dual boot system
When I switch on my computer and boot into Ubuntu - everything is fine.
However, once I have booted into Ubuntu, the next time I boot into Win 7, Windows gets as far as the screen that says 'Windows is loading', then the computer resets.
This happens only once.
If I then boot into Windows again, everything is fine and I can boot into Windows as often as I want.
This problem will only reoccur the next time I boot into Ubuntu.

Does anybody have a clue about how I can go about trouble shooting this?

Thanks very much in advance.

Jim

P.S. I am not adverse to reinstalling Ubuntu if this seems like a reasonable solution.

---

### Post by 2F4U on 2011-09-08
Did you already look into the Windows system log files?

---

### Post by Jim_in_Germany on 2011-09-08
Hi,

In the Windows Event Log I see:

Critical - Event, 41 Kernel-Power

The system has rebooted without cleanly shutting down first. This error could be caused if the system stopped responding, crashed, or lost power unexpectedly.

Using Google, I was unable to find any mention of this error occurring having installed Ubuntu as a dual boot.

Most people seemed to be experiencing this error as a random occurrence.

Would be grateful for any help.

---

### Post by Quackers on 2011-09-08
Try running a chkdsk in Windows and see if things improve. If any errors are found it should be re-run until no errors are reported.

---

### Post by Jim_in_Germany on 2011-09-08
Thanks for the suggestion. I tried chkdsk. No errors were found, but the problem persists.

This all makes no sense to me, though.
I mean, what happened when I installed Ubuntu?

Ubuntu resized one of the partitions on my hard drive, to make space for itself

Ubuntu created a swap partition

Ubuntu formatted both partitions and copied a load of files to the partition it should live on

Ubuntu rewrote the MBR, so that I could select either Windows of Ubuntu on boot.

One of these things is now causing Windows to fail once after using Ubuntu.

It seems to me that when Ubuntu boots, it writes a file somewhere or adjusts a setting somewhere that causes Windows to choke.

Consequently when Windows boots after Ubuntu, it dies, but before it dies it adjusts whatever Ubuntu did to how it likes things.

After that everything is fine as far as Windows is concerned and it will boot indefinitely, until I boot Ubuntu again.

I just have no idea how to figure out what is causing this problem.

Any thoughts?

---

### Post by nipunshakya on 2011-09-08
^^^ I suggest you to repair your Grub once.....maybe that would help place windows 7 to its right place...goodluck.

---

### Post by Mark Phelps on 2011-09-08
The Windows error is claiming that the machine is not being cleanly shutdown.

So, HOW are you shutting down Ubuntu?  

Are you clicking on the icon in the top panel and choosing Shutdown? 

If so, are you seeing any error messages on screen just before the screen turns off?

I'm running 11.04 and, every so often, when I do a clean shutdown, I see error messages on the screen and I have to manually power off the PC. But my Win7 starts OK after that -- but that could be due to it having its own physical drive -- which Ubuntu isn't touching.

---

### Post by Jim_in_Germany on 2011-09-08
> **Mark Phelps said:**
> 
Are you clicking on the icon in the top panel and choosing Shutdown? 

Yup.

> **Mark Phelps said:**
> 
If so, are you seeing any error messages on screen just before the screen turns off?

Nope. That would be too easy :)

I just tried booting from a live CD and using [boot-repair]("https://help.ubuntu.com/community/Boot-Repai") to reinstall GRUB.

Unfortunately, this didn't work.

If anyone can decipher the output, there is a copy of the program's output here (after attempting fix):
[http://paste.ubuntu.com/685504/](http://paste.ubuntu.com/685504/)

There are a bunch of errors towards the end of the file, but nothing which is immediately very helpful (for me).

Thanks for your help so far.

---

### Post by YesWeCan on 2011-09-08
It would eliminate some things if you would try this with a power-cycle.

Boot Ubuntu.
Shutdown. Power off.
Reboot Windows.

---

### Post by Jim_in_Germany on 2011-09-08
Interesting, interesting ...
I did as you suggest and was surprised to see that Ubuntu powers down in about 2 seconds (which can't be correct).

Then, when I restart my computer I don't even get to the boot loader. I get a beep (which is normal), then the computer resets (almost immediately), then I get another beep and the message that my computer failed to boot on the previous attempt. I then press F1 to continue, land in the boot menu and can boot either Ubuntu or Windows without a problem.

It seems then that the problem is Ubuntu not shutting down correctly. 

Is this a known issue?

---

### Post by YesWeCan on 2011-09-08
If only it would boot that fast. ;)

I vaguely recall another instance of these symptoms in this very forum. I just can't recall the details. You  might want to try some searching.

Perhaps looking at the Ubuntu logs might help.

When you shutdown Ubuntu did you also power off the computer - pull the plug out for s few seconds? It may not make a difference, just wondering. Some mobo states may be preserved when power is gone but many won't.

---

### Post by oldfred on 2011-09-08
Regular shutdown should work, but you can try this which is the emergency shutdown. Once you get back to command line it may give some messages that are useful?

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Another
sudo init 0

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by Jim_in_Germany on 2011-09-09
Thanks for all of your replies.

I have been playing around with this all morning now and am not even close to sorting it out.

I think I'll reinstall both Windows (long overdue) and Ubuntu.

Not really a satisfactory solution, but a solution nonetheless.

P.S. Should I mark the thread as solved?

---

### Post by nipunshakya on 2011-09-09
> **Jim_in_Germany said:**
> Thanks for all of your replies.

I have been playing around with this all morning now and am not even close to sorting it out.

I think I'll reinstall both Windows (long overdue) and Ubuntu.

Not really a satisfactory solution, but a solution nonetheless.

P.S. Should I mark the thread as solved?

Dear sir, i don't have other solution rather than suggest you for a re-installation, but if you could just take a moment and try to install some previous version of ubuntu(maybe 10.04LTS or so)without re-installing windows 7, then it might solve your problem as well...maybe 11.04 doesn't go well with your machine...

If you are thinking of reinstallation, then why not try the short way round? But still, if you want a fresh installation of both systems, its all upto you...Goodluck

Regards.WinuxUser

---

### Post by movieman on 2011-09-09
> **Jim_in_Germany said:**
> It seems then that the problem is Ubuntu not shutting down correctly.

It's probably not Ubuntu, it may well be a broken BIOS.

I've forgotten the precise details but I had something similar when I first installed Ubuntu on my laptop; I couldn't reboot into Windows, I had to do a full shutdown and restart. A couple of months later they released a BIOS update that fixed it.

---

### Post by YesWeCan on 2011-09-09
+1 Making sure you have the latest bios is an excellent suggestion.

---

### Post by Coronas and Pretzels on 2011-09-09
When I was dual booting separate HDD's with the same setup I used EasyBCD to chainload and never had a problem. Just pick the OS you want in the boot menu.
 It works with Vista and 7 not XP though.

Hope this helps.

---

### Post by thiebaude on 2011-09-09
Interesting that someone mentioned Ubuntu not shutting down. Even since Plymouth came out, my Ubuntu does not shut down, it just restarts. I click on the shutdown button, but it never shuts down. The problem had been reported to Launchpad, but nothing ever came of it.The shutting down occured when I had only Ubuntu installed on the HDD.

---

### Post by Jim_in_Germany on 2011-09-12
Hi,

Just wanted to report back in case it helped anyone else.

I reinstalled everything and it turned out to be a problem with 11.04, as the problem persisted after the new install.

I dropped back to 10.10 and now everything is good.

Thanks for all your help

P.S. Mainboard is a Asus P5NE32-E with the latest BIOS, therefore I think it probably was Ubuntu.

---

