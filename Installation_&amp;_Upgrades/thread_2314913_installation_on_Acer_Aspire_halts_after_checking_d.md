---
title: "installation on Acer Aspire halts after checking drive."
date: 2016-02-24
forum: Installation &amp; Upgrades
---

### Post by famboog on 2016-02-24
Hi, I am a newbe. I have an Acer laptop 1350 and am trying to get Lubuntu 15.10 running.
After switching on I see The Lubuntu logo for a second and then the screen gets black with the text 
fsck from util-linux 2.26.2
/dev/sda1: clean, .....files .... blocks
and a blinking cursor (underscore)
Please can someone give me a hint how to continue?

---

### Post by yancek on 2016-02-24
Some information on the hardware (cpu, RAM, Graphics card) and the age of the laptop would be useful.  Since you make no mention of anything, we can only assume this laptop has a blank hard drive with nothing on it.

Have you done an md5 checksum on the downloaded iso file to verify its integrity?
Are you booting from a DVD or flash drive.  If a flash drive, what software did you use to make it bootable?

---

### Post by famboog on 2016-02-25
thx for the quick response
it concerns a laptop make Acer Series Aspire model 1350. The laptop was running Windows XP.
I wanted to change to Linux and tried a few (a.o Linux Mint). All crashed. I learnt it might be better to use LUBUNTU
The iso file used is lubuntu-15.10-alternate-i386.iso. I checked md5 sum with windows program

I managed to enter the terminal abd to mount a usb stick. I copied the lshw listing 

quote
buntu

    description: Computer

    width: 32 bits

    capabilities: smbios-2.3

  *-core

       description: Motherboard

       physical id: 0

     *-memory

          description: System memory

          physical id: 0

          size: 1019MiB

     *-cpu

          product: Mobile AMD Athlon(tm) XP 2400+

          vendor: Advanced Micro Devices [AMD]

          physical id: 1

          bus info: cpu@0

          version: 6.10.0

          size: 1592MHz

          capacity: 1791MHz

          width: 32 bits

          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow 3dnowprefetch vmmcall cpufreq

        *-cache:0

             description: L1 cache

             physical id: 0

             size: 128KiB

        *-cache:1

             description: L2 cache

             physical id: 1

             size: 512KiB

     *-pci

          description: Host bridge

          product: VT8378 [KM400/A] Chipset Host Bridge

          vendor: VIA Technologies, Inc.

          physical id: 100

          bus info: pci@0000:00:00.0

          version: 00

          width: 32 bits

          clock: 66MHz

          configuration: driver=agpgart-via latency=8

          resources: irq:0 memory:e0000000-efffffff

        *-pci

             description: PCI bridge

             product: VT8235 PCI Bridge

             vendor: VIA Technologies, Inc.

             physical id: 1

             bus info: pci@0000:00:01.0

             version: 00

             width: 32 bits

             clock: 66MHz

             capabilities: pci pm normal_decode bus_master cap_list

             resources: memory:d1000000-d1ffffff memory:f0000000-f3ffffff

           *-display UNCLAIMED

                description: VGA compatible controller

                product: KM400/KN400/P4M800 [S3 UniChrome]

                vendor: VIA Technologies, Inc.

                physical id: 0

                bus info: pci@0000:01:00.0

                version: 01

                width: 32 bits

                clock: 66MHz

                capabilities: pm agp agp-2.0 vga_controller bus_master cap_list

                configuration: latency=64 mingnt=2

                resources: memory:f0000000-f3ffffff memory:d1000000-d1ffffff


unquote

Hope this helps in solving the issue. Awaiting your valued response

---

### Post by famboog on 2016-03-01
please advise

---

### Post by mörgæs on 2016-03-02
VIA graphics can be difficult to work with.
Have you tried the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by famboog on 2016-03-02
yes, I used lubuntu-15.10-alternate-i386.iso. the 'standard' did not work at  all.
I do not understand. I see the lubunti logo for a second. this should indicate the vide card is running???? Then fsck runs (on a black background). And no desktop returns.  Would it be a suggestion to blocj fsck? I don't know how.

---

### Post by X-RED_Tech on 2016-03-02
It's a waste of time trying to install anything else than XP on that machine. And XP is out of support so... Take it to the nearest recycling plant.

---

### Post by mörgæs on 2016-03-03
If the alternate ISO gives problems we take the next in line. Have you tried the minimal ISO?

To begin with it's about installing a text-only system.

---

### Post by famboog on 2016-03-04
no I did not; I will try a minimal ISO. Any suggestions for distro?

---

### Post by mörgæs on 2016-03-04
No. As I mentioned it's about getting a command line system for now. 

Which of the buntus comes later.

---

### Post by famboog on 2016-03-05
I read [https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/) carefully and installed the mini.iso referred to. checked md5 sum. used option "Command-line install". 
Everything went smooth. After restart I get a 'black screen'. 
Pressing alt-F1 gives: 

Ubuntu 15.10 ubuntu tty1
Ubuntu login: and a blinking cursor

Awaiting your valued instructions

---

### Post by mörgæs on 2016-03-05
At the login prompt you log in :-) 

After that please click the link in my signature and search on the page for 'minimal'.

---

### Post by famboog on 2016-03-05
I followed "old hardware" link.
sudo apt-get install lubuntu-desktop --no-install-recommends
no problems reported 

sudo reboot now
black screen with on top 
fsck from util-linux 2.26.2
/dev/sda1: clean, ../.. files, ../.. blocks
and a blinking cursor

what is next?

---

### Post by mörgæs on 2016-03-07
> **famboog said:**
> 
what is next?

You should be able to find more than enough of ideas in Old Hardware.

---

### Post by famboog on 2016-03-07
oke, thx for your support.

---

### Post by mörgæs on 2016-03-07
Good, please let us know what works. It will help other people with a similar problem.

---

### Post by famboog on 2016-03-09
> **mörgæs said:**
> Good, please let us know what works. It will help other people with a similar problem.

I have followed the following procedures that led to a reasonable working desktop.

from [https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)

 
 
 1. Download [Ubuntu Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD") (mini.iso) for your PC architecture. The file size is only less than 30MB.

 2. You won&#8217;t be able to create a USB startup disk with this iso file, so the only way is to [burn it]("https://help.ubuntu.com/community/BurningIsoHowto") into a bootable CD.

 3. Make sure your PC/laptop is connected to a [LAN network]("http://rover.ebay.com/rover/1/711-53200-19255-0/1?type=2&campid=CAMPAIGNID&toolid=11000&customid=CUSTOMID&ext=151287541751&item=151287541751&ipn=psmain&icep_vectorid=229466&icep_ff3=2&icep_item=151287541751"). Insert the CD into your CD-rom and boot up your computer from the ROM. This is what you will see. Select &#8220;Install&#8221;.

Follow usual settings untill you are asked to select packages

 select &#8220;manual package selection&#8221;

The last thing it will install is the GRUB loader  
Finally. the installation is completed. Remove the CD from the CD-rom and select &#8220;Continue&#8221; to restart the computer.  

 Restart the computer. Press &#8220;Alt + F1&#8221; when the grub loader appears.

 Now follow [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)
sudo apt-get install lubuntu-desktop (ubuntu crashed!)

 sudo reboot now

 
 
 Still a black screen.  

 
 
 I decided to install the OpenChrome driver

 following [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

sudo apt-get install build-essential
 sudo apt-get install autoconf automake libtool git xutils xutils-dev

Note I deleted the version number from the 'automake' as the system could not vind version 1.9

sudo apt-get install pkg-config xserver-xorg-dev libxext-dev libxv-dev libxvmc-dev

Compile and install the 2D driver
git clone git://anongit.freedesktop.org/openchrome/xf86-video-openchrome
cd xf86-video-openchrome
./autogen.sh --prefix=/usr --enable-debug --enable-xv-debug
make

sudo make install

 Test the driver restarting your computer.

it doesn't work
 
Log into textual console

 
sudoedit /etc/X11/xorg

    Section "Device"

                   Identifier      "Configured Video Device"

                   Driver          "vesa"

    EndSection

 
And it &#8220;worked  :o 
I still hae to deal with error messages

 please be so kind to comment on how to improve my path; I also want to have a better understanding of linux!

---

### Post by mörgæs on 2016-03-09
I don't think there is much to improve. Vesa drivers is also what I use for old graphics processors if everything else fails. They are solid and well tested but slower and sometimes give a limited resolution.

The chances of getting a real bug fix for such old hardware is small so I think this is as good as it gets.

While keeping a backup of the xorg.conf you created you could experiment with even lighter set-ups than the default Lubuntu.

I hope you get some more working hours out of the old Acer. If you are satisfied please mark the thread 'solved'.

---

