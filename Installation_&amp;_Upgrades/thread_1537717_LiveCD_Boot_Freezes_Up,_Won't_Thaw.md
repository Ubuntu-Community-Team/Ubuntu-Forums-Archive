---
title: "LiveCD Boot Freezes Up, Won't Thaw"
date: 2010-07-24
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-07-24
As reported on several occasions, a temporary lockup of the screen updates with Ubuntu can normally be cleared by noving the mouse or pressing a shift key.  However, these methods don't work with a VirtualBox client, but you can toggle whether the client is in full screen or not, and that normally works.  It happens frequently though, and my wife is so irritated at this conduct that she wants an immediate fix.

I agree it is aggrevating, and is pronounced on all four of the the PCs I have here, plus others that I've worked on.  Haven't seen other complaints though, which is rather odd.

Anyway, the things that interest my wife the most are embroidery, working on some family albums (pictures), and daily email.  The best photo client software I've dealt with on my own is Irfanview, which is free, but not available to Linux.  However, it will work with wine.  But wine now takes either Ubuntu 9.10 or 10.04 LTS as the host, so I have to consider upgrading my wife's PC, which is still at 9.04.

That was my project for this morning.  It's still not done, and the way things are going, may not be done for some time yet.  I got 9.04 to update, but somehow it went faster than expected and apparently went all the way to 10.04 LTS on its own.  Haven't had that happen before.  And I did tell it not to write the boot record, planing on working aroudn that manually, but then it just showed "GRUB" and nothing happened.  I went back into Setup and changed the boot drive order back to the old way, and it booted into 10.04,  but would freeze in a few keystrokes or mouse movements.  Really odd.

So back to the LiveCD approach, sometimes with the 9.04, 9.10, or 10.04 CD, but always having the same problem. The Freeze, where the mouse will not work and neither will the keyboard.  I've tried to be very deliberate and slow in my actions, but invariably, I will do something and the keyboard and mouse both quit working.  I try waiting to see if it is a timing issue, but it just remains that way until I power off and back on.

What do I do?  Well, I add folders to /media and then mount the drives one by one.  No problem here.  But to view the contents of a drive might cause it to happen, or to make any changes to a drive's contents, like create a folder or try to copy and paste, and it all just stops.

What really gets to me is that the only way that I have found to respond to this is to cut power, wait until power dies, then bring it back on again.  It is not just that this is totally aggrevating, but to kill power as a means to get beyond a bad situation is bad policy.  You have no assurance that the last act initiated had time to complete before the power had to be cut.  That's never a good idea.

What I am doing now is going back a few versions with Ubuntu and see if I get the same results there.  I don't recall the 8.xx versions having a problem like this.  If they don't then they can at least help me get back what my wife in folders she set up.  Every attempt to just do that much with 9.xx or 10.04 LTS has failed today.

I've been impressed with Linux's resilience and ability to boot if things are not exactly as they should be, but that certainly does not include the troublesome grub boot process.  With Grub 2 I now get 'grub rescue>' on the screen, but what are you suppose to do from there?  There isn't even an associated help command, and none of the commands I thought might be of some value were even recognized.  At least with Legacy Grub you had a menu.lst file to work with and tailor in an effort to get it right.

Just thought it was something work commenting on while I wait for 8.10 to download.

---

### Post by oldefoxx on 2010-07-24
Just for your benefit, the same efforts that I have spent many hours on today with the three later releases of Ubuntu went down PERFECTLY on the very first attempt when I switched to 8.10 instead.  Almost 50 k worth of tiles had to be copied between mediums, an enterprise that took less than 15 minutes.

Believe me, I knew when I had it that 8.10 was about as good as it could get, but eventually I felt that I alo had to move on to 9.04,   then 9.10, which was and is about on a par with Vista when it comes to being a failure, and while I see some good in 10.04 LTS, it is not near as stable as 8.10 is.

Of course that is just my opinion you understand, but it is based on hands-on experience.  Somewhere between 8.10 and 9.04,  the Ubuntu development community made some bad decisions and we are stuck with the screwed up shambles that passes for Ubuntu now.  I guess they will never admit it, and will try to pretend that it never happened, but you take 8.10 and compare it to what came later, and you will likely understand what I mean.

You know what I would do if I were in charge?  I would have the whole community revert to 8,10, and start building up from that point again.  What's the point of staying on a road going to nowhere like this?  But again, just my humble opinion.

---

### Post by oldefoxx on 2010-07-24
I figured the stake drivers would have begun swining at this thread by now.  You know, the ones that eiher start off with 'Thats never happened to me", or "Did you try this" approach, or "You need to use fewer words".

Hey, I just call them the way I see them.  Focus on what I am reporting, not the manner in which I am reporting it.

For instance, many of you probably weren't aware that you can use the Terminal mode and sudo to work beyond the scope of the LiveCD, to actually make change or check settings that already exist in the existing installs  You can access the partitions in one of two ways:  The easy way is to click on them where they show up under Places or Computer.  Your password gives you access.  The other way is to add folders under eiher /media or /mnt that are appropriately named, then use the "mount -t <type> </dev/name> <mpunt point>.  The mount point, incidently, is that /media or /mnt folder that you just added.

You can also do an "apt-get install grub", which takes you back to the legacy grub method of dealing with grub booting.  This is where you work with /boot/grub/menu.lst using an editor like nano.  If you do an "apt-get install grub-pc", you are asking for Grub2 to replace the legacy grub method.  Unfortunately, you are replacing it only in the LiveCD's way of doing things, and it does not convert /boot/grub/menu.lst to /boot/grub.cfg or vice versa.  And there is no tool provided that will do this for you.  If you know enough to do it manually, that is find.  Otherwise, hat is on the partitions will remain on the partitions.

Legacy grub does provide a limited interface for checking and modifying the boot process.  You type grub, and you are in the interface.  A find command there can help you identify where something like /boot/grub/stage2 is, or where /boot/grub.cfg or /boot/grub/menu.lst is.  You can actually have both together in one partition, but which one gets used then depends on how the boot process was set up to start with.  That you don't really know, but using the root (hdx) followed by the setup (hdx) command is suppose to change this.  But there are a number of things you need to know at tis point that you do not have immediate access to.

One is the flag state of each partition.  Which one(s) are considered boot, which one is marked to be active, and which ones are primary or logical.  The last is not particularly important, but the combination of boot and active tells you a lot about how a system was marked to be used.

Unfortunately, while a tool like gparted can provide some of the informtion, it does not provide all of it.  You can see which are marked as boot, their size, location, and even change their names, but that is not what is really needed.

What is really needed is a nifty way to either determine what the MBR (Master Boot Record) points at now, or to change it to what you want it to be instead.  Apparently the MBR can be screwed up in other ways, which can cause havoc in trying to set up a good boot process, so you need to be able to cut it down to just a very basic boot sequence.  I've yet to find a decent tool in Linux for all this, and most people are just instructed to get a Windows XP Install disk, start the install, when asked if either install new or repair, to pick repair, and when given the choice to choose console, pick console.  At this point you can execute a limited range of XP commands.   The command you want to then use is FIXMBR, and you can use it with or without a drive parameter.  You may need to use it both ways, just to be sure.  

So what's all this got to do with the reported problem, of some Ubuntu
LiveCDs just hanging at some point?  There are actually several tie-ins.

First, to show that I've experience in working more deeply from a LiveCD than many even considered.  So I am not a fool in this regard.

Second, to pass on some grain of wisdom that I have acquired in this regard, and this alone may benefit others.

Third, to show that LiveCD freeze-ups is not typical, that I have worked from the same LiveCDs befpre quite successfully,, but on other PCs, not the Gateway model my wife was working with.

But while the Freeze-Ups encountered yesterday might be specific to some uniqueness in the hardware, the actual fact is that all the PCs at hand, which includes the Gateway, two from HP, and a laptop from Toshiba, plus an Asis desktop that my sister-in-law has that I set up, they all show the same problem with the installed versions of Ubuntu, that the screen would cease updating on its own and require some user activity at the keyboard or mouse to resm, and that this problem was much more pronounced if conveyed by VirtualBox to the client.

---

### Post by oldefoxx on 2010-07-28
I've had my hands busy and my mind occupied, and it has shed some light on this matter.

My wife's complaints have been on the increase lately, but it just sounded like the familiar problems.  Then she told me two days ago that her PC would not boot, and wanted me to stick her old HP back in its place.  I first tried getting past the failure to boot problem, but whatever the problem was, it just seemed to be getting worse.  So I decided to pull it aside and do what she asked.  But her old PC was unbelievably slow with the new Ubuntu and VirtualBox mix, and I decided to just give her the Asus PC in its place.  The Asus is working very well at this point.

Her old  HP went into the garage, and the Gateway went by my chair to check out further. But no matter what software I wenf with, the LiveCD and installs all just flunked out with all manner of video, keyboard, and mouse issues.  Something was terribly wrong here, but what?  I finally wiped both hard drives and used fixmbr on a WinXP disk, and started over.  Windows XP
went on the first partition with no problems, so I decided to go with Ubuntu 10.04 on the second.  Big mistake, the problems came raging back.  The same again with 9.04 and 9.10.  This is despite repeated attempts.  So in near desperation I went back to 8.10 again.  And aside from s small glitch in not properly resizing the monitor screen to 1024x768, it installed with no problems,

Now as I've said on several occasions, the latest releases of Ubuntu and VirtualBox have struggled against hangups with either the mouse or the keyboard, or both.  This is now true of just Ubuntu alone, but only on the Gateway GM5661E.  The tendency for a keyboard lockup with a VirtualBox client at the forefront has presisted since 9.04, and maybe that is somehow related to the other as well,

It beats me.  I even tried the gparted.iso, and once passed the menu selection section, it would consistently report a number of segmentation errors and finally just stop.  There were a number of other fail or errors reported throughout the initiation process, not a large number, or particularly significant, but having an accumulation effect.

I've never encountered a problem quite like this before.  The hardware works in some cases but not in others.  Where it does not work properly it is consistent, although intermittent.  But go back to 8.10, and other than an occasional glitch in screen updates, it seems to do well,  Then jump over to Gparted.iso, and something is very clearly wrong at that point.  Run a memory test, and it can run forever without errors.

I guess the only thing I can conclude at this point is that a significant coding change took place in either Ubuntu or the kernel at that point, but heck, that is exactly what new releases are all about.  If someone were to try and track this down, they might be forced to conclude that the Gateway PC suffered from an almost insignificant defect in the way it interpreted one instruction given it, but that instruction had not really been employed before these last few releases came out.  Yet that seems to be contradicted in part by the ability to repartition the hard drive and install Windows XP without difficulty on the first partition.

I could persist in either just using some early version of Windows, or checking out how well other versions of Linux fair under these circumstances.  Or I could assume the PC is just shot and replace some or all of it when I get the chance.  We will have to see what the future brings.

Of course I might have some bright and enterprising developer contact me and offer to buy the PC in question off my hands because he wants to explore the matter himself and devise his own solutions are inclined to seize such an opportunity.  Not that I would blame them either way in this regard.

But here is a thought.  What if it is not a defect, but a characteristic, sort of a signature, and by understanding the signature a bit more, you could write software that was specific to certain PCs and would not run on others?  That might prove useful, and avoid any obvious method of employment.  Perhaps something to think on.

---

### Post by oldefoxx on 2010-08-08
Looks like this thread and a few others can be related to what seems to be a common set of things not working as they should.  Fact is, there are bug reports that go at these problems, but we are three released ahead and the problems remain.  No fixes in sight or due, and this is all about something that we got stuck with and probably don't really need.

Anyway, the point is if the get around to fixing some of the bugs, or pulling back on aspects that are not really helping us, the problem then
goes away on its own.  If they don't learn to live with it.  It seems like we are stuck with thingws like this no matter if there are bugs or not.

---

