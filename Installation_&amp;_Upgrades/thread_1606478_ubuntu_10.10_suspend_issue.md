---
title: "ubuntu 10.10 suspend issue"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by gigaforce1111 on 2010-10-26
Hi all,
I had a dual boot machine with win7 and ubuntu 10.04.
I thought that I'm ready to move on to ubuntu 10.10 as primary OS and loose the windows OS.
(I'm running xp in virtual box just for a few apps)

The problem is that suspend / hibernate is not working!!!
The thing is that sometimes it works and sometimes it doesn't. 
Another thing is that when it does work, doing the same operation fails. In example: suspend - wake up - suspend = fail.

My machine is a laptop so suspend/hibernate is very needed.

I know that there is threads about this and there is a bug listed for this but in generally I'm disappointed and considering moving back to win7 that has good reviews. :(

Any help solving this will be appreciated.

---

### Post by gigaforce1111 on 2010-10-27
anyone?

---

### Post by netipot on 2010-10-27
I have a thinkpad T60 & suspend stopped working in 10.10. I went into power management & changed it to hibernate instead and now it at least wakes up when I open the lid.

---

### Post by meng1usa on 2010-10-27
having the same issue. waiting for someone with the solution.

---

### Post by gigaforce1111 on 2010-10-28
Yep, It's sad.
I'm not familiar with building an OS but it seems that it is going like one step forward and two backward. :(

---

### Post by netipot on 2010-10-28
I thought that I may have worked around my problem. To clarify, It was really that my Thinkpad will not wakeup from suspend which it had had no issues with lucid. I went into power management and set it to hibernate when I closed the lid and it worked well. I tried it repeatedly. However when I shut down the computer, my error message flickered for a second. When I booted up the next day I found I can no longer wake up from hibernation.
Oh well I have faith that this bug will get fixed, maybe only to resurface again down the road. I did fix my problems with opening nautilus. I uninstalled f-spot. Good by f-spot, hello shotwell.

---

### Post by BB_DaKraxor on 2010-10-29
Hi,

Same here.

When Maverick was released I thought I should give it a try. I was happy with Arch Linux, I just wanted to see if Ubuntu has anything to add to the experience. Well, with Arch I had absolutely no problems. Now suspend fails 80% of the time and I get tons of random hang-ups. In the last month I had to reboot my machine at least 6 times. I'm not used to this and I really don't like it. So once again, I have to go back to Arch.

Really sorry, I just can't use a system that is 10% more user friendly and 80% more unstable. I'm just disappointed :(.

---

### Post by ptosiani on 2010-10-29
Yep.. I have the same issue, but it's really a random thing, sometimes when i try to suspend the laptop, y just get a black screen and I hear the FAN working at high speed, but nothing happens if I try to ctrl+alt+F1 or ctrl+alt+del... 

I can see we are all N00bs on this thread, maybe someone with more experience can point some logs files to check, in order to try to find the cause!

Thanks!

---

### Post by gigaforce1111 on 2010-10-31
Yes, I also would like to see a reply from experienced linux user that can help us out!

---

### Post by synthaxx on 2010-10-31
X200 user reporting in with the same issue.

Really random. One time it'll suspend, the other it'll crash.

I've searched launchpad but can't seem to find a bugreport on this. Has anyone gotten any more information on this that can be submitted?

---

### Post by wanted on 2010-11-01
There are plenty of bug reports e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364) [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223)

I'll just paste what I found through a series of experiments:
1) using pm-suspend I could safely suspend the T400 from text console (ctrl-alt-f1) every single time on stock kernel (even if gdm was running on X session at the same time)
2) the same pm-suspend would freeze the laptop randomly if ran from xterm in GNOME
3) upgrading to PPA kernel 2.6.36 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb)) fixed the issue for me completely

---

### Post by dt_ on 2010-11-02
> **wanted said:**
> There are plenty of bug reports e.g. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625364) [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/644223)

I'll just paste what I found through a series of experiments:
1) using pm-suspend I could safely suspend the T400 from text console (ctrl-alt-f1) every single time on stock kernel (even if gdm was running on X session at the same time)
2) the same pm-suspend would freeze the laptop randomly if ran from xterm in GNOME
3) upgrading to PPA kernel 2.6.36 ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb)) fixed the issue for me completely

I tried to install the 2.6.36 kernel via the .deb on the site you posted, but that caused my system to be unable to boot into a graphical interface. Thankfully it kept 2.6.35  around ;)
Did you have to install both the headers and image? Or just the image? Did it just work?

---

### Post by r_gnuce on 2010-11-14
I have an IBM Thinkpad R40 (with an ATI Mobility Radeon 7000 (M6)) that used to suspend and resume just fine when I was running 9.10.  Upon upgrading to 10.10, suspend and resume stopped working.  When the laptop is closed the light that is used to indicate that the laptop is suspended flashes rapidly, and the laptop never fully suspends.  Today I tried disabling kernel mode setting since that's new since 9.10.  It appears to have made a difference... I was able to successfully suspend and resume the laptop twice since disabling KMS.  However, I'm not sure this fully resolved the issue as the first time the laptop suspended fairly quickly, but it took a good bit longer the second time.  At any rate, I thought I'd mention this just in case it might help some one.

---

### Post by netipot on 2010-11-15
I have a thinkpad T60 and gave up on suspend and hibernate so I adjusted my laptop to shutdown when closed. This week I tried suspend again and all has been fine for about a week.

---

### Post by fictivetoast on 2010-11-16
Was having this problem on my Acer 3810t laptop as well - half the time suspended without issue, half the time would dump to a cursor and freeze entirely requiring hard reboot (wouldn't even respond to REISUB).

Seem to have solved the issue by upgradeing to the 2.6.36 kernel by [following directions here]("http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/") (obvious note - be sure to select AMD64 and not i386 if you're on 64-bit).

---

### Post by netipot on 2010-11-18
Well my thinkpad T60 did not keep suspending and now suspend rarely works. So I tried your fix and upgraded the kernel and it did not fix suspend at all. Plus it did not seem to speed things up as the Author said. I am happy enough with the speed as is so no cares yet though it was a little buggy the first time out. As long as there are no other bugs with this kernel upgrade I guess I should consider myself lucky!
I am now back to "shutdown when lid is closed".

---

### Post by florentin_ on 2010-11-19
Is a user issue apparently ...
acpitool -s 
 Function Do_Suspend : could not open file : /sys/power/state. 
 You must have write access to /sys/power/state to suspend your computer.
sudo acpitool -s should work.

---

### Post by netipot on 2010-11-20
florentin_ ....... are you saying that if I open a terminal and type  sudo acpitool -s 

suspend will work?

---

### Post by Bufke on 2010-11-20
I have this issue and can report that running 
sudo acpitool -s 
works. This is probably the easiest way to work around.

Make sure it's installed 
sudo apt-get install acpitool

---

### Post by netipot on 2010-11-20
Well I did it and it worked. Thank you Bufke, I did needed to install acpitool first.
Thank you florentin for letting me know about the fix.
I am going to mark this solved.
I hope that's OK.

---

### Post by twg on 2010-11-22
Well I had this problem and I came to find out that I did not have acpitool installed by default. Once I installed it, suspend worked. I will test it more later as I am in the middle of my work day.

I did a clean install of 10.10 32bit on a Thinkpad T400 and was having a problem on suspend. The laptop was sticking at ***checking battery state*** but no errors were given, it would just sit and speed flash the moon (sleep) led. Took me a bit to catch the problem. 

After installing acpitool, it took 2-3 seconds to suspend without any problems using the suspend off the menu. 

Thanks for the help all.

---

### Post by gigaforce1111 on 2010-11-26
> **Bufke said:**
> I have this issue and can report that running 
sudo acpitool -s 
works. This is probably the easiest way to work around.

Make sure it's installed 
sudo apt-get install acpitool

Hi,
I installed acpitool and it works, excluding 1 time.
Thank you Bufke.
Do you all still have problems with suspend?
Should I mark the thread as Solved?

---

### Post by Darth Pudding on 2010-11-26
I can get my laptop to suspend, but I can't it to wake from suspend. Not sure if that's the same issue you guys were working on here.

---

### Post by djolk on 2010-11-26
I have this problem on dell Inspiron 14. Sometimes suspend/resume works a-ok. Other times it doesn't seem to suspend at all. The screen goes blank, but the power light doesn't blink (indicated its suspended) and if I open the lid the screen stays blank and I have to reboot.

---

### Post by gigaforce1111 on 2010-11-29
hi all,
it seems that the last kernel update 2.6.35-23 fix this issue.
i did have some problems with previous one.
tonight, after updating and trying suspend and hibernate a lot of times i can say it works fine for me now.
is it solved now for you?

---

### Post by ULtimeeTje on 2010-11-30
> **florentin_ said:**
> Is a user issue apparently ...
acpitool -s 
 Function Do_Suspend : could not open file : /sys/power/state. 
 You must have write access to /sys/power/state to suspend your computer.
sudo acpitool -s should work.

Okay I have the same issue... My laptop won't suspend when I log in as my normal user, it does work as root...

When I give the group users write permissions to the files in /sys/power everything works fine. Is there any way I could configure that?

---

### Post by yonnie on 2010-11-30
The 2.6.35-23 update seems to have fixed my wakeup issue.  MSI Wind Netbook.  Before, it would not wakeup after a suspend, was thinking perhaps it was broken at first.

---

### Post by ULtimeeTje on 2010-12-01
the latest kernel update seems to fix it indeed... *yay*

---

### Post by hjsmith67 on 2010-12-08
I have the same issue with my Dell Inspiron 600M. I have changed the settings not to go into sleep mode but even then I sometimes get a black screen (fan running, hard disk lights blinking) and it will not wake-up

I just downloaded the latest patch and it seems to work!

---

### Post by dlanor78 on 2011-01-02
> **hjsmith67 said:**
> 
I just downloaded the latest patch and it seems to work!

I have a dell inspiron 600m and I can't get it to wake from suspend. I have kernel version 2.6.35-24-generic and am running kubuntu with kde version 4.6 RC1.

What patch are you talking about and how do I use it?  Is it still suspending and waking for you?

---

### Post by Morgoth1299 on 2011-01-02
> **meng1usa said:**
> having the same issue. waiting for someone with the solution.

ME TOO! 

Please help someone?

---

### Post by ami7878 on 2011-01-03
> **yonnie said:**
> The 2.6.35-23 update seems to have fixed my wakeup issue.  MSI Wind Netbook.  Before, it would not wakeup after a suspend, was thinking perhaps it was broken at first.

2.6.35-23 as well as the latest 2.6.35-24 did not fix the problem with my Toshiba Satellite U400.  To double check that this has nothing to do with the hardware I booted from a USB flash drive ubuntu 10.04 and it suspends and wakes with no problem.  I also tried a 11.04 dev version and again everything was working like a charm.

**Update**: I just installed linux kernal 2.6.36, following the instructions I found here: [http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/](http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/), and now I can again suspend and resume my pc as before. :)

---

### Post by shan420 on 2011-01-03
Ubuntu doesn't resume after I close my laptop lid. I'm running it on Inspiron 9200, 1.8 ghz, 2 gb ram. 

I attached my acpi-support configuration (sudo gedit /etc/default/acpi-support).

Any assistance please?

---

### Post by nocx on 2011-02-04
My x200 is cannot suspend or hibernate after the updates to 10.10 this week.  Since then I've installed acpi and unchecked everything in the gconf editor, as described by winnie666.  It still won't suspend or hibernate. Help.

---

### Post by djolk on 2011-03-10
Try installing the 'hibernate' package. It fixed everything for me. Like magic.

---

### Post by f03el on 2011-03-19
I can confirm that kernel 2.6.36 does the trick. Why have I waited so long?! This issue has been a plague since I installed 10.10 in October.

This guy seems to summarize the problem quite well: [http://www.linuxquestions.org/questions/slackware-14/unreliable-suspend-with-i915-due-to-regression-in-2-6-35-kernel-851396/](http://www.linuxquestions.org/questions/slackware-14/unreliable-suspend-with-i915-due-to-regression-in-2-6-35-kernel-851396/)

---

