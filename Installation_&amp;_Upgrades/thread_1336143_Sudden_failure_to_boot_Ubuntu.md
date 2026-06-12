---
title: "Sudden failure to boot Ubuntu"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by wrightak on 2009-11-24
Hi there,

I started a thread here:

[http://ubuntuforums.org/showthread.php?t=1328648](http://ubuntuforums.org/showthread.php?t=1328648)

about this issue but only one very kind person replied, who has little experience with Wubi. After reading this page:

[https://wiki.ubuntu.com/WubiGuide#Cannot](https://wiki.ubuntu.com/WubiGuide#Cannot) boot into Ubuntu

I followed the instructions there and am posting here instead. I hope someone can take a look.

I installed Ubuntu 9.10 using Wubi and used it happily with no problems for 4 days. Then one day, things went wrong and it has been the same ever since. After selecting Ubuntu at startup, errors are encountered and are displayed very briefly. The computer speaker beeps at me. I am then directed to a Grub command prompt. I am only able to use certain commands which are listed when I press tab. I have taken a photo of this screen, showing the available commands and the results of entering "ls". Here is the photo:

[http://img22.imageshack.us/img22/7111/p1030178e.jpg](http://img22.imageshack.us/img22/7111/p1030178e.jpg)

My questions are:

1. Why did this happen? I speculated in the previous thread that it may be related to a large number of updates that were installed automatically the previous evening.

2. How do I fix this?

3. Should the uninstall process complete successfully? If I reinstall, will I encounter the same problems?

Thank you very much for your help. Sorry for the newbie questions.

---

### Post by MelDJ on 2009-11-24
i did not go through the other post but you could try doing a chkdsk /f of your drive and then boot into ubuntu.
or try booting into recovery mode and see what is the error (the last thing to load before the prompt comes up or the error which comes up)

---

### Post by wrightak on 2009-11-24
I managed to take a photo of the errors that are briefly displayed before the prompt. Here it is:

[http://img193.imageshack.us/img193/4733/p1030180j.jpg](http://img193.imageshack.us/img193/4733/p1030180j.jpg)

When I see garbled text like that, it's usually a sign of encoding problems. This is a Japanese machine with a Japanese Windows XP installed at the factory. I get unicode problems a lot.

Then again, I could be way off base.

I should also mention that I ran chkdsk and there were no problems encountered.

---

### Post by wrightak on 2009-11-24
> **MelDJ said:**
> i did not go through the other post but you could try doing a chkdsk /f of your drive and then boot into ubuntu.
or try booting into recovery mode and see what is the error (the last thing to load before the prompt comes up or the error which comes up)
Thanks for the reply. I already did a chkdsk and no problems found. Attempts at booting after that fail.

For your other suggestions, I will try and explain a bit better.

When things were working, the first screen I get is 

1. Win XP
2. Ubuntu

Then after selecting 2, I get

1. Ubuntu
2. Ubuntu recovery mode
3. Ubuntu something else
4. WinXP

Right now, I'm not getting the second menu. The errors occur immediately and I am presented with the prompt I photographed.

---

### Post by MelDJ on 2009-11-24
does that mean that before you select ubuntu, it screws up? if that is so, grub must have been messed up.


well...as it seems, if i were you, i would uninstall it. if there are no important files there, i will cut the hassle and do a reinstall. 
if you do decide to reinstall bear in mind two things:
a) whatever that was in ubuntu will be lost forever
b) install ubuntu on a new partition when you reinstall. its much more stable as it is independent from windows 

hope you find a way to repair it if you dont want to uninstall ;)

---

### Post by wrightak on 2009-11-24
> **MelDJ said:**
> does that mean that before you select ubuntu, it screws up? if that is so, grub must have been messed up.


well...as it seems, if i were you, i would uninstall it. if there are no important files there, i will cut the hassle and do a reinstall. 
if you do decide to reinstall bear in mind two things:
a) whatever that was in ubuntu will be lost forever
b) install ubuntu on a new partition when you reinstall. its much more stable as it is independent from windows 

hope you find a way to repair it if you dont want to uninstall ;)
Thanks for the advice. I'm prepared to lose the data. I just want to thoroughly investigate things first.

---

### Post by wrightak on 2009-11-24
> **MelDJ said:**
> does that mean that before you select ubuntu, it screws up? if that is so, grub must have been messed up.
I think so, yes. Before there were two menus, now I only get the first. Maybe this is a grub problem?

---

### Post by MelDJ on 2009-11-24
i believe so. since we arent so fussy about data loss, we can try some ways without a care in the world! :D

you might want to try this: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) to see if you can recover grub

---

### Post by bomboyj on 2009-11-26
I am also having this same problem i would like to know if anyone has fixed this once i do i am going to get my files off and then make a true partition :] so please help

---

### Post by harlequinade on 2009-11-26
> **bomboyj said:**
> I am also having this same problem i would like to know if anyone has fixed this? Once i do i am going to get my files off and then make a true partition :] so please help

Yes, Bomb - I'm having the very same problem, but the 
only fix seems to be re-installation.

One snag with that is, as soon as we re-install how do
we know it will not do an update, get the same core
files and breakdown all over again??

Michael.

---

### Post by wrightak on 2009-11-28
> **harlequinade said:**
> Yes, Bomb - I'm having the very same problem, but the 
only fix seems to be re-installation.

One snag with that is, as soon as we re-install how do
we know it will not do an update, get the same core
files and breakdown all over again??

Michael.
So you both are experiencing the same problem? I just did a re-install and being prompted to install updates. I haven't done so yet. Do you think that one of these updates is causing the problem? If so, which one?

---

### Post by snipedog on 2009-12-11
Hello,

Apparently I have the same kind of problem. I installed Ubuntu 9.10 on Monday (7.12.09) and everything was working fine. I ran the update function yesterday (10.12.09) and now Ubuntu won't boot anymore, exactly as described in the thread. It only boots into the GRUB menu when I select Ubuntu and that is it. Shortly before the GRUB command line is loaded it says on a black screen:  no wubildr

I should mention that I have installed Ubuntu through Wubi Installer next to a Windows Vista installation. I searched for the  no wubildr error and it says that Wubi might be missing some files. I checked the C:\Ubuntu\Disks folder and everything seems to be in order.

It would be great if someone could find a solution or this.

In my opinion this was definitely caused by the update.

Many thanks.



 only get to the GRUB menu

---

### Post by wrightak on 2009-12-11
I can also confirm that an update is triggering the problem. After my previous post, I re-installed and went through the essential security updates one by one, trying to figure out which one it was.* None of them triggered it, so I assumed that it was a recommended update instead. A few days later, I get prompted to install essential security updates again. I do so (in bulk) and land myself in the same situation.

No more messing around with Wubi for me. When I've got time, I'm partitioning.

How does one get the attention of whoever is developing the Wubi installer? Is it not officially supported by Canonical now? Is this problem restricted to certain users?

*By the way, this isn't easy. You have to manually uncheck and check the boxes. Can we have a select/de-select all feature please?

---

### Post by MelDJ on 2009-12-11
> **wrightak said:**
> 
How does one get the attention of whoever is developing the Wubi installer? Is it not officially supported by Canonical now? Is this problem restricted to certain users?


from the wubi FAQ: 
Wubi was born as an independent project, as such 7.04 and 7.10 are unoffical releases. But since 8.04 the code has been merged within Ubuntu and Wubi is now fully supported. Wubi can also be found in the Ubuntu 8.04 Live CD.

wubi is simple to set up but partitioning brings better benefits

---

### Post by Khepesh on 2009-12-11
I'm pretty much having the same issues after updating and subsequently following the advice to reboot just yesterday. I too used Wubi, as being new to linux I wasn't sure just how long I'd want to keep it.
The problem seems to be stemming from an inability to locate the kernel, and being somewhat of a newbie I've no idea just how to find it myself. I ran through some instructions that were supposedly meant to help me find it and set it as the default, but the end result was me trying desperately to restrain myself from throwing my laptop out the window.
After selecting Ubuntu from the first menu, the prompt I was used to seeing appears, lists the first partition (which is some factory system partition), moves to the second which is where Ubuntu and Vista are installed, and after hanging for a awhile longer than it used to, boots a Grub2 command prompt. I figure the steps I followed were intended for Grub1, and could explain the error... if anyone has any suggestions as to what course of action I should take (short of a complete reinstall) I'd undoubtedly appreciate it. I'm getting quite tired of Windows' limits, but I'm not quite ready to abandon it fully.

---

