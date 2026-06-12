---
title: "Ubuntu 10.04 Login Loop"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2010-05-04
I installed ubuntu-10.04-desktop-i386.iso from a CD I burned. (I ran md5sum and got the correct result. Also checked the media for errors; there were none.) The installation ended with the long list of "end-request: I/O error" and I've read that I should not be concerned about that. 

However, when I try to log in, I'm returned to the login prompt. If I switch to Gnome-failsafe, I can successfully log in. I've tried several things listed on this forum, but none of them work on my machine. A number of them talk about problems with nvidia. My machine has the on board VIA video hardware.

The last post that seems related was six days ago. Has there been any further progress? 

Is there something I can do to resolve the problem from the failsafe login?

Thanks for any help.

---

### Post by AJH101 on 2010-05-05
I have the same problem by the sound of it - a login 'Groundhog Day' - a looping login!

---

### Post by dabl on 2010-05-05
"Login-loop" has historically had several possible causes:

- filesystem full/almost full
- root permissions attached to ~.ICEauthority and ~.Xauthority
- some miscellaneous video driver issues

So, in your "recovery mode" session (running as root at the "#" prompt) you can run ```
df -h
``` and observe how much free space you have in your root filesystem -- on a new installation there should be 20% or more free space.

Also in recovery mode, you can safely delete the hidden ~.ICEauthority and ~.Xauthority files that are in your user's home folder.  Then you can try a reboot, or else

```
# service gdm start
```

and see if it starts the X server.

---

### Post by AJH101 on 2010-05-05
Great - how do we delete the files?!

---

### Post by kansasnoob on 2010-05-05
My guess is that it's related to Plymouth. First look here:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984/comments/18](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984/comments/18)

The whole thread:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984)

But since you're dealing with an installed Lucid rather than the Live CD when it boots you'll need to try temporarily editing the "boot line" in grub2. 

Now if you only have one OS you won't see the boot menu unless you press the Shift key right after the System/BIOS screen passes, but once you get the boot menu press **e**.

That will allow you to temporarily edit the grub "boot" parameters. On the line that looks something like:

```
linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=fb0e61a6-d355-4687-9a98-da164a56cc60 ro splash quiet  quiet splash
```

Just use the backspace key to remove all of the "splash quiet  quiet splash". Why that's redundant I don't know? Dev asleep at the wheel?

Then just press Enter to try and boot. If it works then you know it's Plymouth! So then file a bug against Plymouth using "ubuntu-bug plymouth".

In the meanwhile you can sort of "fix" it by editing "/etc/default/grub". Look here:

```
lance@lance-desktop:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=60
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[B][COLOR="Red"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="splash quiet"[/COLOR][/B]

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I don't know why I have that redundancy, but you remove only the part in parentheses! So those two lines would end up like this:

```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

```

Of course you may not have that redundancy, then again maybe that redundancy is good?????????

Just be careful! If you break it you own it!

Oh also be sure to run "sudo update-grub" after you're done editing any grub file.

Another also: this will disable your quiet splash!

---

### Post by bitter_mike on 2010-05-05
I'm having this same problem and I think it has something to do with apparmor. I managed to get dmesg output from when I try to login and I get this error message:

```
[  506.798163] type=1503 audit(1273089330.541:17):  operation="open" pid=2001 parent=1951 profile="/usr/share/gdm/guest-session/Xsession" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/mike/.profile"
```

I also checked out ~/.xsession-errors which contains the following, also relating to ~/.profile:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open /home/mike/.profile
```

I've seen similar errors in the forums which have the same format but the file in question has something to do with a program or service besides GDM (i.e. firefox or evince).

Hopefully someone with more knowledge than I about apparmor knows what this error means and can help with fixing it. I've already tried dpkg-reconfigure apparmor, which completed successfully, but didn't fix the problem.

Mike

---

### Post by bitter_mike on 2010-05-05
kansasnoob: I tried doing that on the fly edit of the Grub entry and it did indeed make the booting verbose, but the problem remained, so I don't think the problem is Plymouth.

On a further note, I played around with a few things in apparmor to see if I could get this working. First, I disabled apparmor by logging into one of the terminal screens and executing 

```
sudo service apparmor stop
```

After this, when I logged in, instead of flashing the black screen and bringing me back to the login screen, it just hangs with nothing but the background and a cursor, which I can move. Doing this generates no dmesg output and no output in the ~/.xsessionerrors file. It just hangs there.

From this, I conclude that apparmor definitely plays some role in this, but there's more to it obviously.

---

### Post by dabl on 2010-05-05
> **AJH101 said:**
> Great - how do we delete the files?!

If you boot recovery mode, and are at a text prompt, you need to "_c_hange _d_irectory" (cd) to the /home/user directory, and then "_r_e_m_ove" (rm) the files I named above.

so it is

```
# cd /home/AJH101
``` (or whatever your user name on the system is)

and then 

```
# rm .ICEauthority
```
```

# rm .Xauthority
```

```
# service gdm start
```

---

### Post by bitter_mike on 2010-05-05
I can't speak for the originator of  this thread, but I already tried removing .Xauthority and .ICEauthority and that didn't work either. No change.

Mike

---

### Post by bitter_mike on 2010-05-05
Ok, so good news and bad news. Good news: I got this fixed on my computer. Bad news: its a pain in the ***. Here's how I did it:

Important note: I noticed that the menu for selecting a Gnome session was gone from the login menu before I got the idea to do this.

step 1: Re-install GDM.

Boot up normally, then press control+alt+f3 to get to a TTY login window and login. From there, execute the following command to stop GDM:

```
sudo service gdm stop
```

Then, use apt-get to first remove, then re-install the gdm package.

At this stage, restarting GDM and logging in got me to a blank desktop with a cursor and a single terminal window in the upper-right hand corner. There was still no sessions menu at the logon page; just keyboard and language selection.

step 2: Install gnome-session

For some reason this package is not installed when you re-install GDM. As far as I can tell, it actually enables GDM to run the desktop environment session with menu bars and such. From that tty window, use apt-get to install gnome-session.

At this stage, when I logged it, everything worked fine except it threw an error about not being able to load the fast-user-switcher applet.

step 3: Install the applet again.

Just use apt-get to install the package indicator-applet-session. This fixed my problems completely and I'm not back to my normal desktop.

If this works for anyone else with the problem, go ahead and mark it solved.

---

### Post by cato58 on 2010-05-06
This is how I fixed this problem on my computer:


During the boot up, hit ctrl-alt-F1 for a tty login

Use these commands:

sudo stop gdm
sudo apt-get purge gdm
sudo apt-get install wdm
sudo reboot now

---

### Post by rlindell on 2010-05-10
> **bitter_mike said:**
> Ok, so good news and bad news. Good news: I got this fixed on my computer. Bad news: its a pain in the ***. Here's how I did it:

[...]



This did the trick for me. Thanks!

---

### Post by Huike on 2010-05-10
I have tried all of the above solutions but with no luck. My Ubuntu 10.04 is installed on a Asus P4VM800 BIOS 1.60 with VIA on-board VGA with 32MB vRAM. P4 3G. Ubuntu 9.10 was working perfectly until I upgrade to 10.04 and it just stays in the login screen. I thought it might be the upgrade was not successful so I reinstalled 10.04 freshly but it was the same. Any other thoughts? Thanks.

---

### Post by Amerikaner on 2010-05-11
I'm having the same problem.  Get to login, enter info, login comes back up.  EXTREMELY frustrating.

I am able to get to the desktop by using failsafe graphics.  Once there I have no idea what to do to fix it.  I can't use the TTY login because I get an error saying "device cant enter state" or something like that.  I'm on an Averatec 3700 laptop if that makes any difference.


EDIT: also, is the reason I can't go above 800x600 res because I'm in failsafe graphics or is that an additional problem?  I believe I've had video driver issues with this laptop and ubuntu before but not sure.

---

### Post by AJH101 on 2010-05-12
I had to reinstall Lucid and (try this if you can log into recovery/rescue mode) turn off the log in requirement (under Preferences or Administration I think).

This means you will have to log into your keyring each time but now I have Lucid working I do not want to risk turning my 'login screen' back on a blocking access again!

---

### Post by Amerikaner on 2010-05-12
> **AJH101 said:**
> I had to reinstall Lucid and (try this if you can log into recovery/rescue mode) turn off the log in requirement (under Preferences or Administration I think).

This means you will have to log into your keyring each time but now I have Lucid working I do not want to risk turning my 'login screen' back on a blocking access again!

Doesn't work for me.  It does the automatic login right back into the login.  I'm thinking its a video issue for me because the login prompt shows up in the lower right of the screen as if the resolution is wrong.

---

### Post by Barnabooth on 2010-05-14
> **cato58 said:**
> This is how I fixed this problem on my computer:


During the boot up, hit ctrl-alt-F1 for a tty login

Use these commands:

sudo stop gdm
sudo apt-get purge gdm
sudo apt-get install wdm
sudo reboot now

Thank you, fixed the problem for me as well.

---

### Post by Amerikaner on 2010-05-16
I tried the above fix in the terminal. After the purge command it said it needed to refresh the video settings or something similar to that and then I couldn't get back.  I don't know how to install wdm from the basic command prompt especially since I don't know how to login to my network connection from there.  Help?  Is it possible to do the above and just not do the purge command?

EDIT:  I reformatted and tried doing purge after i installed wdm.  wdm installed fine apparently and i chose it as the default.  I still get the login loop.  Someone's gotta know how to fix this.  Help a noob out?

---

### Post by theiLLziLLa on 2010-05-17
> **Amerikaner said:**
> Doesn't work for me.  It does the automatic login right back into the login.  I'm thinking its a video issue for me because the login prompt shows up in the lower right of the screen as if the resolution is wrong.

Did you have any luck fixing that issue? I am having the same problems, and I can not access the terminal.

---

### Post by Amerikaner on 2010-05-19
> **theiLLziLLa said:**
> Did you have any luck fixing that issue? I am having the same problems, and I can not access the terminal.

Unfortunately no.  I'll be sure to post here if I fix it.

---

### Post by mbutash on 2010-06-04
I had this issue, and the suggestion to install gnome-session again was it.  I realized when doing so, it was reinstalling evolution, which I removed out of spite because it has let me down more often than not.  Seems a bug that it would remove gnome-session for evolution, enough to break the desktop.  I'm sure I'm not the only one that hates evolution enough to inadvertently kill their desktop.  sudo apt-get install gnome-session  Evolution might not be the only thing dangerously removing gnome-session the only dependency.

---

### Post by doubi on 2010-07-13
> **bitter_mike said:**
> Ok, so good news and bad news. Good news: I got this fixed on my computer. Bad news: its a pain in the ***. Here's how I did it:

step 1: Re-install GDM.

...

step 2: Install gnome-session

...

step 3: Install the applet again.
Thanks so much sir! Worked a treat for me.

---

### Post by orzeh on 2010-07-18
> **bitter_mike said:**
> Ok, so good news and bad news. Good news: I got this fixed on my computer. Bad news: its a pain in the ***. Here's how I did it:

Important note: I noticed that the menu for selecting a Gnome session was gone from the login menu before I got the idea to do this.

step 1: Re-install GDM.

Boot up normally, then press control+alt+f3 to get to a TTY login window and login. From there, execute the following command to stop GDM:

```
sudo service gdm stop
```

Then, use apt-get to first remove, then re-install the gdm package.

At this stage, restarting GDM and logging in got me to a blank desktop with a cursor and a single terminal window in the upper-right hand corner. There was still no sessions menu at the logon page; just keyboard and language selection.

step 2: Install gnome-session

For some reason this package is not installed when you re-install GDM. As far as I can tell, it actually enables GDM to run the desktop environment session with menu bars and such. From that tty window, use apt-get to install gnome-session.

At this stage, when I logged it, everything worked fine except it threw an error about not being able to load the fast-user-switcher applet.

step 3: Install the applet again.

Just use apt-get to install the package indicator-applet-session. This fixed my problems completely and I'm not back to my normal desktop.

If this works for anyone else with the problem, go ahead and mark it solved.

It worked for me either, thanks

---

### Post by Penny N. Nickels on 2010-07-18
> **cato58 said:**
> This is how I fixed this problem on my computer:


During the boot up, hit ctrl-alt-F1 for a tty login

Use these commands:

sudo stop gdm
sudo apt-get purge gdm
sudo apt-get install wdm
sudo reboot now

In another post in this thread, it has it as **[COLOR=Red]ctrl-alt-f3[/COLOR]**[COLOR=Black]**. **Which one is it: [COLOR=Red]**f1**[/COLOR] or [COLOR=Red]**f3**[/COLOR]? I've also been having the same problem of the login looping. [/COLOR]And, yes, I am a noob! Thanks!

---

### Post by ClrScr on 2010-08-26
> **cato58 said:**
> This is how I fixed this problem on my computer:


During the boot up, hit ctrl-alt-F1 for a tty login

Use these commands:

sudo stop gdm
sudo apt-get purge gdm
sudo apt-get install wdm
sudo reboot now

Please Help!

I tried this

after 
sudo apt-get install wdm

I get the following message

> Reading Package Lists ... Done
Building dependancy tree ... Done
Reading State information ... Done
Package wdm is not available etc...
E: Package wdm has no installation candidate

What do I do now?
O yes, I am a noobs noob!

PS That pc is not connected to the www. Wil not be connected. Ever. If that is relevant.

---

### Post by ClrScr on 2010-08-26
> **bitter_mike said:**
> Ok, so good news and bad news. Good news: I got this fixed on my computer. Bad news: its a pain in the ***. Here's how I did it:

Important note: I noticed that the menu for selecting a Gnome session was gone from the login menu before I got the idea to do this.

step 1: Re-install GDM.

Boot up normally, then press control+alt+f3 to get to a TTY login window and login. From there, execute the following command to stop GDM:

```
sudo service gdm stop
```

Then, use apt-get to first remove, then re-install the gdm package.

At this stage, restarting GDM and logging in got me to a blank desktop with a cursor and a single terminal window in the upper-right hand corner. There was still no sessions menu at the logon page; just keyboard and language selection.

step 2: Install gnome-session

For some reason this package is not installed when you re-install GDM. As far as I can tell, it actually enables GDM to run the desktop environment session with menu bars and such. From that tty window, use apt-get to install gnome-session.

At this stage, when I logged it, everything worked fine except it threw an error about not being able to load the fast-user-switcher applet.

step 3: Install the applet again.

Just use apt-get to install the package indicator-applet-session. This fixed my problems completely and I'm not back to my normal desktop.

If this works for anyone else with the problem, go ahead and mark it solved.

Mike, please be so kind as to add the code to all the steps so that I can try this out.
Thanks

---

### Post by iansane on 2010-10-16
Hi all,

I just wanted to share my own encounter with this login loop.

Before doing anything without knowing what was causing the issue I used CTRL+ALT+F1 and tried loggin into TTY (command prompt) with success. I then did "service gdm stop" followed by "service gdm start" and saw that the first thing my system tried to do was find /usr/lib/oracle/ex/product/...blah blah some file.

The problem was that the file didn't exist because I had removed oracle the night before. Even after deleting the lines from my .bashrc file that exported the path to oracle, something in my system was still trying to open the non-existing path. In my case I had installed oracle with su - but when I removed it I used synaptic and chose the "completely remove" option. It failed to tell me that something residual was left in the system.

The fix was to log in as root in the command prompt and then reinstall oracle. Well that was what it took to get me back into gdm anyway. Now I have to figure out how to remove oracle without it causing the login loop again.

The point of sharing this is to say that you should try logging in to TTY and see if you get any clue as to what is actually causing the problem before trying random fixes.

---

### Post by StygianAgenda on 2011-03-01
It doesn't matter either way, whether you use CTRL+ALT+F3 or CTRL+ALT+F1.  On *most* Linux systems, regardless of distribution, you will find multiple TTYs... usually associated against CTRL+ALT+F1~F6.  CTRL+ALT+F7 usually takes you to the TTY that Xwindows is loading on.

Also, provided that you are either using an older version of Ubuntu, or a different Linux distro altogether, you can use CTRL+ALT+Backspace to restart the X-server.  However, the last few versions of Ubuntu have dropped this setting from the defaults... it can be re-enabled though.

---

