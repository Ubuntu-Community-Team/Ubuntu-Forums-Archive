---
title: "Installer Crashed: 11.04"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by fantab on 2011-05-04
I am trying to install ubuntu 11.04-amd64 when the **Installer Crashed**. I tried again and it crashed again. (My Desktop supports 64bit)

I suspected a faulty CD and used another CD to burn and install 11.04... but the installer crashes. It crashes roughly after I choose the keyboard layout. I re-downloaded 11.04 and burned it to yet another CD... and the Installer crashed again.

I thought that something could be wrong with the 64bit natty and downloaded and installed 32bit... the Installer Crashed again.

I am trying to Clean Install 11.04 on a new HDD I got myself.

Please help...

(I can also attach syslog and partman files if anyone can analyze them for me and help me with this issue.)

Thanks

---

### Post by Quackers on 2011-05-04
What exactly do you mean when you say the installer crashed? Did a message come up saying the installer has crashed?
Is the HDD brand new or did it come from another system? How much ram is installed in your system?
Details please.

---

### Post by fantab on 2011-05-04
> **Quackers said:**
> What exactly do you mean when you say the installer crashed? Did a message come up saying the installer has crashed?
Is the HDD brand new or did it come from another system? How much ram is installed in your system?
Details please.


Yes. During the installation a dialogue box poped up saying that the 'Installer Crashed' and had asked to report the bug... which I did along with files 'syslog' and 'partman' (See Attachments) as required.

Yes the HDD is brand new. I am currently using 2Gb, DDR2 800mhz RAM; Processor- Intel core 2 duo E8400; Desktop Board - Intel DG45ID [Media Series].

---

### Post by fantab on 2011-05-04
After my unsuccessful attempts to Install Natty 11.04_64 and 11.04_32 I had a suspicion that there could be something wrong with my new HDD. To confirm this I reinstalled [clean] Ubuntu 10.10_32, which I had been using prior to my decision to upgrade to 11.04, and... no problems 10.10 installed as it should; the installer DID NOT Crash.

This confirmed that my Hardware is fine and there are no problems with my new HDD. The problem is clearly with 11.04_64 & 32 Installer. I am downloading 10.04.2_64[LTS] just to see and make sure that there are no problems with 64bit installation either.

I request the forum to assist me identify the issues I am having with 11.04 and help me install 11.04.

---

### Post by yugo4k on 2011-05-05
The installer did crash with me as well.

I got a Ubuntu 11.04 64x (kernel 2.6.38-8-generic, GNOME 2.32.1)  image just now (May 05), created a usb drive boot and tried to install  it directly... and it crashed.
Tried to install from a live session and it crashed again.

I inserted the login, password and network name, it stopped "copying  files" and displayed the "Scanning the CD-ROM" message when the  following was displayed in a message box: 

"apt configuration problem
An attempt to configure apt to install additional packages from the CD failed."
 

I clicked OK and got this:
 

"Installer crashed
We're sorry; the installer crashed. Please fill a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug)  (do not attach your details to any existing bug) and a developer will  attend to the problem as soon as possible. To help the developers  understand what went wrong, include the following detail in your bug  report, and attach the files /var/log/syslog and /var/log/partman:"
 and just a "Close" button...

... I'm filling the bug report, but though I might as well post this here...

---

### Post by fantab on 2011-05-05
> **yugo4k said:**
> 
"Installer crashed
We're sorry; the installer crashed. Please fill a new bug report at [https://launchpad.net/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/ubuntu/+source/ubiquity/+filebug)  (do not attach your details to any existing bug) and a developer will  attend to the problem as soon as possible. To help the developers  understand what went wrong, include the following detail in your bug  report, and attach the files /var/log/syslog and /var/log/partman:"
 and just a "Close" button...

... I'm filling the bug report, but though I might as well post this here...

I too got the same message and have filed the bug report, but it seems that reported bugs take forever to be addressed. :(

Anyways, I have now **installed Ubuntu 10.04.2 [LTS]-amd64** and it installed as it should. No Problems and issues during installation. I am using this version presently. I have ascertained as far as I could that the problem is not on my side.
But knowing that a lot of people may have installed Natty beats me in understanding what could be going wrong.

I am waiting for the analysis of my filed bug report. 

Any help regarding my woes with Natty is heartily welcome.

---

### Post by yugo4k on 2011-05-05
I'd guess it's just a bit too early for us to get the 11.04 version... :D

I use 10.04, no problems, tried 11.04 just because it gets my hp g2410 scanner to work no problem using the "Try it" option.

---

### Post by Richard85 on 2011-05-20
I had the same problem doing a side by side install with Ubuntu 10.04. Help appreciated!

---

### Post by DurocShark on 2011-05-29
I'm getting the same error installing on my MacBook Pro within a VirtualBox virt from the downloaded ISO. 

That same ISO installed into a Hyper-V virt (2k8r2) fine, but not on my OSX lappy.

---

### Post by yugo4k on 2011-05-30
Check this out:

I tried to use a different usb device to install natty... and it worked. Flawlessly.

It's really odd, because keep using the same usb stick that didn't work with natty with different ubuntu versions and it always works... so I'm guessing it's not my usb stick's fault. Does that even make sense?

---

### Post by f145h on 2011-07-04
> **yugo4k said:**
> Check this out:

I tried to use a different usb device to install natty... and it worked. Flawlessly.

It's really odd, because keep using the same usb stick that didn't work with natty with different ubuntu versions and it always works... so I'm guessing it's not my usb stick's fault. Does that even make sense?

Yeah it may be the problem;cause  mainly U3 capable san-disk rem. devices are having the problems of installer crashes.Moreover there's a tool for [removing the U3 feature ]("http://www.sandisk.com/Assets/u3/launchpadremoval.exe")on san disk devices...
Alternately you guys must try using a different rem.drives and see if it works.

---

