---
title: "Ubuntu 12.04 on HP Envy dv7 laptop"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by bart.vanaudenhove on 2013-06-08
Hello,

I have been installing and tweaking Ubuntu 12.04.2 LTS Precise Pangolin (64-bit) on a [HP Envy dv7 7390eb laptop]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03626043&cc=nl&dlc=nl&lc=nl&jumpid=reg_r1002_nlnl_c-001_title_r0001") with Windows 8 (UEFI) pre-installed, and I have been logging my problems and solutions. I wanted to share them here, maybe they can save some time for other people having the same or almost the same laptop.

I use XFCE but I think that most of my findings here are universal, all the more because I didn't install xubuntu but the default ubuntu.

[FONT=Trebuchet MS]I have to say that, in general, Ubuntu 12.04 works pretty well out of the box on this laptop, but needs a bit of tweaking to get every detail working - still a work in progress that I intend to keep logging on [this blog page here]("http://bartssolutions.blogspot.be/2013/06/how-to-install-ubuntu-1204-lts-on-hp.html") but here are already some results...[/FONT]

[FONT=Trebuchet MS]So...[/FONT]
**Step 1: installing Ubuntu**

[FONT=Trebuchet MS]Pretty straightforward, I encountered no problems. You have to do some extra steps to have a working boot manager because of the UEFI system (see further), but if you follow the instructions you should not encounter any problems.[/FONT]
[FONT=Trebuchet MS]
[/FONT]
[FONT=Trebuchet MS]The laptop comes with two 1 TB hard disks. Disk 1 contains Windows, Disk 2 is partitioned as "DATA". I decided to use disk 1 for Windows + Windows DATA and disk 2 for Linux.[/FONT]
[FONT=Trebuchet MS]
[/FONT]
[FONT=Trebuchet MS]First, _from within Windows_, I deleted the "DATA" partition, then shrunk the "OS" partition to make room for a new "DATA" partition on disk 1, which I then created. For instructions about all this, see for instance [here]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/") or do a search on internet with keywords "*Windows 8 shrink volume*".[/FONT]
[FONT=Trebuchet MS]Do not create a partition on Disk 2 from within Windows, just leave it "unallocated" (free) and reboot on your Linux Live USB. Linux will take care of everything.[/FONT]
[FONT=Trebuchet MS]
[/FONT]
[FONT=Trebuchet MS]Then just do a standard Ubuntu "install alongside Windows" automatic install (see general installation instructions via the links on the [Ubuntu page]("http://www.ubuntu.com/download/desktop")), then follow the steps outlined in "*Installing Ubuntu Quickly and Easily via Trial and Error*" on the [UEFI-page of help.ubuntu.com]("https://help.ubuntu.com/community/UEFI"). You will have to restart from Live-USB and do a boot-repair, it's all explained on the pages I mentioned.

To install Ubuntu from live USB I did not have to disable SecureBoot; however once installed and the boot-repair executed (as outlined on the Ubuntu UEFI page, see above link), I had to disable it to be able to boot into Windows. Weird, but true. So I just keep SecureBoot disabled for the moment, although with Linux it does work. [/FONT]
[FONT=Trebuchet MS]
[/FONT]
[FONT=Trebuchet MS]After the install I decided I wanted a bigger swap in linux. Default installed is 16GB, same as RAM and I wanted double for extra safety so as to be sure that suspend would work. This may or may not be necessary or a good idea, but it's what I did and it seems to work. Apparently I could have just installed a swap file - more info and detailed instructions on the [SwapFaq page of Ubuntu help]("https://help.ubuntu.com/community/SwapFaq/").[/FONT]
[FONT=Trebuchet MS]I didn't write down the steps I took, but, from memory, I did the following.  [/FONT]
[FONT=Trebuchet MS]
[LIST]
[*]rebooted with live-USB,
[*]ran Gparted,
[*]right-click on swap partition (16GB at this moment) -> swapoff
[*]right-click on swap partition -> delete
[*]apply
[*]right-click on main linux partition -> resize to about 17 GB less
[*]apply
[*]new unallocated space is 32 GB, right-click on it -> new -> extended
[*]right-click in extended partition -> new, choose type "linux-swap"
[*]apply
[/LIST]
Now boot into your installed linux (on hard drive) and

[LIST]
[*]run Gparted (install first if necessary)
[*]right-click on swap partition -> swapon
[*]then follow instructions [here]("https://help.ubuntu.com/community/SwapFaq/") (chapter "How do I add more swap") to edit /etc/fstab.
[/LIST]
I did get an error message on first reboot after the Live-USB, probably because I did "swapon" from within the LiveUSB without editing /etc/fstab, but it didn't cause any further problems, and I never got it again. Which makes sense, as I edited /etc/fstab.

[SIZE=3]**Step 2: adding TLP and Bumblebee**[/SIZE]

[TLP]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html") is a tool that runs in the background to optimize battery-life. See installation instructions on the [TLP-homepage]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html").

[Bumblebee]("http://bumblebee-project.org/") is a package that enables [NVIDIA Optimus]("http://www.nvidia.com/object/optimus_technology.html") in Linux. This laptop comes with two graphics cards, one that uses little power but is not very good for 3D, and another one (NVidia) that is a lot better for 3D but consumes more power and generates more heat. The[Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html") technology is designed to optimize battery life by disabling the NVidia card when not necessary. After installing [Bumblebee]("http://bumblebee-project.org/"), if I understand correctly, the default card used is the "simple" one (not Nvidia), unless you start the program in question in a terminal and put "optirun" in front of the program name (see the [Bumblebee wiki]("https://github.com/Bumblebee-Project/Bumblebee/wiki") for all details). More info on the [Bumblebee]("http://bumblebee-project.org/") homepage, [installation instructions here]("http://bumblebee-project.org/install.html").
I tested running "glxspheres" and "optirun glxspheres" and there was indeed a notable difference in performance.

[SIZE=3]**Step 3: Wifi**[/SIZE]

Wifi actually works out of the box (kind of) but you may need to have a look at [this thread here]("http://ubuntuforums.org/showthread.php?t=2150529") to get it up and running. Basically I have to use the command[INDENT]sudo rfkill unblock all [/INDENT]
at every boot to activate the device, after this I can turn on or off the wifi and bluetooth using the net applet. I also installed [wifi-radar]("http://wifi-radar.berlios.de/").

[SIZE=3]**Step 4: get Beats Audio working**[/SIZE]

Learning from [this thread]("http://askubuntu.com/questions/70156/hp-dv7-beats-audio-alsa-base-modification-what-should-be-the-line/303656#303656"), I did in a terminal:[INDENT]gksudo gedit /etc/modprobe.d/acpi-base.conf[/INDENT]
and added the following line at the bottom:[INDENT]options snd-hda-intel model=ref[/INDENT]
Save the file. Then reboot, all speakers work, great sound.

Only problem is that, when connecting headphones, the subwoofer keeps playing. There is however an easy workaround: in your favorite alsamixer (for instance gnome-alsamixer), bring down the volume of "Front" to zero. In the alsamixer you can actually set the volumes for headphones and speakers separately, they're called "Headphones" and "Front" respectively. So it is a bit of a hassle, every time you connect the headphones you have to go to alsamixer and bring down the "Front" volume, and vice versa, but it does work.

[SIZE=3]**Step 5: non-free codecs / Playing encrypted DVDs**[/SIZE]

The prime source of information is here: [RestrictedFormats/Playing DVDs on Ubuntu help]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

What I did was:
Go to [medibuntu.org]("http://www.medibuntu.org/"), follow instructions and install especially the lib- and non-free-packages. I installed them almost all. Reboot.
At first I still got error messages when trying to play a certain DVD.
Then I used [regionset]("http://linvdr.org/projects/regionset/") to set the region of my DVD-player to 2 (Europe). Reboot.
The DVD played, but garbled. Finally I deleted the ~/.dvdcss/ folder (I [opened my home folder as root in Thunar]("http://kedaver.blogspot.be/2011/08/open-as-root-in-thunar-xubuntu.html")), rebooted, and then everything worked.[/FONT]

---

