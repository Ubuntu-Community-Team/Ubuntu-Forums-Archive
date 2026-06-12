---
title: "using an AMD/ATI Radeon 6850 on linux"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Nilsb7 on 2011-02-28
SPECS:
AMD Phenom II x4 940 @3.4Ghz
AMD Radeon 6850
2x19inch monitor (see below)
Ubuntu 10.10 x64 version

So I've asked how to install the drivers on here before, and finally got those working by using these commands

sudo apt-get remove --purge xserver-xorg-video-radeon 
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run) 
chmod +x ati-driver-installer*.run 
sudo ./ati-driver-installer*.run 
Go through installation. 
sudo aticonfig --initial 
sudo reboot

the drivers, CCC included, are working fine, see pic.

[IMG]http://img809.imageshack.us/img809/1645/screenshot1th.png[/IMG]

But...

I'm using two monitors.
1. Samsung Syncmaster 901B (19 inch)
2. LG FLATRON L1919S (19 inch)

The option in the previous screenshot is the one I'm using right now, cause it kind of works like Windows extended desktops, but it doesn't "remember where programs where placed last before I closed them. For instance, I prefer using firefox on my right screen (No. 2) but all programs open on the left screen (No. 1) is there any way I can change this? Making programs "remember" where they were placed before closing them the last time? and is there a way to use a different wallpaper on every screen instead of the same on both?

also
I got compiz effects working, but this (see screenshot) still shows up when I select System>Administration>Additional Drivers
[IMG]http://img231.imageshack.us/img231/8486/screenshot2jf.png[/IMG]
Does this mean that the 3D potential of the graphics card still isn't used? I see pretty large amount of CPU usage when for instance spinning around the cube.
I want to know this because I'm also trying to run Counter Strike: Source on here.

Thanks in advance,
Nils

---

### Post by adduds on 2011-02-28
buddy man

I've got the exact! same two problems ATI and CS:S at least you got CCC installed i followed your post exactly; possibly you could help? now when i boot up my whole screens black when the login window should be present....recovery graphics works ok that's what i'm using now

> 01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035d
	Flags: fast devsel, IRQ 7
	Memory at d0000000 (64-bit, prefetchable) [disabled] [size=128M]
	Memory at dc400000 (64-bit, non-prefetchable) [disabled] [size=128K]
	I/O ports at 3000 [disabled] [size=256]
	Expansion ROM at dc440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: fglrx, radeon


---

### Post by Nilsb7 on 2011-02-28
> **adduds said:**
> buddy man

I've got the exact! same two problems ATI and CS:S at least you got CCC installed i followed your post exactly; possibly you could help? now when i boot up my whole screens black when the login window should be present....recovery graphics works ok that's what i'm using now

make sure before you start this, go into recovery mode to reset graphicX  to default and than restarting you're pc so you can install the  drivers. it doesn't work from the recovery.

if you get any errors during install, stop, google time, or just come back here.

Use these commands:

1. removing old drivers
sudo apt-get remove --purge xserver-xorg-video-radeon 

2. download new drivers (warning 1: click this link and then copy the link from the address bar because as you can see this forum shortuns urls. warning 2: this is the link for the 64 bit version)
wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-2-x86.x86_64.run)

3. make them executable
chmod +x ati-driver-installer*.run 

4. starting installation 
sudo ./ati-driver-installer*.run 

5. just go through installation as on windows

6. don't exactly know what this does but I think it automatically generates a xorg.conf that's suitable for you.
sudo aticonfig --initial 

7. you're done, only thing left is rebooting
sudo reboot


should work, have fun

---

### Post by adduds on 2011-03-01
Thanks very much two questions for you 

one i was able to get the driver working i had to set

Graphics: switchable to discrete (in bios)

when back in X 

```
toews@kidlapp:~$ sudo aticonfig --initial
[sudo] password for toews: 
Found fglrx primary device section
 Unable to find any supported Screen sections
```

two

even after "sudo apt-get remove --purge xserver-xorg-video-radeon"

lspci -v

```
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 035c
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at c0000000 (64-bit, prefetchable) [size=128M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at cc040000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

```

---

### Post by Nilsb7 on 2011-03-01
> **adduds said:**
> Thanks very much two questions for you 

one i was able to get the driver working i had to set

Graphics: switchable to discrete (in bios)

when back in X 

```
toews@kidlapp:~$ sudo aticonfig --initial
[sudo] password for toews: 
Found fglrx primary device section
 Unable to find any supported Screen sections
```two

even after "sudo apt-get remove --purge xserver-xorg-video-radeon"

lspci -v

```
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 035c
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at c0000000 (64-bit, prefetchable) [size=128M]
    Memory at cc000000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at 3000 [size=256]
    Expansion ROM at cc040000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

```

I'm not really sure if the "sudo apt-get remove --purge xserver-xorg-video-radeon" is the right command to be honest. I think I added removing fglrx to that command. that might be the problem.

No idea what the command looks like then. probably simply something like "sudo apt-get remove --purge xserver-xorg-video-radeon fglrx" but yeah I'm not sure. Just try it :p

or maybe this (googled)
sudo apt-get remove xorg-driver-fglrx

---

### Post by Nilsb7 on 2011-03-03
So is it working for you adduds?

and is anyone else here able to help me? see original post for questions & info

---

### Post by thanospc on 2011-03-03
hi guys..i have the same video card and intel i7 proccessor with windows 7 and 23" lg monitor via hdmi connection...i want to remove win7 for ever and i am wondering if i can use the hdmi connection with my monitor with this video card on ubuntu...do you know if i can? have you ever try to connect this card with hdmi with a monitor on ubuntu?

---

### Post by Nilsb7 on 2011-03-03
> **thanospc said:**
> hi guys..i have the same video card and intel i7 proccessor with windows 7 and 23" lg monitor via hdmi connection...i want to remove win7 for ever and i am wondering if i can use the hdmi connection with my monitor with this video card on ubuntu...do you know if i can? have you ever try to connect this card with hdmi with a monitor on ubuntu?
I'm currently using it so yes it does work, but it's not that easy. so you might think about keeping windows as backup on a seperate drive.

---

### Post by thanospc on 2011-03-03
what do you mean is not that easy? first i must do the connection with dvi and then install the drivers and after the installation do the connection with hdmi? which are the steps i must do?Please help me!! :)

---

### Post by Nilsb7 on 2011-03-03
> **thanospc said:**
> 
what do you mean is not that easy? first i must do the connection with  dvi and then install the drivers and after the installation do the  connection with hdmi? which are the steps i must do?Please help me!! :smile:


1. Have you ever used Linux before?
2. Are you sure you'll never need windows anymore? i7 sounds to me like something I'd use for gaming... (which you pretty much can't do on ubuntu, besides some old games through wine)
3. It doesn't matter what connection you use to connect your monitor. It's the graphic cards driver that causes the problem.

---

### Post by thanospc on 2011-03-03
i have a laptop and i am using ubuntu since 7.04 version i think...i have used and other distros such as fedora and archlinux...but the laptop has nvidia geforce 8600m gt so i didnt have problem with drivers...i dont know about ati so thats why i asked you...the pc had win7 when i purchased it so i want to make a format and install ubuntu but i didnt know if i will have problems  with hdmi...my job is developer so i dont mind if i dont play games ^^

---

### Post by Nilsb7 on 2011-03-03
> **thanospc said:**
> i have a laptop and i am using ubuntu since 7.04 version i think...i have used and other distros such as fedora and archlinux...but the laptop has nvidia geforce 8600m gt so i didnt have problem with drivers...i dont know about ati so thats why i asked you...the pc had win7 when i purchased it so i want to make a format and install ubuntu but i didnt know if i will have problems  with hdmi...my job is developer so i dont mind if i dont play games ^^
as long as you get the drivers working it should be fine. and even I got that working (eventually xD) and I barely know anything about linux.

---

### Post by thanospc on 2011-03-03
so at the beggining i must have the monitor connected on tower via dvi or vga and then when i install ubuntu i will install the ati drivers from restricted drives on ubuntu...and then when i istall the drivers i ll connect my monitor again with the tower via hdmi connection?

---

### Post by Nilsb7 on 2011-03-03
> **thanospc said:**
> so at the beggining i must have the monitor connected on tower via dvi or vga and then when i install ubuntu i will install the ati drivers from restricted drives on ubuntu...and then when i istall the drivers i ll connect my monitor again with the tower via hdmi connection?
Dude did you even read the rest of the thread? and as I've said before to, DVI or VGA doesn't matter.

---

### Post by thanospc on 2011-03-04
And what about additional drivers that ubuntu recommends to you (ATI/AMD proprietary FGLRX graphics driver) did you try it?
do you know if this driver is working well?

---

### Post by Nilsb7 on 2011-03-04
> **thanospc said:**
> And what about additional drivers that ubuntu recommends to you (ATI/AMD proprietary FGLRX graphics driver) did you try it?
do you know if this driver is working well?
Those drivers DO NOT WORK. That's the problem. You will get a black screen at startup when the login screen is supposed to show up.

---

### Post by thanospc on 2011-03-04
:/ and when you put the drivers from site of ati the others drivers why are still in the list?
and something else...when a new kernel update comes out you must install the drivers from the ati sire again?? (sorry for my english)

---

### Post by Nilsb7 on 2011-03-04
> **thanospc said:**
> :/ and when you put the drivers from site of ati the others drivers why are still in the list?
and something else...when a new kernel update comes out you must install the drivers from the ati sire again?? (sorry for my english)
No idea.

---

### Post by Nilsb7 on 2011-03-06
bumping this thread for replies on my own question in my first post.

---

### Post by Nilsb7 on 2011-03-06
> **Nilsb7 said:**
> bumping this thread for replies on my own question in my first post.
Again.

---

### Post by Nilsb7 on 2011-03-08
> **Nilsb7 said:**
> Again.
and again.

---

### Post by Nilsb7 on 2011-03-08
> **Nilsb7 said:**
> Again.
aaaaand again.

---

### Post by Hakunka-Matata on 2011-03-08
This is a rather humourous Thread.  I'm not bashing you Nilsb7, I just never saw a new request for help go so awry!!  Good Luck, my system is not like your system, sorry, otherwise I would help.

here, I'll even add the next "bump" for you



BUMP

---

### Post by Nilsb7 on 2011-03-08
> **Hakunka-Matata said:**
> This is a rather humourous Thread.  I'm not bashing you Nilsb7, I just never saw a new request for help go so awry!!  Good Luck, my system is not like your system, sorry, otherwise I would help.

here, I'll even add the next "bump" for you



BUMP
Yea sure thanks.

---

### Post by emilianozublena on 2011-05-13
Hi! im new to these forums, had been user of ubuntu for a couple of years now, recently i changed my desktop and bought this amazing video card.

I was having the same issues that everyone else has, but i found the commands needed to fully uninstall fglrx from your system, its in the troubleshooting area of the wiki that ubuntu has ;)

sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

After i did this, i rebooted my system and then installed the drivers downloaded from ati site, then voilá! its working ;)

Cheers! :popcorn:

---

### Post by Nilsb7 on 2011-05-13
> **emilianozublena said:**
> Hi! im new to these forums, had been user of ubuntu for a couple of years now, recently i changed my desktop and bought this amazing video card.

I was having the same issues that everyone else has, but i found the commands needed to fully uninstall fglrx from your system, its in the troubleshooting area of the wiki that ubuntu has ;)

sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

After i did this, i rebooted my system and then installed the drivers downloaded from ati site, then voilá! its working ;)

Cheers! :popcorn:

Sorry I've completely forgotten about this thread.
Here are the commands I used. Just edit the wget link if there's a new version.

sudo aticonfig --uninstall (--force)

sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx

wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)

chmod +x ati-driver-installer*.run
sudo ./ati-driver-installer*.run

Go through installation.

sudo aticonfig --initial

sudo reboot


Hope this helps someone.

---

### Post by finndo on 2011-10-06
just bought an XFX 6850 and this worked for me

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide")

could not have been simpler, just follow all the steps.


Gigabyte GA-990FX-UD3
XFX Radeon 6850
AMD Phenom II 1090T

---

