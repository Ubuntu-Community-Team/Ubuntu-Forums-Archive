---
title: "All I can say is...."
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2008-10-30
The upgrade from 8.04 to 8.10 went horribly.  I'm ashamed.  I've been using this for some time now and I can only say how upset I am at how badly this past update has been.

I started with a solid long standing well adjusted 8.04 install.  After the upgrade I stood at a character based log in screen with some incredibly cryptic errors preceeding it.  This essentially killed my ability to work.  And I do work with my computer.  It is important that it keep working.  Updates should never cause me to not be able to function.  After the update I was essentially non-functional, totally.

As time went by and I read some forums I found out how poorly this whole thing went.  I can't believe the people that beta tested this didn't manage to get Canonical to get more issues resolved, serious issues, show stopper issues...

It is no wonder that the Canonical people were summarily closing down threads in the brainstorm site.  They must have been so overwhelmed with this that they felt they couldn't cope.

As of now I am somewhat successful at getting things back up and running and much of that was done with guess work.  Here are some of my issues and how I resolved them.  

When I first did the install I was prompted many times to "keep" (or not) certain settings in various config files.  In all cases I said to keep them because I didn't realize what those files were nor how these changes would affect them and so I chose the default of "keep" and not change.  This turned out to be bad.

What I found was that the menu for the kernel hadn't been updated to include the kernel release provided by this distribution.  As a consequence when I attempted to load the GUI it came up but the 3d accelerated graphics didn't work.  

Prior to this during the install received some error message about hal lib or something and it asked me to submit a bug report, which I did.  The responses I got on it from the bug system from the individuals responding have to be a joke.  They were totally unhelpful and even showed a great deal of arrogance.  They passed the buck almost attacking me, when I really just said.  "I don't know, here's the info it compiled for you."

Prior to my first desktop, during the boot I was watching the progress bar with my fingers crossed hoping things would just go well and I would not have to deal with any issues.  What was going through my mind was the hopes that Canonical had gotten it right this time since last time was almost as bad this one made me feel.

While I watched the progress bar I was jarred when I realized that it has stopped at a certain point and it was taking a very very long time.  I waited long enough and the restarted the computer.  This time it wanted to run a disk check.  I let it do that and it completed successfully, apparently.  After that the next boot took me to the same progress bar stopped at the same point.  I waited a while and hit alt+ctl+del and then it proceeded on and actually I got to the desktop.  It was stuck at the point where it was to activate the networking.

Later I found out why.

When I finally was presented with my first desktop I noted that my avant window navigator was missing and I noticed that the 3d effects were off and that compiz was not functioning. I then noted that there was a prompt for me regarding new hardware that I could activate.  I did this, rebooted, and got to the same lock point where it wouldn't proceed past the networking activation.

I alt+ctl+del again and went past it, but only to end up at a prompt where I was to log in to a character based session.  I decided to reboot, go into bios, and turn off networking.

At this next reboot the computer no longer stopped for a long time at the network activation.  It just continued.  But, alas it continued to a character based prompt from which I was supposed to log in.

I have two network ports on the motherboard so I decided to switch them and try again.  Into bios, turn on the network adapters, and reboot.  Lock up again.

I then decided to start in failsafe mode.  No luck at all.

I then did a uname -r and noticed I was using the old kernel still so I looked into the /boot/grub/menu.lst file to see which kernels were available.  Only the older ones.  My answering during the install to keep these settings kept the menu.lst from being updated to give me the choice to use the new kernel.  There were so many prompts during the install and the average person would never even begin to undestand what the questions were about that it was considered the safe bet to keep the existing files.  In this case that is apparently not the best choice.

I then went into the /boot folder at the command prompt and looked to see if the new kernel was actually there.  It was.

At this point I then went into the /ect/X11 folder and looked at the xorg.conf files to see if they were correct.  They appeared to be correct.  I then went to change the driver settings from "nvidia" to "nv" and rebooted.  Same issue.  I then reexamined the file and found a second entry and changed those as well.  I have two 8800gts cards and noticed that there was a section for each.

I rebooted and went to the same prompt.  No GUI, just a character based log in with some cryptic messages preceding it.

I got the bright idea at this point to run the nvidia installer.  When I did it told me there was a mismatch and this was not good.  I could attempt to continue anyway but it might cause problems.  I chose to continue, to reboot, and nothing...same problem.


At this point I looked at the two different nvidia installers and ran the latest that I'd downloaded the night before I did the update.  That one generated the same errors and indicated that there was no appropriate matching kernel info upon which to compile the new kernel module.

I tried again with both the 173 version and the 177 version.

I then went into the other room and attempted to do the update on my laptop which is based on an nvidia chipset.  This update went pretty well with only one error and when I rebooted I was a the desktop but the compiz function didn't work.  I saw that there were available hardware drivers so I chose those.  Those then allowed me to activate compiz again.  The problem with that install is that when I move the mouse pointer over the titlebar or the buttons they become distorted.  Not a good thing and they didn't do it before I upgraded.

During the day I was playing with the laptop and I was visiting the forums and chatting in the IRC channel.  I encountered various issues that were similar so I put my comments in.  Someone recommended I add the addargb......=true option in the xorg.conf file.  So, I did.  Boom the laptop gui stopped working.  Whoah.  I backed out of that fast.

Back to the desktop that I've had so much trouble with.  I tried both the drivers and they both generated the same message.  I was never given a GUI.  So, I thought to myself, hey, let's remove one of the video cards.  I shut down the computer, pulled a card and rebooted.  At this time the GUI started up and there was a message that I was in low graphics mode and was prompted with some totally inept wizard to reconcile the issues.  No luck.  Didn't work.  Also, when I got to the desktop the only thing there were my icons.  No panels, no menubars, no avant window navigator, no networking.

At this point I decided to run the nvidia installer again. I opened a terminal window (alt+f2) then typed gnome-terminal and hit enter.  When I got the terminal i did a uname -r.  It told me the old kernel name.  After this I stopped the gdm by typing "sudo /etc/init.d/gdm stop".  This stopped the GUI and then I did an alt+f5 and entered my username and password.  I then tried to run the nvidia video driver install again. I was given the same rash about how there was a mismatch.  When given the choice to continue anyway I chose that and was then give another rash about how the files necessary to compile the kernel module were not present.  Now, I'd done these installs before so I know that they were there prior to the upgrade.  At this point I decided to reboot, go through the "you are running in low res graphics mode prompts yet again" and finally end up at a desktop with just icons.  

I did an alt+f2 and typed in gksu synpatic.  I was prompted for my password and synaptic was brought up, except, remember, I have no network capability still so I was out of luck on getting updates.

I searched for kernel and found that many of the old kernels were there and I questioned the name of the kernel header/source files necessary for the latest kernel.  Nonetheless I was not able to definitively know whether the necessary files were there for the older kernels.

At this point I was determined to find out why I couldn't use the net and mistakenly started pidgin to enter the IRC chat.  Unfortunately no network so it was futile.  I was getting tired and frustrated.

I then chose to go back into the bios and ensure both network cards were on.  They were.  I then rebooted and went to a terminal and typed in ifconfig.  This told me I had an ip address of 192.168.0.100.  I said OK and did a google search to find the file where I had set a satic IP address for the eth0 and eth1 ports.  I'd done this because I wanted to ensure I got the same IP for my tests of zimbra.

I took a while but I found it in /etc/network/interfaces file.  I edited this file and commented out the hard coded IP info.

I then rebooted and went back in and found I had network access again.

I then loaded synaptic again and checked for updates.  I found that the kernel had been updated and I chose to take that update down.  I also figured it would add itself to the menu.lst file but it did not.

So, I opened the menu.lst file and found the common format for each entry of the various kernels and chose to copy it and make the changes manually to reference the newest kernel.  I did this, then rebooted.

At this time I decided to reinstall the nvidia drivers hoping that it would see the header and other files necessary to build the kernel loadable module.  It did and I was in the money. Except.......

When I get to the desktop I get no menus at all. I do have compiz working and I can click on folders and icons and have them work, but there's no menus "gnome panels" to which I can choose options.

That's were I stand now.  I am unable to find out how to get those panels to show up.


Please be advised that i will edit this post over time to fix grammar and to make what happened more clear and to add other things but for now I appologise for the spelling, grammar, etc.  I was getting my ideas down.

The basic failure on my update was four-fold, but I got 3 of the 4 working.

1)  Two video cards.  Had to remove one.

2)  Static IP which had been entered months and months ago and forgotten.

3)  Telling the installer to keep the settings in various files.  This was done because I didn't know the impact of letting the installer make any changes...and anyway, I chose the default which is hard to put blame on me for doing that.

4)  The fact that I can't get the gnome panels working so I can begin to clean up the rest of this nightmare.

---

### Post by starcannon on 2008-10-30
I'll post the probable fix for you gnome-panels first:
Alt-F2
```
gnome-terminal
```Press Enter
```

gconftool-2 --recursive-unset /apps/panel

```Press enter
```

gnome-panel

```Press Enter
In the possible event that you get a message stating:
> A panel is already running.then issue the following command as well:
```
pkill gnome-panel
```Press Enter
gnome-panel should autorestart itself, if it does not then issue once more this command:
```
gnome-panel
```Press Enter
That *should* get you back in business with panels and menus etc...

   
  
As for the Nvidia installer, you will need to install build tools.
Alt-F2
```
gnome-terminal
```Press Enter
```
sudo apt-get install build-essential
```Press Enter
Press "Y" when prompted.
You should now be able to build the nvidia drivers and any other compile from source projects.

GL and try to relax and have fun.

P.S.  Okay, I read most of your post, and while I understand your frustrated, it is very helpful to dispense with the rant, and try to clearly and plainly present the problem and its nature. I would also recommend NOT upgrading everytime something comes out. If your happily using an LTS (8.04 Hardy Heron is an LTS-Long Term Support) release, and if you are annoyed by tech problems, then DO NOT upgade to a non LTS release. I'm also curious why with all the problems you had on computer A, you went in and then did the same thing to Computer B?

---

### Post by jimbo99 on 2008-10-31
Though I appreciate your assistance and it did fix the gnome panel issue I managed to get the video working before.

It is extremely important that Canonical and everyone else including the linux bashers have an opportunity to see the frustrations and the rants of the individuals.  I believe this to be of the utmost imperative.

I have been using linux for some time, quite a while in fact, and the one thing that I find, and my friends find, and what I read about most often, is that they were disrespected or ignored or their problems belittled. There's not polite way to express frustration that results in change.  When you are polite about your frustration people assume you'll be OK.  They'll never understand their faults and never work to address them.  If i were to say anything about Linux it has been that, especially back in the day when we fought even to get a GUI.  You were belittled for thinking that you needed a GUI in linux and it wasn't your place to question them.

This is a hard mindset to overcome so it is important that people speak up, that they rant, that they complain and that the complain to everyone, including the Linux bashers.  Because it seems that only by lighting a fire under the asses of the developers do we get changes made.

Now, in this case, with Canonical they've known about their utterly poor execution on upgrades for the past 1.5 years and still abandon the fixes to the average user, when in fact, Ubuntu is supposed to be targetted to the human beings amongst us.  Their refusal to correct some very serious issues and to actually test adequately most often result in rants because it is just wrong to abandon people to issues that essentially kill their ability to use their computers.

Mark Shuttleworth may not have known what he was getting into when he created Ubuntu though I think his motivation was honorable.  He's let the user base down by not pushing to ensure that these upgrades to as flawlessly as possible.

My system had been running these past 6 months with few flaws.  I'd been using very few enhancements with the exception of maybe the latest compiz and always kept up to date with the Nvidia drivers.  I'd had the build-essentials in from the beginning.  And in fact, when I got the nvidia drivers working this time, before you attempted to assist me, it was not necessary for me to reinstall them.

Being that I had some knowledge of how this works in Ubuntu I was successful at getting my machine up and running again, but the average home user would not.  They would not tolerate having their systems down to the point they couldn't work.  They would not tolerate excuses about why nor would they even venture to guess how to modify the /boot/grub/menu.lst to add the correct references for the latest kernel.  They would not have known to pull the second video card nor would they have been willing, considering all the issues they had over the time they've used it, to consider having someone else do the update or fix their problems.  They'd have given up and they'd of had a good reason to do so.  But we should not encourage them to by being disassociated with their problems, feelings, and even rants, because as we all know, the squeeky wheel gets the grease.

Canonical and all the other distros must focus on the update as much as they focus on new features and they must focus on satifying people.  Mark Shuttleworth in his comments about the lack of possibility to make money on the desktop is really telling us he's backing out of his committment to bug number one.  We know this because the desktop is what drives all innovation in computing.  Servers are machines that require little human intervention on a day to day basis, whereas the desktop requires we interact constantly.

I understand the desire to not want to kick a dead horse and certainly not pay to feed a dead one, but this horse isn't dead.  It is simply ill because it doesn't get as much attention as the server horse.

---

### Post by starcannon on 2008-10-31
It's cool man, I hear ya, no worries. I'm happy the panels got fixed. I also encourage you to voice your thoughts about Ubuntu; I'm certainly not one of the ones that thinks theres nothing that need improved. 

That said, those who would be most interested in hearing what you have to say are less likely too find it in a call for help post, and most likely too find it in the forum specifically for personal testimonials and experiences: 
[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

Installing operating systems from the ground up is difficult, its why OEM's came up with restore partitions that automate the entire process for the particular machine thats being installed/restored to. Even Linux OEM Dell does this, on the 1420n I bought for my Mother, it had a restore partition on it, with a few clicks of the mouse her laptop can be restored to factory defaults, no knowledge needed.

Anyway, hang in there, give yourself time, and you'll sort your install out. I'd also recommend again, to not install the various intermediate releases; the LTS releases are excellent, are usually sorted out quickly, and kept in good working order for 3 years, then another LTS is released and the cycle rinses and repeats.

GL and I truly do hope you have a great time with your computer.

---

### Post by jerrylamos on 2008-10-31
For any number of us the crux problem is compiz.  That's the code that does "eye candy" by "playing tricks" with graphics hardware and software.

For most, 8.04 compiz worked O.K.

For many, looking at the posts, 8.10 compiz screws up or even freezes the pc solid.

My fix is to boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit 
resume normal boot.

With that, this 1 gHz laptop is running probably faster than it ever has, even you tube video's are better on this 1 gHz 32 bit Celeron 512 mb.

Looking at launchpad bug 259385 you'll see the developers mention a "blacklist" of graphics where officially compiz is not supposed to even start.  I think the "blacklist" is not near long enough.

Jerry

---

