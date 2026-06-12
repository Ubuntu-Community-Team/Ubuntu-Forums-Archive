---
title: "Installing Lubuntu with no boot menu"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by louintoronto on 2015-12-22
Hello!
I really want (almost need) to install Lubuntu onto my laptop, but there's no boot menu and I can't enable it. To make things more complicated, the PC is in a language I don't understand, and changing settings (like partitioning) is very difficult.
I've tried unetbootin, but I get an error message.
Is there a way for me to install without a boot menu?
Thanks!

---

### Post by Vladlenin5000 on 2015-12-22
You need to provide a lot more info before someone can start thinking about it...
What laptop?
What Lubuntu release/version?
What boot menu are you talking about?
What has the "PC language" to do with anything? And what language? Where? AFAIK, the only place in a PC that pertains to the PC itself and has language is the BIOS/UEFI. That is usually in English by default. And it has nothing to do with partitioning... Everything else is OS/software so, are you referring to the factory installed OS? If so, the question is, again, what it has to do with the Lubuntu installation?
Are you intending to do a dual boot? If so, what is the other OS?

And the list goes on... When posting please avoid such vague assertions and help others helping you by providing useful information.

---

### Post by louintoronto on 2015-12-23
**What laptop?** Acer Aspire E 11
**What Lubuntu release/version? **15.10 64x
**What boot menu are you talking about? **The one that usually appears when I hit F2 or F12 on the opening splash screen. It does not exist on this device, apparently.
**What has the "PC language" to do with anything? And what language?  Where? AFAIK, the only place in a PC that pertains to the PC itself and  has language is the BIOS/UEFI. That is usually in English by default.  And it has nothing to do with partitioning... Everything else is  OS/software so, are you referring to the factory installed OS? If so,  the question is, again, what it has to do with the Lubuntu installation? **I am referring to the OS language. Many of the instructions I've found online involve me changing settings by the Windows control panel, and that has been very difficult without access to the language.
**Are you intending to do a dual boot? If so, what is the other OS? **I would be fine with either a dual boot or replacing the OS - whatever's easier. Windows 8.1 64x.

---

### Post by yancek on 2015-12-23
Do you have windows 8.1 already installed?  Was it pre-installed?  If so, it will be using UEFI.  Have you read the information at the link below on dual-booting UEFI with windows and the different Ubuntu derivatives?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'm still not sure what the problem is with language.  Did you buy this computer from someone with windows already installed with some language you don't understand used?

---

### Post by yancek on 2015-12-23
Do you have windows 8.1 already installed?  Was it pre-installed?  If  so, it will be using UEFI.  Have you read the information at the link  below on dual-booting UEFI with windows and the different Ubuntu  derivatives?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I'm  still not sure what the problem is with language.  Did you buy this  computer from someone with windows already installed with some language  you don't understand used?

---

### Post by Vladlenin5000 on 2015-12-23
ACER Aspire E11 is UEFI indeed like all others with factory installed Windows 8/8.1/10. This alone results in different challenges and requires a slightly different installation method compared to the traditional BIOS. The document linked in the previous post should answer extensively to what the users should be aware before attempting to do a dual boot or installing Ubuntu as a standalone OS. BTW, installing a standalone Ubuntu is much easier then building a dual boot scenario but doing the latter isn't complicated either as long as you understand the specificities of the machine.

I think I also understand where you're coming from with the language issue. Indeed, for a dual boot scenario you're strongly recommended to make space - shrink partitions - _from Windows_ and using _Windows native tools_ then let it reboot twice in order to run chkdsk on the 'new' drive. As a matter of fact, one should only proceed with the second OS installation after assuring the factory installed Windows is happy with the drive's rearrangement. Doing so in a foreign language can be daunting for sure but hey, use Google Translate if you must. _Needless to say, if you intend to install Ubuntu as a standalone nothing of that matters._ Ubuntu installer can easily use the whole drive and remove Windows entirely. So, it's up to you to decide what to do. We can help you either way. However, before you make a decision _please consider the following reasons to keep Windows_:

1. Most manufacturers nowadays release BIOS/UEFI updates as Windows executable files (*.exe) that can be run (in Windows) like any other program. Without Windows an high level of technical expertise if often required in order to perform such BIOS/UEFI upgrades or might not be possibler at all. 
2. You may have one or more softwares that you can't go without for which there are no good alternatives in Linux.
3. In Warranty claims: Customer service, for obvious reasons, often require the original OS to be installed in order to perform diagnostics and they are entitled to refuse service if the customers don't follow the rules/procedures.

So, at this point, you have to decide what to do. Again, we can help you either way.

---

### Post by louintoronto on 2015-12-23
Thanks both of you for your help. I am a little conflicted about what to do here, but I think I'd like to proceed with erasing Windows completely. I don't have a warranty, and I can't think of any software that I need windows for (everything I do is on a browser). I'm not sure what the advantages of BIOS/UEFI update would be, but I don't think they're as essential as a computer with a language I can understand. 
I will proceed with the instructions in yancek's post and return if I have questions.

---

### Post by Vladlenin5000 on 2015-12-23
BIOS/UEFI upgrades are intended to correct issues and/or extend compatibility with new CPUs and/or memory types - common in motherboards for desktops, rare in notebooks - and other situations. That said I concur with your reasoning. However, I suggest you check at ACER's for BIOS/UEFI updates and apply the latest release before proceeding, while you still have Windows (search by serial number or _exact_ model number).

Then, when you're ready, I would like to summon @oldfred - our beloved guru for all things UEFI - because over the years he has been compiling lots of brand/model specific procedures and I remember reading something about ACERs requiring a "supervisor password" or something at BIOS/UEFI in order to "trust" Ubuntu installation. I don't use ACERs therefore my knowledge is very limited. If I'm correct this preliminary procedure is required both for dual booting or standalone.

---

