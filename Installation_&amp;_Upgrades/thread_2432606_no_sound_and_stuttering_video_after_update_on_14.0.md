---
title: "no sound and stuttering video after update on 14.04"
date: 2019-12-05
forum: Installation &amp; Upgrades
---

### Post by Dermot Doyle on 2019-12-05
Hi All,
I hope this is the right forum for update problems. Thankfully it's been a few years since I needed any help, but this has has stumped me. I am a great believer in 'if it works, leave it alone', especially since I am not very good with computers. But last night I succumbed to the machine's repeated offer of updates and pressed the button. After restarting I now have a very slow computer, no sound and videos such as youtube which jerk constantly. Everything that involves graphics such as opening anything is laborious and slow.
The sound output shows 'Dummy output' and the additional drivers shows what is in the the attached screenshot. I guess its a graphics card issue, but my guesses could be dangerous.
The computer is a Dell Inspiron on which I loaded 14.04 from new in 2016. The kernal is 3.13.0-170-generic.
Thanks for any help.

---

### Post by Dermot Doyle on 2019-12-05
Further to the problem, the computer went to sleap and then when I woke it up the screen was black. I restarted and the screen came back, but I have lost the Internet. The icon says no network devises available. This update seems to have screwed up my computer completely. Desperate for help now. Thanks.

---

### Post by ajgreeny on 2019-12-05
You should note that 14.04 is now out of support so your problem will be difficult to solve.

You should update the system to a supported version; I recommend 18.04 which is supported until 2023, or 2021 if you use one of the alternative DE versions such as Xubuntu or Lubuntu.

---

### Post by Dermot Doyle on 2019-12-05
I understand 14.04 is no longer supported, I  just hoped my problem wasn't unique and could be fixed. I was hoping I could simply uninstall the updates that have obviously mucked up the computer. Maybe not.
I also understand the advice to go with a newer system, but I have more questions if I go down that route.
Since I can't get on the internet anymore I'll have to find another way to download it.
If I get that far I'll need to connect to the internet to complete the installation. Will that work considering I have already lost the connection?
My experience of Ubuntu has been very mixed and the efforts needed to get a fresh install working properly are daunting for someone like me.
My needs are tiny compared to the power and complexity of modern systems. I search the web, email, watch youtube and netflix and write documents. Is there a more basic version of open source software than Ubuntu and if so is it more reliable?
Would I get a more reliable system if I paid for one?
Answers to any or all of these questions gratefully received.

---

### Post by Autodave on 2019-12-05
Installation on most Dells goes w/o any issues.  Is this a laptop or desktop?  Can you give us the model of this unit so that we can get some specs on it?

Once you get downloaded an installation .iso, you should be good to go from there.  What problems did you run into before when you installed 14.04?

---

### Post by Dermot Doyle on 2019-12-05
Hi, it's a Dell Inspiron laptop 15-3552. As an update I have just rebooted it into the previous kernel and the internet has come back. The graphics and sound still don't work and it's very slow.
Loading ubuntu on all my laptops since around 2007 I have had constant niggles with things disappearing like sound, video, internet, folders etc. but it seemed from all my searches and questions on the forum this was pretty normal and I had to expect to have to work at keeping everything running properly. I only ever had one problem no one could fix, but that was because a computer listed in canonical as compatible with ubuntu wasn't, so hardly ubuntu's fault.
14.04 has been no worse than any other version.
Thanks for the interest.

---

### Post by rsteinmetz70112 on 2019-12-05
> **Dermot Doyle said:**
> I understand 14.04 is no longer supported, I  just hoped my problem wasn't unique and could be fixed. I was hoping I could simply uninstall the updates that have obviously mucked up the computer. Maybe not.
I also understand the advice to go with a newer system, but I have more questions if I go down that route.
Since I can't get on the internet anymore I'll have to find another way to download it.
If I get that far I'll need to connect to the internet to complete the installation. Will that work considering I have already lost the connection?
My experience of Ubuntu has been very mixed and the efforts needed to get a fresh install working properly are daunting for someone like me.
My needs are tiny compared to the power and complexity of modern systems. I search the web, email, watch youtube and netflix and write documents. Is there a more basic version of open source software than Ubuntu and if so is it more reliable?
Would I get a more reliable system if I paid for one?
Answers to any or all of these questions gratefully received.

Your problem almost certainly can be fixed, although working with an out of date version can be more complicated.. 
We would need some more information about your system and what exactly is happening. 
How exactly did you upgrade your computer and from what previous version?
Can you get to a terminal session and login?

You should probably do an upgrade to 16.04 LTS which is still supported and then upgrade to 18.04 LTS. That is the path using the automated release upgrade, *(do-release-upgrade)* although if you are using a i386 version that may be a problem and require a reinstall. Upgrades especially for old system can be troublesome but I recommend them for computers with a lot of special configurations, which it does not seem your have. Other disagree with me on that.

Based on your description of your use it may be easier to simply backup your home directory to another drive and do a new install, especially if you aren't using any non-standard software. You could do that with a DVD or USB drive. You would need to obtain the relevant ISO over the Internet. 

Depending on your hardware you may want to look at lubuntu which is lighter weight than standard Ubuntu, but as noted above has a shorter support cycle. To make a recommendation we would need to know something about your hardware.

Other than Windows, I'm not sure what system you could pay unless you buy Apple hardware. Possibly a Chrome book which uses Internet based apps for the most part. Windows is not in my experience and opinion more reliable and is also in need of constant upgrades. 

You mention you don't have an Internet connection, how do you surf the web. do email or watch youtube or Nexflix?  If you can do that you should be able to  download what you need or upgrade your current system, although depending on the connection speed it may take a long time..

---

### Post by Dermot Doyle on 2019-12-05
Hi, I probably wasn't clear on the internet problem. It only just happened after losing the sound and video. Everything worked before that for a year at least. Also I rebooted to an earlier kernel and the internet has come back. Still no sound or video and very slow.
I'm sure you're right about a later version and have backed up all my stuff on an external hard drive and followed advice on how to download ubuntu18 onto a stick using my wife's mac.
As to the mac I would never buy another one. A nicely made if expensive box needing 2 new motherboards in 6 months.
 From what I have read all of the flavours of ubuntu use the same basic os, just change the desktop environment. If that's so I don't suppose any one would be more reliable than the other.

---

### Post by SeijiSensei on 2019-12-05
Since you have backed everything up, if you are considering installing 18.04 from scratch, let me suggest that you create a separate partition for /home during the installation sequence. Then you can change the operating system version but keep all your personal files and settings intact.  During the disk partition step of installation, choose the "manual" or "something else" option. Allocate some 30 GB to the root filesystem ("/"), then create a separate ext4-formatted partition that spans the remainder of the disk and assign it to /home.

---

### Post by alianco on 2019-12-05
Hi Seijisensei,
Thanks for the advice, but it's too late, I have already installed 18.04. I have to say that one of my problems with Ubuntu is that I barely understood a word of your advice and so it, and maybe a lot of good advice, is simply too difficult for me to understand. That's why a plug and play system that simply works would suit me better. 
The installation seemed to go ok as did the updates. However, I now have 2 problems, one annoying and the other potentially serious.
Whenever I turn on the computer A Dell page comes up saying I seem to be having trouble opening the os and troubleshoots for a few minutes. Then it says the problem is unfixable and only offers the option to turn off. I have to go into the boot menu, select hard drive and then ubuntu will open.
The second problem is that I saved everything on an external hard drive and 18.04 can't read any of it. It says 'unknown file system 'exfat'. My wife's mac can open everything on it.
Anybody any ideas on what to do next.

I have managed to get the computer to read the external hard drive. Now I can't find how to copy and paste the folders off it and the right click doesn't work on the touch pad.

Sorry if this sounds like a stream of consciousness. Ctrl C and V I get that now. I'll just have to search the web for all the things I used to use all the time. This is why I was happy with 14.04. All progress isn't necessarily progress.

I seem to have got everything working at last, but I have 2 final problems. Maybe someone has the answers.
When the computer goes to sleep it demands a password to reopen. I have gone into settings and turned off the screen lock, but it has made no difference. Is there a way to cancel this feature?
Also, If I restart the computer it goes into Dell's diagnostic mode and after some minutes of checking, it says the computer can't be opened and only offers a shut down option. If I go into the boot menu the first option is legacy under which there is the hard drive, ready highlighted and then a CD/DVD option. Below that is the UEFI option under which it just says UBUNTU. If I click on the highlighted 'HARD DRIVE' the computer opens properly, if I click on 'UBUNTU' it goes into Dell's diagnostic mode. From what I have read I should use the UEFI option, but this clearly doesn't work for me. Any suggestions?

---

### Post by Lantizia on 2020-09-06
> **Dermot Doyle said:**
> Hi All,

Hi Dermot,

Sorry for messaging you on this thread (and sorry to anyone else for offtopic necroposting) but I couldn't find any other way of getting in touch (hopefully you get alerts to new posts on this thread).[FONT=arial]
[/FONT]
I stumbled upon [this thread you started 10 years ago]("https://ubuntuforums.org/showthread.php?t=1302973") and it sounds like you once had the exact same Inspiron that I had back then (with Ubuntu 8.04 pre-loaded plus LinDVD and the Fluendo codecs).

A bunch of us (at some point) are hoping to do a bit of a history talk on desktop Linux at a local LUG and I've recently refurbished my Inspiron from 2008.  I was hoping you took the opportunity (probably back in 2008-ish) to create a restore DVD (likely a dual-layer disc) or kept the rather large (likely around 4.9GB) ISO image?

That way I can get the restoration perfect.  Unfortunately the first thing I did with my Inspiron back in 2008 is load Debian on to it and lost all the recovery partitions and ability to create the restore DVD.  After checking extensively with Dell and Canonical, the restore images (at least back in the days of Ubuntu 8.04) were custom to each specific machine and there isn't any available to download anywhere else (at least none with that exact custom config and extra software).

I can me messaged through the Ubuntu Forums private messaging system (although I think you have this disabled on your account for new messages, and maybe replies?!) if you can or are willing to help.

Thanks

---

