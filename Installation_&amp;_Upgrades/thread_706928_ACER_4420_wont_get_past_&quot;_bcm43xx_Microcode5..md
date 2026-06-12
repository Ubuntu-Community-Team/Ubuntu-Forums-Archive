---
title: "ACER 4420 wont get past &quot; bcm43xx_Microcode5.fw&quot; error"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by ftblstr2319 on 2008-02-24
I just picked up an acer 4420 from BB :( and this sucks

The wireless network card is BCM94311MCG

I havent found a solution.  

This is what I am experiencing.

Install doesnt work from the Live cd .  Stops on "bcm43xx_microcode5.fw" 

Install from the Alternate CD work fine.  On boot however it cannot load past "bcm43xx_microcode5.fw

I tried blacklisting 43xx in modprobe.d When I do that it hangs on the step right before loading the bcm43xx_microcode5.fw which is "running local boot scripts"

I also tried this solution "On an Acer Extensa 4420, ATI 1250 graphics card...

[INDENT]If you aim to dual boot (one windows vista (in my case), one gutsy) go to windows and download the appropriate driver for your graphics card and system

(i.e. go to [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html) . I used linux_x86_64 -> Integrated motherboard -> Radeon Xpress 1250.

Download this to your windows desktop.

Download and burn the alternative cd (64 bit gutsy)

Set bios to boot from cd first, install as usual. It is quite clear. See the psychocats website or any other installation guide. Don't give more than 2gb to swop - wastes space.

After the installation was successful, boot into safe-graphics mode (second option down)

root@yourcompname> cp /media/sdaX/Users/YourUserName/Deskop/ati_driver.r un .
[email]root@yourcompname>./ati_driver.run[/email]

Hopefully this installs ok. Then reboot, go into top option, login -> happy days."[/INDENT]


PLEASE HELP!  I know others are having this problem too.

---

### Post by ftblstr2319 on 2008-02-25
Bumped for the fact that I cannot stand vista, and I cannot return the laptop.

---

### Post by dstew on 2008-02-25
The issue you have is different that the one about the ATI graphics card. Your problem is that the Broadcom wireless card is not interacting properly with the Ubuntu system. It seems to be due to a firmware issue. The native Ubuntu driver cannot work with the firmware that comes with a Vista-installed computer.

You can do one of two things: Install firmware that works with Ubuntu, or use the Windows driver using the ndiswrapper utility. If you install new firmware, you might find that the card won't work with Vista. So, I would recommend using ndiswrapper.

> I tried blacklisting 43xx in modprobe.dSo you can get it to boot OK? If so, [this thread]("http://ubuntuforums.org/showthread.php?t=201902&highlight=Broadcom+4306+With+Ndiswrapper+54+Mbps") I think has the least confusing information about ndiswrapper. In that thread, you can skip steps 5 to 11 (compiling ndiswrapper from source) and just install ndiwrapper (and ndiswrapper-utils) using synaptic. Hopefully you can get a wired internet connection to do this.

---

### Post by ftblstr2319 on 2008-02-25
Sadly no I cannot get it to boot correctly into the OS once I blacklist bcm43xx.  

It just stops at basically the same spot except it does not give me the BCM43xx error.  I can press CNTL-ALT-DEL and give it a reboot.

The strange part is.  I will get the ubuntu loading screen then it will go to a command line loading/boot  info.   When it says "loading boot script" or something along that nature.  It flashes 4 times then it usually displays the 43xx error or just stalls if it's blacklisted.

Was that clear?

I've been using Ubuntu for well over a year and had my fair share of installation issues with the wireless network card.  (BCM4318) FW-cutter and NDIS wrapper and all that fun stuff.   But at least was able to boot into the OS to fiddle.

---

### Post by dstew on 2008-02-25
Make sure the filesystem is OK. From live CD, do** fsck -a /dev/sda1** (or whatever your Ubuntu partition is named).

---

### Post by ftblstr2319 on 2008-02-25
I can't boot into the live cd.  I have to boot into the alternate cd.  

I've installed the system and can get to "recovery mode" that leads to a command prompt root@myname?

Just reinstalled and still the same error...bcm43xx_microcode5.fw  not available or load failed.

---

### Post by dstew on 2008-02-26
> I tried blacklisting 43xx in modprobe.dHow did you do this exactly? I think if you correctly blacklist the bcm43xx module you might be able to boot.
[Here ]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/howto-bcm43xx-broadcom-drivers-462995/")is an example.

---

### Post by ftblstr2319 on 2008-02-27
Well I ran through these steps.  Until 

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils (IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

I cant open the OS so I rent into a cmd prompt in Recovery mode at boot screen

I typed sudo apt-get install ndiswrapper-utils and I think it gave me a message that ndis- common was newer and included that.  So i ran that command.  Which installed.  

On this step.

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

I am not sure where this file is located: ndiswrapper -i oem3.inf.  

There is also no folder in modprobe.d called Ndiswrapper :/

I miss linux

Also I  think my wireless came up as eht0 and my wired came up as eth1...could be mistaken though.  A reinstall only takes a few minutes

---

### Post by dstew on 2008-02-27
> 4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

I am not sure where this file is located: ndiswrapper -i oem3.inf.

There is also no folder in modprobe.d called Ndiswrapper :/First, did you download the Windows driver package? If so, where did you download it to? You have to locate the Windows driver folder, which is named bcm43xx, at least according to your instructions. It might be in your home folder. You need to change directories into that folder (the cd command means "change directory") and execute the ndiswrapper command from within that folder. The oem3.inf file contains the instructions that Windows usually uses to install its driver. Ndiswrapper interprets those instructions to install the Windows driver within a linux "wrapper". If that is successful, there should be an ndiswrapper file in the modprobe.d directory. Also, the file will be named ndiswrapper, and not Ndiswrapper. Linux names are CaSe sEnsITive.

---

### Post by ftblstr2319 on 2008-03-04
Alright this is SOLVED THANKS O'Meara

Here is what I did If you cannot get your live cd to work with An ACER 4420 with a x1250 graphics card

Install Ubuntu with the Alternate CD which will work
Plug in your network cable

** Pay attention to which network adapter takes on ETH0 OR ETH1
You want to remember your WIRED adapter.  Mine was ETH1

Once the install is finished take out the CD and boot into Recovery Mode

When you get the the command prompt Type this

nano /etc/hosts

replaced the second entry with (your computers IP address you want mine was) 192.168.1.116 computer-name.nc.rr.com computer-name

Mine was originally 176.0.0.0 laptop
Replaced it with
192.168.1.116 laptop.nc.rr.com laptop

Save and exit the file

go back to the command prompt
DONT TYPE IN THE INFO IN THE ()

ifconfig eth1 192.168.1.116 netmask 255.255.255.0 up(my computers network address and adapter for the wired ehternet) Press Enter

press enter 

route add -net 192.168.0.0 netmask 255.255.255.0 eth1 (Just used that network address.  You should too)

press enter

route add default gw 192.168.1.1 eth1

Press enter

ping [www.google.com](www.google.com)

You should get a ping and you are then ready to go with an internet connection.  DONT RESTART  

do this

root# apt-get update
root# apt-get install xorg-driver-fglrx
root# aticonfig --initial
root# aticonfig --overlay-type=Xv 

then restart the system with 

root# shutdown -r 

You should then download all the new drivers for you hardware and will be good to go..


[INDENT][INDENT]"So there are really two issues going on.  The bcm43xx_microcode5.fw is the driver for the wireless card which doesn't work.  There are two solutions-- using ndiswrapper and fwcutter.  But the bigger problem is the ATI graphics card isn't working.  You should deal with this first, that way you can actually use the computer!

I see you've tried to get your internet connection working from the command line, but you still haven't gotten a connection working?

if you think you have it working,
 
root# ping [www.google.com](www.google.com)

should give you something like

PING [www.l.google.com](www.l.google.com) (74.125.47.147) 56(84) bytes of data.
64 bytes from yw-in-f147.google.com (74.125.47.147): icmp_seq=1 ttl=245 time=21.1 ms
64 bytes from yw-in-f147.google.com (74.125.47.147): icmp_seq=2 ttl=245 time=20.5 ms
64 bytes from yw-in-f147.google.com (74.125.47.147): icmp_seq=3 ttl=245 time=21.9 ms
64 bytes from yw-in-f147.google.com (74.125.47.147): icmp_seq=4 ttl=245 time=22.6 ms


otherwise it will just sit there.   

If it's working that's great otherwise 

do this



and tell me the output as best you can.

If it works do like first post says

root# apt-get update
root# apt-get install xorg-driver-fglrx
root# aticonfig --initial
root# aticonfig --overlay-type=Xv 

then restart the system with 

root# shutdown -r 



Let me know how it goes.
[/INDENT][/INDENT]

---

