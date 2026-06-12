---
title: "Your Firefox snap installation needs some work"
date: 2023-11-13
forum: Installation &amp; Upgrades
---

### Post by rossignol on 2023-11-13
Upgraded Ubuntu a couple months ago, and the Firefox installation ever since has sucked royally. It keeps freezing,runs slow,and quite often turns itself off - and sometimes actually turns the computer off.

Where the heck are the correct instruction to get Firefox running correctly again?

---

### Post by ian-weisser on 2023-11-13
How unusual. Most folks encounter no such problems.

What leads you to believe the Firefox is (somehow) turning off your hardware? What troubleshooting did you conduct to rule out other possible causes?

Freezing and running slow are more commonly symptoms of lack of RAM...or a faulty power supply. What troubleshooting did you conduct that pointed to Firefox?

---

### Post by rossignol on 2023-11-13
The only problem I have is with Firefox - it constantly asks me to either allow it to quit or wait. Most of the time it decides to quit on its own, and every once in a while it quits and them shuts the computer off. Sorry, but I can't describe it any better than that - I know not much at all about computers. I'll check on RAM tomorrow and see where it is.

---

### Post by ian-weisser on 2023-11-13
It is likely that you are seeing merely symptoms that need to be investigated to find the actual cause(s).

Are you open to the possibility that you might have more than one underlying cause?

To "check on RAM", use the "free -h" command.
Run it once after startup, but before you have started any applications. Record the entire output. It's text; you can simply copy/paste it. 
Run it again while Firefox is slow. Record the entire output.
Show us both complete sets of output.

---

### Post by TenPlus1 on 2023-11-14
You could always try to install the .deb Firefox and see if that helps any - [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by SeijiSensei on 2023-11-14
I switched to Debian 12 so I can avoid snaps and other Canonical cruft.

---

### Post by rossignol on 2023-11-14
At the moment, the free space on the hard drive is about 17% (shows as 295M available) . Free RAM is 1.1Gi.

---

### Post by ajgreeny on 2023-11-14
You haven't mentioned your hardware specs at all which might be why you're seeing this problem so tell us in detail what you are using.

---

### Post by rossignol on 2023-11-14
The best I can tell you at the moment is that the computer is a Dell Precision Workstation T5500.  I've tried everything I can find for terminal commands to see what the CPU, etc, are, but zero luck so far.

---

### Post by Rubi1200 on 2023-11-14
Open a terminal and run this command:

```
inxi -Fz
```

Copy the output and then reply using Go Advanced >> paste the output >> highlight the text and click on the # icon to wrap with code tags.

The output will give us information on the specifications.

Thanks.

---

### Post by iamjiwjr on 2023-11-15
I have a Dell Precision desktop 3650. It runs all chrome-based browsers like a slug. The longer I run Firefox the slower it gets. Sometimes it pops a window right up, but usually it's wait-wait-wait before the window opens.

---

### Post by rossignol on 2023-11-15
Here's what I got:

ichard@richard-Precision-WorkStation-T5500:~$ inxi -Fz
System:
  Kernel: 5.15.0-88-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Dell product: Precision WorkStation T5500 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 0CRH6C v: A02 serial: <superuser required> BIOS: Dell
    v: A18 date: 10/15/2018
CPU:
  Info: 6-core model: Intel Xeon E5645 bits: 64 type: MCP cache: L2: 1.5 MiB
  Speed (MHz): avg: 2352 min/max: N/A cores: 1: 2394 2: 2394 3: 2311
    4: 2394 5: 2226 6: 2394
Graphics:
  Device-1: NVIDIA GF108GL [Quadro 600] driver: nouveau v: kernel
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: modesetting unloaded: fbdev,vesa
    gpu: nouveau resolution: 1920x1080~60Hz
  OpenGL: renderer: NVC1 v: 4.3 Mesa 23.0.4-0ubuntu1~22.04.1
Audio:
  Device-1: Intel 82801JI HD Audio driver: snd_hda_intel
  Device-2: NVIDIA GF108 High Definition Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-88-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Broadcom NetXtreme BCM5761 Gigabit Ethernet PCIe driver: tg3
  IF: enp6s0 state: up speed: 100 Mbps duplex: full mac: <filter>
RAID:
  Hardware-1: Intel SATA Controller [RAID mode] driver: ahci
Drives:
  Local Storage: total: 372.61 GiB used: 58.99 GiB (15.8%)
  ID-1: /dev/sda vendor: Seagate model: ST3400620AS size: 372.61 GiB
Partition:
  ID-1: / size: 365.7 GiB used: 58.99 GiB (16.1%) fs: ext4 dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 864 MiB (42.2%) file: /swapfile
Sensors:
  System Temperatures: cpu: 29.0 C mobo: 20.0 C gpu: nouveau temp: 46.0 C
  Fan Speeds (RPM): cpu: 827 mobo: 1116 gpu: nouveau fan: 3120
Info:
  Processes: 251 Uptime: 1h 26m Memory: 2.88 GiB used: 1.4 GiB (48.7%)
  Shell: Bash inxi: 3.3.13
richard@richard-Precision-WorkStation-T5500:~$

---

### Post by ajgreeny on 2023-11-15
You have only the open source nouveau driver for your Nvidia graphics card which will not be very successful.
Most, if not all, and I've never used Nvidia graphics so may be wrong, need to use a proprietary driver so from Activities in the corner of your screen, top left i think, look for Additional Drivers to see if anything is offered.

By using the Gnome version of Ubuntu you have also chosen the most resource hungry OS of the family,  but let's see if the better driver overcomes these problems for you.

---

### Post by rossignol on 2023-11-15
Thanks. I've changed the driver to a Nividia driver, so now I'll see what it does over the next couple days.

How would I have received the Gnome version of Ubuntu when I did the upgrade as Ubuntu laid out?

---

### Post by rossignol on 2023-11-15
Nope -it changed nothing,unfortunately.

All I want Ubuntu for is emails and internet brousing, aa well as better resistance to getting hacked - I rarely use anything else other than Rythmbox, so I don't care one bit about all of the fancier features that more serious users want - my design computer is isolated from the net and stays isolated for security purposes.

---

### Post by ian-weisser on 2023-11-15
> **rossignol said:**
> Memory: 2.88 GiB used: 1.4 GiB (48.7%)

Your system does not appear to have the minimum suggested RAM installed (4GB).
Encountering slow Firefox as you exhaust RAM and begin swapping is expected. Web browsers are notorious RAM consumers.

Nothing I have seen so far suggests a problem with Firefox or with snaps.

---

### Post by rossignol on 2023-11-15
What line in that printout says what the RAM is? 

If that is true ( too little RAM), that is an easy problem to fix.

---

### Post by aljames2 on 2023-11-15
A good idea is to review system requirements before installing an OS as well as when you are considering upgrade versions.
[https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Desktop_Edition)

Good new, there are some lighter versions you could try on your hardware that likely would give you better performance. Have good backups of your data first.

---

### Post by ajgreeny on 2023-11-16
Almost the final line of your inxi output shows the memory usage; as mentioned above, that is simply insufficient ram for the gnome DE used by Ubuntu.
Another DE version, eg Xubuntu may be much easier on your hardware, but if you really want the standard Ubuntu add more ram!

---

### Post by rossignol on 2023-11-16
Well I'll be damned! This thing has 3 2 gig sticks, so it looks like one of them doesn't work, and was never a problem until the upgrade. My friend who gave me the computer is bringing over 24g from his server that he doesn't need, so that should take care of the problem!

---

### Post by ian-weisser on 2023-11-16
Something similar happened to one of my machines a couple years ago. Such things happen.

---

### Post by TheFu on 2023-11-17
> **SeijiSensei said:**
> I switched to Debian 12 so I can avoid snaps and other Canonical cruft.

I switched to Linux Mint for the same reason.

> Memory: 2.88 GiB
That's the problem.  Not enough RAM in the system.  These days, 8GB is a minimal amount of RAM if you plan to use bloated software.  Any less and you need to go with a stripped down DE and expect limitations on how many windows/tabs/programs can run concurrently.  BTW, I'm guessing the GPU is on-board and stealing 1.2G of RAM from the system RAM. Ouch.

> This thing has 3 2 gig sticks, so it looks like one of them doesn't work, and was never a problem until the upgrade.
3 sticks? That's odd.  Best to go with even numbers to get DDR performance.  Most desktop motherboards only have 4 RAM slots. Be certain to use matched RAM sets.  I had a problem where I had 2 separate, but matched pairs of RAM.  The RAM was all the same model number and speed.   They wouldn't run at the designed speed, however. I ended up reducing from the 3200Mhz spec speed down to 2666Mhz to get the system to be stable.  Eventually, RAM got cheap enough that I was able to buy new RAM cheap to replace the 4 sticks down to 2 sticks of the same total amount.  Things have been stable over a year now AND fast.

Anyway, my point is that not all RAM is matched and not all RAM will work in all systems. Pulling RAM randomly from a stack and hoping they work together was easier with DDR2 and DDR3, but not with DDR4 and newer.

---

### Post by rossignol on 2023-11-17
This machine has 3 slots with white locking tabs, and 3 with black tabs, so I would assume that Dell wanted you to use matched sets. The new sticks are 8g each of DDR3, self-correcting ( they came our of a server that had 48g of RAM), so I doubt I'll ever have another issue! :)

---

### Post by TheFu on 2023-11-17
Most desktop motherboards do not use ECC RAM.  Too bad.  Wish I had some.  Xeon motherboards might - nice.

6-RAM slots - nice.  Just be certain to use matched sticks in each pair and using all of the slots may provide 1% bump in RAM performance, but if you don't, 2x8GB should make a huge difference.

Hopefully, putting the inxi output inside 'code-tags' will help with the better formatting:
```
$ inxi -Fz
System:
Kernel: 5.15.0-88-generic x86_64 bits: 64 Desktop: GNOME 42.9
Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
Type: Desktop System: Dell product: Precision WorkStation T5500 v: N/A
serial: <superuser required>
Mobo: Dell model: 0CRH6C v: A02 serial: <superuser required> BIOS: Dell
v: A18 date: 10/15/2018
CPU:
Info: 6-core model: Intel Xeon E5645 bits: 64 type: MCP cache: L2: 1.5 MiB
Speed (MHz): avg: 2352 min/max: N/A cores: 1: 2394 2: 2394 3: 2311
4: 2394 5: 2226 6: 2394
Graphics:
Device-1: NVIDIA GF108GL [Quadro 600] driver: nouveau v: kernel
Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
compositor: gnome-shell driver: X: loaded: modesetting unloaded: fbdev,vesa
gpu: nouveau resolution: 1920x1080~60Hz
OpenGL: renderer: NVC1 v: 4.3 Mesa 23.0.4-0ubuntu1~22.04.1
Audio:
Device-1: Intel 82801JI HD Audio driver: snd_hda_intel
Device-2: NVIDIA GF108 High Definition Audio driver: snd_hda_intel
Sound Server-1: ALSA v: k5.15.0-88-generic running: yes
Sound Server-2: PulseAudio v: 15.99.1 running: yes
Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
Device-1: Broadcom NetXtreme BCM5761 Gigabit Ethernet PCIe driver: tg3
IF: enp6s0 state: up speed: 100 Mbps duplex: full mac: <filter>
RAID:
Hardware-1: Intel SATA Controller [RAID mode] driver: ahci
Drives:
Local Storage: total: 372.61 GiB used: 58.99 GiB (15.8%)
ID-1: /dev/sda vendor: Seagate model: ST3400620AS size: 372.61 GiB
Partition:
ID-1: / size: 365.7 GiB used: 58.99 GiB (16.1%) fs: ext4 dev: /dev/sda1
Swap:
ID-1: swap-1 type: file size: 2 GiB used: 864 MiB (42.2%) file: /swapfile
Sensors:
System Temperatures: cpu: 29.0 C mobo: 20.0 C gpu: nouveau temp: 46.0 C
Fan Speeds (RPM): cpu: 827 mobo: 1116 gpu: nouveau fan: 3120
Info:
Processes: 251 Uptime: 1h 26m Memory: 2.88 GiB used: 1.4 GiB (48.7%)
Shell: Bash inxi: 3.3.13

```

5000 passmarks should be fine for light use. [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5645+%40+2.40GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Xeon+E5645+%40+2.40GHz)  I'd use a lighter DE than Gnome on that CPU.

That's an old Nvidia GPU.  I had a workstation like that a few years ago. It was designed for CAD, not typical stuff desktop users do.  Also, nvidia is known to have problems with Wayland, so you probably want to switch from Wayland to Xorg for your display server.  When 22.04 support ends in either 2025 (most light DE flavors get 3 yrs of support) or 2027 if you stick with Gnome), probably plan to either upgrade the entire computer or at least swap in a cheap GPU. Nvidia has a habit of dropping support for older GPUs and when/if Linux drops Xorg and only supports Wayland, you (and I) may not have any choice.

BCM5761 using a 100base-tx NIC.  Doesn't matter if you don't use it.  Not great networking can slow a machine down, since it is surprising how many things perform DNS queries. If each of those has to time-out, I'd suggest optimizing the nsswitch.conf file for off-line use if you see issues at all.

And lastly, for a desktop, swap becomes important on RAM limited systems.  Less important if you add more RAM.
a) I'm not a fan of swapfiles. I much prefer swap partitions.  Swap partitions have been around since the beginning.  Swapfiles are relatively new.  Hopefully, the capabilities that swap partitions support have finally been achieved in a swap file.  I don't know.  I always delete the swap file and create a swap partition.
b) For a desktop, the swap should be 4.1GB about 95% of the time.  It is more important for low-memory systems.  The point of swap on a desktop is to provide feedback to users that they are running with low-RAM, so Putting the swap on slow HDDs, not an SSD is also something I recommend. Otherwise, the users may not "feel" the swapping and know to close some huge application like their browser or fat-email client or itunes or libreoffice.  4GB should be enough to hold the modern browser.  On systems with lots of RAM that will never be fully used, having some swap puts the kernel into a different mode than zero swap, so having 500MB would be good enough.  I wouldn't do that for a desktop with 32GB of RAM or less. You can check swap and RAM use with this command:
```
free -hm 
```

---

