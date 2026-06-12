---
title: "Problems booting and or installing"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by jazzman101 on 2007-12-14
Cherrio!
the freshly aquired and untouched Sony Vaio VGN-CR11Z seems to be very linux-unfriendly.
I can't get any system to run.

My first try was the Desktop-CD Ubuntu 7.10: it wouldn't boot up completely.

My second try Knoppix Live-CD. That, too, could not be persuaded to boot up.

After some googling I tried the Alternate-CD Ubuntu 7.10, there were several posts suggesting that might work. And it did, somewhat: the installation worked, although the network couldn't be setup properly.

However the freshly installed system won't boot either ;-(

Recovery-Mode works but X cannot be started 
```

(II) Module already built-in
(EE) VERSA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found

```


The CR11Z uses an ATI Mobility Radeon X2300 Graphics-Chip.
I was using the 32biit-Variants btw.

My xorg.conf is untouched (by me anyways)
I can't copy'n'paste the whole xorg.conf but the parts that seem relevant say:
```

Section "Device"
Identifier "Standardgraphikkarte" # <-- german for standard graphics card
Driver "vesa"
BusIS "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Standardbildschirm" # <-- german for standard monitor
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Identifier
Section "Screen"
Identifier "Default Screen"
Device "Standardgraphikkarte" # <-- german for standard graphics card
Monitor "Standardbildschirm" # <-- german for standard monitor
EndSection 

```

Any suggestions are welcome. I really need this notebook up an running - it's a work thing, kinda.

---

### Post by Pumalite on 2007-12-14
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by jazzman101 on 2007-12-14
I' have to type everything manually, so I hope this is readable....

sudo fdisk -lu
```

Device      Boot    Start          End              Blocks            Id   System
/dex/sda1     *       63             498014         248976          83   Linux
/dev/sda2             498015     312576704   156039345      5    Extended
/dev/sda5             498078     312576704   156039313+    8e   Linux LVM

```

cat /boot/grub/menu.lst
```

# comments ignored
default 0
timeout 3
hiddenmenu

title       Ubuntu 7.10, kernel 2.6.22-14-generic
root      (hd0,0)
kernel  /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro quiet splash
initrd    /initrd.img-2.6.33-14-generic
quiet

title       Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root      (hd0,0)
kernel  /vmlinuz-2.6.22-14-generic root=/dev/mapper/ubuntu-root ro single
initrd    /initrd.img-2.6.33-14-generic

# here comes the memtest
# End

```

---

### Post by Pumalite on 2007-12-14
Are you able to boot a Live CD? If so, do the above commands and then copy and paste here.

---

### Post by jazzman102 on 2007-12-14
I can't get any LiveCDs to boot. So far I have tried a rather old Knoppix CD and the regular Ubuntu Desktop 7.10 CD. The latter stops right after it tells my that local boot script exited OK. (can't think of the exact name right now, if it makes any difference, I can try again, of course.)

I guess that too starts to get buggy when it comes to starting X.

// Same person, new account - other one locked out :-( -not my day, I guess

Also: Thank you for your efforts, I really appreciate this!

---

### Post by Pumalite on 2007-12-14
Why don't you just copy and paste here?
Get in the terminal and do:
df -h

---

### Post by jazzman102 on 2007-12-14
Can't copy'n'paste because this is a different computer. On the one with the problem, X isn't running, which seems to be the whole problem. All I have there so far is a shell with no connection to the outside world.

df -h
```

                                                Size       Used  Available  Use % Mounted on
/dev/mapper/ubuntu-root                 141G       2.1G   132 G      2%      /   
varrun                                  1014M     16k    1014M     1%      /var/run
varlock                                 1014M     0        1014M     0%      /var/lock
udev                                   1014M     84k    1014M     1%      /dev
devshm                                 1014M               1014M     0%      /dev/shm
lrm                                    1014M     34M   1014M     4%      /lib/modules/2.6.22-14-generic/volatile
/dev/sda1                              236M      24M   200M       11%    /boot

```

---

### Post by Pumalite on 2007-12-14
Well; you have plenty of space too. The only thing I can suggest is a clean install.

---

### Post by jazzman102 on 2007-12-14
But that's the problem. I can't install from the regular Desktop CD b/c it won't boot. And this is a clean install from the Alterna CD. Very clean, 1st boot (attempt anyway) to be precise.

---

### Post by Pumalite on 2007-12-14
Start looking closely at your hardware then.

---

### Post by jazzman102 on 2007-12-14
Brand new notebook. Unpacked it. Booted it up. The preinstalled Vista worked (if you can say that about a microsoft product).
I also ran memchecks - no errors found.

---

### Post by Pumalite on 2007-12-14
Apparently is Vista friendly, but Ubuntu unfriendly.

---

### Post by jazzman102 on 2007-12-14
I guess so. Darn it.
Well, if anyone has a clue what the problem is, let me know.
I think I'll try with some other live CDs. Maybe I'll get lucky after all.
Thanks for the help though!

---

### Post by Pumalite on 2007-12-14
You are welcome. Good luck.

---

### Post by torgrot on 2007-12-14
Did you try hitting F6. I beleive when the grub list comes up on the LiveCD, it may be only a matter of adding some command line parameters to the boot.

torgrot

---

### Post by jazzman102 on 2007-12-14
Hi torgrot,
that's definately worth a shot. What parameters would that be though?

---

### Post by Pumalite on 2007-12-14
Here is a guide and a collection to try in case that works:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by jazzman102 on 2007-12-14
> noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317
I tried that. I'm not quite sure what happened. After the status bar saying "Loading Kernel" finished, the screen went black and I couldn't even tell whether the notebook was still on. Then nothing happened for a long time - nothing on the screen, no sounds from the cdrom drive or the harddisk -  and I shut it down.

Tried that twice, just to be on the safe side.

---

### Post by jazzman102 on 2007-12-14
Ok, tried it again with the following parameter
```
vga=0x317
```
This time a lot more action from the cdrom drive: there are some sounds for about 2 minutes. The screen stays black w/ a cursor on the top left. After the sounds disappear. again nothing seems happen.
Can you make heads or tails from all this?

---

### Post by Pumalite on 2007-12-14
Try them all, but one at the time. Read the guide.

---

### Post by jazzman102 on 2007-12-14
```
noapic
```
This time the Ubuntu start screen shows up. Something is happening for sure. The system appears to boot up. After the message "Running local boot scripts (/etc/rc.local)" the screen turns black for a second, the messages reappear, it turns black again. This repeats 2 or 3 times. The again, nothing happens. Pushing the power button shuts the system down gracefully.
Everything is going pretty fast, you know how quickly those messages fill up the screen during the start up process, but I think there were a few messages saying something like
"uvcvideo failed to query(135)"
And something about "uvccontrol 1"
About 3 lines of code, way to fast to write down.

```
nolapic
```
As far as I can tell the same thing happens. This time the error messages say
/var/lib/acpi-support/system-manufacturer no such file or directory

```
acpi=off
```
There are fatal errors from the PnP BIOS suggesting to turn pnpbios off.
The computer can only be restarted by force.

```
acpi=off pnpbios=off
```
After the kernel is loaded no messages appear, no sound can be heard, the screen is black with a blinking cursor.
The computer can only be restarted by force.

```
pci=noacpi
```
We have a start screen again - I just love that orange staus bar.
Similar to "noapic". There are SQUASHFS errors on top of that (a lot!) and a segmentation fault is being reported.
/etc/rc.local is executed again and once again the screen turns black 3 times and everything stops. System shuts down gracefully again.


I'm havin a ball here, can you tell?


Well, those are about all of 'em. None of the other parameters seem appropriate.

---

### Post by Pumalite on 2007-12-14
If you get to the Grub menu; boot in Recovery Mode and edit your menu.lst, removing 'splash' from the end of the kernel line.
gksudo gedit /boot/grub/menu.lst
Make the change, save, exit and reboot.

---

### Post by jazzman102 on 2007-12-15
Removing "splash" didn't do the trick either.
After the message
```
Running local boot scripts (/etc(rc.local) [OK]
```
the screen goes black three times again and that's it.
Also right at the beginning the error messages concerning uvcvideo appear.

---

### Post by Pumalite on 2007-12-15
At this point, you should try different distros and see if you are incompatible with Linux in general or Ubuntu in particular.

---

### Post by jazzman102 on 2007-12-15
Phew, what a relief.
X is finally running. A friend of mine was able to help. But all the work done in here was the basis for that. I'll share the solution for other owner of the cr11z in here later on.
Thanks again for your help and cya later.

---

### Post by wyntrblue on 2007-12-19
i also have a cr11z and have been going through hell to get X started.

i had to use the alternate image to install it at all. but the machine installed with no errors (thank goodness) then when i restarted it and it tryed to start X for the first time it seemed to stop at 

```
running local boot scripts (/etc/rc.local)
```

so i hit ALT+2 to get another console to actualy work wtih (no problems there) logged in and took a look at the X servers logs and found

```
(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(EE) VESA(0): No matching modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

went on to try 

```
sudo dpkg-reconfigure xserver-xorg
```

but was unable to get X working that way.

any suggestions?

---

### Post by wyntrblue on 2007-12-19
additional....

i have uploaded a copy of my xorg.conf to [www.wyntrblue.co.uk/xorg.conf](www.wyntrblue.co.uk/xorg.conf) 

thanks for any help you can be :)

---

### Post by jazzman102 on 2007-12-22
Ok, here it is (I hope).

First fix your network.

Add these lines to **/etc/modules** 
```
r8169 # Netzwerk
fglrx # Graphik
```

Next edit **/etc/resolv.conf**
```
nameserver 192.168.0.1 # Your Router's IP
```

In **/etc/network/interfaces** add these lines
```
auto eth0
iface eth0 inet static
adress 192.168.0.99 # this is gonna be your IP, change it to whatever you like
gateway 192.168.0.1 # IP Router
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255

```

In the shell enter
```
ifconf eth0 up
route add default gw 192.168.0.1
```

You might have to restart at this point.

Check your network
```
ping google.de
```

If it works go ahead and get the drivers
```
apt-get update
apt-get dist-upgrade
apt-get install linux-restricted-modules-$(uname-r)
apt-get install xorg-driver-fglrx
depmod -a

```
This migth take a while

Now all that should be left to do is edit **/etc/X11/xorg.conf** 
Where it says
```
Section "Device"
Identifier "ATI Radeon...."
Driver "vesa"
```
change *vesa* to *fglrx*.

I hope this helps.

---

### Post by riderforever on 2008-02-20
Hi!
Is there a final solution to make Ubuntu work in the CR11Z? I was thinking about buying it, but I must be sure I'll be able to install Ubuntu on it.

---

