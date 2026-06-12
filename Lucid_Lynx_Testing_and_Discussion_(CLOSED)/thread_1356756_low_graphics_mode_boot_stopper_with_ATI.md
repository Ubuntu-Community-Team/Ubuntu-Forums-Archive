---
title: "low graphics mode boot stopper with ATI"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-16
I am still having trouble booting to my Stoned Lizard install.

I have gotten to the point where I can log in with the CLI log in in recovery (with startx).

There was a problem with "ibus" for some time that I finally got straight by removing and installing "ibus ibus-gtk ibusm17n ibus-table".  Got an error that a file wasmissing and it couldn't be set up.  Transplanted the file from Lounge Lizard and ran "dpkg --configure -a" and that fixed that.

If I use the generated menu entry or the symbolic menu entry I get the low graphics mode song and dance.  Click OK on the boxes and then the thing locks up.

I tried (desperation move) "nomodeset" on the bugger and that just locks it up off the bat.  Decided that was a bad move.

Anyone have an idea what I should do now?

---

### Post by mattduckman on 2009-12-16
I was able to fix my low graphics mode problem by using xorg-edgers. This was on a Radeon HD 4850.

Your problem seems different than mine though, because I was able to get a working desktop in low graphics mode, while it sounds like you aren't.

---

### Post by ranch hand on 2009-12-16
No It just quits after the low graphics boxes are gone.

I do not understand why I can boot in fine from the recovery menu using the CLI though.

This is a Radeon HD 2400 PRO.

I have never used any but the standard generic drivers with any real success.  I have 3 other installations of 10.04 and have had small problems with them but nothing as persistent  as this.  They video stuff is set up the same on all of them.

The one I am having trouble with is a 9.04>9.10>10.04 upgrade (from Stoner Edition1.0, thus Stoned Lizard).  It is the one I really want to use as my daytime production machine but I have had to switch to Lounge Lizard (9.10>10.04 upgraded when the tool chain went up, my oldest Lizard).

I will look at the xorg-edgers stuff.  This card seems to be one that is just not real well supported by anyone.  There is a driver for it on the ATI site now though.  I have tried it on 9.04 and deleted it, not a real good experience.

---

### Post by BwackNinja on 2009-12-16
This has happened to me too, but went away after a reboot.

---

### Post by ranch hand on 2009-12-16
I have 4 installs of 10.04 and run one as my production OS during the day when I can keep an eye on it.  This is because of boinc that I have set to keep my cpus running full time at 100%.  It only backs off if  I am doing something that requires a good bit of cpu.  To make it better the boinc is an alpha too.

I run 9.04 at night with boinc from the repos and can trust it.

Needless to say, I reboot at least twice a day into something.  Usually more.  I rebooted at least 6, it may have been 8, times to the problem OS today.  Try booting normal - fail, boot recovery succeed.  Look things over and try again.

I am about to start tearing my hair out.

---

### Post by ranch hand on 2009-12-16
I am in Stoned Lizard via recovery and CLI log in.

Right toward the end of the recovery text, before you get to the recovery menu, there are 4 lines that basically say that the read only FS needs fixed and will be in "recovery" and then saying that this has been done.

This has to do with "journal recovery".  This is part of Plymouth isn't it?

What is this with the "read only FS"?

---

### Post by n0glu3 on 2009-12-16
I have this problem with a Nvidia card.

---

### Post by ranch hand on 2009-12-16
Well, I am sure glad that I am not alone in this.

I can't even file a bug on it.  Haven't got a clue as to the package involved.

---

### Post by n0glu3 on 2009-12-16
Out of curiosity, what kind of monitor do you have?

---

### Post by ranch hand on 2009-12-16
Dell LCD.

---

### Post by n0glu3 on 2009-12-16
> **ranch hand said:**
> Dell LCD.

Nevermind then.

---

### Post by ronacc on 2009-12-16
try booting a livecd or another partition and doing an fsck on your stoned lizard root partition . the journel recovery I think means its trying to recover from an fs error using the journel (ext3 or 4) , the ro indicates read only , if errors are detected when the fs is mounted it is remounted read only .

---

### Post by ranch hand on 2009-12-16
I am on 9.04 over on my main drive right now running boinc for all it is worth.

However, While I don't boot into my test OS' with this drive turned on, I don't mind mounting them (turn on the switch on the external enclosure).  The up shot of this is that I have a script to chroot into the buggers from here.

I will just do that little thing right now.

I assume that the fact that the normal check that just took place during boot up (attempted) would not catch all the possible problems.

---

### Post by ranch hand on 2009-12-16
> 
StonedLizard-roo: clean, 377606/1635392 files, 2005214/6602707 blocks
e2fsck 1.41.9 (22-Aug-2009)

So, now what?

---

### Post by ronacc on 2009-12-16
oh well it was just a shot in the dark . does your .xsession-errors tell you anything useful ? I have no knowledge of what problems ati cards are having I'm 100% nvidia here .

---

### Post by ranch hand on 2009-12-16
Doesn't look to my ignorant eyes to be anything to stop the bugger booting.
> 
Unable to open desktop file /home/stoner/.local/share/applications/gksu.desktop for panel launcher: No such file or directory
<file is there>

<got a lot of the below>
** (gnome-volume-control-applet:2180): WARNING **: Connection failed, reconnecting...
** (gnome-settings-daemon:2126): WARNING **: Connection failed, reconnecting...

<two of the below>
(nautilus:2685): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

got a couple of failed to connect nautilus with samba shares song and dance - don't have it set up - have never used it any where

got a couple about boinc manager - can't find what it is talking about - boinc removed 

/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
is interesting don't use compiz

 WARNING: Could not launch application 'conky.sh.desktop': Unable to start application: Failed to execute child process "/home/stoner/conky.sh" (No such file or directory)
haven't tried to run conky - left over from when this was 9.04

(polkit-gnome-authentication-agent-1:2163): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'
(polkit-gnome-authentication-agent-1:2163): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
have no idea what this is - sounds bad - oh, has to do with appletts removed a few lines further on

some stuff about obsolete themes (more leftovers from 9.04)

--- Hash table keys for warning below:
--> image/png
--> Lazy Larry
--> l2071
--> text/plain
--> root
--> l2056
--> inode/directory
--> larry

(nautilus:3004): Eel-WARNING **: "unique eel_ref_str" hash table still has 8 elements at quit time (keys above)
have no clue as to this at all

(gnome-power-manager:2829): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (gnome-power-manager:2829): WARNING **: Failed to send buffer
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

** (gnome-power-manager:2829): WARNING **: Failed to send buffer

** (gnome-power-manager:2829): WARNING **: Failed to send buffer

** (gnome-power-manager:2829): WARNING **: Failed to send buffer

** (gnome-power-manager:2829): WARNING **: Failed to send buffer
no clue

** Message: Got disconnected from the session message bus; retrying to reconnect every 10 seconds
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
very last lines


---

### Post by ronacc on 2009-12-16
hmm if this is a /home that has been carried forward through 2 upgrades mabye there is a leftover desktop config file somewhere that is stopping your DT from loading .Are your other installs that are booting ok all full fresh installs ? that would tend to indicate that it is something leftover that is gumming up the works .

---

### Post by ranch hand on 2009-12-16
Well that could be.  This is 9.04>9.10>10.04 upgrade.  It is the second Lizard put on the drive.

Lounge Lizard was the first and it is a 9.10>10.04 upgraded right with the toolchain.  I have had a little more problem with it than with Daily that was installed with the first daily build.

I have another one that I do apt dist-upgrades on that is from the A1 ISO testing and I consider a "throw away OS" as it will be replaced when A2 or 8.04.4 comes along.

I am not having any problems with it right now (last couple of days) but it is not a good comparision for anything but testing to see how toxic the upgrades are.

I will have a look at that home partition.  I am not sure where to start.  At least I have Daily to compare things to (and Lounge for that matter).

---

### Post by alain57 on 2009-12-17
Hi,
i have the same problem with an Intel X3100 integrated graphic chip

I'm using lucid on my laptop (not a VM) with a second display (a dell 22" monitor)

I had 2 problems:
-low graphics
-only one monitor working (laptop one or dell one)

i found a solution:
boot in recovery mode
choose root console
type gdm


ok its not a good solution, but at least i can use my laptop without low graphic or monitor problem

---

### Post by olnir on 2009-12-17
> **mattduckman said:**
> I was able to fix my low graphics mode problem by using xorg-edgers. This was on a Radeon HD 4850.

Your problem seems different than mine though, because I was able to get a working desktop in low graphics mode, while it sounds like you aren't.

Second that.
Using Xorg-edgers repo was the only thing that got me past low graphics mode problems on my box 9.04 - 9.10 - 10.04
ATI HD4850

---

