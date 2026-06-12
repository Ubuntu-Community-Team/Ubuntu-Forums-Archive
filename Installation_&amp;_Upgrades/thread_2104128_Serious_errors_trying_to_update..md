---
title: "Serious errors trying to update."
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by CinoxFellpyre on 2013-01-12
Trying to update, get
```
E: /var/cache/apt/archives/libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb: trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1
```Sudo's broken according to kubuntu as well.

Should I just reinstall Kubuntu?


EDIT:

Here's the details section in Synaptic

```
(Reading database ... 403943 files and directories currently installed.)
Preparing to replace libdrm2 2.4.40+git1301070925.891517~gd~p (using .../libdrm2_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm-intel1 2.4.40+git1301070925.891517~gd~p (using .../libdrm-intel1_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libdrm-intel1 ...
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libdrm-nouveau1a ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1
No apport report written because MaxReports is reached already
                                                              Preparing to replace libdrm-radeon1 2.4.40+git1301070925.891517~gd~p (using .../libdrm-radeon1_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libdrm-radeon1 ...
Preparing to replace libgl1-mesa-dri 9.1~git1301090914.959e83~gd~p (using .../libgl1-mesa-dri_9.1~git1301101658.2f8994~gd~p_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 9.1~git1301090914.959e83~gd~p (using .../libgl1-mesa-glx_9.1~git1301101658.2f8994~gd~p_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libglapi-mesa 9.1~git1301090914.959e83~gd~p (using .../libglapi-mesa_9.1~git1301101658.2f8994~gd~p_i386.deb) ...
Unpacking replacement libglapi-mesa ...
Preparing to replace libkms1 2.4.40+git1301070925.891517~gd~p (using .../libkms1_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libkms1 ...
Preparing to replace libosmesa6 9.1~git1301090914.959e83~gd~p (using .../libosmesa6_9.1~git1301101658.2f8994~gd~p_i386.deb) ...
Unpacking replacement libosmesa6 ...
Preparing to replace libxatracker1 9.1~git1301090914.959e83~gd~p (using .../libxatracker1_9.1~git1301101658.2f8994~gd~p_i386.deb) ...
Unpacking replacement libxatracker1 ...
Preparing to replace linux-image-3.2.0-36-generic 3.2.0-36.56 (using .../linux-image-3.2.0-36-generic_3.2.0-36.57_i386.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-36-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Preparing to replace gpgv 1.4.11-3ubuntu2.1 (using .../gpgv_1.4.11-3ubuntu2.2_i386.deb) ...
Unpacking replacement gpgv ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gpgv (1.4.11-3ubuntu2.2) ...
Setting up libosmesa6 (9.1~git1301101658.2f8994~gd~p) ...
Setting up libdrm2 (2.4.40+git1301100933.1dbd87~gd~p) ...
Setting up libdrm-radeon1 (2.4.40+git1301100933.1dbd87~gd~p) ...
Setting up linux-image-3.2.0-36-generic (3.2.0-36.57) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-36.56 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-36.56 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-36-generic /boot/vmlinuz-3.2.0-36-generic
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.0.0-26-generic
Found initrd image: /boot/initrd.img-3.0.0-26-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up libxatracker1 (9.1~git1301101658.2f8994~gd~p) ...
Setting up libglapi-mesa (9.1~git1301101658.2f8994~gd~p) ...
Setting up libgl1-mesa-glx (9.1~git1301101658.2f8994~gd~p) ...
Setting up libkms1 (2.4.40+git1301100933.1dbd87~gd~p) ...
Setting up libdrm-intel1 (2.4.40+git1301100933.1dbd87~gd~p) ...
Setting up libgl1-mesa-dri (9.1~git1301101658.2f8994~gd~p) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by ibjsb4 on 2013-01-12
try

```
sudo apt-get clean
```

and follow with

```
sudo apt-get update
```

And please any errors you get (from apt-get update), if it doesn't work.

---

### Post by CinoxFellpyre on 2013-01-12
Didn't get any errors doing so.

---

### Post by ibjsb4 on 2013-01-12
> **CinoxFellpyre said:**
> Didn't get any errors doing so.

Have you tried your update manager?  Any errors?

---

### Post by misomoravcik on 2013-01-12
I have the same problem.

```
sudo apt-get clean
sudo apt-get update
```

doesn't help and update manager gives the same error.

I have no idea how to solve this.

---

### Post by CinoxFellpyre on 2013-01-12
> **ibjsb4 said:**
> Have you tried your update manager?  Any errors?
Update manager gives me the same errors. Also Ubuntu Software Center is broken.

---

### Post by ibjsb4 on 2013-01-12
Ok, try

```
sudo apt-get dist-upgrade
```

#3

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by CinoxFellpyre on 2013-01-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin aptdaemon aptdaemon-data gnupg gnupg-agent gnupg2 gpgsm libdrm-nouveau1a libportmidi0 libvlc5 libvlccore5
  linux-headers-3.2.0-36 linux-headers-3.2.0-36-generic linux-libc-dev python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse xserver-xorg-video-ati
  xserver-xorg-video-intel xserver-xorg-video-radeon
28 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.6 MB of archives.
After this operation, 865 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/main gnupg i386 1.4.11-3ubuntu2.2 [789 kB]
Get:2 http://archive.canonical.com/ubuntu/ precise/partner adobe-flash-properties-gtk i386 11.2.202.261-0precise1 [131 kB]
Get:3 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ precise/main libdrm-nouveau1a i386 2.4.40+git1301100933.1dbd87~gd~p [27.5 kB]
Get:4 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ precise/main xserver-xorg-video-radeon i386 1:7.0.0+git1301111216.e5e22d~gd~p [164 kB]
Get:5 http://archive.canonical.com/ubuntu/ precise/partner adobe-flashplugin i386 11.2.202.261-0precise1 [6,593 kB]                                         
Get:6 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ precise/main xserver-xorg-video-ati i386 1:7.0.0+git1301111216.e5e22d~gd~p [24.2 kB]          
Get:7 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ precise/main xserver-xorg-video-intel i386 2:2.20.17+git1301111216.a37d56~gd~p [692 kB]       
Get:8 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/main gnupg2 i386 2.0.17-2ubuntu2.12.04.2 [1,077 kB]                                              
Get:9 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/main gnupg-agent i386 2.0.17-2ubuntu2.12.04.2 [297 kB]                                           
Get:10 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/main gpgsm i386 2.0.17-2ubuntu2.12.04.2 [488 kB]                                                
Get:11 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/universe libportmidi0 i386 1:200-0ubuntu1.12.04.1 [20.6 kB]                                    
Get:12 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe vlc-plugin-notify i386 2.0.5-0ubuntu0.12.04.1 [6,608 B]                                
Get:13 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe vlc-plugin-pulse i386 2.0.5-0ubuntu0.12.04.1 [23.2 kB]                                 
Get:14 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe vlc i386 2.0.5-0ubuntu0.12.04.1 [1,408 kB]                                             
Get:15 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe libvlccore5 i386 2.0.5-0ubuntu0.12.04.1 [468 kB]                                       
Get:16 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe vlc-data all 2.0.5-0ubuntu0.12.04.1 [9,466 kB]                                         
Get:17 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe vlc-nox i386 2.0.5-0ubuntu0.12.04.1 [2,989 kB]                                         
Get:18 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-updates/universe libvlc5 i386 2.0.5-0ubuntu0.12.04.1 [50.8 kB]                                          
Get:19 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main linux-headers-3.2.0-36 all 3.2.0-36.57 [11.7 MB]                                          
Get:20 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main linux-headers-3.2.0-36-generic i386 3.2.0-36.57 [977 kB]                                  
Get:21 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main linux-libc-dev i386 3.2.0-36.57 [869 kB]                                                  
Get:22 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main aptdaemon-data all 0.43+bzr805-0ubuntu8 [163 kB]                                          
Get:23 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/universe python-aptdaemon-gtk all 0.43+bzr805-0ubuntu8 [1,678 B]                               
Get:24 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main python-aptdaemon.gtk3widgets all 0.43+bzr805-0ubuntu8 [14.8 kB]                           
Get:25 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/universe python-aptdaemon.gtkwidgets all 0.43+bzr805-0ubuntu8 [13.9 kB]                        
Get:26 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main python-aptdaemon.pkcompat all 0.43+bzr805-0ubuntu8 [29.0 kB]                              
Get:27 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main aptdaemon all 0.43+bzr805-0ubuntu8 [15.9 kB]                                              
Get:28 http://ftp.ussg.iu.edu/linux/ubuntu/ precise-proposed/main python-aptdaemon all 0.43+bzr805-0ubuntu8 [82.7 kB]                                       
Fetched 38.6 MB in 5min 25s (119 kB/s)                                                                                                                      
(Reading database ... 403943 files and directories currently installed.)
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb) ...
Unpacking replacement libdrm-nouveau1a ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1
Preparing to replace gnupg 1.4.11-3ubuntu2.1 (using .../gnupg_1.4.11-3ubuntu2.2_i386.deb) ...
Unpacking replacement gnupg ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/music-glossary.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-contributor.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-essay.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-usage.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-notation.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-extending.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-changes.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-snippets.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-learning.info.gz'
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.40+git1301100933.1dbd87~gd~p_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ibjsb4 on 2013-01-13
I am not finding any solution to this.  All my searches seem to eventually lead to the same place; "multiarch" support.  Sorry, but I am out of ideas :(

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

---

### Post by oldos2er on 2013-01-13
> **misomoravcik said:**
> I have the same problem.

```
sudo apt-get clean
sudo apt-get update
```

doesn't help and update manager gives the same error.

I have no idea how to solve this.

Please start your own thread, and give full details of your problem e.g. which version of Ubuntu you're using, any terminal output showing the problem, etc.

---

### Post by CinoxFellpyre on 2013-01-18
Bump.

---

### Post by CinoxFellpyre on 2013-01-22
Gonna bump with errors from the regular update manager:

```
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 403952 files and directories currently installed.) 
Preparing to replace libdrm-nouveau1a 2.4.39-0ubuntu1 (using .../libdrm-nouveau1a_2.4.41+git1301220934.303ca3~gd~p_i386.deb) ... 
Unpacking replacement libdrm-nouveau1a ... 
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau1a_2.4.41+git1301220934.303ca3~gd~p_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/i386-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.41+git1301220934.303ca3~gd~p_i386.deb 
Error in function: 
```

It seems when it hits the kernel (could be reading it wrong), suddenly everything takes a giant dump and falls apart. Sudo's also trashed so my account with sudo privileges doesn't happen, causing things like Skype to not access the pulseaudio server in order to work with the mic.

Everything else was able to update smoothly, so it's a package fault, but it's really messing with my permissions. Thankfully I can use sudo to start certain programs that need it but I really don't want to do that.

---

### Post by matt_symes on 2013-01-22
Hi

It wants to overwrite a file that is in another package. If you are sure there are no conflicts with the new file overwriting the old file then you can use

```
sudo dpkg  -i --force-overwrite /var/cache/apt/archives/libdrm-nouveau1a_2.4.41+git1301220934.303ca3~gd~p_i386.deb
```Kind regards

---

### Post by CinoxFellpyre on 2013-01-23
Ok, well it worked, now the other thing is I don't think sudo's working with Skype, because I can't voice chat with people without using sudo skype in terminal. I can hear them fine but if I'm not using sudo I can't talk with them back, meaning it's an issue with permissions between PulseAudio and the skype call.

Any way to fix this to remove the necessary hoops? After that I believe that'd be it.

---

### Post by oldos2er on 2013-01-24
Running Skype as root sounds dangerous to me. At any rate, you'd be better off starting a new thread, and marking this one 'Solved'.

---

