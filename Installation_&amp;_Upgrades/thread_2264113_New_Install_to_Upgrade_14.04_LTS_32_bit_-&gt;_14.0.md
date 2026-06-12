---
title: "New Install to Upgrade 14.04 LTS 32 bit -&gt; 14.04 LTS 64 bit"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by RecceDG on 2015-02-05
I'm starting this thread to record my trials and tribulations with my main Linux box.

This machine is my household Samba server, housing the shared network drive that holds all our images, documents, videos, music etc. It houses the home Wiki site (that we use as a project planner). I also use it as a study station (Recoll and a ton of pdf textbooks is very handy) It hosts our Subsonic server for whole-house music playback, and I also use it as a Linux gaming machine, via Steam.


The machine itself is a Phenom II x6 1090T, with 8Gb of DDR2 RAM (it's an AM2+ motherboard) and a Radeon HD 7870 graphics card. It has 2 x 3Tb drives, 2 x 1 Tb drives, and a brand new 120 Gb SSD.


It had been running 14.04 LTS 32 bit, upgraded in place from Ubuntu 10 from when I first built the box in 2009. The upgrade from 12.04 to 14.04 went particularly poorly, and the machine was getting flakier and flakier with time. I bought the SSD specifically to hold a new, fresh install of the OS with a view to eliminating all the flakiness. And to be honest, I was planning on moving to Fedora and washing my hands of Ubuntu and a lot of the strange choices Canonical has been making lately.

Unfortunately, I need the AMD Catalyst drivers and I want GNOME as my desktop environment, and those don't play well on Fedora (or so I'm told). I'm also heavily dependent on Steam working (which prefers Ubuntu) and the other bits of my setup also are known to work on Ubuntu... so I guess I'm locked in for the moment.

Recently, the latest crazy has been that the machine would segfault 9 times out of 10 at boot if the SSD was plugged in - the problem occuring when the md drives are being assembled. I have my root partition as an md drive, my home partition as an md drive, and a third md drive is mounted as extra space in /home.

This AM, my hand was forced. I got up to find the machine hard locked, and it segfaulted on boot no matter if the SSD was plugged in or not. Happily, I had a 14.04 LTS 64 bit install DVD ready to go.

The first attempt at installing crashed with about 3/4 of the "copying files" process done. It attempted to file a bug report (it opened Mozilla, I logged into launchpad) but it never completed; it was stuck on a 10-second refresh loop that never ended.

The second attempt, I unchecked "download updates while installing" and this time it worked. It complained about the language package checksum not matching the DVD (and recommended burning the disk slower or moving the computer to a cooler environment) but otherwise it installed to competion. On reboot, I entered the BIOS and set the boot priority to the SSD, and the system booted pretty much immediately (SSDs are pretty cool)

Once logged in, I changed the display preferences to account for my portrait-mode second monitor, and then attempted to start mdadm. It wasn't installed, so I installed it, then ran "sudo mdadm --assemble --scan" and it found all 3 md drives. The /home drive and the /home/media/blah drives came right up; the / drive only came up on 1 drive.

I now suspect that either the physical drive that didn't come up is failing, or that something corrupted that partition.

My plan going forward is to:

1. Mount the md arrays in temporary mount points
2. Move the old user directory from the md version of /home to an olduser directory
3. Copy the /home directory from the SSD to the md version of /home
4. Edit /etc/fstab to mount the md /home as /home and the old / degraded array as /oldroot
5. Reboot.

That should get me all my data files back, set up my user with a clean home directory with no old dotfiles in it, and give me access to the old drive and old config files to help setting up the various servers easier.

Once I have the new system fully set up, I'm going to reformat the 2 x 1Tb drives as a single RAID 1 partition (like the 3Tb drives are) plus a little swap space. Long-term, I'm going to migrate all the drives to 3 x 6Tb drives in a RAID 5 setup.

My immediate issue is setting up the GNOME environment and getting rid of Unity. What is the current recommended process for that?

---

### Post by TheFu on 2015-02-05
Seems like you are doing fine.  instll the gnome you want, logout, select it on the option menu, login. If that works, start purging unity*.

I'm not a fan of RAID5 on disks over 750G in size. There's a well-know article about RAID5 issues.  Better to go for RAID6 if you really need the HA - RAID is never a substitute for backups - NEVER.  Backups are 1,000x more important than RAID.

Most server settings are not stored in /home.  You need to keep all the places where those settings are stored until every daemon you want again is working.  I find it easier to put the settings back, prior to re-installing the services. Major changes should be migrated to the new settings necessary. That's the theory.

---

### Post by RecceDG on 2015-02-05
I got the "purple screen on boot" issue. Changing /etc/default/grub seems to have fixed it.

There was a minor hiccup when I forgot to change the permissions on the user directory and it mounted the /home raid array with the user directory owned by root. Whoops.

Used the install DVD as a rescue DVD and fixed that.

Samba is back in operation.

MediaWiki is back in operation.

Recoll reinstalled.

Printers installed.

It is sooooo nice that I have a functioning copy of the old root directory to steal config files, mysql databases, and the like from. I agree with your statements about backups, but RAID sure helps bridge the gap.

I'm now installing Catalyst drivers, using the debs from ATI instead of the command line installer. We'll see how that goes.

Which GNOME do I want? What's the most functional, best-behaved package?

lcd4linux doesn't seem to be working. My case has a parport driven display on it that I use to show CPU load and network activity. To be investigated later.






Installing Steam before rebooting after the Catalyst drivers locked the display and I hadn't installed ssh server yet.

Whoops.

After reboot lcd4linux came up properly.

Catalyst seems to be working.


So now Steam segfaults and no combination of re-installing it (from either the repository or the Steam website) will work.

Awesome.


I've found a bunch of references that talk about uninstalling Catalyst, installing the OSS ATI drivers, installing Steam, then instaling Catalyst.

So I guess I'll try that.




Installing the OSS video driver worked. Steam is installed.

I'm going to run a benchmark then try Catalyst again




I'm still looking for advice on the best way to get a Gnome environment.

Compiz or Metacity? Which is better supported?


Team Fortress @ 1080p max settings 4xAA = 42.5 FPS on OSS drivers and 51 FPS on Catalyst

---

### Post by mörgæs on 2015-02-07
I have merged your posts.

When you have the latest post in a thread please edit it in stead of posting a new one.

---

### Post by TheFu on 2015-02-07
> **RecceDG said:**
> I'm still looking for advice on the best way to get a Gnome environment.


Sorry - can't help with that. Don't use **any** DE here.  I live in a lighter, pure WM-only, world.
I find all the extra stuff that DEs do too distracting. It just isn't necessary.

Plus there are many gnome spinoff options that have become popular. Lots of instructions for how-to install those exist.

---

### Post by RecceDG on 2015-02-07
> **TheFu said:**
> Sorry - can't help with that. Don't use **any** DE here.  I live in a lighter, pure WM-only, world.
I find all the extra stuff that DEs do too distracting. It just isn't necessary.

Plus there are many gnome spinoff options that have become popular. Lots of instructions for how-to install those exist.

Those "lots of instructions" are exactly *why *I'm asking for advice. Too many choices with no indication of the strengths and weaknesses of each.

As you can see, a straight-up installation - even for somebody with over 20 years of Linux experience - is not a trouble-free process. And the target is constantly moving; what was good advice in somebody's installation guide in 2010 may no longer hold in 2015.

So I would appreciate some advice and direction from someone who *does *use a Gnome environment.

---

### Post by TheFu on 2015-02-07
> **RecceDG said:**
> So I would appreciate some advice and direction from someone who *does *use a Gnome environment.

I'd recommend starting a new thread with just that question. We've buried it deep now.

A few random thoughts:
* check youtube for current gnome-based desktops to see what you like before doing anything. Lots of people will show off their desktops there, for fun.  Mate, gnome2, gnome3, cinnamon, just to get started.  
* Ask folks at your LUG for their thoughts.  I'm in 3 LUGs here - huge variety of experiences available just by posting to 3 email lists.
* You can install all of these DEs on the same system, but they will likely use the same ~/.config/ area and can have conflicting settings. Just create a new userid/home for each trial as you test them out yourself. Once you've decided, move the current ~/.config/ to a backup and logout/login using a new selection and that .config area will be recreated.  In theory, settings should be all stored there, but ... there are likely to be exceptions.  A full backup would be smart.

---

