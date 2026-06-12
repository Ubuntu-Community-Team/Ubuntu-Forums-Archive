---
title: "ubuntu server blank screen + blinking cursor after install"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by marty80 on 2010-09-23
Hi,

I'm a newbie and trying to install ubuntu server to run a samba home server.

I have installed it from usb as the cd installation failed at the point where you decide which type of installation you want (lamp or samba, etc)

the installation completed but when booting nothing happens, only a black screen with a blinking cursor. pressing the shift key or any other keys doesn't work.

strangely when i boot from the usb flash drive again (and not from the hard drive) the server does boot and asks for the user name and password!!

i have chosen the guided lvm partition with 20% reserved for system files.

my machine is an athlon xp 2GHz (32bit), 1GB, SATA hard drive, nvidia 6600 graphics

my guess is that its a problem with grub and lvm.

many thanks for your help in advance

cheers, martin

---

### Post by marty80 on 2010-09-24
bump

---

### Post by sikander3786 on 2010-09-24
<snip>

Sorry. Wrong post.

---

### Post by canonhead311 on 2010-10-04
Bump... I seem to be having the same issue.  I have done some searching and most forums I have found have the error trying to load X and they fix that in GRUB. I can't seem to get to GRUB.

I did my first server install a couple of weeks ago and starting playing with some options for a home server... I pretty much had it figured out what all I wanted on my server and decided to do a fresh install. I installed it the same way I did a few weeks ago, using the same disk as before writing over the previous partitions. No problem during the install. 

Once prompted to take out my install CD and reboot, it did but after post I get the blinking cursor blank screen and nothing happens. I remember on the first server install it took a little while there and I got worried but then it eventually booted, after the first time it was always quick so I never thought about it again. Now, however it never continues to boot. 

I even have now tried to install it all over again and I get the same thing. Any help would be great. Thanks

---

### Post by Peter09 on 2010-10-04
Jus to clarify,
you installed Ubuntu Server ...... this does not come with a GUI - it should boot to a terminal prompt which is asking for you to login in via username and password - there is no GUI.
 
Is this what you are getting - if so then its installed correctly.

---

### Post by canonhead311 on 2010-10-04
> **Peter09 said:**
> Jus to clarify,
you installed Ubuntu Server ...... this does not come with a GUI - it should boot to a terminal prompt which is asking for you to login in via username and password - there is no GUI.
 
Is this what you are getting - if so then its installed correctly.

Nope, prior to GRUB even loading Ubuntu, I get a blank screen with blinking cursor. I am still fairly new to Linux but have pretty good experience with DOS so I am familiar with Command Line, just not all the Linux cmds or file locations.

---

### Post by Peter09 on 2010-10-04
Have you tried holding down the shift key during boot, that should get to the grub prompt. If you do not have 'dual boot' you will not see a grub menu on normal boot.

---

### Post by canonhead311 on 2010-10-04
> **Peter09 said:**
> Have you tried holding down the shift key during boot, that should get to the grub prompt. If you do not have 'dual boot' you will not see a grub menu on normal boot.


I will have to give that a shot. It's a headless server though so I have to get my monitor back from my wife's PC now, so I will let you know if it works later on.  Thanks

---

### Post by Peter09 on 2010-10-04
Hi,
if you can get to the grub prompt then you can edit the boot line to include the parameter 'noquiet', which should allow you to see where the boot process is stalling. Of cause this all assumes that you are getting to Grub at all.

---

### Post by nothingspecial on 2010-10-04
Stab in the dark here, but if you installed from a usb drive, and set your bios to boot from usb first. And you have any usb drives connected at boot time. Sometimes your server will try and boot from the usb drive that is connected, even though there is no operating system on it, and hang

It`s happened to me before now

---

### Post by canonhead311 on 2010-10-04
Peter - I cannot get to the GRUB loader, it hangs right before that should load.

nothingspecial - I actually installed from a CD, so I did remember to change it back to boot from the hdd (the correct hard drive I might add, since there are 5 of them in there).


After thinking about it a bit today, I remember that I didn't install it exactly the same way I did 3 (or so) wks ago. When it came to partitioning it, I originally set the ubuntu partition to about 40GB (on a 500GB hdd) and the rest was set to unencrypted LVM. This time I just let Ubuntu use the whole disk (minus the swap). Could that be causing some unforeseeable issue... I am not familiar with LVM since computers are a hobby and have nothing to do with my job I don't always keep up with the latest and greatist. 

My wife is a photographer, and has been trying to catch up on photo editing so I am still waiting on that monitor... hopefully will get back to you all soon.

---

### Post by canonhead311 on 2010-10-05
Alright well I seem to have fixed my issue. Maybe someone can give me some insight to what might have been going on...

I tried holding the shift key as well as a few other keys, after reading various forums. Nothing changed, I was still unable to get GRUB to run. 

On my third reinstall I noticed towards the end when it was installing GRUB that the installer flashed something about /dev/sda, well I had installed Ubuntu on what would be /dev/sde     When I did this a few weeks ago, I set my bios to boot from that drive and had no problems.  

So, now just because I was having issues, I changed the physical configuration so that the 500GB hdd was the first disk, reinstalled and it works. So, it would seem to me like it was installing grub somewhere other than where I wanted, but why did that config work before when I tried it?

Thanks all, for your help.

---

### Post by HimeNoHogosha on 2010-12-24
> **canonhead311 said:**
> 
On my third reinstall I noticed towards the end when it was installing GRUB that the installer flashed something about /dev/sda, well I had installed Ubuntu on what would be /dev/sde     When I did this a few weeks ago, I set my bios to boot from that drive and had no problems.  

So, now just because I was having issues, I changed the physical configuration so that the 500GB hdd was the first disk, reinstalled and it works. So, it would seem to me like it was installing grub somewhere other than where I wanted, but why did that config work before when I tried it?


Just wanted to comment that I had the same problem, and your solution worked for me also. The disk I was trying to install to was plugged into SATA3 on my motherboard. After plugging it into SATA1 (I had two other disks which were then plugged into 2 and 3) I reinstalled and had no problems after reboot!

Thanks :)

---

