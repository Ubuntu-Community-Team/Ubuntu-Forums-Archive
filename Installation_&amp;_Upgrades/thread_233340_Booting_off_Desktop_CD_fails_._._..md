---
title: "Booting off Desktop CD fails . . ."
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by Wilco on 2006-08-10
So I picked up a shiny new Alienware lappy and thought I'd throw the latest Ubuntu distro on it. I was disappointed to find that things weren't going to go as smoothly as I thought.

Here's what happens:

Booting off the Ubuntu CD, everything goes fine until it gets to "Starting kernel log . . ." At this point it exits the graphical boot for the more traditional white-on-black look. This is where I get stuck.

After about 20 minutes I managed to get it past this point, but again it gets stuck "Running local boot scripts (/etc/rc.local)"

Any idea what the problem might be? My guess would be a problem with either my RAID setup or my SLI setup (but since it's a laptop, I'm hesitant to pull one of the graphics cards to test this theory).

Here are some hardware details, in case it helps:

= Alienware Aurora m9700 Notebook =
- AMD Turion 64 ML42
- Dual GeForce Go 7900 GS cards (SLI)
- Two 100GB HDD, RAID striping setup (Nvidia nforce RAID controller)


Any advice appreciated!

---

### Post by rowanparker on 2006-08-10
You could try the Alternative CD.

---

### Post by Wilco on 2006-08-25
Tried the alternative CD to no avail. Reading through the forum, it sounds like even with my RAID 0 setup, I should still be able to at least boot into the live CD (the SATA/FakeRAID howto even includes this as the first step). It might be the SLI setup, but I have my doubts (I would expect it to simply default to one card, but I could be wrong).

Any advice? Anyone with a similar system that might have some insignt?

---

### Post by Calv!n on 2006-08-28
Hey, I just got an alienware Aurora m9700 as well, and I am having the same problems as you are. My laptop fails to boot off the cd, and thus I cannot install. I'm guessing it has something to do with Ubuntu not liking my STI setup.

Is there a way to disable graphics mode, or something so you can just install ubuntu? I already have my hard drive partitioned and I have a 15 gig partition ready for installation. Any help would be greatly appretiated.

BTW, I heard something about tryinging "no acpi"... idea?

---

### Post by kshymkiw on 2006-08-28
What kind of RAM do you have?  I had an issue installing ubuntu on my PC with PC4200 Memory

---

### Post by Calv!n on 2006-08-28
I have:

1GB Dual Channel DDR SO-DIMM at 400MHz - 2 x 512MB

can you help me?

---

### Post by estimablesir on 2006-08-30
Have the same Alienware laptop with also the same problem. :( 

Can't seem to get past that point either.  Did anyone find a solution?

---

### Post by randell6564 on 2006-08-30
Have a look here [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by sfmadmax on 2006-11-10
> **Calv!n said:**
> Hey, I just got an alienware Aurora m9700 as well, and I am having the same problems as you are. My laptop fails to boot off the cd, and thus I cannot install. I'm guessing it has something to do with Ubuntu not liking my STI setup.

Is there a way to disable graphics mode, or something so you can just install ubuntu? I already have my hard drive partitioned and I have a 15 gig partition ready for installation. Any help would be greatly appretiated.

BTW, I heard something about tryinging "no acpi"... idea?


Hey Calvin and others...      I am a latest convert to Ubuntu I abosuletly love the interface and the synpatic tools along with automatix.. HHowever We all share the same problem.. I also have a Alienware m9700 I picked it up 3 months ago... Current setup is...

SLI 7900 GO GeForce GS
Dual 80 GB Sata Raid 0 with windows
2gb ram

Everything else is standard...  17" etc etc...  Well.. So far my first problem is the video.. I want to use the Live Cd since i've already installed Ubuntu on my desktops at home.. I'm almost 100% converted and Microsoft Free..  I even have Cedega going for Battlefield games and Company of Heroes ...  So we'l see...    I plan on keeping the Sata Raid 0 with windows.. im not going tro install Ubuntu on there.. I picked up a external notebook drive USB and installing ubuntu on that.. I have already experimented with it so i know it works on my desktop..  Heres the deal.. The SLI is giving me the hassle..  From the research I've done so far I think the problem is either with the LCD screen .. Ubuntu doesnt understand the refresh rates or its the SLI setup.. im sure it has something to do with both.. I noticed in the /var/log/Xorg log.. that it tries to probe for external display devices then  after nothing is found has some problems talking to the generic display.. 

So I attached network to the laptop and configured in /etc/network/interfaces to talk to my router.. then used apt-get to download the latest nvidia-glx packages..  I managed to get at least a step ahead.. but still no video.. The errors in the Xorg log changed, My next Test Will be to Try and attach an external monitor and see if it will come up off of that.. If it does then that confirms the issue is the LCD screen. So far tho.. thats where I am.. I'm using this laptop for work / mobile games  ...  And honestly.. I dont wanna keep using windows to work from..  Cgywin is great to Xhost back apps from unix however, i just want a real os to work from :P . .

---

### Post by estimablesir on 2006-12-01
wow, no one has solved this problem yet.  I'm dying to get ubuntu working on my alienware.  I've tried everything, I don't know what else to do.  I'm completely stumped :confused:

---

### Post by Exodus103 on 2006-12-04
I too have an alienware m9700 with a similar setup as most of the other posters have described. I Have not been able to boot from the ubuntu cd, or just about any other live cd linux enviroment. My thoughts are that it is the SLI setup that is causing the problem. But thats only a minorly educated guess. Any other thoughts would be appriciated.

---

### Post by estimablesir on 2006-12-15
> **Exodus103 said:**
> I too have an alienware m9700 with a similar setup as most of the other posters have described. I Have not been able to boot from the ubuntu cd, or just about any other live cd linux enviroment. My thoughts are that it is the SLI setup that is causing the problem. But thats only a minorly educated guess. Any other thoughts would be appriciated.

It can't be the SLI setup, because I bought the laptop with only 1 video card and I'm still having the issue.  Is this problem restricted to Live type distributions or is it all Linux distributions?

---

### Post by Allmighty on 2006-12-16
I have a similar problem with similar hardware- Alienware desktop, AMD 64 X2 Dual 4200+, 2gb ram, Single ati X1900XTX. I boot from the cd, get to the Start/Install/Start in non-graphical/yadayadayada. after i select "Start/Install", Nothing happens, just a black screen and a little flashing white line. BTW, i have a 15g partition, but no swap partition.

ubuntu-6.10-desktop-i386.iso
Hash checks out

Note- Linux n00b

---

### Post by solardeity on 2006-12-19
Im thinking about getting me a Alienware Laptop so ive been looking around to see if Ubuntu goes good with it... And looking at your Problems, i would say that it is the Xserver... 

Okay, what i would do is...... download the Ubuntu DVD .... install in Text mode and after that if the xserver does not work i would do 

sudo dpkg-reconfigure xserver-xorg

then set it to VESA (the nv driver wont work) and set the refresh-rate, fit the settings.. and restart PC

Ubuntu should run after that... then i would install the nvidia beta driver [http://de.nzone.com/object/nzone_downloads_rel70betadriver_de.html]("http://de.nzone.com/object/nzone_downloads_rel70betadriver_de.html")

a how to for the beta driver here: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA#Installing_the_nVidia_Beta_Driver]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA#Installing_the_nVidia_Beta_Driver")

---

### Post by sfmadmax on 2007-01-25
Yes it seems that easy, I have seemed to have got myself a little further. Another recommendation is to disable the Nvidia Raid, i know you can get by Raid 0 / 1 configs with dmraid, however it adds unneeded hassles to the installation. I did actually try updating my nvidia drivers with the beta ones while booted from the live cd.. then try to restart X.. It didn't like it still.. I had the SLI options incorrect I believe. I'm going to try again later this week.. I'll post any progress that i make..

---

### Post by TDub on 2007-03-09
I managed to get into the Live CD to install Ubuntu on my m9700 laptop

My Specs:
AMD Turion
Geforce Go 7800 GS in SLI
Single 100GB HDD
1920x1200 screen

These steps worked for me, let me know how you got on!

Before you start:
[LIST]
[*]Ensure the sound dial on the laptop is up (i.e not on mute!). 
[*]Ensure that you have a valid internet connection via wired Ethernet connected to the laptop (as configuring the wireless with the Live CD is beyond the scope of this HOWTO)
[/LIST]

Turn on laptop

Insert the Ubuntu 6.10 CD into your Alienware Aurora m9700 Laptop

Wait for CD to boot

When the menu appears, pick the first option on the menu, and wait for Ubuntu to load

You will see the Ubuntu logo and progress bar &#8211; as normal

Moments later is where the open source nv driver doesn&#8217;t detect the display properly and the screen goes blank &#8211; as you know else you wouldn&#8217;t be reading this &#61514;. Wait for the startup sound to fire so you know the system has finished loading.


Press Ctrl + Alt + F1 to get to the console

EDIT: Head to [page 4]("http://ubuntuforums.org/showthread.php?t=233340&highlight=m9700&page=4") for improved method with no need for driver download

Download NVIDIA drivers:
For 32-bit:
```
#] wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run

```
For 64-bit:
```
#] wget ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run

```
Type the following
```
#] sudo apt-get install build-essential
#] sudo /etc/init.d/gdm stop
#] sudo killall gdm
#] sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

```
Run though the NVIDIA wizard and it will compile and install a driver for your system. Ensure that it compiles and that it modifies the X config for you.

Last step:
```
#] sudo /etc/init.d/gdm restart
```

X should fire up and you&#8217;ll be looking at the Live CD desktop

Hope this helps

---

### Post by Wilco on 2007-03-26
Wow, I just googled my problem to check in to see if this had been resolved yet, and my original thread was the first result! If only I could get my websites to do that ;-). Thanks TDub for that info - I'm going to make another pass at getting Ubuntu on here - I'll post my findings once I'm done <crosses fingers> . . .

---

### Post by rhydewithdis on 2007-03-26
> **solardeity said:**
> 
Okay, what i would do is...... download the Ubuntu DVD .... install in Text mode and after that if the xserver does not work i would do 

sudo dpkg-reconfigure xserver-xorg

then set it to VESA (the nv driver wont work) and set the refresh-rate, fit the settings.. and restart PC


Hmm, I tried that very command and it didn't work for me!

When I type: ```
sudo dpkg-reconfigure xserver-xorg
```

I got back the response: **/bin/sh/: sudo: not found**  

Anyone have any idea why?

---

### Post by Wilco on 2007-03-27
Hmmm, when I try this I get to the startup sound, but when I switch to tty1 it sis there with "Loading, please wait ..." and a flashing cursor on the line below. Do I need to wait for this? So far I've waited about 15 minutes without anything changing. Anyone else have luck with this yet?

---

### Post by Wilco on 2007-03-29
Update: I made an attempt at installing the lateset Feisty Fawn (7.04) and got the same results.

---

### Post by Wilco on 2007-03-30
Maybe another avenue to pursue is why Fedora would work but not Ubuntu? Obviously it's got to be some kind of hardware issue, but what could it be? Just throwing some thougths out there . . .

---

### Post by Wilco on 2007-04-17
Has anyone else had any luck with this?

---

### Post by colalord on 2007-05-14
> **TDub said:**
> I managed to get into the Live CD to install Ubuntu on my m9700 laptop

My Specs:
AMD Turion
Geforce Go 7800 GS in SLI
Single 100GB HDD
1920x1200 screen

These steps worked for me, let me know how you got on!

Before you start:
[LIST]
[*]Ensure the sound dial on the laptop is up (i.e not on mute!). 
[*]Ensure that you have a valid internet connection via wired Ethernet connected to the laptop (as configuring the wireless with the Live CD is beyond the scope of this HOWTO)
[/LIST]

Turn on laptop

Insert the Ubuntu 6.10 CD into your Alienware Aurora m9700 Laptop

Wait for CD to boot

When the menu appears, pick the first option on the menu, and wait for Ubuntu to load

You will see the Ubuntu logo and progress bar – as normal

Moments later is where the open source nv driver doesn’t detect the display properly and the screen goes blank – as you know else you wouldn’t be reading this &#61514;. Wait for the startup sound to fire so you know the system has finished loading.


Press Ctrl + Alt + F1 to get to the console

Download NVIDIA drivers:
For 32-bit:
```
#] wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run

```
For 64-bit:
```
#] wget ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run

```
Type the following
```
#] sudo apt-get install build-essential
#] sudo /etc/init.d/gdm stop
#] sudo killall gdm
#] sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

```
Run though the NVIDIA wizard and it will compile and install a driver for your system. Ensure that it compiles and that it modifies the X config for you.

Last step:
```
#] sudo /etc/init.d/gdm restart
```

X should fire up and you’ll be looking at the Live CD desktop

Hope this helps

You are a brilliant person and deserve a pat on the back for your very helpful advise.  I was able to get Ubuntu running from the LiveCD and installed on my laptop today while following your instructions.  This being the case, the problem being described by most everyone is almost assuredly a driver related issue, not a hardware issue or display unit incompatibility.  I have the following hardware configuration:

I have an Alienware m9700.
[LIST]
[*]AMD Turion 64 ML44 2.4GHz
[*]17" WideUXGA 1920 x 1200 LCD
[*]Alienware® NVIDIA® Mobile SLi Chipset
[*]2GB Dual Channel DDR SO-DIMM at 400MHz - 2 x 1024MB
[*]200GB (100GB x 2) Serial ATA 1.5Gb/s 7,200 RPM w/ NCQ & 8MB Cache
[*]8x Dual Layer CD-RW/DVD±RW
[*]Dual 256MB NVidia® GeForce™ Go 7900 GS
[*]Internal 802.11b/g WiFi Card w/ Airgo MIMO Technology
[/LIST]

HDD 1 (100GB):
[LIST]
[*]Partition 1 (70GB): Windows Vista Ultimate
[*]Partition 2 (23GB): Linux, Ubuntu
[/LIST]

HDD 2 (100GB):
[LIST]
[*]Partition 1 (93GB): Misc. Windows Games and Documents
[/LIST]

With this hardware configuration and the updated video driver installed Ubuntu Feisty Fawn 7.04 runs fine.

Please Note:  You have to install the updated driver twice.  Install it the first time for use with the LiveCD and then the second time after you have installed Ubuntu to your HDD and have booted from it.

Thank you again for your help!

---

### Post by Rainn on 2007-05-15
Hello everyone :)
im at my first experience with linux aaaaaaand sadly i got the same problem (have an aurora too)
i dont have actuallyt a working internet connection at home that i could use to download the driver
i downloaded the drivers from work, should i be able to to load them from a cd or from an usb drive?
sorry for my noob question but can you tell me how to do that?:P
thanks :)

---

### Post by stefaan.dutry on 2007-05-15
Sorry, posted after only seeing 1 page; therefore my info was not to the point anymore and i deleted it

I appolagize for this.  And i can't find a way to delete my post

---

### Post by dyssident on 2007-05-26
> **TDub said:**
> I managed to get into the Live CD to install Ubuntu on my m9700 laptop

the solution described above worked for me. unfortunately, although X is now running, the gnome desktop never loads after login. any suggestions on where to start figuring out how to get gnome to load would be appreciated.

---

### Post by dyssident on 2007-05-26
> **Rainn said:**
>  should i be able to to load them from a cd or from an usb drive?
sorry for my noob question but can you tell me how to do that?

the easiest way would be to load them from a usb drive. first type `ls /media`. plug the drive in and then do `ls /media` again. the new directory is your usb drive. if the new directory is named /media/disk, the commands youd use would be

```

sudo apt-get install build-essential
sudo /etc/init.d/gdm stop
sudo killall gdm
sudo sh /media/disk/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm restart

```

---

### Post by sfmadmax on 2007-06-01
I got ubuntu working on it,,, I used the server cd.. and installed envy,,,  then envy cleaned up the nvidia config for me.. and got it working SLI as well..

---

### Post by dyssident on 2007-06-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/94048) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Fixed my own problem. Seems that there is a very strange problem with gnome and the hosts file Edit /etc/hosts with `sudo nano /etc/hosts`. It should look like

127.0.0.1 localhost
127.0.0.1 myhostname

change it to 

127.0.0.1 localhost myhostname
127.0.0.1 myhostname

Yea, thats really all it takes.

I also found that on reboot X failed to start, so I had to run the Nvidia installer again. The fix was to edit the file /etc/default/linux-restricted-modules-common and change the line 

DISABLED_MODULES=""

to 

DISABLED_MODULES="nv"

---

### Post by colalord on 2007-08-30
KUBUNTU

I just installed kubuntu onto my m9700 instead of ubuntu and it had the same problem as ubuntu.  nothing new here since they both will rely on the same driver.  however, thought i would mention that i installed the driver with the same set of instructions as provided above and it worked just fine.  i had to add the "nv" module to the disabled modules to keep it from reactivating on reboot as well.

---

### Post by nxain on 2007-09-13
While I really, really want to be able to run Ubuntu on my Alienware M9700, but I've pretty much given up for now.  I will try 7.10 when it's beta as there are changes which it seems like could make a difference.

On the other hand, I have gotten the Fedora live CD to work just fine with the M9700 (video-wise) and may install that on the laptop unless anyone has a good reason not too?

Thanks!

---

### Post by macker76 on 2007-09-19
[I] Re: Booting off Desktop CD fails . . .
I managed to get into the Live CD to install Ubuntu on my m9700 laptop

My Specs:
AMD Turion
Geforce Go 7800 GS in SLI
Single 100GB HDD
1920x1200 screen

These steps worked for me, let me know how you got on!

Before you start:

    * Ensure the sound dial on the laptop is up (i.e not on mute!).
    * Ensure that you have a valid internet connection via wired Ethernet connected to the laptop (as configuring the wireless with the Live CD is beyond the scope of this HOWTO)


Turn on laptop

Insert the Ubuntu 6.10 CD into your Alienware Aurora m9700 Laptop

Wait for CD to boot

When the menu appears, pick the first option on the menu, and wait for Ubuntu to load

You will see the Ubuntu logo and progress bar – as normal

Moments later is where the open source nv driver doesn’t detect the display properly and the screen goes blank – as you know else you wouldn’t be reading this &#61514;. Wait for the startup sound to fire so you know the system has finished loading.


Press Ctrl + Alt + F1 to get to the console

Download NVIDIA drivers:
For 32-bit:
Code:

#] wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

For 64-bit:
Code:

#] wget [ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run)

Type the following
Code:

#] sudo apt-get install build-essential
#] sudo /etc/init.d/gdm stop
#] sudo killall gdm
#] sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

Run though the NVIDIA wizard and it will compile and install a driver for your system. Ensure that it compiles and that it modifies the X config for you.

Last step:
Code:

#] sudo /etc/init.d/gdm restart

X should fire up and you’ll be looking at the Live CD desktop

Hope this helps[/I]

This works like a charm. When it hangs, its pretty obvious that something is wrong with the X server. Once it hangs, and you go into your virtual terminal (ctl-alt-f1), then sudo bash, cd var/log, and more Xorg.0.log, you can see there are issues, though not too specific. If your hardware varies a little for the M9700, read through /var/log. It doesnt seem to provide too much info though.

I couldnt ping nvidia and was worried it was the yukon LAN driver. However, after setting my WRT54GS running DD-WRT to DHCP for my DNS, I could finally ping out. If you follow the instructions as Tdub says, it should work for you.

I also had success by using an axtra DVI cabled attached into an HDTV set at a low resolution. You might be able to go throught he setup, and once installed, download the appropiate NVIDIA driver (im using the beta, in an SLI setup).

My specs:
Aurora m9700
2 x Nvidia 7900GS in SLI config
1 x 200GB 7800rpm HD
1x80GB 5400rpm HD
2GB RAM
RTL8185 wireless
Yukon LAN
1920x1200 HD resokution
triple boot (vista ultimate, ubuntu defalt (previous mandrake/mandriva user), backtrack|2

That was a pain in the ***, thanks to Tdub for the starting point.

---

### Post by macker76 on 2007-09-19
Oh yeah, I didnt use the 6.X.X version, I used the newest version 7.x.x. They both seem to work, as does the server version which was tested.

---

### Post by TDub on 2007-10-04
> **dyssident said:**
> the easiest way would be to load them from a usb drive. first type `ls /media`. plug the drive in and then do `ls /media` again. the new directory is your usb drive. if the new directory is named /media/disk, the commands youd use would be

```

sudo apt-get install build-essential
sudo /etc/init.d/gdm stop
sudo killall gdm
sudo sh /media/disk/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo /etc/init.d/gdm restart

```

Additionally, you will need to have all the .deb dependencies of the build-essential package on the USB drive as well, then instead do
```

sudo dpkg -i /media/disk/*.deb

```

instead of running apt-get

TDub

---

### Post by Wilco on 2007-10-16
I'm determined to get Ubuntu on this damn laptop! I'm downloading the 7.10 RC release now, so we'll have to see if any of the updates helped . . .

---

### Post by TDub on 2007-10-17
The Gutsy live CD has the same problem i'm afraid, i have tried it.

I have managed to find out what is going on! The NV driver obviously doesn't support SLI, and there lies your problem - it is getting confused with the 2 cards. The 2 cards (as least on my m9700) are on PCI address 6:0:0 and 7:0:0. the NV driver is initializing the card at 7:0:0, then X tries to use the card at 6:0:0.

I've figured a really simple fix to get into the Live CD, follow my guide on page 2 up until you get into the shell. Then open xorg.conf with your fav editor:
```

sudo vi /etc/X11/xorg.conf

```

scroll down to the "Device" section and change the line 
```
BusID       "PCI:6:0:0"
```
 to
```
BusID       "PCI:7:0:0"
```

then just restart X, and up pops the live cd
```

sudo killall gdm
sudo /etc/init.d/gdm restart

```

i don't know if BusIDs are different on other alienware laptops, if the above doesn't work, have a look in the Xorg.0.log file in /var/log for the IDs for your system

much simpler than downloading the binary drivers, thou still a pain

really hope this helps

TDub

---

### Post by colalord on 2007-10-23
I have recently installed World of Warcraft onto my m9700 and I was having OpenGL issues with the binary driver that was used in the description on page 2 of this thread.

Because of that I installed a different driver that does have support for glx.

```
sudo apt-get install nvidia-glx-new
```

This will cause Ubuntu and Kubuntu to be able to run on an Aurora m9700 with single or dual nVidia GeForce Go 7900 GS graphics card(s).  It will also providing optimized hardware acceleration of OpenGL applications via a direct-rendering X Server.

Laymen's terms, once you've installed this new driver you should be able to use 3D apps that use OpenGL a lot better then they would have before if they even did run while you had the driver described on page 2 installed.

Now WoW runs flawlessly on my m9700 under Kubuntu.  Hope this helps!  :)

[How to install World of Warcraft in Ubuntu/Kubuntu!]("http://ubuntuforums.org/showthread.php?t=579378&highlight=installing+world+of+warcraft")

---

### Post by scurry7 on 2007-11-13
I have had the same issue same sys specs...bla bla bla, tried everthing the post said but still got blank screen when I relaunched gdm, but I got it working when by using (what i think is) an updated driver from NVIDIA (I'm installing 7.10) here is the link: [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

so instead use: ```
wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run
```
then follow the rest of the walkthrough

Hope it helps!!!!
thanks for the original post, (now i get to use ubuntu!!!)

---

### Post by mango42 on 2007-12-06
TDub - thanks indeed for that piece of wizardry! Not that I enjoyed my first plunge into vi ;-)

Tip for vi - get a cheat sheet first and remember vi is always in command mode unless you <insert> into edit mode. :w saves :q quits :q! quits without saving. HTH.

colalord & scurry7 - can you guarantee these will work with alienware SLI boards? The reason I ask is that I just downloaded 68Mb of nVidia 163.xx WindowsXP drivers for my other partition only to discover that the install does not 'recognise the hardware', despite saying on their site that the 7900GS is covered - perhaps not the laptop version?

Hopefully one of these Linux drivers is more effective in Ubuntu?

Aah, but which one...?

TIA, mango

---

### Post by scurry7 on 2007-12-10
mango42,
yes it worked for my alienware with 7900GS dual graphics cards...
A different prob I'm having now though is after install grub throughs and err 2 at me (but after the vid card driver update i was able to load gdm to the live cd just fine.)
I'm still working on my install...(may be because of the raid config, still working on it...)

---

### Post by mango42 on 2007-12-11
Thanks for the confirmation but after jumping thru various hoops, the pkg ran then trashed the xorg.conf file - so no gdm now - stuck. Guess it's re-install time before this seemingly infinite rabbit hole does my head in ;-)

Can't help with the grub prob as I don't have RAID, sorry.
.

---

### Post by scurry7 on 2007-12-11
what do you mean > the pkg ran then trashed the xorg.conf file

---

### Post by pieisgood4589 on 2007-12-11
This exact same thing happened to me. What you have to do is bootup from the Zenwalk Linux install CD (Download the ISO and burn it to a disk) and do the automatic hard drive partition. Then, bootup from the Ubuntu LiveCD and it should work.

---

### Post by sgt_ferret on 2008-02-07
I get all the way to the point where I code sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run and it tells me that it cannot open the file. ?? Help?

---

### Post by scurry7 on 2008-02-07
you cannot open the file?
did you do sh NV.......  ?

this is what i do...

/etc/init.d/gdm stop
ps aux|grep gdm
(kill all gdm processes)
then run your driver ( #sh NVIDIA.... )

you have to have build-essentials installed, then it should work 
oh after do /etc/init.d/gdm start to start up gdm again...
let me know!

---

### Post by sgt_ferret on 2008-02-08
I'm pretty sure I have build essentials installed. I run the sudo apt-get install build-essential command line, and it says OK.  THis time, I followed your "sudo #sh NVIDIA...."  with the "#" and ran a list of stuffs on the screen.  However, when I restarted the GDM, it tells me that a display is already running in :0 and that I must choose to either look for a different slot or go with that one.  The screen looks severely messed up, and it still doesn't display video once I actually get GDM running.


PS: does it help to say that I'm dual booting, and that I have vista already installed? (But I have allotted 10 gigs on a separate NTFS partition to use for UBUNTU.)

---

### Post by scurry7 on 2008-02-08
did you run the nvidia driver?
my driver is NVIDIA-Linux-x86-100.14.19-pkg1.run (its an older one, but i dont have problems with it)
so i would type this at the command prompt: sh NVIDIA-Linux-x86-100.14.19-pkg1.run
that will run the driver install script...
make sure you have /etc/init.d/gdm stop  (gdm stopped (and end any other ps that may be hung (ps aux|grep gdm - then kill {the process number})))
it will install a few nvidia programs, like nvidia-bug-report.sh  nvidia-settings       
nvidia-installer      nvidia-xconfig

the install script will build the drivers for you then once you start gdm back up (/etc/init.d/gdm start) you should have it...

---

### Post by sgt_ferret on 2008-02-08
> **scurry7 said:**
> did you run the nvidia driver?
my driver is NVIDIA-Linux-x86-100.14.19-pkg1.run (its an older one, but i dont have problems with it)
so i would type this at the command prompt: sh NVIDIA-Linux-x86-100.14.19-pkg1.run
that will run the driver install script...
make sure you have /etc/init.d/gdm stop  (gdm stopped (and end any other ps that may be hung (ps aux|grep gdm - then kill {the process number})))
it will install a few nvidia programs, like nvidia-bug-report.sh  nvidia-settings       
nvidia-installer      nvidia-xconfig

the install script will build the drivers for you then once you start gdm back up (/etc/init.d/gdm start) you should have it...

that's the driver I'm trying to run.  do a wget on the driver, and then I "sudo apt-get install build-essential", and then stop GDM, then sudo killall gdm then I install the driver with the #sh NVIDIA, etc.  I then did sudo /etc/init.d/gdm restart and the same thing happened. Black screen with the load music.

---

### Post by scurry7 on 2008-02-10
so does the driver actually install? (you will have to go through a few steps and it will update your xorg.conf)
do you have the programs:"nvidia-bug-report.sh, nvidia-settings, nvidia-installer, nvidia-xconfig"?
if you do an "sudo nvidia-installer --update" then restart gdm what happens?

---

### Post by sgt_ferret on 2008-02-14
> **scurry7 said:**
> so does the driver actually install? (you will have to go through a few steps and it will update your xorg.conf)
do you have the programs:"nvidia-bug-report.sh, nvidia-settings, nvidia-installer, nvidia-xconfig"?
if you do an "sudo nvidia-installer --update" then restart gdm what happens?

I don't really know anything anymore. When I run a wget, it tells me "Failed: Name or service unknown"

I type: "wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19pkg1.run"

and then it runs some stuff, says the file name and then "failed: name or service unknown"

I'm getting pretty annoyed by all of this. I just want Ubuntu on my laptop.

---

### Post by scurry7 on 2008-02-14
your not even getting the file then (you miss typed it from what you typed in your post).....
you have to download the file (with wget) then you run the file.....
type this (exactly):

```

wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run

```

i checked it before i posted and it worked....
after wget you will see the file in your current directory  (type "ls")

---

### Post by sgt_ferret on 2008-02-14
Ok, since I've never done this, how can I run a  .run file without a GUI?  "sudo #sh NVIDIA-Linux-x86-100.14.19-pkg1.run"?

Also, will ubuntu use wireless, or do I have to be wired to a cat5?

---

### Post by scurry7 on 2008-02-14
type: "sudo sh {scriptFile}"   //replace scriptFile with your file name to run ( without {} )


for hardware support try searching google for ubuntu hardware support.....
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by sgt_ferret on 2008-02-14
> **scurry7 said:**
> your not even getting the file then (you miss typed it from what you typed in your post).....
you have to download the file (with wget) then you run the file.....
type this (exactly):

```

wget http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run

```

i checked it before i posted and it worked....
after wget you will see the file in your current directory  (type "ls")



Even when I run the code you've given me, I still get the "Failed: name or service not known" error.

---

### Post by scurry7 on 2008-02-18
are you connected to the internet?

---

### Post by gpilkay on 2008-02-18
I had the same problem but I got around it, sort of, by faking it.  I put VirtualBox on my laptop, then loaded 7.10 on a virtual machine I made i the partition I had originally intended for a real install.

So far, though, it works well as I've set up the fake machine to what Ubuntu wants, even though my real hardware isn't close.  Downside is I have to boot XP before Ubuntu.

---

### Post by kakudo on 2008-03-08
Thanks everyone for showing how to get into live cd and install Ubuntu.

My question is after the install what steps do you take before you restart so you can get back into Ubuntu? I have read through the 6 pages several times and didn't see what to do next. Thanks in advance.

---

### Post by scurry7 on 2008-03-10
I just had to reboot, then install the video drivers again...

---

### Post by nxain on 2008-03-12
I've used the 8.04 alpha 5 & 6 with the CD boot and both have worked fine for me (whereas the 7.10 never worked).  I've also used the wubi install and it's worked very well, although I had to edit 1 file to get the package manager to work right.  As well as 8.04 has been working, I think I'm going to setup my laptop to be dual boot once it's released.  My only remaining problem is getting the wireless network card to work.

nXain

---

### Post by Drexoll on 2008-04-08
I spent many hours trying to get the Nvidia Drivers to work. It wasn't until I had given up on them and went back to trying the restricted drivers that I noticed this problem. xserver saw the card pci:6:0:0 as the one to use but pci:7:0:0 was the primary. When I switched this in the xorg.conf file the restricted drivers kicked in and I was very happy. I didn't try it with the Nvidia drivers though so I don't know if that was the problem there or not, though neither were working before that.

Darcy

---

