---
title: "Install 6:10 CD: Black screen at GDM Login"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Rory on 2006-10-20
Booting in to the 6.10 CD and RC DVD.
Boots and goes along without issue through the boot process with new Ubuntu boot splash in background.  Is about to switch over to the Live Desktop and the screen goes blank/black. This occurs on the default Install/Start boot and the 2nd Safe Graphics option.  Using the F4 VGA commands do not help.  Note: a signature of this particular bug is that selecting ctrl+alt+F1 through F6 does NOT bring up console immediately before or after you get a black screen. As a result, commands to change drivers as a workaround will not work with this bug.

Hardware Specs:
ATI Radeon 9200 SE video card
Compaq P1100 21' monitor and Acer 54e monitor
ASUS K8V SE Deluxe mobo
AMD Athlon XP 64 (I only load the 386 OS on to it, though)
512mb RAM.

Bug filed and acknowledged as "Critical" by Ubuntu.  Still debate as to whether this is limited to ATI cards.
[https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

If you're experiencing the same problem, please file a report bug with launchpad, above.  Ubuntu Developers need to get a sense of how widespread this problem is. Don't forget to note your hardware specs, specifically your video card, monitor, CPU and which Ubuntu CD you're using (ie 32 vs 64).

Update:
[Bug #67487]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/67487") has found a couple of workarounds for this particular bug.  Here is one that worked for me:

1) Boot the LiveCD.  When you get to the Grub menu, hit F6.  

2) F6 will bring up a long text boot command.  At the end of the boot command, simply add: break=bottom 

 3) Hit 'Enter' and the CD will boot .  Wait for the (initramfs) prompt.  At the prompt type:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

4) Hit 'Enter' and at the next prompt type: exit

You should now boot in to a vesa desktop.  **Do this at your own risk.  No warranties.** Check the above bug report for a couple of other workarounds. If this does work for you, please still file a bug report at launchpad.  Note: the Alternative CD Install also works for most people (not all) who can't boot in to the Regular CD's Live Desktop to Install.

---

### Post by wpshooter on 2006-10-20
Did you check the integrity of your Ubuntu CD by running the verification function on the Ubuntu initial boot screen menu ?

Have you tried booting in the safe video mode ?

If that does not work, then download and try the ALTERNATE/TEXT based version of Ubuntu.

Good luck.

---

### Post by Rory on 2006-10-20
Yes, the integrity of the dics and the MIDSUMS are fine.  

What commands do I use to boot in via Safe Mode?  Or any other mode that might help the graphics issue.  

Thanks for your response.

Anyone else have any ideas?

Thanks.
Rory

---

### Post by Rory on 2006-10-20
By the way, if safe mode is the second boot option, I've tried this with the same result.  It's odd how the graphical Ubuntu screen is up with then it changes when it goes to boot in to the desktop in the final moment.

---

### Post by wpshooter on 2006-10-20
Might want to try the ALTERNATE CD.

I am going to be trying the DESKTOP CD tonight myself.  I have had problems during the installation before and am anxious to see if they have cured any of these yet.

Good luck.

---

### Post by Rory on 2006-10-21
Anyone have any ideas as to how I might get in to the CD and bypass this graphical problem.  I've never had this problem with a Linux distro CD before and I've been using Linux since SuSE 9.0.  Something funky is going on.

---

### Post by Rory on 2006-10-22
UPDATE

Short story: no luck

Longer story: I downloaded the 6.10 RC DVD.  It booted, the boot splash screen moved through its paces, the screen went black and the white cursor appeared in the top left corner (normal), and then it went to click over in to the desktop or GDM login (I haven't seen it to know what the next step is) and...  BLACK SCREEN...  again. 

I've tried the first Start/Install default option.  I've tried the second Safe Graphics Mode option.  I used the F4 VGA mode and tried different modes with the first two install options, including 16bit VGA (I usually do 32) and different screen resolutions.  No luck.  

Same thing happens each time.  Now, the Text Install starts up fine (on both the DVD and Alternate CD).  But, without wiping my drive and doing a full install, I won't know if it's going to work, which makes me nervous, as you could understand, given my lack of luck, so far.

So, I'm stuck but trying hard to resolve this.  Anyone have any ideas?  A different boot line, for example.  

And can anyone guess the root of this problem?  An Xorg issue?  Not good.

Thanks,
Rory

---

### Post by Rory on 2006-10-22
I've done some more testing and I believe this is a real bug in the upcoming Edgy release.

I've used two monitors: Acer 54e (pretty generic monitor that works with everything) and my Compaq P1100, which is a more exotic 21" monitor.  

I ran the Dapper 6.06 CD with both monitors.  
-The default Start/Install did not boot in to the desktop, going black after the boot sequence.  
-The Safe Graphics mode did work with the Acer 54e monitor.  It also worked with the Compaq P1100 when I chose VGA (I used the 768x1024 16 mode).  

The Edgy 6.10 CD does not work with either monitor, in either the default or the Safe Graphics mode, with or without using VGA mode options.  It just doesn't boot in to the Desktop (formerly called Live CD).  

Something has changed between Dapper and Edgy that will make it difficult for a certain number of people to boot in to the Desktop off the CD when checking out Ubuntu starting on Oct. 26th. 

I'd like to try to find a workaround and eliminate issues, if people are willing to help me. 

Would booting in with a "vesa" option in the boot parameters be an option?  If so, how would I do this?  Any other ideas?

---

### Post by Rory on 2006-10-23
update: Bug now filed.  [https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

Any ideas?

---

### Post by Flat Cat on 2006-10-23
I had a similar problem. I must have tried to install the program 10 times. The screen went black at about the same place. Sometimes I would get a Ubuntu splash screen. Very frustrating. It acted like it was a video driver problem.

I then downloaded the alterative CD, which is a step by step method and not that user friendly as the live original CD. At the place where it asked to partition the disk, I said yes and to also format the drive, which would erase Windows. Might as well be committed.

Well the alternate disk installed well, and went almost through the entire process of installing the program, but locked up at 64%. There was no more black screen. Apparently with Windows gone, there was no conflicting video drivers.

I then reverted back to the ORIGINAL live CD and it locked up at 65% as well. I re-burned the CD at a slower speed and used the original live CD and had no problems. All installed now. I think it also did not like a blank music CD. I went and purchased a data CD and that seemed to help as well.

Next: Onto the WIFI.

---

### Post by nixnoob on 2006-10-27
I also have the blank screen problem. After booting with nearly every option I get a blank/black screen where the login screen would usually be. Nothing I can do after that except reset. 

I'm running an Ati 9800 pro, with a 19" LCD using DVI.

Since this occurs using the final "release" CD, am I correct to assume that a fix/new CD image is unlikely to appear soon?

---

### Post by Rory on 2006-10-27
If you're experiencing the same problem, please file the details with the Launchpad Bug (link in the first post in this thread).  Ubuntu Developers need to get a sense of how widespread this problem is.

---

### Post by scotty32 on 2006-10-27
am not sure if am facing the same problem or not

but it seems to sound like it.

i tried upgrading from Dapper to Edgy, i was bored waitin an hour for the upgrade so i was pissin bout, i was addin Armok to a desktop panel and my system locked up (i was near the end of the  upgrade so i dunno if it was the panel, or the upgrade that locked up my pc)

i restarted, it booted with the dapper bootup splash screen, loaded everythin, went black - but never loaded the login manager

as others have said, i get a black screen with a white cursor and can type any random things i like - doesnt seem to do anything.

if i boot in recovery mode it stops on loadin my USB hub (guess cose its the last thing) and am allowed to type random crap like the other way.

tried on diff kernal versions in my grub - doesnt do out

as others have said, i have an ATI too.... a Radeon 8500 DV

is it a bug in edgy or have i failed the upgrade?

---

### Post by rjtd on 2006-10-28
I upgraded Dapper to Edgy and I have the black screen after Splash too :(
I'm using a Nvidia Geforce4MX, and I already tried vesa and nvidia drivers.

---

### Post by ArcturusM51 on 2006-10-29
When you(re in front the black screen (after you have heared the sound from login panel), press ctr + alt + F6 and in the xorg.conf file chosse vesa driver instead of ati or nvidia. Add also in device section : Option "MonitorLayout" "LVDS,TMDS". Register the file and press ctr + alt + f7 to go to xwindow and the press ctr +alt +backspace to restart.

---

### Post by Rory on 2006-10-29
With this bug, pressing Ctrl-Alt+F1 through F6 does not appear to bring you to console.  If this works for anyone else, *after* the usplash finishes and you hit the Black Ubuntu Screen of Death, please post here.

---

### Post by Aikon- on 2006-10-29
I have experienced the same problem:

AthlonXP 2500+
ATI Radeon 9600XT
ABIT NF7-S motherboard

As with you, I am anxious to install using the alternate CD as it seems to imply that its not going to work =/

---

### Post by grkravi on 2006-10-29
> **Rory said:**
> Yes, the integrity of the dics and the MIDSUMS are fine.  

What commands do I use to boot in via Safe Mode?  Or any other mode that might help the graphics issue.  

Thanks for your response.

Anyone else have any ideas?

Thanks.
Rory

I am having the same problem...i am using Dell Inspiron 5160 laptop and seems Edgy doesnt have the Vesa driver...reinstalled Dapper. I was able to install from the same iso image into one of my virtual machines.

---

### Post by fishbolt on 2006-10-30
I've encountered this bug on several machines and I know what's wrong. Jump to the text console (ctrl-alt-F1). cd to /etc/X11. vim the xorg.conf file. Look for the monitor resolutions. You'll see the first entry is "1680x1680" which is a square and complete nonsense. I had to delete both the 1680x1680 and the next entry after that to make it work. I deleted them for all bit depths since I didn't know which one was right.

Two alternate fixes: I don't have this problem with the DVI interface, only the VGA one. Also, you can try to insert your display's actual native resolution instead, this also worked for me (1920x1200).

---

### Post by fishbolt on 2006-10-30
I forgot the basics: you need to "sudo bash" before editing. Also, once you make the edit, you'll need to restart the gdm. I did this with the brute force approach:

init 1
init 5

---

### Post by Aikon- on 2006-10-30
> **fishbolt said:**
> I've encountered this bug on several machines and I know what's wrong. Jump to the text console (ctrl-alt-F1). cd to /etc/X11. vim the xorg.conf file. Look for the monitor resolutions. You'll see the first entry is "1680x1680" which is a square and complete nonsense. I had to delete both the 1680x1680 and the next entry after that to make it work. I deleted them for all bit depths since I didn't know which one was right.

Two alternate fixes: I don't have this problem with the DVI interface, only the VGA one. Also, you can try to insert your display's actual native resolution instead, this also worked for me (1920x1200).

Thanks for trying to lend a hand, fishbolt.  Unfortunately the problem with this particular error that we've been receiving is that once we've reached Ubuntu's BSOD (where B is for "Black"), we ***can't*** get to a terminal by using ctrl-alt-f1 through ctrl-alt-f6; no keystrokes have any effect.

-Aikon

---

### Post by sloggerkhan on 2006-10-30
I think I am having this problem. My screen blanks after boot screen of edgy install disk. Know it's running because of sound effects. Setting custom resolution appears to only apply to the loading screen and not the gdm session. External video out doesn't help: apparently it's switching to resolution beyond my monitor's capability.

Consequently, I can't use install disk, which sucks because the distro upgrade sequence is really buggy.

---

### Post by Handssolow on 2006-10-31
I'm having the same problem with a fresh install of Edgy on a new HD (with the Windows HD disconnected) on my wife's PC. It's ubuntu-6.10-desktop-i386.iso which I downloaded last week.

System Asus A7V880 AMD Athlon 2.4Ghz 1Gb Ram Radeon 9600
 
Like others eventually the screen goes black I then briefly get a message "out of range" and then a black screen again. Looks like a graphics configuration problem. 

Sometimes if I time the ctrl+alt+f6 when the solid orange fills the slot or this Ubuntu screen disappears, I can get a command line but no sooner have I started to type, about 10 seconds later the black screen reappears.

Therefore I'm not able to access xorg.conf.

Kubuntu 6.10 doesn't load either.

Ok I can get Dapper on but it's got an old Linksys Broadcom card and I only want to sort out the wireless once.

Any new solutions?

---

### Post by Handssolow on 2006-10-31
No change. Just tried a different monitor, a Samsung Syncmaster 940 MW TV that's got a DVI input, same results, a final black screen though this time no "out of range message".

---

### Post by craigi on 2006-10-31
I've tried using the live CDs for both Ubuntu and Xubuntu with the same results.  I see the loading screen fine, but when it tries to boot into GDM, my screen remains black with just a little line of video at the very top.

I've been reading these forums and have tried different things and discovered hitting F4 at the CD boot screen.  I was able to select 1024x768/16b and using this I was able to get into Gnome to install Ubuntu.

After the installation, I booted from the hard drive and the same thing happens now with Ubuntu installed.  When I am at the black screen, I can't CTRL-ATL-F1 or anything.  When I try, it either does nothing or it changes my screen color to red and freezes the machine.

I have a GeForce6800 DVI'd to a Viewsonic LCD 21".

---

### Post by Handssolow on 2006-10-31
Nothing really new.

It's very frustrating though. If I time a press of crt+alt+f4 until just after the Ubuntu screen with full slot has disappeared and when there's still a flashing _ in the top left hand corner, I can access a command line. I even managed to type "help" and get a full screen of information.

But I've still found nothing to stop the disappearance of this command line screen after about 5 to 10 seconds. No time to input much else.

---

### Post by sloggerkhan on 2006-11-01
Hey everyone. We all have ATI cards, no? Guessing someone forgot to check ATI support on the CD release, or somehow ATI cards trigger a bad default setting.

EDIT: Most of the people with this problems seem to have ATI+AMD... not just ATI.

Update:
Workaround: getting to console:
Suggestion of removing splash from boot line (see launchpad [https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487) ) 

GDM monitor died, but it did let me get into consoles on the other x-windows, which didn't work with splash in the line. I checked out the xorg.conf, and it set the setting under device that normally reads driver "fglrx" (for ati proprietary on my comp) said "ati". I have never seen/had a working x with "ati" listed under driver. (Is this the driver for non proprietary?) That's probably the problem. Anyhow, it seemed ot work by changing it back to a non-hardware driver. What I don't understand is why everyone I know with an Intel doesn't have this problem and everyone I know with an AMD does.

Anyhow, that should allow people to work around and do a custom xorg.conf ... for the live installer.

---

### Post by sloggerkhan on 2006-11-01
Yeah, using this method you can change your display driver for the live CD to vesa, and then reload gdm, which will run, though somewhat slowly (IMO). It checked out.

So pretty much at boot screen, you hit f6 or whichever button brings up custom boot line. 

Then delete the "[COLOR="Blue"]splash[/COLOR]" from it. Hit enter. 

Sit there while it looks like it's doing nothing, eventually some console stuff will roll past, it will switch to screen 7, which will then power off. 

At this point you have use of your console screens still, thankfully. ([COLOR="Lime"]ctrl-alt-f1[/COLOR]) then change xorg.conf to use [COLOR="Blue"]vesa[/COLOR] 

([COLOR="Blue"]sudo nano /etc/X11/xorg.conf[/COLOR]). Change this by adding a [COLOR="Blue"]load "vesa"[/COLOR] under [COLOR="Blue"]module[/COLOR] section, the same section as load glx and dri and all the other ones. 

next, under "Device" section:

change [COLOR="Blue"]Driver "ati"[/COLOR] to [COLOR="Blue"]Driver "vesa"[/COLOR] and write out the changes.

go back to screen 7 ([COLOR="Lime"]ctrl+alt-f7[/COLOR]) and hit [COLOR="Lime"]ctrl-alt-bkspc[/COLOR] to reload gmd. 

My machine then loaded a laggy vesa powered gdm session @ 1400x1050 res (who knows how it came up with that res, possible I didn't enter vesa stuff correctly in xorg.conf) which worked fine until I tried to switch resolutions, which made it crash again.

Anyhow, I guess that gets the live cd "working."

---

### Post by Handssolow on 2006-11-01
No success after another hour working on my wife's PC.

Yes f6 gets a boot line but I not able halt the inexorable final destination of the black screen, black hole more like.

---

### Post by sloggerkhan on 2006-11-01
Handss, can you post specs? And you are supposed to get a blank screen still,  on my comp the difference was that I was able to switch to an active console after, whereas without modifying the boot line it all just died.

---

### Post by Handssolow on 2006-11-02
The is about work in progress with this problem. I did register with launchpad but not been able to post there for some reason.

I've got Edgy to load from the live CD on my wife's PC with an AMD 2.4GHz Athlon mobile and ATI Radeon 9600 x4 AGP card.

The problem is described here. I'm not sure If the cut and paste has worked.

[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/67487](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/67487)

On the first screen I used f6 and just altered the number after boot to 480000 (800x600) for no particular reason.

I then followed the advice to press mostly alt+SysRg perhaps some ctrl d when the screen went black and eventually Edgy started to load slowley.

[https://wiki.ubuntu.com/TriagingXBugs](https://wiki.ubuntu.com/TriagingXBugs)

I then was able to access a terminal and in xorg.conf change the driver from ati to vesa, save and choose to install Edgy as I've been typing this.

It didn't shut down without further help.

I've been able reboot from the installed Edgy, vesa driver and on the small Belinea  10153 monitor its giving 1024 x768 at 76 Hz.

Hope this helps others but it was a struggle.

I hope my install wasn't corrupted.

---

### Post by Stannly on 2006-11-02
ive had a similar problem, i tryed installing the alternative package text instal and it worked but had to go into safe mode console and reconfigure gfx to vesa to get the gfx to work, but when i tried to login it just went to a blank screen and took me back to the login page

---

### Post by spandon on 2006-11-02
Hi,
Had the same problem, I got round it by:
Try the following:
Live CD.
when the initial screen appears, press Escape, then enter
**boot: vga 771 noapic nolapic **
**If that works** 
or installation, use Alternative CD use 
**Install vga771 noapic nolapic**
Worked for me, Breezy and Dapper worked fine without these commands for the Desktop, but needed them on Breezy for laptop
Hope this helps
Don

---

### Post by sloggerkhan on 2006-11-02
Those commands (771, noapic, lapic) aren't working for all. I can't speak for alternate instal disc, tho.

---

### Post by jerrylamos on 2006-11-02
6.10 CD verified, runs on laptop IBM Thinkpad, but not on IBM Net Vista 8303-SB2, Pentium 4, 2.0 GHZ, 512MB storage, Intel 82845G Graphics Controller.

Windows XP Professional reports max res 2048x1536 16 bit, I usually run 1024x728 32 bit. Sony Multiscan 15sf monitor.

On CD live (I hope) using sudo dpkg-reconfigure xserver-xorg with any number of the available drivers including i810 and vesa get all kinds of errors reported example "No video bios modes for chosen depth" on i810, and "No matching modes" on vesa.

In particular, with resolutions (*) for 1024x768, 800x640, 640x480 get "cannot open /dev/wacom no such file".

So with resolutions (*) for everything except 1024.., 800.., 640 Edgy came up in 640x480 mode.  System Preferences Display only shows 640x480 available.  Suddenly it's 1982 screen mode.  Bummer.  Yes, Firefox worked.

Now I have a USB memory on the system where I could put a driver if anyone in Ubuntu knows which one and how to do it, and how to get the CD to find it.  

For that matter the 6.10 iso is on my desktop on my older scratch built system running Dapper, if anyone knows how to modify the image.

Any ideas anyone?
:evil:

---

### Post by legolas on 2006-11-03
I have the same problem on Dapper when I switch users.  I get back to my logged in screen if I type in my password and hit return at the black screen.  Sometimes it takes me a couple times just typing in my password and return over and over again, but eventually it kicks you into your GUI.  This is hardly a fix though.

---

### Post by Crayz9000 on 2006-11-09
I'd just like to chime in that I've managed to unintentionally duplicate this black screen issue with an IBM Thinkpad T21 (Savage IV-MX, savage driver) and Edgy.

This is from a fresh install (in text mode) using the alternative CD.

I rebooted into single-user mode when I got the black screen (keyboard was completely unresponsive -- even Magic SysRq didn't do anything!) and first ran dpkg-reconfigure xserver-xorg to no effect. I then went in, removed the lines for the spurious devices like the Wacom and Synaptics touchpads. No effect. Finally I went in and changed the savage driver to vesa and was able to get it to start.

I was not able to get any logs from when it would lock up, however, because it would do it so fast that nothing got logged (there were only a bunch of ^@s when I looked at my Xorg.0.log in nano).

I had a similar problem when installing on a Thinkpad 600, but that problem went away after running dpkg-reconfigure and manually cleaning up the xorg.conf.

---

### Post by cwmoser on 2006-11-18
I'm disappointed that I could not get Ubuntu Edgy to install on my desktop.  Installed fine on my Laptop though.  My desktop used an ATI 9550.

BTW, since I cannot get Ubuntu Edgy to run on my Desktop PC, what other distro is almost as good as Ubuntu?

Carl
[email]Carl@CarteBlanc.com[/email]

---

### Post by Rory on 2006-11-19
Carl, 

[Bug #67487]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/67487") has found a couple of workarounds for this particular bug.  Here is one that worked for me:

1) Boot the LiveCD.  When you get to the Grub menu, hit F6.  

2) F6 will bring up a long text boot command.  At the end of the boot command, simply add: break=bottom 

 3) Hit 'Enter' and the CD will boot .  Wait for the (initramfs) prompt.  At the prompt type:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

4) Hit 'Enter' and at the next prompt type: exit

You should now boot in to a vesa desktop.  **Do this at your own risk.  No warranties.**  Check the above bug report for a couple of other workarounds.  Note: the Alternative CD Install also works for most people (not all) who can't boot in to the LiveCD.

Carl, in terms of other distros that are "almost as good as Ubuntu," there are many (sorry, ubuntu fanboys).  In many ways, both Fedora and OpenSuSE are far more mature than Ubuntu, although I still prefer Ubuntu and I'm staying away from OpenSuSE now because of the deal that Novell just did with Microsoft.  But, they are two good examples of excellent distros with strong communities and lots of support.  

Hopefully, the Ubuntu Devs will become more aggressive in rolling out actual fixes for these critical bugs, but they are paying attention and are trying to deal with the Xorg issues that are causing many people problems.

---

### Post by spandon on 2006-11-19
Hi,
[B]Sorry, my previous post was incorrect, have just rerun the live cd on both machines, using the details below and both loaded with no further trouble
[/B]
I had similar problems with the Edgy (ubuntu 6.10)Live Cd on two of my machines (laptop and a desktop) both had ati cards.
I did the following to load the live cd and then to install:

**Live CD**
when the booting the disk, at the first, press escape, you will then get a message stating that you are leaving the graphical boot etc, press enter.
at the boot: prompt enter
**live vga=771 noapic nolapic** (exactly as written) and press return.
the disk then loads up edgy and I get a screen resolution of 1280x1024 plus alternatives.

If this works and you want to install, then you have to use the **Alternative CD**, and to install it, at the boot: prompt enter
**install vga=771 noapic nolapic**, then edgy installs.

This worked for me, give it a try using the Live CD, if this works then the installation will also work (using the Alt CD)
Good luck
Don

---

