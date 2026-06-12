---
title: "installin 10.10"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by pjrandall on 2010-11-21
I just got a Tablet PC, and I installed Ubuntu on it.  But, problem is, I tried to install 10.10, and it would install properly, but it wouldn't load, just brought up the GRUB loader with a terminal prompt. I ended up having to install 7.04, and it works great. but I'd like to upgrade it. any suggestions?

---

### Post by Favux on 2010-11-22
Hi pjrandall,

It's probably the video chipset that's the problem.  Find out what it is:
```
lspci | grep VGA
```
I'll bet it's that Intel GMA whatever.  I think there's an update for it.

---

### Post by pjrandall on 2010-11-22
uh.... ok. How do I do all that? Sorry, I'm a newb. :P

---

### Post by pjrandall on 2010-11-22
> **Favux said:**
> Hi pjrandall,

It's probably the video chipset that's the problem.  Find out what it is:
```
lspci | grep VGA
```
I'll bet it's that Intel GMA whatever.  I think there's an update for it.
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

Those are the results I got from your code.

---

### Post by pontdecheruy on 2010-11-22
I'm running Ubuntu 10.4LTS since two months now,i'm happy with it but i can't update to ubuntu 10.10 maverick.It wont boot after i upgrade to 10.10.
Is there just because i didn't do clean installation for ubuntu on my **C:/** partition but it's installed within windows? Or some other reasons???
Please help, your help is appreciated!
Thanks in advance
A.F

---

### Post by lordpaladin on 2010-11-22
i made the same mistake with 10.10 64-bit dual booting with windows xp 32 bit
i freshly installed ubuntu on a partition with / as mount point, ext4 format, in the beginning and as primary
when i boot to ubuntu i get the grub terminal with prompt.
i just found out that i made a wrong installation procedure based from one of the persons who helped me here.
i should never installed the boot loader to the same partition where i will install ubuntu.
it should be on dev/sda of the hard disk on where you will install the ubuntu

now its working properly.

how it works

---

### Post by Favux on 2010-11-22
Hi pjrandall,

Well it isn't the GMA855, you have the Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03), otherwise the Intel 915GM.

Knowing that you can now search google:

site:ubuntuforums.org Intel 915GM

site:wiki.ubuntu.com Intel 915


Doesn't seem to be a problem with it in Maverick other than with Flash.

Still could be a suppose but not as likely.  Maybe the wireless card?  Try in a terminal:
```
lspci
```
and see what hardware you have.

---

### Post by pjrandall on 2010-11-22
> **Favux said:**
> Hi pjrandall,

Well it isn't the GMA855, you have the Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03), otherwise the Intel 915GM.

Knowing that you can now search google:

site:ubuntuforums.org Intel 915GM

site:wiki.ubuntu.com Intel 915


Doesn't seem to be a problem with it in Maverick other than with Flash.

Still could be a suppose but not as likely.  Maybe the wireless card?  Try in a terminal:
```
lspci
```and see what hardware you have.


Here are the terminal results.

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
10:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)

---

### Post by Favux on 2010-11-22
Nothing jumps out at me as a show stopper.  We need one of the install gurus to help.

Are you booting with just wireless or do you have an ethernet cable plugged in?

---

### Post by pjrandall on 2010-11-22
> **Favux said:**
> Nothing jumps out at me as a show stopper.  We need one of the install gurus to help.

Are you booting with just wireless or do you have an ethernet cable plugged in?
Wireless.

---

### Post by Favux on 2010-11-22
It's Intel wireless so that should be OK.  Sometimes Broadcom wireless is a problem, but you have Broadcom ethernet.  So I'm pretty much stumped.

Have you tried adding the kernel boot line options the installer gives you when you go to the menu rather than proceed?  If so you might also want to try:

edd=skipmbr

Or if that doesn't work, try:

edd=off

Some old BIOS's do not like the new way of finding the master boot record.

---

### Post by pjrandall on 2010-11-23
> **Favux said:**
> It's Intel wireless so that should be OK.  Sometimes Broadcom wireless is a problem, but you have Broadcom ethernet.  So I'm pretty much stumped.

Have you tried adding the kernel boot line options the installer gives you when you go to the menu rather than proceed?  If so you might also want to try:

edd=skipmbr

Or if that doesn't work, try:

edd=off

Some old BIOS's do not like the new way of finding the master boot record.
I'll give it a shot. 

Also, I thought I had a good idea, and tried to install Ubuntu in Windows via Wubi, and that failed too. It said something about "Unable to download (something, I forget what), and unable to download .iso." Am I doing something wrong?

---

### Post by Favux on 2010-11-23
I don't know, it'd be good to know the error message.  But just because you weren't able to download the iso in Windows shouldn't affect the install from your live CD.  You got that iso with your Desktop computer I suppose.

---

### Post by pjrandall on 2010-11-23
> **Favux said:**
> I don't know, it'd be good to know the error message.  But just because you weren't able to download the iso in Windows shouldn't affect the install from your live CD.  You got that iso with your Desktop computer I suppose.
Indeed. BTW, I really appreciate all the help.

---

### Post by pjrandall on 2010-11-23
I tried installing LinuxMint 10, just to see if it'd work. I got this screen after install. [http://picasaweb.google.com/lh/photo/Tw2nWJiKjUZnaHodB0bC3xn6T5Q83KlRQeGPrXtG64k?feat=directlink](http://picasaweb.google.com/lh/photo/Tw2nWJiKjUZnaHodB0bC3xn6T5Q83KlRQeGPrXtG64k?feat=directlink)

Also, I found out the message from before, it said 
ERROR: Out of Disk
GRUB RESCUE:

---

### Post by Favux on 2010-11-23
Hi pjrandall,

Well we're getting way outside my area of "expertise" such as it is, as I mentioned before.

But it kind of sounds like the problem is you are running out of disk space.  Do you have another OS installed on the tablet pc?  How big is the partition you are installing into?  Did you let the installer set up a swap file?

You can download Gparted if you want to look at your disk and see what's going on.

---

### Post by pjrandall on 2010-11-23
> **Favux said:**
> Hi pjrandall,

Well we're getting way outside my area of "expertise" such as it is, as I mentioned before.

But it kind of sounds like the problem is you are running out of disk space.  Do you have another OS installed on the tablet pc?  How big is the partition you are installing into?  Did you let the installer set up a swap file?

You can download Gparted if you want to look at your disk and see what's going on.

Well, I don't have any other OS's installed. I'm reformatting every time I try to reinstall. :P And I'm leaving about aa 2 gig swap file.

---

### Post by Favux on 2010-11-23
Sorry I'm stumped.  It usually isn't this hard.  Hopefully someone else can help.

---

### Post by pjrandall on 2010-11-23
OK, thanks for your help!

---

### Post by pjrandall on 2010-11-24
Well, I tried installing 10.04, and it works great! Don't know what was wrong, but it works great now. Thanks for the help.

---

### Post by Favux on 2010-11-24
Good!

Now if you need help setting the tablet up, digitizer and rotation, that I should be able to help you with.

---

### Post by pjrandall on 2010-11-25
> **Favux said:**
> Good!

Now if you need help setting the tablet up, digitizer and rotation, that I should be able to help you with.
Ubuntu natively supports the pen import, but it's not rotating when I flip the screen down. I think I like it better in landscape mode though. But I do wish I could use the other end of the stylus as an eraser, and the button as right mouse button, like it did when WinXP Tablet edition was on it.

---

### Post by Favux on 2010-11-25
We should be able to do that.  How many buttons does the stylus have?  One or two (might be a rocker switch).  Does the stylus have and eraser?  A sort of button on the other end of the stylus barrel that sort of depresses into it?

Also post the output of this command in a terminal:
```
xinput --list
```

---

### Post by pjrandall on 2010-11-25
> **Favux said:**
> We should be able to do that.  How many buttons does the stylus have?  One or two (might be a rocker switch).  Does the stylus have and eraser?  A sort of button on the other end of the stylus barrel that sort of depresses into it?

Also post the output of this command in a terminal:
```
xinput --list
```

	xinput get-feedbacks <device name>
	xinput set-ptr-feedback <device name> <threshold> <num> <denom>
	xinput set-integer-feedback <device name> <feedback id> <value>
	xinput get-button-map <device name>
	xinput set-button-map <device name> <map button 1> [<map button 2> [...]]
	xinput set-pointer <device name> [<x index> <y index>]
	xinput set-mode <device name> ABSOLUTE|RELATIVE
	xinput list [--short || --long] [<device name>...]
	xinput query-state <device name>
	xinput test [-proximity] <device name>
	xinput create-master <id> [<sendCore (dflt:1)>] [<enable (dflt:1)>]
	xinput remove-master <id> [Floating|AttachToMaster (dflt:Floating)] [<returnPointer>] [<returnKeyboard>]
	xinput reattach <id> <master>
	xinput float <id>
	xinput set-cp <window> <device>
	xinput test-xi2 <device>
	xinput list-props <device> [<device> ...]
	xinput set-int-prop <device> <property> <format (8, 16, 32)> <val> [<val> ...]
	xinput set-float-prop <device> <property> <val> [<val> ...]
	xinput set-atom-prop <device> <property> <val> [<val> ...]
	xinput watch-props <device>
	xinput delete-prop <device> <property>
	xinput set-prop <device> [--type=atom|float|int] [--format=8|16|32] <property> <val> [<val> ...]




It has a regular "pen" style tip, with an "eraser" at another end, and a button on the side.

---

### Post by Favux on 2010-11-25
Alright, but you missed the command.  Looks like you forgot the '--list' part and just got the xinput.

---

### Post by pjrandall on 2010-11-25
I copy/pasted it into Terminal. Are there no spaces in the command?

EDIT; I got the command right now .


jp@jp-tablet:~$ xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Mosart Wireless Mouse                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet                     	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

---

### Post by Favux on 2010-11-25
Good.  Now to get your stylus button to be a right click edit the 10-wacom.conf (you're in Lucid right?) first serial snippet so it looks like so:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "Button2" "3"
EndSection

```
To edit it use the following command:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
And then reboot.

My bet is your eraser already works.  It only works in programs built for it like Gimp, Inkscape, and Xournal.  By the way you'll want to install Xournal and CellWriter!  To set up the eraser see near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Then we can move on to rotation.

---

### Post by pjrandall on 2010-11-25
Rad. The right click works great, and the eraser does work, but it behaves the same as the tip.

---

### Post by Favux on 2010-11-25
Great!  :)

If you're in say Gimp you point the eraser to the little eraser icon until it assigns.  Test it.  Then you do the save at the bottom of the tool bar.  Then the eraser will be the eraser.

OK, onto rotation.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Method 1 or 3 should work for you.  It may look harder than it is.  Just read through the relevant stuff a few times and you'll get it.

---

### Post by pjrandall on 2010-12-05
> **Favux said:**
> Great!  :)

If you're in say Gimp you point the eraser to the little eraser icon until it assigns.  Test it.  Then you do the save at the bottom of the tool bar.  Then the eraser will be the eraser.

OK, onto rotation.  See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Method 1 or 3 should work for you.  It may look harder than it is.  Just read through the relevant stuff a few times and you'll get it.

Sorry, I haven't been able to get on in a while. I couldn't get the rotation program to work correctly, but the point is moot, as I've grown accustomed to drawing in landscape format. Also the eraser wouldn't work like you said.

---

### Post by Favux on 2010-12-05
Hi again pjrandall,

OK, you're in Lucid (10.4) correct?  You can rotate into Landscape (inverted) when in tablet mode.  You don't have to rotate to Portrait (90 degrees either way).  Let's look at your output in a terminal of:
```
xrandr -q --verbose
```
That should have worked for your eraser.  Did I point you to the Wacom wiki?  Near the bottom it shows you how to set up in Gimp and Inkscape:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

By the way it would help if you reminded me of which tablet pc you have.  You know the maker and model and stuff like that.

---

