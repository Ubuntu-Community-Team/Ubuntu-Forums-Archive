---
title: "Live cd trouble"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by Huesos on 2007-03-20
This is very frustrating, after having heard about it and wanting to try it for some time I am very close to giving up on Ubuntu entirely. I have burned 6 live cd's, they have all taken me to the first menu and past the loading screen. But as soon as it goes blank and I expect to be welcomed into the system it leaves me hanging with a black screen.

I don't know what to do. :/

---

### Post by Lord Crow on 2007-03-20
I know how you feel and have come to the same conclusion. I have checked my CD and it's fine and get past the loading screens like yourself but then eventually I get an Activating swap error, surely someone else has the same error but its not easy to find. :(

---

### Post by wpshooter on 2007-03-20
> **Huesos said:**
> This is very frustrating, after having heard about it and wanting to try it for some time I am very close to giving up on Ubuntu entirely. I have burned 6 live cd's, they have all taken me to the first menu and past the loading screen. But as soon as it goes blank and I expect to be welcomed into the system it leaves me hanging with a black screen.

I don't know what to do. :/

First, have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Did you burn your CDs at 4X or less ?

If you have done the above, then have your tried booting using the safe graphics mode parameter ?

Does you computer already have existing O/Ss on it or is Ubuntu going to be your one and only O/S ?

---

### Post by Huesos on 2007-03-20
> **wpshooter said:**
> 

First, have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?



Yes, it said it was fine.

> **wpshooter said:**
> 

Did you burn your CDs at 4X or less ?



Less

> **wpshooter said:**
> 

If you have done the above, then have your tried booting using the safe graphics mode parameter ?



Countless times

> **wpshooter said:**
> 

Does you computer already have existing O/Ss on it or is Ubuntu going to be your one and only O/S ? 

It has Windows XP installed on one of its disks, the computer has three. I was planning to dual boot and have the third disk work as one where I could reach files from both systems.

---

### Post by wpshooter on 2007-03-20
What are your computer specs, how much memory do you have ?

You might want to try either the ALTERNATE (text based) CD or if you system is short on memory you may want to consider Xubuntu.

---

### Post by Huesos on 2007-03-20
> **wpshooter said:**
> What are your computer specs, how much memory do you have ?

You might want to try either the ALTERNATE (text based) CD or if you system is short on memory you may want to consider Xubuntu.

AMD 64
200gb Seagate SATA + 80gb Seagate SATA + 80 gb Hitachi IDE3,5
ATI Radeon

---

### Post by eapache on 2007-03-20
If you have a radeon graphics card, then that is definitely the trouble. There is a problem  with the ATI driver in the install cd that is fairly easy to fix. Please do post your specs though, because there may be other incompatibility issues.

EDIT
--------
This problem has been floating around for a while, and here is a working solution:
> This is a big old problem with ATI graphics on the Ubuntu install, though I didn't think it went as far back as that card basically the driver called "ATI" that Ubuntu defaults to doesn't usually work by itself, even though other distros do it out the box. It is, though, fairly easy to get working again.

On the first boot screen (the one giving you boot options) press F6 to edit the boot options line.

Delete "quiet - splash" and type in "break=bottom". This will rid of the fancy looking ubuntu loading bar and give you a command line half way through booting.

When you get the command line type "chroot /root nano etc/X11/xorg.conf". This will bring up your xorg.conf file, which is the file that Ubuntu uses to set up your graphics. Scroll down the page until you see a heading called "Device".

There should be a sub-heading under this called "Driver" with the driver listed to the right. This will probably be "ATI" (the faulty driver), now change it to "radeon" (this driver should work but, if it doesn't, repeat the steps and use the driver "vesa" instead, which gives the most basic graphics: like windows safe mode only a bit better ).

Once you've changed it press "ctrl+O" then "ctrl+X", this will bring you back to the command line. Unless you want to do anything else type in "exit", this should load up the rest of Ubuntu and, fingers crossed, your Graphics will work

I really hope they fix this bug soon as I've posted the work-around about ten times now, and that's after I've found it myself in the forum

---

### Post by wpshooter on 2007-03-20
Huesos:

I am sort of doubting that the ATI Radeon 9600 is the problem.  The very machine that I am typing this on has an ATI Radeon 9600 in it and I installed Dapper on it with basically no problems other than needing to switch to the fglrx drivers after I had gotten the O/S installed (I was getting an Out of Range message at each boot).

What version of Ubuntu are you trying to install & is it 32 bit version or 64 bit version ?

Thanks.

---

### Post by Huesos on 2007-03-20
Thankyou very much!

I apologize, I looked for solutions for this problem and didn't fint so much as a tip, you're the first one to give me a possible reason for the screw-ups. Anyhow, thanks agian.

---

### Post by wpshooter on 2007-03-20
Heusos:

I just looked at your specs. again and I think I may see your problem.

Please try this.  I would suggest that you (at least at first) download, burn and try the 32bit version of either Dapper or Edgy.

Then after you have done that (make sure you check the integritiy of the Cd) and then before you attempt to install the Ubuntu O/S (humor me and unplug the hard drive in your system - probably the IDE, that you do not plan on putting Ubuntu on) and then try to install Ubuntu.

I **THINK** that certain versions of Ubuntu may NOT like systems that have two different drive types in them.

Good luck.

---

### Post by Huesos on 2007-03-20
Eapache: It seemed to work right up untill the point of startup. Then then the screen turned blue and there was a warning that said there was a problem with server x which appearantly means there are craphical configurations that are causing problems. Yet, I did everything you said... :(

---

### Post by thunkt on 2007-03-21
Hi guys, 

My first post, yay!

I'm getting exactly the same problem. I've previously installed ubuntu 32bit ed on my laptop and had no worries at all. After finding it to be such a beautifully simple process as compared to the gentoo installation, (which I love to bits, but don't have time for anymore) I went ahead and downloaded kubuntu 64bit ed. for my desktop. I'm getting exactly the same problem as the OP, except I have no second HD, and an Nvidia card as opposed to the Radeon. I have just installed Vista on the box, which I can't see as being the problem. I get the blue progress bar, after the initial menu, then my screen simply goes black. If I ctrl+alt+backspace to reboot, the progress bar comes back in it's unload fashion, but with funky colours, so I'm assuming the problem has to do with the video card. 

My specs include :
AMD x64
1gb RAM
NVIDIA 6800 GS
WD 160gb SATA HD

Any help would be greatly appreciated.

Thanks very much.

P.S. And a big thanks to the devs of such a fine distro!! You guys are bringing linux to the masses. Cheers.

---

### Post by EineBeBoP on 2007-03-21
Im having the same problem I'm afraid. 

Boot from cd, have it start and I get the loading bars, but then it goes black after several minutes. Nothing happens after that.

AMD 64 3200+
1gb of ram
ATI X800 Pro
With a 200gb IDE and a 300 Sata drive

Thanks for any help guys.

---

### Post by mrn1c3 on 2007-03-21
I am having exactly the same problem as everyone else here, and have near enough the same setup as EineBeBoP.


AMD 64bit 3000
1 Gig Ram
ATI X850
200 gig SATA / 200gig IDE


Same symptoms when booting from the VERY LATEST 32bit live install CD.

is it worth pulling the 64 bit version down, and trying that?

---

### Post by Huesos on 2007-03-21
I hope this thing gets fixed before the next release... :(

---

### Post by dannyboy79 on 2007-03-21
WOW, everyone is having this issue. I too have it. Although I don't want to install Edgy Eft 6.10 Live CD version, I merely was trying to use linux to see a windows hard drive that has the NTLDR is missing error. I tried various methods to FIXBOOT, use the ATTRIB command, copy files to it's root drive but no, windows won't boot. Anyway, back to the Live CD problem at hand. 

**Setup**
~Asus P4P800-E Deluxe (Bios 1009, i think)
   -North Bridge Intel® 865PE Memory Controller Hub (MCH); 
   -South Bridge Intel® Intel 82801ER Enhanced I/O Controller Hub (ICH5R); 
   -Interbridge link: Hub Link v1.5;
   -AGP 4x/8x
~Intel P4 Prescott 2.8E (originally overclocked 20% using asus option BUT I ended up clicking on the global setting to make it all default, NOT optimum or best, but standard or default. this depends on bios)
~ATI AIW 9800 Pro, DVI Interface (AGP 4X/8X) 
~1.5gb RAM (Kingston Value Ram)
~2 Optical Drives (Toshiba as slave and NEC as master both on ide0 [ide1 not being used])
~Floppy (unknown)
~120gb Samsung Sata drive-simply NTFS storage for my winbloz xp pro box (connected to ICH5R controller)
~Synergy714 17" flat panel monitor (DVI)
~iogear mini-kvm 2 computers ([http://www.iogear.com/main.php?loc=product&Item=GCS612A&name=MiniView&#8482;%20Micro%20PS/2%20Audio%20KVM%20Switch](http://www.iogear.com/main.php?loc=product&Item=GCS612A&name=MiniView&#8482;%20Micro%20PS/2%20Audio%20KVM%20Switch))
~wireless (RF, ps/2) mouse and dell keyboard (ps/2) plugged into kvm (wireless keyboard is acting weird so not using it) [[http://www.newegg.com/Product/Product.aspx?Item=N82E16823201019]](http://www.newegg.com/Product/Product.aspx?Item=N82E16823201019]) this is the same model I have but when I bought it, the wireless module box had 2 ps/2 connectors instead of 1 usb!
~80gb sata windows hard drive-OS=Windows Media Center-1 fat16 partition, 1 NTFS partition, 1 fat32 partition (originally connected to Promise controller BUT switched it to ICH5R)
~originally had left all usb plugs in, printers, usb extender cables, etc, etc BUT removed them all and ran bare min! keyboard connected to kvm and RF wireless mouse to kvm as well and monitor staright to box. See I only use the kvm for mouse and keyboard because my monitor has 2 inputs, so i just use the input button on the front of the monitor and hit scroll lock twice and I am in my other computer. i love it.

No matter what I did I could NOT boot any live cd, I tried Knoppix (i think 5.0), DSL (latest as of 3-17-07), Puppy (latest 3-17-07), Edgy and everyone either stalled during bootup or ended up at the infamous black screen that doesn't do s__t. NO, ctrl-alt-F1 thru F6 didn't bring up a console, and no vga= didn't do anything, trying boot to safe mode didn't work either. Even tried to remove "splash" and then add break=bottom after the "--". I followed this guide: [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)
but even when I got to the initramfs and used the command as noted, I get an error that says that nano doesn't exist. YES, I did verify the cd and I checked my RAM. All ok!! I was like come on, I can't win!!!!!! So, I was thinking to myself, gosh what else can I try.  Well I read somewhere that you can add other options for "broken bios" but I knew my bios wasn't broken but I figured, I'll try anything!!! I did what the above guide said but also added noapic and nolapic to see what would happen. Still it either wouldn't make it to the initramfs or nano didn't exist? Then I remember reading that people suggested removing all devices like usb devices plugged in etc etc, just base min, keyboard, mouse, monitor. I also thought I would try a different sata port as my motherboard has 4 total, 2 of them are built into the ICH5R and 2 are on a promise controller. I had the windows drive in the promise port and the other storage NTFS drive in the built in sata port. I thought maybe I'll not use the promise and just use the built in ones because I wasn't sure about support for the controller within the livecd. Still NOTHING!!! AWWWWWW. I have spent 3 hours total gogling and just booting live cd's and still nothing. So I happen to watch the output of it booting 1 time and it suggested trying irqpoll as a boot option and I thought, well nothing to lose. I get to the menu, click F6, edit the boot line like the above guide BUT also REMOVED quite and added irqpoll noapic nolapic AND I GOT IN!!!!!!!!! YES, I screamed as loud as I could and thought, persistance always wins out!!!!!!!!!! 

**_Let's recap some important things, at least for my situation._**
-make sure you have bare min hooked to your computer: monitor, keyboard, mouse period! (i am surprised that it worked with the kvm. i also was about to try and remove 1 of the optical drives so Ubuntu had to check less hardware)
-maybe change bios to defaults, some have reported that changing bios agp to 4x instead of 8x helps but I don't have that option in my bios. nor did I have an option for fast writes which I have also read works if you DISABLE it.
-use controllers that you know are supported by Ubuntu or the native ones (in my case I had a promise sata controller as well as a RAID ide controller built into my mb, DON'T use these, try the ones built into southbridge if you can)
-At the boot screen where it says the following: Start or Install Ubuntu, run in safe graphics mode, Check CD, boot first hard disk, memtest etc etc (see this link for awesome guide with pics: ([https://wiki.ubuntu.com/EdgyKnownIssues/59618)](https://wiki.ubuntu.com/EdgyKnownIssues/59618)), follow the guide BUT also delete "quite" and add these options if that guide alone didn't work. irqpoll noapic nolapic. so the final end of the line would be: .............../ram rw irqpoll noapic nolapic -- break=bottom  (NOTE: the "dots" just represent the begining of the boot line that doesn't need changing). There are also other options that may work if these didn't. you can also try: 
acpi=off
pci=irqroute
xmodule=vesa
vga=normal
vga=771
pci=irqroute
framebuffer=false

You should end up in Ubuntu Edgy Eft Live CD Environment!!!!!!! YEAH

There are also so many guides out there for various situations where certain things didn't work for this bug (there is also more than 1 bug so I am going to post 1 and also post the bug report to reference.
-ATI X700 on a Asus laptop Turion Amd: [http://linuxmint.com/forum/viewtopic.php?p=8065](http://linuxmint.com/forum/viewtopic.php?p=8065)
-https://launchpad.net/ubuntu/+bug/67487

(NOTE: I haven't tried to install just so that everyone realizes this, this is all only to run a live cd. So, once you're install finishes and it tells you to remove the cd and it reboots, once grub appears, you can edit that boot line also by hitting E again, just use the same options and do that same thing again using "vesa" to get into your graphical environment. Then you can install another driver or whatnot. I might suggest ENVY, it worked wonders for my GeForce 6200 but I can't speak for ATI cards as I didn't install Edgy onto this machine. This is my winbloz xp pro box, only using it to troubleshoot friends windows install. Long story short my main ubuntu box is in pieces cause I need to install the E4300 and ASRock 775dual-VSTA motherboard I just bought to replace a Celeron 2.66 and Foxconn MB both of which worked fine I am just a computer freak. I can't wait!!!! GOOD LUCK TO ALL. We should maybe sticky this if something like this isn't already!!

---

### Post by Lord Crow on 2007-03-21
I got a Dell Inspiron 9400
Intel Duo 1.83 GHz
1 GB of Ram
Mobil Intel 945 gM 

I have burnt the CD and checked it and have tried nearly every boot I can think of safe mode as well. It seems to get nearly at the end of the whole process, according to the orange bar anyway, and then it crashes in the same place everytime. From what I can make out it has something to do with the xserver and reading the faults description it seems to be the video bios and can't find a screen resolution. My laptop is a 1440x900 but none of the standard resolutions onthe boot menu works, 640x480, 800x600, 1024x768 16 and 32 bit. It seems to find my chipset no problem just not the resolution. I have read countless threads and some examples give you strings to run from the commans prompt, how do you get to the command prompt using the livecd? Sometimes after the error it goes back to a flashing cursor where I have typed in various strings but it doesn't do anything, I have read there should be a '~' but there isn't. There are people with Inspiron 9400's who have installed it but I can't. My aim is to replace windows XP which I have now if it's any good and then install the 64 bit version on my desktop but I'm nowhere near that alas. If this version is no good could you recommend one that is? I'm using the Ubuntu 6.10 32 bit btw.

---

### Post by dannyboy79 on 2007-03-21
um, this is really weird reading this especially since you post it right after I post a huge explianation about getting to a command prompt. Please re-read my thread and you'll find the answer, which will get you to a initramfs command line. From there you can edit your xorg.conf and add or change the appropriate resolutions. good luck.

Otherwise try dapper, I have read about plenty of people using this laptop with that resolution

OR


If by chance you did read my post and you can't even get to the initramfs command line, than I can't help. Did you try disabling the wifi and bluetooth button in the bios as this says: 
Possible fix for this problem -- works for me: 
(NB: This fix are for somewhat knowledged users. Others please wait for someone more 
user-oriented to post a working "easy fix" or wait for a official update that resolves the 
problem) 
 
Hardware tested on: Dell Inspiron 9400, Intel Mobile 945GM chipset (and ofcourse this 
includes the infamous Intel Pro Wireless 3945 chip). 
 
First off: I've had this problem for three weeks -- I ran into it a mere three days after getting 
my brand new laptop. I've bugged the living h*ll out of people I know who knows more about 
Ubuntu and Linux kernels than me, and I'd like to thank them for putting up with me and my 
frustrations (Berge, Tollef, Morten, et. al.). 
 
SHORT description of fix: 
Edit /etc/apt/sources.list and alter it so that it contains the Dapper sources. 
Install the 2.6.15-27-686 kernel and restricted-modules-2.6.15-27-686 packages. 
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup. 
Enter BIOS -- turn WiFi and Bluetooth completely off. 
Disable the key for switching on and off WiFi/Bluetooth. 
Reboot. 
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup. 
Reboot. 
Enter BIOS -- turn WiFi on. 
Enable the key for switching on and off WiFi only for WiFi -- not for Bluetooth. 
Reboot. 
Boot the 2.6.15-27-686 kernel and verify that you can get a sucessful bootup. 
Use the fn+f2-keycombo to enable WiFi -- push it only once. 
Open a terminal and use iwconfig to configure the WiFi-device to suit your needs. 
 
 
The longer story: 
I tried upgrading to the unstable Feisty edition: had no luck the issue was still around with the 
rf_kill unwritable in /sys, and there was no way to make fn+f2 work the way it should. Any 
pushing of the keys spewed out the errors in dmesg like so many others have reported. 
 
Then I tried to reinstall Edgy from the LiveCD and surprise, surprise, the machine froze with 
the soft lockup. To resolve this I used the Edgy ServerCD-installation and since it does not 
probe the ipw3945 at all, I got to install Edgy by hand from it. Others may want to use Dapper 
since it's a little less effort to install than a server-installation. 
 
I have tried a lot of kernels from Dapper, Edgy and Feisty (actually all vanilla kernels available I believe): 
 
    2.6.15-25-686 
    2.6.15-27-686 
    2.6.17-10-386 
    2.6.17-10-generic 
    2.6.19-7-generic 
    2.6.20-1-generic 
    2.6.20-2-generic 
    2.6.20-3-generic 
 
The issue was present with all. To resolve it I had to fiddle A LOT with the BIOS: 
 
Entering BIOS I switched off wireless completely, switched off bluetooth completely, set the 
special key for wifi/bluetooth to be disabled and rebooted. Verified that I could get 
2.6.20-2-generic (from Feisty) working and rebooted again. Back in BIOS i switched wireless 
on, set the key for wifi/bluetooth to be only for wifi enabled and rebooted again. 
 
I booted the 2.6.15-27-686 kernel from Dapper and to my big surprise I got no soft lockup. 
In a terminal I then had to use iwconfig to set parameters for the wireless card (eth1) as the 
Network Settings-utility would not allow me to configure it). 
 
Since I got WiFi working again I thought I could be so user-like stupid to push the button 
again, just to see if I could reproduce the failure; but it kept on working on the 2.6.15-27-686 
kernel. Even with being switched off and rebooted WiFi could be turned back on with the 
fn+f2-keys. (Booting the 2.6.17-10-generic kernel from Edgy ofcourse replicates the problem 
if pushing the fn+f2 switch to turn WiFi off and then booting..) 
 
In the end I've now tested rebooting and switching the WiFi on and off in 2.6.15-25-686 and 
2.6.15-27-686. The 2.6.17-10-generic kernel from Edgy gives the dmesg output about the 
keys pushed not being recognized but after adding the modified ipw3945.o-module posted 
multiple places on this forum and on launchpad.net I could get the function to work and I can 
switch the kernel on and off.

---

