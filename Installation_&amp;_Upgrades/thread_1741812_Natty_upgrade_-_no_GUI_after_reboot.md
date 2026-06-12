---
title: "Natty upgrade - no GUI after reboot"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by seeyouza on 2011-04-28
Hey guys

Hoping someone can help. I upgraded to Natty this afternoon. Everything went fine (or so I thought) but on rebooting, I see a console version of all the startup scripts (ie. Starting <blah> [OK]) etc, it runs through everything and finishes, but then just sits there. I have a blinking cursor, but not even a login prompt, and nothing else happens. Almost as if Ubuntu thinks it has started the GUI. How can I find out what the problem is and fix it?

---

### Post by seeyouza on 2011-04-28
As an addendum - ctrl-alt-F2 gives me a login prompt and I can log in. If I try a "sudo service gdm restart"

I get:

gdm start/running, process 2335

But still no GUI.

---

### Post by Hedgehog1 on 2011-04-28
This sound like the video driver from the previous version of Ubuntu needs to be swapped for the new one.

May I suggest downloading the Natty ISO and repeating the upgrade from the LiveCd/LiveUSB you create from the ISO:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

You **might** want to backup any data from you PC using the LiveCD/LiveUSB in 'TRY' mode just to be safe, before you run the update again.


***The Hedge***

:KS

---

### Post by seeyouza on 2011-04-28
Will I still get that upgrade option if the system is essentially already running 11.04? I don't want to lose my entire setup.

---

### Post by roh8880 on 2011-04-28
Ok, I have something similar. Absolutely no GUI. I get a prompt asking for my loging a pword, but in a script only fashion. Then I get this:

[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-1.jpg[/IMG]

I didn't do anything different this time. Somebody help me!

---

### Post by ninja9578 on 2011-04-28
I have the same problem, how do you revert the distro upgrade?

---

### Post by Hedgehog1 on 2011-04-28
> **seeyouza said:**
> Will I still get that upgrade option if the system is essentially already running 11.04? I don't want to lose my entire setup.

Yes, you will get an 'upgrade from 11.04 to 11.04' option.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-28
> **roh8880 said:**
> Ok, I have something similar. Absolutely no GUI. I get a prompt asking for my loging a pword, but in a script only fashion. Then I get this:

I didn't do anything different this time. Somebody help me!

I have posted on your thread with a simliar solution.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-28
> **ninja9578 said:**
> I have the same problem, how do you revert the distro upgrade?

**Sadly, you cannot revert a disto upgrade.**  Your only option is to save your data (boot from a LiveCD/LiveUSB and copy your data to an external HDD or USB stick) and reinstall the version of Ubuntu you wish to use.



***The Hedge***

:KS

---

### Post by Lencho66 on 2011-04-28
I think I will wait until all the bugs are mostly worked before upgrading to Natty. I have a touchscreen lap with a crappy video card, thus I will upgrade in 2 or 3 months. Thanks for the help though :)

---

### Post by Hedgehog1 on 2011-04-28
> **Lencho66 said:**
> I think I will wait until all the bugs are mostly worked before upgrading to Natty. I have a touchscreen lap with a crappy video card, thus I will upgrade in 2 or 3 months. Thanks for the help though :)

**Waiting is a good plan.**

Be aware you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by ninja9578 on 2011-04-28
> **Hedgehog1 said:**
> **Waiting is a good plan.**

Be aware you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

Is there a way to load that up if you are already stuck at the command line?  I can't even get X's failsafe to load up.

---

### Post by seeyouza on 2011-04-29
Unfortunately, the LiveCD upgrade didn't work for me. Rather, I didn't get an upgrade option. I have a SSD and a SATA drive, the SSD being partitioned into my Ubuntu partition and a Windows 7 partition. The installer didn't seem to detect the existing version of Ubuntu, so there was no upgrade option, and I don't want to erase everything I already have installed.

I'm currently sitting with re-installed ATI drivers (the one from Additional Drivers in the Admin menu) - the resolution and everything else seems to run properly - but I cannot log into Unity, or Classic with effects. It seems to be stuck on "Classic (no effects)" no matter which option I select.

Any advice?

---

### Post by seeyouza on 2011-04-29
Really can't seem to come right with this. I guess either the ATI drivers aren't working, or they're not installed/configured properly. I tried installing GNOME3 to see if that would make a difference. It installed, booted, and then told me it was running in fallback mode, most likely because my graphics hardware couldn't support it. I have a ATI HD6950, so this seems a little unlikely. Is there any way I could fix the driver/graphics setup?

---

### Post by seeyouza on 2011-04-29
In case this helps anyone else - I've found following the steps listed here:

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

Let me boot into GNOME3/Unity. However, animations still run slowly/choppy - but I can at least use the machine.

---

### Post by surgus on 2011-04-29
Steps for ATI users:
1. When the boot hangs, press ctrl+alt+f1.
2. Login as user with root privileges.
3. Type "cd /usr/share/ati" and press enter.
4. Type "sudo sh ./fglrx-uninstall.sh" and press enter.
5. Type "sudo reboot".

---

### Post by kolbiel on 2011-04-29
any advice for nvidia users?

---

### Post by PeterWhittaker on 2011-04-30
> **Hedgehog1 said:**
> This sound like the video driver from the previous version of Ubuntu needs to be swapped for the new one.

May I suggest downloading the Natty ISO and repeating the upgrade from the LiveCd/LiveUSB you create from the ISO:

:KS

Hedge, you're kidding, right? The supported upgrade path for a production system leaves the user and their system in an unworkable state and the solution is to download an ISO?

I have the same problem and am lucky enough to have a machine on which I can create a CD - but others might have only the machine that has just been hosed. Of course, I don't have any blank CDs, why would I? And the only available USB drive has a working bootable version of 10.10. Why would I want to replace that, given my natty experience?

I would much rather have a command line alternative. If you have one to propose, I am all ears, all eyes.

---

### Post by Nymn on 2011-04-30
So are any of these a definite solution? I get the same screen that roh8880 has. I need to fix this!:mad:

---

### Post by PeterWhittaker on 2011-04-30
> **PeterWhittaker said:**
>  The supported upgrade path for a production system leaves the user and their system in an unworkable state and the solution is to download an ISO?

I would much rather have a command line alternative. If you have one to propose, I am all ears, all eyes.

In the end, my need to restore this machine took precedence over all other factors. So my printer drivers and configuration? Gone.

My virtualbox installation? Gone. Crossover? Gone. Other things I haven't yet remembered? Gone, gone, gone.

This is the worst Ubuntu upgrade ever. Bear in mind I started with Breezy. And they've all been better than this.

---

### Post by MAFoElffen on 2011-04-30
Sorry I didn't notice this thread... was putting out other fires.

Have you read or tried the things in this sticky first?
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by khoacao on 2011-04-30
> **roh8880 said:**
> Ok, I have something similar. Absolutely no GUI. I get a prompt asking for my loging a pword, but in a script only fashion. Then I get this:

[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-1.jpg[/IMG]

I didn't do anything different this time. Somebody help me!







Hi all, 
This is both frustrating and exciting at the same time. Being frustrated  because I just spent six hours trying to THINK how to fix this very  same problem without being able to back up my home folder that contains  800Gbs of data from LIVECD. And I just got so excited ten minutes ago to  see that a simple step to get a view of the new layout of Natty  version. 

Here is the trick, whatever you are stuck at, Ctrl+Alt+Del to reboot the  system, when it starts asking "Press Esc for..." with the 3-second  timing, please do so, *_HOLD ON TO THE ESC KEY_*. 

Next you will see a listing of various "kernel" and please pay close attention to the line **GNU/Linux 2.6.38-8-generic-pae i686** and **its recovery version** both of which I am pretty sure are positioned on top of the list. Now ***_CHOOSE_*** the 3rd line which is exactly the same without the *_**"-pae"**_* part and miracle will happen in time, so PLEASE BE PATIENT.

AT LEAST IT WORKS FOR ME, I was literally dancing!!! Guess I'm a noob after all! GOOD LUCK

And I'm dying to see the fix that eliminates this "pae" problem because I need to do this every time.

Thanks all

---

### Post by Rasa1111 on 2011-04-30
> **PeterWhittaker said:**
> Hedge, you're kidding, right? The supported upgrade path for a production system leaves the user and their system in an unworkable state and the solution is to download an ISO?

I have the same problem and am lucky enough to have a machine on which I can create a CD - but others might have only the machine that has just been hosed. Of course, I don't have any blank CDs, why would I? And the only available USB drive has a working bootable version of 10.10. Why would I want to replace that, given my natty experience?

I would much rather have a command line alternative. If you have one to propose, I am all ears, all eyes.


Yeah definitely.

Hedge is a great and helpful guy,
but he has suggested this a number of times lately to people who are left with a non-working system "download an ISO"
uhm, what? 
I know would get agitated if it were me not able to boot my system, and someone told me "download an ISO!" :???:

 Ive also contemplated upgrading to 11.04,
but my 10.10 install is too perfect and too nice to be screwing with it. 11.04 hardly seems worth whatever troubles i might run into along the way.

---

### Post by Hedgehog1 on 2011-04-30
> **PeterWhittaker said:**
> Hedge, you're kidding, right? The supported upgrade path for a production system leaves the user and their system in an unworkable state and the solution is to download an ISO?

Oh boy - I am taking heat on this.

Remember that (as annoying as I am), I did not create the upgrade defect(s) or the overwhelmed servers that dropped 'otherwise good upgrades' on the heads.

It is possible to use an older LiveCD, download the Natty ISO and create a Natty LiveCD or LiveUSB.  But I did neglect to explain the steps for that (I will admit to some rushing about these last two days on the forums with so many request for help).

Granted, not everyone has blank CDs (I am never without then, but I am a card-carrying nerd).

I believe the tee-shirt that says: ***It was already on fire when I got here*** is my only real claim to requesting clemency.

From my own perspective, to load a new version of an OS without creating a matching LiveCD for emergencies and maintenance defies my (rather limited) logic.

The number of folks who had a bad upgrade and then needed to 'back up there data' ***afterwards*** is hard for me to watch. 

I did not mean to give poor advice, it was well meant and based on the way I see the world.

***The Hedge***

---

### Post by Dutch70 on 2011-04-30
> **PeterWhittaker said:**
> Hedge, you're kidding, right? The supported upgrade path for a production system leaves the user and their system in an unworkable state and the solution is to download an ISO?

That's one possible solution. I'm a little surprised that you're attempting to upgrade a production machine in the first place. Especially to a non LTS version that just came out 2 days ago. :shock: 

> I have the same problem and am lucky enough to have a machine on which I can create a CD - but others might have only the machine that has just been hosed. Of course, I don't have any blank CDs, why would I? And the only available USB drive has a working bootable version of 10.10. Why would I want to replace that, given my natty experience? 

I would much rather have a command line alternative. If you have one to propose, I am all ears, all eyes.

a. Don't worry, people with only a hosed system won't be reading his post.

b. Creating a live cd/usb for Ubuntu, or a repair disc for windows is often used for repair or back ups. Why would you not have any? 

c.The people that are on here trying to help others are volunteers & are doing it out of the goodness of their heart. 
If you want to dictate the way that support is given, I strongly suggest you go here...
[[COLOR="Red"]http://www.ubuntu.com/business/services/desktop[/COLOR]]("http://www.ubuntu.com/business/services/desktop")

---

### Post by Hedgehog1 on 2011-04-30
Thanks for coming to my rescue **Dutch70** (see what they did - now your spines are up, too!).

> **Dutch70 said:**
> a. Don't worry, people with only a hosed system won't be reading his post.

I am trying not to laugh to hard as I type this; your comment is very true.  Whether it help or hinders my cause I just cannot decide... :D


***The Hedge***

:KS

---

### Post by Nymn on 2011-05-01
Well, I installed the proprietary driver and now I have my GUI back! It's pretty sluggish, though and I had to re-install the compiz manager (compiz animations are a bit chuggly, too).
Will this get better with updates?

---

### Post by Hedgehog1 on 2011-05-01
> **Nymn said:**
> Well, I installed the proprietary driver and now I have my GUI back! It's pretty sluggish, though and I had to re-install the compiz manager (compiz animations are a bit chuggly, too).
Will this get better with updates?

For debugging purposes, what is the speed difference between 'Classic no effects' (not using Compiz) and 'Classic' (uses Compiz)?  This will help us know if it is driver or Compiz that is slow.


***The Hedge***

:KS

p.s. I am running a clean install of Natty on two different NVidia GPU systems with excellent performance (equal to 10.10 with Compiz), so I don't have a similar system to see your issues.

---

### Post by Nymn on 2011-05-01
I don't think it's compiz, that's just another thing that's slow. It was already a bit slower even before I activated the animations.
There are some other things, too, like funky colors on certain websites (only on Firefox, they're fine on Chrome).

---

### Post by Hedgehog1 on 2011-05-01
> **Nymn said:**
> I don't think it's compiz, that's just another thing that's slow. It was already a bit slower even before I activated the animations.
There are some other things, too, like funky colors on certain websites (only on Firefox, they're fine on Chrome).

Thanks! That helps.

The joys of a new release, huh?

***The Hedge***

:KS

---

### Post by Dutch70 on 2011-05-01
Nymn your chances of getting your problem solved are not very good considering your question about 
system lag is hidden away inside a thread that is titled **"no GUI after reboot"**

Reading this will help you start your own thread so that you & the OP 
get the undivided attention you deserve.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by khoacao on 2011-05-02
Man, I guess I have to reinstall the whole thing using ISO after all. It's a pain in the you-know-what to do what I have been doing so far. It's true someone said that this is his also my worst upgrade yet!!:???:

---

### Post by Tanetris on 2011-05-03
> **khoacao said:**
> Hi all, 
This is both frustrating and exciting at the same time. Being frustrated  because I just spent six hours trying to THINK how to fix this very  same problem without being able to back up my home folder that contains  800Gbs of data from LIVECD. And I just got so excited ten minutes ago to  see that a simple step to get a view of the new layout of Natty  version. 

Here is the trick, whatever you are stuck at, Ctrl+Alt+Del to reboot the  system, when it starts asking "Press Esc for..." with the 3-second  timing, please do so, *_HOLD ON TO THE ESC KEY_*. 

Next you will see a listing of various "kernel" and please pay close attention to the line **GNU/Linux 2.6.38-8-generic-pae i686** and **its recovery version** both of which I am pretty sure are positioned on top of the list. Now ***_CHOOSE_*** the 3rd line which is exactly the same without the *_**"-pae"**_* part and miracle will happen in time, so PLEASE BE PATIENT.

AT LEAST IT WORKS FOR ME, I was literally dancing!!! Guess I'm a noob after all! GOOD LUCK

And I'm dying to see the fix that eliminates this "pae" problem because I need to do this every time.

Thanks all

If you go into Synaptic Package Manager and do a search for "pae", you'll come up with 3 (iirc) installed packages. Go ahead and uninstall all of them and reboot, and the pae option will disappear from GRUB.

DISCLAIMER: I do not know how wise this is, but I have not suffered any ill effects so far.

---

### Post by KilledXDestiny on 2011-05-06
I'm having the same problem, after the upgrade finished and system rebooted I was presented with a CL, it lets me log in but I have been able to get the GUI working. The first thing I tried was start x but it threw up a bunch of errors like

(EE NVIDIA (0) Failed to load NVIDIA kernal MOdule
(EE) Screen(s) found, but none have a usable configuration
Fatal Server error: No screens found
xinit: Unable to connect to x server: Connection refused

(Full screenshot attached)

After reading the forums for a bit I also tried sudo X -configure which gave me "The number of screens does not match the number of dectected devices" "Configuration failed" and sudo apt-get install ubuntu-desktop which told me I had the latest version.

Any help in fixing this would be very much appreciated otherwise I'm going to look at doing a fresh install from a live disc (assuming I can get all my data from my drive first)

---

### Post by Dutch70 on 2011-05-06
KilledXDestiny

Try other boot options.
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Or try logging in to failsafe mode.

Other than that, you should start your own thread.

---

### Post by KilledXDestiny on 2011-05-07
My apologies, I thought it was considered pointless to have 10 threads on one forum dedicated to the exact same problem.

---

### Post by Dutch70 on 2011-05-07
No need to apologize. It's a common mistake. :)

The problem is that it's very confusing to help more than one person in the same thread. Unless you have the same exact hardware & the same set up, the solution may be entirely different. 
Your problem deserves undivided attention. 

I still don't see where you've started a thread. I hope this means you've got it working correctly, but if not, check the 2 sticky threads at the top of the "installation & upgrade" forum. 

Best regards

---

### Post by CaronMargarete on 2011-05-15
> **surgus said:**
> Steps for ATI users:
1. When the boot hangs, press ctrl+alt+f1.
2. Login as user with root privileges.
3. Type "cd /usr/share/ati" and press enter.
4. Type "sudo sh ./fglrx-uninstall.sh" and press enter.
5. Type "sudo reboot".

I tried the above and it worked to correct my blank screen problem with my acer aspire 4535 however, it seems to have stopped working now. I think there were some updates that required a restart (I don't typically shut my laptop down, preferring sleep mode) but since that restart I'm back to the blank screen and these steps no longer work. 

Does anyone know why this might be? And what I can do to make a permanent fix?

When I follow the steps above I do notice that at Step 3 I get the response "No such file/ directory exists" which I assume is part of the problem but I don't know how to fix it.

Ideas? Please keep your feedback in layman-lady talk as I am rather fresh at all this... Thanks.

---

