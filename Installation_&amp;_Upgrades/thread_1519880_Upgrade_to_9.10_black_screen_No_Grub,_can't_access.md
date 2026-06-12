---
title: "Upgrade to 9.10 black screen No Grub, can't access Bios menu"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by WylieE on 2010-06-28
I just upgraded from 9.04 to 9.10 (using Update Manager) in an attempt to get to 10.04.  Installation and upgrade seemed to go OK until reboot.  Now I only get a black screen - I don't see the grub menu, I don't even see any way to access the BIOS menu- not even a blinking cursor. I can hear it start and I can see the numlocks key go on.  Ctrl-Alt-PrtScrn-B does not reboot (nor does Ctrl-Alt-Backspace- but I didn't expect that would)  Surprisingly Ctrl-Alt-Del does (or at least it sounds like it does) reboot the system.  I do have a NVIDIA cards and after reading around I suspect that this is likely the problem but I have no idea what to do now.. 

Here's what I've attempted:
I figured since I wanted to get to 10.04 anyway and this was so troublesome I could just go do a fresh install with a Live CD or USB to 10.04.  However, even with a live CD or USB I still just get a blank screen.  

Continually holding down F2 (and other function keys to try to acces Bios)

Holding down Shift while booting

Esc while booting

Moving the monitor to the VGA port (as opposed to the NVIDIA card).

Other information...
Previously I had tried to upgrade to 9.10, but ran into problems with it not recognizing my RAID, so I just found it easier to go back to 9.04.
(so although this is likely a graphics problem I guess the possibility is that now it doesn't even see my boot drive- although- if that was the case, I'd assume I wouldn't have the same problems from the CD or USB boot.)

My ultimate goal is to get this to 10.04, if I could do it with an upgrade instead of a fresh install I'd prefer that, but at this point just getting back to a functioning computer would be ideal.  I see many options in other posts for how to get back once you can access a command line- but since I can't even see that, I'm not sure what to do now.

Thanks for any advice help.

---

### Post by WylieE on 2010-06-28
Somehow, after a combination of playing around with different monitors / ports and this link 
[http://ubuntuforums.org/showthread.php?p=9445778#post9445778](http://ubuntuforums.org/showthread.php?p=9445778#post9445778)
 I am now able to see the grub menu and get to login- I still don't have the NVIDIA drivers correctly set up- but I am wondering if I should bother with this now or just try to go on to 10.04 and fix everything there?
Any suggestions?
Many thanks!

---

### Post by chkneater on 2010-07-01
This sounds like what I've affectionately come to know as "the Problem".  You can hear the system sounds in the background while booting right?  Also you do see the normal system startup stuff up to the point Ubuntu is loaded right?

---

### Post by WylieE on 2010-07-01
"The Problem", I like that.  Actually, it's even worse than that!  I couldn't get any screen signal, not BIOS, not booting info, not even Grub!  But I think I have it solved.
My problem was that upgrading switched my default screen output- I have 5 GPUs, so I have a total of 6 potential places to attach a monitor.  This isn't probably very elgant, but I can now use my computer, so I'll post my solution in case it gives someone else a starting point. And for myself so next update I can remember how to do it. 

1.  First figure out where to attach the monitor, for me this took a lot of rebooting and trying different ports- it does not seem to work to switch the monitor after booting, I had to switch it before restarting. 
2.  Next hit escape to get the Grub loading menu. I don't want to change kernels I just want to paus here to switch monitors.
3. Switch the monitor to the graphics card that it used to work from (in 9.10) - now I have a blank screen, but I just hit enter to boot from the kernel.

For me... (I have NVIDIA cards) it now loads in low graphics mode.
To adjust this (from many google/ forum searches).

Download latest NVIDIA drivers
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

I get my kernel name
$ uname -r
2.6.32-23
$ sudo apt-get install build-essential linux-headers-2.6.32-23

(if you're running an X-server you probably need to stop that to load NVIDIA drivers do the next step)
$ etc/init.d/gdm stop
(not sure about this one - I didn't have an X-server going yet)
$ sudo /sbin/init 3 

then get to the driver location and run the drivers.
$ sudo chomd +x NVIDIAdrivername.run
$ sudo ./NVIDIAdrivername.run

then (this is may already be done by the driver install but just to be safe)
$ sudo nvidia-xconfig

One last step- if you didn't do this before the upgrade you'll need to blacklist nouveau

$ gedit /etc/modprobe.d/blacklist.conf

now I reboot (probably restarting X-server would be sufficient).

My main problem still is that I have to move the monitor before rebooting to the "wrong" card, let it boot, and then stop at Grub move it to the "right" one then continue to boot.... a bit of a hassle but I hope I won't have to reboot much more.

I suppose I could change something in BIOS, but it's strange because I did not have to move the monitor before and Ubuntu shouldn't be messing with any of those settings.

I'm also going to add how I was able to get COMPIZ running on two monitors and moving the window between the monitors since this was in fragments from many other forums.

First be sure that you have visual effects off (I found this kept the changes from "sticking" when I didn't do this first)

system->preferences->appearance->visual effects  select "none"

edit /etc/X11/xorg.conf

comment out the line for Xinerama (put a # in front of it)
Alternatively I think you can change the line to 
Option    "Xinerama"  "0"

then run nvidia-settings
$ sudo nvidia-settings

go to X Server Display Configuration
select configure
select twin-view
Save X configuration file.

restart X Server

restart compiz
system->preferences->appearance->visual effects  select "custom"


now I can move windows between the screens

I don't know if this will help anyone but at least maybe it will be a start for future searches.

---

