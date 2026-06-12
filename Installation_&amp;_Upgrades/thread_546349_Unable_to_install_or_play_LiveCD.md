---
title: "Unable to install or play LiveCD"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by t0bbe on 2007-09-08
Just bought a new Gateway Laptop, T-6815, with Vista installed. First I tried installing XP instead of Vista, but didn't get all the drivers working (Since Gateway only provides drivers for Vista), so I thought I would try Linux for the first time. 

Downloaded and burned the Ubuntu 7.04, boots up fine then I get the error message:
"/bin/sh: can't access tty: job control turned off" 
I've searched a lot of posts on this on the forum, but couldn't find a real solution, more than to reboot or try a different version of Ubuntu.

I downloaded the alternative CD instead, it installs fine until I reboot and get the message that it cannot load my graphic drivers.
So there is obviously something wrong with my graphics drivers, as long as the installation is in text mode it works fine.

I have spent the last 3 days trying to get this computer up and running, and I would really appreciate some help!

Specs on my laptop:

Gateway T-6815
Intel Core 2 Duo T5250 
Intel 965 Express Chipset Family
1024 MB DDR2 RAM
Intel Graphics Media Accelerator X3100 with up to 384 MB of Dynamic Video Memory
160 GB Hard Drive, WDC WD1600BEVS-22RST0

Here's the error report I got:

X Window system version 7.2.0
Release date: 22 jan 2007
X protocol version 11, revision 0, release 7.2
build operation system: linux ubuntu
current operating system: linux ubuntu 2.6.20-15-generic #2 SMP Sun
Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version
module loader present
markers: (--) probed, (**) from config file (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 8 12:17:43 2007
(==) using config file: "/etc/X11/xorg.conf
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by Pumalite on 2007-09-08
Do you get a command line?. If not, then Ctrl+Alt+F1 Then:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as a driver, then
startx

---

### Post by climber0085 on 2007-09-10
I've downloaded the ubuntu 7.04 alt cd and installed.

Reconfigured the xserver-xorg.
Tried using the vesa as driver (tried many other options as well...)
Stopped and restarted the gnome desktop manager.
Restarted x and...

nothing. 

So how can I get past this? I too have the same laptop and have not found a viable solution.
Interestingly, this solution works (somewhat) on 6.10, but on 6.10 I cannot get my ethernet to to work, not even when hardwired.

I'm struggling here, please help!

---

### Post by Pumalite on 2007-09-10
Post your specs.

---

### Post by climber0085 on 2007-09-10
same as the t0bbe - Its a gateway t-6815, same core and graphics chip.

btw, thanks for the help.

---

### Post by Pumalite on 2007-09-10
Then you are going to have to tell me in details what happened with your Alternate installation.

---

### Post by climber0085 on 2007-09-10
Sorry, I'm a bit new.

I installed the system the best I could.
The entire installation went fine, complete install with the eject cd at the end.

I get the following error after grub:
kinit: name_to_dev_t (/dev/sda5)= sda5(8.5)
kinit: trying to resume from /dev/sda5
kinit: no resume image, doing normal boot.

After that, I get the blue screen.

---

### Post by Pumalite on 2007-09-10
What did you do during reconfiguring?. And do you have a working system in your computer now?.

---

### Post by climber0085 on 2007-09-10
I do have a working system on the computer now - vista ultimate, which I bought from the school.
It consumes sda2 & sda3 (I think). I'm not too attached to it.
I did repartition the old swap partition in the extended partition behind vista (partition order: linux-vista-programs-swap).

When I reconfigure the system, I allow for all the auto configurations. I do not use frame buffering. I select a 14" monitor (simple). The keyboard and mouse auto configures well.

As a side note, I installed this over a working version of opensuse 10.2. 
I just didn't like it as much - and there wasn't nearly the community support that ubuntu provides.

---

### Post by Pumalite on 2007-09-10
Get a Knoppix Live CD and see if you can boot from it: [http://www.knoppix.org/](http://www.knoppix.org/)
When you do, post: sudo fdisk -lu... and cat /boot/grub/menu.lst... from your newly installed system. (Knoppix mounts all partitions automatically). You could add your /etc/X11/xorg.conf to see how it stands at the present time.

---

### Post by climber0085 on 2007-09-11
Allright, I downloaded the Knoppix distro and obtained the files you've asked for.
Since I'm still on windows, I'm uploading them as .zip files.

---

### Post by Pumalite on 2007-09-11
I looked at your files and they all seem in order. You have a system installed. your menu.lst points to the right places and at least, to me, your xorg.conf file looks OK.
The problem might lie here:
Intel Graphics Media Accelerator X3100 with up to 384 MB of Dynamic Video Memory
And the answer might be changing something in your xorg.conf file ( if that's the case, I don't have the answer at this moment)
The only thing that occurs to me is for you guys to try Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
If not, maybe someone with more expertize tweaking the xorg file might come along.

---

### Post by climber0085 on 2007-09-12
I went ahead and downloaded the Xubuntu CD, but (alas) I get a tty error upon trying to install.
I still don't know what to do. This goes beyond my want of ubuntu. Perhaps I'll try it again in 6 months or so.. :(

---

### Post by Pumalite on 2007-09-12
At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by htdjose on 2007-09-12
hi, im new to linux, i just recently bought a hp pavilion dv 9428nr and i hate vista, so i ordered  ubuntu seven poing four, and i just got it today, when i pop it into my laptop it dosent start up, i go into my computer, and it dosent recognize the cd or something, i leave the disk in , and restart, and it does nothing but start up vista, im sure the cds are fine because i tried them on my dads computer(also has vista) its older, but it worked...i dont understand, any help?
=swoop=

---

### Post by Pumalite on 2007-09-12
Lets start with the basics. Not everybody knows the specs of you computer; I suspect that you need an Alternate CD, but would help to know your memory and graphics. Also don't forget to set CD to boot first in your BIOS. Burn your iso as an 'Image', preferably at 4x, check CD for corruption after burn and before install. It also helps to do md5sum on your iso to ensure you have a good CD.

---

### Post by htdjose on 2007-09-12
> **Pumalite said:**
> Lets start with the basics. Not everybody knows the specs of you computer; I suspect that you need an Alternate CD, but would help to know your memory and graphics. Also don't forget to set CD to boot first in your BIOS. Burn your iso as an 'Image', preferably at 4x, check CD for corruption after burn and before install. It also helps to do md5sum on your iso to ensure you have a good CD.

alright, amd turion dual core precessors 2.2ghz, two gigs of ram, two hard drives, and i set the cd to boot first, whats the difference between the alternate and the live cd?
=swoop=

---

### Post by Pumalite on 2007-09-12
Alternate CD avoids graphics problems, which I think you have, even though you didn't mention it. I would also follow scrupulously all the other suggestions.

---

### Post by htdjose on 2007-09-12
yeah, thanks, im downloading the alternate cd right now, wish i would of known this before i ordered them, lol, so yeah, ill let you guys know after i finnish, 
=swoop=

---

### Post by Pumalite on 2007-09-12
I'm still curious about your graphics for future reference. (so I can help others better).

---

### Post by htdjose on 2007-09-12
nvidia g force 6150, im not sure how much video memory that is, but im sure its not so much, because halo looks like crap when i play it, lol, so yeah, and some other things i forgot to mention: when i put the cd in it sounds like its trying to start up, but after a few tries it gives up, and thats it, and in my computer it dosent show anything, so yeah, ...still downloading the alternate...
=swoop=

---

### Post by Pumalite on 2007-09-12
Thanks. Post back if you have any problems with the Alternate. Good luck.

---

### Post by htdjose on 2007-09-13
yeah, i tried it, and they worked, until i started installing, some of the files were corrupt, and i did that whole m5 check, and i turned my burning speed really low, so i just dont know, im downloading it again on my other computer, wish me luck?
=swoop=

---

### Post by Shocklance on 2007-09-13
I've had a similar problem, managed to install from the alternate CD, but cannot get the x server to start. Whenever I start the x server, i get the error:
 Screen(s) found, but none have a usable configuration. 

computer specs:
DFO-4008114L Latitude(TM) D830 Intel(R) Core(TM) 2 Duo Processor T7300 (2.0GHz)
-Genuine Windows(R) XP Home SP2 Edition (English)
-1GB (2x512MB) 667MHz DDR2 SDRAM
-120GB SATA (7200RPM) Hard Drive
-8X DVD-ROM + 24X CD-RW Combo Drive
-Integrated 10/100/1000 Ethernet D830
-Integrated UMA Base Intel(R) Graphics Media Accelerator
-X3100 Intel(R) PRO/Wireless 3945 (802.11 a/g)
-MiniPCI Card Intel 965GM with Intel GMA Dell(TM) Palmrest
-15.4" Wide Aspect SXGA+ (1680x1050 resolution) UltraSharp(TM) Display 1 Year 19 

I think it has something to do with the graphics drivers, i'll update details when able.

---

### Post by Shocklance on 2007-09-13
I am currently trying to install the drivers from:

[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)

will update if it works

---

### Post by Pumalite on 2007-09-13
Have you tried just: startx... or:
sudo dpkg-reconfigure xserver-xorg?

---

### Post by htdjose on 2007-09-13
yeah,the cd worked, and it installed, and everything was fine, but when i restarted it, and the dual boot screen poped up, i chose ubuntu, and it shows the load screen and everything, but then it just goes black, anyone know whats up?
=swoop=

---

### Post by Pumalite on 2007-09-13
Full specifications for Gateway T-6815
Manufacturer: Gateway Inc.
Part number: T-6815
There are no available specs for this product. 

Probably graphics.

---

### Post by htdjose on 2007-09-13
pumalite, im not trying to be greedy, but HELP ME!!!lol, yeah, my computer is an hp pavillion dv 9000 and its an nvidia graphics card so it has to be decent right? yeah, so should i just give up on ubuntu(i hope i dont have to) maybe ill try and biuld one of the osx86 hackintosh's, lol
=swoop=

---

### Post by Pumalite on 2007-09-13
Don't give up yet let me investigate this and let you know.

---

### Post by Pumalite on 2007-09-13
Have you tried "noapic" boot option?

---

### Post by htdjose on 2007-09-13
in full realization that im going to sound like a noob, how do i do that?
=swoop=

---

### Post by htdjose on 2007-09-13
ohh, and another thing is i get a boot error (18) i think, lemme check
=swoop=

---

### Post by htdjose on 2007-09-13
bios bug 81
=swoop=

---

### Post by Pumalite on 2007-09-13
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by htdjose on 2007-09-13
thanks it worked, now all i need to do is figure out how to make this thing permanent, which seems a little harder, 
=swoop=

---

### Post by Pumalite on 2007-09-13
Just follow the link. You can do it.
Make sure you backup your menu.lst before editing.

---

### Post by htdjose on 2007-09-13
alright, thanks, i got to go to work, but ill let you know if it works, thanks, im really excited about this...thanks again.
=swoop=
p.s. cant wait to rub this in all those mac losers faces, lol
hah

---

### Post by Pumalite on 2007-09-13
You are welcome. Good luck.

---

### Post by htdjose on 2007-09-14
okay, so i cant figure out how to get into the text editor, is it the normal text editor in applications or is it a different one i need to download?
=swoop=

---

### Post by Pumalite on 2007-09-14
gksudo gedit /path/to/the/file

---

### Post by htdjose on 2007-09-14
so am i in ubuntu when i do this, or do i do this from the grub menu?
=swoop=

---

### Post by Pumalite on 2007-09-14
Applications>Accessories>Terminal

---

### Post by htdjose on 2007-09-14
ohhh, lemme try that.
=swoop=

---

### Post by htdjose on 2007-09-14
thanks it worked....linux rocks, 
=swoop=

---

### Post by htdjose on 2007-09-14
so i can kind of understand what i did, what did noapic do?
=swoop=

---

### Post by Pumalite on 2007-09-14
No interrupt routing

---

### Post by htdjose on 2007-09-15
no interupt routing?
=swoop=

---

### Post by Pumalite on 2007-09-15
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

[http://www.linuxquestions.org/questions/showthread.php?t=454675](http://www.linuxquestions.org/questions/showthread.php?t=454675)

[http://ubuntuforums.org/showthread.php?t=334083](http://ubuntuforums.org/showthread.php?t=334083)

[http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)

[http://www.wilderssecurity.com/showthread.php?p=747186](http://www.wilderssecurity.com/showthread.php?p=747186)

---

