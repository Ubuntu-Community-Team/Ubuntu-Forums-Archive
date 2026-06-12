---
title: "After update, boots to tty1, no X11 GUI"
date: 2019-06-19
forum: Installation &amp; Upgrades
---

### Post by fglrx-updates on 2019-06-19
I have not found any posts on this particular problem. I might already have a workaround; I am making this post to possibly help others who come after.
(Or to get a warning to NO DON'T DO THAT.)
(If I don't make a follow-up post with the results, then I bricked my computer.)


Possible relation to [https://ubuntuforums.org/showthread.php?t=2317545&highlight=boots+tty1](https://ubuntuforums.org/showthread.php?t=2317545&highlight=boots+tty1) is unknown. There sudo dpkg --configure -a was a solution to a problem, here it is the cause of the problem.


Ubuntu 14.04 LTS Trusty Tahr


2019-06-11 about 15:00, I wanted to install a package. (openjdk-11-jdk, to be specific, but it doesn't matter because I never got to install it.)
I have previously installed many packages with sudo apt-get install, with no problems.
I got an error message saying that I couldn't install the package without first running sudo dpkg --configure -a. (I don't remember what the error message said exactly, and it was impossible to retrieve later.)
So I ran sudo dpkg --configure -a. Then I rebooted, just to make sure everything was fine.
On boot, my computer booted straight to tty1.
ctrl+alt+F2--6 could access tty2--tty6. ctrl+alt+F7 yields a black screen with a white curser blinking in the top left corner.


Attempt 1: In GRUB, "Ubuntu, with Linux 3.13.0-165-generic (recovery mode)". "resume" just yields the usual problem, so I tried "dpkg --- Repair broken packages".
Result: "The following NEW packages will be installed: linux-base linux-headers-3.13.0-170 linux-headers-3.13.0-170-generic linux-image-3.13.0-170-generic linux-image-generic linux-modules-3.13.0-170-generic linux-modules-extra-3.13.0-170-generic
The following packages will be upgraded: [a lot, but nothing that looks like a graphics driver]"
Of course if I approve it, I get a bunch of "Failed to fetch", because it fails to connect to the wifi. Then it says "Finished, please press Enter." and kicks me back to the recovery menu.


Attempt 2: In GRUB, "Ubuntu, with Linux 3.13.0-165-generic (recovery mode)" but this time selecting "failsafeX" from the recovery menu.
Result: "Fatal server error: (EE) no screens found(EE) Please consult the X.Org Foundation support at wiki.x.org for help.
Please also check the log file at /var/log/Xorg.failsafe.log for additional information.
Server terminated with error (1). Closing log file."


Attempt 3: In GRUB, "Ubuntu, with Linux 3.13.0-24-generic (recovery mode)". Results same as 3.13.0-165.


Attempt 4: In tty1, sudo service lightdm start.
Result: "start: Job failed to start"


The HP Video Memory Fast Check shows everything fine.


$ lspci -nn
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Richland [Radeon HD 8550G] [1002:990d]


Radeon 8500 appears to be supported: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
(I don't know what else to check as far as the video card.)


Examining the install log makes it look like an old update from March was completed by the sudo dpkg --configure -a. I don't know whether that matters.


I am getting a list of all recently installed packages like so:


$ grep --binary-files=text "2019-06-11.*.install" /var/log/dpkg.log | awk '{print $5}' | uniq > installedPackages.txt
I don't know why --binary-files=text is necessary, but it is, otherwise grep just complains it's a binary file.


I'm planning to pipe the list to xargs apt-get -y remove as recommended in [https://askubuntu.com/questions/68460/how-can-i-uninstall-all-the-packages-ive-installed-today](https://askubuntu.com/questions/68460/how-can-i-uninstall-all-the-packages-ive-installed-today) .
I'd rather revert each package to whatever version it had before the update, but I don't know how to do that.


I've attached the full log files from dpkg and apt, and the simple list of packages is also below.




liblwres90:amd64
dkms:all
grub-common:amd64
apt-transport-https:amd64
avahi-autoipd:amd64
virtualbox-dkms:all
linux-libc-dev:amd64
krb5-locales:all
thunderbird:amd64
thunderbird-gnome-support:amd64
libgs9-common:all
linux-image-3.13.0-165-generic:amd64
poppler-utils:amd64
linux-headers-3.13.0-165:all
libexiv2-12:amd64
libc-bin:amd64
firefox:amd64
openssh-client:amd64
firefox-locale-en:amd64
grub2-common:amd64
apt-utils:amd64
libisc95:amd64
ca-certificates:all
policykit-1:amd64
grub-efi-amd64-bin:amd64
thunderbird-locale-en:amd64
shim-signed:amd64
virtualbox:amd64
linux-headers-3.13.0-165-generic:amd64
ssh-askpass-gnome:amd64
linux-image-extra-3.13.0-165-generic:amd64
14.12-0ubuntu6.14.04.4
landscape-client-ui-install:amd64
libgs9:amd64
libisccc90:amd64
thunderbird-locale-en-us:all
virtualbox-qt:amd64
ghostscript:amd64
libdns100:amd64
linux-headers-generic:amd64
libisccfg90:amd64
linux-signed-image-3.13.0-165-generic:amd64
grub-efi-amd64:amd64
grub-efi-amd64-signed:amd64
linux-crashdump:amd64
linux-signed-image-generic:amd64
ghostscript-x:amd64
libbind9-90:amd64
bind9-host:amd64
avahi-daemon:amd64
dnsutils:amd64
avahi-utils:amd64
libnss3-nssdb:all
libnss3:amd64
adobe-flashplugin:amd64
libreoffice-core:amd64
python3-uno:amd64
libreoffice-math:amd64
adobe-flash-properties-gtk:amd64
libreoffice-base-core:amd64
google-chrome-stable:amd64
libreoffice-pdfimport:amd64
libnss3-1d:amd64
libreoffice-avmedia-backend-gstreamer:amd64
libreoffice-gtk:amd64
libreoffice-draw:amd64
libreoffice-calc:amd64
libreoffice-impress:amd64
libreoffice-writer:amd64
libreoffice-gnome:amd64
libreoffice-ogltrans:amd64
libc-bin:amd64
libreoffice-presentation-minimizer:all
libreoffice-common:all

---

### Post by CatKiller on 2019-06-20
14.04 has passed its End Of Life. The repositories have moved and are no longer maintained.

Installing 18.04 LTS would be the best thing to do.

If the repositories still existed, booting from a live image and chrooting your local install is a useful way of fixing things if recovery mode doesn't have the tools you need.

---

### Post by fglrx-updates on 2019-06-29
Update: I reinstalled Ubuntu (18.04) and everything appears to be working now.

---

