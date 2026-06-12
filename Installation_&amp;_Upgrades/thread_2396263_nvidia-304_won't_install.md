---
title: "nvidia-304 won't install"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by enigma9o7 on 2018-07-13
Fresh install of lubuntu 18.04 on old desktop pc with nvidia 6100 graphics.   Default drivers are flickering and doing all sorts of weird stuff constantly.  Searched and found I need nvidia drivers version 304 last updated 2017.  Followed procedure - 

added repo: sudo add-apt-repository ppa:graphics-drivers/ppa
and updated: sudo apt update

I tried to: sudo apt install nvidia-304
but got the output pasted in box below.

I tried to install from synaptic, and it gives me a list of all my apps and says they have to be uninstalled.

I ran: ubuntu-drivers devices
and got:
== /sys/devices/pci0000:00/0000:00:05.0 ==
modalias : pci:v000010DEd00000242sv0000105Bsd00000CAFbc03sc00i00
vendor   : NVIDIA Corporation
model    : C51G [GeForce 6100]
driver   : nvidia-304 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

I ran: sudo ubuntu-drivers autoinstall
and got the same output as when I tried to apt install nvidia-304 myself.

```

 sudo apt install nvidia-304
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@Winfast:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:05.0 ==
modalias : pci:v000010DEd00000242sv0000105Bsd00000CAFbc03sc00i00
vendor   : NVIDIA Corporation
model    : C51G [GeForce 6100]
driver   : nvidia-304 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

user@Winfast:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by enigma9o7 on 2018-07-17
I ended up finding a solution for anyone who finds this thread later, based on: [https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)

I had already switched to another distro first (Bodhi) and same exact probem, what worked for me was:
(change your download directory and username as needed)

download 64-bit nvidia driver from: [URL="http://www.nvidia.com/download/driverResults.aspx/123709/en-us"]http://www.nvidia.com/download/drive...x/123709/en-us
[/URL]or 32bit: [https://www.nvidia.com/Download/driverResults.aspx/123708/en-us]("http://www.nvidia.com/download/driverResults.aspx/123709/en-us")
save patch from: [https://adufray.com/nvidia-304.137-bionic-18.04.patch](https://adufray.com/nvidia-304.137-bionic-18.04.patch)

sudo nano  /etc/modprobe.d/disable-nouveau.conf 

   COPY/PASTE:
blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist amd76_edac
options nouveau modeset=0
   SAVE/EXIT (CTRL-X)

sudo apt install gcc make build-essential gcc-multilib dkms mesa-utils
cd /home/bodhi/Downloads 
./NVIDIA-Linux-x86_64-304.137.run -x
cd ./NVIDIA-Linux-x86_64-304.137
patch -p1 < ~/Downloads/nvidia-304.137-bionic-18.04.patch
sudo update-initramfs -u
reboot

After reboot you'll be in some lower resolution video driver, goto terminal and run:

sudo service lightdm stop

Press CTRL+ALT+F2 

login: bodhi
cd /home/bodhi/Downloads/NVIDIA-Linux-x86_64-304.137
sudo ./nvidia-installer
reboot

edit: 
added link for 32-bit version
Note: The nvidia installer overwrites libvdpau with a version that doesnt work with mplayer/etc, so just reinstall the normal one:
sudo apt install --reinstall libvdpau1

---

### Post by rsteinmetz70112 on 2018-07-17
I had the same problem. Thank you for posting a solution. I find nouveau doesn't work for me consistantly.

---

### Post by raiden-c on 2018-07-22
I have performed  the steps correctly with a GeForce 6200 LE, and I have verified that driver = nvidia is  active, but now I can not play any movie due to codecs error:
[HTML]
Failed to load plugin '/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstlibav.so': libvdpau.so.1[/HTML]

Before, with noveau, I could reproduce everything, although with the CPU always at 100%.

How can I solve that or, if it is not possible, how can I go back to nouveau?

Thank you.

---

### Post by JKyleOKC on 2018-07-27
> **raiden-c said:**
> I have performed  the steps correctly with a GeForce 6200 LE, and I have verified that driver = nvidia is  active, but now I can not play any movie due to codecs error:
[HTML]
Failed to load plugin '/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstlibav.so': libvdpau.so.1[/HTML]

Before, with noveau, I could reproduce everything, although with the CPU always at 100%.

How can I solve that or, if it is not possible, how can I go back to nouveau?

Thank you.There's a major problem with Nvidia's driver in the most recent updates; it's on launchpad as bug #1737750. I found that on Xubuntu 16.04.5 I can use the system settings screen, additional drivers, to switch back to noveau, and that has worked around the bug for me. However I don't play movies on this system so it may not work for you.

---

### Post by rocketdave on 2018-08-18
Replying to[URL="https://ubuntuforums.org/member.php?u=2098306"][B][COLOR=#000000] enigma9o7
[/COLOR][/B][/URL] 	 
This worked beautifully with the patch.  Graphics performance hugely improved over Nouveua driver.  Am experiencing issue with CODECs in web pages but VLC works just fine on media.  I selected yes to all nvidia-installer prompts.  Config below:

**UPDATE: Video codecs work just fine if I use Chrome instead of Firefox.

Used: NVIDIA-Linux-x86_64-304.137

Running on an XFX motherboard (2 / MG-630I-7159)
Ubuntu 18.04.1 LTS (Kernel 4.15.0.33)
Intel Core 2 Quad CPU Q6600 @2.4GHz
NVIDIA GeForce version: 2.1.2 NVIDIA 304.137

sudo lshw -c display
  *-display                 
       description: VGA compatible controller
       product: C73 [GeForce 7150 / nForce 630i]
       vendor: NVIDIA Corporation
       physical id: 10
       bus info: pci@0000:00:10.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:23 memory:ed000000-edffffff memory:d0000000-dfffffff memory:ee000000-eeffffff memory:c0000-dffff

---

### Post by enigma9o7 on 2019-03-03
> **raiden-c said:**
> I have performed  the steps correctly with a GeForce 6200 LE, and I have verified that driver = nvidia is  active, but now I can not play any movie due to codecs error:
[HTML]
Failed to load plugin '/usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstlibav.so': libvdpau.so.1[/HTML]

Before, with noveau, I could reproduce everything, although with the CPU always at 100%.

How can I solve that or, if it is not possible, how can I go back to nouveau?

Thank you.

sudo apt install --reinstall libvdpau1

---

### Post by ivanjunior20 on 2019-04-26
[COLOR=#242729][FONT=Arial]It didn't work for me. After installing the NVidia driver and rebooting, my Ubuntu will not boot anymore. It gets stuck at "Starting Tool to automatically collect and submit kernel crash signatures...".[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
From all instructions above, only "sudo service lightdm stop" failed with error "lightdm.service not loaded". I thought it was OK to ignore this.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
My hardware configuration is: 
[/FONT][/COLOR]
[LIST]
[*][COLOR=#242729][FONT=Arial]HP Pavilion dv6000 / AMD64[/FONT][/COLOR]
[*][COLOR=#242729][FONT=Arial]00:12.0 VGA compatible controller: NVIDIA Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)[/FONT][/COLOR]
[/LIST]

---

### Post by nuevosean2 on 2019-06-10
> **enigma9o7 said:**
> I ended up finding a solution for anyone who finds this thread later, based on: [https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic](https://adufray.com/blog/2018/06/02/nvidia-304-127-on-bionic)

I had already switched to another distro first (Bodhi) and same exact probem, what worked for me was:
(change your download directory and username as needed)

download 64-bit nvidia driver from: [URL="http://www.nvidia.com/download/driverResults.aspx/123709/en-us"]http://www.nvidia.com/download/drive...x/123709/en-us
[/URL]or 32bit: [https://www.nvidia.com/Download/driverResults.aspx/123708/en-us]("http://www.nvidia.com/download/driverResults.aspx/123709/en-us")
save patch from: [https://adufray.com/nvidia-304.137-bionic-18.04.patch](https://adufray.com/nvidia-304.137-bionic-18.04.patch)

sudo nano  /etc/modprobe.d/disable-nouveau.conf 

   COPY/PASTE:
blacklist nouveau
blacklist vga16fb
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
blacklist amd76_edac
options nouveau modeset=0
   SAVE/EXIT (CTRL-X)

sudo apt install gcc make build-essential gcc-multilib dkms mesa-utils
cd /home/bodhi/Downloads 
./NVIDIA-Linux-x86_64-304.137.run -x
cd ./NVIDIA-Linux-x86_64-304.137
patch -p1 < ~/Downloads/nvidia-304.137-bionic-18.04.patch
sudo update-initramfs -u
reboot

After reboot you'll be in some lower resolution video driver, goto terminal and run:

sudo service lightdm stop

Press CTRL+ALT+F2 

login: bodhi
cd /home/bodhi/Downloads/NVIDIA-Linux-x86_64-304.137
sudo ./nvidia-installer
reboot

edit: 
added link for 32-bit version
Note: The nvidia installer overwrites libvdpau with a version that doesnt work with mplayer/etc, so just reinstall the normal one:
sudo apt install --reinstall libvdpau1

Haven't performed this on my gf's old laptop yet, but just an fyi, both of the links you shared were for the 64 bit version, so here's the proper link for the 32 bit version in case any onlookers have problems:

[https://www.nvidia.com/Download/driverResults.aspx/123708/en-us](https://www.nvidia.com/Download/driverResults.aspx/123708/en-us)

---

### Post by fljarvis on 2019-12-04
I've just gone through the installation on Bodhi-5.0.0-legacy, 32-bit.
Two small points:

-after the run file is downloaded, should run the
command     sudo chmod +x  NVIDIA*.run,
 to make the file executable.

-because Bodhi-5.0.0-legacy uses kernel 4.9,
 the patches which apply to kernels 4.14 and 4.15
 are not required.

Bodhi-5.0.0 is quite old, so I'll be looking forward to
applying this procedure to Bodhi-5.1-legacy when it
comes out.

Len E.

---

### Post by Frogs Hair on 2019-12-04
Thread Closed

---

