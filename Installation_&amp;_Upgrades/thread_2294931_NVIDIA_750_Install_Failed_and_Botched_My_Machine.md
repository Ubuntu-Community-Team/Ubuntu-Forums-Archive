---
title: "NVIDIA 750 Install Failed and Botched My Machine"
date: 2015-09-14
forum: Installation &amp; Upgrades
---

### Post by incubus158 on 2015-09-14
Hello there, I need help recovering my ubuntu box.  I am on 14.4 ubuntu.

I downloaded an NVIDIA GeForce 64 bit 750 driver and installed it because it was stating that when I plugged in a second monitor that I didnt have enough graphics memory.

Several times rebooting I was able to get it where I see my login screen, but now it just goes to a terminal and kind of freezes.  

I took out the drive and mounted in windows and here is my .xsession_errors file:

/usr/lib/nux/unity_support_test: error while loading shared libraries: /usr/lib/x86_64-linux-gnu/libGL.so.1: file too short
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: hud main process (3213) terminated with status 127
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: gnome-session (Unity) main process (3217) terminated with status 1
init: at-spi2-registryd main process ended, respawning
init: unity-settings-daemon main process (3199) killed by TERM signal
init: logrotate main process (3084) killed by TERM signal
init: update-notifier-crash (/var/crash/_opt_google_chrome_chrome.1000.crash) main process (3122) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_bin_compiz.1000.crash) main process (3126) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_bin_skype.1000.crash) main process (3127) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_bin_Xorg.0.crash) main process (3128) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_lib_ibus_ibus-ui-gtk3.1000.crash) main process (3129) killed by TERM signal
init: update-notifier-crash (/var/crash/_usr_lib_x86_64-linux-gnu_indicator-application_indicator-application-service.1000.crash) main process (3130) killed by TERM signal
init: unity-panel-service main process (3226) killed by TERM signal
init: xsession-init main process (3195) killed by TERM signal
init: Disconnected from notified D-Bus bus

Does anyone have any ideas of commands I can try running to get rid of this crap NVIDIA stuff?  

I tried running NVIDIA.run --uninstall and it says I dont have it installed.  I also tried sudo apt-get uninstall nvidia* and I think that got me to my login screen, but now I cant login!

Please help me with your wise 'nix wizardry and experience!!!

---

### Post by v3.xx on 2015-09-14
Are you sure its crap nvidia stuff and not a crap install :)

Most find it better to install from the ppa if the driver is not offered in driver upgrade tab.

[http://askubuntu.com/questions/478014/new-nvidia-graphics-card-drivers](http://askubuntu.com/questions/478014/new-nvidia-graphics-card-drivers)

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=)

---

### Post by efflandt on 2015-09-15
The default nouveau driver or nvidia-current package do not work for nvidia cards with the new Maxwell chip, or at least they did not work in Ubuntu 14.04.1 when I installed that with a GTX 750 Ti.

If you ran a .run file earlier, when you tried to do NVIDIA.run --uninstall are you sure that the error was not "file not found"? I have never used a .run file from nvidia.com, but judging from another post, the name of the run file is probably longer including the driver version and you have had to use "sudo " prefix for something like: sudo ./NVIDIA-Linux-x86_64-355.06.run --uninstall

If you have Ethernet that can connect automatically or configured WiFi during install, I would suggest doing the following:
- Boot a (recovery mode) kernel.
- When the menu comes up, **Enable Networking** (which also remounts the read-only file system read-write). If you get any errors about unidentified hardware, wait a while for it to return to the menu.
- Choose **Root Console** (as root you will not need to use sudo where you normally would)
- **cd** to the directory where you have that .run file, then with ./ prefix attached to it run that .run file with --uninstall after it like: ./NVIDIA-Linux-x86_64-355.06.run --uninstall
- Just in case you did try to install any nvidia package do: apt-get purge nvidia*
- Then do
apt-get update
apt-get install nvidia-331-updates
reboot

The nvida-331-updates package currently installs a 340 version driver. That should at least get you up and running unless you have other issues.

One possible remaining issue might be if you did not use **nomodeset** boot parameter when booting the live/install iso (for anything with nvidia except a laptop). That can temporarily be added by hitting e during the grub menu and inserting nomodeset in the line that includes "quiet splash". Then insert **nomodeset** inside of the quotes in the line in /etc/default/grub that contain "quiet splash", and run: sudo update-grub

---

