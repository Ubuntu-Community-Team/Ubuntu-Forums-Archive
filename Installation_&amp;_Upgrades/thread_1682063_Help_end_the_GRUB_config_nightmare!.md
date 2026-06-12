---
title: "Help end the GRUB config nightmare!"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by danboid on 2011-02-05
I am surprised its 2011 yet Ubuntu still lacks an easy way to resolve the all too common fubar'd GRUB scenario, as most commonly experienced when someone (re)installs Windows or installs an additional Linux OS. I hate to think how many people have given up on Linux as a result of not having a simple way to restore or fix GRUB.

Lets make sure we get this fixed for 11.10 - see my proposed solution here:



[[IMG]http://brainstorm.ubuntu.com/idea/27119/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/27119/)

---

### Post by Quackers on 2011-02-05
I'm not sure what your problem is exactly.
Of course re-installing Windows will wreck grub - it's over-writing the mbr, where grub lives.
Installing another Linux system deosn't wreck grub, unless you allow it to.
If you have a specific problem, please ask a question, don't rant.

---

### Post by demosthene1 on 2011-02-05
I agree with danboid. Just look around this forum and see the amount of confusion grub brings to new users. And we were all new to linux at one time. Yes, grub is the funkiest part to deal with and the most basic aspect of an installation.

---

### Post by Quackers on 2011-02-05
And among the easiest to diagnose (thanks to the boot script) and to fix, once you know what's wrong. If you look around at these threads regarding grub errors you will often see that a user error was to blame - ie grub got installed to the usb flash drive, instead of the hard drive; grub was installed to a partition instead of to the mbr of the drive; etc etc etc

---

### Post by presence1960 on 2011-02-05
New users really need to read and study prior to installing a new OS, especially one they are unfamiliar with. There is a wealth of documentation and how-to guides both in this community and on the web.

My philosophy is you should read and gain at least a working understanding of what you are about to do. 

There is no way to fix it simply, the problem lies with windows when you install windows after linux or reinstall an existing windows installation. It is windows, unlike GRUB, which gives you no option at all for the boot loader. With GRUB you can choose where to put GRUB, with windows  the MBR of the first disk to boot in BIOS is reset to use the windows bootloader. I would suggest that this is a windows issue, as such take it up with Bill Gates and Microsoft.

Reinstalling GRUB 2 is a simple process: 2 commands from terminal off the Live CD/USB. How simple can it get? I'd prefer to run two commands rather than an exhausting series of mouse clicks and/or keyboard shortcuts.

---

### Post by Rubi1200 on 2011-02-05
> **presence1960 said:**
> New users really need to read and study prior to installing a new OS, especially one they are unfamiliar with. There is a wealth of documentation and how-to guides both in this community and on the web.

My philosophy is you should read and gain at least a working understanding of what you are about to do. 

There is no way to fix it simply, the problem lies with windows when you install windows after linux or reinstall an existing windows installation. It is windows, unlike GRUB, which gives you no option at all for the boot loader. With GRUB you can choose where to put GRUB, with windows  the MBR of the first disk to boot in BIOS is reset to use the windows bootloader. I would suggest that this is a windows issue, as such take it up with Bill Gates and Microsoft.

Reinstalling GRUB 2 is a simple process: 2 commands from terminal off the Live CD/USB. How simple can it get? I'd prefer to run two commands rather than an exhausting series of mouse clicks and/or keyboard shortcuts.
+1 to everything said here!

@demosthene1
> Just look around this forum and see the amount of confusion grub brings to new users. 

I say, just look around the forums at the number of users we have helped solve these issues quickly and efficiently. 

With everything new there is a learning curve and most of those I have helped personally were not only grateful, but also commented on how they had learned an important lesson they could apply again (should the situation arise of course).

---

### Post by Harbard on 2011-02-05
> **Rubi1200 said:**
> +1 to everything said here!

@demosthene1


I say, just look around the forums at the number of users we have helped solve these issues quickly and efficiently. 

With everything new there is a learning curve and most of those I have helped personally were not only grateful, but also commented on how they had learned an important lesson they could apply again (should the situation arise of course).


I think the issue is they shouldn't have to ask for help to fix these problems.  I'm not exactly a newbie, yet I am having problems (see my other thread.)  Hard to say I screwed it up when all I did was hit install.  I wasn't even given an option to change anything having to do with grub.

The sad fact is, we have to deal with these issues regardless of whose "fault" it is. Some enterprising hacker should write some sort of troubleshooting script to fix things when they go wrong.  Please don't suggest that I do it....if we depended on my skills civilization would collapse.

---

### Post by kansasnoob on 2011-02-05
> **Harbard said:**
> I think the issue is they shouldn't have to ask for help to fix these problems.  I'm not exactly a newbie, yet I am having problems (see my other thread.)  Hard to say I screwed it up when all I did was hit install.  **[COLOR="Red"]I wasn't even given an option to change anything having to do with grub.[/COLOR]**

The sad fact is, we have to deal with these issues regardless of whose "fault" it is. Some enterprising hacker should write some sort of troubleshooting script to fix things when they go wrong.  Please don't suggest that I do it....if we depended on my skills civilization would collapse.

Check out what I just posted here (along with the first link):

[http://ubuntuforums.org/showpost.php?p=10430779&postcount=3](http://ubuntuforums.org/showpost.php?p=10430779&postcount=3)

---

### Post by danboid on 2011-02-05
I'm sorry but I've never been able to understand the RTFM crowd like Quackers- people like yourself would prob be better off using Gentoo or LFS as your comments are more inline with such communities. I posted my suggestion with the aim of trying to improve Ubuntu which is aimed at less technical and inexperienced users of Linux.

If you had actually followed my link you would realise I know how to fix these problems but I also know that this process can be made easier, should be made easier and Ubuntu will be better off as a result - just look at the amount of GRUB questions in this forum. The average person wants to use their computer, not spend hours reading man pages! Ubuntu is trying to be "Linux for human beings" (ie user friendly) remember?

Here is the current guide for people who find themselves in such a situation:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

OK, so its basically 5 or 6 commands or actions but theres much room for error and theres no-way my parents would be willing to follow that guide, even if they are quite happy running and using Ubuntu otherwise. Anything more than very basic terminal usage (Ie copy/pasting an unmodified command or two) really does scare non-techies senseless. If I could say "Boot off the CD, choose 'Fix Grub' and then pick your HD, say Yes" or whatever they would be quite happy to do that.

If anyone has a better idea for reducing the number of GRUB problems or generally making GRUB easier to live with then please speak up- otherwise please take your 'RTFMisms' elsewhere., they're not helping anyone.

---

### Post by presence1960 on 2011-02-05
> **danboid said:**
> I'm sorry but I've never been able to understand the RTFM crowd like Quackers- people like yourself would prob be better off using Gentoo or LFS as your comments are more inline with such communities. I posted my suggestion with the aim of trying to improve Ubuntu which is aimed at less technical and inexperienced users of Linux.

If you had actually followed my link you would realise I know how to fix these problems but I also know that this process can be made easier, should be made easier and Ubuntu will be better off as a result - just look at the amount of GRUB questions in this forum. The average person wants to use their computer, not spend hours reading man pages! Ubuntu is trying to be "Linux for human beings" (ie user friendly) remember?

Here is the current guide for people who find themselves in such a situation:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

OK, so its basically 5 or 6 commands or actions but theres much room for error and theres no-way my parents would be willing to follow that guide, even if they are quite happy running and using Ubuntu otherwise. Anything more than very basic terminal usage (Ie copy/pasting an unmodified command or two) really does scare non-techies senseless. If I could say "Boot off the CD, choose 'Fix Grub' and then pick your HD, say Yes" or whatever they would be quite happy to do that.

If anyone has a better idea for reducing the number of GRUB problems or generally making GRUB easier to live with then please speak up- otherwise please take your 'RTFMisms' elsewhere., they're not helping anyone.

You have the right to your own opinion. But you do not have the right to tell another community member to go elsewhere, or where their skill set is more suited to be utilized. If one "claims" the right to have their own opinion they should also learn to allow others the same right. Quackers does a lot of good work in this forum. I endorse his opinion, as I also allow you to have yours even though I do not agree with it. To see why I do not agree with it go to your suggestion page, I posted a comment there.

[Here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") is a better guide in my opinion.

---

