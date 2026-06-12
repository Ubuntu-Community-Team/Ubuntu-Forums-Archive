---
title: "Black Screen after fresh installation of Kubuntu 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Neremor on 2010-05-01
Hello!

After the upgrade from 9.10 to 10.04 resulted in a black screen after reboot, I decided to don't waste more time, backed up my data and made a fresh installation.

First Issue [solved]: After I inserted the Kubuntu 10.04 Live-CD and started the system, I got to the CD's boot-mode selection menu. When I selected "Install Kubuntu", I got the Kubuntu bootscreen, but the system hang up then. I was able to solve this problem through pressing F6 in the boot-mode selection menu and setting "nomodeset". I also had to remove "quit splash" from the boot-entry line. Afterwards the installation process was fine.


Second Issue: I wanted to boot my new installated system, but, off course, got the blank screen again. So I edited the Grub-entry for recovery mode in the grubmenu (replaced "quit splash" with "nomodeset") and booted into recovery mode. I selected "netroot", and installed the proprietary nvidia-drivers with "apt-get install nvidia-current". Afterwards I ran "nvidia-xconfig" to generate the xorg.conf. To solve the blank screen issue, I edited the /boot/grub/grub.cfg the same way I described above and rebooted. Now I don't get a blank screen anymore, but I also don't get an XServer. The system boots now (off course without splash and "unquit"), but drops me into the tty1... When I type "sudo service kdm start", I get into KDM and can login, but I get many errors and crash-reports there. I also don't have any internet. I only have internet when booting in recovery mode and select "netroot".

I'm a bit surprised that Ubuntu released a LTS-Version that causes so much trouble (I've searched the forum and it seems that I'm not the only one with such big problems). Has Ubuntu droped support for NVidia-users?

Thanks in advance for every help!
Greetings,

Jonathan

EDIT: When starting X via "sudo service kdm start", I get to the KDM login screen, but when entering username and password and pressing return, I get the error "Unable to start ksmserver. Check your installation!"... Afterwards I'm brought back to the login screen...

---

### Post by elcorazon on 2010-05-01
Same problem here - some console window and message "Could not start ksmserver. Check your installation."

I upgraded from 9.10 without bigger issues except I could not install the native NVIDIA-Linux-x86_64-195.30 binary driver downloaded from nvidia.com. But I could login to a low-res gnome session and activate the restricted driver "NVIDIA accelerated graphics driver". After doing that I now get a fully functional gnome session, kdm and gdm but no kde session.

Any suggestions?

---

### Post by elcorazon on 2010-05-01
Guess I found the reason in ~/.xsession-errors:
```
Xsession: X session started for m at Sat May  1 13:23:56 CEST 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
Version mismatch detected between the NVIDIA libGL.so
and libGLcore.so shared libraries (libGL.so version:
195.30; libGLcore.so version: 195.36.15).
Please try reinstalling the NVIDIA driver.kdeinit4_wrapper: Warning: connect(/home/m/.kde/socket-tiger/kdeinit4__0) failed: : Connection refused
Version mismatch detected between the NVIDIA libGL.so
and libGLcore.so shared libraries (libGL.so version:
195.30; libGLcore.so version: 195.36.15).
Please try reinstalling the NVIDIA driver.startkde: Could not start ksmserver. Check your installation.
startkde: Shutting down...
kdeinit4_wrapper: Warning: connect(/home/m/.kde/socket-tiger/kdeinit4__0) failed: : Connection refused
Error: Can not contact kdeinit4!
startkde: Running shutdown scripts...
startkde: Done.
```

The solution is simple (at least that's what worked in my case):
```
cd /usr/lib/
rm libGL.*
```
(make shure not to skip the dot - otherwise files like libGLU.so.1 get deleted ;)

That removes the libs of the old (native nvidia) installation. The libs of the "NVIDIA accelerated graphics driver" seem to be located in /usr/lib/nvidia-current/

---

### Post by Neremor on 2010-05-01
Congratiulations that it worked for you, but I cant really imagine that it works for me... Because I did a "apt-get install nvidia-current" directly after a fresh installation without some graphic card drivers installed so there should be nothing old to remove...

All I would like to now is, whether there is an official fix for this problem or not... Many people have this problem, so I think the official ubuntu package maintainers should provide an updated kernel-compatible nvidia-current driver... and if this isn't possible, provide the old driver as default which was working all right with the current kernel release...

Thanks in advance for further help. greetings,
Jonathan

---

### Post by elcorazon on 2010-05-01
What is the content of your ~/.xsession-errors file?

---

### Post by Neremor on 2010-05-01
Well the .xsession-errors-file is empty, because the XServer isn't starting... When starting it manually with "sudo start kdm", it contains many DBus-errors, but I think that isn't causing the problem.

I did a fresh installation right now to see whether I just had bad luck with my first installation, but I still only get to the ttyX consoles and only have internet when booting in recovery mode and then select netroot...

---

### Post by elcorazon on 2010-05-01
Hi Neremor,

this is what you wrote before..
> **Neremor said:**
> Hello!
EDIT: When starting X via "sudo service kdm start", I get to the KDM login screen, but when entering username and password and pressing return, I get the error "Unable to start ksmserver. Check your installation!"... Afterwards I'm brought back to the login screen...

Does this still apply? Because if so, the problem is not the XServer itself but some KDE lib.

Otherwise if the Xserver does not start - what does /var/log/Xorg.0.log say?

---

### Post by Neremor on 2010-05-01
Well I think the KSMServer wasn't able to start because I disabled KSM with the boot-entry modification "nomodeset"... This is at least what I read in the internet.

I did a fresh install again, and have the same problem. I only got to the ttys again, had no internet, installed the nvidia-driver via the netroot in recovery mode, and tried after a reboot "sudo start kdm" again. KDM is starting and I'm able to login, but after Plasma is loaded, I get many krash reports of mainly two kde-apps: KNetworkManager and PolicyKit1... Off course, I still don't have Internet at this point and the graphical interface won't survive long because the huge amount of crash reports bring the xserver down again.

Edit: The /var/log/Xorg.0.log doesn't contain errors or warnings...

---

### Post by renatkh on 2010-05-01
> **elcorazon said:**
> 
The solution is simple (at least that's what worked in my case):
```
cd /usr/lib/
rm libGL.*
```
(make shure not to skip the dot - otherwise files like libGLU.so.1 get deleted ;)


The solution worked for me! Thanks!!!

---

### Post by Neremor on 2010-05-02
I tried what you said, but I don't have a file called libGL.*... I think it's because I did a fresh installation...

---

### Post by elcorazon on 2010-05-02
> **Neremor said:**
> I tried what you said, but I don't have a file called libGL.*... I think it's because I did a fresh installation...

Yes, the files where remainders of the native NVIDIA driver installation. Also the problem you seem to have now is different to your first post.

> **Neremor said:**
> Well I think the KSMServer wasn't able to start because I disabled KSM with the boot-entry modification "nomodeset"... This is at least what I read in the internet.

I did a fresh install again, and have the same problem. I only got to the ttys again, had no internet, installed the nvidia-driver via the netroot in recovery mode, and tried after a reboot "sudo start kdm" again. KDM is starting and I'm able to login, but after Plasma is loaded, I get many krash reports of mainly two kde-apps: KNetworkManager and PolicyKit1... Off course, I still don't have Internet at this point and the graphical interface won't survive long because the huge amount of crash reports bring the xserver down again.

Edit: The /var/log/Xorg.0.log doesn't contain errors or warnings...

Yes, it seems your Xserver starts without problems. Do you have a completely fresh installation or did you mount your old /home? If so, I'd try to rename or remove the old ~/.kde directory to get a fresh one. If that does not help, I have no idea.. maybe you should check some logfiles like /var/log/syslog

Hope that helps, good luck! :p

---

### Post by hrocks on 2010-05-04
The solution is simple (at least that's what worked in my case):
```
cd /usr/lib/
rm libGL.*
```
(make shure not to skip the dot - otherwise files like libGLU.so.1 get deleted ;)

That removes the libs of the old (native nvidia) installation. The libs of the "NVIDIA accelerated graphics driver" seem to be located in /usr/lib/nvidia-current/[/QUOTE]

This worked for me too.
Thanks.:)

---

### Post by jazzcommunication on 2010-05-09
this is not a specific ubuntu/kubuntu problem, but a kde4.3 problem
because i tried many life cd's kde based and all have the same problem
tested : mandriva 2010 kde, fedora 2010 kde, pclinuxos kde...it all fails the same way.
even when you install kde after ubuntu(gnome)10.04 is running well, the if you like to start a kde session , it fails
Simply wait and see what kde development goes doing

---

### Post by _guybrush_ on 2010-05-10
> **Neremor said:**
> Hello!

After the upgrade from 9.10 to 10.04 resulted in a black screen after reboot, I decided to don't waste more time, backed up my data and made a fresh installation.

First Issue [solved]: After I inserted the Kubuntu 10.04 Live-CD and started the system, I got to the CD's boot-mode selection menu. When I selected "Install Kubuntu", I got the Kubuntu bootscreen, but the system hang up then. I was able to solve this problem through pressing F6 in the boot-mode selection menu and setting "nomodeset". I also had to remove "quit splash" from the boot-entry line. Afterwards the installation process was fine.


Second Issue: I wanted to boot my new installated system, but, off course, got the blank screen again. So I edited the Grub-entry for recovery mode in the grubmenu (replaced "quit splash" with "nomodeset") and booted into recovery mode. I selected "netroot", and installed the proprietary nvidia-drivers with "apt-get install nvidia-current". Afterwards I ran "nvidia-xconfig" to generate the xorg.conf. To solve the blank screen issue, I edited the /boot/grub/grub.cfg the same way I described above and rebooted. Now I don't get a blank screen anymore, but I also don't get an XServer. The system boots now (off course without splash and "unquit"), but drops me into the tty1... When I type "sudo service kdm start", I get into KDM and can login, but I get many errors and crash-reports there. I also don't have any internet. I only have internet when booting in recovery mode and select "netroot".

I'm a bit surprised that Ubuntu released a LTS-Version that causes so much trouble (I've searched the forum and it seems that I'm not the only one with such big problems). Has Ubuntu droped support for NVidia-users?

Thanks in advance for every help!
Greetings,

Jonathan

EDIT: When starting X via "sudo service kdm start", I get to the KDM login screen, but when entering username and password and pressing return, I get the error "Unable to start ksmserver. Check your installation!"... Afterwards I'm brought back to the login screen...
Hi Neremor,

I do have the exact same symptoms as you (all of them). Have you found a solution yet? If yes, I would be glad if you could share it with me...

Thanks in advance,

guybrush

---

### Post by joonate on 2010-05-25
Same symptoms here too!!!

---

### Post by steeg on 2010-05-30
Hi,
I found this BLOG (after some very very boring search) and like to provide some short conclusion to enable others having the same problem to resolve the "KDEINIT4_WRAPPER CONNECTION REFUSED" quickly

I have Debian Etch, but I guess this applies to other linux distributions (esp. Ubuntu) as well.

HERE IS THE PROBLEM
startkde (not launched from kdm, but from an xinit etc.) runs under ROOT but not under normal user privileges, the error under normal user is::
kdeinit4_wrapper: Warning: connect(/home/steeg/.kde/socket-Goliath/kdeinit4__0) failed: : Connection refused

HERE IS THE SOLUTION
1.) (as already mentioned somewhere above) /usr/lib/libGL.* need to be removed (or renamed)
$ rm -f /usr/lib/libGL.*

2.) startkde will then not find libGL.so.1 (at least at my installation) because it is located as /usr/lib/nvidia/libGL.so.1.2.xlibmesa (or something similar, look to your /usr/lib/nvidia directory!)
$ cd /usr/lib
$ ln -sf ./nvidia/libGL.so.1.2.xlibmesa libGL.so.1

You may alternatively set the link (ln -sf ..) in your /usr/lib/nvidia, but then you need also to add /usr/lib/nvidia to your /etc/ld.so.conf (and reboot resp. issue a $ ldconfig -a)

I hope this helps,
 Martin

---

### Post by kennethx on 2011-03-23
> **elcorazon said:**
> Guess I found the reason in ~/.xsession-errors:
```
Xsession: X session started for m at Sat May  1 13:23:56 CEST 2010
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
Version mismatch detected between the NVIDIA libGL.so
and libGLcore.so shared libraries (libGL.so version:
195.30; libGLcore.so version: 195.36.15).
Please try reinstalling the NVIDIA driver.kdeinit4_wrapper: Warning: connect(/home/m/.kde/socket-tiger/kdeinit4__0) failed: : Connection refused
Version mismatch detected between the NVIDIA libGL.so
and libGLcore.so shared libraries (libGL.so version:
195.30; libGLcore.so version: 195.36.15).
Please try reinstalling the NVIDIA driver.startkde: Could not start ksmserver. Check your installation.
startkde: Shutting down...
kdeinit4_wrapper: Warning: connect(/home/m/.kde/socket-tiger/kdeinit4__0) failed: : Connection refused
Error: Can not contact kdeinit4!
startkde: Running shutdown scripts...
startkde: Done.
```

The solution is simple (at least that's what worked in my case):
```
cd /usr/lib/
rm libGL.*
```
(make shure not to skip the dot - otherwise files like libGLU.so.1 get deleted ;)

That removes the libs of the old (native nvidia) installation. The libs of the "NVIDIA accelerated graphics driver" seem to be located in /usr/lib/nvidia-current/

Thank you! This worked like a charm!

---

