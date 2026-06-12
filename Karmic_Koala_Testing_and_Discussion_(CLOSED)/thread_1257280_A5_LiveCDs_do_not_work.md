---
title: "A5 LiveCDs do not work"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-09-03
I downloaded the 32bit CD first and it gets to the GDM login screen and loops.

The 64bit version was downloaded second and gets to the login screen and freezes.

Both of these .iso md5sums checked out perfect.

Because I use 64bit normally, I used the install option and installed A5.  It went on a 2 partition installation of A4 that became unbootable 2 days ago after an update.

Would not boot but I did go through the recovery boot 3 (fsck and changing some root permissions) times and did get to the login where it just looped.  I am back on my usual 9.04 OS and will edit the Xorg file for the vesa driver for my ATI card and it will probably boot.

I will also try the 32bit CD for installation as soon as i figure out where I want the clean install to go on my 32bit dedicated drive.

---

### Post by taavikko on 2009-09-03
They will not work on the account of bug 419126
Everyone running ATI GPU r600 or higher is affected.

Alpha releases are just a snapshot of the repos, milestones.

---

### Post by ranch hand on 2009-09-03
> **taavikko said:**
> They will not work on the account of bug 419126
Everyone running ATI GPU r600 or higher is affected.

Alpha releases are just a snapshot of the repos, milestones.
That is me for sure.

I have the first one I installed on 64bit running.

Installed a second one and think that I did all the same things to it but it does not work at all.

I changed the /root permissions, added the xorg.conf file (DRI  0 - copied from new working install).  Tried to boot and it froze at the login screen.  Remembered that I had updated in the recovery terminal on the 1st one so did that.

Now all I get is the message about having to get the kernal up first.

---

### Post by jerrylamos on 2009-09-03
A5 CD doesn't get past the first boot menu on IBM ThinkCentre i845 video graphics.  Select boot or check the CD or whatever, the CD whirls a bit and quits.  Select anything, CD whirls and quits.

Same CD does boot, does check CD for errors, and boot on IBM Thinkpad T40 ati video graphics.  It did get a crash in modprobe which I reported.

Jerry

---

### Post by ranch hand on 2009-09-03
I just did a dist-upgrade on a 32bit 9.04 to 9.10 no problem works great.  Updated another to current no problem and a CD install over the root partition of a clean install A4 no problem.

What ever the problem is does not seem to be effecting the 32bit stuff near as bad as the 64bit.

---

### Post by ronacc on 2009-09-03
I know it's not much help but my 64bit install with an nvidia 7600gt (185.18 driver) is working ok . updated last night and about 2 hrs ago reboots no problem , so it does seem to be ATI related .

---

### Post by ELD on 2009-09-04
So it is still borked for a lot of ATi users then, like myself with a HD4850? This has been going on for fracking ages now.

---

### Post by ranch hand on 2009-09-04
> **ELD said:**
> So it is still borked for a lot of ATi users then, like myself with a HD4850? This has been going on for fracking ages now.
Yes it is getting kind of old.  I am thinking of getting a different card.

---

### Post by rbmorse on 2009-09-04
If it really need to run A5 on your box with an ATI HD series GPU, load the "VESA" driver and go with that.   You won't have hardware accelerated anything, but it will work.

---

### Post by ELD on 2009-09-04
I haven't been able to boot for well over a week, i have a nvidia card in my "tobuy list" since their drivers are better anyway i thought it would be worth it, will take me a good few months to save back for it though :(

---

### Post by ranch hand on 2009-09-04
> **rbmorse said:**
> If it really need to run A5 on your box with an ATI HD series GPU, load the "VESA" driver and go with that.   You won't have hardware accelerated anything, but it will work.
I have A5 running on my box and yes I am using the vesa driver.  I don't have any use for the silly compiz stuff anyway.

It would, however, be nice if the live CD would work.  I had no trouble using the "install ubuntu" choice in the menu.  It worked great.

I even have all 4 of my 32bit 9.10s working this morning.  The 64bit stuff will have to wait and I am pretty sure that one of them is actually toast.

---

### Post by taavikko on 2009-09-04
> **ELD said:**
> So it is still borked for a lot of ATi users then, like myself with a HD4850? This has been going on for fracking ages now.

Not that long...

It would be easier to just use an older installation media, than to trying to force install on alpha5. Which in any way isn't supposed to bring magic fixes to some issues
just a snapshot of repos.

Upstream is working hard on drivers, it should improve with time.
Which then again is a luxury, few of us can't afford. but they should then stick with more stable releases.

If using karmic and applying the upgrades, the issue will arise, to fix, disable DRI in xorg.conf.

---

### Post by Lem on 2009-09-04
Could be worse - I have an nvidia 8200 IGP and both A4 and A5 will not even get as far as installing. Fails to staret x for the installer gui, even in safe graphics mode. A2 worked fine.

---

### Post by ranch hand on 2009-09-04
I bet that A6 works.

It is about time for me to fool with my 64 bit installs and I may even salvage the "bad" one (if not - so what?).

I like the way this is going even with this rash of bugs.  This seems to be the time to have them to me.

I really think that 9.10 is going to be slick and fast.  10.04 should be nice and stable and slick and fast.

I am excited by the whole deal.

Right now it is a little rough.  If folks are using it as a production OS, well, they have been warned.

---

### Post by Lem on 2009-09-04
> **Lem said:**
> Could be worse - I have an nvidia 8200 IGP and both A4 and A5 will not even get as far as installing. Fails to staret x for the installer gui, even in safe graphics mode. A2 worked fine.

Workaround - Use alternative installer.

Will install and then fail at starting x.

sudo apt-get install nvidia-glx-185 

and then reboot

---

### Post by jerrylamos on 2009-09-04
> **rbmorse said:**
> If it really need to run A5 on your box with an ATI HD series GPU, load the "VESA" driver and go with that.   You won't have hardware accelerated anything, but it will work.

On karmic, GtkPerf video benchmark "vesa" has usually been faster than the "accelerated" driver on my four test pc's.  I assumed it was because not all these "accelerated" features had been debugged...."vesa" might not be so bad in comparison.

Jerry

---

### Post by tsger on 2009-09-05
Read how I resolved the ATI looping GDM issue [**HERE**]("http://ubuntuforums.org/showpost.php?p=7902691&postcount=11")

---

### Post by SeePU on 2009-09-05
What if you don't even know what the problem is?   

The LiveCD, 32-bit version, boots up okay and I can select wireless and connect (horrible utility, btw, though, as I can only find the one in the far right corner to log on - is this a Gnome thing?!?) but after a short while, the entire system freezes!

This is on a Thinkpad T41 that has an ATI Radeon 9000 video card.  I believe I have to use the open source driver so I thought there wouldn't be much of an issue with the configuration.

---

### Post by ranch hand on 2009-09-09
Bummer, just tried the build for today and it won't boot and the installer/partitioner from the "install ubuntu" menu item doesn't work either.

I'll file a bug on this.

Edit;
Well I would file a bug on this but can't seem to find a combination that fits launchpad.  Is that the wrong place to file this?  Can't see any info on the daily build or A5 download sites as to where to report problems.

---

### Post by jerrylamos on 2009-09-09
A5 CD has same md5sum as Ubuntu Daily Build for date 20090902.  Would not boot and run on my Thinkpad R31 with i830 graphics or ThinkCentre with i845 graphics nohow.  It did boot on my Compaq Presario ati and Thinkpad T40 ati.  Some users report certain ati pc's dont boot either.

Daily Build 20090905 from [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/) would boot & install successfully only if:

CD F6 on top line, esc, then replace splash with
nomodeset single

That boots recovery mode, then at the recovery mode menu go down arrow to root prompt, then

nano /etc/X11/xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
Ctrl-o
enter
Ctrl-x
resume boot

CD booted successfully rather slow compared to previous ubuntu CD's
installed really slow compared to previous CD's, I didn't set an hourglass to time it.

After install & boot,

select recovery mode
e on linux line
replace splash with nomodeset
then continue boot

At recovery mode menu do the same nano as above.  This time it will be permanent.

Resume boot. If boot is successful like my two were, at a terminal session
sudo chmod 644 /boot/grub/grub.cfg
sudo gedit /boot/grub/grub.cfg
add nomodeset to the end of the regular boot linux line & the recovery boot linux line
save

At this point the intel machines both booted.  Do note an update or anything else that does an update to grub.cfg I have to add nomodeset again.  If you put "quiet nomodeset" in /etc/default/grub it might save having to do it for the regular boot line, but I still had to add it for the recovery boot line.

Yes there are launchpad bugs on this for the last 2 months.  I don't hold any expectations this will be fixed for beta.  The simplest fix would be to blacklist intel drivers with the bug for intel.modeset=1, i.e. force nomodeset or intel.modeset=0.  I still have to use Driver "vesa".

The last time the i845 would boot without all this mess was A2.

Jerry

Good luck.

Jerry

---

### Post by VMC on 2009-09-09
> **jerrylamos said:**
> 
nano /etc/X11/xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
Ctrl-o
enter
Ctrl-x
resume boot


Hey Jerry, when you use the "vesa" mode do you get 1024x768? I can only get 800x600. Or rather how do you get 1024 using "vesa"? Thanks, Vern

---

### Post by jerrylamos on 2009-09-10
> **VMC said:**
> Hey Jerry, when you use the "vesa" mode do you get 1024x768? I can only get 800x600. Or rather how do you get 1024 using "vesa"? Thanks, Vern

On IBM Thinkpad R31 i830 I do get 1024x768 with vesa.  'Way back when I did check the bios choices to make sure to use the most memory the video setup would.  On IBM ThinkCentre i845 I get 1280x1024 with vesa, same thing, check the bios video memory choices.

Jerry

---

### Post by VMC on 2009-09-11
> **jerrylamos said:**
> On IBM Thinkpad R31 i830 I do get 1024x768 with vesa.  'Way back when I did check the bios choices to make sure to use the most memory the video setup would.  On IBM ThinkCentre i845 I get 1280x1024 with vesa, same thing, check the bios video memory choices.

Jerry

That was my problem. I had video memory set at 1mb. I changed to the only other setting, 8mb. That did it. Now though when I logoff or shutdown I get a weird color light show of browns and stripes. Logging on is ok. And jaunty on shutdown is ok.

---

