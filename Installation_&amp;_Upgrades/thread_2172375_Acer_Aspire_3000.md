---
title: "Acer Aspire 3000"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by Ultimatefry on 2013-09-04
This computer I got recently can only seem to handle up to Ubuntu version 11.10 (it was super cheap and the hard drive isn't recognized) and therefore I cannot install the Steam (gaming social network) software from the Ubuntu Software Center. WHen I was installing Steam, it told me that it depended on a newer version of libc6 and curl. I was able to easily install curl, but when I tried installing [a newer version of libc6]("http://packages.ubuntu.com/precise/i386/libc6/download"), I got this:

```
(Reading database ... 154106 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using libc6_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6 ...
dpkg: dependency problems prevent configuration of libc6:
 libc6 depends on libc-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-bin on system is 2.13-20ubuntu5.3.
dpkg: error processing libc6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6

```

So, it needs itself to install itself...what do I do?

---

### Post by mörgæs on 2013-09-04
Have you considered a fresh install of Lubuntu 13.04?

---

### Post by Ultimatefry on 2013-09-04
What's the difference between this and Ubuntu 11.10, and would this computer likely handle it?

---

### Post by Ultimatefry on 2013-09-05
the bumping

Any have any option I can take that wouldn't require switching my version of Linux?

---

### Post by Bashing-om on 2013-09-05
Ultimatefry; Hi !

There is no better Long Term Solution. Version 11.10 has reach End Of Life, and as such is no longer supported. It is most strongly recommended to upgrade to a current version. Version 12.04 (the current LTS) is supported 'till the year 2017.
see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
for details to make this happen.
[INDENT][INDENT]just my thought too
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-05
This computer can't handle Ubuntu 12.10.

---

### Post by Bashing-om on 2013-09-05
Ultimatefry; Umph ,, should have reread the thread ... my bad.

Still, the better solution is to install a current version .. I - like mörgæs - suggest lubuntu, if you have as much as 512 Megs of ram. Else there does exist even lighter versions of linux.
I personally like and endorse lubuntu.
All it will cost you is a bit of time and a blank CD to try and see if lubuntu will work for you.
from the links at top of page ->ubuntu community
download the .iso
burn the .iso as a "image", slow burn rate
set in bios to boot the cd as 1st priority
boot the liveCD -> try ubuntu

and see what you see.

[INDENT][INDENT]is there a point in flogging a dead horse
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-07
Okay, after two installs on the Alternate Installer for Lubuntu 12.04, I've only gotten as far as the logo. I think I'm having a problem with where I'm supposed to put the GRUB, because the two options I've tried is the reccommended choice and /dev/sdb

---

### Post by Bashing-om on 2013-09-07
Ultimatefry; Good deal !

Grub .. single hard drive; install grub to "sda" for a standard install nothing fancy.
Else install grub onto the hard disk (ie "sdb") that you are installing 'buntu onto, Grub will pick up any other operating systems and chainload them. In order for this multi disk boot system to work .. leave the boot priority set to the drive that 'buntu is installed onto.

You must set the boot priority in bios .. then bios knows where the boot code is located- to hand off to.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-09-07
Is there any particular reason that you are trying 12.04 and not 13.04?

---

### Post by Ultimatefry on 2013-09-08
I'm seeing if the computer can handle this one first before going up one (It's an Acer Aspire 3000 that I got for $7 at a thrift shop to see if it could be fixed up).

---

### Post by Ultimatefry on 2013-09-08
Okay, it seems that installing with the receiving flash drive plugged into where the installer was got me the option I was supposed to use from the installation instructions, but it still keeps flashing between the screen with the lil' underscore guy and a black screen with the cursor centered (the logo appears when it first loads, though).

---

### Post by Bashing-om on 2013-09-09
Ultimatefry; Hey !

Let's presume that the kernel is unhappy with your graphics card, this will get around that situation and if that is a true condition allow you to install a recommended graphics driver:

Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->System Settings ->Additional Drivers  [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-09
I was able to get to the nomodeset step, but the thing still flashed black and purple.

---

### Post by Bashing-om on 2013-09-09
Ultimatefry; Disappointing !

Ok let's back up a step or so ..Let's see if the system it's self is stable.
Edit once more the grub boot parameter, this time remove quiet and splash, inset the term text.
At this time when booting one should boot to a text login console (TTY1).
At this prompt enter your username and then password when requested ... bear in mind on the password there will be no response back to the screen.
Enter your password blindly and hit the enter key.

Now enter:
```

sudo service lightdm start

```

What happens ?... pass back to us any errors displayed on the screen. If you are able to boot to the CLI (Command Line Interface), then we can look at why the GUI is not launching. 

[INDENT][INDENT][INDENT]where there is life there is hope
[/INDENT][/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-09
Term text?

---

### Post by Bashing-om on 2013-09-09
Ultimatefry; Yep.

Delete the terms "quiet splash" and type in "text" - without the quotes- and one should boot to that CLI environment.

[INDENT][INDENT]more than one way to skin a cat
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-10
I was able to log in and type in the command, but it continued flashing, but this time it said this sometimes inbetween flashes:

```
* ??????? AppArmor profiles
??????? profile in /etc/apparmor??/????????????                    [OK]

?????ing ??? server ???? (maybe failed/start, unsure what it says) [OK]
                                                                      *
???? ??????????????? edit /etc/default/?????
                                       *Checking battery state...  [OK]
```

I see similar stuff when shutting down my computer (starting/stopping bluetooth, other things) when running my working Ubuntu 11.10.

---

### Post by Bashing-om on 2013-09-10
Ultimatefry; Shucks;

Not enough info at this time to suggest a solution.. indications are:
1. Grub is hosed up;
2. /etc/fstab file is hosed up
3. Partition is hosed up
4. file system is hosed up
maybe any and all of the above.

OK .. can you successfully boot the install liveDVD/USB to the "try ubuntu" mode ? -> rules out hardware problems and gives a means of access to the hard drive.
can you successfully boot the install to the text login prompt ? Will make diagnostics much simpler.

We need to know your status in order to provide proper diagnostic commands.

You have come a long way, but not made it home yet.

[INDENT][INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-11
Lubuntu installer only provides 'Boot from first hard disk', and since it is that, it just reboots itself.

---

### Post by Bashing-om on 2013-09-11
Ultimatefry; Hey ..
Give me a bit .. I have a Lubuntu 12.04 liveCD on hand. Let me reboot and refresh my memory ... 

[INDENT][INDENT]back soonest
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-11
Ultimatefry; OK ..
Booting up the liveCD of Lubuntu ...it does have the following options:
1. Try Lubuntu without installing
2. Install Lubuntu
3. Check Disk for Defects
4. Test Memory
5. Boot from First Hard Disk

My question remains .. what results when you choose "Try Lubuntu without Installing" ???

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-11
up and get Install Lubuntu, , Check disk for defects, Test memory, Boot from first hard disk, and Rescue a broken system.

---

### Post by Bashing-om on 2013-09-11
Ultimatefry; Hey ..
Do not know why there would be a difference in 12.04 lubuntu liveCD and 12.04 Lubuntu USB .. in any event .. we still need to verify that you are able to boot your machine with "try Lubuntu".
What results when you choose the option "try Lubuntu without Installing " ?????????

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-09-11
Must be the alternate ISO. 

Where exactly does the process fail, if you install using NOMODESET?

---

### Post by Bashing-om on 2013-09-11
"Must be the alternate ISO." Duh ! .. blame it on my tunnel vision !

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-12
Okay, tried running it from the desktop install version of 13.04 (not sure why I said I was using 12.04 earlier, because I wasn't), and still flashed, but the blank screen with the cursor held for longer. Nomodeset and nodmraid didn't work, either.

---

### Post by mörgæs on 2013-09-12
You mentioned initially that you had 11.10 running. Though it's a step backwards I think it would be good to reinstall this one and do some tests before proceeding. 

My guess is that the problem is either SIS graphics or not enough memory.

---

### Post by Ultimatefry on 2013-09-12
I've been using two seperate flashdrives: one with my 11.10 on it, and the Lubuntu one.

Also, I just noticed the post on installing normal with NOMODESET, and that didn't work, either.

---

### Post by mörgæs on 2013-09-13
The post above was meant as a question. How much memory do you have and which screen card? 

Is this our guy and has more memory been added?
[http://www.cnet.com/laptops/acer-aspire-3000/4507-3121_7-31532504.html](http://www.cnet.com/laptops/acer-aspire-3000/4507-3121_7-31532504.html)

Also it would be interesting to hear of some broader experiments  and not only a brief statement of what does not work.
[Minimal Buntu]("https://help.ubuntu.com/community/Installation/MinimalCD")? 
Bodhi? (link in my signature)
[Puppy]("http://puppylinux.com/")?
...
...

What do you think is the reason for 11.10 not working now if it worked a few days ago?

And so on...

---

### Post by Ultimatefry on 2013-09-13
11.10 has been working the entire time; I just wanted to get a version of ubuntu that supported Steam.

I got this used, and this is what I get as my computer starts up (no matter what happens)

```
CPU0 =Mobile AMD Sempron(tm) Processor 3000+
639K RAM Passed
446M Extended RAM Passed
128K Cache SRAM Passed
System BIOS Shadowed
```

it then goes on about my CD/DVD drive, USB, etc

Here's the history of OS'es(?) that I've tried on here (in order):

[LIST]
[*]Windows 7 (hard drive not recognized)
[*]Ubuntu 12.04 (failed to load installer/Try Ubuntu)
[*]Ubuntu 10.04 (worked)
[*]Ubuntu 10.10 (worked)
[*]Ubuntu 11.04 (worked)
[*]Ubuntu 11.10 (worked, current edition)
[*]Ubuntu 12.04 (failed to load installer/Try Ubuntu)
[*]Lubuntu 12.04 [or 13.04] (failed to load installer)
[*]Lubuntu 13.04 Alternate Installer (Installed; failed to load)
[*]Lubuntu 13.04 (failed to load installer/Try Ubuntu)
[/LIST]

---

### Post by Bashing-om on 2013-09-13
Ultimatefry; Hey.

My wife's system is also AMD sempron ... worked wonderfully with 10.04 . Was initially unable also to get Lubuntu installed on it.
A lot of difficulties getting 12.04 installed .. and when I finally did get 12.04 installed .. was slow and laggy ...Took advisements and tried to install Lubuntu 13.04. Nope ... could not get it to install, installer kept hanging up.
The solution in that case to get Lubuntu to install was not to enable updates or 3rd party software sources during the install.
This particular install is the standard desktop. I have not seen the alternate edition  - reason for a lot of my confusion - so I do not know if those options exist within the installer to be disabled. 
But if so .. try disabling both items during the install...

Lubuntu runs great on my Wife's box ... Graphics card is hurting in intense graphical applications ... but that is another story. 

[INDENT][INDENT]there are those times I just do not know
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-13
Startup Disk Creator isn't letting me make an installer with the mini.iso...

---

### Post by Bashing-om on 2013-09-13
Ultimatefry; If I may suggest;

Download the desktop edition of the .iso file (Lubuntu 13.04) and burn that .iso file to disk ... so we are on the same page. Then I will be able to better assist you.
Not wanting to be difficult, I just know of no better way to offer assistance.

[INDENT][INDENT]I know it can be done
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-14
Okay, done (though the startup creator doesn't let me burn to disks, so I always have to use USB).

---

### Post by Bashing-om on 2013-09-14
Ultimatefry; Great !
Please also understand I do not mean to undermine others efforts to assist you. All advise given is good ->
My effort presently is to insure that you can boot to a GUI ..easiest method for testing is from the liveUSB.
OK, please;
Set in bios as the USB 1st boot priority,
Boot the USB,
Choose "try lubuntu".

What results ? - do we have a graphics driver problem ? else ?

[INDENT]we are backing up to punt[/INDENT]

---

### Post by Ultimatefry on 2013-09-14
I choose 'Try Lubuntu' and get the light blue/blue/white loading screen. While loading, it lets me know that my wireless drivers aren't working and turns into the orange/black/white Ubuntu loading colors (this happens when choosing Try Ubuntu/Lubuntu, but then ones that work for me like 11.10 seem to work fine anyways), then I see several small, stretched out versions of the Lubuntu image + loading dot guys along the top of the screen. It goes back to the orange/black/white screen with something about "LightDM Display Manager", then it starts flashing between black and purple, with the cursor appearing occasionally.

---

### Post by Ultimatefry on 2013-09-14
UPDATE: Just returned to the laptop after a shower, and now it's left on a blank screen without flashing. No amount of touchpad swiping or keyboard clicking will rouse it.

---

### Post by ericrichards420 on 2013-09-14
My sugestion is to upgrade the memory of that computer to 2 gigs of memory. 
[http://www.ebay.com/itm/NEW-2GB-2x1GB-Acer-Aspire-3000-Series-LAPTOP-Memory-DDR-RAM-PC2700-SODIMM-/290699012164?pt=US_Memory_RAM_&hash=item43af02e844](http://www.ebay.com/itm/NEW-2GB-2x1GB-Acer-Aspire-3000-Series-LAPTOP-Memory-DDR-RAM-PC2700-SODIMM-/290699012164?pt=US_Memory_RAM_&hash=item43af02e844) its only 41.50 that computer will run 4 times faster.

If your computer will not install ubuntu or lubuntu I recommend you trying "xubuntu".
let us know how it works out for you.

---

### Post by Bashing-om on 2013-09-14
Ultimatefry'
See ericrichards420's last; more memery is always a good thing. However, as you can run 10.04, 10.10, 11.04 and 11.10 there should not be a problem running Lubuntu 13.04.

I continue to look at this issue as graphics driver related. Are you connecting to the internet through a "wired" connection ? .. The wireless connection is something to be dealt with after installation is completed.
Try:
Boot the liveUSB;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s); choose "nomodeset" space or enter to accept and then the escape key to exit; for other additions the boot options kernel boot line is also available, append any desired boot parameter to the end of the line.
Not required in this instance.
Enter key to continue the boot process to the GUI desk top;


Now what results with "nomodet" ?

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-15
I only have a wired connection when I'm installing.

I get the same thing when I boot, except I get a white bar at the bottom of the screen very shortly before/after the LightDM part.

---

### Post by Bashing-om on 2013-09-15
Ultimatefry; Yuk !
 As we are trying to install on a "Acer Aspire 3000" that is a laptop model ..and before we can do an actual install we must be able to boot that liveUSB.
To that end .. try some of the other booting parameters from that boot options screen in the liveUSB .. next try "acpi=off". As you are able to install earlier versions your system should be able to handle the lighter Lubuntu, So, still looking at the situation as hardware related. Be aware "acpi" is power management ..if you can boot up the liveUSB with "acpi=off" do not run the machine long .. as power management is disabled .. do not want the machine to overheat. Then we will find a solution to that one.

[INDENT][INDENT]still try'n
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-15
acpi = off did the same as nomodeset.
nodmraid did the same as acpi=off, but the boot text turned orange and it started up with an underscore in the corner.
nolapic didn't work.
noapic didn't work.
edd-off didn't work.

All that's left is Free Software Only

---

### Post by mörgæs on 2013-09-15
We have a long series of attempts of installing from 10.04 to 13.04. The oldest half of the installs work but not the newest.

Each Lubuntu release is a little more memory greedy than the previous. On a memory-constrained computer like this one it is expected that somewhere along the line the installations will begin failing. 

Because of this I would (still) like to hear how the 13.04 mini.iso behaved when installed from USB with wired internet connection.

---

### Post by Ultimatefry on 2013-09-16
The startup disk creator doesn't let me make an installer with the mini.iso.

---

### Post by Bashing-om on 2013-09-16
Ultimatefry; Hey;

Can you try installing from a CD ? As mörgæs has pointed out, you only have 256 MB of memory... maybe the USB is using too much of the scarce resource, in addition the sis chip set is not too well supported by the manufacturer.

[INDENT][INDENT]simpler is better
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-17
It doesn't seem to be letting me use even CD's with data on them for install.

---

### Post by Bashing-om on 2013-09-17
Ultimatefry; Well !

from archlinux -> try this as the boot parameter:
> 
video=sisfb:mode:1024x768x16,mem:12288,rate:75
that's an example... but you should be able to do something with it


[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-19
[Using the Desktop, not Alternate, like you asked]

It seems to work better. While the stuff is smaller, I get an image when booting Lubuntu, and the flashing slows down.

---

### Post by Bashing-om on 2013-09-19
Ultimatefry; Hey ! Making some progress .

Ok .. we know it is the relations of the graphics driver...let's see what we can work with:
Boot to the grub boot menu, press "c" for a command line interface.
input:
```

vbeinfo

```
to see what modes are supported.
Then maybe change that boot parameter to something like:
> 
video=sisfb:mode:1024x768x16,mem:4096,rate:70
 with a lower resolution and just cause you are real short on memory.


[INDENT][INDENT]that too is worth a shot
[/INDENT][/INDENT]

---

### Post by Ultimatefry on 2013-09-20
OK, loaded the one with the successful but unviewable install. vbeinfo showed a BUNCH of things, and the code provided didn't work on it.

---

### Post by Bashing-om on 2013-09-20
Ultimatefry; 

Did you try a different resolution from ?
> 
1024x768x16

choosing a resolution as provided by the output of "vbeinfo".

What now is the boot parameter you are attempting ?

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by halo.yanu on 2013-12-02
I have same exact problem, using ubuntu 13.10 desktop (live usb)
trying all param in this thread with no luck :(

any other suggestion?
thanks

---

### Post by Bashing-om on 2013-12-02
halo.yanu; Hi ! Welcome to the forum.

No, nothing new as the OP abandoned the attempt.

What results do you get from post numbers 48 and 50 ?

we can at least give it a try and see what we can do.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-10
Hi, I have Acer Aspire 3002LC, and trying to Install my very first Linux. I have the exactly same problems as Ultimatefry with Lubuntu 13.10. Looking forward to see the answer :)

Regards, Hermanni

---

### Post by Bashing-om on 2013-12-10
hemu79; Hi ! Welcome to the forum .

There is nothing new to this time,
With your renewed interest we can thresh on this some more, see what can be done.
Can you boot to a terminal ?
Can you post the output of the terminal commands ? :
So we can see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```
-As a new user, if you have difficulties with the terminal, we can work through that too -

That is the standard starting place, and go from there.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-11
Hi, I was able to install Lubuntu 13.10 on my computer with this: [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) (Text based installation). About me, I'm not noobie with computers, just new with linux system.  

After the installation I get stuck with same kind of flashing screen. At the startup when pressing "shift" GNU GRUP opens up. And from there I can see that the Filesystem is ok. Problem seems to be with graphics card. This is the information from terminal (or whatever root user...text thing.... root@Lubuntu:~#  <---- that's where I wrote the code)

description: VGA compatible controller
product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display adapter
Vendor: Silicon Integrated Systems (SiS)
Physical id: 0
bus info: pci@0000:01:00.0
Version: 00
width: 32 bits
clock: 66MHz
Capabilities: pm agp agp-3.0 vga_controller cap_list
configuration: latency=0
resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)

My Acer has 1 GB of memory (updated from 512MB) 32-128MB shared with Graphics card, 128 GB SSD (updated from 40 GB HDD). Chipset SiSM760GX. 

Many people seem to have problems with SiS, it is not so well supported. That's what I read from Forums. 

Thanks, Hermanni

---

### Post by mörgæs on 2013-12-11
Correct, SIS is often a problem. There are workarounds (installed through a PPA) but it is probably easier to try Bodhi Linux first.

---

### Post by Bashing-om on 2013-12-11
hemu79; Hello ;

See mörgæs' last.
Also of interest:
[https://help.ubuntu.com/community/BinaryDriverHowto/Sis](https://help.ubuntu.com/community/BinaryDriverHowto/Sis)
Has helpful information.

[INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-11
Hi just Installed Bodhi, works great. Have to check Bashing-om's tips later. 

Thanks, Hermanni

---

### Post by Bashing-om on 2013-12-11
hemu79; Hey !

Outstanding ! Let us know how it goes.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-12
Hi. Is this gonna help me with the problem concerning Lubuntu Graphics driver problem: [http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html](http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html) ? 

And if yes, then I would need some help installing the driver.

Thanks, Hermanni

---

### Post by Bashing-om on 2013-12-12
hemu79; Hey,

I am undecided how best to proceed to get you a working driver for the SIS chip set.
See the ongoing bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464)
It appears the original maintainer is no longer doing so:
[http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl](http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl)

Let's back up and regroup, refresh my memory and for quicker reference:
```

lsb_release -a
uname -a
sudo lshw -C display
lspci -nnk | grep -iA3 vga
dpkg -l xserver-xorg-lts-<version>
dpkg -l xserver-xorg-video-sis-lts-<version> 
ls -la /etc/X11/xorg.conf ##to see if this file exist to make the mods to.

```

Maybe we can implement the referenced patch ?
Any input from those of knowledge of the SIS chip set are welcome to offer comments !

[INDENT][INDENT]sometimes I wonder, other times I do not know
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-14
Hi, I'm right now writing from my Bodhi Linux, finally got Wireless working :) 

So is there anything I can do from this Bodhi Linux, or should I start up to Lubuntu recovery mode?

First two commands show me information about this Bodhi Linux.. 
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Bodhi 2.4.0
Release:        12.04
Codename:       precise

 uname -a
Linux hermanni-Aspire-3000 3.8.0-19-generic #30~precise1-Ubuntu SMP Wed May 1 22:39:29 UTC 2013 i686 athlon i386 GNU/Linux


Next ones:
 sudo lshw -C display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)

lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
        Subsystem: Acer Incorporated [ALI] Device [1025:0083]
        Kernel modules: sisfb

Next two give me errors, because not in Lubuntu?

Last one, I can use File Manager in Bodhi, and could not find xorg.conf in Lubuntu install.

Why I'm changing from Windows XP to Linux is because of the old SSD that I have. XP handles it not so good, it hangs alot. As I have read Linux can handle old SSD's better, and from short experience with Bodhi this seems about right, system is running smoothly and really fast all the time. 

But anyway, what is better in Lubuntu compared with Bodhi? Or should I just start using Bodhi? GUI seems a bit strange in Bodhi.

Thanks, Hermanni

---

### Post by Bashing-om on 2013-12-14
hemu79; Still with out.
The out put of the  "lshw -C display" shows there is no graphics driver loaded.

Presently not sure what to recommend to get a driver installed. Most likely will have to create an /etc/X11/xorg.conf file. However, that is stepping into matters I have no experience with. Never have had to make/alter that file.

When I get caught up, I will devote some effort to seeing what I can do.

Where there is a will
[INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-15
So, I was able to log into Lubuntu after making the xorg.conf file. Had to find a way to log into Terminal first, GRUB menu "e" and added word TEXT after QUIET SPLASH, and then booting with CTRL-X. Then I wrote into xorg.conf the information from this page: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464) (sudo nano /etc/X11/xorg.conf). 

And now I'm writing from Lubuntu!! 

Haven't yet tried any video softwares to see how they run, but this is a one step ahead. I like these challenges with Linux system, have been able to solve many problems already, thanks to Google and this forum thought. 

Thanks, Hermanni

---

### Post by Bashing-om on 2013-12-15
hemu79; You do good work !

Glad you are making such good progress. 
Keep on keep'n on ->
[INDENT][INDENT]just gets better and better
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-17
Hi, is this gonna help me with the sis Video Driver? Still strugling with this, video seems a bit slow, tried Cinnamon desktop on Lubuntu, and it said there is no acceleration on, and Cinnamon was very slow.

Help, please, Hermanni

---

### Post by hemu79 on 2013-12-17
ups... forgot the link :) [http://www.winischhofer.net/linuxsispart1.shtml](http://www.winischhofer.net/linuxsispart1.shtml)

---

### Post by hemu79 on 2013-12-19
Hi again, somehow I have now working driver... I installed it from page [http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html#contenttoc4](http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html#contenttoc4) and it seems to work ok... 

So... How did I get working Lubuntu 13.10 on my Acer Aspire 3002LC?

1. Installed Lubuntu with Alternate install [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

2. Logged into the Terminal mode from Grup, GRUB menu "e" and added word TEXT after QUIET SPLASH, and then booting  with CTRL-X. Then I wrote into xorg.conf the information from this page:  [https://bugs.launchpad.net/ubuntu/+s...s/+bug/1066464]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/1066464") (sudo nano /etc/X11/xorg.conf). 

3. Downloaded the driver from [http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html#contenttoc4](http://manpages.ubuntu.com/manpages/saucy/man4/sis.4.html#contenttoc4)

4. Re-installed the driver

5. Restart

6. sudo lshw -C display: 
*-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)

So am I good now? How can I check if hardware acceleration is on or not?

Thanks, Hermanni

---

### Post by hemu79 on 2013-12-20
Me again! got new driver from this page: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages) (patched..don't know yet what that really means, but gonna find out)

Everything seems to works ok, removed xorg.conf file, so acceleration should be on by default. At least I can drag Firefox window with youtube video running realtime without any problem. And found a little program called GtkPerf, and it gives me a result 19.3 sec with 100 rounds, seems ok after googling some results from that program. So I'm happy with this. 

Thanks for all the help. Now I got my first Linux set up to do some exploring. Hermanni

---

### Post by Bashing-om on 2013-12-20
hemu79; Still with you.

Just have not had a good solution:
> 
6. sudo lshw -C display: 
*-display UNCLAIMED 
description: VGA compatible controller
<snip>
configuration: latency=0
<snip>


I am still concerned that there is no graphics drivers loaded.
The above says there is still no driver loaded. I am not familiar with the SIS graphics but, maybe the drivers are blacklisted such that the kernel can not load them, even though the drivers are installed onto the system ?

What is the new situation with the "new Driver" ?
What does:
```

sudo lshw -C display
ls -la /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf

```
relate to us in respect to drivers.
You want to see a result similar to mine (radeon):
> 
 *-display:[color=red]0[/color]             
       description: VGA compatible controller
       product: RV515 [Radeon X1300/X1550]
       vendor: Advanced Micro Devices [AMD] nee ATI
<snip>
 capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: [color=red]driver=radeon[/color] latency=0


I wish I could help more, but;
[INDENT][INDENT][INDENT]help'n the best I can
[/INDENT][/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-22
Hi, found out something like this:

[    10.623] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    10.623] X Protocol Version 11, Revision 0
[    10.623] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    10.623] Current Operating System: Linux Lubu 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:07:40 UTC 2013 i686
[    10.623] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=5dc0165b-3c6c-4959-9d6a-ddb06dab9cde ro quiet splash vt.handoff=7
[    10.623] Build Date: 15 October 2013  09:23:29AM
[    10.623] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    10.623] Current version of pixman: 0.30.2
[    10.623]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    10.623] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.623] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 17:24:38 2013
[    10.641] (==) Using config file: "/etc/X11/xorg.conf"
[    10.641] (==) Using config directory: "/etc/X11/xorg.conf.d"
[    10.641] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.644] (==) No Layout section.  Using the first Screen section.
[    10.644] (**) |-->Screen "Configured Screen" (0)
[    10.644] (**) |   |-->Monitor "Configured Monitor"
[    10.645] (**) |   |-->Device "Card0"
[    10.645] (==) Automatically adding devices
[    10.645] (==) Automatically enabling devices
[    10.645] (==) Automatically adding GPU devices
[    10.645] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.645]     Entry deleted from font path.
[    10.645] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    10.645]     Entry deleted from font path.
[    10.645] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    10.645]     Entry deleted from font path.
[    10.645] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    10.645]     Entry deleted from font path.
[    10.645] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    10.645]     Entry deleted from font path.
[    10.645] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    10.645] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.645] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.645] (II) Loader magic: 0xb776d6a0
[    10.645] (II) Module ABI versions:
[    10.645]     X.Org ANSI C Emulation: 0.4
[    10.645]     X.Org Video Driver: 14.1
[    10.645]     X.Org XInput driver : 19.1
[    10.645]     X.Org Server Extension : 7.0
[    10.646] (--) PCI:*(0:1:0:0) 1039:6330:1025:0083 rev 0, Mem @ 0xe8000000/134217728, 0xe2100000/131072, I/O @ 0x0000a000/128
[    10.653] (II) Open ACPI successful (/var/run/acpid.socket)
[    10.653] Initializing built-in extension Generic Event Extension
[    10.653] Initializing built-in extension SHAPE
[    10.653] Initializing built-in extension MIT-SHM
[    10.653] Initializing built-in extension XInputExtension
[    10.653] Initializing built-in extension XTEST
[    10.653] Initializing built-in extension BIG-REQUESTS
[    10.653] Initializing built-in extension SYNC
[    10.653] Initializing built-in extension XKEYBOARD
[    10.653] Initializing built-in extension XC-MISC
[    10.653] Initializing built-in extension SECURITY
[    10.653] Initializing built-in extension XINERAMA
[    10.653] Initializing built-in extension XFIXES
[    10.653] Initializing built-in extension RENDER
[    10.654] Initializing built-in extension RANDR
[    10.654] Initializing built-in extension COMPOSITE
[    10.654] Initializing built-in extension DAMAGE
[    10.654] Initializing built-in extension MIT-SCREEN-SAVER
[    10.654] Initializing built-in extension DOUBLE-BUFFER
[    10.654] Initializing built-in extension RECORD
[    10.654] Initializing built-in extension DPMS
[    10.654] Initializing built-in extension X-Resource
[    10.654] Initializing built-in extension XVideo
[    10.654] Initializing built-in extension XVideo-MotionCompensation
[    10.654] Initializing built-in extension SELinux
[    10.654] Initializing built-in extension XFree86-VidModeExtension
[    10.654] Initializing built-in extension XFree86-DGA
[    10.654] Initializing built-in extension XFree86-DRI
[    10.654] Initializing built-in extension DRI2
[    10.654] (II) "glx" will be loaded by default.
[    10.654] (WW) "xmir" is not to be loaded by default. Skipping.
[    10.654] (II) LoadModule: "dri2"
[    10.654] (II) Module "dri2" already built-in
[    10.654] (II) LoadModule: "glamoregl"
[    10.663] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    10.701] (II) Module glamoregl: vendor="X.Org Foundation"
[    10.701]     compiled for 1.14.3, module version = 0.5.1
[    10.701]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.701] (II) LoadModule: "glx"
[    10.702] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    10.702] (II) Module glx: vendor="X.Org Foundation"
[    10.702]     compiled for 1.14.3, module version = 1.0.0
[    10.702]     ABI class: X.Org Server Extension, version 7.0
[    10.702] (==) AIGLX enabled
[    10.702] Loading extension GLX
[    10.702] (II) LoadModule: "sis"
[    10.702] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[    10.702] (II) Module sis: vendor="X.Org Foundation"
[    10.702]     compiled for 1.14.2.901, module version = 0.10.7
[    10.702]     Module class: X.Org Video Driver
[    10.702]     ABI class: X.Org Video Driver, version 14.1
[    10.702] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[    10.703] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[    10.703] (++) using VT number 7

[    10.703] (WW) Falling back to old probe method for sis
[    10.703] (--) Assigning device section with no busID to primary device
[    10.703] (--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
[    10.703] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.14.2.901)
[    10.703] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[    10.703] (II) SIS(0): *** See [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)
[    10.703] (II) SIS(0): *** for documentation and updates.
[    10.703] (--) SIS(0): sisfb not found
[    10.703] (--) SIS(0): Relocated I/O registers at 0xA000
[    10.703] (II) Loading sub module "ramdac"
[    10.703] (II) LoadModule: "ramdac"
[    10.704] (II) Module "ramdac" already built-in
[    10.704] (II) SIS(0): Creating default Display subsection in Screen section
    "Configured Screen" for depth/fbbpp 24/32
[    10.704] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[    10.704] (==) SIS(0): RGB weight 888
[    10.704] (==) SIS(0): Default visual is TrueColor
[    10.704] (--) SIS(0): Video BIOS version "2.27.g8" found (new SiS data layout)
[    10.704] (==) SIS(0): Using HW cursor
[    10.704] (==) SIS(0): Color HW cursor is enabled
[    10.704] (II) SIS(0): Using VRAM command queue, size 512k
[    10.704] (==) SIS(0): Hotkey display switching is enabled
[    10.704] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[    10.704] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[    10.704] (==) SIS(0): SiSCtrl utility interface is disabled
[    10.704] (II) SIS(0): For information on SiSCtrl, see
        [http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl](http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl)
[    10.704] (==) SIS(0): DRI disabled
[    10.704] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[    10.704] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[    10.704] (--) SIS(0): 65536K shared video RAM (UMA)
[    10.704] (--) SIS(0): DRAM type: DDR SDRAM
[    10.704] (--) SIS(0): Memory clock: 198.861 MHz
[    10.704] (--) SIS(0): DRAM bus width: 64 bit
[    10.704] (--) SIS(0): Linear framebuffer at 0xE8000000
[    10.704] (--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
[    10.704] (--) SIS(0): VideoRAM: 65536 KB
[    10.704] (II) SIS(0): Using 64960K of framebuffer memory at offset 0K
[    10.704] (--) SIS(0): Hardware supports two video overlays
[    10.704] (II) SIS(0): 
    Dear SiS76x user, your machine is using a shared memory framebuffer.
    Due to hardware limitations of the SiS chip in combination with the
    AMD CPU, video overlay support is very limited on this machine. If you
    experience flashing lines in the video and/or the graphics display
    during video playback, reduce the color depth and/or the resolution
    and/or the refresh rate. Alternatively, use the video blitter.
[    10.705] (--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
[    12.069] (--) SIS(0): No CRT1/VGA detected
[    12.069] (--) SIS(0): Detected LCD/plasma panel (1024x768, 0, non-exp., RGB18 [02c100])
[    12.069] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.069] (II) SIS(0): CRT1 gamma correction is enabled
[    12.069] (II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
[    12.069] (II) SIS(0): CRT2 gamma correction is enabled
[    12.069] (--) SIS(0): Memory bandwidth at 32 bpp is 397.722 MHz
[    12.069] (--) SIS(0): Detected LCD PanelDelayCompensation 0x0c (for LCD=CRT2)
[    12.069] (--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
[    12.069] (II) Loading sub module "ddc"
[    12.069] (II) LoadModule: "ddc"
[    12.069] (II) Module "ddc" already built-in
[    12.069] (--) SIS(0): CRT2 DDC probing failed
[    12.069] (==) SIS(0): Min pixel clock is 10 MHz
[    12.069] (--) SIS(0): Max pixel clock is 290 MHz
[    12.069] (II) SIS(0): Replaced entire mode list with built-in modes
[    12.069] (II) SIS(0): Correcting missing CRT2 monitor HSync range
[    12.069] (II) SIS(0): Correcting missing CRT2 monitor VRefresh range
[    12.069] (II) SIS(0): "Unknown reason" in the following list means that the mode
[    12.069] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[    12.069] (II) SIS(0): Configured Monitor: Using hsync range of 30.00-80.00 kHz
[    12.069] (II) SIS(0): Configured Monitor: Using vrefresh range of 59.00-61.00 Hz
[    12.069] (II) SIS(0): Configured Monitor: Using vrefresh value of 71.00 Hz
[    12.069] (WW) SIS(0): Unable to estimate virtual size
[    12.069] (II) SIS(0): Clock range:  10.00 to 290.64 MHz
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[    12.069] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[    12.069] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[    12.069] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.069] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[    12.070] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
[    12.070] (II) SIS(0): Not using default mode "1360x768" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1680x1050" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1920x1080" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[    12.070] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[    12.070] (--) SIS(0): Virtual size is 1024x768 (pitch 1024)
[    12.070] (**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[    12.070] (**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[    12.070] (**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
[    12.070] (**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
[    12.070] (**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
[    12.070] (**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
[    12.070] (**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
[    12.070] (**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
[    12.070] (**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
[    12.070] (**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
[    12.070] (**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
[    12.070] (**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
[    12.070] (**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
[    12.070] (**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
[    12.070] (**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
[    12.070] (**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
[    12.070] (**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
[    12.070] (==) SIS(0): DPI set to (96, 96)
[    12.070] (II) Loading sub module "fb"
[    12.070] (II) LoadModule: "fb"
[    12.071] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.071] (II) Module fb: vendor="X.Org Foundation"
[    12.071]     compiled for 1.14.3, module version = 1.0.0
[    12.071]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.071] (II) Loading sub module "exa"
[    12.071] (II) LoadModule: "exa"
[    12.071] (II) Loading /usr/lib/xorg/modules/libexa.so
[    12.071] (II) Module exa: vendor="X.Org Foundation"
[    12.071]     compiled for 1.14.3, module version = 2.6.0
[    12.071]     ABI class: X.Org Video Driver, version 14.1
[    12.071] (--) Depth 24 pixmap format is 32 bpp
[    12.072] (II) Loading sub module "vbe"
[    12.072] (II) LoadModule: "vbe"
[    12.072] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    12.072] (II) Module vbe: vendor="X.Org Foundation"
[    12.072]     compiled for 1.14.3, module version = 1.1.0
[    12.072]     ABI class: X.Org Video Driver, version 14.1
[    12.072] (II) Loading sub module "int10"
[    12.072] (II) LoadModule: "int10"
[    12.073] (II) Loading /usr/lib/xorg/modules/libint10.so
[    12.073] (II) Module int10: vendor="X.Org Foundation"
[    12.073]     compiled for 1.14.3, module version = 1.0.0
[    12.073]     ABI class: X.Org Video Driver, version 14.1
[    12.073] (II) SIS(0): initializing int10
[    12.073] (II) SIS(0): Primary V_BIOS segment is: 0xc000
[    12.076] (II) SIS(0): VESA BIOS detected
[    12.076] (II) SIS(0): VESA VBE Version 3.0
[    12.076] (II) SIS(0): VESA VBE Total Mem: 16384 kB
[    12.076] (II) SIS(0): VESA VBE OEM: SiS
[    12.076] (II) SIS(0): VESA VBE OEM Software Rev: 1.0
[    12.076] (II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[    12.076] (II) SIS(0): VESA VBE OEM Product: 6330
[    12.076] (II) SIS(0): VESA VBE OEM Product Rev: 2.27.g8
[    12.506] (II) SIS(0): Setting standard mode 0x64
[    13.332] (II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
[    13.358] (II) EXA(0): Offscreen pixmap area of 63373312 bytes
[    13.358] (II) EXA(0): Driver registered support for the following operations:
[    13.358] (II)         Solid
[    13.358] (II)         Copy
[    13.358] (II)         UploadToScreen
[    13.358] (II)         DownloadFromScreen
[    13.358] (--) SIS(0): CPU frequency 1600.00Mhz
[    13.359] (II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
[    13.371] (--) SIS(0):     Checked libc memcpy()...     350.1 MiB/s
[    13.383] (--) SIS(0):     Checked built-in-1 memcpy()...     357.2 MiB/s
[    13.421] (--) SIS(0):     Checked built-in-2 memcpy()...     75.5 MiB/s
[    13.431] (--) SIS(0):     Checked MMX memcpy()...     361.7 MiB/s
[    13.442] (--) SIS(0):     Checked 3DNow! memcpy()...     366.6 MiB/s
[    13.452] (--) SIS(0):     Checked MMX2 memcpy()...     457.5 MiB/s
[    13.453] (--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
[    13.453] (--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
[    13.453] (--) SIS(0): CPU frequency 1600.00Mhz
[    13.454] (II) SIS(0): Benchmarking video RAM to system RAM memory transfer methods:
[    13.572] (--) SIS(0):     Checked libc memcpy()...     23.6 MiB/s
[    13.689] (--) SIS(0):     Checked built-in-1 memcpy()...     22.6 MiB/s
[    13.806] (--) SIS(0):     Checked built-in-2 memcpy()...     23.6 MiB/s
[    13.923] (--) SIS(0):     Checked MMX memcpy()...     22.6 MiB/s
[    14.040] (--) SIS(0):     Checked 3DNow! memcpy()...     23.7 MiB/s
[    14.157] (--) SIS(0):     Checked MMX2 memcpy()...     23.2 MiB/s
[    14.157] (--) SIS(0): Using 3DNow! method for aligned data transfers from video RAM
[    14.157] (--) SIS(0): Using 3DNow! method for unaligned data transfers from video RAM
[    14.157] (==) SIS(0): Backing store disabled
[    14.157] (==) SIS(0): Silken mouse enabled
[    14.158] (==) SIS(0): DPMS enabled
[    14.158] (II) SIS(0): Using SiS300/315/330/340 series HW Xv
[    14.158] (II) SIS(0): Default Xv adaptor is Video Overlay
[    14.189] (II) SIS(0): Initialized SISCTRL extension version 0.1
[    14.189] (II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
[    14.189] (==) RandR enabled
[    14.200] (II) SELinux: Disabled on system
[    14.202] (II) AIGLX: Screen 0 is not DRI2 capable
[    14.202] (II) AIGLX: Screen 0 is not DRI capable
[    14.292] (II) AIGLX: Loaded and initialized swrast
[    14.292] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    14.310] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    14.315] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    14.315] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.315] (II) LoadModule: "evdev"
[    14.315] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    14.316] (II) Module evdev: vendor="X.Org Foundation"
[    14.317]     compiled for 1.14.1, module version = 2.7.3
[    14.317]     Module class: X.Org XInput Driver
[    14.317]     ABI class: X.Org XInput driver, version 19.1
[    14.317] (II) Using input driver 'evdev' for 'Power Button'
[    14.317] (**) Power Button: always reports core events
[    14.317] (**) evdev: Power Button: Device: "/dev/input/event3"
[    14.317] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.317] (--) evdev: Power Button: Found keys
[    14.317] (II) evdev: Power Button: Configuring as keyboard
[    14.317] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    14.317] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    14.317] (**) Option "xkb_rules" "evdev"
[    14.317] (**) Option "xkb_model" "pc105"
[    14.317] (**) Option "xkb_layout" "se"
[    14.322] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    14.324] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    14.324] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    14.324] (II) Using input driver 'evdev' for 'Power Button'
[    14.324] (**) Power Button: always reports core events
[    14.324] (**) evdev: Power Button: Device: "/dev/input/event1"
[    14.324] (--) evdev: Power Button: Vendor 0 Product 0x1
[    14.324] (--) evdev: Power Button: Found keys
[    14.324] (II) evdev: Power Button: Configuring as keyboard
[    14.324] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    14.324] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    14.324] (**) Option "xkb_rules" "evdev"
[    14.324] (**) Option "xkb_model" "pc105"
[    14.324] (**) Option "xkb_layout" "se"
[    14.325] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    14.325] (II) No input driver specified, ignoring this device.
[    14.325] (II) This device may have been added with another device file.
[    14.325] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    14.325] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    14.325] (II) Using input driver 'evdev' for 'Sleep Button'
[    14.325] (**) Sleep Button: always reports core events
[    14.325] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    14.326] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    14.326] (--) evdev: Sleep Button: Found keys
[    14.326] (II) evdev: Sleep Button: Configuring as keyboard
[    14.326] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    14.326] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    14.326] (**) Option "xkb_rules" "evdev"
[    14.326] (**) Option "xkb_model" "pc105"
[    14.326] (**) Option "xkb_layout" "se"
[    14.327] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    14.327] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    14.327] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    14.327] (**) AT Translated Set 2 keyboard: always reports core events
[    14.327] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    14.327] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    14.327] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    14.327] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    14.327] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    14.327] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    14.327] (**) Option "xkb_rules" "evdev"
[    14.327] (**) Option "xkb_model" "pc105"
[    14.327] (**) Option "xkb_layout" "se"
[    14.328] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    14.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    14.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    14.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    14.328] (II) LoadModule: "synaptics"
[    14.328] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    14.329] (II) Module synaptics: vendor="X.Org Foundation"
[    14.329]     compiled for 1.14.2, module version = 1.7.1
[    14.329]     Module class: X.Org XInput Driver
[    14.329]     ABI class: X.Org XInput driver, version 19.1
[    14.329] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    14.329] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.329] (**) Option "Device" "/dev/input/event5"
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 61)
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 100)
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    14.329] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    14.329] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.329] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    14.329] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    14.329] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    14.329] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    14.329] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    14.329] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    14.329] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    14.329] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    14.329] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    14.330] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    14.330] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    14.330] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.528] (II) XKB: reuse xkmfile /var/lib/xkb/server-523B07B557B20588EB459118C97940B7C9FF61EB.xkm
[    22.557] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CF9FE8264DCD20238B4E6735C1FC4EDF5B76FF7.xkm
[    22.864] (II) XKB: reuse xkmfile /var/lib/xkb/server-CA77D3C9974672559BF238B59AF8F31B450C77E6.xkm
[    22.893] (II) XKB: reuse xkmfile /var/lib/xkb/server-5CF9FE8264DCD20238B4E6735C1FC4EDF5B76FF7.xkm

---

### Post by Bashing-om on 2013-12-22
hemu79; Looking good !

The log certainly indicates that the sis driver is loaded. Any problems now ?
I note the log has some hints to follow if there are any problems.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-22
Hi, just installed Xubuntu 12.04 and it went without any problems.

/var/log/Xorg.0.log seems to be almost the same on this.

And on Xubuntu: sudo lshw -C display

*-display UNCLAIMED    
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff memory:e2100000-e211ffff ioport:a000(size=128)

So this is also same in both.

Xubuntu seems to handle sis-driver a little bit better, I tested GtkPerf, and it gave me a result 16.5 sec. 

Because Xubuntu installed without any problem, and performance seems to be better I think Xubuntu is going to be my primary OS. 

You mentioned some hints to follow from the log file, what are they? I might give it a try.

Hermanni

---

### Post by Bashing-om on 2013-12-22
hemu79; Hey,

This is what first caught my attention:
> 
Dear SiS76x user, your machine is using a shared memory framebuffer.
Due to hardware limitations of the SiS chip in combination with the
AMD CPU, video overlay support is very limited on this machine. If you
experience flashing lines in the video and/or the graphics display
during video playback, reduce the color depth and/or the resolution
and/or the refresh rate. Alternatively, use the video blitter.
[ 10.705] (--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)


to understand the logs: The legend is explained:
> 
[ 10.623] Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
[ 10.623] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 10.623] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 17:24:38 2013


There are a couple other entries that one might explore further: As in: 
> 
[ 10.703] (WW) Falling back to old probe method for sis
## I do not understand this one next;
[ 10.703] (--) Assigning device section with no busID to primary device
##When clearly the bus ID is assigned: per:
[ 10.646] (--) PCI:*(0:1:0:0) 1039:6330:1025:0083 rev 0, Mem @ 0xe8000000/134217728, 0xe2100000/131072, I/O @ 0x0000a000/128
##unless I am totally out there in left field !
 10.704] (==) SIS(0): SiSCtrl utility interface is disabled

Now what I also do not comprehend, the logs say the sis driver is loaded, but then ->
"lshw -C display" does not report it at all, says no display and no driver loaded ... sheessshh.
Do not comprehend the why and whereof !

I hate to leave you with more questions than answers, but -> here I do not know.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-22
This is a log file from Xubuntu

[     7.541] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     7.541] X Protocol Version 11, Revision 0
[     7.541] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[     7.541] Current Operating System: Linux ubuntu 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:38:12 UTC 2013 i686
[     7.541] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=972c86f9-ca9a-4e10-831a-7bee979ca60a ro quiet splash vt.handoff=7
[     7.542] Build Date: 16 October 2013  04:45:22PM
[     7.542] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     7.542] Current version of pixman: 0.24.4
[     7.542]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     7.542] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.542] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 19:45:26 2013
[     7.548] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.551] (==) No Layout section.  Using the first Screen section.
[     7.551] (==) No screen section available. Using defaults.
[     7.551] (**) |-->Screen "Default Screen Section" (0)
[     7.551] (**) |   |-->Monitor "<default monitor>"
[     7.553] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     7.553] (==) Automatically adding devices
[     7.553] (==) Automatically enabling devices
[     7.565] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.565]     Entry deleted from font path.
[     7.565] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.565]     Entry deleted from font path.
[     7.565] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.565]     Entry deleted from font path.
[     7.568] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.568]     Entry deleted from font path.
[     7.568] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.568]     Entry deleted from font path.
[     7.568] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     7.568]     Entry deleted from font path.
[     7.568] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     7.568] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     7.568] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.569] (II) Loader magic: 0x8ca5a0
[     7.569] (II) Module ABI versions:
[     7.569]     X.Org ANSI C Emulation: 0.4
[     7.569]     X.Org Video Driver: 11.0
[     7.569]     X.Org XInput driver : 16.0
[     7.569]     X.Org Server Extension : 6.0
[     7.570] (--) PCI:*(0:1:0:0) 1039:6330:1025:0083 rev 0, Mem @ 0xe8000000/134217728, 0xe2100000/131072, I/O @ 0x0000a000/128
[     7.570] (II) Open ACPI successful (/var/run/acpid.socket)
[     7.570] (II) LoadModule: "extmod"
[     7.575] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     7.577] (II) Module extmod: vendor="X.Org Foundation"
[     7.577]     compiled for 1.11.3, module version = 1.0.0
[     7.577]     Module class: X.Org Server Extension
[     7.577]     ABI class: X.Org Server Extension, version 6.0
[     7.577] (II) Loading extension MIT-SCREEN-SAVER
[     7.577] (II) Loading extension XFree86-VidModeExtension
[     7.577] (II) Loading extension XFree86-DGA
[     7.578] (II) Loading extension DPMS
[     7.578] (II) Loading extension XVideo
[     7.578] (II) Loading extension XVideo-MotionCompensation
[     7.578] (II) Loading extension X-Resource
[     7.578] (II) LoadModule: "dbe"
[     7.578] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     7.580] (II) Module dbe: vendor="X.Org Foundation"
[     7.580]     compiled for 1.11.3, module version = 1.0.0
[     7.580]     Module class: X.Org Server Extension
[     7.580]     ABI class: X.Org Server Extension, version 6.0
[     7.580] (II) Loading extension DOUBLE-BUFFER
[     7.580] (II) LoadModule: "glx"
[     7.581] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     7.595] (II) Module glx: vendor="X.Org Foundation"
[     7.595]     compiled for 1.11.3, module version = 1.0.0
[     7.595]     ABI class: X.Org Server Extension, version 6.0
[     7.595] (==) AIGLX enabled
[     7.595] (II) Loading extension GLX
[     7.595] (II) LoadModule: "record"
[     7.595] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     7.597] (II) Module record: vendor="X.Org Foundation"
[     7.597]     compiled for 1.11.3, module version = 1.13.0
[     7.597]     Module class: X.Org Server Extension
[     7.597]     ABI class: X.Org Server Extension, version 6.0
[     7.597] (II) Loading extension RECORD
[     7.597] (II) LoadModule: "dri"
[     7.597] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     7.599] (II) Module dri: vendor="X.Org Foundation"
[     7.599]     compiled for 1.11.3, module version = 1.0.0
[     7.599]     ABI class: X.Org Server Extension, version 6.0
[     7.599] (II) Loading extension XFree86-DRI
[     7.599] (II) LoadModule: "dri2"
[     7.600] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.602] (II) Module dri2: vendor="X.Org Foundation"
[     7.602]     compiled for 1.11.3, module version = 1.2.0
[     7.602]     ABI class: X.Org Server Extension, version 6.0
[     7.602] (II) Loading extension DRI2
[     7.602] (==) Matched sis as autoconfigured driver 0
[     7.602] (==) Matched vesa as autoconfigured driver 1
[     7.602] (==) Matched fbdev as autoconfigured driver 2
[     7.602] (==) Assigned the driver to the xf86ConfigLayout
[     7.602] (II) LoadModule: "sis"
[     7.603] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[     7.610] (II) Module sis: vendor="X.Org Foundation"
[     7.610]     compiled for 1.11.3, module version = 0.10.3
[     7.610]     Module class: X.Org Video Driver
[     7.610]     ABI class: X.Org Video Driver, version 11.0
[     7.610] (II) LoadModule: "vesa"
[     7.611] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     7.612] (II) Module vesa: vendor="X.Org Foundation"
[     7.612]     compiled for 1.11.3, module version = 2.3.0
[     7.612]     Module class: X.Org Video Driver
[     7.612]     ABI class: X.Org Video Driver, version 11.0
[     7.612] (II) LoadModule: "fbdev"
[     7.612] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     7.613] (II) Module fbdev: vendor="X.Org Foundation"
[     7.613]     compiled for 1.11.3, module version = 0.4.2
[     7.613]     ABI class: X.Org Video Driver, version 11.0
[     7.613] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[     7.613] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[     7.613] (II) VESA: driver for VESA chipsets: vesa
[     7.613] (II) FBDEV: driver for framebuffer: fbdev
[     7.613] (++) using VT number 7

[     7.613] (WW) Falling back to old probe method for sis
[     7.614] (--) Assigning device section with no busID to primary device
[     7.614] (--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
[     7.614] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[     7.614] (WW) Falling back to old probe method for vesa
[     7.614] (WW) Falling back to old probe method for fbdev
[     7.614] (II) Loading sub module "fbdevhw"
[     7.614] (II) LoadModule: "fbdevhw"
[     7.614] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     7.616] (II) Module fbdevhw: vendor="X.Org Foundation"
[     7.616]     compiled for 1.11.3, module version = 0.0.2
[     7.616]     ABI class: X.Org Video Driver, version 11.0
[     7.618] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.11.3.0)
[     7.618] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[     7.618] (II) SIS(0): *** See [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)
[     7.618] (II) SIS(0): *** for documentation and updates.
[     7.618] (--) SIS(0): sisfb not found
[     7.618] (--) SIS(0): Relocated I/O registers at 0xA000
[     7.618] (II) Loading sub module "ramdac"
[     7.618] (II) LoadModule: "ramdac"
[     7.618] (II) Module "ramdac" already built-in
[     7.618] (II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     7.618] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[     7.618] (==) SIS(0): RGB weight 888
[     7.618] (==) SIS(0): Default visual is TrueColor
[     7.618] (--) SIS(0): Video BIOS version "2.27.g8" found (new SiS data layout)
[     7.619] (==) SIS(0): Using XAA acceleration architecture
[     7.619] (==) SIS(0): Using HW cursor
[     7.619] (==) SIS(0): Color HW cursor is enabled
[     7.619] (II) SIS(0): Using VRAM command queue, size 512k
[     7.619] (==) SIS(0): Hotkey display switching is enabled
[     7.619] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[     7.619] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[     7.619] (==) SIS(0): SiSCtrl utility interface is disabled
[     7.619] (II) SIS(0): For information on SiSCtrl, see
        [http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl](http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl)
[     7.619] (==) SIS(0): DRI disabled
[     7.619] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[     7.619] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[     7.619] (--) SIS(0): 65536K shared video RAM (UMA)
[     7.619] (--) SIS(0): DRAM type: DDR SDRAM
[     7.619] (--) SIS(0): Memory clock: 198.861 MHz
[     7.619] (--) SIS(0): DRAM bus width: 64 bit
[     7.619] (--) SIS(0): Linear framebuffer at 0xE8000000
[     7.619] (--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
[     7.619] (--) SIS(0): VideoRAM: 65536 KB
[     7.619] (II) SIS(0): Using 64960K of framebuffer memory at offset 0K
[     7.619] (--) SIS(0): Hardware supports two video overlays
[     7.619] (II) SIS(0): 
    Dear SiS76x user, your machine is using a shared memory framebuffer.
    Due to hardware limitations of the SiS chip in combination with the
    AMD CPU, video overlay support is very limited on this machine. If you
    experience flashing lines in the video and/or the graphics display
    during video playback, reduce the color depth and/or the resolution
    and/or the refresh rate. Alternatively, use the video blitter.
[     7.619] (--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
[     8.623] (--) SIS(0): No CRT1/VGA detected
[     8.623] (--) SIS(0): Detected LCD/plasma panel (1024x768, 0, non-exp., RGB18 [02c100])
[     8.623] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.623] (II) SIS(0): CRT1 gamma correction is enabled
[     8.623] (II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
[     8.623] (II) SIS(0): CRT2 gamma correction is enabled
[     8.623] (--) SIS(0): Memory bandwidth at 32 bpp is 397.722 MHz
[     8.623] (--) SIS(0): Detected LCD PanelDelayCompensation 0x0c (for LCD=CRT2)
[     8.623] (--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
[     8.623] (II) Loading sub module "ddc"
[     8.623] (II) LoadModule: "ddc"
[     8.623] (II) Module "ddc" already built-in
[     8.623] (--) SIS(0): CRT2 DDC probing failed
[     8.623] (==) SIS(0): Min pixel clock is 10 MHz
[     8.623] (--) SIS(0): Max pixel clock is 290 MHz
[     8.623] (II) SIS(0): Replaced entire mode list with built-in modes
[     8.623] (II) SIS(0): Correcting missing CRT2 monitor HSync range
[     8.623] (II) SIS(0): Correcting missing CRT2 monitor VRefresh range
[     8.623] (II) SIS(0): "Unknown reason" in the following list means that the mode
[     8.624] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[     8.624] (II) SIS(0): <default monitor>: Using hsync range of 30.00-80.00 kHz
[     8.624] (II) SIS(0): <default monitor>: Using vrefresh range of 59.00-61.00 Hz
[     8.624] (II) SIS(0): <default monitor>: Using vrefresh value of 71.00 Hz
[     8.624] (WW) SIS(0): Unable to estimate virtual size
[     8.624] (II) SIS(0): Clock range:  10.00 to 290.64 MHz
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[     8.624] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
 [     8.624] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[     8.624] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.624] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
[     8.624] (II) SIS(0): Not using default mode "1360x768" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1680x1050" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1920x1080" (unknown reason)
[     8.624] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.625] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.625] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.625] (--) SIS(0): Virtual size is 1024x768 (pitch 1024)
[     8.625] (**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[     8.625] (**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[     8.625] (**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
[     8.625] (**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
[     8.625] (**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
[     8.625] (**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
[     8.625] (**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
[     8.625] (**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
[     8.625] (**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
[     8.625] (**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
[     8.625] (**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
[     8.625] (**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
[     8.625] (**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
[     8.625] (**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
[     8.625] (**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
[     8.625] (**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
[     8.625] (**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
[     8.625] (==) SIS(0): DPI set to (96, 96)
[     8.625] (II) Loading sub module "fb"
[     8.625] (II) LoadModule: "fb"
[     8.625] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.627] (II) Module fb: vendor="X.Org Foundation"
[     8.627]     compiled for 1.11.3, module version = 1.0.0
[     8.627]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.627] (II) Loading sub module "xaa"
[     8.627] (II) LoadModule: "xaa"
[     8.628] (II) Loading /usr/lib/xorg/modules/libxaa.so
[     8.632] (II) Module xaa: vendor="X.Org Foundation"
[     8.632]     compiled for 1.11.3, module version = 1.2.1
[     8.632]     ABI class: X.Org Video Driver, version 11.0
[     8.632] (II) SIS(0): 2D acceleration enabled
[     8.632] (II) UnloadModule: "vesa"
[     8.632] (II) Unloading vesa
[     8.632] (II) UnloadModule: "fbdev"
[     8.632] (II) Unloading fbdev
[     8.632] (II) UnloadModule: "fbdevhw"
[     8.632] (II) Unloading fbdevhw
[     8.632] (--) Depth 24 pixmap format is 32 bpp
[     8.632] (II) Loading sub module "vbe"
[     8.632] (II) LoadModule: "vbe"
[     8.632] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     8.635] (II) Module vbe: vendor="X.Org Foundation"
[     8.635]     compiled for 1.11.3, module version = 1.1.0
[     8.635]     ABI class: X.Org Video Driver, version 11.0
[     8.635] (II) Loading sub module "int10"
[     8.635] (II) LoadModule: "int10"
[     8.635] (II) Loading /usr/lib/xorg/modules/libint10.so
[     8.637] (II) Module int10: vendor="X.Org Foundation"
[     8.637]     compiled for 1.11.3, module version = 1.0.0
[     8.637]     ABI class: X.Org Video Driver, version 11.0
[     8.637] (II) SIS(0): initializing int10
[     8.639] (II) SIS(0): Primary V_BIOS segment is: 0xc000
[     8.640] (II) SIS(0): VESA BIOS detected
[     8.640] (II) SIS(0): VESA VBE Version 3.0
[     8.640] (II) SIS(0): VESA VBE Total Mem: 16384 kB
[     8.640] (II) SIS(0): VESA VBE OEM: SiS
[     8.640] (II) SIS(0): VESA VBE OEM Software Rev: 1.0
[     8.640] (II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[     8.640] (II) SIS(0): VESA VBE OEM Product: 6330
[     8.640] (II) SIS(0): VESA VBE OEM Product Rev: 2.27.g8
[     9.070] (II) SIS(0): Setting standard mode 0x64
[    10.116] (II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
[    10.299] (II) SIS(0): RENDER acceleration enabled
[    10.299] (II) SIS(0): Framebuffer from (0,0) to (1023,16238)
[    10.299] (II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
[    10.299]     Screen to screen bit blits
[    10.299]     Solid filled rectangles
[    10.299]     8x8 mono pattern filled rectangles
[    10.299]     8x8 color pattern filled rectangles
[    10.299]     Solid Lines
[    10.299]     Dashed Lines
[    10.301]     Setting up tile and stipple cache:
[    10.301]         32 128x128 slots
[    10.301]         32 256x256 slots
[    10.301]         16 512x512 slots
[    10.301]         32 8x8 color pattern slots
[    10.301] (--) SIS(0): CPU frequency 1600.00Mhz
[    10.304] (II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
[    10.316] (--) SIS(0):     Checked libc memcpy()...     355.6 MiB/s
[    10.326] (--) SIS(0):     Checked built-in-1 memcpy()...     356.4 MiB/s
[    10.365] (--) SIS(0):     Checked built-in-2 memcpy()...     76.0 MiB/s
[    10.375] (--) SIS(0):     Checked MMX memcpy()...     361.3 MiB/s
[    10.386] (--) SIS(0):     Checked 3DNow! memcpy()...     351.5 MiB/s
[    10.396] (--) SIS(0):     Checked MMX2 memcpy()...     457.1 MiB/s
[    10.397] (--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
[    10.398] (--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
[    10.398] (==) SIS(0): Backing store disabled
[    10.398] (==) SIS(0): Silken mouse enabled
[    10.398] (==) SIS(0): DPMS enabled
[    10.398] (II) SIS(0): Using SiS300/315/330/340 series HW Xv
[    10.399] (II) SIS(0): Default Xv adaptor is Video Overlay
[    10.428] (II) SIS(0): Initialized SISCTRL extension version 0.1
[    10.428] (II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
[    10.428] (==) RandR enabled
[    10.428] (II) Initializing built-in extension Generic Event Extension
[    10.428] (II) Initializing built-in extension SHAPE
[    10.428] (II) Initializing built-in extension MIT-SHM
[    10.428] (II) Initializing built-in extension XInputExtension
[    10.428] (II) Initializing built-in extension XTEST
[    10.428] (II) Initializing built-in extension BIG-REQUESTS
[    10.428] (II) Initializing built-in extension SYNC
[    10.428] (II) Initializing built-in extension XKEYBOARD
[    10.428] (II) Initializing built-in extension XC-MISC
[    10.428] (II) Initializing built-in extension SECURITY
[    10.428] (II) Initializing built-in extension XINERAMA
[    10.428] (II) Initializing built-in extension XFIXES
[    10.428] (II) Initializing built-in extension RENDER
[    10.429] (II) Initializing built-in extension RANDR
[    10.429] (II) Initializing built-in extension COMPOSITE
[    10.429] (II) Initializing built-in extension DAMAGE
[    10.443] (II) AIGLX: Screen 0 is not DRI2 capable
[    10.444] (II) AIGLX: Screen 0 is not DRI capable
[    10.635] (II) AIGLX: Loaded and initialized swrast
[    10.635] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    10.660] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.666] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    10.666] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.666] (II) LoadModule: "evdev"
[    10.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.672] (II) Module evdev: vendor="X.Org Foundation"
[    10.672]     compiled for 1.11.3, module version = 2.7.0
[    10.672]     Module class: X.Org XInput Driver
[    10.672]     ABI class: X.Org XInput driver, version 16.0
[    10.672] (II) Using input driver 'evdev' for 'Power Button'
[    10.672] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.672] (**) Power Button: always reports core events
[    10.672] (**) evdev: Power Button: Device: "/dev/input/event3"
[    10.672] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.672] (--) evdev: Power Button: Found keys
[    10.672] (II) evdev: Power Button: Configuring as keyboard
[    10.672] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    10.672] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.672] (**) Option "xkb_rules" "evdev"
[    10.672] (**) Option "xkb_model" "pc105"
[    10.672] (**) Option "xkb_layout" "fi"
[    10.676] (II) XKB: reuse xkmfile /var/lib/xkb/server-F30D752BAEAAD4B8C79BE2C421539A0D3700902C.xkm
[    10.678] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.679] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.679] (II) Using input driver 'evdev' for 'Power Button'
[    10.679] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.679] (**) Power Button: always reports core events
[    10.679] (**) evdev: Power Button: Device: "/dev/input/event1"
[    10.679] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.679] (--) evdev: Power Button: Found keys
[    10.679] (II) evdev: Power Button: Configuring as keyboard
[    10.679] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    10.679] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    10.679] (**) Option "xkb_rules" "evdev"
[    10.679] (**) Option "xkb_model" "pc105"
[    10.679] (**) Option "xkb_layout" "fi"
[    10.680] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    10.680] (II) No input driver specified, ignoring this device.
[    10.680] (II) This device may have been added with another device file.
[    10.680] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    10.681] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    10.681] (II) Using input driver 'evdev' for 'Sleep Button'
[    10.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.681] (**) Sleep Button: always reports core events
[    10.681] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    10.681] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    10.681] (--) evdev: Sleep Button: Found keys
[    10.681] (II) evdev: Sleep Button: Configuring as keyboard
[    10.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    10.681] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    10.681] (**) Option "xkb_rules" "evdev"
[    10.681] (**) Option "xkb_model" "pc105"
[    10.681] (**) Option "xkb_layout" "fi"
[    10.682] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    10.682] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.682] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.682] (**) AT Translated Set 2 keyboard: always reports core events
[    10.682] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    10.682] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.682] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.682] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.683] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    10.683] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    10.683] (**) Option "xkb_rules" "evdev"
[    10.683] (**) Option "xkb_model" "pc105"
[    10.683] (**) Option "xkb_layout" "fi"
[    10.684] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    10.684] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    10.684] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    10.684] (II) LoadModule: "synaptics"
[    10.685] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.687] (II) Module synaptics: vendor="X.Org Foundation"
[    10.687]     compiled for 1.11.3, module version = 1.6.2
[    10.687]     Module class: X.Org XInput Driver
[    10.687]     ABI class: X.Org XInput driver, version 16.0
[    10.687] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    10.687] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.687] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.687] (**) Option "Device" "/dev/input/event5"
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    10.687] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.687] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.687] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    10.687] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    10.687] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    10.687] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    10.687] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    10.688] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    10.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    10.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    10.688] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    10.688] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.688] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    10.688] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

---

### Post by Bashing-om on 2013-12-22
hemu79; Well,

Looks to be a bit better; still :
> 
video overlay support is very limited on this machine


And as well this:
> 
 7.619] (==) SIS(0): DRI disabled
[ 7.619] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[ 7.619] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".

Looksee:
```

cat /proc/cpuinfo

```
in the flags field, do you see pae, sse, and sse2 ?

Again I say, it is amazing what I do not know

---

### Post by hemu79 on 2013-12-22
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up lah

... seems to be all, edited the post, there was a second line also :)

Hermanni

---

### Post by hemu79 on 2013-12-22
I was able to enable sse with xorg.conf -file. GtkPerf is now 15.5 sec. 

and this is xorg.0.log

[     7.609] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     7.609] X Protocol Version 11, Revision 0
[     7.609] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[     7.609] Current Operating System: Linux ubuntu 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:38:12 UTC 2013 i686
[     7.609] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=972c86f9-ca9a-4e10-831a-7bee979ca60a ro elevator=noop quiet splash vt.handoff=7
[     7.609] Build Date: 16 October 2013  04:45:22PM
[     7.609] xorg-server 2:1.11.4-0ubuntu10.14 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     7.609] Current version of pixman: 0.24.4
[     7.609]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     7.609] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.609] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 22 22:44:53 2013
[     7.609] (==) Using config file: "/etc/X11/xorg.conf"
[     7.609] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     7.714] (==) No Layout section.  Using the first Screen section.
[     7.735] (**) |-->Screen "LaptopScreen" (0)
[     7.735] (**) |   |-->Monitor "Configured Monitor"
[     7.735] (**) |   |-->Device "SiSVideoCard"
[     7.735] (==) Automatically adding devices
[     7.735] (==) Automatically enabling devices
[     7.735] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     7.735]     Entry deleted from font path.
[     7.735] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     7.735] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     7.735] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     7.736] (II) Loader magic: 0x7265a0
[     7.736] (II) Module ABI versions:
[     7.736]     X.Org ANSI C Emulation: 0.4
[     7.736]     X.Org Video Driver: 11.0
[     7.736]     X.Org XInput driver : 16.0
[     7.736]     X.Org Server Extension : 6.0
[     7.736] (--) PCI:*(0:1:0:0) 1039:6330:1025:0083 rev 0, Mem @ 0xe8000000/134217728, 0xe2100000/131072, I/O @ 0x0000a000/128
[     7.737] (II) Open ACPI successful (/var/run/acpid.socket)
[     7.737] (II) LoadModule: "extmod"
[     7.743] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     7.743] (II) Module extmod: vendor="X.Org Foundation"
[     7.743]     compiled for 1.11.3, module version = 1.0.0
[     7.743]     Module class: X.Org Server Extension
[     7.743]     ABI class: X.Org Server Extension, version 6.0
[     7.743] (II) Loading extension MIT-SCREEN-SAVER
[     7.743] (II) Loading extension XFree86-VidModeExtension
[     7.743] (II) Loading extension XFree86-DGA
[     7.743] (II) Loading extension DPMS
[     7.743] (II) Loading extension XVideo
[     7.743] (II) Loading extension XVideo-MotionCompensation
[     7.743] (II) Loading extension X-Resource
[     7.743] (II) LoadModule: "dbe"
[     7.744] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     7.744] (II) Module dbe: vendor="X.Org Foundation"
[     7.744]     compiled for 1.11.3, module version = 1.0.0
[     7.744]     Module class: X.Org Server Extension
[     7.744]     ABI class: X.Org Server Extension, version 6.0
[     7.744] (II) Loading extension DOUBLE-BUFFER
[     7.744] (II) LoadModule: "glx"
[     7.744] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     7.744] (II) Module glx: vendor="X.Org Foundation"
[     7.745]     compiled for 1.11.3, module version = 1.0.0
[     7.745]     ABI class: X.Org Server Extension, version 6.0
[     7.745] (==) AIGLX enabled
[     7.745] (II) Loading extension GLX
[     7.745] (II) LoadModule: "record"
[     7.745] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     7.745] (II) Module record: vendor="X.Org Foundation"
[     7.745]     compiled for 1.11.3, module version = 1.13.0
[     7.745]     Module class: X.Org Server Extension
[     7.745]     ABI class: X.Org Server Extension, version 6.0
[     7.745] (II) Loading extension RECORD
[     7.745] (II) LoadModule: "dri"
[     7.745] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     7.746] (II) Module dri: vendor="X.Org Foundation"
[     7.746]     compiled for 1.11.3, module version = 1.0.0
[     7.746]     ABI class: X.Org Server Extension, version 6.0
[     7.746] (II) Loading extension XFree86-DRI
[     7.746] (II) LoadModule: "dri2"
[     7.746] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     7.746] (II) Module dri2: vendor="X.Org Foundation"
[     7.746]     compiled for 1.11.3, module version = 1.2.0
[     7.746]     ABI class: X.Org Server Extension, version 6.0
[     7.746] (II) Loading extension DRI2
[     7.746] (II) LoadModule: "sis"
[     7.747] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[     7.747] (II) Module sis: vendor="X.Org Foundation"
[     7.747]     compiled for 1.11.3, module version = 0.10.3
[     7.747]     Module class: X.Org Video Driver
[     7.747]     ABI class: X.Org Video Driver, version 11.0
[     7.747] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[     7.747] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[     7.747] (++) using VT number 7

[     7.747] (WW) Falling back to old probe method for sis
[     7.747] (--) Assigning device section with no busID to primary device
[     7.747] (--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
[     7.747] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[     7.747] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.11.3.0)
[     7.747] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[     7.747] (II) SIS(0): *** See [http://www.winischhofer.eu/linuxsisvga.shtml](http://www.winischhofer.eu/linuxsisvga.shtml)
[     7.747] (II) SIS(0): *** for documentation and updates.
[     7.748] (--) SIS(0): sisfb not found
[     7.748] (--) SIS(0): Relocated I/O registers at 0xA000
[     7.748] (II) Loading sub module "ramdac"
[     7.748] (II) LoadModule: "ramdac"
[     7.748] (II) Module "ramdac" already built-in
[     7.748] (II) SIS(0): Creating default Display subsection in Screen section
    "LaptopScreen" for depth/fbbpp 24/32
[     7.748] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[     7.748] (==) SIS(0): RGB weight 888
[     7.748] (==) SIS(0): Default visual is TrueColor
[     7.748] (--) SIS(0): Video BIOS version "2.27.g8" found (new SiS data layout)
[     7.748] (**) SIS(0): Option "EnableSiSCtrl" "yes"
[     7.748] (**) SIS(0): Option "UseSSE" "yes"
[     7.748] (==) SIS(0): Using XAA acceleration architecture
[     7.748] (==) SIS(0): Using HW cursor
[     7.748] (==) SIS(0): Color HW cursor is enabled
[     7.748] (II) SIS(0): Using VRAM command queue, size 512k
[     7.748] (==) SIS(0): Hotkey display switching is enabled
[     7.748] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[     7.749] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[     7.749] (**) SIS(0): SiSCtrl utility interface is enabled
[     7.749] (**) SIS(0): Will eventually use SSE CPU instructions
[     7.749] (==) SIS(0): DRI disabled
[     7.749] (WW) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[     7.749] (WW) SIS(0): If you get a signal 4 here, set the option "UseSSE" to "off".
[     7.749] (--) SIS(0): 65536K shared video RAM (UMA)
[     7.749] (--) SIS(0): DRAM type: DDR SDRAM
[     7.749] (--) SIS(0): Memory clock: 198.861 MHz
[     7.749] (--) SIS(0): DRAM bus width: 64 bit
[     7.749] (--) SIS(0): Linear framebuffer at 0xE8000000
[     7.749] (--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
[     7.749] (--) SIS(0): VideoRAM: 65536 KB
[     7.749] (II) SIS(0): Using 64960K of framebuffer memory at offset 0K
[     7.749] (--) SIS(0): Hardware supports two video overlays
[     7.749] (II) SIS(0): 
    Dear SiS76x user, your machine is using a shared memory framebuffer.
    Due to hardware limitations of the SiS chip in combination with the
    AMD CPU, video overlay support is very limited on this machine. If you
    experience flashing lines in the video and/or the graphics display
    during video playback, reduce the color depth and/or the resolution
    and/or the refresh rate. Alternatively, use the video blitter.
[     7.749] (--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
[     8.771] (--) SIS(0): No CRT1/VGA detected
[     8.771] (--) SIS(0): Detected LCD/plasma panel (1024x768, 0, non-exp., RGB18 [02c100])
[     8.771] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.771] (II) SIS(0): CRT1 gamma correction is enabled
[     8.771] (II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
[     8.771] (II) SIS(0): CRT2 gamma correction is enabled
[     8.771] (--) SIS(0): Memory bandwidth at 32 bpp is 397.722 MHz
[     8.771] (--) SIS(0): Detected LCD PanelDelayCompensation 0x0c (for LCD=CRT2)
[     8.771] (--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
[     8.771] (II) Loading sub module "ddc"
[     8.771] (II) LoadModule: "ddc"
[     8.771] (II) Module "ddc" already built-in
[     8.771] (--) SIS(0): CRT2 DDC probing failed
[     8.771] (==) SIS(0): Min pixel clock is 10 MHz
[     8.771] (--) SIS(0): Max pixel clock is 290 MHz
[     8.771] (II) SIS(0): Replaced entire mode list with built-in modes
[     8.771] (II) SIS(0): Correcting missing CRT2 monitor HSync range
[     8.771] (II) SIS(0): Correcting missing CRT2 monitor VRefresh range
[     8.771] (II) SIS(0): "Unknown reason" in the following list means that the mode
[     8.771] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[     8.771] (II) SIS(0): Configured Monitor: Using hsync range of 30.00-80.00 kHz
[     8.771] (II) SIS(0): Configured Monitor: Using vrefresh range of 59.00-61.00 Hz
[     8.771] (II) SIS(0): Configured Monitor: Using vrefresh value of 71.00 Hz
[     8.771] (WW) SIS(0): Unable to estimate virtual size
[     8.771] (II) SIS(0): Clock range:  10.00 to 290.64 MHz
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[     8.771] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[     8.771] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[     8.771] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.771] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
[     8.772] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x720" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x768" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
[     8.772] (II) SIS(0): Not using default mode "1360x768" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x800" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1680x1050" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1920x1080" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.772] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[     8.772] (--) SIS(0): Virtual size is 1024x768 (pitch 1024)
[     8.772] (**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[     8.772] (**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[     8.772] (**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
[     8.772] (**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
[     8.772] (**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
[     8.772] (**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
[     8.772] (**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
[     8.772] (**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
[     8.772] (**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
[     8.772] (**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
[     8.772] (**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
[     8.772] (**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
[     8.772] (**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
[     8.772] (**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
[     8.772] (**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
[     8.772] (**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
[     8.772] (**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
[     8.772] (==) SIS(0): DPI set to (96, 96)
[     8.772] (II) Loading sub module "fb"
[     8.772] (II) LoadModule: "fb"
[     8.773] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.773] (II) Module fb: vendor="X.Org Foundation"
[     8.773]     compiled for 1.11.3, module version = 1.0.0
[     8.773]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.773] (II) Loading sub module "xaa"
[     8.773] (II) LoadModule: "xaa"
[     8.773] (II) Loading /usr/lib/xorg/modules/libxaa.so
[     8.773] (II) Module xaa: vendor="X.Org Foundation"
[     8.773]     compiled for 1.11.3, module version = 1.2.1
[     8.773]     ABI class: X.Org Video Driver, version 11.0
[     8.773] (II) SIS(0): 2D acceleration enabled
[     8.774] (--) Depth 24 pixmap format is 32 bpp
[     8.774] (II) Loading sub module "vbe"
[     8.774] (II) LoadModule: "vbe"
[     8.774] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     8.774] (II) Module vbe: vendor="X.Org Foundation"
[     8.774]     compiled for 1.11.3, module version = 1.1.0
[     8.774]     ABI class: X.Org Video Driver, version 11.0
[     8.774] (II) Loading sub module "int10"
[     8.774] (II) LoadModule: "int10"
[     8.774] (II) Loading /usr/lib/xorg/modules/libint10.so
[     8.774] (II) Module int10: vendor="X.Org Foundation"
[     8.774]     compiled for 1.11.3, module version = 1.0.0
[     8.774]     ABI class: X.Org Video Driver, version 11.0
[     8.774] (II) SIS(0): initializing int10
[     8.775] (II) SIS(0): Primary V_BIOS segment is: 0xc000
[     8.777] (II) SIS(0): VESA BIOS detected
[     8.777] (II) SIS(0): VESA VBE Version 3.0
[     8.777] (II) SIS(0): VESA VBE Total Mem: 16384 kB
[     8.777] (II) SIS(0): VESA VBE OEM: SiS
[     8.777] (II) SIS(0): VESA VBE OEM Software Rev: 1.0
[     8.777] (II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[     8.777] (II) SIS(0): VESA VBE OEM Product: 6330
[     8.777] (II) SIS(0): VESA VBE OEM Product Rev: 2.27.g8
[     9.205] (II) SIS(0): Setting standard mode 0x64
[    10.043] (II) SIS(0): SiS76x/UMA: two video overlay(s) available in current mode
[    10.068] (II) SIS(0): RENDER acceleration enabled
[    10.068] (II) SIS(0): Framebuffer from (0,0) to (1023,16238)
[    10.068] (II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
[    10.068]     Screen to screen bit blits
[    10.068]     Solid filled rectangles
[    10.068]     8x8 mono pattern filled rectangles
[    10.068]     8x8 color pattern filled rectangles
[    10.068]     Solid Lines
[    10.068]     Dashed Lines
[    10.070]     Setting up tile and stipple cache:
[    10.070]         32 128x128 slots
[    10.070]         32 256x256 slots
[    10.070]         16 512x512 slots
[    10.070]         32 8x8 color pattern slots
[    10.070] (--) SIS(0): CPU frequency 1600.00Mhz
[    10.073] (II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
[    10.085] (--) SIS(0):     Checked libc memcpy()...     342.1 MiB/s
[    10.096] (--) SIS(0):     Checked built-in-1 memcpy()...     338.8 MiB/s
[    10.134] (--) SIS(0):     Checked built-in-2 memcpy()...     73.9 MiB/s
[    10.145] (--) SIS(0):     Checked MMX memcpy()...     340.7 MiB/s
[    10.155] (--) SIS(0):     Checked SSE memcpy()...     472.1 MiB/s
[    10.166] (--) SIS(0):     Checked 3DNow! memcpy()...     349.0 MiB/s
[    10.176] (--) SIS(0):     Checked MMX2 memcpy()...     446.0 MiB/s
[    10.178] (--) SIS(0): Using SSE method for aligned data transfers to video RAM
[    10.178] (--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
[    10.178] (==) SIS(0): Backing store disabled
[    10.178] (==) SIS(0): Silken mouse enabled
[    10.178] (==) SIS(0): DPMS enabled
[    10.178] (II) SIS(0): Using SiS300/315/330/340 series HW Xv
[    10.178] (II) SIS(0): Default Xv adaptor is Video Overlay
[    10.208] (II) SIS(0): Initialized SISCTRL extension version 0.1
[    10.208] (II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
[    10.208] (==) RandR enabled
[    10.208] (II) Initializing built-in extension Generic Event Extension
[    10.208] (II) Initializing built-in extension SHAPE
[    10.208] (II) Initializing built-in extension MIT-SHM
[    10.208] (II) Initializing built-in extension XInputExtension
[    10.208] (II) Initializing built-in extension XTEST
[    10.208] (II) Initializing built-in extension BIG-REQUESTS
[    10.208] (II) Initializing built-in extension SYNC
[    10.208] (II) Initializing built-in extension XKEYBOARD
[    10.208] (II) Initializing built-in extension XC-MISC
[    10.208] (II) Initializing built-in extension SECURITY
[    10.208] (II) Initializing built-in extension XINERAMA
[    10.208] (II) Initializing built-in extension XFIXES
[    10.208] (II) Initializing built-in extension RENDER
[    10.208] (II) Initializing built-in extension RANDR
[    10.208] (II) Initializing built-in extension COMPOSITE
[    10.208] (II) Initializing built-in extension DAMAGE
[    10.222] (II) AIGLX: Screen 0 is not DRI2 capable
[    10.222] (II) AIGLX: Screen 0 is not DRI capable
[    10.246] (II) AIGLX: Loaded and initialized swrast
[    10.246] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    10.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.269] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    10.269] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.269] (II) LoadModule: "evdev"
[    10.270] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.270] (II) Module evdev: vendor="X.Org Foundation"
[    10.270]     compiled for 1.11.3, module version = 2.7.0
[    10.270]     Module class: X.Org XInput Driver
[    10.270]     ABI class: X.Org XInput driver, version 16.0
[    10.270] (II) Using input driver 'evdev' for 'Power Button'
[    10.270] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.270] (**) Power Button: always reports core events
[    10.270] (**) evdev: Power Button: Device: "/dev/input/event3"
[    10.270] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.270] (--) evdev: Power Button: Found keys
[    10.270] (II) evdev: Power Button: Configuring as keyboard
[    10.271] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    10.271] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.271] (**) Option "xkb_rules" "evdev"
[    10.271] (**) Option "xkb_model" "pc105"
[    10.271] (**) Option "xkb_layout" "fi"
[    10.275] (II) XKB: reuse xkmfile /var/lib/xkb/server-F30D752BAEAAD4B8C79BE2C421539A0D3700902C.xkm
[    10.277] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.277] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.277] (II) Using input driver 'evdev' for 'Power Button'
[    10.277] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.277] (**) Power Button: always reports core events
[    10.277] (**) evdev: Power Button: Device: "/dev/input/event1"
[    10.277] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.277] (--) evdev: Power Button: Found keys
[    10.277] (II) evdev: Power Button: Configuring as keyboard
[    10.277] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    10.277] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    10.277] (**) Option "xkb_rules" "evdev"
[    10.277] (**) Option "xkb_model" "pc105"
[    10.277] (**) Option "xkb_layout" "fi"
[    10.278] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    10.278] (II) No input driver specified, ignoring this device.
[    10.278] (II) This device may have been added with another device file.
[    10.279] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    10.279] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    10.279] (II) Using input driver 'evdev' for 'Sleep Button'
[    10.279] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.279] (**) Sleep Button: always reports core events
[    10.279] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    10.279] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    10.279] (--) evdev: Sleep Button: Found keys
[    10.279] (II) evdev: Sleep Button: Configuring as keyboard
[    10.279] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    10.279] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    10.279] (**) Option "xkb_rules" "evdev"
[    10.279] (**) Option "xkb_model" "pc105"
[    10.279] (**) Option "xkb_layout" "fi"
[    10.280] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    10.280] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.280] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.280] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.280] (**) AT Translated Set 2 keyboard: always reports core events
[    10.281] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    10.281] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.281] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.281] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.281] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    10.281] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    10.281] (**) Option "xkb_rules" "evdev"
[    10.281] (**) Option "xkb_model" "pc105"
[    10.281] (**) Option "xkb_layout" "fi"
[    10.282] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    10.282] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    10.282] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    10.282] (II) LoadModule: "synaptics"
[    10.283] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.283] (II) Module synaptics: vendor="X.Org Foundation"
[    10.283]     compiled for 1.11.3, module version = 1.6.2
[    10.283]     Module class: X.Org XInput Driver
[    10.283]     ABI class: X.Org XInput driver, version 16.0
[    10.283] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    10.283] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.283] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.283] (**) Option "Device" "/dev/input/event5"
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    10.283] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.283] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.283] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    10.283] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[    10.283] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    10.283] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    10.283] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    10.284] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    10.284] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    10.284] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    10.284] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    10.284] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.284] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    10.284] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"

---

### Post by Bashing-om on 2013-12-22
hemu79; Well,

That output looks pretty good, I notice nothing else to address.

I hope all is fine now.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by hemu79 on 2013-12-23
Everythigs fine, system is running smoothly. Thank you million times for all the help. 

Happy Holidays,

                Hermanni

---

### Post by Bashing-om on 2013-12-23
hemu79; Great !

You did all the work ! .. Pleased as all get out to know there is life after "SIS".

Take care .. and will be pleased to read you next time.

to you 
[INDENT][INDENT]Merry Christmas[/INDENT][/INDENT]

---

