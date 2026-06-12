---
title: "Driver installation problems in MSI P6NGM MS-7366 Motherboard"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by steinair on 2008-03-27
On my MSI MS-7366 motherboard I have built-in:
 Nvidia GeForce MCP73 Video driver 
 Realtek ALC888 Audio driver 

I still couldn't find an appropriate video driver.
I have problems installing ALC888 audio driver :
" checking for initscr in -lncurses... no
  checking for initscr in -lcurses... no
  configure: error: this packages requires a curses library
  make: *** No targets specified and no makefile found.  Stop.
  make: *** No rule to make target `install'.  Stop.
  Remove Folder.....
  ./install: 101: alsaconf: not found "

I bet I'm not the only one in the world using this MSI board and using Ubunto7.10...

Anybody - help :confused:

---

### Post by Ub1476 on 2008-03-27
Post the output of 

```
lspci
```

It's easier to identify:)

---

### Post by delta_charlie on 2008-03-27
> **steinair said:**
> On my MSI MS-7366 motherboard I have built-in:
 Nvidia GeForce MCP73 Video driver 
 Realtek ALC888 Audio driver 

I still couldn't find an appropriate video driver.

Hi, I have this motherboard on order for a MYTHTV box I hope to build so I have been researching some and found there is a closed video driver available from: [http://www.nvidia.com](http://www.nvidia.com) in the downloads section for Linux. From what I have read so far this is the driver to use for MYTHTV so you might want to look into it. 

Try google something like "MYTHTV Nividia GeForce"

Got to run but I will be following this thread and will try to post more when I get a chance.

Later, DC

---

### Post by steinair on 2008-03-27
~/realtek-linux-audiopack-5.01$ lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation Unknown device 07e1 (rev a2)
01:06.0 Communication controller: Intel Corporation 536EP Data Fax Modem

---

### Post by steinair on 2008-03-27
:)
OK, Some good news... I just did a 
sudo update-pciids

And look what I got in the bottom of lspci...
 lspci
00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:06.0 Communication controller: Intel Corporation 536EP Data Fax Modem

---

### Post by sabhain on 2008-03-28
I have a similar board: MSI-P6NGM (I think it's a -D or something w/ DVI out).

In order to get this to work, I did have to use drivers from the vendors for both sound and video.

Use the latest driver from Nvidia's site .. but some comments:
[LIST=1]
[*]You do need to uninstall or disable the "proprietary driver" from ubuntu .. or Xorg will keep trying to use it.  It was a common problem here to do the install and then still have X11 fire in safe mode.
[*]when you have it up and running, you need to "sudo nvidia-settings" to run the configuration application.  Do NOT run the "Screens & Graphics" or "Screen Resolutions" apps that are within gnome / ubuntu.  You will only end up being frustrated.  Run the nvidia-settings as root and it will be able to correctly configure and write a new Xorg.conf file.
[*]Search here or at Nvidia's forums about the steps to make sure that xorg.conf is calling the right driver.  This will be a little confusing, but I found 2 or 3 clear posts that helped me solve it.
[/LIST]

The Realtek thing was a similar issue.  I think there are 2 paths here ... 
[LIST=1]
[*]You can try [http://ubuntuforums.org/showthread.php?t=658902&highlight=realtek+ALC888]("http://ubuntuforums.org/showthread.php?t=658902&highlight=realtek+ALC888")this thread for what appears to be an easier approach without recompiling drivers.
[*]Or, you can go to the Realtek site and download their driver package and compile from source.  I did this step, and found it to be pretty straightforward.  There are lots of resources on google for what you need to install to get that working.  I found a pretty helpful step by step either here or at google.
[/LIST]

I can tell you that I have been able to get both onboard peripherals working fine in Ubuntu with the P6NGM board.  Use search liberally here and you'll find the same.

Good luck.

---

### Post by delta_charlie on 2008-03-29
Check Envy out at: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Hope this helps, DC

---

### Post by Mntz on 2008-04-03
I have the same motherboard,
Installing the linux-backports-modules fixed my audio,
(install with synaptic and reboot)

---

