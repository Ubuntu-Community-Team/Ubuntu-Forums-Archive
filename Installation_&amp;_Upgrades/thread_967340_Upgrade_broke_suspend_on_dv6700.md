---
title: "Upgrade broke suspend on dv6700"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by CalderCoalson on 2008-11-01
[COLOR="Red"]**UPDATE:**Rad3k_N found a solution howto written by 67GTA here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)[/COLOR]

I had suspend working under Hardy on my HP dv6700z, (pretty similar to the rest of the dv6000 series, but the z stands for an AMD processor), but the Intrepid upgrade broke it.  I had the installer replace my customized acpi-support file, (but when I went back to the same configurations it didn't work again).  The changes I had made were:
```

SAVE_VBE_STATE=true
POST_VIDEO=false
USE_DPMS=true

```

I've tried tweaking all three, but nothing changed the behavior  When I resume, the lights come on but the wireless light remains orange, (not in use) and the capslock and numlock lights are unresponsive, (which I assume to mean the kernel is not alive) and the screen remains black, (no backlight, just off).

Possibly relevant information:
nvidia 177 accelerated graphics driver with a GeForce 7150M
Kernel 2.6.27-7 (same problem in 2.6.26-?)
64-bit clean install of Intrepid, (although the same thing happened when I originally tried upgrading from 32-bit Hardy)

Any help will be much appreciated, as this is the only operating system on my only computer which I happen to carry around a lot, (so suspend is a rather nice feature, :D)

Thanks,
-Calder Coalson

---

### Post by CalderCoalson on 2008-11-02
*selfish bump*

---

### Post by CalderCoalson on 2008-11-02
I also ran into two other completely unrelated issues, (both of which are only slightly annoying, unlike suspend).

First, the window title bars frequently breaks down and turns from brown to white with a line through it and no close-minimize-maximize buttons.  This can be solved simply by switching to another window and then back, but it's rather annoying.  I'm using Compiz, if that explains anything.

Second, when I start up the computer, the orange bar goes about 1/3 of the way to the right side, and then just stops.  I've tried leaving it on for a while and going to CTRL-ALT-F1, but both reveal that nothing is actually happening, instead of the GUI just being borked.  Anyway, this would be showstopper, (not being able to boot!) but I fortunately discovered that by holding down the ENTER key, I can make it start up normally.  When I let go of the ENTER key, all progress halts likes it's playing red-light green-light.  I'm guessing this is a trivial debugging feature left over from the development cycle.  It really doesn't matter much, but I can't start the computer, walk away, grab something, and come back to a login screen.
[COLOR=Red]
UPDATE: dsmex found an excellent solution to this problem on the second page of this thread.
At the end of the /boot/grub/menu.lst file, there is a list kernels with options for each.  Each entry should look something like this:
```
title           Ubuntu 8.10, kernel 2.6.27-12-generic
uuid            c12f0ae6-c9a8-4643-84a7-b201788b033f
kernel          /boot/vmlinuz-2.6.27-12-generic root=UUID=c12f0ae6-c9a8-4643-84643-84a7-b201788b033f ro quiet splash
initrd          /boot/initrd.img-2.6.27-12-generic

```You need to add 'acpi=noirq' to the end of the kernel line.  For instance, my kernel line would look like this:
```

kernel          /boot/vmlinuz-2.6.27-12-generic root=UUID=c12f0ae6-c9a8-4643-84643-84a7-b201788b033f ro quiet splash acpi=noirq

```
[/COLOR]

Again, thanks in advance for any help,
-Calder Coalson

---

### Post by CalderCoalson on 2008-11-02
Original problem confirmed with driver version 173 as well.  ](*,) :cry:

---

### Post by CalderCoalson on 2008-11-03
Any help whatsoever would be much appreciated...

---

### Post by dsmex on 2008-11-03
I can confirm that this problem on a HP dv6610. I have been using kubuntu 7.10 for a long time and did a clean install of kubuntu 8.10 on a different partition.

It's a 2x64 AMD processor, and I'm running the 64-bit version. I'm using the nvidia 173 driver and the broadcoam wi-fi driver. (Had no problem there)

In 7.10 suspend worked fine. Hibernate didn't work, but I never bothered to try to fix it.

In 8.10 I can not get suspend to work. I have tried most of the tips I can find online for acpi-support settings, disabling desktop effects etc.

It seems to enter suspend correctly. It powers down, and the light on the power-button and on the front are blinking.
To wake it up, pressing a key doesn't have any effect (it did in 7.10). I need to press the power button to get any reaction. This will get the lights back on the 'multimedia' touch buttons (volume, play, stop..). The screen however, does not get switched on. The computer freezes in this state. The only thing I can do is to turn it off. There is no reaction to caps lock, CTRL+ALT+DEL or CTRL+ALT+BACKSPACE. 

There is also a problem on boot where I have to press and hold a key to get past the initial boot phase. Any key seems to work. I guess it just needs an interrupt.

I hope someone can help on this. Ubuntu/Kubuntu is getting better all the time and easier to install. The suspend feature is however a critical feature on a laptop. With the popularity of the HP pavillion dv-series I am sure a lot of users have the same problem.

---

### Post by CalderCoalson on 2008-11-03
> **dsmex said:**
> 
There is also a problem on boot where I have to press and hold a key to get past the initial boot phase. Any key seems to work. I guess it just needs an interrupt.


That's interesting dsmex, I hadn't thought to try any other keys.  I'll confirm that as soon as I can.

---

### Post by leachyboy2001 on 2008-11-03
I've got a dv6000 also have the holding key down to boot problem.  I haven't confirmed any issues with suspend.
The update also broke some of my multimedia keys.

---

### Post by Josueped on 2008-11-03
I have the exact same problems on a Compaq Presario F700

I turned off the splash screen and I got a kernel panic...fun. But when I restored the splash it was as before, I had to hold down a button (any) and it booted

---

### Post by Josueped on 2008-11-03
Looks like the suspend thing is a known bug

[https://bugs.launchpad.net/ubuntu/intrepid/+source/pm-utils/+bug/287374](https://bugs.launchpad.net/ubuntu/intrepid/+source/pm-utils/+bug/287374)

---

### Post by dsmex on 2008-11-03
Joshueped

Are you sure this is the same issue?

To me the problem described seems to be about entering suspend mode and not about resuming. However, I am not at all an expert.

I guess if this is the same issue, installing pm-utils_1.1.2.4-1ubuntu8 from intrepid-proposed repository would solve it...

Did anybody try this?

---

### Post by CalderCoalson on 2008-11-03
Actually, that looks more like a problem with the suspend process, not waking from suspend...

---

### Post by CalderCoalson on 2008-11-03
If someone could even tell us how to start debugging this, it would be great.  I hate to complain after all the hard work that's gone into making Intrepid, but this situation kinda sucks: having something that use to work get broken by an upgrade?  I don't want to use the V-word, but you know were all thinking it.

---

### Post by dsmex on 2008-11-03
A bit of good news...

The hold-a-key-to-boot issue is a know issue and it is very easy to fix. You just need to add a parameter in the grub menu file.

Instructions here:
[http://www.ensode.net/roller/dheffelfinger/entry/just_finished_installing_ubuntu_intrepid](http://www.ensode.net/roller/dheffelfinger/entry/just_finished_installing_ubuntu_intrepid)

Bug report here:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/272247)

I just did this, and it works.. It boots all by itself, and fast.

For the suspend issue, I have still no idea.

---

### Post by CalderCoalson on 2008-11-03
Following dsmex's lead, I've attempting to upgrade to the intrepid-proposed versions of four hopefully relevant packages: nvidia-177-kernel-source, nvidia-177-modaliases, nvidia-glx-177 and pm-utils.  I'll keep you updated...

---

### Post by dsmex on 2008-11-03
This seems to be a bug report for the suspend problem.

However it has been closed, suggesting that a new report is filed if the problem still exists.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232045](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232045)

---

### Post by CalderCoalson on 2008-11-03
Well, the proposed updates didn't do anything as far as waking from suspend is concerned, but the solution dsmex found to make Intrepid start automatically works like a charm.

---

### Post by CalderCoalson on 2008-11-04
This looks more like a problem with initial suspension process than what we're experiencing, with not being able to wake from suspend...

---

### Post by Josueped on 2008-11-04
> **dsmex said:**
> Joshueped

Are you sure this is the same issue?

To me the problem described seems to be about entering suspend mode and not about resuming. However, I am not at all an expert.

I guess if this is the same issue, installing pm-utils_1.1.2.4-1ubuntu8 from intrepid-proposed repository would solve it...

Did anybody try this?

You are right, it is a different issue

---

### Post by CalderCoalson on 2008-11-05
Cross your fingers, but there are updates to the linux-headers-2.6.27, linux-headers-2.6.27-generic and linux-2.6.27-generic.  We'll see if that does anything...

[EDIT] Nope...  :'( [\EDIT]

---

### Post by dsmex on 2008-11-05
I discovered yesterday that my laptop actually does wake up from suspend, it just takes a very long time. I haven't had any time to investigate this yet, but I will look into it.

On resume I get the following:
- The fan start
- The power light and the multimedia keys goes on
- The HD light goes on for a split second
- Then a long wait (several minutes)
- The computer doesn't react to anything (neither CTRL+ALT+DEL, CTRL+ALT+INS)
- I then get a garbled screen..
- After moving the mouse or pressing keys, it resumes normally

I did try to press several keys when the computer was in its frozen state. I also switched off and on the wifi button. I don't know if this helps, or if its just a matter of waiting.

I have only had it wake up once, so I don't know yet if it is consistent behavior. I will let you know when I have time to debug a bit more.

---

### Post by CalderCoalson on 2008-11-05
Interesting, dsmex, I'll confirm as soon as I can.  It should be easier to debug now too, as we don't have to go to a bunch of way-to-complicated steps to get dmesg to save its output long enough for us to reboot and check it.

[EDIT]I had the same initial result, with colors and gradients changing every 2 seconds, but it continued for another 30 minutes before I decided that it wasn't getting anywhere.  The kernel was definitely alive, because the Caps Lock and Num Lock lights responded, but the wireless one didn't, and I don't really know what that means.[\EDIT]

---

### Post by dsmex on 2008-11-05
I tried a few more times...

It seems to be a more or less fixed delay of 3 minutes.

I have changed some settings in the acpi-support file. I have no idea if the changes I have done affect anything, but I have attached my current file.

I also installed todays updates, but it didn't seem to affect suspend/resume.

I would appreciate any help on debugging the suspend/resume issue. Which log files to check, what to look for etc.

---

### Post by dsmex on 2008-11-05
I did one more test... but now I seriously need to work ;-)

I suspended, then pressed the power button to resume and waited.
Without touching any key... the same thing happens. It seems dead for just under 3 minutes and then magically comes back to life. Everything seems to be working. The wi-fi reconnects itself automatically without any problem.

So, the problem seems to be that I have a 3 minute resume, which used to be about 5 secs on kubuntu 7.10.

I have attached my syslog from the moment I moment I suspend until everything is up and running again. 

I would be very happy if some knowledgeable person would have a look at it.

Please let me know if more information is needed.

---

### Post by homerhomer on 2008-11-05
You might have the same bug that I have.

If you have a single running the 64bit version of Ubuntu and it reboots when you resume.
you might want to follow this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/292515)

---

### Post by CalderCoalson on 2008-11-05
Do you know if that is that a confirmed AMD specific issue, homerhomer?

---

### Post by CalderCoalson on 2008-11-07
*bump*
*Although there aren't that many of us experiencing this, it's a debilitating bug and would be immensely discouraging to someone trying Ubuntu for the first time on a similar model.*

---

### Post by ljoslin on 2008-11-07
I'm having similar issues to the suspend/hibernate issues explain in this thread.  I have a compaq Presario F700 (AMD 64, 2 gig ram, NVidia video).  From what I have seen it appears to be an ACPI issue, but haven't really had enough time to play around with different options yet.  Hopefully I will have time early next week.  Has anybody tried SSHing into the machine that won't wake up, see if it's actually still down or maybe video just isn't waking up correctly??

-=Ljoslin=-

I think I have sort of confirmed it's a ACPI issue.  I have been playing with acpi-support and getting different responses.  I have even gotten it to "Hibernate" but it thought it was rebooting?!  however it did save everything.

---

### Post by Rad3k_N on 2008-11-07
Hello there,
I'm experiencing the same problem - on my HP dv6840ew (amd64, nvidia graphics, broadcom wifi) hibernate and suspend were working perfectly in Xubuntu Hardy, but in Intrepid suspend is broken.

It's just like described here - laptop will suspend, with a power led blinking, but it won't resume correctly. I haven't tried waiting more than 10 minutes, so I don't know if it'll eventually resume, but I'll check it.

Hibernate works, but not as good as in Hardy - resuming from hibernation takes now more time than rebooting.

I'm also getting boot lag, and pressing a key helps too. I have yet to check whether the solution mentioned by dsmex works.

---

### Post by CalderCoalson on 2008-11-08
> **ljoslin said:**
> Has anybody tried SSHing into the machine that won't wake up, see if it's actually still down or maybe video just isn't waking up correctly??

The CapsLock and NumLock lights don't change, meaning the kernel, (and therefore SSH) is not alive.

---

### Post by CalderCoalson on 2008-11-10
testing update to linux-restricted-modules-common... failed.

---

### Post by maskman_01 on 2008-11-12
HP Pavilion dv6607rs (AMDx2), NVIDIA GeoForce 7150M, and Broadcom 94311.

Running Kubuntu 8.04 with KDE 3.5, resume and suspend worked beautifully.  8.04 also worked well with KDE 4 once I installed PowerDevil.

Under Kubuntu 8.10 suspend and hibernate is spotty at best.

If the laptop is on AC then I can initiate a suspend/hibernate without an issues.  It also resumes without any issue when on AC.  It will not, however, suspend after 60 minutes of inactivity as I have set in Guidance.

When the laptop is on battery it will not suspend/resume properly.  When it goes to suspend/hibernate the screen goes dark (backlight is still on), there is no HDD activity, and the laptop power LED is on.  If I plug the power back in the laptop finishes it suspending or hibernating. 

Coming out of a hibernate on AC is very similar.  The laptop usplash says it is waking up and there is HDD activity.  Eventually the HDD activity stops but the usplash continues to say it is waking up.  Plugging the laptop back in prompts the usplash to disappear and the screensaver loads. 

Any thoughts?

---

### Post by stanley drew on 2008-11-19
I am giving this a bump because of the very useful post above from dsmex regarding the hanging boot on some hp amd64 laptops. Adding acpi=noirq to the grub boot options works amazingly. I had searched for the last two weeks for a solution to specific hangs i was getting during boot but this single solution solved all of them.

I can now move on to working on hibernate and suspend. I'll post here after some testing.

---

### Post by stanley drew on 2008-11-19
Ok so I cannot return from suspend either (surprise!). But I do get some messages from the kernel as it's trying to come back. First there is a wait of about 2 or 3 minutes with a blank screen. then there are a bunch of messages about killing various processes because there's not enough memory, e.g. compiz, gnome, nautilus, something with wpa. Is anybody getting kill signals like that as well?

---

### Post by Rad3k_N on 2008-11-19
Stanley, what video driver do you use? I tried "acpi=noirq", but it gave me very strange side effects. I couldn't start X using proprietary nvidia driver, it worked only with nv. And even then, weird things happened so beware.
The workaround I'm using is "hpet=disable". It seems to have no visible side effects and fixes the need-to-hold-a-key-to-boot problem.

Resuming from suspend still doesn't work though. I tried to debug it following instructions from [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) but it didn't give me any clues.
When I have more time I'll try some more serious debugging, like described here: [http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)

---

### Post by stanley drew on 2008-11-20
Rad I'm using the proprietary nvidia driver version 177. i'm also using ath5k for my AR5007 wireless card.

---

### Post by CalderCoalson on 2008-11-25
I am rather embarrassed for the Ubuntu team over this issue.  Next time, I hope they consider making the OS actually work properly before releasing it...

Yes, as you've probably guessed, there's still no fix.

---

### Post by TuckWat on 2008-12-13
I have an HP dv2315nr and I'm unable to resume sleep in intrepid as well.  Any updates or ideas for me to try?

Thanks

---

### Post by CalderCoalson on 2008-12-23
I wish!

---

### Post by CalderCoalson on 2009-01-08
*Violent Bump!*

---

### Post by khb008 on 2009-01-18
Hey everyone, I have had the same problem, and I have been looking for a solution for a long long time.  I can't seem to figure it out, I have tried almost every single one of the tweeks that there is on the net.  I still can't get it to work.  Im just here to ask 2 questions:
1) All the changes i made (to acpi file and xorg file) should i put in a live cd and go for repair? or should I just continue on using my pc as if I had never made the changes??
2) Since there hasn't been any new posts on this thread I am just wondering If any one found a good tut or guide?  If yes could someone plz post it.  

I will keep on searching since suspend is a big must for me.  I cant shutdown computer everytime I leave the chair.  If I find something I will definitely come back to post it.  And Calder is absolutely right, this is very discouraging.  I am not new to ubuntu, I had it since 6.10.  And now a major component of laptops is not functioning due to this bug.  I sincerely hope they get this fixed soon.

---

### Post by for.i.am.root on 2009-01-29
Hi guys:

HP DV6700z CTO with the same problem: have to hold key during boot, no suspend, no hibernate. I am also experiencing a problem with my caps light and num light, they don't work at all. When I first switched over to Ubuntu the caps light worked, however, now it doesn't?!?!

Is this an AMD problem or is this a x86_64 problem??? Is anyone with this problem running a 32 bit version of *buntu or is everyone running 64?

Will keep you updated on my journey.

Please take it easy on these guys. Remember that *buntu has better hardware support "out of the box" than any other free flavor around and most non-free flavors as well. We don't need any more "violent" bumps.

---

### Post by eigenman on 2009-02-07
Hey Maskman_1,

did you ever find a workaround? I have the exact same model (dv6607), with the exact same problem.

As a side note, I was using gentoo for the past year, since when I initially bought my laptop, wireless/video/sound worked in gentoo but not in ubuntu. However, in a recent (careless) upgrade, my suspend/hibernate broke in gentoo, leading me to switch to install Ubuntu, which seems to be more functional to some extent right now.

Cheers,
eigenman

---

### Post by CalderCoalson on 2009-02-18
I recently received an email from one (1) Leann Ogasawara as follows:
> Care to test the latest Jaunty 9.04 Alpha 4 release to confirm if thisissue remains?  It contains a newer 2.6.28 based kernel.   You should be able to test suspend via a LiveCD.  Please let us know your results.

I will be testing this over the weekend, but just wanted to post in case anyone wants to try it sooner.

---

### Post by GeneW on 2009-03-01
I'm looking forward to finding out if is(or will be) fixed in Jaunty.  I have an HP DV6915 and have (temporarily) given up on Ubuntu due to this suspend issue.  A laptop that doesn't suspend is pretty much worthless to me so I had to revert back to using Vista.

---

### Post by Rad3k_N on 2009-03-25
Hi all!
I have some good news - I think I've found a workaround for this problem. At least it works for me.
If you want to try it yourself, follow the instructions from _[this thread]("http://ubuntuforums.org/showthread.php?t=1036051")_

It also seems to fix the "system freezes at boot unless you press and hold a key" bug, which is quite common on these laptops.

---

### Post by CalderCoalson on 2009-05-08
Holy $#!& it works!!!  Thanks so much for the tip!

---

