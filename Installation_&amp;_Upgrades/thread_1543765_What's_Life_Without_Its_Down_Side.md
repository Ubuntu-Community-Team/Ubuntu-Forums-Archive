---
title: "What's Life Without Its Down Side?"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-08-01
See, I just gave everyone something to complain about, which is, my postings don't always indicate a specific topic in the title, so how is anyone to find out what it is that the post is about?  I guess you have to read it.  So that is a type of down side.

Here are a few down sides of my own:

Installer cannot connect via wireless, meaning to install Ubuntu, you have to get wired up first.  Not so good for laptoppers and the like.

Installer usurps any found /home to use with a new install, even if set there by a different distro or verison.  That can be very conflictive when it comes to one /home serving two oManyr more installs of Linux.

The partitioner used by the installer doens't have much to say.  No flag states, such as what is primary or boot.  You can also only designate a single partition for one purpose, such as root (/).  That can also cause allocations inconsistent with user intent and purpose.

The Installer ignores the directive for any partition to be ignored. It does what the partitioner writer decided to do in all cases anyway.

The installer insists on givng only repartitioning choices if you elect to use one of the automated install methods.  Tha twould wipe out any present partitioning you have.  I've read elsewhere that some think this only applies within a given partition, but the separate partitions will all be removed according to details read elsewhere. What if you have data stored on any of them?  What if they are Windows partitions, where Windows uses as a reference a given drive letter, and that apparent drive is not there anymore?
.  
The whole matter of user settings is way off track.  That apparently entails specific settings under user accounts which are under the /home folder.  Those accounts also have all the data and other particulars of the users, and under the installer's manual partitioning option, you can have /home and all its contents left alone by signalling no reformat of the partition that has /home on it.  Sounds good for reinstalling a failed system without losing user accounts or data, but if the failure involves a configuration setting under /home someplace, then that missettingcaries forward into the new reiknstall as well.  There should be a division between configuration settings and all else that relates to user accounts, so that corrective action to the cnfigratons can take place as well during a reinstall, or even preceding the need for a reinstall.

I am struggling with various techniques that together, act more favorably towards what appears technically to be a reinstall.  It has gotten rather involved, and I won;t go into the details of all that at this point.  It is still a work in progress.

Aside from the down sides of the installer, there are other areas worth noting.  For instance, the appearance of the desktop with 10.04 LTS is rather flawed.  You can deal with the appearance after the instqll is complete, but two options related to the pointer are rather disappointing.  The first is that you can pick the mouse style and coler to some extent under appearance, but the size scale for the mouse is ineffedctive, and with laptops that have a touchpad that acts as a mouse, you would be concerned about how it behaves, yet the settings for the pointer and touchpad are located in different areas.

There appears to be a lot of variance from one release of Ubuntu to the next, most of it unaccounted for.  Take for example the matter of screen resolution.  At one point is was quite reasonably listed as what it was, Screen Resolution, under System/Preferences.  But then magically it was moved to a setting under Display, and is currently found under Monitor.  All this moving around has helped us how?  And remember, new releases are expected at roughly 6 month intervals.  And as to the default appearance of 10.04 LTS, why black, and why move the control buttons for a window from the upper right side of the frame to the upper left, and change their color ahd shape so notably?  It's been the other way for so long that you might consider it a standard of sorts.

But to move on, I have kicked about the forums structure a bit.  But here is another down aide in that regard.  You specify which named release to wri te a thread undre,but is there anything about the range of versions that the ticket or thread is applicable to?  I that problems in one version may or many not carry over to another version, maybe even another release. And if marked SOLVED, does that hold true for each of the above, and does it carry back to the earlief versions or is it just resolved in the ones going forward?  It makes a big difference sometimes.

Here is my own example, and just took place, but with VirtualBox, which is riding on Ubuntu.  I'm using several USB devices, all available under VirtualBox to pass on to a client.  They each show up under Devices/USB when checked from the client side, but quite often the one for the USB printer is grayed out, meaning I cannot dlect ot use it.  Now this is vearsion 3.2 of VirtualBox, but sI search their forums for postings on problems of this sort, and find some, with suggestions on how to try and resolve it.  But these posts are all related to version 3.0, not 3.2.  So maybe the fixes won't apply, because it is a different problem.  The main suggestion was make sure of the print server settings.  They name s setting that is not displayed under Windows' print server. Maybe they meant on the host side.  Yes, there is a print server under Ubuntu, but again, no setting of that name.  What version of Ubuntu was the responder using>  Look again at the post, and it does not say,  In facsponder does not identify what the host was,at all, or which version of Windows was the client, or which of the two servers he was talking about.  Talk about non-information, but so typical of most postings it seems.

I make changes, and restart the client, but no help. I repeat the process but also stoo and restart VirtualBox, still no help,  I had it working fine a few days ago, and it still works with the host, but it grayed out for the client.  Maybe that is the problem, that it is not really shared but allocated to one or the other.  If the host has it, then not the client,that sort of thing.  So I throw in another step.  If I make a change, I try restarting the PC to see if it registersw.  But it does not help.  So I shut down the PC for the night.

Next day, it powers up and works fine.  So what happened?  My wife uses it for the day, cuts it off, and the day following the printer access is grayed out again.  I check the settings and they are the same, something else is involved.  And which party is more at fault in this Ubuntu or VirtualBox,  My thinking is coming around to the possibility that when it comes to sharing, Ubuntu means either youhave it or I have it.  If I have it, then it's not on the table for VirtualBox to offer to you.  So I try taking out of use with Ubuntu, but no help.  And restarts don't make a difference.

My sister-in-law's PC and her husband's got fried by a nearby lighting strike.  Igt only got my KVM switch, so I was real lucky.  She brought me her PC to check out, possibly to see if I could recover her data from the hard drive.  First I disconnected the 20/24 connector and shortd the green lead pint to an adjaced black lead pin.  This is the method the notherboad signals the power supply to turn on.  The green power light came on, and with the short in place, I checked power on one of the drive leads, and the +5 and +12 volts were both present.  Good, the power supply was sound, but the motherboard then was damaged as the alternative.

I pulled the short between the leads to kill the power, and moved on to pulling the leads to the drives and getting the drive cage out.  I note in passing that the power light was still on, but as I remembered at that point, this is characteristic of a really decent power supply, because it helps the equipment being powered to right through power glitches.

AT some point the the two matters came together in my head.  Maybey the restarts were not doing the job adeqately, because the power supply never has time to really quit, it just reduces power temporarily.  Maybe that was not enough.  Maybe you had to shut down the PC long enough for the pawer to completely drain away, a process that might take 30 seconds or more.  Don't forget that an early design target was to ensure that the PC had enoujgh power to keep it working while data was stored to drives and programs could end cleanly, or it could move into hibernaton.

So maybe a restart was not enough.  Mayhbe it requjred a full shutdown and a short interval for a complete power discharge, then a new power up.
So I tried it, and it worked.  I think that put the problem into Ubuntgu's camp in two significant ways:

First, apparently Ubuntu was not truly sharing the printer between itself and VirtualBox.  I mean it does not really see the client past VirtalBox, so its dealings are just withe the VM.  Now I suppose a problem could arise because the client only has occasional need for the printer, yet possibly VirtualBox has locked up access to the printer on behalf of the client, in which case it is not doing its part properly either,

I think the other indicaton is that Ubuntu is not really observing changes in the printer server, or possibly the printer itself, because it is in a running status and mmy only observe configuration setting on initial startup, and that might only happen when Ubuntu starts up.

VirtualBox might even signal a problem in this area itself, but in a more obvious way.  You set up or select a client, you can at that point make configuration settkings.  But once the client is running, you can no longer go through Settings to make changes, until the client is stopped.  There is effort to allow CDs or DVDs,to be changes out, and change USB devce status through the Devices menu option, but this merely capitalizes on the clients' native ability to work with such changes on an ongoing basis.

Trying to make some changes in Ubuntu while dealing wiht this, I found another down side.  Some of the Choice screens that came up let you pick something, but you only had one button to push.  It was labeled "Cancel". So you suppose that if you push that buttion, your change will register?  What else is there to do?  If you push the "X", that usually counts as a cancellation too.  Go to the bottom task bar, right click, and you get a "Close" choice. You might get the feeling that they were not serious when they said they were offering some kind fo choice in some areas.

I just figured I would lay it all out. You can take it any way you want   If you want to suggest writing a few bug reports, I've tried that route and feel I need to decline.  Another one of my down things.  Like I am sure many of regard this posting, or even me personally, as being on your down link list

Well, take heart.  we are coming into the election season and the down links are due to rise, at least in number and persistence.  I already know some of whom I am not voting for, and I will likely learn the rest in short order.  The trick is then,who is left?.

---

