---
title: "installation hangs on detecting filesystem"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by beathydrolysis on 2007-01-07
Hi all.  New to Ubuntu and excited to buck the Micro$oft machine.  However I have had no end of trouble getting the os installed.  I am running an emachines m6809 laptop with a mobile AMD Athlon 64 Processor 3200+ (according to my system properties) with 800 MHz bus and 512 mb ram.  I have an extra 60 gb 2.5" hard drive which I want to install ubuntu to (Toshiba MK6021GAS 60 gb drive).
     I downloaded the 6.06 (dapper drake) 64 bit version of ubuntu and everything boots okay off the cd.  I run through the 6 steps for install and then it goes to work.  At this point it all goes sour.  It always hangs at or before 15% complete and to my knowledge always while displaying "detecting filesystem".  I shut it down after 20 or so minutes of observing the computer not accessing the hard drive (no light, no noise) and boot back into windows with my other hard drive.  I throw the 60 gb into an external enclosure check the drive through device manager and it shows that the main partition and 1.5 gb swap are healthy.  The install just never seems to get to putting anything on them.  Any ideas....I'm really desperate to get switched to ubuntu.
   I have also tried using the ubuntu partitioner in the installer to get ubuntu side by side on my windows hard disk (a different 80 gb drive) and it hangs before between step 5 and 6 every time.  I'm wondering if I just have some innate sort of hardware incompatibility.
   If that's the case, I'd like to build a desktop to run ubuntu with.  I was browsing parts on newegg and was wondering if anyone had any ideas about what I should pick.  Being as it has been so hard to install ubuntu on my laptop I'm reluctant to invest $500+ in a desktop that may not even be able to run the operating system.  What processors etc. are best?
    Sorry for the long post, looking forward to meaningful replies.  Thanks, beathydrolysis

---

### Post by kebes on 2007-01-07
First off, welcome!

Now when the installer 'hangs' does it freeze completely or is it just stuck? If you go Ctrl+Alt+F1 (or Ctrl+Alt+F2, F3, etc...) you get to different screens that show background output. It's often useful to see what error messages were being output by the kernel at the point where it gets stuck. This can help figure out what the problem is. If you are unable to switch using Ctrl+Alt+F# then it's really frozen...


Something else to try is to install using the "Alternate" CD instead of the standard CD. The alternate installer is a text-based installer that is "simpler" and often works better on quirky hardware. It's certainly worth a shot. It's also worth pointing out that the 32-bit version of Ubuntu should install and again, might be worth trying. (Yes there are some performance advantages you won't be taking advantage of, but it's probably okay!)


Another thing to try with difficult installs is to pass kernel boot parameters. Before hitting "enter" to begin the install you press the "other options" key (F6 I think) and then add flags like "irqpoll" or "noapic" ... the exact flags you need depend on the problem you are encountering, of course...

---

### Post by beathydrolysis on 2007-01-07
Thanks for the quick reply.  The system does not freeze during installation.  I can actually just minimize the install, and continue using the os off the cd at what appears to be full speed.  I guess a more appropriate description of the install is that it just stops.  Does this help at all?  Would you recommend just going ahead with the alternate intstall?  If so, is there a guide out there to do it?  Since it's text-based, I'm sure it's not as novice friendly ( is this correct?)  Thanks.

---

### Post by meng on 2007-01-07
Actually the installer on the Alternate CD, although text-based, is essentially the same as the graphical install on the Live CD. So you should feel quite comfortable using it.

---

### Post by kebes on 2007-01-07
> **beathydrolysis said:**
> I'd like to build a desktop to run ubuntu with.  I was browsing parts on newegg and was wondering if anyone had any ideas about what I should pick.  Being as it has been so hard to install ubuntu on my laptop I'm reluctant to invest $500+ in a desktop that may not even be able to run the operating system.  What processors etc. are best?

You can get an idea about hardware compatibility by checking:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

(there are other Linux hardware compatibility databases that are also worth checking...)

If you have a particular system in mind, or have a series of components in mind, you can post a thread to these forums for feedback on whether they are a good match with Ubuntu or not.

Some general comments: For graphics cards, the nVidia cards generally work much better than ATI. For motherboards, be aware that the newest Intel chipsets have conflicts with the current version of Ubuntu (only fixed in the unstable development branch as of this writing). I recently built a machine with an ASUS motherboard, AMD processor, nVidia graphics card and it works like a charm... The core2duo processors are right now an amazing "power per dollar" (if they are within your price range) but as I said you have to do some research to make sure you get a compatible motherboard.

---

### Post by kebes on 2007-01-07
> **beathydrolysis said:**
> Thanks for the quick reply.  The system does not freeze during installation.  I can actually just minimize the install, and continue using the os off the cd at what appears to be full speed.  I guess a more appropriate description of the install is that it just stops.  Does this help at all?  Would you recommend just going ahead with the alternate intstall?  If so, is there a guide out there to do it?  Since it's text-based, I'm sure it's not as novice friendly ( is this correct?)  Thanks.

I think the alternate CD is worth a try... The 32-bit install might also be worth a try. Were you able to do Ctrl+Alt+F# to get some information on what was happening at the moment where the installer appears to 'stop' ?

As meng says the steps in the alternate install are the same as the LiveCD installer, so I don't think you'll have too much trouble. (Just need to use arrow keys and tab key to move between selections!)

---

### Post by beathydrolysis on 2007-01-07
allright.  Thanks for all the quick replies.  I'm gonna give it a try.  I'll try the Ctrl+Alt+F# when it hangs and see what I get then I'll get back to you guys.  Thanks for the help.  I should have something to report within an hour or so.  Until then...
  Ps.  my graphics card is ATI mobility radeon 9600 (could that be the problem)?

---

### Post by meng on 2007-01-07
I doubt your video card is causing this particular problem. Good luck!!

---

### Post by beathydrolysis on 2007-01-07
Hi all.  Tried the install again.  This time with the 32 bit version.  Install stopped just like usual at the 15% mark with the message detecting file systems in the installation window.  Tried the ctrl+alt+F# bit and F1 -> F6 yielded something about ubuntu being provided with free software with the last line showing
   ubuntu@ubuntu:~$
ctrl+alt+F7 showed the desktop

and

ctrl+alt+F8 showed a whole bunch of text with the last line reading

Running local boot scripts (/etc/rc.local)           ok

ctrl+alt+F9, F10, F11, F12 didn't do anything.

Does this help at all?  No go on the 64 or 32 live cd installer, is the next step the alternate install?

---

### Post by kebes on 2007-01-07
Ctrl+Alt+F8 was the one I wanted... but it looks like there were no error messages. Hmm..

I'd give the Alternate CD a try... although it's quite strange that there is no suggestion as to what is going wrong...

---

### Post by beathydrolysis on 2007-01-07
allright, downloading the 32 bit alternate install and will give it a try tomorrow.  Not super hopeful but I'll keep plugging because I really want to run ubuntu.  I'll be back tomorrow night after I've tried again with the alternate install.

If that doesn't work do I have any other reasonable options or am I pretty much out of luck until I build a new machine.  Thanks for all the help thus far.

---

### Post by kebes on 2007-01-07
> **beathydrolysis said:**
> allright, downloading the 32 bit alternate install and will give it a try tomorrow.  Not super hopeful but I'll keep plugging because I really want to run ubuntu.  I'll be back tomorrow night after I've tried again with the alternate install.

If that doesn't work do I have any other reasonable options or am I pretty much out of luck until I build a new machine.  Thanks for all the help thus far.

I can't think of anything else to try, at the moment. I'm quite confused because after doing a search for your model of laptop, it seems that others have installed linux on that model.

Since you already have the CDs ready to go I would also try booting with kernel flags (press "F6 for more options") and pass the "nopcmcia noapic" options. You might get lucky.

In any case, have a good night and you're quite welcome for the help.

---

### Post by Toribor on 2008-01-18
I'm having this exact same issue so I don't think it is a hardware problem. The more I google the more I find others with the exact same problem. I am running a Dell XPS M1210 with a 2.4ghz dual core processor and 2gb RAM. My onboard hard drive is 160gb, but I am installing it on a new Maxtor external drive with 500gb of space connected through USB. (Woo for dual booting!)

I am using the live CD so I will try the alternate and report back on my findings. (I'll do this in about an hour) Wish me luck. :)

---

### Post by mbelienkz on 2008-01-29
I was having the same problem with my feisty installation. I've erased and reformat my disk but the problem still exists (there was one ntfs partition before which I thought might be the problem). Then I use the alternate cd and add the option "acpi=off" and the installation goes smooth and completed. Haven't tried using the live cd with that option yet. Hope this will help you guys.

---

### Post by RavanH on 2008-01-29
Right... I am experiencing this too with a Xubuntu 7.10 32bit version on an ASUS laptop. But the WEIRD thing is that with the Ubuntu version, the install process does not hang at 15% but goes on and installs Ubuntu/Gnome (only seems to take hours) just fine...

I have found that I had to ad the boot option 'nolapic' to get both Live CD sessions up and running (and after installation of Ubuntu, I had to ad it manually to grub's menu list too) but even experimenting with 'acpi=off' and 'noapic' in various combinations did not solve the 15% issue during Xubuntu install.

Hope this mystery gets solved because I would really like to start with a clean Xubuntu installation :(

---

### Post by Serverguru on 2008-02-28
I have ran into this problem as well.  I don't know if anyone has found a work around or fix for it, but I can at least say what  I have seen happen.  If I opened up a console and watch the system memory, it would drop almost to nothing (this system had 256M).  As I noticed this, I tried putting a swap partition on the drive before installing to help alleviate the problem.  This made the install go even smoother, however, as soon as it started detecting the filesystem, it would turn the swap off and once again lock it up (on mine it completely locks up).  So, I set up two console windows (one to run a top and one to turn the swap back on) and as soon as I could I turned the swap on before it locks.  This allowed me to go through the rest of the process fine.

---

