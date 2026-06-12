---
title: "install 22.04 Jellyfish -Firefox not working"
date: 2022-05-13
forum: Installation &amp; Upgrades
---

### Post by fearless752 on 2022-05-13
G'day everyone

Just had major computer failure. Installed new graphics cards and 480gig SSD drive.

Installed 22.04 jellyfish, updates installed. Boots fine.

Firefox will not start or connect to network.

Any clues as to why not.

Cheers
Frank

---

### Post by guiverc on 2022-05-13
You are aware `firefox` is now a *snap* package, thus is slower to start.  The program is now in a *squashfs* thus needs to be *uncompressed* and setup before it can be run. This impacts on the initial run in that session.

I'd suggest starting it with a command like

```
snap run firefox --enable-logging=stderr --v=1
```

in hopes more details on problems with `firefox` are revealed.

---

### Post by fearless752 on 2022-05-13
Tries that, got error message -- fail to load module " canberra-gtk-module'

---

### Post by guiverc on 2022-05-14
That isn't an error message, instead a warning message that is expected, telling you that GTK2/GTK3 theming modules weren't found.  On a standard Ubuntu desktop system that message is expected (*they're not included by default*) and messages are only shown as verbose logging was asked for.

If I run `firefox` using the command I provided in the prior post, then exit it once it's appeared; the warning message you provided is all I'll see. I was hoping when you ran it, you'd get extra messages that may provide more clues.

Next I'd look in /var/crash/ for .crash files, ie.

```
ls -lah /var/crash
```

where I'd look for time/date stamps close to when you ran `firefox`.

If your system wasn't a clean install; but it found older firefox profiles, it'll try and import them, which can take awhile (*let alone the first run on a login/session taking time to due snap package format*).  I'd probably check it wasn't still running; which I'd likely do with 

```
ps -elf |grep firefox
```

(the *long* won't be needed; it's just how my fingers type it). Assuming you waited long enough for the *squashfs* to be uncompressed; any profiles found to be imported, sorry that's all I've got currently. You'll have to wait for others who may have further ideas.

---

### Post by UBUminJ on 2022-05-15
In my case, this helped: [https://ubuntuforums.org/showthread.php?t=2474678](https://ubuntuforums.org/showthread.php?t=2474678)
It seems, NVIDIA is part of the problem.

---

### Post by fearless752 on 2022-05-15
Still not working.

---

### Post by grahammechanical on 2022-05-15
A bit of wild thinking from me. How did you update? When we use the terminal any snap packaged apps do not get updated (refreshed).  When we use Software Updater snap apps are automatically refreshed. We can update snap apps from the terminal.

```
sudo snap refresh
```

A few weeks ago I had a situation where the snap version of zoom-client failed to load. It was the zoom 5.10 version. A few days later an automatic update of snaps downgraded the version to 5.9 and now the snap version of zoom-client loads. But there was a different problem. I could join a regular meeting with one individual but not join a regular meeting with many individuals. The Zoom server said I needed to upgrade to version 5.10. I join that particular meeting using the deb version. I am waiting for the snap version to be updated to a working 5.10 version.

I relate this story to suggest that you may have got a buggy snap version of Firefox that has not been fixed because the snap version of Firefox has not been refreshed (update/upgrade).

Regards

---

### Post by fearless752 on 2022-05-15
It was a clean install. New SSD hard drive, new nvidia GeForce GT 730 graphics card. Intel i5, 16gig RAM.

Still trying anything that may work.

Cheers

---

### Post by ajgreeny on 2022-05-15
To give us a bit more info about your system, let's see the output of command ```
inxi -Fzx
```
Among other info this will show us the details of your graphic system and the current driver being used by that nvidia card, which I think is now a fairly old model.

---

### Post by fearless752 on 2022-05-16
System info

~$ inxi -Fzx
System:
  Kernel: 5.15.0-30-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.0 Distro: Ubuntu 22.04 (Jammy Jellyfish)
Machine:
  Type: Desktop System: Micro-Star product: MS-7D18 v: 1.0
    serial: <superuser required>
  Mobo: Micro-Star model: B560M PRO-VDH WIFI (MS-7D18) v: 1.0
    serial: <superuser required> UEFI: American Megatrends LLC. v: 1.00
    date: 03/01/2021
Battery:
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M510
    charge: 55% (should be ignored) status: Discharging
  Device-2: hidpp_battery_1 model: Logitech K350
    charge: 70% (should be ignored) status: Discharging
CPU:
  Info: 6-core model: Intel Core i5-10400 bits: 64 type: MT MCP
    arch: Comet Lake rev: 3 cache: L1: 384 KiB L2: 1.5 MiB L3: 12 MiB
  Speed (MHz): avg: 800 high: 801 min/max: 800/4300 cores: 1: 800 2: 800
    3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 9: 800 10: 800 11: 800 12: 801
    bogomips: 69597
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GK208B [GeForce GT 730] vendor: ASUSTeK driver: nouveau
    v: kernel bus-ID: 01:00.0
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: nouveau resolution: 1920x1200~60Hz
  OpenGL: renderer: NV106 v: 4.3 Mesa 22.0.1 direct render: Yes
Audio:
  Device-1: Intel vendor: Micro-Star MSI driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3
  Device-2: NVIDIA GK208 HDMI/DP Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-30-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Tiger Lake PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlo1 state: down mac: <filter>
  Device-2: Realtek RTL8125 2.5GbE vendor: Micro-Star MSI driver: r8169
    v: kernel port: 3000 bus-ID: 02:00.0
  IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth type: USB driver: btusb v: 0.8
    bus-ID: 1-14:5
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 1.37 TiB used: 606.79 GiB (43.1%)
  ID-1: /dev/sda vendor: PNY model: CS900 480GB SSD size: 447.13 GiB
  ID-2: /dev/sdb vendor: Western Digital model: WD10EZEX-00WN4A0
    size: 931.51 GiB
  ID-3: /dev/sdg type: USB vendor: SanDisk model: Cruzer Blade
    size: 28.65 GiB
Partition:
  ID-1: / size: 438.55 GiB used: 184.13 GiB (42.0%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: N/A gpu: nouveau temp: 36.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 361 Uptime: 19m Memory: 15.53 GiB used: 3.69 GiB (23.8%)
  Init: systemd runlevel: 5 Compilers: gcc: N/A Packages: 1718 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

I have got Firefox running, it was only because I clicked on a link in my mail.
Not surre if it works when I reboot.

Going to try that now.

Frank

---

### Post by fearless752 on 2022-05-16
Tried rebooting. Still need to click on link in email to load Firefox.

What are we missing.

Cheers
Frank

---

### Post by ajgreeny on 2022-05-16
It looks as if you are using wayland graphics on the system which I believe had problems with nvidia in the past.

At the login screen try logging in using X11. Choose your username, enter your password but before hitting Enter find the cog-wheel icon where you can choose 3ither the default Ubuntu or X11-Ubuntu.

I also see that you are using the nouveau driver for the nvidia card. This may be all that is offered as the card is an old one but it's worth going to Additional-Drivers from the Activities system to see if an nvidia driver is available and recommended.

---

### Post by fearless752 on 2022-05-17
Not sure how to do this. I have set my computer to login automaticly. 

When I click on link in e-mail, Fireefox starts but does not show arrow in task bar.

Not the ideal way to get it working but it is a work around.

Cheers

> **ajgreeny said:**
> It looks as if you are using wayland graphics on the system which I believe had problems with nvidia in the past.

At the login screen try logging in using X11. Choose your username, enter your password but before hitting Enter find the cog-wheel icon where you can choose 3ither the default Ubuntu or X11-Ubuntu.

I also see that you are using the nouveau driver for the nvidia card. This may be all that is offered as the card is an old one but it's worth going to Additional-Drivers from the Activities system to see if an nvidia driver is available and recommended.

---

### Post by ActionParsnip on 2022-05-17
Do other browsers run OK?

---

### Post by fearless752 on 2022-05-17
FIREFOX WORKING - yes

Did some more googling for my problem, found this: [https://www.makeuseof.com/things-to-do-after-upgrading-to-ubuntu-2204-lts/](https://www.makeuseof.com/things-to-do-after-upgrading-to-ubuntu-2204-lts/)

Scrolling down was this solution:

[https://www.makeuseof.com/things-to-do-after-upgrading-to-ubuntu-2204-lts/](https://www.makeuseof.com/things-to-do-after-upgrading-to-ubuntu-2204-lts/)

[h=2]Replace Snap Firefox With a Quicker Version[/h] One of the biggest gripe with Ubuntu 22.04 LTS is the change to the  Firefox browser. In previous releases, it was pre-installed in the  standard way, much like other apps.
 With the switch to support for [Snap packages]("https://www.makeuseof.com/everything-you-need-to-know-about-snap-and-snap-store/"),  Mozilla Firefox is more secure, running in its own snap-managed sandbox  and auto-updating. However, this also makes the software slower.
 Fortunately, there is a way to revert to running Mozilla Firefox the old way.
 Start by removing the Snap version of Firefox in the Terminal with
 sudo snap remove --purge firefox To add the &#8220;real&#8221; Firefox, you&#8217;ll need to add the Mozilla Team PPA  repository. Once this is added, you have a location from which to  install Firefox. Again in the terminal enter
    sudo add-apt-repository ppa:mozillateam/ppa Input your password when prompted.
 To install Mozilla Firefox with apt, use
 sudo apt install -t 'o=LP-PPA-mozillateam' firefox Note the use of -t 'o=LP-PPA-mozillateam'. This condition ensures  that apt uses the PPA you added earlier as the source for the  installation.
 With that done, you can start using the &#8220;real&#8221; Firefox, rather than the Snap file.

It worked. Rebooted computer, found and dragged Firefox to favourites. 

We now have a working system with browsing. Must go and have a drink to celebrate.

Thanks for all your info and possible solutions.

Cheers

Frank
Gold Coast Australia.

---

