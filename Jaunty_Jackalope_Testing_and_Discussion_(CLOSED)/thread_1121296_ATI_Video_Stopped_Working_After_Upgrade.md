---
title: "ATI Video Stopped Working After Upgrade"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by suavecu on 2009-04-09
So I've been looking for awhile now, and I'm sure it's here, but I can't find it. As a result, a link will do if you know where the solution is.

With that being said, I just upgraded to Jaunty Jackalope (great name, btw) and when it happened, it removed the proprietary ATI driver (fglrx). I figured, when it was done upgrading, I could just re-install the package from the command line and all would be ok. As a result, after the install I started it in recovery mode with network support and ran the following command:

> sudo apt-get install fglrx

The package installed, I restarted, and now I just get a garbled screen. So, I clearly missed a step and can't figure out what it is.

Any help would be greatly appreciated.

Thanks

---

### Post by FrankT-Qc on 2009-04-09
Under Intrepid, I had the same problem... A short time after the official release, an update hit the repos for ati and everything was ok...

By the way, have you looked at ATI web site, they usually have a more recent version... There's a pretty cool one sitting there right now...

---

### Post by sLiFtIaK on 2009-04-10
I am using Nvidia with no problem :)

---

### Post by suavecu on 2009-04-10
slifiak - what card do you have?

Frank T-QC - is there a way to navigate to it via command line?

---

### Post by Cerberus108 on 2009-04-10
I had the same problem, solved by entering single-user mode (the second entry below the regular one in grub) and giving the command: 

```
sudo aticonfig --initial -f
```

It will update your X11 configuration file, hopefully solving the problem. Let me know if you had some luck with it!

---

### Post by suavecu on 2009-04-10
When I try that it says:

> aticonfig: No supported adapters detected

I have the ATI All-In-Wonder 9600 series (I believe it's 9600).

---

### Post by suavecu on 2009-04-10
ya it is. When I run, lspci -v this guy appears:

> ATI Technologies Inc RV350 AP [Radeon 9600]
Subsytem: ATI Technologies Inc Device 4723
etc
etc

---

### Post by Cerberus108 on 2009-04-10
Hmm.. That's a bit of a problem. Are you sure your GPU is supported by the fglrx driver? You could try the "ati" or "radeon" driver, just do:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to reset your configuration file, and then edit it:

```
sudo nano /etc/X11/xorg.conf
```

browse it until you reach the section "Device". Add a string beneath the title:

```
Driver "ati"
```
or
```
Driver "radeon"
```

then press CTRL+O to save it, and CTRL+X to exit the editor.

---

### Post by suavecu on 2009-04-10
How could I get the ATI driver via command line? Is it in a repository somewhere? I thought I was running fglrx before, but maybe I wasn't.

I'll give your stuff a try in a bit.

---

### Post by Cerberus108 on 2009-04-10
The ati and radeon drivers should be already installed in ubuntu.. Maybe you were using the vesa driver, which is a very poor one.. any luck anyway?

---

### Post by markbuntu on 2009-04-10
fglrx for jaunty is a pre-release version of the ati 9.4 driver. This driver and future drivers from ati will no longer supports rv300-500 cards which is anything older than the HD3xxx series. You can use the open source ati or radeon drivers which have full support for the 9600.

---

### Post by suavecu on 2009-04-10
Open Source driver did not work, fglrx did not work. What I've done now is download the driver with wget:

> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-3-x86.x86_64.run)

then turned it into a package:

> sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms 

sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg



Then installed the package:

> sudo dpkg -i xorg-driver-fglrx_8.593-0ubuntu1_i386.deb fglrx-kernel-source_8.593-0ubuntu1_i386.deb fglrx-amdcccle_8.593-0ubuntu1_i386.deb

That finally installed the driver, and now I have a new problem. My screen doesn't go black, it says input not supported, and I think that it has something to do with my now screwed up xorg.conf file.

This site has been helpful - [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

This one was helpful, but not for me - [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) 

as it apparently does not work with the ATI All-in-Wonder Radeon 9600 card.

---

### Post by suavecu on 2009-04-11
I'm getting nowhere fast. I should have never upgraded versions. Even if I try to put in an install cd 8.04 and try to re-install in safemode I get input not supported.

I hate this about Linux. It makes me want to buy a mac.

Why Novel can give me something that works with the card out of the box, but no wireless support, and ubuntu can give me wireless but no video is beyond me. I thought we were supposed to co-operate.

I'm venting, maybe the OEM install will help me get back to the beginning so that I don't have an expensive paper weight again.

That doesn't work either.

So at the moment I cannot run any install, I cannot find a driver that works, or instructions that get me there all because I upgraded to Jaunty. Time to re-think Operating Systems.

---

### Post by Cerberus108 on 2009-04-11
I agree about most of what you said. Beside the bogus cooperation, the ATI drivers affair is a mess. Personally, I have bought almost an year ago an HD 3650 card, and I've yet to have many, too many compiz effects work with ANY driver. I mean, my card is neither too old nor too new. It's the last time i buy an AMD/ATI component. Going back to your problem, all I can suggest you is to enter the "safe mode" and (after having fglrx installed) to run this command: 

```
sudo aticonfig --initial -f
```

Maybe this will fix something.

---

### Post by suavecu on 2009-04-11
ok, so I deleted all my xorg files because there were like 15 of them and they all didn't work.

Then I booted into safemode again, and ran xfix from the menu of options, which created a brand new xorg.conf file

Then I ran sudo aticonfig --initial -f

Then I ran startx and that still didn't work. I have attached the xorg.conf file to see if anyone can see anything.

I tried piping the output to a file, but that didn't work for some reason.

---

### Post by rbmorse on 2009-04-11
The latest version(s) of FGLRX (9.3, 9.4) do not support your video adapter. 

You can either stick with 9.2 (recommended) 

or

install the xserver-xorg-video-radeon package from repository. But, before you do that you have to COMPLETELY REMOVE EVERY SINGLE, STINKING TRACE OF FGLRX ON YOUR YOUR MACHINE (files, libraries, kernel modules). 

You might be able to clean FGLRX using Synapitc and the "completely remove" option, or apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source but I usually just end up reinstaling the operating system because it's quicker and easier.  

FGLRX taught me the value of maintaining /home in a separate partition.

BTW...with your card, if you do a clean install of Jaunty the installer should use the "radeon" driver by default.

---

### Post by markbuntu on 2009-04-11
If you used the installer then all you need to do to remove the driver is go to /usr/share/ati and run the uninstaller script fglrxuninstall.sh or something like that.

---

### Post by suavecu on 2009-04-11
> **rbmorse said:**
> The latest version(s) of FGLRX (9.3, 9.4) do not support your video adapter. 

You can either stick with 9.2 (recommended) 

or

install the xserver-xorg-video-radeon package from repository. But, before you do that you have to COMPLETELY REMOVE EVERY SINGLE, STINKING TRACE OF FGLRX ON YOUR YOUR MACHINE (files, libraries, kernel modules). 

You might be able to clean FGLRX using Synapitc and the "completely remove" option, or apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source but I usually just end up reinstaling the operating system because it's quicker and easier.  

FGLRX taught me the value of maintaining /home in a separate partition.

BTW...with your card, if you do a clean install of Jaunty the installer should use the "radeon" driver by default.

I would even go as fast as to re-install 8.04, but I cannot because the new disc doesn't have a text based installer, and of course the live disc that  I just burned no longer supports my video card.

I'll give these two suggestions a try.

---

### Post by amano on 2009-04-11
And please do not blame Ubuntu or Linux altogether when ATI decides to drop the support for your card. This is even mentioned in the release notes that fglrx doesn't work with older ATI cards anymore.

Blame ATI for their lousy mess.

It is not an Ubuntu problem, but a problem for all distros that ship the current X.org 1.6 release. Old ATI drivers don't work with it and the new ATI drivers dropped the support for your card.

Your best bet is to get rid of the fglrx and try to use the open source -ati driver. Just get rid of anything related to fglrx and delete your xorg.conf file. If you are lucky than it should auto-configure the system to use the -ati driver after a reboot.

And if you want to keep the fglrx drivers, you have to stick to Hardy or Inteprid. Blame ATI.

---

### Post by suavecu on 2009-04-11
I removed everything that said fglrx, installed the radeon package, and then it just gives my monitor no signal and shuts off. Any other thoughts?

And don't give me the don't blame Ubuntu and or Linux. I have one OS that will show video, but no wireless, and Ubuntu all of sudden doesn't support video of any kind for me. I can't even re-install the Operating System because the disc doesn't have a text installer, and I just get a blank screen when it runs.

That's no different than the Mac's who force you to use a hardware. However, at least with Apple it's easy to find. I still haven't found anything that says this set of hardware will work or won't work with Ubuntu. If I would have known that my hardware wouldn't work, I would not have upgraded. But why would I think that my hardware would suddenly stop working when it previously worked without a problem. I'm not even asking for 3d acceleartion here, I just want to be able to see a desktop. It's ridiculous.

Anyone have any other ideas.

---

### Post by suavecu on 2009-04-11
Note I tried open source ati driver and that didn't seem to work either.

---

### Post by amano on 2009-04-11
What happens if you try to boot a live cd image?

---

### Post by suavecu on 2009-04-11
The Ubuntu screen with the status bar that goes back and forth shows up and then, when it should show something, the monitor says no signal and the monitor goes black. Same as if I just try to run it without going to single.

---

### Post by suavecu on 2009-04-11
is there a way I can get a log file out of this? My guess is that it thinks it is working. The worst part is everytime I test it (with the radeon) I can't get back to the terminial (startx) so I have to restart, reset the wireless over and over again :(

---

### Post by krazyd on 2009-04-11
Could you get an alternative installation CD and boot from that?

---

### Post by suavecu on 2009-04-12
I'll give that try once I can burn a blank cd again (I have them at work).

I have attached three files for anyone who's feeling quite randy today.

output-vga.txt - which shows the output from lspci | VGA
output-dpkg.txt - which shows the output from dpkg -l
xorg.conf - which shows my xorg.conf file

If anyone needs anything else, let me know.

Note: I have 2 /usr/lib/libGL.so.* files, but no libGL.so file (without a number after it).s Should I delete both of those, and how do I create a new one?

---

### Post by suavecu on 2009-04-12
Should I remove all the packages that have mesa in them, since some of them seem to be a part of the open source ATI driver?

---

### Post by BwackNinja on 2009-04-12
If you're still on jaunty, you won't get anything but the open source ATI driver working, so you'd want mesa. You might want to re-install them too:

libgl1-mesa-dri
libgl1-mesa-glx

I'd even suggest you move/delete your xorg.conf because it shouldn't be necessary with xserver 1.6 (unless you have some special needs).

Then I'd want to see your /var/log/Xorg.0.log (or /var/log/Xorg.0.log.old) to see where it is messing up. Then it should be straightforward to help you.

PS: I've got a rv370 (radeon X300 PCIE) and it works fine with the open source driver.

---

### Post by suavecu on 2009-04-12
Of course my cable provider sucks and I lose my signal right after that. Anyways, so I removed the radeon drivers. deleted the xorg.conf file. Rebooted. Re-installed the mesa drivers you mentioned. Rebooted. The started the computer up like normal. When it got to where the login screen should be it gave me the "Input not supported" box that kept bouncing around the screen. which is different than what it was doing before. I remember back in 05, something like that used to happen with the vesa driver. I'm wondering if it is because of the monitor resolution (1440 x 900). I used to have to install the proprietary drivers back then. Anyways, I've attached the log file you asked for (actually I think I attached it twice, once is a cat output piped to a file, but the log file is there regardless).

Monitor is Acer AL1913w

Thanks again everyone for all your help.

---

### Post by BwackNinja on 2009-04-12
looks like you are using the vesa driver right now...

When you said "Anyways, so I removed the radeon drivers." I was hoping you were talking about fglrx, but it seems you don't actually have the open source drivers installed.

Mesa is just the 3D portion of the driver

xf86-video-ati (the xserver-xorg-video-ati package along with xserver-xorg-video-radeon) is more of the main component. In your case, you could also try the radeonhd drivers because you have an r500 card, but I'd try that only if -ati doesn't work for you.

Just reinstall xserver-xorg-video-ati and xserver-xorg-video-radeon, then try again and send the Xorg.0.log.

---

### Post by suavecu on 2009-04-12
I installed the two packages you suggested. Rebooted. Started the computer like normal and it go to where the login screen should appear and the monitor showed "No signal" and turned back off (as it was doing before). Log file is attached.

---

### Post by BwackNinja on 2009-04-12
sorry for the delay~

491: (II) RADEON(0): Output VGA-1 using initial mode 1152x864

That line shows the problem, the resolution detected is way off.

for this you'd need just a simple xorg.conf that has your resolution in it. Just use the xorg.conf you had earlier and add in a line that says:

Modes        "1440x900" "1024x768"

in the "Screen" section under the Subsection Display that has "Depth 24" in it.

then you should be fine.

---

### Post by suavecu on 2009-04-12
do the permissions of the xorg.conf file need to be something specific?

Anyways, I added the line you suggested, where you suggested, and got the same problem. I've attached the log, and the xorg.conf file again.

I appreciate the help.

---

### Post by BwackNinja on 2009-04-12
Scoured the internet for a solution for a bit, but found nothing.

The log doesn't show any problems with your drivers as far as I can tell, it seems to be loading up right and setting the resolution correctly too.

(EE) RADEON(0): No connected devices found!

When probing for outputs seems to be the problem, and I don't know how to fix it. Its somehow not finding your monitor I think.

Just to check though, you're using a VGA cable, right? Only thing I've found is that Dual-Link DVI cables aren't supported by the open source driver.

---

### Post by suavecu on 2009-04-12
Any ideas?

---

### Post by suavecu on 2009-04-12
the card has a square output (maybe dvi) and the connector has two vga outputs, which you connect the vga cable to, and then connect the cable to the monitor. I'm assuming it is what you are talking about.

---

### Post by suavecu on 2009-04-12
So, with that thought in mind, I tried the the other VGA output connector on the cable and oddly enough, it works. Not sure why the other one would all of sudden stop working, but maybe the one I've had it connected to all this time was the "second" output for dual displays (there is no marker), and like you said it doesn't support dual monitors. Rebooted a second time, and it works.

You are my hero.

---

### Post by maphilli14 on 2009-04-13
Honestly I'm lazy and my head hurt after page 2 of this thread.  I will add that my Lenovo T60p with VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250] stopped giving me resolution options beyond 1280x720.  Which is a fairly good resolution, but I really miss the 16xx X xxx higher res!  :(

Mike

---

### Post by MALEADt on 2009-04-13
[ Deleted, only read first two pages of the thread ]

---

### Post by BwackNinja on 2009-04-13
> **maphilli14 said:**
> Honestly I'm lazy and my head hurt after page 2 of this thread.  I will add that my Lenovo T60p with VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250] stopped giving me resolution options beyond 1280x720.  Which is a fairly good resolution, but I really miss the 16xx X xxx higher res!  :(

Mike

xrandr --addmode VGA-0 1680x1050
xrandr --output VGA-0 --mode 1680x1050

that should do it. (assuming 1680x1050 was the resolution you were talking about)

---

### Post by maphilli14 on 2009-04-13
> **BwackNinja said:**
> xrandr --addmode VGA-0 1680x1050
xrandr --output VGA-0 --mode 1680x1050

that should do it. (assuming 1680x1050 was the resolution you were talking about)

BwakNinja, thanks much!  This is a handy trick.  I had been using the display prefs applet but it seems to max out at 1280x720 and errs off with this

```
xrandr --addmode VGA-0 1680x1200
xrandr: cannot find mode "1680x1200"

```

Perhaps this is a larger issue from somewhere?  What did happen do xorg?

Mik

---

### Post by BwackNinja on 2009-04-13
you'll need to use gtf to create a modeline then.

example, with 1360x768 @60hz

gtf 1360 768 60

which will output something like:

  # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

and copy everything that you get after "Modeline" (don't copy what I've posted) and enter it in

xrandr --newmode "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

then you can do:

xrandr --addmode VGA-0 1360x768_60.00

of course with the name of the mode that you set with xrandr --newmode.

---

### Post by Enicko on 2009-04-13
Had the same problem here. The very last note on the Jaunty update site seems to suggest this will be fixed with the official launch.  

It also seems like this is running rather hot at idle, I hope the driver smooths that out at well.  Sitting here in battery save mode this one is at 56C.  ATI Mobility 5700 on a thinkpad.

All this rockin out in 2d, going to be a ninja when the faucet of compiz love gets turned back on.

---

### Post by maphilli14 on 2009-04-13
> **Enicko said:**
> 
All this rockin out in 2d, going to be a ninja when the faucet of compiz love gets turned back on.

HEY HEY!  I like the way that sounds!  Yeah, that video mode seems messed:

```
miphilli@DRACO-V23:~$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 720, maximum 2048 x 768
VGA-0 disconnected (normal left inverted right x axis y axis)
   1680x1050_60.00   60.0  
LVDS connected 1280x720+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x720       59.9* 
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
miphilli@DRACO-V23:~$ xrandr --output VGA-0 --mode 1680x1050_60.00
xrandr: screen cannot be larger than 2048x768 (desired size 1680x1050)

```

---

