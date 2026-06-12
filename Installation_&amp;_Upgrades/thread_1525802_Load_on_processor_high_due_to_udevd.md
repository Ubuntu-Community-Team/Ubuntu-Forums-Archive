---
title: "Load on processor high due to udevd"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by AvinThat on 2010-07-07
Hi all,

I've attached an image to show what's going on. This is what is going on from boot.

A lot of udevd, one of which is ripping the processor to pieces.

Any ideas what is going on here?

Cheers

---

### Post by SlugSlug on 2010-07-07
I had a similar prob a while back - a work round is not to mount NTFS drives...

---

### Post by AvinThat on 2010-07-07
> **SlugSlug said:**
> I had a similar prob a while back - a work round is not to mount NTFS drives...


Thing is, this is what happens from start up. So I've literally done nothing to the computer other than log in. No drives mounted, nothing.

---

### Post by tommcd on 2010-07-07
> **AvinThat said:**
> Thing is, this is what happens from start up. So I've literally done nothing to the computer other than log in. No drives mounted, nothing.
Hi AvinThat, it's me again ;)

Do you possibly have a Windows partition that is set to automount in your /etc/fstab file? If you do, try commenting out 
(that is, put a # in front of) the line for mounting your Windows partition(s), Then reboot.
Also, if you have any flash drives or external hard drives hooked up to the system, try disconnecting them and see if the problem goes away. Udev is used for automounting things connectied to the system.

---

### Post by AvinThat on 2010-07-07
> **tommcd said:**
> Hi AvinThat, it's me again ;)

Do you possibly have a Windows partition that is set to automount in your /etc/fstab file? If you do, try commenting out 
(that is, put a # in front of) the line for mounting your Windows partition(s), Then reboot.
Also, if you have any flash drives or external hard drives hooked up to the system, try disconnecting them and see if the problem goes away. Udev is used for automounting things connectied to the system.


Hello - u get around lol

in the /etc/fstab file i have this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
f09dad8b-aa86-485f-9a92-f79ed3985de0       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e73a212f-b63c-4cb4-84de-e7a69ba68824 none            swap    sw              0       0
```So I'm guessing that because only the partition that Ubunutu is using plus it's swap are present I'd say no 'automount' present.

With regards to externals, nothing connected to the computer at all. I'm on a laptop that has an in corporated memory card slot, no optical drive.

---

### Post by tommcd on 2010-07-07
> **AvinThat said:**
> 
With regards to externals, nothing connected to the computer at all. I'm on a laptop that has an in corporated memory card slot, no optical drive.
So it is not trying to automount Windows then.
I wonder if Ubuntu is constantly polling the memory card reader.
Does this problem go away after the system boots up?
Can you try inserting a memory card (if you have one) into the slot and see if the problem goes away?
Also try installing **powertop**. Powertop is a program that can look for things that are hogging your CPU on laptops and offer ways to save power.
See this tutorial:
[http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/](http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/)
also:
[http://www.ubuntugeek.com/saving-power-on-intel-hardware-using-powertop.html](http://www.ubuntugeek.com/saving-power-on-intel-hardware-using-powertop.html)
So install powertop:
```
 sudo apt-get install powertop
```
 and then run it with "sudo powertop". See if it offers to disable polling of the memory card slot. If it does, then let it, and see if it helps.

---

### Post by AvinThat on 2010-07-07
Hi,

no unfortunately it isn't the card reader cos that would be easy to leave one in there.

It's definitely udevd - and it's being flooded by messaged about card0....which a quick google search appears to the the video.

I've search through loads of the results and none seem to be conclusive.

No idea how to stop this, it's completely chewing the battery up. 

Windows 7 gives me 6 1/2 hours on battery.....Ubuntu has managed 2 1/2

---

### Post by iggy30 on 2010-07-07
I have a very similar problem on a 64-bit Core 2 Quad desktop machine (with Intel GMA X4500 graphics)  that I recently acquired and installed Karmic on.  Luckily, for me, this problem is only taking 20-30% CPU (not 100%, so the machine is still very usable).  The CPU usage sometimes starts right after I login, but sometimes it doesn't start till hours later.  The problem always starts after I start watching, and then quit, a video (player doesn't matter).

According to udevadm monitor, it has to do with card0's interaction with both the Kernal and the Udev service (card0 is not the card reader, since disabling the card reader in the BIOS doesn't alleviate the problem).  Some of the solutions I've seen included "sudo killall udevd" (not only did that not fix it for me, but I cannot unplug and replug something that was connected to the computer via USB when I killall'd udevd, but plugging in new things works fine [reboot fixes this]), stopping the udev service (while it does stop the CPU usage and Udev's messages in udevadm monitor, the Kernal messages remain.  Stopping the service also disables USB auto-mounting, which I don't like since both my keyboard and mouse are wireless devices that turn off after a period of inactivity), and removing NTFS devices from fstab (I have none listed on mine, just the processor and ubuntu's ext3 file system [I dont have a swap]).

I have noticed that sometimes the problem just corrects itself, and I have noticed that playing a video in full-screen stops udevd's CPU usage (which is odd, cause the video uses less CPU than udevd did!), but resumes when I quit full-screen.  Since all signs are pointing to something related to the on-board graphics, I was thinking about getting a graphics card and just disabling the on-board graphics, but I wouldn't want to spend the extra money unless I had to.

Any solutions or insights into this problem would be greatly appreciated!

---

### Post by AvinThat on 2010-07-08
Hi,

Yeah the research I've done points to that as well.

I'm on a laptop so dont have the option of putting another card in. Although, from what I've read on other sites it seems that it's not unique to on board graphics.

Strange thing is, this morning I've booted from scratch and the problem has gone. Idle is now at 1%, battery has doubled in time left. I've changed absolutely nothing.

Don't understand. It'll probably come back later

---

### Post by AvinThat on 2010-07-09
It did indeed come back, and has gone again.

It appears to be completely random. Nothing has changed with the set up. I have one USB mouse plugged in on all occasions.

Very very odd

---

### Post by Arise on 2010-07-10
It's the problem of Intel x4500 video driver (or, let's say, its compatibility with kernel architecture; if you need more information on this, look thru udevd logs; anyway, this problem was discussed over the internet a while ago). No solution so far. Desktop mobo owners can install a discrete video card (doing so definitely solves the problem, GTS 250 did so for me).
Stopping udevd may be kinda helpful, until you find that you have to turn it on again every time you insert a flash drive...

---

### Post by iggy30 on 2010-07-11
> **Arise said:**
> It's the problem of Intel x4500 video driver (or, let's say, its compatibility with kernel architecture; if you need more information on this, look thru udevd logs; anyway, this problem was discussed over the internet a while ago). No solution so far. Desktop mobo owners can install a discrete video card (doing so definitely solves the problem, GTS 250 did so for me).
Stopping udevd may be kinda helpful, until you find that you have to turn it on again every time you insert a flash drive...

Thanks for the info.  Guess I know what my next purchase is going to be :D

---

### Post by Arise on 2010-07-11
_[Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440411")_ one may find more info on this bug
BTW 32-bit systems are also affected.

---

### Post by Arise on 2010-07-11
Oh I forgot, there is a workaround, but it involves patching the kernel. The patch disables HDMI hotplug function and sometimes causes troubles with some third party hardware. See link above.

---

### Post by AvinThat on 2010-07-12
The problem seemed to be linked to my boot problem I was having.

I've upgraded the BIOS as I realised it it wasn't the latest version.

Now Ubuntu loads very quickly and idles around 2-5% CPU

---

