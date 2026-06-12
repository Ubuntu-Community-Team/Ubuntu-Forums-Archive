---
title: "ati fglrx bricks 10.04 LTS install"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by trocar75 on 2010-05-04
Hi,

So I have the 10.04 LTS amd64 image, and I went through the install process over the live cd. If I boot from the cd and just let it start the installer automatically, my screen flashes very fast with errors I cant read(they move across the screen from right to left diagonally)and it just sits in a loop until I reboot. If I tell it to go to the live CD, then do the install from there, it installs and will boot fine. However, once I have booted, it tells me to activate my ati fglrx drivers for 3d acceleration support(which I need), and it installs them, and asks me to reboot. On reboot, it gets to the Ubuntu splash screen with the 4 red dots, but they start out all red and it immediately locks. I have to power down with the power button, as the system completely locks. Ive tried reinstalling 3 times, happens every time.

once this happens, I can not get to a terminal via ctrl+alt+f1, and I am never prompted to boot into single user mode before the splash screen pops up(i don't get any grub screens on boot, not sure how ubuntu handles the bootloader. Im used to debian)so i really have no way of checking logs to see where the error is. 

I am running an ati hd3850, athlon 64 x2 4000+ if that helps at all. Any ideas?

---

### Post by frantid on 2010-05-04
my splash looked horrible with a 4670, I just removed the splash argument from my kernel line in grub.

---

### Post by quadproc on 2010-05-04
> **trocar75 said:**
> Hi,

So I have the 10.04 LTS amd64 image, and I went through the install process over the live cd. If I boot from the cd and just let it start the installer automatically, my screen flashes very fast with errors I cant read(they move across the screen from right to left diagonally)and it just sits in a loop until I reboot. If I tell it to go to the live CD, then do the install from there, it installs and will boot fine. However, once I have booted, it tells me to activate my ati fglrx drivers for 3d acceleration support(which I need), and it installs them, and asks me to reboot. On reboot, it gets to the Ubuntu splash screen with the 4 red dots, but they start out all red and it immediately locks. I have to power down with the power button, as the system completely locks. Ive tried reinstalling 3 times, happens every time.
...
Did you completely remove the old driver before you installed 10.04?  I ask because I seem to get burned every time that I don't do this.  Somehow, little bits of the old driver seem to contaminate the new kernel.

Also, you probably want to do the driver install yourself rather than letting "hardware drivers" do it.  If you try the latter then you don't have any control over the version of the driver.  I suggest getting the driver's .run file from ATI, put it into a directory of its own, then doing ```
sudo sh <the_ati_install_file_name> --keep --install
```
This will leave behind all of the files and directories that were used so that you can look at them if you so desire.  You can remove them later if you like.

quadproc

---

### Post by trocar75 on 2010-05-04
Thanks Quad, I will give that a shot. 

I didn't remove any old driver, this is off a fresh installation. I install ubuntu, and as soon as it boots after install, it tells me it needs to upgrade my driver, so i let it. My room mates are running ubuntu 10.04 off the same install cd and they installed their drivers that way and it worked fine.

Im downloading from amd site right now, ill post results as soon as i install it.

---

### Post by trocar75 on 2010-05-04
ati-driver-installer-10-4-x86.x86_64.run has been downloaded on a fresh install of ubuntu. 

"you are running a x86_64 machine with glibc-2.1
operating system: debian gnu/linux (or similar) 0.0"

does that all look right?

after confirming that, install goes through without any issues. 

doing a gdm restart after the install goes through makes the screen flash with 
*ERROR* Raw EDID:
*ERROR* EDID checksum is invalid, remainder is 132

And the system locks. I am guessing this is what is displayed behind the splash screen when i boot, but i cannot get to the verbose boot info behind the splash screen before it locks. 

After doing a reboot, i get the same issue. As soon as the splash screen with the 4 dots comes up, they lock at all red and the machine is completely locked up. 

So I cannot get it working with the driver wizard through ubuntu or by installing them from ATI site.

---

### Post by trocar75 on 2010-05-04
ok i got into syslog via a knoppix live cd, i have a repeating error of gdm-simple-slave[14808]: warning: unable to load file '/etc/gdm/custom.conf': no such file or directory, thats the last entry in syslog. 

In my xorg log I get a large set of 

fglrx: no matching device section for instance (BusID PCI:0@0:0:0) found

theres several lines, with the busid changing each time, then it looks to load the driver. 

At the end it saysscreens found, but none have a usable configuration. 

fatal server error: 
no screens found

If there are any other logs you need me to check let me know. If you want me to post entire logs i can do that too.

---

### Post by quadproc on 2010-05-04
> **trocar75 said:**
> ati-driver-installer-10-4-x86.x86_64.run has been downloaded on a fresh install of ubuntu. 

"you are running a x86_64 machine with glibc-2.1
[COLOR=Red]operating system: debian gnu/linux (or similar) 0.0"
[/COLOR] 
does that all look right?

The operating system report is highly suspicious.  It should be the linux kernel version.
> 
after confirming that, install goes through without any issues. 

doing a gdm restart after the install goes through makes the screen flash with 
*ERROR* Raw EDID:
*ERROR* EDID checksum is invalid, remainder is 132
Definitely something wrong here.  I would suspect that this is a bug in 10.04.
> 
And the system locks. I am guessing this is what is displayed behind the splash screen when i boot, but i cannot get to the verbose boot info behind the splash screen before it locks. 

After doing a reboot, i get the same issue. As soon as the splash screen with the 4 dots comes up, they lock at all red and the machine is completely locked up. 

So I cannot get it working with the driver wizard through ubuntu or by installing them from ATI site.I don't know where the problem is located so I can't tell how to fix it.  But it looks like a genuine bug; your best bet is probably to file a bug report in launchpad.  They will need some things like an lspci -vvnn and probably copies of your system and xorg logs so you may want to be prepared to furnish those.

One other thought - there is a new default in 10.04: KMS.  You might try disabling this; see_ _[URL="http://http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg41999.html"]http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg41999.html
[/URL]
Good luck!

quadproc

---

### Post by jeantasse on 2010-05-04
About ATI drivers for linux... As long as I can remember, there is always trouble with ati drivers and linux.  It seems that it just cannot be easy with them.  A company with that much experience should come up with something better.  I'm bitting my fingers ever since I purchase an ATI card and tried linux.  As soon as I have the money, I'm switching back to NVIDIA.  I still think that ATI makes great cards but, my gosh it takes them quite some times to make a good linux driver.  I hope that soon they will work more closely with linux folks.

---

### Post by quadproc on 2010-05-04
> **jeantasse said:**
> ... I hope that soon they will work more closely with linux folks.
ATI has recently done something unprecedented: they released their software interface specifications for their present model graphics cards!  This is making life much easier and better for the open source driver authors.  I think that we will see rapid progress in this arena.

quadproc

---

### Post by alphacrucis2 on 2010-05-04
> **quadproc said:**
> ATI has recently done something unprecedented: they released their software interface specifications for their present model graphics cards!  This is making life much easier and better for the open source driver authors.  I think that we will see rapid progress in this arena.

quadproc

The OSS driver for my 3400 already does 2D acceleration really well. The only reason I am sticking with fglrx is the GPU power management. It runs too hot at present. I am told that this will be addressed with later kernels.

---

