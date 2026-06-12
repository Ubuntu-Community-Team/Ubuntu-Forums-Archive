---
title: "A Tale about external HDDs"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by igtech on 2007-06-09
Hello all,

First of all, let me tell you that, althouth I have been working with computers years ago, I am not an IT guy or OS geek, I claim to be just a USER. Thanks.

Yesterday I did next:

  I installed Ubuntu v7 in my Windows XP laptop machine, into an external USB Hard Disk drive, wich I made a swap partition and an ext2 partition first using "PartitioMagic". Everything ran nicely and no probs. OK.

I restart my computer and it appears a GRUB OS selector where I can choose between Ubuntu or Windows. That is great. 

But, of course, I won't live attached to my external HDD forever. So in an innocent action I just deattached the external USB HDD, store it and just reboot my machine to keep working with Windows as usual. For me that is a logical step. I am just a user!

BUT... then I see a GRUB "Error 21" that does not let me do anything. Looks like the OS selector was not in the external drive, but Ubuntu installation touched something deep into my laptop that now I am forced to have this external HDD attached to the computer if I want grant access to the Windows XP boot option. Of course this is a mess, and so annoying.

I just wanted to run my computer as normal, then if I want to experience Ubuntu, just attach the USB HDD and boot from it. For me that makes soooo much sense. Pretty usable! Instead, now I am in a stupid situation.

SO, Only and please, ONLY if you a way to get rid of this easily, something straightforward, not wasting a whole day following LOOONG pages of instructions I barely understand (I am a USER, not a engineer!) to match my Goal  play both OS and enjoy and be happy and blah blah blah, I would appreciate your help. Otherwise, don't bug me with messy, complicated "solutions". Instead, be honest and tell me the best is to get back to be just a Windows user, and wait until install Ubuntu is really "for human beings" and not "for human nerds" as I see it is still at this time.

Sincerely , thanks.

---

### Post by confused57 on 2007-06-09
You need to restore your Window's IPL to you internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
the easiest way is to use a Window's XP install cd(not a recovery cd), press "r", then enter FIXMBR.

You can still use Ubuntu on your external hard drive...if you're not able to boot first to USB, you could use the Super Grub Disk to boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you can boot first to your USB drive, install grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then boot first to your USB drive & if you get a grub boot menu, highlight your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot...x just represents the root partition.

---

### Post by igtech on 2007-06-09
Yes, may work... It sounds to me as I spend my whole morning doing research in many forums about this subject. But I cannot afford spend such that time reading and reading things that are so weird for me.

So I will recover my Windows MBR and destroy the Linux partition and forget about getting inside Ubuntu, as I planned. It is sad, but I have been thinking about that and it's the only thing to do by now.

Why? 

Because I *was* really enthusiastic with Ubuntu project, and as I am a software teacher (of other stuff) I was planning to start some training sessions to show people that are just computer users, not IT guys, that there are alternatives to Windows, and move to free OS and software, etc. 

But I don't want my customers to get stuck into such terrible situations like these, when after installing Ubuntu (even if it's not in an external HDD or USB drive, that would be great!) takes control over the Boot stuff and there is no way back rather than recover MBR and that lingo they barely understand, and won't feel like understand it. Do you follow?

I wish there would SOMETHING, something really EASY, an OS I can just have it onto a external media, and when I plug it into my computer, runs that OS, when not, is like nothing ever happened. From the point of view of the USER, that would be the most normal way to go. No need to get stuck into weird achronyms or complex tasks to perform. Just start your computer and go. Then people is not affraid of forgetting about the OS they always used, and step by step get into new things. You know, people's so resistant to major changes. Only if we can show it is harmless, they could make a try. And I see that even today this is not they way it is, and it is so Sad, because this way things never change...

OK, thank you for reading my complains, if you read it of course! :-P

---

### Post by airtonix on 2007-06-09
the reverse of your scenario is also true if your laptop were ubuntu and you tried to install windows on an exteranl usb hardrive...in fact you'd be further up the creek since weindows bootloader isnt as advanced as the linux ones available.

Boot from a usb external drive with windows.....can this even be done?

My point is that if you had installed the ubuntu OS as per normal onto your laptop, you would end up with a NORMAL setup like NORMAL USER would have.

your method of booting from second drive(not to mention a usb one too), is one that expects the user to know what they are doing.

I have used windows since 3.1 and correct me if i am wrong, but windows never presented me with a feature to boot from and external usb drive.

i know about NU2 boot discs...and his work on the "windows live cd" which actually borders on piracy more than the ludicrous claims tha linux is IP infringement.

---

### Post by confused57 on 2007-06-09
> **igtech said:**
> Yes, may work... It sounds to me as I spend my whole morning doing research in many forums about this subject. But I cannot afford spend such that time reading and reading things that are so weird for me.

So I will recover my Windows MBR and destroy the Linux partition and forget about getting inside Ubuntu, as I planned. It is sad, but I have been thinking about that and it's the only thing to do by now.

Why? 

Because I *was* really enthusiastic with Ubuntu project, and as I am a software teacher (of other stuff) I was planning to start some training sessions to show people that are just computer users, not IT guys, that there are alternatives to Windows, and move to free OS and software, etc. 

But I don't want my customers to get stuck into such terrible situations like these, when after installing Ubuntu (even if it's not in an external HDD or USB drive, that would be great!) takes control over the Boot stuff and there is no way back rather than recover MBR and that lingo they barely understand, and won't feel like understand it. Do you follow?

I wish there would SOMETHING, something really EASY, an OS I can just have it onto a external media, and when I plug it into my computer, runs that OS, when not, is like nothing ever happened. From the point of view of the USER, that would be the most normal way to go. No need to get stuck into weird achronyms or complex tasks to perform. Just start your computer and go. Then people is not affraid of forgetting about the OS they always used, and step by step get into new things. You know, people's so resistant to major changes. Only if we can show it is harmless, they could make a try. And I see that even today this is not they way it is, and it is so Sad, because this way things never change...

OK, thank you for reading my complains, if you read it of course! :-P
You're definitely not the first person to install Ubuntu to an external hard drive...the Ubuntu installer automatically installs grub IPL to (hd0), which is the internal hard drive's mbr...grub overwrites the Window's IPL & they're unable to boot Windows without the external drive connected.   If your bios is capable of booting first to USB, setting your pc up to boot USB before your internal hard drive would have installed grub to the external hard drive mbr(which would have been recognized as hd0 by grub).
Here's an excellent guide to how grub works:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I think I explained as best as I can how you can set up your system to boot Windows without the external hard drive connected and to boot Ubuntu on the external drive when you choose to do so.  Easy, that's a matter of interpretation, effort, & desire to get it working...different than using Windows, yes.

---

### Post by ComputersXP on 2007-06-09
this is the samee reason ive just grabbed 20GB off my Bacup partition on my laptop to install this !!

---

### Post by igtech on 2007-06-10
Thanks a lot to everyone, mostly to "Confused57". Among all the message I read, I catch this excerpt:

***"If your bios is capable of booting first to USB, setting your pc up to boot USB before your internal hard drive would have installed grub to the external hard drive mbr..."***

This is the kind of easy, short sentences me and most users can understand, rather than read link pages of 1000 lines about command lines and that stuff. 
Yes, my laptop allows me to boot first from the external device. So If I had adjusted the Boot sequence, first Removable media, then CD, then Internal drive (for instance) and then started the process of installling Ubuntu, I would be able to detach the USB HDD , then boot my laptop "alone" as usual, am I right?

Because if so, I think this is the key point of the whole process. I can recommend my users to buy an external HDD, plug into their computers, and follow these instructions. So If they don't like Ubuntu at all, just store that new HDD in the shelf and keep working normally. No threads. That is Basic to convince anyone. 

And about being in the reverse situation, like the other post said: I understand, but believe most users work with Windows, not because Windows itself if any better than Ubuntu or Linux, it's because most PROFESSIONAL tools they use are only available for Windows or Mac OS. I have been playing with -for instance- the Vector drawing tool for Ubuntu, and yes may be great, but if I show it to one of my users that works with ¡, let's say Adobe Illustrator, he would say it is a software for kids. Do you understand me?

This Ubuntu or Linux stuff I think is still so inmature and still so restricted to the small world of computer geeks. But if you see an attractive look and feel and advertisement like Ubuntu does, like it is "for human beings", you don't expect to end reading tons of strange achronyms like GRUB, MBR, or end working with balck screens with command lines, etc. As a user you don't have to do anything about that kind of stuff. SO by now for me it is quite much better another OS like Mac OS X, so far.

Again thanks anyone for your patience, and I'd like from this topic that you end understanding my position, that is different from yours. A user that is familiar with computers but don't feel like become a computer engineer. Thanks.

---

### Post by confused57 on 2007-06-10
I don't try to convince other people to use Ubuntu; however, if the topic of computers comes up in casual conversation, then I explain about this "Ubuntu Linux" that I'm using...the typical response is "What's that?", they think it's a program or an alternative web browser.   I explain it's a free, open-source OS, like Window's is an OS, but it's not free & you keep on paying & paying for software programs, antivirus, firewalls, security suites, etc.  If they express an interest, I'm more than willing to assist them; that's the beauty of the live cd, they can try it out on their computers without actually installing...if they want to install Ubuntu after trying the live cd, I'm more than willing to help.

There are countless threads in the forum debating the pros & cons of Ubuntu & Linux, such as this current one:
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

My first experience with Linux of any kind was 18 months ago...I wasn't expecting much, therefore I installed it on an old computer and was pleasantly surprised that basically everything I needed in an OS "just worked".
A couple of months later, I installed a 2nd hard drive & set up a dual boot with Windows:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Installing Ubuntu on an external hard drive is definitely not the easiest way to set up & install Ubuntu, it's almost impossible to install on an external hd which is USB powered...as already discussed, knowing where grub is going to be installed can be an issue for new users.

My advice would be to let "prospective" users test drive the live cd...if they show an interest and have the desire to learn something new and are willing to put in some effort, then suggest they have an excellent resource in this forum, to answer their questions or help set up their system.

I'm not a computer geek, too old for that, and I don't have the desire or inclination to debate the pros & cons of using Linux...it's been a steep learning curve for me and I try to use what I have learned to "pay it forward" to new users who ask for assistance in the forum.  When I have a problem or question, a forum search will usually turn up a solution.

I suppose my point is, through all this babble, is to recommend interested people  try Ubuntu with the Desktop live cd...installing on an external hard drive is probably not the best idea, especially for new users.

---

### Post by eentonig on 2007-06-10
I run the exact same setup as the OP. HD attached and Grub greets me to choose my OS. HD detached and Windows boots without any complaint.

The mistake you made, was that you installed grub on the disk with the Windows install. You should have payed more attention to your partitions and to where to install Grub. But then again, as a new user, there's so much to keep in mind.


To solve issue Windows: Run the Windows install CD in recovery mode and fix your mbr.

To solve the Ubuntu booting afterwards: Boot with live cd and install grub, but pay attention it goes to the correct dir.

---

### Post by tgalati4 on 2007-06-10
igtech makes some valid points.  As the Ubuntu campaign becomes better known, more users will experience it and have their opinions.  These opinions are valid.  We don't have Adobe Photoshop for Linux, we don't have Illustrator, we don't have AutoCAD, we don't have Maya.  Linux has tools that can perform similar functions with similar results, if you know what you are doing.  Audacity under Linux can create an mp3 music file just as well as Final Cut Pro or Logic or Sound Forge.

The Live CD is a great way to take Ubuntu for a test drive.  For a skeptical user that wants to install it, putting in on an external drive would make sense, especially for a laptop where the drives are small to begin with.  The current installation methods do not handle external drives well.  It can be done (as posted by many), but it is difficult and not obvious when things go wrong.  Most people simply reinstall Windows or Ubuntu or both in an attempt to get things working again.  This is not necessary, but if you are sitting with a busted system you don't know that.

Installation of Ubuntu is relatively easy compared to earlier versions of Linux--which is difficult by most user's standards.  Installing Windows is not hard, but it is time consuming.  You need to reboot after installing each set of drivers.  That normally results in 4 or 5 reboots for a typical installation.

There should be a warning or a notice on the Live CD about installing to an external disk.  A simple readme file on the desktop might work.  For those would still want to try Ubuntu, continue to use the Live CD until you have a spare computer to install it natively (that is as dual-boot with Windows on an internal disk drive, or as a Ubuntu-only--wiping the entire drive).

The current crop of Live CD's makes it very easy to try Ubuntu and install it and unfortunately bork a system with an unusual install path.  As more people try it, we will see more instances of this.

I think igtech deserves a full refund from Canonical, Inc.

---

### Post by igtech on 2007-06-10
Let me try to make kind of "summary" of some of the ideas exposed in this subject, in order to come out with somethign that makes sense and would be helpful for the future.

About the most "technical" aspect: eentonig, you said ***"...You should have payed more attention to your partitions and to where to install Grub..."***. Sorry, but I tried to be as careful with it as I could. I carefully made the partitions first with Windows and PartitionMagic. I went though the "Manual" selection of partition, because I got several HDDs and did not want to ruin anything. But believe, NEVER seen a single workd about MBR or GRUB. This is something I have discovered afterwards, when all this happened and was forced to investigate.

About "spreading the word", that is something Ubuntu encourages to do. I agree. I know that you can play Live CD. I use to order Ubuntu CDs to give to my users to engourage them. But play Live CD is slow and just to show. Once it is shown, people stores that Live CDs in the shelf and forget about the whole thing.

The concept of Live CD is great, because people insert it, play with it, then shuts down and it is like nothing ever happened. 

Would be even greater that this concept could be translated to install Ubuntu at all. I mean, If people could easily know how to install the whole thing in a removable device (USB Hard Disk, USB drive, SD cards in the near future, etc), and run Ubuntu or the OS of their choice with no complications, people will really start getting there instead of playing one day in their lives with it and that's all. Ubuntu could end being just a freak for 1 day show. And I don't think this is the spirit of it. 

So, finally, a nice, user-level well made tutorial (like video tutorial or similar) on how to install Ubuntu in a removable device, and use it or not without problems, would be from my point of view a huge step to the goal of standarize Ubuntu or Linux over the mass. Next step would be to develop really professional software for it.

Thanks.

---

