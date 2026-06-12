---
title: "&quot;You have held broken packages&quot; Apt-Get refusing to work."
date: 2018-09-19
forum: Installation &amp; Upgrades
---

### Post by kieferrodriguez on 2018-09-19
Hey guys,

Im a little overwhelmed here, I upgraded from 16.04 to 18.04 last night. Ive been trying to install RetroArch (although the problem occurs with any package I attempt to install via apt-get) - here is the output:

```
user@tux:~/Downloads$ sudo apt-get install retroarch libretro-*Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libretro-beetle-lynx' for glob 'libretro-*'
Note, selecting 'libretro-genesisplusgx' for glob 'libretro-*'
Note, selecting 'libretro-4do' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-mercury-performance' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-mercury-accuracy' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-performance' for glob 'libretro-*'
Note, selecting 'libretro-beetle-wswan' for glob 'libretro-*'
Note, selecting 'libretro-beetle-ngp' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-balanced' for glob 'libretro-*'
Note, selecting 'libretro-gambatte' for glob 'libretro-*'
Note, selecting 'libretro-fbalpha2012' for glob 'libretro-*'
Note, selecting 'libretro-fba' for glob 'libretro-*'
Note, selecting 'libretro-beetle-psx' for glob 'libretro-*'
Note, selecting 'libretro-gtk-0.14-0' for glob 'libretro-*'
Note, selecting 'libretro-ppsspp' for glob 'libretro-*'
Note, selecting 'libretro-vba-next' for glob 'libretro-*'
Note, selecting 'libretro-mupen64plus' for glob 'libretro-*'
Note, selecting 'libretro-beetle-sgx' for glob 'libretro-*'
Note, selecting 'libretro-frontend' for glob 'libretro-*'
Note, selecting 'libretro-2048' for glob 'libretro-*'
Note, selecting 'libretro-tyrquake' for glob 'libretro-*'
Note, selecting 'libretro-beetle-pcfx' for glob 'libretro-*'
Note, selecting 'libretro-prosystem' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-accuracy' for glob 'libretro-*'
Note, selecting 'libretro-parallel-n64' for glob 'libretro-*'
Note, selecting 'libretro-picodrive' for glob 'libretro-*'
Note, selecting 'libretro-nestopia' for glob 'libretro-*'
Note, selecting 'libretro-mednafen-psx' for glob 'libretro-*'
Note, selecting 'libretro-core-info' for glob 'libretro-*'
Note, selecting 'libretro-beetle-pce-fast' for glob 'libretro-*'
Note, selecting 'libretro-mgba' for glob 'libretro-*'
Note, selecting 'libretro-beetle-supergrafx' for glob 'libretro-*'
Note, selecting 'libretro-beetle-vb' for glob 'libretro-*'
Note, selecting 'libretro-tgbdual' for glob 'libretro-*'
Note, selecting 'libretro-gtk-0.14-dev' for glob 'libretro-*'
Note, selecting 'libretro-fmsx' for glob 'libretro-*'
Note, selecting 'libretro-stella' for glob 'libretro-*'
Note, selecting 'libretro-yabause' for glob 'libretro-*'
Note, selecting 'libretro-gtk-0.12-dev' for glob 'libretro-*'
Note, selecting 'libretro-desmume' for glob 'libretro-*'
Note, selecting 'libretro-gtk-0.10-dev' for glob 'libretro-*'
Note, selecting 'libretro-beetle-bsnes' for glob 'libretro-*'
Note, selecting 'libretro-catsfc' for glob 'libretro-*'
Note, selecting 'libretro-quicknes' for glob 'libretro-*'
Note, selecting 'libretro-bsnes-mercury-balanced' for glob 'libretro-*'
Note, selecting 'libretro-vbam' for glob 'libretro-*'
Note, selecting 'libretro-nxengine' for glob 'libretro-*'
Note, selecting 'libretro-snes9x-next' for glob 'libretro-*'
Note, selecting 'libretro-beetle-saturn' for glob 'libretro-*'
Note, selecting 'libretro-fbalpha' for glob 'libretro-*'
Note, selecting 'libretro-snes9x' for glob 'libretro-*'
Note, selecting 'libretro-prboom' for glob 'libretro-*'
Note, selecting 'libretro-beetle-gba' for glob 'libretro-*'
Note, selecting 'gnome-games-app' instead of 'libretro-frontend'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libretro-gtk-0.14-dev : Depends: libgtk-3-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Ive tried all the standard solutions:
[LIST]
[*]user@tux:~/Downloads$ sudo dpkg --configure -a
[*]user@tux:~/Downloads$ sudo apt-get clean && sudo apt-get update
[*]user@tux:~/Downloads$ sudo apt-get dist-upgrade
[*]Using synaptic GUI (Edit->Fix broken) etc
[/LIST]
Any help would be hugely appreciated! If any further info is needed feel free to ask and Ill post it asap.

Cheers!

Update:

Running the following
[LIST]
[*]user@tux:~/Downloads$ sudo apt-get dist-upgrade
[/LIST]
Has the following message at the end:
```
Processing triggers for linux-image-4.15.0-35-generic (4.15.0-35.38) .../etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-35-generic
W: initramfs-tools configuration sets RESUME=UUID=3a188c23-67e5-481f-8864-e5cc2a92e2b3
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=d36ff8fd-0429-48e5-9abf-9b407085672b)
I: Set the RESUME variable to override this.
cp: cannot stat './99-default.link': Not a directory
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.15.0-35-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-4.15.0-35-generic (--configure):
 installed linux-image-4.15.0-35-generic package post-installation script subprocess returned error exit status 1
Processing triggers for initramfs-tools (0.130ubuntu3.3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
W: initramfs-tools configuration sets RESUME=UUID=3a188c23-67e5-481f-8864-e5cc2a92e2b3
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=d36ff8fd-0429-48e5-9abf-9b407085672b)
I: Set the RESUME variable to override this.
cp: cannot stat './99-default.link': Not a directory
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.15.0-34-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-35-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Im unsure how relevant that is, but figured I should post it regardless.

Many thanks!

---

### Post by ajgreeny on 2018-09-19
Where does this retroarch come from; it does not appear to be in the repos?

---

### Post by westie457 on 2018-09-19
Did you re-enable the PPA in your Software Sources?
Have you tried running ```
sudo apt -f install
```

---

