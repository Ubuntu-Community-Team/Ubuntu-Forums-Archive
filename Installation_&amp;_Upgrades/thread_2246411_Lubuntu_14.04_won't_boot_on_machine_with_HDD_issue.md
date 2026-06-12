---
title: "Lubuntu 14.04 won't boot on machine with HDD issues"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by ashgupta3 on 2014-09-30
Here are the specs of my machine:


mobo: it is a DFI board with the same specs as a DFI CM33-TL
      except it doesn't have an onboard LAN port
RAM: 768MB
CPU: Intel Celeron 766Mhz (dating back to 2001)
HDD: IDE WD Blue 500GB (**however only the first 138GB are recognized by
     the mobo because the mobo is so old)
ODD: BenQ CD burner
LAN: a TP-Link 10/100 NIC card
modem: a PCI modem card
monitor: IBM E74M CRT monitor (max res 1280x1024)


I was successfully running Xubuntu 12.04 on this system. However, the GUI was
sluggish so I wanted to switch to Lubuntu because it supposedly requires less
resources. I waited until Lubuntu 14.04 was released. However, the Live CD
of Lubuntu 14.04 wouldn't run. It got to the splash screen, and after a few
moments went blank and froze. Also, installing from the CD was useless because
it was taking too long.


(Interestingly, the Live CD of Lubuntu 12.04 did run. Also, I thought I would try 
the Live CD of Xubuntu 14.04 but the ISO doesn't fit on a CD.) (Also, note that 
I checked all discs for defects and there were none.)


So I tried installing using the Lubuntu 14.04 alternate installer. The installation
process went smoothly. (I allocated the first 100GB to root and the next 2GB for
swap - making sure I didn't go over the 138GB barrier.)


When I rebooted, the screen eventually went blank during the boot process and
stayed that way. So I booted into recovery mode and added "nosplash single" to
the Linux kernel parms. Again, it froze, but I noted the last couple of error
messages:






init: plymouth-upstart-bridge main process (157) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
Adding 1952764k swap on /dev/sda2 Priority:-1 extents:1 across:1952764k FS
EXT4-fs (sda1):re-mounted. Opts:errors=remount-ro




I booted into recovery mode again and noticed that the options in fstab for my
root partition were "errors=remount-ro". I though this might be a problem so
I changed this to "defaults". I also created a swapfile and disabled the swap
partition. Again, it froze on reboot with the following last messages:




init: plymouth-upstart-bridge main process (156) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning
EXT4-fs (sda1):re-mounted. Opts: (null)

Obviously, this is not my main system. I'm just trying to salvage it so I can
give it away.

---

### Post by UltimateCat on 2014-09-30
Hi:

I have a few idea's but I can't guarantee that they will work.

At the black screen try Ctrl+Alt+F2 and log in and than type:
```
startx

```
That should take you to the Lubuntu GUI--

 Plymouth if I am not mistaken is related to graphic's.
```

init: plymouth-upstart-bridge main process (157) terminated with status 1
init: plymouth-upstart-bridge main process ended, respawning

```
Copy and paste the output of the error message and see what Google returns.

You can try editing the kernel line.  Edit the boot arguments and add "nomodeset" at the  end of the line.

If you're still having issues, you can also remove "quiet splash --" from that same line.

That's all I can think of for now, sorry-
If you still need help you can private message me (gotta to to work)

Cheers
Ultimatecat-;)

---

### Post by ashgupta3 on 2014-10-04
I found that, while booting, if I rapidly switched between console 1
and 2, using <CTRL>+<ALT>+<F1> and <CTRL>+<ALT>+<F2>, I get a
command prompt in one of the consoles. (No command prompt in any of the other
consoles.)


I am booting with the kernel parms
```
nosplash single nomodeset

```From the command line, I installed ssh. I tried executing
```
startx

```and
```
service lightdm start

```However, the screen goes blank. But the system does not freeze
because I can still ssh into it and run any command I want.


I'm thinking it is a problem with X windows or lightdm so I ran
```
dpkg-reconfigure xserver-xorg

```but it didn't ask me any questions (like screen resolution, etc.). I tried
```
startx

```again, but no improvements - just a blank screen.


The log file /var/log/lightdm/lightdm.log clearly shows that x server and 
lightdm are being terminated. However, I didn't get any luck
using google to find out why.


The last line of /var/log/lightdm/x-0.log is
```
X: ../../dix/pixmap.c:112: AllocatePixmap: Assertion `pScreen->totalPixmapSize > 0' failed.

```Google didn't help with this msg either. The output of 
```
lspci | grep -i VGA

```is
```
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a)

```

(Again note that I don't have a video card, just integrated graphics.)

---

### Post by UltimateCat on 2014-10-04
I'm not sure why startx is failing. It should take you to the GUI.

From what you said it doesn't sound like the RAM or the HDD is bad.
You could run Memtest overnight just to make sure about the RAM.

Try booting with the Lubuntu or Xubuntu Live CD and try to mount and read the HDD.

If you still don't have the GUI try:
```
sudo install ubuntu desktop 

```

That's all I can think of. Sorry I don't know more.
I asked one of our Moderators to join your thread.
Maybe he will know what else to try--

---

### Post by gordintoronto on 2014-10-05
This sounds like a video problem. Have you tried using nomodeset?

---

### Post by ashgupta3 on 2014-10-05
Yes. It let me get to a command line but didn't give me a GUI.

---

### Post by UltimateCat on 2014-10-05
[**[COLOR=#000000]gordintoronto[/COLOR]**]("http://ubuntuforums.org/member.php?u=507940"):

Would installing the GUI help?

I'm asking because ashgupta3 already tried "startx" (I suggested in a pm) and all that did was give him a blank screen.

---

### Post by gordintoronto on 2014-10-05
Sorry, I missed some of the things in the OP's second post. I think it's the Trident video; if possible, I would install an ati or nvidia video card into the machine. But I wouldn't spend money on a computer of this age. I have turned better computers than this into scrap metal.

---

### Post by ashgupta3 on 2014-10-05
I tried executing
```
apt-get install lubuntu-desktop
```
and it said it is already installed (and the latest release).

As for Lubuntu 14.04 not supported Trident, well then
why do Xubuntu and Lubuntu 12.04 run fine?

---

### Post by ashgupta3 on 2014-10-06
I ran memtest overnight and it found no errors.

I also ran
```
fsck -V -t ext4 /dev/sda1
```
and it came back clean.

---

### Post by Vladlenin5000 on 2014-10-06
12.04 and 14.04 do indeed come with different driver versions:

Precise: [http://manpages.ubuntu.com/manpages/precise/man4/trident.4.html](http://manpages.ubuntu.com/manpages/precise/man4/trident.4.html)
Trusty: [http://manpages.ubuntu.com/manpages/trusty/man4/trident.4.html](http://manpages.ubuntu.com/manpages/trusty/man4/trident.4.html)

but I'm not sure that's the problem. Perhaps you need other boot parameters than just - or instead of - *nomodeset*.

---

### Post by ashgupta3 on 2014-10-07
I've given up and switched to Bodhi 2.4.0 (yes, I know, it's based on Ubuntu 12.04, but what can I do?).
Thanks anyway for your help guys.

---

