---
title: "What you should know before installing and upgrading Ubuntu."
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by kio_http on 2010-05-16
[CENTER][COLOR=DarkRed][SIZE=5][FONT=Comic Sans MS]_I am writing this article because I have noticed an increase in issues occurring from blindly installing and upgrading._

Note: Current LTS Release is Ubuntu 10.04 and Latest Stable release is Ubuntu 10.10

[/FONT][/SIZE][/COLOR][LEFT][COLOR=DarkRed][COLOR=Black][SIZE=4]Installing Ubuntu or Upgrading it to a newer release can be an exiting task that one anticipates. [COLOR=Red]
*But hey not so fast!*[/COLOR][/SIZE][/COLOR][/COLOR][I][COLOR=DarkRed][COLOR=Black][SIZE=4]Read this article to prevent possible errors.[SIZE=3]

[/SIZE][/SIZE][/COLOR][/COLOR][/I]**[SIZE=3]Why these issues occur?[/SIZE]**

[LIST]
[*]**[SIZE=3][Garbage in Garbage Out]("http://en.wikipedia.org/wiki/Garbage_In,_Garbage_Out") (GIGO)[/SIZE]**
[/LIST]
[SIZE=3]This is the classic error. The user is unaware and believes he /  she is doing it right and unknowingly makes a mistake. This is why I  always advise to read instructions the first time you do something.
[/SIZE]
[LIST]
[*]**[SIZE=3]Wrong expectations[/SIZE]**
[/LIST]
[SIZE=3]Every OS varies from the others in one way or another, you  should not expect Ubuntu to behave like Windows or Mac OS X or any other  Operating system.
[/SIZE]
[LIST]
[*]**[SIZE=3]Misconception[/SIZE]**
[/LIST]
[SIZE=3]Sometimes users attempt to use their knowledge of another  system with Ubuntu. This results in them believing that Ubuntu lacks a  feature. In fact this is not the case; Ubuntu has the feature but you  don't know how to access it. This is where [this forum]("http://ubuntuforums.org") comes in. There  are plenty of users willing to share their knowledge with you. In a  matter of no time you will know your way around. For a complete article about forum features and related information [see here]("http://ubuntuforums.org/showthread.php?t=1006656").[/SIZE]

*[SIZE=3]Lets move on to what you must know.[/SIZE]*
[U][SIZE=4][B]Known problems in Ubuntu
[/B][/SIZE][/U][SIZE=3]Ubuntu is made by people and like every OS it has its problems. Therefore is is advisable to read the release notes. Some variants(Explained later)  have published release-notes. For the current release lucid, see
[Ubuntu notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes")
[Kubuntu notes]("https://wiki.kubuntu.org/LucidLynx/Final/Kubuntu")
[/SIZE] 
_[SIZE=4]**Installation**[/SIZE]_
[B][SIZE=3]
What will happen to my current Operating System(s)?

[/SIZE][/B][SIZE=3]Ubuntu's installer is able to auto-detect other Operating systems and provide you with a list-like choice on which OS you want to boot when you start your computer.

**How can I set it up to work as mentioned above?**[/SIZE]

[SIZE=3]Confused about how you can have multiple OS's at once? The answer is partitioning. 

Basically partitioning involves dividing your disk drive into multiple "pieces" allocating smaller storage spaces. E.g. Splitting a 160GB disk into two 80GB parts.
For more details about partitioning, see [this page]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics").

[/SIZE][SIZE=3][B]What you must do.

[/B][/SIZE][SIZE=3]Ubuntu's installer provides you with everything you need for partitioning.

What options are present?
[/SIZE]
[LIST]
[*]**[SIZE=3]Use entire disk[/SIZE]**
[/LIST]
[SIZE=3]The target disk will be entirely erased. This means the other Operating Systems and all saved data on that disk will perish. ***If you want to dual boot this is not the option you seek!*** [/SIZE]

[LIST]
[*]**[SIZE=3]Resize partition and use free space[/SIZE]**
[/LIST]
[SIZE=3]The indicated partition will be shrunk; it will lose available free space. There is a slider allowing you to chose by how much you want to shrink. The free space created will be used for a new partition on which Ubuntu will install itself. Note: This procedure takes quite a while to complete. ***T****his is the recommended option for users with little experience and would like to just get things done.  ***[/SIZE]
**[COLOR=DarkRed]NOTE:[/COLOR]** In releases prior to 10.04 LTS, there was a known issue resulting in failure in this process. If you use such a release consider using other software, like Windows of Apple disk-utilty to shrink for you.

[LIST]
[*]**[SIZE=3]Manual[/SIZE]**
[/LIST]
[SIZE=3]On the next step, you will be taken to an advanced utility allowing you to manually create and manipulate as many partitions as you want. Eventually once you are familiar with Ubuntu, you will prefer this option over the rest. ***This option is aimed at advanced users who are already familiar with partitioning***[/SIZE]

[SIZE=3][B]Partitioning sounds scary, I'm not ready for it!

[/B][/SIZE][SIZE=3]*Any particular situation preventing you from partitioning / shrinking your other OS partition?*

*No problem if you have Windows.*
Use [the WUBI installer]("http://wubi-installer.org/"), this will install Ubuntu within a virtual disk file on a Windows accessible disk.

**[COLOR=Red]Note:[/COLOR]** Using this method, installed Ubuntu will be unable to access files on your Windows disk.
[/SIZE]                              [SIZE=3]Wubi filesystem is more vulnerable to hard-reboots (turning off the  power) and power outages than a normal filesystem, so try to avoid  unplugging the power. An Ubuntu installation to a dedicated partition  provides a file-system that is more robust and can better tolerate such  events.                      [/SIZE]
[B][SIZE=3]
Can I get some of my Windows applications working?
[/SIZE][/B][SIZE=3]Most free applications like [firefox]("http://www.mozilla-europe.org/en/firefox/") are available for both Windows and Ubuntu. However if you have a Windows only application you can install [WINE]("http://www.winehq.org/")[/SIZE] [SIZE=3]and see if the app then works under Ubuntu. There is a possibility it may not[/SIZE], [SIZE=3]in that case using [virtualbox]("http://www.virtualbox.org/")[/SIZE], [SIZE=3]you can have a complete installation of Windows running at the same time as Ubuntu. For more details on getting Windows running in Ubuntu with VirtualBox, see my tutorial [here]("http://ubuntuforums.org/showthread.php?t=1322436").[/SIZE]
[B][SIZE=3]
[/SIZE][/B][B][SIZE=3]Which Ubuntu iso image should I download.

[/SIZE][/B][SIZE=3]The Ubuntu download pages offer you a variety of downloads. You should use the right one.

[B][SIZE=4][COLOR=DarkGreen]_Architectures_[/COLOR][/SIZE]
AMD64[/B] [/SIZE]
[SIZE=3]This image is for users with 64-bit CPU's. Note it is for both Intel and AMD 64-bit CPUs. E.g of compatible CPU's are AMD athlon 64, phenom, INTEL PENTIUM D, CORE 2 series, CORE i3, i5,i7.[/SIZE]
[SIZE=3][B]I386
[/B][/SIZE][SIZE=3]This image will work on almost any INTEL or AMD computer. It is intended for those CPU's that are not 64-bit capable.

[/SIZE][SIZE=3]**[SIZE=4][COLOR=DarkGreen]_Variants_[/COLOR][/SIZE]**[/SIZE]
[SIZE=3][B]Ubuntu
[/B][/SIZE][SIZE=3]Ubuntu is currently the most wildly used variant of the Ubuntu project. It features the [GNOME desktop environment]("http://www.gnome.org/").[/SIZE]
[SIZE=3]The right place for getting Ubuntu is [here]("http://ubuntu.org").
[/SIZE][SIZE=3][B]Kubuntu
[/B][/SIZE][SIZE=3]Kubuntu features the [KDE desktop environment]("http://kde.org/").[/SIZE][SIZE=3] The right place for getting it is [here]("http://www.kubuntu.org/").[/SIZE]
[SIZE=3]**Xubuntu**[/SIZE]
[SIZE=3]Xubuntu uses the low resource but pleasant and simple desktop environment [XFCE]("http://www.xfce.org/")[/SIZE]. [SIZE=3]The right place for getting it is [here]("http://xubuntu.com/").[/SIZE]
[SIZE=3]**Lubuntu**[/SIZE]
[SIZE=3]Lubuntu features an extremely lightweight desktop environment, [LXDE]("http://lxde.org/").[/SIZE] [SIZE=3]It is intended to be used on old hardware that cannot cope with advanced desktop environments. [/SIZE][SIZE=3]The right place for getting it is [here]("http://lubuntu.net/").[/SIZE]
[SIZE=3]**Edubuntu**[/SIZE]
[SIZE=3]Edubuntu is Ubuntu + educational applications, it is ideal for installing on school computers etc. [/SIZE][SIZE=3]The right place for getting it is [here]("http://edubuntu.org/").[/SIZE]
[SIZE=3][B]
What are the netbook editions?
[/B][/SIZE][SIZE=3]Ubuntu and Kubuntu have netbook edition options. Basically they are the same as the normal editions but are designed for smaller screens; the menu integrates with the desktop.
Note: It is not necessary that you must use the netbook variant on a netbook, the normal edition will work as well.

[/SIZE][SIZE=3]**[SIZE=4][COLOR=DarkGreen]_Desktop or Alternate?_[/COLOR][/SIZE]**[/SIZE][SIZE=3][B]
Desktop
[/B][/SIZE][SIZE=3]The desktop version is both a live-cd and installer. It provides a fully graphical installer and is recommended for new users.[/SIZE]
[SIZE=3][B]Alternate
[/B][/SIZE][SIZE=3]This version has only an installer, you can't try Ubuntu before installing. It is aimed at advanced users who want to configure Ubuntu bit by bit to their taste.[/SIZE]

[SIZE=3][B]This sounds great, can I have multiple varriants at the same time?
[/B][/SIZE][SIZE=3]Yes, all variants can be run together in a way you select which you want at logon.[/SIZE][SIZE=3] Once you have installed one variant, you can install the rest via packagemanager. [/SIZE]
[SIZE=3][B][SIZE=4][COLOR=DarkGreen][U]
Current release or LTS?
[/U][/COLOR][/SIZE][/B][/SIZE][SIZE=3]**LTS**[/SIZE]
[SIZE=3]LTS is for users that need a system that is meant to be kept running for years. Don't expect many new features etc to come 6 months after the LTS is released. You will still recieve security updates however.[/SIZE]

[SIZE=3]**Current**[/SIZE]
[SIZE=3]The current release is for users who like new features coming every now and then. Users of the current version usually upgrade Ubuntu version every six-months.[/SIZE]

[U][SIZE=4][B]Upgrades
[/B][/SIZE][/U][[SIZE=3]Not all upgrades go well![/SIZE]]("http://ubuntuforums.org/showthread.php?t=1465548") [SIZE=3]For this reason I advise you to always backup the essential before an upgrade. The less you tweak advanced setting of Ubuntu, the more likely your upgrade will succeed[/SIZE].

[SIZE=3][This issue]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724") currently faces many upgrading users, please note:
/dev/sda is the first hard disk
/dev/sdb is the second hard disk
and so forth.

Chose the hard disk your PC uses to boot to avoid getting an unusable system. You can find the appropriate device in system BIOS.

[COLOR=Navy]Thanks for reading
I shall continue to edit and improve this thread in future
[/COLOR] [/SIZE] 
[/LEFT]
[/CENTER]

---

### Post by kio_http on 2010-05-16
Post removed

---

### Post by MartyBuntu on 2010-05-16
I thought that was a pretty good guide. Thanks for that.

:)

---

### Post by kio_http on 2010-05-16
> **MartyBuntu said:**
> I thought that was a pretty good guide. Thanks for that.

:)

Your welcome. I will do anything to help beginners to Ubuntu.

---

### Post by kansasnoob on 2010-05-16
I said yes, I like it :)

Suggestions:

1) Include links to Release Notes.

2) Regarding Wubi this is important if you live in an area where power outages are common:

> Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

That's from:

[http://wubi-installer.org/faq.php#requirements](http://wubi-installer.org/faq.php#requirements)

3) This bug has been very prominent:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

A lot of that is due to NOT understanding the drive and partition designations in Linux.

But definitely this deserves a sticky!

Oh and kudos on the effort! Planning is the key to a successful Ubuntu experience!

---

### Post by kio_http on 2010-05-16
> **kansasnoob said:**
> I said yes, I like it :)


But definitely this deserves a sticky!

Oh and kudos on the effort! Planning is the key to a successful Ubuntu experience!

Thanks for the feedback, I consider it valuable and updated the post.

I'm glad that you believe my efforts deserve a sticky.

---

### Post by kio_http on 2010-05-16
erased

---

### Post by Old_Grey_Wolf on 2010-05-16
The reasons I voted No.

I have found it best for beginners to resize Windows after defragging, and using Windows to shrink the Windows partition. There are a couple of things that can go wrong when using the Linux partition editor. Then install Ubuntu using the largest unallocated space option. The method you described works most of the time; however, I prefer not to give a Linux beginner a bad experience when it can be avoided.

Also, an LTS is not "extremely stable" in my experience. It is supported longer so you don't have to upgrade/reinstall as often.

---

### Post by kansasnoob on 2010-05-16
Well, sticky or not, I'd hate to see this removed!

I'd like to know the reasoning for this not being a sticky?

I think it's quite informative.

Maybe consider a bit of rephrasing and presenting this as a HowTo, like:

How to prepare for installing or upgrading Ubuntu.

I think you did a great job and you're obviously open to sensible edits. What more could we ask for?

HowTo's go here:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

It can take weeks for approval :)

For what it's worth I appreciate your dedication.

---

### Post by Iowan on 2010-05-16
> **kio_http said:**
> I state this because

[LIST]
[*]The moment an edited erased post was removed, a no vote came.
[*]The moment  I requested it to be stickied via report system a no vote came.
[/LIST]I removed the edited erased post - I have NOT voted in your poll.

---

### Post by kansasnoob on 2010-05-16
> I have found it best for beginners to resize Windows after defragging, and using Windows to shrink the Windows partition. There are a couple of things that can go wrong when using the Linux partition editor. Then install Ubuntu using the largest unallocated space option. The method you described works most of the time; however, I prefer not to give a Linux beginner a bad experience when it can be avoided.

This is true but the OP has already shown the willingness to edit :)

---

### Post by Old_Grey_Wolf on 2010-05-16
> **kansasnoob said:**
> This is true but the OP has already shown the willingness to edit :)

Not when I originally voted. I waited 2 or 3 hours before I explained why I voted that way.

---

### Post by KiwiNZ on 2010-05-16
> **Old_Gray_Wolf said:**
> The reasons I voted No.

I have found it best for beginners to resize Windows after defragging, and using Windows to shrink the Windows partition. There are a couple of things that can go wrong when using the Linux partition editor. Then install Ubuntu using the largest unallocated space option. The method you described works most of the time; however, I prefer not to give a Linux beginner a bad experience when it can be avoided.

Also, an LTS is not "extremely stable" in my experience. It is supported longer so you don't have to upgrade/reinstall as often.

Agreed , LTS does not equal " extremely stable" , that is misleading.

---

### Post by kio_http on 2010-05-16
> **Iowan said:**
> I removed the edited erased post - I have NOT voted in your poll.

Sorry, my mistake I appologise.

> **kansasnoob said:**
> This is true but the OP has already shown the  willingness to edit :)

Edited concerning graywolf's issue.

---

### Post by kio_http on 2010-05-16
> **KiwiNZ said:**
> Agreed , LTS does not equal " extremely stable" , that is misleading.
Edited.

Your feedbacks are extremely appreciated.

Actually LTS is developed to be more stable, however it does not always turn out to be so.
In the long run with the sub releases like 8.0.1, .2 etc it gets very stable.

---

### Post by kio_http on 2010-05-16
> **Old_Gray_Wolf said:**
> Not when I originally voted. I waited 2 or 3 hours before I explained why I voted that way.

Can't edit when offline!:KS

---

### Post by Old_Grey_Wolf on 2010-05-16
> **kio_http said:**
> Can't edit when offline!:KS

Hehe, I was offline as well. That is why it took so long to explain my vote. I had other things to do like change the oil in my car. 

I haven't looked at the partition editor in 10.04 in order to actually know if it handles Windows partitions properly every time. I probably won't as I tend to use Virtualization these days.

---

### Post by kio_http on 2010-05-16
> **Old_Gray_Wolf said:**
> Hehe, I was offline as well. That is why it took so long to explain my vote. I had other things to do like change the oil in my car. 

I haven't looked at the partition editor in 10.04 in order to actually know if it handles Windows partitions properly every time. I probably won't as I tend to use Virtualization these days.

In the past around 3 in 10 PC's failed the shrink, for 10.04 all worked:guitar:

---

### Post by kio_http on 2010-05-18
Updated 18/05/10


[LIST]
[*]Fixed typos
[*]Added details
[/LIST]

---

### Post by kio_http on 2010-07-30
Update - Added Information 30/07/10

---

### Post by kio_http on 2010-10-15
Guide updated and improved to be relevant with Ubuntu 10.10 systems.
15/10/2010

---

### Post by ronparent on 2010-10-15
Should definitely be posted as a sticky.

---

### Post by Slim Odds on 2010-10-15
> **Old_Gray_Wolf said:**
> ...

Also, an LTS is not "extremely stable" in my experience. It is supported longer so you don't have to upgrade/reinstall as often.

+12 for this one.

I think it's another myth that must be busted.

There is no difference in stability between and LTS and the rest. It's all about the length of support.

Keep spreading the word!!

---

### Post by kio_http on 2010-10-15
> **Slim Odds said:**
> +12 for this one.

I think it's another myth that must be busted.

There is no difference in stability between and LTS and the rest. It's all about the length of support.

Keep spreading the word!!

This ammendment has already been made to the article.

---

