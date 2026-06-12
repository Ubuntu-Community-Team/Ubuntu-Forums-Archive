---
title: "6x86 installation hangs"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by makria on 2010-01-22
Hi,

Am trying to inject new life into one of my old machines and learn more about ubuntu/Linux in the process. However I've come to a grinding halt and need help if I am to get any further.

**Setup:**
6x86 CPU (IBM)
Motherboard unknown
128MB RAM

**Symptoms**
Insert disc (alternative minimal Ubuntu 9.10)
Boot: prompt / graphic menu displays
<I configure / kick off the install process>
Console displays messages...
[INDENT]Linux....
initrd.gz.....
Ready[/INDENT]

After the 'Ready' message the machine halts with a blinking cursor, the screen is blank, the keyboard does not respond (e.g. CAPS LOCK has no effect).

I have tried a raft of suggestions from the net regarding various different routes to boot up (e.g. export / cli modes) as well as differing parameters to turn things off / change the config of the boot / install process - e.g. turning off power management, changing the VGA mode, and all to no avail.

What is frustrating is I don't seem to be able to find any way of  tracking what's going wrong between 'Ready' appearing on the console, and the machine freezing up. 

E.g. I tried the 'debug' parameter but nothing different appears on the console.

I believe the 6x86 is supported.

I'm now completely stuck so any help would be massively appreciated.

Regards,
Mark.

---

### Post by makria on 2010-02-15
Managed to 'solve' my problem.

I worked out the mobo is PcChips (cheap junk apparently), and I managed to upgrade the BIOS (by the skin of my teeth - as the files are no longer hosted by the manufacturer).

Neither of the above directly helped - however.

What I did was I worked my way backwards through all Ubuntu releases. It's quite a crude approach but it suits my skill level just fine :-)

Having first tried Karmic I progressed all the way to Breezy, which was the only release to get passed the initial installation page, install to completion, and run fine.

I had to do some configuration to get the mouse and the video card to work properly (e.g. specify the exact memory in the video card), but it all worked fine.

Couple of observations:

(1) The processor seemed to be recognised as I386 when the physical CPU is I586.

(2) The older the release, the more verbose the error message just prior to it locking up - this did provide a better 'key' into google searches but none of them happened to lead to viable solutions in my case

BTW this week I bought a replacement CPU, a genuine Intel (can be bought for the price of a box of biscuits these days).

Unfortunately this broke the Breezy GUI. Rather than plough straight into trying to fix this I was tempted to try installing a newer Ubuntu release (on the new CPU). 

This I did, and amazingly the Karmic alternative install ran to completion without locking up (as it did with the IBM CPU) . I selected Kubuntu (for elderly machines), unfortunately it locks up when the GUI starts up (when the Ubuntu logo first appears). However, I'm hoping I can fix this freezing / locking up problem and stick with the latest release. I've just got to work out how to boot to a command line and go from there.

I'm sticking with Ubuntu - but it should be mentioned that Windows 95 installed without issue on both processor types. Microsoft do come in for a lot of stick and Windows 95 isn't quite Linux, but at least the installation is pain free.

Regards.

---

### Post by makria on 2010-02-16
I sorted out the UI on my Karmic install (actually it&#8217;s Xubuntu not Kubuntu as per previous post).
 
The &#8216;fault&#8217; was the xorg.conf (it wasn't wrong, it simply wasn't there).
 
I powered up my Breezy installation (I have slottable hard disks and I saved the first install that worked which was Breezy).
 
Got xorg.conf off of Breezy. Not knowing how to transfer files I first tried telnet and this failed (kept getting 'couldn&#8217;t find package errors'). I next tried FTP and it sailed through (providing -p was added to fix 500 port errors). Breezy was already connected to the net so I transferred the file to an FTP server on the net.
 
Booted back to Karmic and in the recovery console, by good fortune, I was given access to a command line with network support, this allowed me to pull down Breezy's xorg.conf via FTP.
 
Then ran startx and blocked out a couple of xorg.conf lines it didn't like but still the UI failed to start. After some googling I found a [thread]("http://ubuntuforums.org/showthread.php?t=138537") suggesting the driver be changed from "ati" to "vesa" and it worked - the GUI powered up.

However no mouse control and the ALT-F1/6 terminal shortcuts resulted in a screen full of garbled graphics.
 
First tried to fix the mouse, found a claim to a fix [here]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/9068"): Option "AllowEmptyInput" "false"

However after changing this I found the UI no longer came up, and worse still I couldn't get into the recovery console. Given that my ALT-F1 terminal windows were also up the spout this well and truly finished consigned this installation to the grave.

I'm considering two directions now - working backwards through Ubuntu releases or trying Fedora. Fedora 1 installed itself onto a Pentium 75 cleanly. It was dog slow but the installation worked without pain. The machine doesn't have a CD boot option but the Fedora discs not only came with floppy images but also Windows software to write the images to disks!

I've attached my original Breezy xorg.conf for info.

---

### Post by northrup on 2010-02-16
I'm amazed you got it to run at all with only 128 MB of RAM.  The "Recommended Minimum" according to the Ubuntu help page is 384 MB.  Although, older versions might have lower requirements.  I would think that upgrading your RAM will help tremendously, if not to actually fix the problem, then at the very least to make the computer useable.
 
I'm guessing that "AllowEmptyInput = False" would result in Xorg refusing to start if it doesn't detect a mouse.  What kind of mouse are you using?  You might have to configure it manually.
 
I don't know if Karmic has an xsetup command.  I used to use Damn Small Linux on an old Compaq Presario 1210.  I had to use xsetup both to configure the touchpad properly (specify a 2-button "PS/2" ( -not) mouse) and to activate framebuffer mode instead of the normal VESA driver.
 
Hopefully this helps, and best of luck :)

---

### Post by makria on 2010-02-16
Hi thanks for responding.

The RAM is maxed out (it's an old machine). I chose Xubuntu as it claims to be easier on older machines.

It has a serial mouse. Xorg certainly started without the mouse. When the GUI started (switching ati to vesa) I had to use the keyboard (the pointer stayed in the centre of the screen). BTW CTRL-ESC on Xubuntu does what ALT-F1 does on on Ubuntu! I.e. get open the application menu.

I just installed Hardy and it also needs the Xord fixing. I chose Hardy because it still has the dpkg-reconfigure command. Although when I just ran it the thing didn't prompt for any video options...  Thanks for the tip re xsetup which I will try on Hardy before I start on the Fedora route.

It may sound like I'm making hard work of it but I've decided to do this more as a device for learning some Linux (if I get a usable machine it will be a bonus).

Regards,
Mark.

---

### Post by makria on 2010-02-17
Final post on this thread.

I tried Fedora and whilst the installation got further with the Intel CPU than the IBM CPU it still went bang.

I reverted to getting Hardy to install and work. The GUI appeared OK once I aligned the xorg.conf to the file I had from Breezy. I had to do this manually as the dpgk-reconfigure xserver-xorg didn't seem to do it right (and I needed to switch Breezy's "ati" driver to "vesa").

To get the serial mouse working I followed the instructions at [help.ubuntu.com/community/SerialMouseHowto]("https://help.ubuntu.com/community/SerialMouseHowto").

It runs pretty slow (as expected). I may be able to squeeze a bit more performance out by stopping a couple of processes and making a bit more use of RAM versus swap storage.  I'm just happy to have the thing working, very pleased it was viable on what is very old hardware, and to have learned a fair bit along the way. An old PC that was destined for the breakers yard is now fully functional.

Whilst googling the various problems I also read about Mandriva and Puppy which claim to be smaller (and faster) so I may give them a go next.

Regards,
Mark.

PS to northrup - I tried xsetup but the command was unknown

---

