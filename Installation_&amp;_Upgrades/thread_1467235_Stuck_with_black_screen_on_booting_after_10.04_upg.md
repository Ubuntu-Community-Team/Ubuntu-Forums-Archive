---
title: "Stuck with black screen on booting after 10.04 upgrade"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by M@s on 2010-04-30
Hey!

Yesterday I upgraded from 9.10 to 10.04 via Update Manager. But when the upgrade procedure was finished and I made a reboot, I only come to the Ubuntu logo appears for a second, then the screen turns completely black and nothing happens. I then have to reboot via the power button.

But I can get it working with so far no problem, by booting to the third option in the boot options list. In the list there are several options, something like this:

1. Ubuntu 10.04
2. Ubuntu 10.04 recovery mode
3. Ubuntu 10.04
4. Ubuntu 10.04 recovery mode
... and some other options...

Now the question is; what does this mean when there are several alternatives with the same name? What is the difference between alternative 1 and 3, other than 3 is working and 1 is not? Is there any problem running alternative 3 instead of 1, and if so how do I get it to boot from alternative 3 as standard?

If this is not the right way to do it, how can I figure out what the error is on alternative 1?

Thanks,
M@s

---

### Post by stef-l on 2010-05-01
Please may I request help with the same issue? 
I run dual boot with Windows XP SP3 Nvidia 6200 graphics card
Was running 8.04LTS very happily,upgraded overnight to 10.04LTS via update manager.  This worked fine until the 'restart computer to complete upgrade stage' and now I have a black screen with a frozen cursor.  None of the options at boot does anything, although the 2 recovery mode options do list a lot of things which it thinks have not worked; I understand none of this and there's far too much to try and reproduce here.  The word MONITOR does appear, suggesting there's possibly a graphics card issue?

But this card worked fine under 8.04!

Any suggestions about what to try next much appreciated, but if they involved trying to do the update again, or anything like that, will soon use up all my monthly download allowance..

stef-l

---

### Post by splodgebat on 2010-05-01
I have a similar problem.
 
I have been running Ubuntu 9.10 very successfully on a Fujitsu Siemens S7010 laptop.
 
I upgraded to 10.04 using Update Manager - and when the update was completed the machine refused to boot. I get some initial boot screens and then the screen goes black, disk activity stops etc.
 
I downloaded the 10.04 ISO image and tried both booting from that - and using it to boot from the HD and tweaking boot options - same results in both cases - black screen etc...
 
The only interesting thing I did notice was that during the update I got one error dialog which said something like "Resource not found - gconf..." - something to do with graphics card config?
 
Unless I can find a quick fix I shall be re-installing 9.10 (I checked, and I can still boot fine from the 9.10 ISO CD - so not a new hardware fault).
 
Any help would be very gratefully received...

---

### Post by skbhat03 on 2010-05-01
Do the following:

1. When you insert the CD and boot, you will get a screen with a small rectangle (keyboard) and a human figure at the bottom of the screen. When u arrive at that screen, just press any key, space bar will do.
2. You will get the language option, select English and press enter, you will be taken to a screen with options for installation.

3. Make sure the option "Try Ubuntu without any changes" is selected (don't hit enter yet)

4. Now press F6 on ur keyboard.

5. You will see a small pop up on the right hand side of the screen, just hit escape to make it go away. And you can see a long command line which is already there.
Just start typing 
i915.modeset=0 xforcevesa and press enter.

And from there it should work fine :)


Best regards,
Subbu.

---

### Post by splodgebat on 2010-05-01
Thanks for the super-fast response - I think I have found a different fix, but I'll try yours as well.
 
The workaround I found:
1. Boot from the Ubuntu 9.10 CD
2. Mount the internal HD and look for /etc/X11/xorg.conf - its missing!
3. Copy a new "known good" xorg.conf file to the HD (I had to use sudo cp ... otherwise I got permission problems)
4. System boots fine.
 
So the problem was that the upgrade had deleted my xorg.conf file.
 
Also strange though that the 9.10 CD boots fine - whereas the 10.04 will not boot.
 
Maybe an interaction between Ubuntu 10 and my hardware??
 
Anyway - thanks for the suggestion, which I'll certainly try as well.

---

### Post by arevirlegna on 2010-05-02
Hi everyone,

Basically same problem. I upgraded from 9.10 to 10.04 using the Update Manager. After reboot, I get Ubuntu logo, and then a blank screen.

I tried the recovery mode. I selected the failsafe graphics mode. At the end, I get a couple of messages saying that there was a problem with X: no screens found --the log file for starting X in failsafe mode has these messages.

I tried several things people have pointed out in this thread: starting using the 3rd option in the list presented by grub (no luck), checking for the existence of /etc/X11/xorg.conf  (it is there. The installer did commented staff related to my wacom tablet, but the information about the monitor and displays is the same.)

This is my old Dell Latitude D505 laptop with 1GB ram. Integrated graphics. 
This is the laptop I use everyday, for everything...now I am stuck!
Any ideas? :confused:

---

### Post by Esau on 2010-05-02
Hi everyone. I had the same problem and this worked for.  Thanks to manoynmonic for the solution:    Re: HELP...cannot boot into 10.04 after upgrade I had the same issue - old kernels worked, but the newer one wouldn't. What worked for me was to boot into the older kernel, and install a kernel from the ppa (a few notches newer than the one that ships with the Lucid iso).  I got it from the index here: [http://kernel.ubuntu.com/~kernel-ppa....34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa....34-rc5-lucid/)  There is one that came out yesterday that is newer than the link above, but I know 2.6.34 works perfectly (for me).   THREAD: [http://ubuntuforums.org/showthread.php?t=1467019](http://ubuntuforums.org/showthread.php?t=1467019)  Hope this helps!

---

### Post by jagland on 2010-05-02
Just upgraded a Lat D505 to LTS 10.04 (from 9.10)

Had the black screen with my d505 - no easy way to get into grub etc... so resorted to booting of a CD (lucky found my 9.10 CD),Connected to my network (wireless) and googling to find the clue that I needed the 2.6.34 kernel...

Mounted my root partition, Setup as a jail i.e. mount proc and udev and download the kernel from here - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

So a bit like this...

> 
mkdir /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
mount -t proc proc /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
cp /etc/resolv.conf /mnt/ubuntu
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb)
dpkg --install linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb


---

### Post by M@s on 2010-05-05
> **Esau said:**
> Hi everyone. I had the same problem and this worked for.  Thanks to manoynmonic for the solution:    Re: HELP...cannot boot into 10.04 after upgrade I had the same issue - old kernels worked, but the newer one wouldn't. What worked for me was to boot into the older kernel, and install a kernel from the ppa (a few notches newer than the one that ships with the Lucid iso).  I got it from the index here: [http://kernel.ubuntu.com/~kernel-ppa....34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa....34-rc5-lucid/)  There is one that came out yesterday that is newer than the link above, but I know 2.6.34 works perfectly (for me).   THREAD: [http://ubuntuforums.org/showthread.php?t=1467019](http://ubuntuforums.org/showthread.php?t=1467019)  Hope this helps!

Thanks! I upgraded to kernel 2.6.34 RC6 and now it works like a charm!

Thank you all!

---

### Post by arevirlegna on 2010-05-22
> **jagland said:**
> Just upgraded a Lat D505 to LTS 10.04 (from 9.10)

Had the black screen with my d505 - no easy way to get into grub etc...  so resorted to booting of a CD (lucky found my 9.10 CD),Connected to my  network (wireless) and googling to find the clue that I needed the  2.6.34 kernel...

Mounted my root partition, Setup as a jail i.e. mount proc and udev and  download the kernel from here - [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc5-lucid/")

So a bit like this...

Awesome info. Did it and it worked like a charm (I installed  v2.6.34-rc7-lucid instead since it was available). Only a few notes to  have a more complete set of instructions:

[LIST]
[*]Prefix all the  commands in jagland's post with **sudo **--don't worry, the liveCD  will not ask you for a password
[*]Find out in which partition you  have your ubuntu installed. My d505 is dual-boot and Ubuntu is in sda3,  not sda1 (use  **fdisk -l** to find out --and, that is a lowercase L)
[*]Download  the kernel package (the .deb file in the url) to your hard drive  (/mnt/ubuntu), not to the ubuntu home of the liveCD (why? see next step)
[*]change  the root to /mnt/ubuntu 
Why? If you are using a liveCD, your hdd is  not mounted at / so, dpkg will try to install the new kernel image on  the file system created by the liveCD, not on your hdd. By changing the  root to /mnt/ubuntu, dpkg will install the new kernel in the right  place. Type **exit** to return to the way it was before
[/LIST]
So,  the commands look like:
```

sudo mkdir /mnt/ubuntu
sudo mount /dev/sda1 /mnt/ubuntu
sudo mount -t proc proc /mnt/ubuntu/proc
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo cp /etc/resolv.conf /mnt/ubuntu
cd /mnt/ubuntu
sudo chroot  /mnt/ubuntu
sudo wget [http://kernel.ubuntu.com/~kernel-ppa...34rc5_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc5-lucid/linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb")
sudo dpkg --install  linux-image-2.6.34-020634rc5-generic_2.6.34-020634rc5_i386.deb 			 		
```

If everything goes well, you should be able to restart  your d505 without problems.
You might want to delete that huge .deb  file you now have in /
Cheers!

---

### Post by alibro on 2010-05-27
> **splodgebat said:**
> I have a similar problem.
 
I have been running Ubuntu 9.10 very successfully on a Fujitsu Siemens S7010 laptop.
 
I upgraded to 10.04 using Update Manager - and when the update was completed the machine refused to boot. I get some initial boot screens and then the screen goes black, disk activity stops etc.

 
I downloaded the 10.04 ISO image and tried both booting from that - and using it to boot from the HD and tweaking boot options - same results in both cases - black screen etc...
 
The only interesting thing I did notice was that during the update I got one error dialog which said something like "Resource not found - gconf..." - something to do with graphics card config?
 
Unless I can find a quick fix I shall be re-installing 9.10 (I checked, and I can still boot fine from the 9.10 ISO CD - so not a new hardware fault).
 
Any help would be very gratefully received...

I have been trying to install 10.04 on the same model of Fujitsu laptop with no joy so far. Using "i915.modeset=0 xforcevesa" allows the laptop top boot without crashing (I hear the startup tones) but the display resolution seems to be out of range as it remains blank apart from some flickering on the right hand side. Any suggestions how to force the 1024x768 when forcing vesa mode?

Thanks
[I]
Update!
I connected an external monitor which could handle the stupid resolution which 10.04 decided to use, changed to a more appropriate 1024 x 768 and changed back to the laptop display. It worked but is not a usable solution.[/I]

Why Ubuntu did you screw up your system for so many people???????

---

### Post by ketansp on 2010-06-11
pls help. i am having similar but deeper problem. 

[http://ubuntuforums.org/showthread.php?p=9445778#post9445778](http://ubuntuforums.org/showthread.php?p=9445778#post9445778)

---

### Post by K7AAY on 2010-06-12
> **M@s said:**
> 
{snip}

But I can get it working with so far no problem, by booting to the third option in the boot options list. In the list there are several options, something like this:

1. Ubuntu 10.04
2. Ubuntu 10.04 recovery mode
3. Ubuntu 10.04
4. Ubuntu 10.04 recovery mode
... and some other options...
{snip}


Look at the numbers following 10.04
for me, 2.6.32-22 fails, yet 2.6.32-16 works.
Known bug, no solution yet.
Stay tuned.

---

