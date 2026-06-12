---
title: "Lucid on iMac 21,5 (10.1)"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ZeroLinux on 2010-03-25
Lucid Beta 1 on iMac 21,5 (10.1)

Solution of some problems and some unsolved problems:

**Sound** 
1) After Installing you need to unmute front speaker
Go to Terminal (Application -> Accessories -> Terminal) and there write alsamixer. Then go 3 times press right arrow key and press m
And then yo can press the key "Up" to set volume level you like

**Microphone**
2) You need to boost mic because it is muffled. 
To do it install "PulseAudio Device Chooser"
Write in Terminal 
sudo apt-get install paman (it was in my case)
or
sudo apt-get install padevchooser (may be it works also)

Start it from Application -> Sound & Video -> PulseAudio Device Chooser
Click on its the icon in the upper-right corner. Choose Manager... -> Tab "Devices" -> In the tree "Sources" -> alsa_input.pci-0000_00_08.0.analog-stereo Internal Audio Stereo -> Button "Properties". Set the Volume to 300% (I like this level. You can choose whatever). Close. Well done.

**Skype**
3) If you like Skype - it will set Volume of the mic to the 100% back or, in other word, reset it, and it again will be muffled. To avoid it, after installing Skype do this. Before calling, in Skype go to Options -> Sound Devices and UNCHECK "Allow Skype to automatically adjust my mixer levels". In such a way you will enjoy normal sound even after reboot.

**Reboot**
4) Yes, you cannot reboot out of box. The system hangs right before reboot, you can safely press turn off button behind your iMac and press it again. But shutdown works fine. System goes to Sleep and wakes up fine. 
Solution: 
in Terminal: sudo gedit /etc/default/grub
Change in the editor: (GRUB_CMDLINE_LINUX_DEFAULT="quit splash")to (GRUB_CMDLINE_LINUX_DEFAULT="quit splash reboot=pci")
Save and quit.
Make update grub in terminal: sudo update-grub

**Keyboard**
5) Works if you press several buttons to help to recognize it. The key "fn" doesn't work.

**Magic Mouse**
6) If you press several times on it - it will work. You can move it. You will have left and right click, but there is no scrolling out of box

**Webcam**
7) iSight works out of box and works fine. Nothing to do. Install Cheese and use it.

---

### Post by xvila on 2010-03-25
Good information ! Thanks

Just a question regarding keyboard: Does the "fn" function work ?

---

### Post by ZeroLinux on 2010-03-25
No, "fn" desn't work
I use another keyboard therefore I didn't notice it. Thank you. I will change a header.

---

### Post by kagou on 2010-03-27
Have you installed Lucid on a special partition (like sda4)?

I can't have any success with lucid on my imac.

I use desktop-amd64.
Refit 0.14
I install lucid on sda4 (sda3 is swap)
Before launching installation, I set root for grub on sda4

But After reboot, no entry for lucid on refit. How do you proceed ?

---

### Post by jaco223 on 2010-03-28
> **kagou said:**
> Have you installed Lucid on a special partition (like sda4)?

I can't have any success with lucid on my imac.

I use desktop-amd64.
Refit 0.14
I install lucid on sda4 (sda3 is swap)
Before launching installation, I set root for grub on sda4

But After reboot, no entry for lucid on refit. How do you proceed ?

Have you tried installing grub on /dev/sda. This worked for me on my iMac.

---

### Post by ZeroLinux on 2010-03-30
I installed Lucid on the additional USB drive and put boot loader to /dev/sdc 
New rEFIt 0.14 sees it without problem
But boot process very loooong 
The cursor blinking on the black screen approximately 50 times after choosing in grub right option
If I try to boot without options quiet and splash - system hangs at all after detecting CPU and boot process doesn't continue. It's very strange. I think if I want to see boot process verbosely it mustn't affect ability to boot. But it does.

---

### Post by jaco223 on 2010-03-31
> **ZeroLinux said:**
> I installed Lucid on the additional USB drive and put boot loader to /dev/sdc 
New rEFIt 0.14 sees it without problem
But boot process very loooong 
The cursor blinking on the black screen approximately 50 times after choosing in grub right option
If I try to boot without options quiet and splash - system hangs at all after detecting CPU and boot process doesn't continue. It's very strange. I think if I want to see boot process verbosely it mustn't affect ability to boot. But it does.

Maybe you can try and add nomodeset to the boot process, edit GRUB, go to this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" edit this line to look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

See if that helps.

If you're not able to boot, do you have the livecd? if you do boot from the livecd
and select nomodeset. And if you can boot that way, you can then edit GRUB like above.

Jaco

---

### Post by jaco223 on 2010-03-31
zerolinux, you say your "fn" key doesn't work? is your apple keyboard functioning
correctly? if not you can add "options hid_apple fnmode=2" to /etc/modprobe.d/imac.conf
That will get the keys functioning properly.

Jaco

---

### Post by ZeroLinux on 2010-03-31
quiet splash nomodeset - in the boot option doesn't affect anything
I created  /etc/modprobe.d/imac.conf and put there options hid_apple fnmode=2
"fn" doesn work either - I usually check trying to make "Delete" symbol on the right side of the cursor. Multimedia keys also doesn't work, but it doesn't matter for me - I don't use them in Linux either.

The problem with long boot or even with hanging system during booting (if you delete "quiet splash" or "splash" from options) is after this string (accordng to dmesg)

[    0.027539] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.027543] ftrace: allocating 22512 entries in 89 pages
[    0.030046] Setting APIC routing to flat
[    0.030433] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.135250] CPU0: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Here is the problematic place. It is here system either hangs (without "splash" option) or delays approximately 30-40 sec (cursor is blinking 50 times)
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 3072K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.290112] CPU1: Intel(R) Core(TM)2 Duo CPU     E7600  @ 3.06GHz stepping 0a
[    0.290121] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300013] Brought up 2 CPUs
[    0.300015] Total of 2 processors activated (12205.61 BogoMIPS).
[    0.300483] CPU0 attaching sched-domain:
[    0.300486]  domain 0: span 0-1 level MC
[    0.300487]   groups: 0 1
[    0.300491] CPU1 attaching sched-domain:
[    0.300493]  domain 0: span 0-1 level MC
[    0.300494]   groups: 1 0
[    0.300617] devtmpfs: initialized
[    0.300860] regulator: core version 0.5


What I really want - it is to have normal boot and correct reboot.
And to have scroll on Magic Mouse
Does anybody know how to make it?

---

### Post by xvila on 2010-04-07
The F1-F12 keys work perfectly as they are supposed to work no matter
what option (fnmode=1 or fnmode=2) you put in the modprobe.d directory
The problem is that the key "fn" (bottom left) has no effect. Hence, you can not use "VolumeUP/VolumeDown" etc.

More annoying is that you can not emulate PgUp/PgDown/Home/End by pressing
"fn+UpArrow/fn+DownArrow/fn+Left/fn+Right"

Also, in my spanish keyboard, the keys "</>" and "º/ª" are inverted

I have tried several keyboard layouts in KDE with no luck

Xavi

> **jaco223 said:**
> zerolinux, you say your "fn" key doesn't work? is your apple keyboard functioning
correctly? if not you can add "options hid_apple fnmode=2" to /etc/modprobe.d/imac.conf
That will get the keys functioning properly.

Jaco

---

