---
title: "Difficult install"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by Byb on 2013-02-17
Hi forum
Is it possible to repair an install that had issues?
I explain: the only way I nearly reached was with PC (Intel x86) alternate install CD (half-graphic mode). Previous trials with generic ended in the very beginning with kernel panic or file copy errors although I checked several CDs and isos.
In the nearly good install there was an error loop in the step just before GRUB install, i.e. the one where softwares are installed: I skipped (saying IIRC "don't update, then jumping to Grub install - I sayed don't update because I was puzzled seeing quetzal things passing when I'm 100% sure I use a 12.04 CD)
My brand new MoBo and video are ASRock k7s41gx2 and Twintek nVidia6200A agp8x fanless(NV44A), and I have 2 SATA vt6421 pci boards for 2 samsung 320GB drives and 2 CD drives, plus a maxtor PATA 160GB (for boot and OS) and a floppy and a Iomega ZIP both three  attached to the MoBo.

On boot I get GDM screen OK, but it turns in a nice blue Windows color when I login.

Switching to tty1 I can see sources.list with a single line```
deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release -i386 (20130214)]/ precise main restricted
``` when a file sources.list.apt-setup is in the same directory.
EDIT: in this file there seem to be the usual things there are in the usual sources.list

When login in tty1 I get
```
0 packages can be updated
0 updates are security updates
```Please what went wrong? Is there a way to have it work?
dpgk --get-selections shows 1279 packages flaged "install".
Also the nvidia driver is not installed

I wanted to read the sticky post but saw it is 114 pages

Thanks for help



PS: [EDIT]:
Following [http://doc.ubuntu-fr.org/nvidia#probleme_apres_installation_de_precise_pangolin_1204](http://doc.ubuntu-fr.org/nvidia#probleme_apres_installation_de_precise_pangolin_1204), I tried:
```
apt-get install nvidia-current-updates
Reading packages lists... Done
Building dependancies tree
Reading status informations... Done
E: Impossible to find package nvidia-current-updates

```

---

### Post by dino99 on 2013-02-17
better to do a clean reinstall

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: use a usb stick if possible, otherwise always burn a cd/dvd at the slowest possible speed (better tool : k3b)

note2: sometimes boot option can help
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by sudodus on 2013-02-17
> **dino99 said:**
> better to do a clean reinstall

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: use a usb stick if possible, otherwise always burn a cd/dvd at the slowest possible speed (better tool : k3b)

note2: sometimes boot option can help
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
+1 for boot options.

Try with different boot option live (booted from your Ubuntu install drive) if you still have such a CD. When you have found one option, that helps, enter it in the correct place in your installed system. That might be enough to get passed the blue screen of death. See the link above about boot options!

Good luck :-)

---

### Post by Byb on 2013-02-17
Hi guys
reinstall is no more an option as I already did it about a tenth of times along with burning/checking isos AND CDs as I said, as well with md5checker AND CD's embeded checking tool AND brasero AND infrarecorder. I'm just currently giving a last chance to brasero to find the mysterious option to burn slowly.
Bootoptions are not an option too, because too huge number of them makes a huge^huge number of combination to try before it ***may*** work, and in the end the hardware is dead before I accidentaly read somewhere either it could have never work for a known reason or there is now a patch available. Believe me, this is not a joke nor is bad mind, this is my own experience from 5 years trying to use ubuntu and some minutes ago I found in the 12.04.2 release notes that my old (RIP) Amilo 7405 would have never work.

My bigger wander is in choosing the good iso, because I just discovered that beside the 2 available options that seemed OK to me, there are 2 others, which make a total of 6 possibilities before ever beginning to dream to use the computer for something else than trying to have it working:
Please, drive me through the options:
**1rst** I discover there are 3 Pangolin releases: 12.04 | 12.04.1 | 12.04.2
As I want to stick with a LTS, which one should I choose? I tried to read the things about the StackEnablement thing, but understood nothing at all, but maybe why I saw quetzal things passing.
Please could you try to explain simple way (if possible) instead of links that required huge pre-knowledge?
Thank you

**2nd**: after this choice is done clearly in my mind, I can try with serenity either x86 or alternate x86 (although apparently not needed as I have 2GB ram and don't want RAID)

PS:In the lap time, brasero ended burning without showing the low speed option stated somewhere in the link you gave to me.
PS2: I don't run in a BSOD: the system boots, but I still wander if I choose the apropriate iso

Thank you again

---

### Post by sudodus on 2013-02-17
> **Byb said:**
> I discover there are 3 Pangolin releases: 12.04 | 12.04.1 | 12.04.2
As I want to stick with a LTS, which one should I choose?

Choose the last one 12.04.2, it is the result of almost one year of debugging and tweaking. It is only a few days old, and will need few updates to be complete up to date (today).

By the way, you could at least try the ***nomodeset*** boot option. It is the most likely to be needed and will not waste much time for you.

---

### Post by steeldriver on 2013-02-17
Your original post isn't very clear on exactly what part of the install went wrong

However I do remember having problems with the last couple of 12.04 alternate installs that I tried - iirc there are a few bug reports about it, there was a situation in which it couldn't find the software sources - there were a couple of workarounds involving dropping to a root shell from the installer menu and remounting the CD

[In fact iirc the last time, I used a unetbootin and actually dropped the whole iso file onto the USB as well, then pointed the installer at that at the appropriate point in the process]

---

### Post by Byb on 2013-02-17
> **sudodus said:**
> Choose the last one 12.04.2, ...
Fine, that's what I have :)
> try the ***nomodeset*** boot optionPopup: Failed to load session "ubuntu" (with single "Log out" button) :(
Even I don't care with SLI, can I use this I found there?: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) 
and after do I have to do the nomodeset thing? 
```
**Notes about nvidia cards and SLI  **
 The "nomodeset" kernel bootline switch usually works for most nVidia cards, but now all.

Especially for nvidia cards, I usually just into a text mode by going to   a text console via grub edit ('e") append " text " to the end of the   kernel boot line and boot{"ctrl-x') and after a login type  
      Code:
     sudo apt-get update sudo nvidia-installer --uninstall sudo apt-get remove nvidia-* sudo apt-get install linux-headers-'uname -r' sudo apt-get install nvidia-current   sudo nvidia-xconfig sudo apt-get update 
(Note- This example assumes that you have a GeoForce 6xxx or better card) then try to start the GUI via      Code:
     sudo service gdm  start 

```

---

### Post by Byb on 2013-02-17
no fun
Hand typed in, and fr->en translation, please pardon typos:
sudo prefixed all commands
> apt-get update
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise InRelease
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/main TrnaslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/restricted TranslationIndex
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/main Translation-fr_FR
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/main Translation-fr
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/restricted Translation-fr_FR
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/restricted Translation-fr
Ign cdrom://Ubuntu 12.04.2 LTS _Precise Pangolin_ Release i386 (20130214) precise/restricted Translation-en
Reading packages lists... Done
nvidia-installer --uninstall
sudo: nvidia-installer --uninstall: command not found
apt-get remove nvidia-*
Reading packages lists... Done
Building dependencies tree
Reading status informations... Done
Note : selection of nvidia-180-modaliases for regexp « nvidia-* »
Note : selection of nvidia-current-modaliases for regexp « nvidia-* »
Note : selection of nvidia-185-modaliases for regexp « nvidia-* »
Note : selection of nvidia-common for regexp « nvidia-* »
Note : selection of libgl1-nvidia-alternatives for regexp « nvidia-* »
Following packages will be REMOVED
 nvidia-common
0 updates, 0 newly installed, 1 to remove and 0 not updated
After this operation, 154 kB of disk space will be freed.
Do you wish to continue [Y/n] ? Y
(Reading database... 135967 files and folders already installed.)
Removing nvidia-common...
Doing postponed actions (« triggers » for « ureadahead »
Apt-get install linux-headers-'uname -r'
Reading packages lists... Done
Building dependencies tree
Reading status informations... Done
E: Unable to find package linux-headers-uname -r (I will try later with backquotes)
Apt-get install nvidia-current
Reading packages lists... Done
Building dependencies tree
Reading status informations... Done
E: Unable to find package nvidia-current
nvidia-xconfig
sudo: nvidia-xconfig: command not found

later

Apt-get install linux-headers-`uname -r`
Reading packages lists... Done
Building dependencies tree
Reading status informations... Done
linux-headers-3.5.0-23-generic is already the most recent release available.
linux-headers-3.5.0-23-generic changed to « installed manually ».
0 updates, 0 newly installed, 0 to remove and 0 not updated


---

### Post by Byb on 2013-02-17
I will know try something you did not care from my first post (the source.list stuff)
something like cat /etc/sources.list.apt-setup >> /etc/sources.list
and retry the install of nvidia driver
Just hope the PC won't end in XP

---

### Post by sudodus on 2013-02-17
I think we are getting to the point, where it is probably better to do a fresh install. When you do that, please do not install any proprietary driver! Have a thorough try with the automatic selection of free drivers!

Also help us give relevant advice by posting some important specs of your computer:

- cpu ?

- ram ?

- graphics chip/card is Twintek nVidia6200A agp8x fanless(NV44A) is this the right specs:
[[COLOR="Red"]http://www.gpureview.com/geforce-6200a-card-198.html[/COLOR]]("http://www.gpureview.com/geforce-6200a-card-198.html")

- wifi chip/card (if any)?

You may have posted it, but I cannot find it easily.

We should also discuss 12.04 LTS versus 12.10 and discuss the various flavours of Ubuntu, not only [vanilla] Ubuntu, but also light-weight Xubuntu and ultra light-weight Lubuntu.

But first you need to get it running live (testing with boot options) before starting to install.

---

### Post by Byb on 2013-02-17
Thanks menz for still being here

video [http://www.twintech3d.com/en/cartes_graphiques.asp?categorie=47](http://www.twintech3d.com/en/cartes_graphiques.asp?categorie=47) but mine has 512MB memory
According to cat /proc/cpuinfo and lspci

processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 8
model name    : AMD Athlon(tm) XP 2000+
stepping    : 0
cpu MHz        : 1678.973
cache size    : 256 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips    : 3357.94
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE/SATA Controller (rev 50)
00:0a.0 RAID bus controller: VIA Technologies, Inc. VT6421 IDE/SATA Controller (rev 50)
01:00.0 VGA compatible controller: NVIDIA Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by sudodus on 2013-02-17
- how much ram?

- if I understand correctly, wired internet (ethernet)

Anyway, this hardware indicated that the current standard (vanilla) Ubuntu will need more horsepower, so I'm inclined to recommend

1. Lubuntu 12.04 or 12.10
2. Xubuntu 12.04 LTS

Test them live (booted from external drive) including boot options, start with nomodeset. Avoid installing drivers manually!

and if you have too much problems try

3. Knoppix

[[COLOR="Red"]http://www.knopper.net/knoppix-mirrors/index-en.html[/COLOR]]("http://www.knopper.net/knoppix-mirrors/index-en.html")

which is known to work well with old hardware. Normally you don't install Knoppix, instead you run it live or persistent live "poor man's install", and update by downloading a new iso file when available.

---

### Post by Byb on 2013-02-17
2GB ram
PATA 
sda1 / 160GB
SATA1 
sdb1 /home 320GB
SATA2 
sdc1 swap 2500MB
sdc5 /var 50GB
sdc6 /tmp 50GB
sdc7/srv remaining (~210GB) (the idea herebehind this one was to store shared data for a samba server)

---

### Post by Byb on 2013-02-17
I just did the cat /etc/apt/sources.list.apt-setup >> /etc/apt/sources.list
then apt-get update
then apt-get install nvidia-current
here is the output:
Some packages can't be installed. This could mean
you asked the impossible, or, if you use the unstable distribution,
that some packages are not yet created  or are not published out of Incoming.
The following information may help you to resolve the situation:

The following packages contain unsatisfied dependancies:
nvidia-current: 
depends on : xorg-video-abi-11
depends on :  xserver-xorg-core (>= 2:1.10.99.901)
E: impossible to correct problems, faulty packages are in "keep in state" mode.

---

### Post by sudodus on 2013-02-17
Please don't try to install nvidia-current now! Try to run Ubuntu without it. There is a built-in driver, that is automatically chosen by the kernel. If Ubuntu with Unity will be too slow, use another desktop environment: Lubuntu with LXDE or Xubuntu with XFCE or some other distro, that needs less horsepower from the cpu and graphics chip!

When your operating system runs reasonably well, at a later stage, you can back it up to an external drive, and then try to install a proprietary driver for your nvidia card.

---

### Post by Byb on 2013-02-17
Cool
I rebooted and login into the blue screen: here I got a OSD like popup (up right) saying drivers are available, but in this blue screen with no icons, I couldn't do anything, so I tty1'd to apt-get install gnome-shell, went back to tty7, killed X and from GDM loged in with gnome-classic and cooool, got icons from which I could download/install nvidia-173
I did not yet tried if unity works but I really don't mind, I rather like gnome shell
Currently downloading french language support et basta

---

### Post by sudodus on 2013-02-18
> **Byb said:**
> Cool
I rebooted and login into the blue screen: here I got a OSD like popup (up right) saying drivers are available, but in this blue screen with no icons, I couldn't do anything, so I tty1'd to apt-get install gnome-shell, went back to tty7, killed X and from GDM loged in with gnome-classic and cooool, got icons from which I could download/install nvidia-173
I did not yet tried if unity works but I really don't mind, I rather like gnome shell
Currently downloading french language support et basta
It was a complicated way to get it working. Congratulations :KS

I'm sorry that I underestimated your skill and I'm glad you managed to get it working. If you are happy with gnome-classic, good! If not, I suggest that you backup your system and start trying some lighter desktop environments to experience fast and nice graphics. You can install lubuntu-desktop and xubuntu-desktop or 'only' LXDE and XFCE.

```
sudo apt-get install lubuntu-desktop
sudo apt-get install lubuntu-desktop
```
or
```
sudo apt-get install lxde
sudo apt-get install xfce4
```
 
Select desktop environment at the log in screen. The most extremely light-weight alternative to select will be Openbox, only a window manager, where you right-click on the background to open a terminal window. Openbox will give you the best chance to play high definition video.

But I guess you want more convenience and maybe also eye-candy, so for other purposes you will select some other alternative, maybe gnome-classic or xubuntu.

Good luck :-)

---

### Post by Byb on 2013-02-18
Hi Sudodus
Please do not overestimate my skill (don't forget my signature: forever newb)
I had nothing to loose but Ubuntu, because I have a XP-sp3 CD that works OOTB everywhere.
I  think I guess what went wrong because of softwares install step failed:  there was only the new gnome (unity like) installed (this is why the  screen was no icons blue).
After the cat sources.list.apt-setup  >> sources.list, I also had a duplicated CDROM entry: I just had  to remove it manualy to get rid of warnings with apt-get commands;  surely a simple copy command would have do the job without this small  issue. I also had a bit later to remove the CDROM entry because it  prevented me to install update-manager without the CD.
Now I'd like  to ensure myself that APT is configured as it would default to, to  prevent any unwanted behaviour in the future. I'll check against my  laptop, but as this one was highly tweaked over the time to make it  ~work~, I'm not so sure it is a good reference.
I will also remove the sources.list.apt-setup file: not sure again, but I think it is no more useful.
Bye bye

---

### Post by sudodus on 2013-02-18
The following commands were posted by oldfred@ubuntuforums to help repairing the apt-get machinery. It can be used as single commands preceded by sudo, or be run as a batch file. I think it is good to run single commands and watch the output of each of them before going to the next one.

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

```

---

