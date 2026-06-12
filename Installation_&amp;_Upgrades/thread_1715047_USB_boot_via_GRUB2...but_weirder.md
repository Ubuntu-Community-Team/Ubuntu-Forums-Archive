---
title: "USB boot via GRUB2...but weirder"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by NJPinator on 2011-03-26
Hey Ubuntu users!!!

So I have a really old (about 10 years) desktop PC manufactured by Packard Bell, and would like to get Lubuntu 10.10 running on it. I had previously burnt a CD with it, but boot time was incredibly slow on the machine and installation of Lubuntu crashed my system. As a result, I created a LiveUSB (as you do).

When I entered my CMOS, I discovered the BIOS on my machine isn't able to boot from USB, and I wasn't able to find a BIOS update for my AMIBIOS chip on the American Megatrends website. So I booted my GParted Live CD and created an ext4 partition at /dev/sda3, which I proceeded to install GRUB2 onto via the commands:

```
$ sudo su
# mkdir /mnt/grub/
# mount /dev/sda3 /mnt/grub/
# grub-isntall --no-floppy --root-directory=/mnt/grub /dev/sda
```

This, as planned, succeeded; I can now get into a GRUB2 prompt when my machine boots...! The only problem is, GRUB2 won't detect my USB...or any device other than my hard drive :(

So, is there any way I can get GRUB2 to find my USB?

P.S. The USB works fine on my laptop, which does support USB booting. I can also boot the USB on my laptop via its GRUB2 command line, using:

```
grub> set root='(hd1,1)'
grub> chainloader +1
grub> boot
```

---

### Post by Hedgehog1 on 2011-03-26
If you create a CD for the 'plop' boot loader: [http://www.plop.at/en/bootmanager.html]("http://www.plop.at/en/bootmanager.html"), this CD will load the USB drivers so you can continue the boot off of USB.

***The Hedge***

:KS

---

### Post by NJPinator on 2011-03-26
If only you knew the trouble I've had with Plop! I'd previously tried it, but it fails to boot from my device...if you see my post >>[here]("http://forum.plop.at/index.php/topic,1157.0.html")<<, it's explained in detail. But thanks for the advice, anyhow...

---

### Post by drs305 on 2011-03-26
If you have grub2 installed and working, you should be able to boot the ISO directly from a drive. And once booted, you can also install it using the procedure I describe in the following link. Since you probably aren't at a rescue prompt, the procedure should be even a bit easier, and if you have access to the /etc/grub.d folder you can even make a menu for the ISO image. The second link has lots of ISO menuentries.

[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

---

### Post by NJPinator on 2011-03-27
Again, you're missing a bit. I can't loopback an ISO because GRUB isn't detecting the USB that my ISO and/or Bootable Partition is on! It's a bit of a weird one, but maybe it's because my BIOS can't boot from USB natively???

Anyways, here's the output of an "ls" at the grub prompt:

```
grub> ls
(hd0) (hd0,msdos1) (hd0,msdos2) (hd0,msdos3) (fd0)
```

I'd expect my USB to show as...

```
(hd1) (hd1,msdos1)
```

...after what already appears. GRUB only seems to be able to detect my internal hard drives!

P.S. GRUB2 is installed to the MBR of (hd0) (i.e. /dev/sda), and the GRUB2 "/boot" folder is at an ext4 partition, (hd0,msdos3) (i.e. /dev/sda3).

(hd0,msdos2) (i.e. /dev/sda2) is my Windows ME installation and (hd0,msdos1) (i.e. /dev/sda1) is my Windows Diagnostics (WinRE) partition with the "diag" boot flag.

UPDATE ==============================================

Oh, wait...do you mean put the ISO on my hard-drive so I can loop-back boot it from there? I'll try that, anyhow -- even if it wasn't what you meant.

UPDATE 2 ============================================

Even so, this DOES solve my issue of speeding up access to the Lubuntu desktop. What it DOESN'T solve is being able to boot from a USB stick, which I'd still like to be able to do in the meanwhile. Any ideas?

---

### Post by NJPinator on 2011-03-27
My Lubuntu 10.10 ISO is now on my Windows ME partition @ "(hd0,2)/Downloads/ISOs/lubuntu-10.10.iso", which is FAT32 formatted.

After reading through your post on "loopback loop"-ing ISOs, and seeing that you've manually specified where the kernel and initial ramdisk files are located within the ISO, it got me wondering...

Couldn't you chainload them using...

```
grub> loopback loop (hdX,Y)/file.iso
grub> chainloader +1
grub> boot
```

..., or are the bootloaders not within the ISOs themselves? If not, what gets the bootloader when you write the ISO to a USB or CD/DVD? This is kind of confusing me...a little.

Also, could I get the kernel and initrd locations from a script in /boot within the ISO? I did this last time when my laptop couldn't get GRUB to boot from a logical partition. (I basically copied the text within some *.cfg file into the GRUB prompt, and it booted flawlessly!!!)

P.S. I'm about to boot the ISO now...wish me luck!

UPDATE ================================================

I managed to get the ISO to boot, but it failed to finish loading X11. However, tty terminals 1 to 6 are available by pressing CTRL+ALT+Fx, where x is the tty#. All I get after boot is a mouse on a black desktop, but the terminals function properly:

```
ubuntu@ubuntu:~$
```

---

### Post by NJPinator on 2011-03-30
Come on, guys! I haven't solved this issue yet... :( I still can't get Lubuntu to boot properly! Here's a review for those who've already tried helping me, or if you're not sure what's been going on exactly:

* I burned a **Lubuntu 10.10 "Maverick Meerkat" CD** , downlaoded from the [official website]("http://www.lubuntu.net"). The CD boots fine, but is slow (as CDs are) and the installation procedure crashes my machine

* I created **a Lubuntu USB**, but my BIOS/CMOS doesn't support USB booting

(I also could not find a BIOS update for my 2001 AMIBIOS. If anyone can help my here...thanks a bunch!)

* I installed the [**PLOP boot manager**]("http://www.plop.at/"), but this also fails to boot from my USB

(for more information, or if you think you can resolve my PLOP issue, read [this forum post]("http://forum.plop.at/index.php/topic,1157.0.html"))

* So I tried to **boot my USB from GRUB2**, installing it on my hard-drive's MBR using the command *grub-install* through my GParted LiveCD, putting the */boot/grub* directory on a 7MiB ext4 partition @ /dev/sda3 (or (hd0,3) to GRUB2)

(GRUB2 failed to detect my USB device, which I'd assumed to be found as...
```
(hd1) (hd1,msdos1)
```
Instead, the *ls* command only gave me...
```
(hd0) (hd0,msdos1) (hd0,msdos2) (hd0,msdos3) (fd0)
```
Could this be due to my BIOS not supporting USB boot?

* Taking a different approach, I tried **booting the ISO off my hard-drive** directly using a *loopback loop* command to mount the ISO at the fictional (loop) partition, and boot it from there

(The OS booted well, until I was stuck with a black screen with a cursor. The cursor responded to my mouse, but there was no desktop to interact with. However, I can access the tty's by pressing CTRL+ALT+Fx, where 'x' is the tty number. These work fine. Would there be any way of installing the full GUI Lubuntu Desktop via the terminal? Any GUI applications obviously give me "cannot open display!".)

* Now, I'm lost for ideas, partially because no-one has posted on this thread since my last failed attempt. I apologize to users **drs305** and/or **Hedgehog1** in advance if they just haven't checked this thread or have no info for me. Even though a response would be nice! :D

---

### Post by drs305 on 2011-03-30
> **NJPinator said:**
> (The OS booted well, until I was stuck with a black screen with a cursor. 
1. That sounds like a video problem. If you can set the kernel option "nomodeset" you may be able to boot and then install a driver via System, Administration, Addl Drivers.

If you are able to get to the Grub menu, you would press "e", edit the first menuentry, and use the cursor to remove "quiet splash" (if present) and add "nomodeset". Then CTRL-x to boot.

2. If you get the two icons in the bottom middle of the screen as the CD/ISO boots, you should be able to press F6 twice to get to an options menu, where you can also select "nomodeset" as well as some other options.

If you are able to mount the ISO, and are using G2, you can install from there. You just have to unmount the /isodevice to be able to complete the install. See my signature link "ISO Install"

---

### Post by NJPinator on 2011-03-31
Hi there again.

Adding the "nomodeset" parameter wasn't needed when booting from a CD, but it'll be easy enough for me to try. By the "two icons", do you mean the accessibility circle and keyboard? I don't even get that when booting from CD, because it skips it, unlike the traditional Ubuntu CD. It automatically takes you to the menu with the options:

* Try without installing
* Install Lubuntu
* Test memory
* Boot from first HDD

Obviously I can press F6 from **there** to get the "nomodeset" option and the "acpi" stuff. But via grub I guess I can just add the parameter to the end of the "linux /casper/vmlinuz ..." line.

Also, could you possibly explain in more detail the process of installing from the GRUB2 prompt directly. I don't think I'll need to unmount the /isodevice directory, as I'm not installing to the partition the ISO resides on, but I'll look at your ISO-Install tutorial. Thanks in advance, I hope this works!

---

### Post by drs305 on 2011-03-31
> **NJPinator said:**
> By the "two icons", do you mean the accessibility circle and keyboard?
Yes. But how dare you use proper terminology in a support forum!

> 
Also, could you possibly explain in more detail the process of installing from the GRUB2 prompt directly. I don't think I'll need to unmount the /isodevice directory, as I'm not installing to the partition the ISO resides on, but I'll look at your ISO-Install tutorial. Thanks in advance, I hope this works!

If you have Grub2 installed, it's possible to mount the ISO file rather than boot from a CD/USB. I rarely burn Ubuntu or rescue CDs, as they will almost all boot from the Grub menu. While I build a menuentry in a custom menu, the same commands could be issued from the terminal I expect. The links to the ISO stuff are in my signature line.

I've found that when installing via the ISO the installer complains in the steps following the partition designation if /isodevice isn't unmounted. Unmounting it doesn't appear to affect the CD's installer adversely, but it won't continue as long as /isodevice is mounted. This may or may not apply on the alternate CD but it has happened each time I've tried doing it with a normal Ubuntu installation CD.

---

### Post by NJPinator on 2011-04-02
> **drs305 said:**
> Yes. But how dare you use proper terminology in a support forum!

:D Just to clarify...haha!

> **drs305 said:**
> While I build a menuentry in a custom menu, the same commands could be issued from the terminal I expect.

That's exactly what I did...via the GRUB2 prompt, anyway. I simply copied your commands into a plain text file in Windows, and then used the **cat** command to view the copied commands, which I then proceeded to type in.

> **drs305 said:**
> ...the installer complains in the steps following the partition designation if /isodevice isn't unmounted. Unmounting it doesn't appear to affect the CD's installer adversely, but it won't continue as long as /isodevice is mounted.

I guess I'll try both, with and without unmounting the **/isodevice** point. Just to be sure, would you unmount it *before* even starting the installer program? Or as you said, after specifying the installation partition?

Also, I actually haven't tried any of these soultions on my system yet...schoolwork's a pain, and I'm in the UK. Let's hope Sunday's events will be a victory!

---

### Post by drs305 on 2011-04-02
> **NJPinator said:**
> 
I guess I'll try both, with and without unmounting the **/isodevice** point. Just to be sure, would you unmount it *before* even starting the installer program? Or as you said, after specifying the installation partition?


I believe I have unmounted it just after the installer starts (you have to boot 'Try It' so you can get to a terminal to unmount it later. Then start the installer from the Desktop with the terminal available. I think I've even waited until the installer complained about not being able to unmount everything, at which time I unmounted it and then selected the 'retry' option.

---

### Post by NJPinator on 2011-04-14
I followed the instructions in your "ISO Install" tutorial and got a very similar outcome...here's what happened:

I booted the ISO as told in your "ISO Install" tutorial, omitting the set of "set prefix=..." commands as I was at a working grub prompt (also, the prefix variable was already set to (hd0,3)/boot/grub , which is where my GRUB2 modules are).

In addition, I added the "nomodeset" setting to the end of the "linux...vmlinuz..." line, as you had suggested would resolve my "video problem". The "nomodeset" option was not required when booting from a CD, and only made a minor difference when following your boot instructions!

Lubuntu had booted exceptionally fast, and it's desktop was available right away. The only issue was my computer not having much RAM (only 128 **MB**, this'll be sorted soon -- I told you it was an old PC!). I got an "out of RAM" error message on tty1 (which I accessed by pressing CTRL+ALT+F1), followed by it killing processes to free memory, all to no avail. My Lubuntu dekstop had soon become nothing but a wallpaper on a screen, and I had to power down my machine. It's a shame I don't have more RAM, but I have a question now...!

**Would it be possible to get Lubuntu to access a Linux Swap partition before getting to booting LXDE?** (i.e. predefined in a file or something / without using a program like GParted, maybe the terminal will work. It did for a while on the tty's.) My swap partition is located at /dev/sda6 (to GRUB it's (hd0,6) ).

P.S. I know it's been a while (actuallly, a week), but I simply haven't had time to try things out.

---

### Post by NJPinator on 2012-10-31
It's been a while (over a year now), but I thought I'd give this thread an update and mark it as "SOLVED". I ended up getting some more RAM for the computer, and installed Windows XP on it, as Lubuntu 12.04 failed to work at a decent speed.

---

### Post by darkonc on 2013-02-17
This solution is for the case where you have a usable grub2 installaiton on your internal hard drive, but are unable to see an external USB drive which has Linux installed on it.

the short answer is:

insmod usbms
insmod ehci
insmod uhci
insmod ohci

Only one of the *hci line  is needed (usually ehci), but older machines may need either uhci or ohci Inserting all 3 works fine.

Those lines should be added to either grub.cfg or custom.cfg (I recommend the latter) in the /boot/grub/ folder on the non-USB drive.

_______________

In my case, I was able to solve the problem (and boot Linux off of the USB drive in this way).
First of all, I installed Linux on the USB drive.  I specified installing grub on the USB drive (sdb, in this case). That way, it should be usable for (other) systems that can boot off of the USB drive via the BIOS.

Then I booted the Linux on my hard drive, mounted the USB root partition (clicked on it in the nautilus sidebar) and did: 
  update-grub2
This placed the menu entries in the bootable grub menu.

(( If you only have grub and it's modules installed on a minimal partition on your local hard drive, you can get a similar result by booting off of a live CD , mounting the drives and running grub-mkconfig:

mount /dev/sda5 /mnt/localHD
mount /dev/sdb1 /mnt/usbHD
grub-mkconfig -o /mnt/localHD/boot/grub/grub.cfg

Change the partitions to suit your system setup, of course.
))


testing:  I then  rebooted to the grub menu
in the grub command line (ctrl-C) , I tried:
insmod usbms
insmod ehci
ls
(at this point the usb drive started showing up).
then I hit 'esc' to go back to the menu, and chose one of the USB linux options.

Final solution:
I edited /mnt/localHD/boot/grub/custom.cfg (which is included at the end of grub.cfg in Ubuntu) and added the following lines:
    insmod usbms
    insmod ehci

At that point, I could boot the usb partitions from grub without any extra work.

---

