---
title: "Ubuntu 9.10 installation not working"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by lolwot92 on 2009-11-15
Hey,
Last time i installed Ubuntu, i think 8.xx it worked fine. But for some reason it didnt work today. I burned it as an ISO and all to a CD, booted from it and the menu came up. I clicked install then this little ubuntu symbol sits in the middle of the screen, after a few minutes, it disappears and goes black and just sits there. It didnt work, so i thought id try it the other way, installing it directly from windows(using wubi), i got it installed properly after a few stuffups (stupid errors in installation, bad copy of cd), rebooted my machine, but instead it just skipped straight into windows. I didnt partition, i just installed Ubuntu onto my smaller hard drive as i dont really use it. Any reason why the boot menu didnt appear? Or why the boot-off-cd install failed?

Cheers,

EDIT: I tried Kubuntu this time, and i got this error message while trying to boot off/install kubuntu. It went to the menu, i hit install, the screen came up with a loading sign, then this error message came up after a few minutes.
"Stdin: 0
Mount: Mounting/Dev/Sr0 On/Cdrom Failed: Invalid argument
(Initramfs) Unable to find a medium containing a live file system."

Maybe this will help, cheers

EDIT 2: timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Kubuntu"
MBR looks like that.

Am i suppose to install kubuntu onto the same HDD that windows is on? because im putting it on a seperate HDD if thats the problem..

---

### Post by lolwot92 on 2009-11-16
bump =x

---

### Post by crane on 2009-11-30
Same issues here as well.

---

### Post by darkod on 2009-11-30
Windows is starting as usual because in your BIOS you still have the hdd where windows is as first choice boot hdd. You need to set the other drive where you installed ubuntu as first boot choice. Grub is probably installed on that drive and it will allow you to boot both ubuntu and windows, unlike windows bootloader which only looks at itself. :)

---

### Post by subashk80 on 2009-11-30
Hi lolwot92, did you get the problem rectified. I had been trying to install Ubuntu 9.10 and same thing appears for me. So help out plz....i had been searching all over for solution unluckily. So plz share your ideas ....

---

### Post by charliko on 2009-12-09
Same problems   I think!!

this is the line i somehow got the blank screen to show

init:  line 1:  can't open /dev/sdc: no medium found


that line repeats with sdd    sdd    sr0

stdin: error 0


I have a dual boot menu and one disk dedicated to old ubuntu the other is Windows 7

Hope someone has some ideas here

Thanks in advance

-charlie

---

### Post by darkod on 2009-12-09
OK, people, you are starting to confuse things.
The OP edited his first post and the line with wubildr means it's a wubi install, not ubuntu/kubuntu. That makes a lot of difference.
So either start your own threads, or when adding here that you have the same problem, specify if you have wubi or not and the issues you are seeing.

Ps. Besides the OP was made 3 weeks ago and the OP hasn't updated with info so far. I guess maybe he even reinstalled.

---

