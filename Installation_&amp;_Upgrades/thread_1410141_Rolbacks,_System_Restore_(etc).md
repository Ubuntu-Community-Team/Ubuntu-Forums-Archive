---
title: "Rolbacks, System Restore (etc)"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by mirmos192 on 2010-02-18
I'm a (relatively) new user of Ubuntu. My main (work) machine OS is Windows Vista. So I'm just playing around, really. But, quite honestly, there are very few things preventing a complete switchover to Linux-Ubuntu. Getting my Skype DualPhone to work, for example (no drivers for Linux - and I do want to use Skype - which I can, but not with the usb DualPhone), and then the relatively trivial one of needing to get to grips with OpenOffice - because Wine and even Crossover Linux don't quite do what is needed to get MS Office 2000 working on all cylinders - with its updates, patches and the app that lets it open Office 2008 etc files. There is also the complication of setting the firewall up properly with the relatively unfriendly Gnome Firewall Configuration Utility (ie you need to know what you are doing, unlike with, say Comodo, or Zonealarm in Windows). But really, with a little bit of application, some sweat and tears, I guess I could solve these issues, or find a suitable workaround. However, what really bothers me - especially, as I do like to fiddle around a bit - which is why I'm using the (so far) fabulous Lucid (10.04) still in Alpha - is that there is no idiot-proof way of rolling back, akin to Windows' System Restore, if I do something which breaks Ubuntu. It only takes one item in Lucid's updates, or from something else I install, breaking my system, for it to be necessary to start all over again from the beginning, having to reinstall all my apps, sources, passwords, etc, etc. Which is fine if I'm just playing around. But what a palaver if I'm using my Linux machine for work!

I may be wrong - but I do not think there is a nice, simple, idiot-proof facility for doing a complete backup and restore in Ubuntu. Or is there? If there isn't, shouldn't there be? Or, is there a shared belief/ethos that all Ubuntu users should always know what they are doing, or otherwise they shouldn't be using Ubuntu?

I've posted this in Installation and Upgrades, rather than Absolute Beginners - because, in my experience, it's during installation and upgrades that 'breakages' tend to occur

---

### Post by Herman on 2010-02-19
> I'm a (relatively) new user of Ubuntu. My main (work) machine OS is Windows Vista. So I'm just playing around, really. But, quite honestly, there are very few things preventing a complete switchover to Linux-Ubuntu:D I'm glad you think so. I agree, everyone should switch to Ubuntu and the world will be a better place!
> However, what really bothers me - especially, as I do like to fiddle around a bit - which is why I'm using the (so far) fabulous Lucid (10.04) still in Alpha - is that there is no idiot-proof way of rolling back, akin to Windows' System Restore, if I do something which breaks Ubuntu. It only takes one item in Lucid's updates, or from something else I install, breaking my system, for it to be necessary to start all over again from the beginning, having to reinstall all my apps, sources, passwords, etc, etc. Which is fine if I'm just playing around. But what a palaver if I'm using my Linux machine for work!
Of course you do realize Lucid is still under development and not recommended for work yet until after it is officially released, don't you? :D
> Or, is there a shared belief/ethos that all Ubuntu users should always know what they are doing, or otherwise they shouldn't be using Ubuntu?No but since the operating system is not under a restrictive EULA and we are allowed to install as many instances of it as we like for free, so we can have one operating system for work which we would be careful with, and another installation for play and for experiments that we don't care if we destroy a few times by accident. The rest of the time the second installation can serve as a fall-back installation for the first one, and as a utilty system. It doesn't matter if your other Ubuntu is an older version, the same, or a newer version than the one you mainly use. So I use Karmic Koala for work and Lucid for fun. 

There are a myriad of other different possible solutions to your problem that are all better than chocking up the operating system with more copies of itself that most of us will never need. :D

One solution I used to use was to make a copy of the operating system with a program called 'Partimage', which can be installed in Ubuntu and also comes in many Linux Live  Utility CDs, such as GParted LiveCD and Parted Magic LiveCD.
The files that Partimage makes can be stored in some other media like DVD disks instead of laying around clogging up your hard disk drive for no good reason.

An older and simpler way is to use the dd command to clone your entire partition or even an entire hard disk to another hard disk and restore it again by reversing the dd command.
Nowadays if you do that you need to be aware of the need to change the UUID number or keep one hard disk unplugged the operating system might be confused about which partitions to boot. 

Another way is to learn how to make a proper backup and re-install, and how to restore your settings again quickly. There are programs like Simple Backup and Simple Restore that can help you.
Really though, if we know what we're doing (after a little practice breaking and re-installing our systems),  the entire operating system can probably be re-installed and restored pretty quickly just by copying the right files to a backup disk without the need for any fancy software at all.

> and then the relatively trivial one of needing to get to grips with OpenOffice - because Wine and even Crossover Linux don't quite do what is needed to get MS Office 2000 working on all cylinders - with its updates, patches and the app that lets it open Office 2008 etc filesI use Ubuntu for work too and most of the other machines are Windows machines.
The ability of Ubuntu to be able to read and write any kind of file type is one of the big advantages of using Ubuntu. I've had Windows users come to me to open files for them made in other versions of Windows and save them as something their version can open. 
 I don't use Wine or Crossover Linux, I just open whatever files I want with Open Office .org, do what I need to do and and when I'm finished if I want others to be able to read the file I just click 'save as' and save it as a Windows file type.
I'm not much of a Windows user so I didn't pay any attention to what version of MS Office is making the files some of the others can't open.  :D

> There is also the complication of setting the firewall up properly with the relatively unfriendly Gnome Firewall Configuration Utility (ie you need to know what you are doing, unlike with, say Comodo, or Zonealarm in Windows).
I don't what you need a firewall for. I don't know much about firewalls. I don't open up any ports to intruders so I don't think I need a firewall. What services do you have running?  :D

---

### Post by mirmos192 on 2010-02-19
Many thanks for a considered and helpful response, Herman. Some useful ideas.

And - yes, I know what an Alpha release is for, and even a Beta!

It's long been clear to me, by the way, that I no longer really need MS Office - even in Windows, given the excellence of OpenOffice - and its ability to open any version of the former without hassle, and to save to Office's formats. But it's laziness. F'rinstance, I have to determine what minor formatting issue is going wrong with Presentation when I open one of my own PPT files with it (has to do with the formatting of a third level indent, where the solution is not immediately obvious... but, doubtless, can be found with a bit of experimentation), etc, etc.

But I still think 'System Restore' is a nice idea for 'lazy' people.  I always delete earlier copies, so it doesn't choke up my system. If the fantastic people who have worked so hard to develop Ubuntu into the truly superb OS it is becoming really would like it to challenge the proprietary OSs in a marketing sense (ie achieve at least a substantial minority of the market - say 10% or more) then they will, eventually have to take account of the fact that most of us are somewhat lazy and ignorant in anything which doesn't immediately affect our own work, hobbies or social life. Most particularly with their computers. Most don't even know how to use Windows' System Restore, for example - or even know it is there. But at least you can tell them - 'do this' and (often) hey, presto - their problem with a corrupt wotsit (or even virus) is solved. Bill Gates and his mates understood their markets very well; they needed to, because they wanted to make money out of them. And they succeeded. I'd like to see Ubuntu really challenge the Gateses and Jobses of this world, is all.

Blimey - where's Hughenden, mate?

---

### Post by Herman on 2010-02-19
Yes, well after thinking about it a little more maybe you're right, if a fast way can be found to do that without using too much disk space.  I would imagine there should be some way to use the already existing /var/log/dpkg file along with some apt-get and dpkg commands to achieve that somehow but I'm only guessing. I have no idea how simple or complicated that might be. It's a good suggestion.
You should get ready to suggest it when the developers are looking for ideas to include in the next Ubuntu release, usually somewhere in the programming and development section of the forums.  :D

---

### Post by Laptop_Max on 2010-05-10
Sounds like a very good idea to me.  I wonder if it's been brought up at brainstorm.ubuntu.com?  I think I'll head over there and check it out...

---

