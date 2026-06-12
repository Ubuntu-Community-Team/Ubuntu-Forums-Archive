---
title: "is it safe to install the new kernel image?"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by coreymon77 on 2007-02-10
i have been holding off on updating to the new kernel because of all the problems. i have an nvidia card and i was wondering if the bug in which the nvidia drivers were not working with the new kernel. i was wondering if that has been fixed and it is safe to upgrade to the newest kernel version. i am using edgy and once again have an nvidia graphics card. I also have a wifi card with an atheros chip in it and ive now heard that there are wifi problems too? has that been fixed?

thank you,

coreymon77

---

### Post by persona_o on 2007-02-10
heh, well I just updated the kernel and ended up without a GUI, so no, it's probably not fixed! Luckily I can still access 2.6.17-10.

---

### Post by mikewhatever on 2007-02-10
In my case, neither of the two (nvidia, wifi) worked after the upgrade. Judge for yourself, I can see you're aware of whats going on. Personally, I would not recommend updating. In fact, still don't know why was such an update needed.:confused:
 PS: I've updated, but can't use the new kernel, so I keep using the old one. :)

---

### Post by shane2peru on 2007-02-10
> **mikewhatever said:**
> In my case, neither of the two (nvidia, wifi) worked after the upgrade. Judge for yourself, I can see you're aware of whats going on. Personally, I would not recommend updating. In fact, still don't know why was such an update needed.:confused:
 PS: I've updated, but can't use the new kernel, so I keep using the old one. :)

I updated, and was completely locked out of my system for both kernels.  My grub was overwritten incorrectly.  I edited the menu, and it still wouldn't completely but up?  It came up with some errors.  I had to boot from a LiveCd and re-install grub to get back into my Ubuntu.  Seems to be a very problematic update.

Shane

---

### Post by markwren on 2007-02-10
We all remember at least one serious previous problem concerning kernel updates on Ubuntu in the last year. So why risk it? I'm advising my local novice ubuntu user group to wait a while ...

If you use an Nvidia (or other) 3d card, chances are that you will not have a GUI if the update is problematic. And then you are left struggling at the prompt trying to use a text web browser like "w3m" to view the forums for an answer, and then implement the advice from the prompt too.

See also "the official word" on the lernel update at [http://ubuntuforums.org/showpost.php?p=2133720&postcount=357](http://ubuntuforums.org/showpost.php?p=2133720&postcount=357)

By the way, can anyone explain the dialogue on [https://launchpad.net/soyuz/+bug/83976](https://launchpad.net/soyuz/+bug/83976) ?

Why is this update-fix "demoted to High priority" ... "we have to fix the code before this issues shows up again" ... "this is not a bug in ubuntu, it's a bug in soyuz"?

Aren't Ubuntu in charge of their own quality control of kernel updates? (What is soyuz?) Is a simple one-click "fixed" kernel update (with no issues) only going to become ready just before the next due kernel update?

---

### Post by clickwir on 2007-02-10
***REALLY EASY FIX IF YOU UPGRADED AND HAVE NO GUI***

Some people upgraded without issue. Some with the nvidia drivers had problems.

If you have problems with the upgrade and have an nvidia card, install ENVY but don't run it. Upgrade your kernel and reboot. If you come to just a login screen, login and type envy. Follow it's instructions. It will download the latest version and compile it all for you, even do the X config.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I had the problem of upgrading the kernel and then not having a GUI. I ran the envy script and it fixed the problem really easy.

---

### Post by lighty14 on 2007-02-10
I have a different issue with the update -- the boot process seems to hang in the middle of the progress bar, and the only kernel that does work is one that doesn't support smp. Any idea on what I can do to either a) fix the new kernel or b) fix an old one that has smp support?

---

### Post by Bigadada_saba on 2007-02-10
I updated about 8 hours ago and don't have any problems with it. 
But thet might just be because of the machine im running it on. Mine is a Acer aspire 3620, my wifi has a atheros  chip and that runs fine. No problem so far.

---

### Post by EricJosepi on 2007-02-10
The update seems to have broken my SPCA drivers.  I've tried to remove and then recompile but I get nothing.  Does anyone know of a fix to this?

---

### Post by lojic on 2007-02-10
My wireless card was not recognized after I updated to 2.6.17-11.  I have a Prism 2.5 Wavelan chipset; others have had wireless problems with other hardware, and apparently some have had no problems with their wireless hardware. I'm glad I'm not using NVIDIA drivers!

I've yet to see an acknowledgment of the wireless problem or an ETA of a fix. One solution that was posted did not work for me. It's frustrating to see "problem solved" posts or "all you have to do is recompile your kernel modules" posts when that doesn't seem to be related to the problem you're experiencing.

So, I guess the short answer to your questions is - it depends.

**UPDATE:** I started a thread regarding the wireless problem here:

[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

If anyone is having wireless problems with the 2.6.17-11 kernel, please post your hardware details there.

---

### Post by 2many2count on 2007-02-10
I had the same issue with my Nvidia driver after the kernel updates.  After I ran Envy as you suggested, the release worked fine.  I noticed that the Nvidia driver wasn't actually upgraded, but the Envy driver install corrected the desktop crashing so I'm happy.   *grin*

---

### Post by markwren on 2007-02-11
Thanks quikwir, for the info on the ENVY python script. It looks just the tool I have been looking for! (for me and my little local user group)

I will not be trying it for now though.

My laptop has nvidia 3d and also Netgear wifi with an atheros chipset - available from the kernel restricted-modules, with which there are also problems.

I can probably work around all of this and get it all working with all of the brilliant help on the forums. 

But why should I? I run my personal business from my laptop. It is critical to me. The update is high-risk/low-benefit. I shall be freezing my kernel until I decide whether to upgrade to Ubuntu 7 later this year. And I will advise my local user group to do the same.

Problematic kernel updates are damaging to Ubuntu's reputation! PLEASE UBUNTU ... do more testing of the update process against each kernel update, especially with this kind of common config (NVidia or ATI + restricted-module Wifi) before releasing updates. And provide advice BEFORE the update if needed, rather than giving the impression of letting us users do the testing for you.

Mark

---

### Post by shane2peru on 2007-02-11
> **markwren said:**
> 
But why should I? I run my personal business from my laptop. It is critical to me. The update is high-risk/low-benefit. I shall be freezing my kernel until I decide whether to upgrade to Ubuntu 7 later this year. And I will advise my local user group to do the same.

Problematic kernel updates are damaging to Ubuntu's reputation! PLEASE UBUNTU ... do more testing of the update process against each kernel update, especially with this kind of common config (NVidia or ATI + restricted-module Wifi) before releasing updates. And provide advice BEFORE the update if needed, rather than giving the impression of letting us users do the testing for you.

Mark

I completely agree!!!  I have been using Ubuntu for a while and am not a newbie.  I love Ubuntu, but I was very unhappy with this kernel update!  And thought, why/how did this get into an official repository?  I could see if it were backports or something, but not an official repo.  I wonder how many newbies this turned away?  Need to double check the work Ubuntu.

Shane

---

### Post by Tanker Bob on 2007-02-11
I use the proprietary NVidia drivers under edgy.  I updated the kernel at first with no problems, but more updates showed up yesterday that hosed my system.  I've encountered two solid lockups.  Rebooting refused to enter the GUI.  I have run the Envy script about four times now.  It seems to fix the GUI issue IF you choose to restart the X-server at the end of the install without rebooting.

That said, I'm still having lockup issues that seem related to the network.  This always happens after a period of time using the network--about an hour or so.  I'm running a wired network through a router, not wifi.  Never had this problem before the -11 kernel update.

My overall recommendation would be to wait on updating until the gurus sort all this out.

---

### Post by mikewhatever on 2007-02-11
> My overall recommendation would be to wait on updating until the gurus sort all this out.
I thought the gurus had spoken already:
> Due to an unavoidable ABI change the Ubuntu 6.06 and Ubuntu
6.10 kernel updates have been given a new version number, which
requires you to recompile and reinstall all third party kernel modules
you might have installed. If you use linux-restricted-modules, you
have to update that package as well to get modules which work with the
new kernel version. Unless you manually uninstalled the standard
kernel metapackages (linux-386, linux-powerpc, linux-amd64-generic), a
standard system upgrade will automatically perform this as well.

What more do you expect?

---

### Post by persona_o on 2007-02-11
> **mikewhatever said:**
> I thought the gurus had spoken already:


What more do you expect?

If you're a newbie like me you might not know what that means. So I have to 'recompile' my drivers...? 

When I tried to install linux-restricted-modules it wanted to install a new kernel image even though I had already done the update. So I backed out, not wanting to bork my older kernel, which seems to work fine (I've set it as default in GRUB for now). 

I guess it's just frustrating because usually the updates run smoothly, and there was no warning that this would 'break' the drivers. I'll be more careful from now on and search the forums before I update.

---

### Post by mikewhatever on 2007-02-11
Persona, I am in the same situation, and have no idea what that message means and why do we have to reinstall graphic drivers. What I was trying to say, was, there is going to be no fix.

---

### Post by Tanker Bob on 2007-02-11
I might just be displaying my copious ignorance here, but I think I'm beginning to see the point of the warning.  It seems that if you use any proprietary drivers at all, i.e., anything from other than the main and restricted repositories, including directly from a vendor's website, then you have to recompile and reinstall them all.  Sometimes the reinstall will automatically compile the drivers for the current kernel.  Other times, scripts like Envy will do it for you.

I think that it comes down to the comments in the repository list file at /etc/apt/sources.list.  A variety of comments say something like that the ubuntu team only officially supports those items in the default repositories and that you're on your own if you use anything else.  That would included any and all proprietary drivers like NVidia, VMWare, and assorted wifi cards.  I think that this latest kernel update has brought those comments home to roost for many of us.

In the end, I agree that we've probably heard the last word from the gurus.  My bad on my earlier post.

---

### Post by lojic on 2007-02-12
I can accept the problems with vmware (and other 3rd party modules that may have to be recompiled) because I had to deal with that after every kernel update from SuSe also, but the vast number of other issues that people are dealing with seem unacceptable IMO - messing up partitions, changing grub incorrectly, not automaticall installing the -11 restricted modules when they were installed on -10, enabling the wrong wireless driver modules, etc., etc.

I really like Ubuntu, so I'm committed to working through solutions, but I really can't expect someone new to the OS to be as committed, and why should they be since the OS is a tool to accomplish other things.

---

### Post by Tanker Bob on 2007-02-12
Thinking along the propietary lines, I believe that my network issue was caused by VMWare Workstation network setup not being recompiled for the new kernel.  I did this late yesterday and took a wait-and-see attitude.  After heavy use last night and this morning, my network setup now seems to be stable again.

Note to self:  Keep a list of proprietary programs and driver that need to be reinstalled/recompiled for kernel updates.  (That list is very short!)

---

### Post by shane2peru on 2007-02-12
> **lojic said:**
> I can accept the problems with vmware (and other 3rd party modules that may have to be recompiled) because I had to deal with that after every kernel update from SuSe also, but the vast number of other issues that people are dealing with seem unacceptable IMO - messing up partitions, changing grub incorrectly, not automaticall installing the -11 restricted modules when they were installed on -10, enabling the wrong wireless driver modules, etc., etc.

I really like Ubuntu, so I'm committed to working through solutions, but I really can't expect someone new to the OS to be as committed, and why should they be since the OS is a tool to accomplish other things.

I completely agree!  Does anyone know how to officially contact Ubuntu and file a complaint about this?  Is just stating it on the forums enough?   I would like to file an official complaint with Ubuntu team.  I'm fine with working through the problems, but I was a little agitated when I could not get into my work computer because of the update!  They are not heading for desktop use on a large scale with newbies, if things like that are going to take place.  That is enough to send a newbie running back to Windows, without a second thought.  Especially if they are looking to use it only on their computer.  Hey, it made me think of looking at other distros, and I really like Ubuntu.

Shane

---

### Post by Tanker Bob on 2007-02-12
Shane - Everyone should do what they believe best in that regard.  I'd like to add a few words if I may:

Last Monday, I came to work and could not log in to my Windows XP Pro desktop.  I had an early meeting with a room full of people sitting around waiting until I could get through the busy lines at the help desk.  Turns out that the Microsoft-certified IT folks pushed through some patches over the weekend that corrupted everyone's Windows log in module on their desktops.  Well over a thousand users sat twidling their thumbs waiting for a patch so that they could work.  I was probably one of the few wishing that we had Linux at work because the rest didn't know any better.

Over the last year, regular and security Microsoft patches to WinXP Pro have successively disable parts of my sound system, corrupted my Outlook mail setup, disabled my built-in USB ports, and messed with other third-party prpgrams that they had no business messing with.  I and many others spend huge amounts of time fixing our friends' Windows boxes because the "average user" doesn't have a clue.  One big difference is that the ubuntu team actually cares and therefore has carefully constructed a box (the supported repositories) in which the "average user" should live.  Inexperienced ubuntu users like myself exit that box at their peril.  In order to get the performance I wish, I willingly accept that risk and occasionally pay the consequences--like this weekend.

I understand that folks are upset by the messed-up kernel update as I was, but the countless unacknowledged Microsoft mistakes and ignored security issues are still fresh in my experience.  The ubuntu team at least acknowledged the errors on Friday and fixed them quickly.  As to the necessity of recompiling proprietary drivers--well, that's just part of the landscape inherent in Linux.  There's always a price to be paid for tweeking a system beyond the supported software load.  That's as true in Windows and Mac as it is in Linux.

I don't say all that to give you a hard time or to try to invalidate your experience.  Believe me, I felt your pain accutely this weekend.  I just wanted to put this weekend's experience into perspective relative to the Microsoft Borg approach.  The multi-billion dollar company is, at best, no better than a collective host of talented free agents that make up the ubuntu and Linux open source teams.  I think that's worth a few moments of thought before hitting Send.  IMHO, Microsoft owns most of the desktop world due to inertia, not recent performance.

---

### Post by Mimsy on 2007-02-12
> **Tanker Bob said:**
> One big difference is that the ubuntu team actually cares and therefore has carefully constructed a box (the supported repositories) in which the "average user" should live.  Inexperienced ubuntu users like myself exit that box at their peril.  In order to get the performance I wish, I willingly accept that risk and occasionally pay the consequences--like this weekend.

I would probabably be a lot more wiling to agree with the truth in those sentences if I had known my wireless would be killed by the update *before* I actually installed it... from the safe supported "box" no less. How about a link to where I can find that information, for future updates?

Also, an ignoramus-friendly guide to how to remove the updates and restore my system to what it was before I installed what was described a critically important kernel update, would be nice. I've just got things up and running again, please don't force me to reinstall! :cry: 

/Mimsy

---

### Post by karachuonyo on 2007-02-12
Quoting shane2peru "I completely agree! Does anyone know how to officially contact Ubuntu and file a complaint about this? Is just stating it on the forums enough? I would like to file an official complaint with Ubuntu team." I  cannot remember the exact words but i think it something to the effect that when you install ubuntu you bear the risks and they are not liable. Please remember you signed on the dotted line when installing ubuntu. And can anyone hazard a guess on how long a similar problem would have taken to be acknowledged officially by windows or mac let alone get fixed. Personally i think we need to give a big thanks to the volunteers who keep this great OS running and show appreciation of their work.:confused:

---

### Post by shane2peru on 2007-02-12
> **Tanker Bob said:**
> Shane - 

I don't say all that to give you a hard time or to try to invalidate your experience.  Believe me, I felt your pain accutely this weekend.  I just wanted to put this weekend's experience into perspective relative to the Microsoft Borg approach.  The multi-billion dollar company is, at best, no better than a collective host of talented free agents that make up the ubuntu and Linux open source teams.  I think that's worth a few moments of thought before hitting Send.  IMHO, Microsoft owns most of the desktop world due to inertia, not recent performance.

Tanker Bob,

  Thanks for helping me keep perspective.  I don't any longer deal with Windows on a daily basis, so sometimes I do forget that it is not an error free environment.  My complaint would not be about the third-party programs, I can understand that, and yes, I do remember running into that all too often with Microsoft.  I'm not wanting to start a Ubuntu bashers meeting, but it completely messed up my grub, and several other peoples grubs.  (of which I have helped them get things fixed)  My problem, is that there is not a reason in my mind that a kernel update should botch up someones grub so badly.  Note, it is a different thing if they botched their own menu.lst by switching things around in it (I have done that before and a kernel update did render windows unbootable, but that was my fault for moving it to the top of the list.)  but for Ubuntu not even to boot, and have grub errors, and be looking in the wrong partition, to me there is something bad wrong with that.  I have been through many kernel updates that have gone smoothly.  I have been using Ubuntu since Breezy.  I don't recall the first kernel number or update, but I know I have seen plenty of them that have been done well, and this was not one of them.  And Ubuntu is the **only OS** on my computer!  How can it get it wrong?  There aren't any other choices!  That is what bothers me.  It was looking in my hda4, when it should have been booting out of hda1. 

> **karachuonyo said:**
> Quoting shane2peru "I completely agree! Does anyone know how to officially contact Ubuntu and file a complaint about this? Is just stating it on the forums enough? I would like to file an official complaint with Ubuntu team." I  cannot remember the exact words but i think it something to the effect that when you install ubuntu you bear the risks and they are not liable. Please remember you signed on the dotted line when installing ubuntu. And can anyone hazard a guess on how long a similar problem would have taken to be acknowledged officially by windows or mac let alone get fixed. Personally i think we need to give a big thanks to the volunteers who keep this great OS running and show appreciation of their work.:confused:

I do appreciate Ubuntu, and they have done a great job for the most part.  However this was a real problem.  I'm not one to blow things up bigger than they are, and again, I'm not complaining about third party apps.  I understand they are not liable too, I'm not wanting to make them liable, just make them better!  They have done a wonderful job with all the other kernel updates I have ever experienced.  This one however was not a good one, and I would like to let them know that.  I would also like to ask why it was pushed through and completely rendering computers un-bootable?  I mean mine didn't get past grub, and others either.  And this is not to bash Ubuntu, I have tried FC4,FC5,FC6, Suse, Mandriva, Gentoo, Mepis, Slackware ..... etc, and I always come back to Ubuntu, because **Ubuntu is without a doubt best distro out!**  however this update should have been checked better.

Don't worry I'm not anti-buntu.

Shane

---

### Post by Pollywoggy on 2007-02-12
I have enjoyed Ubuntu on my laptop for about a month, installing it after using Freespire and Linspire on the laptop for about 8 months.  The only thing that Freespire and Linspire do better is setting up the wifi, but Freespire does not yet support WPA and I was able to get WPA to work in Ubuntu, with some tinkering.

I just installed Edgy on a desktop machine that formerly ran Debian Etch.  The problem came when I upgraded to the new kernel image.  Something went wrong that left my system unbootable.  I reinstalled and the same thing happened.  I installed a third time and I tried to make a boot floppy with liloconfig and I saw what the problem was.

When I upgraded Edgy to the new kernel image, initramfs caused my /etc/fstab to be modified to a new format that uses ID's rather than /dev/hdN and this leaves the system unbootable, leaving me in a BusyBox console with an initramfs prompt.  This is something new to me.  I am familiar with "LI  " and "kernel panic" but I had never seen this BusyBox initramfs thing.

I did a lot of Googling and came up with a plan.  I modified my fstab to look like a traditional fstab, no ID numbers.  That saved me.  The only new problem I have is that a custom kernel I installed will not boot with nvidia drivers, but that is not a problem, I can use the stock kernel.

---

