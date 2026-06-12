---
title: "boot failure (shortly) after graphic driver install"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by smice on 2011-09-14
Hello everyone!

I'm new here as well as to Ubuntu, so forgive me for my noobness.

I have a Sony Vaio laptop with Windows 7 and Ubuntu 11.04 installed (I've used the new Unity GUI).

I randomly encountered boot problems before: although Windows always started up, and the conputer had no hardware problems apparently, Ubuntu sometimes faailed to start up. Why? I don't know. Usually a power off - power on - boot again into Ubuntu resulted in a perfect startup, so I did not care about the few extra startups. They happened totally randomly for me, sometimes 3 times in a row, sometimes at every second startup, sometimes everything was fine for ~10 startups... The system usually just hanged after I chose the Ubuntu option in the GRUB menu, blank screen and nothing was happening.

Then today I got a message that I need a proprietary driver to fully utilize my ATI Radeon graphics card. So I downloaded and installed it using the Jockey manager, then I restarted the system...

Ubuntu started with a message that my graphics card is not good enough for the Unity desktop, so it started a classic Gnome. So since the new proprietary driver was not working, I removed it with Jockey to switch back to the great free driver. After that everything was fine, Ubuntu restarted with the Unity gui again.

Then the next startup resulted in the hang described above. I thought it is the usual problem, and tried to solve it the way I solved many times: with the power button. But the problem was not solved this time. The GRUB menu appears, an underscore is flashing briefly, then comes the blank screen where the process stops. I tried switching on and off a few times more, but the result was always the same, Ubuntu did not started.

I tried to boot in recovery mode; that fails either, although at least it gives me some feedback: I can see from the running lines what my computer is doing. It is random after which line it stops, but before stopping there are usually graphics card related processes: [radeon] is written at the end of some lines before the final line. No failure is reported, and I can still use GRUB to start up Win 7. But there is no way to start Ubuntu.

Can anyone help me please?

---

### Post by smice on 2011-09-16
OK, I've found this:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

After like a ~100 tries I managed to boot in recovery mode to use the CLI so I followed the instructions on that wiki page.

Yes, I am pretty sure that my problems arise from the fglrx driver installation (and incorrect uninstallation).
Yes, I found some bits still installed.
Yes, I purged them all and reinstalled the free driver, according to the wiki page.

No, I still can't boot into Ubuntu. (Unless if you consider those rare occasions when I can boot in recovery mode a success, from where the GUI cannot be started either. But they are like 1 in 50-100 tries. Maybe a bit less... I have a lot of work to do but pretty much all I do is pressing the power button all day.)


(First: I hate you ATI, this is not the first instance when I have severe problems with your drivers/graphic cards, even under Windows, where it is designed to work. I'll never make the mistake of using an ATI product again, and will discourage anyone.

Second: if anyone ever jokes around about the instability of Windows and the stability of Linux... Seriously, guys, my power button is wearing out because I try to use Linux! :(:(:()


As soon as I find my LiveCD, I will reinstall Ubuntu. At least I hope I helped some people with that wiki link...

---

### Post by MAFoElffen on 2011-09-16
> **smice said:**
> OK, I've found this:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

After like a ~100 tries I managed to boot in recovery mode to use the CLI so I followed the instructions on that wiki page.

Looks like you are on the right track by purging the new version fglx and reinstalling the old.  Sounds like their was residual conflicting modules loaded.

Also sounds lke there was previous problems with something hanging during your boot process (possib;y during X intit)... that you were using the power button and rebooting to try to get around.  I suspect that that may still be there after this until you track that down and resolve.

One thing that may help with this until you do get this fugured out is to use "radeon.mode=1" as a kernel boot startup option.  The info contained in the first 3 posts of this sticky may help you with diagnostics and resolving graphics issues:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by smice on 2011-09-16
Thanks so much for the help!

I got another computer temporarily to work but I'll try to fix my laptop at home... as soon as I regain my patience. :)

I'm pretty determined to clear the partition and reinstall Ubuntu right now - hope that solves the earlier boot problems either. (And I'll never use proprietary drivers again.)

Anyways, I was puzzled by the random nature of my previous boot hangs... Why would it hang suddenly when before and after it worked perfectly several times in a row...?

---

### Post by MAFoElffen on 2011-09-16
> **smice said:**
> Thanks so much for the help!

I got another computer temporarily to work but I'll try to fix my laptop at home... as soon as I regain my patience. :)

I'm pretty determined to clear the partition and reinstall Ubuntu right now - hope that solves the earlier boot problems either. (And I'll never use proprietary drivers again.)

Anyways, I was puzzled by the random nature of my previous boot hangs... Why would it hang suddenly when before and after it worked perfectly several times in a row...?
Sometimes those X boot hangs are caused by "the order" modules are loaded, so if they are not spec'ed on the order, it's a race to see whicg module loads first. (work-arounds to force the load order)... Then when you install flgx and flgx.... they have the same name but are really "different" meaning safe is when going between versions, to purge the old version.  Just uninstalling these, leaves residual modules that don't like each other. (refer to my post here:
[http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)

The instructions in that post is for installing proprietary drivers, BUT-- If you look over the first part of it, you should see how to purge the old files out to get a clean backed-off slate going for you...for a clean install of "any" new video drivers.

---

### Post by smice on 2011-09-19
I guess this problem remains unsolved forever.

Alright, follow-up:

I did many attempts to save my Ubuntu system. I tried to follow the diagnostic/recovery steps in MAFoElffen's thread. I got the GRUB, I could start a terminal (after many fails), I installed every drivers correctly... The problem remains. Since I couldn't start Ubuntu, I decided to reinstall it.

I tried to use the LiveCD to boot and to reinstall Ubuntu. However - surprise! - the boot process failed even with the CD! I don't get it, if I can boot from the CD on a totally Ubuntu free machine, or even on a 'raw' machine with no OS... Then it certainly doesn't use drivers from the HDD...

At least after many tries I managed to boot in recovery mode, and I started an X session in failsafe graphic mode. Then I inserted the LiveCD, and... it did not wanted to start! I tried to start it manually, and I get an error message like this:

This program cannot run because Ubuntu can't find the autorun file.

Again, what?! Certainly the CD content wasn't modified...

To the point: I managed to start the CD in this way: again after having more of the power button fun, at one point I successfully booted in recovery mode. Chosing failsafeX mode I reconfigured the graphic settings, choosing the default option, where I got a message telling me that the default mode is active, my previous settings were backed up. I restarted X - and it worked! The Unity desktop appeared. I thought that I finally eliminated the problem, but after restart the boot failure was all the same. So when the next time I started in recovery mode after the usual power button playing, I did that reconfiguration again, CD in, and rebooted immediately - this time the LiveCD started, and after booting it offered me to erase Ubuntu and reinstall it - which I was more than happy to accept. And now I'm typing in my new Ubuntu environment!

I hope the story ends here...

---

### Post by smice on 2011-09-22
Noooooooooooooooooooooooooo!!! :frown::frown::frown:

The mysterious boot failure returns!

After a few smooth booting, the phenomenon exactly the same as described above, has returned. What the heck can I do with it? Please help, I need Ubuntu badly!

And how is it possible that after a complete partition wipeout and OS reinstallation the problem still exists? I swear this time I haven't even looked at the proprietary ATI driver.



I managed to get some info during booting, it was a bloody hard work, but here are some lines that I worry about (in chronological order as seen during booting):

> BUG: unable to handle kernel paging request at faa01ffc
IP: [<f898b689>] evergreen_cp_start +0x49/0xad0 [radeon]
*pde = 30425067 *pte = 00000000
Ooops: 0002 [#1] SMP
last sysfs file: /sys/device/platform/radeon_cp.0/firmware/radeon_cp.0/loading

Then comes a listing of linked modules, then a lot of operations that involves evergreen and/or radeon, usually [radeon] is written at the end of the lines. Then:

> Code: f0 0f 85 84 08 00 00 8b 83 a4 07 00 00 85 c0 0f 8e 5d 08 00 00 8b 83 94 07 00 00 8d 14 85 00 00 00 00 83 c0 01 03 93 8c 07 00 00 <c7> 02 00 44 05 c0 8b 93 a4 07 00 00 23 83 b4 07 00 00 83 ab a0

After that a few lines come, usually one to three, than the booting process just hangs. It is random, what lines come after that long Code line, usually some evergreen or apparmor, apparmor parser things; this time the last line was:

> CR2: 00000000faa01ffc


Things that are extremely suspicious:

1. I assume that a booting OS shouldn't say 'BUG' or 'Ooops' to me.
2. The 'last sysfs file' doesn't exist: in /sys/devices/platform there is no radeon related file or directory.
3. The 'faa01ffc' that was buggy in the first line appears again in the last line before the hang. (With the 00000000 of '*pte'.)
4. I said that the last lines before the hang are not always the same, they vary from booting to booting; but there is one thing I always see before hanging: the long 'Code' line.


I hope someone can do something with this. Many thanks in advance for any help!

---

### Post by Mark Phelps on 2011-09-22
I know you say your PC is working fine in Win7, but nonetheless, this could be a memory problem that is manifesting in Ubuntu because it manages memory differently than does Windows.

Next time you boot into Ubuntu, when you get the GRUB menu, choose the option to run Memtest.

---

### Post by smice on 2011-09-26
First, I just have to tell you the extremely ridiculous - and hopefully just temporary - solution I found to start up Ubuntu 'normally'.

MAFoElffen told me about the racing modules, which gave me an idea. I saw during boot that the system tries to configure the connected USB mouse, like finding X/Y axis, acceleration rate etc. It takes some time, and if the mouse is moving, it takes a lot more time! So I thought if I could delay the loading of some subsequent modules and thus interfere with the race, than that may give time for the proper modules to load...

And guess what, it works! I know it's the silliest thing, but I give a massage to the mouse pad during booting, and in this way I can start up Ubuntu with no problem! Well, in 85% of all startups... But still, without the motions, I still cannot start Ubuntu, that's 100%.


Now to react to Mark Phelps:

A memory problem! (light bulb blinks) That's a totally new direction, but now I'm looking at the system tab in the System Monitor app and it says I have 2.4 GiB memory. (Actually, I have 4 GB RAM.) That's certainly weird. The swap file size however is ~4 GB.

OK, just wait until I run memtest.

Oh and by the way, Win7 detects the memory correctly.

---

### Post by smice on 2011-09-26
Alright, so I chose memtest86+ 4.10 from the GRUB menu. (4.10 should work with 64bit systems.) Aaaaand...

BANG!!!!! :KS

Just like the boot process, memtest86+ crashed. After the line describing the CPU (starts with 'IMC'), it wrote:
> Settings: RAM: 0 MHz (DDR3-   0)

And in the middle of the screen there was a line:
> 1024K           e820          off

And that's it, memtest was hanging, even the menu bar at the bottom of the screen did not appear. ???
I tried a few more times playing with the all-too-familiar power button, but the result was all the same every single time. Memtest was hanging at the same point.


I've got a 64bit hardware with a 32bit Linux. Partly because that was the LiveCD version that came with the freshly bought machine (don't ask me why), and partly because I'm a bioinformatician, and the programs I use are not so professional, mostly inhouse developments of various research teams (life scientists, not informaticians), so 99.99% of them don't create a 64bit version of the program. I know I can run 32bit programs on a 64bit OS too...

So my question is, do you think that reinstalling a 64bit version of Ubuntu would solve my problems? Or what else could be wrong with the memory, and how should I try to fix it?

---

