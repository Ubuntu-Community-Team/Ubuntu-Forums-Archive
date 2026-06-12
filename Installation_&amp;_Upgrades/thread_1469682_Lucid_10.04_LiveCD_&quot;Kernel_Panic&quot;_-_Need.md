---
title: "Lucid 10.04 LiveCD &quot;Kernel Panic&quot; - Need to get Log Files"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by concordfta on 2010-05-02
O.K. Guru's, I humbly require your help.

#1 - Yes, I did a search, nothing came close to my issue, or with any resolve
#2 - I tried to be as accurate and descriptive in title
#3 - I require amd64 because of 4GB and VMs

_**Problem:**_

Lucid 10.04 Desktop amd64 ISO image burned to CD, tried to use as LiveCD, or Install, with multiple options (noapic, acpi=off, nomodeset, etc...) CD boot would stop (on 4 dots screen), keyboard freeze, stop loading.

Tried with deleting quiet and splash... I see that it "kernel Panics"

_**What I've tried:**_

Burned image 2x with 2 separate downloads
Tested CD, burn is good.
Tried CD in VM, works 100%
Tried on 2 other machines, work 100%

_**Machine with problem**_

Zotac GeForce 9300-ITX-WiFi with Q9400, 4GB, Asus Nvidia Silent GT240 1GB
Latest FW (Feb 2010 I think)
This machine works 100% on 9.10

_**What I need help with**_

How can I save the boot logs of a LiveCD to, let's say a USB stick?  Then I can have more details for troubleshooting. OR!!! If anyone had this issue and has an answer, even better!

_**What I can NOT do**_

Do in-place upgrade from 9.10, can't really back it up / screw it up (space/time issue), as I need it running.


Thank you in advance...

Please help :(  I've been using Ubuntu for 3 years and would really like to use 10.04

---

### Post by gman020 on 2010-05-02
Kernel panic - not syncing: Fatal exception in interrupt

I'm having the same problem. 

**_What I've tried:_**
Desktop x64
Alternative x64
Server x64 and then installing ubuntu-desktop. The problem only happens after I install ubuntu-desktop. 

The system is similar to concordfta's. 

**_System:_**
ZOTAC GF9300-G-E LGA 775 NVIDIA GeForce 9300
Intel Q9550
8GB RAM
30gb SSD

---

### Post by concordfta on 2010-05-03
For sh!ts and giggles I tried the i386 Desktop (32bit) ISO and that one works fine.  There can't be anything wrong with my hardware?  It really isn't the solution since I'm losing around 800MB of memory, which could be at least 2 VMs worth, so 64bit is needed.

I just need a solution to write the logs to a USB stick when booting a LiveCD.  Kind of dead in the water at the moment without more info as to why it kernel panics.

---

### Post by dino99 on 2010-05-03
> **concordfta said:**
> For sh!ts and giggles I tried the i386 Desktop (32bit) ISO and that one works fine.  There can't be anything wrong with my hardware?  It really isn't the solution since I'm losing around 800MB of memory, which could be at least 2 VMs worth, so 64bit is needed.

I just need a solution to write the logs to a USB stick when booting a LiveCD.  Kind of dead in the water at the moment without more info as to why it kernel panics.

you have the same result with i386 and pae kernel installed than with 64 bits and less troubles. AS you have a recent video card, as you have tried to boot with noacpi or else, this time boot with video=vesa, it should be easier to go ahead, later you'll search for your latest driver on nvidia site.

"What I can NOT do

Do in-place upgrade from 9.10, can't really back it up / screw it up (space/time issue), as I need it running."
so why not waiting 1 month or so till the main bugs are gone ?

---

### Post by concordfta on 2010-05-03
Ok, I tried 'video=vesa' and removed 'quiet splash'.  It kernel panic-ed but I took a 'screen' shot with my camera!? :redface: better than nothing!

I've attached the picture.

dino99, you mentioned why I don't wait a month and try again.  I can wait, it's not a problem, I just don't know if ubuntu ISOs are updated regularly, or do they stay static per release and just do repository updates?  If they update the actual ISO that would be great!  I can try again in a month or two.  I also like your idea of PAE.  That did not occur to me.  I will search the PAE instructions.  I would be happy with i386 and PAE!  I only needed 64bit for the full memory!  All my VMs are 32bit anyways.

---

### Post by gman020 on 2010-05-04
I was able to install ubuntu server x64 then install ubuntu-desktop.

ran startx to load the gui and installed the nvidia 173 drivers. No kernel panics so far.

The default display driver and current nvidia driver caused the kernel panic when I tried them.

---

### Post by concordfta on 2010-05-04
ok, so I tried the PAE kernel and now I get my full 4gb!!

Thanks for the suggestion dino99

gman020, thats weird, mine still panic'ed with 'video=vesa', so it shouldn't be the nvidia driver from me?  It looks like it panics on the networkmanager from the screenshot.

I tried disabling the ethernet in the bios, but that did not help either..

I will keep searching..  but for now i386 + PAE is a good solution for memory over 3.2GB

---

### Post by quadproc on 2010-05-04
[QUOTE=concordfta;9218059...
_**Problem:**_

Lucid 10.04 Desktop amd64 ISO image burned to CD, tried to use as LiveCD, or Install, with multiple options (noapic, acpi=off, nomodeset, etc...) CD boot would stop (on 4 dots screen), keyboard freeze, stop loading.

Tried with deleting quiet and splash... I see that it "kernel Panics"
...
How can I save the boot logs of a LiveCD to, let's say a USB stick?  Then I can have more details for troubleshooting. OR!!! If anyone had this issue and has an answer, even better!
[/quote]
If you have an older (working) release on the same system then you may be able to get copies of the system log from the failing install. I am assuming that the system installed itself far enough to start using the normal disk rather than ramdisk. To do this you'll need to figure out where the partition(s) for your 10.04 system are located on the disk.  Then create a dummy directory entry in your running system and mount the 10.04 partition onto that dummy directory.  Use your normal tools to grab a copy of whatever you want from that dummy directory, then umount the 10.04 partition.

Good luck!

quadproc

---

### Post by raugfer on 2010-07-03
> **concordfta said:**
> For sh!ts and giggles I tried the i386 Desktop (32bit) ISO and that one works fine.  There can't be anything wrong with my hardware?  It really isn't the solution since I'm losing around 800MB of memory, which could be at least 2 VMs worth, so 64bit is needed.

I just need a solution to write the logs to a USB stick when booting a LiveCD.  Kind of dead in the water at the moment without more info as to why it kernel panics.

I had the exact same issue as you. I think the problem is with the WiFi driver for the VIA 6656 USB module that came with the Zotac 9300-D-E motherboard.

I unplugged the VIA 6656 USB header from the mobo and, voila, the 10.04  LiveCD works perfectly.

The WiFi module did not work out of the box for 9.10, and I remember the VIA driver being broken when compiled for 9.10 64-bit.
I suspect the driver is now being shipped bundled in 10.04 and is producing the kernel panic during the network initialization for 64-bit targets.

Confirm if this is really the issue and advise on reporting this as a bug.

---

### Post by mathew_davis on 2010-07-07
I can confirm this issue.  I also had the same issue.  The live CD wouldn't boot.  When I did a text boot I got the kernel panic.  9.10 worked fine.  So I installed 9.10 and upgraded to 10.04 and got the same kernel panic error.  It was weird though because I got the right back ground and everything seemed to update correctly but upon reboot I could never get back in.

So I re-installed to  9.10 and upgraded to 10.04 with the wireless unplugged and it worked great.

Thanks for the tip.

---

### Post by qopit on 2010-07-18
Same problem confirmed on the same board... this was driving me crazy and I was leaping through hoops trying to repair installs I managed to get mostly completed.

Unplugging the wifi and going from scratch works perfectly.

Isn't it always the wireless drivers?  Geez...

---

### Post by matthewbpt on 2011-05-05
Two releases later and this bug is still present ... see my bug report here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/768524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/768524)

---

### Post by matthewbpt on 2011-05-06
Please go to the bug report and mark it as affecting you to increase its priority. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/768524](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/768524)

---

