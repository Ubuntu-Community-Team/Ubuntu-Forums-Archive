---
title: "ubuntu 11.04 and catalyst 11.5, HOW???"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by Sagacious on 2011-05-10
ok so i went from 10.04 to 10.10 to 11.04 today and now i have the 11.5 catalyst drivers on my desktop. how do i go about installing them? obviously clicking on the file itself isnt going to work. nothing ever seems to work that way in linux. when i do that it says gedit has not been able to detect the character encoding, which is automatically detected and RETRY does not work. i have not seen a write up over this except one and it was about 2 pages of command lines and i cant see how that is necessary. isnt there a down and dirty easy way?

---

### Post by Sagacious on 2011-05-12
*bump* anyone?

---

### Post by hsoulen on 2011-05-12
> **Sagacious said:**
> ok so i went from 10.04 to 10.10 to 11.04 today and now i have the 11.5 catalyst drivers on my desktop. how do i go about installing them? obviously clicking on the file itself isnt going to work. nothing ever seems to work that way in linux. when i do that it says gedit has not been able to detect the character encoding, which is automatically detected and RETRY does not work. i have not seen a write up over this except one and it was about 2 pages of command lines and i cant see how that is necessary. isnt there a down and dirty easy way?

First, save the file to another directory (not your desktop) Downloads should be fine.

Next, open a command prompt and type:

```
cd Downloads
``` Or whatever folder you saved the file to

Then:

```
sudo chmod +x fileneme
``` Where filename is the name of the file you downloaded

Then type:

```
sudo ./filename
``` Where filename is the name of the file you downloaded

That should take care of it for you.

Cheers,

Hank

---

### Post by 3602 on 2011-05-12
**Step 1.**
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```and
```
sudo rm -rf /usr/share/lib32/fglrx
```Proceed.
**WARNING**: SOMEWHERE AFTER THIS YOU MIGHT SEE "_DKMS NOT NEEDED_" OR SOMETHING SIMILAR. **_DO NOT REMOVE_ THE DKMS PACKAGE OR ELSE NOTHING WILL INSTALL.**
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Then 
```
sudo reboot
```You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```Then
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```Wait. A Synaptic window might pop up if you're doing this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```then
```
sudo reboot
```then
```
fglrxinfo
```If the last command returnes "MESA" then report back.
Else enjoy.

---

### Post by belltown on 2011-05-12
I just tried installing the 11.5 catalyst driver. The install seemed to work. Switchable graphics seemed to work. fglxinfo show the intel driver in use when I switched to it and the ATI radeon driver when I switched to that driver.

However, when I try to play a flash video (hulu or YouTube) in full-screen mode, all I get is a blank white screen. In non-full-screen mode the video plays fine. On the Intel driver the video plays fine, just not on the Catalyst driver in full-screen mode.

---

### Post by 3602 on 2011-05-13
Um... Try Flash-Aid. Back a while ago my YT videos played real choppy, after applying Flash-Aid all went on fine even after two more manually installed fglrx-es.

---

### Post by belltown on 2011-05-13
I can get the full-screen flash videos to play if I uncheck the Enable Hardware Acceleration box in the flash settings menu.

---

### Post by rockstar2577 on 2011-05-14
3602, I didn't understand what I was typing, but that DID do the trick, and I have the latest Catalyst installed now.  Thank you :)

---

### Post by 3602 on 2011-05-15
Glad to be of help! If all is fine then you may mark this thread as "SOLVED". Use the "Thread Tools" button at the upper right corner. Cheers!

---

### Post by fogNL on 2011-05-20
Seeing that this thread isn't marked as Solved yet, and rather than starting a whole new thread, I thought I would post my question here.

I just did a fresh install of 11.04 64bit, and removed all fglrx drivers and installed 11.5 from ATI's website, that seemed to go well.  When I rebooted with Switchable graphics enabled in my bios, my boot of Ubuntu hard locks right before it should start the X server.

I booted Ubuntu in safe mode, checked my Xorg.log file, but it was blank.  Continuing with normal boot after safe, it drops me to a command line, running startx hard locks my system again, with no output going to my Xorg.log.  Any idea on what I could try?  Would I have better luck with 32bit over 64?

---

### Post by 3602 on 2011-05-20
Well... Disable switchable graphics then.
I don't think it can work in Linux... At least nVIDIA Optimus doesn't. Apparently you can somehow modify your DSDT file but it cannot be that simple since nVIDIA would have done it already.

---

### Post by fogNL on 2011-05-23
> **3602 said:**
> Well... Disable switchable graphics then.
I don't think it can work in Linux... At least nVIDIA Optimus doesn't. Apparently you can somehow modify your DSDT file but it cannot be that simple since nVIDIA would have done it already.

According to people, Catalyst 11.5 added in support for switchable graphics, and I've seen people with screenshots of Catalyst Control Centre for 11.5 to have a section for switchable graphics.  Reports are that it somewhat works, though you still have to restart the X server.  

I'll try and find where I seen those screen shots and ask there.

---

### Post by dokhidamo on 2011-05-28
> **3602 said:**
> **Step 1.**
```
sudo /usr/share/ati/fglrx-uninstall.sh
```
If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```
This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```
and
```
sudo rm -rf /usr/share/lib32/fglrx
```
Proceed.
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then 
```
sudo reboot
```
You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```
Then
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```
Wait. A Synaptic window might pop up if you're doing this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```
Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```
then
```
sudo reboot
```
then
```
fglrxinfo
```
If the last command returnes "MESA" then report back.
Else enjoy.

Problems. 
sudo /usr/share/ati/fglrx-uninstall.sh returns an error of "no such command" instead of "file not found"

sudo apt-get remove --purge fglrx* returns no errors, and just says 0 files added, 0 files deleted, 7 files unchanged

and "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old" returns "mv: cannot stat `/etc/X11/xorg.conf': No such file or directory"

Are these normal errors to get? Also, I had tried once before to install 11.5 drivers and it said the file "could not be read" in the terminal.

---

### Post by rollape on 2011-05-29
> **3602 said:**
> **Step 1.**
```
sudo /usr/share/ati/fglrx-uninstall.sh
```If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```and
```
sudo rm -rf /usr/share/lib32/fglrx
```Proceed.
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Then 
```
sudo reboot
```You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```Then
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```Wait. A Synaptic window might pop up if you're doing this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```then
```
sudo reboot
```then
```
fglrxinfo
```If the last command returnes "MESA" then report back.
Else enjoy.


Thank you!!! It was very helpful. You solved my problem!

---

### Post by 3602 on 2011-05-30
> **dokhidamo said:**
> Problems. 
sudo /usr/share/ati/fglrx-uninstall.sh returns an error of "no such command" instead of "file not found"

sudo apt-get remove --purge fglrx* returns no errors, and just says 0 files added, 0 files deleted, 7 files unchanged

and "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old" returns "mv: cannot stat `/etc/X11/xorg.conf': No such file or directory"

Are these normal errors to get? Also, I had tried once before to install 11.5 drivers and it said the file "could not be read" in the terminal.
Interesting... It would seem like you've never had any fglrx installed in the first place.
When you have the .run file you just need to do the 
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```
And try to install libqtgui4 at first.
See how it goes.

---

### Post by l0b0 on 2011-05-31
> **3602 said:**
> **Step 1.**
...

Yess, finally some instructions that worked! I've been stuck with 11.2 for ages now. Maybe you could spread the happiness to the [semi-official instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")?

---

### Post by 3602 on 2011-05-31
> **l0b0 said:**
> Yess, finally some instructions that worked! I've been stuck with 11.2 for ages now. Maybe you could spread the happiness to the [semi-official instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide")?
Uh... Much happy to be of help but I simply took the instructions from
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and modified it a tiny bit to work on Natty, so seriously I take no credit...

---

### Post by Shekibobo on 2011-06-01
I get as far as the last step without any apparent errors, but then I try and run the aticonfig and it fails.  Here's the output of my deb install:

```
$ sudo dpkg -i *.deb
(Reading database ... 180527 files and directories currently installed.)
Preparing to replace fglrx 2:8.850-0ubuntu1 (using fglrx_8.850-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:8.850-0ubuntu1 (using fglrx-amdcccle_8.850-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.850-0ubuntu1 (using fglrx-dev_8.850-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-dev ...
Setting up fglrx (2:8.850-0ubuntu1) ...
Loading new fglrx-8.850 DKMS files...
Building only for 2.6.38-8-generic
Building for architecture x86_64
Building initial module for 2.6.38-8-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.850-0ubuntu1) ...
Setting up fglrx-dev (2:8.850-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...

```


Any idea what I'm missing here?

---

### Post by 3602 on 2011-06-01
You should be seeing four packages instead of three like you've posted. Shouldn't there be a fglrx-modaliases?
Interesting... Could you be more specific as to how exactly aticonfig fails? Thanks.

---

### Post by Shekibobo on 2011-06-01
> **3602 said:**
> You should be seeing four packages instead of three like you've posted. Shouldn't there be a fglrx-modaliases?
Interesting... Could you be more specific as to how exactly aticonfig fails? Thanks.
It fails in that it doesn't exist.  I do only have three packages created from the setup.  I guess I'll try and rebuild the packages to see if I can get the last one.

---

### Post by Shekibobo on 2011-06-01
```
$ sudo sh ati-driver-installer-11-5-x86.x86_64.run --buildpkg Ubuntu/natty
[sudo] password for joshua: 
Created directory fglrx-install.t8oVkL
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.85......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/natty
Package /home/joshua/Desktop/fglrx_8.850-0ubuntu1_amd64.deb has been successfully generated
Package /home/joshua/Desktop/fglrx-dev_8.850-0ubuntu1_amd64.deb has been successfully generated
Package /home/joshua/Desktop/fglrx-amdcccle_8.850-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.t8oVkL

```

Looks like it's only building three packages, and doesn't seem to have a problem with that?

---

### Post by 3602 on 2011-06-01
OK... So what specific error do you get with the aticonfig?

---

### Post by Shekibobo on 2011-06-01
command not found. aticonfig isn't getting installed. Apparently it's the missing 4th deb package. I think I need to figure out how to get the 4th package to be built.

---

### Post by Shekibobo on 2011-06-01
Found the solution in their wiki

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot)

---

### Post by 3602 on 2011-06-01
I have an impression that aticonfig is not fglrx-modaliases related. The latter merely provides a list to Jockey.
It sure'd be nice if some expert folk came along...

---

### Post by sbraz on 2011-06-01
> **Shekibobo said:**
> ```
$ sudo sh ati-driver-installer-11-5-x86.x86_64.run --buildpkg Ubuntu/natty

Generating package: Ubuntu/natty
Package /home/joshua/Desktop/fglrx_8.850-0ubuntu1_amd64.deb has been successfully generated
Package /home/joshua/Desktop/fglrx-dev_8.850-0ubuntu1_amd64.deb has been successfully generated
Package /home/joshua/Desktop/fglrx-amdcccle_8.850-0ubuntu1_amd64.deb has been successfully generated
Removing temporary directory: fglrx-install.t8oVkL

```

Looks like it's only building three packages, and doesn't seem to have a problem with that?
the first probably silly thing i'd try is **--buildpkg Ubuntu/maverick**. should a "modaliases.deb" pop up, dpkg it then rebuild with Ubuntu/natty.

this might be unrelated but with 10.10 i had to manually patch fglrx to compile it under 2.6.39 (btw, good news! 3.0.0-rc1 worked too!).

---

### Post by 3602 on 2011-06-02
Kernel 3 is out? Wow. And I'm still on 35-25.
I believe his case is isolated as a couple of posters up there reported success. So...

---

### Post by needeffexor on 2011-06-15
> **Shekibobo said:**
> Found the solution in their wiki

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Aticonfig_not_found_after_installation_.26_.22module_does_not_exist.22_after_boot)

I had the same problem as Shekibobo.  Must be an issue with update-alternatives as ```
sudo update-alternatives --auto gl_conf
```worked for me.

Thank you 3602 for the great write-up.

---

### Post by 3602 on 2011-06-15
Glad to be of help.

(Wow, I can't believe this worked for so many people!)

---

### Post by hyperian on 2011-06-16
i get this when i try to install the ati catalyst drivers

> dpkg: dependency problems prevent configuration of xserver-xorg-video-ati-dbg:
 xserver-xorg-video-ati-dbg depends on xserver-xorg-video-ati (= 1:6.13.2+git20110107.0e432dff-0ubuntu0tormod); however:
  Version of xserver-xorg-video-ati on system is 1:6.14.0-0ubuntu4.

does this mean i need to downgrade my xserver?

getting such a huge headache after hours of trying...

---

### Post by 3602 on 2011-06-16
Interesting. Try removing said package.

---

### Post by smashweights on 2011-06-20
> **hsoulen said:**
> First, save the file to another directory (not your desktop) Downloads should be fine.

Next, open a command prompt and type:

```
cd Downloads
``` Or whatever folder you saved the file to

Then:

```
sudo chmod +x fileneme
``` Where filename is the name of the file you downloaded

Then type:

```
sudo ./filename
``` Where filename is the name of the file you downloaded

That should take care of it for you.

Cheers,

Hank

This solution worked perfectly for me using Catalyst 11.6 package from ATI on HP Envy 14 (Intel + HD5650).  Now have access to switchable graphics options through CCC (admin).  I couldn't simply click the install package to run.  Requires restart to change GPU.
Of note, package install option I selected was #1 the generic install.

---

### Post by Jerome22 on 2011-06-20
> **3602 said:**
> **Step 1.**
```
sudo /usr/share/ati/fglrx-uninstall.sh
```
If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```
This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```
and
```
sudo rm -rf /usr/share/lib32/fglrx
```
Proceed.
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then 
```
sudo reboot
```
You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```
Then
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```
Wait. A Synaptic window might pop up if you're doing this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```
Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```
then
```
sudo reboot
```
then
```
fglrxinfo
```
If the last command returnes "MESA" then report back.
Else enjoy.
Thanks a lot for your help. I waisted a lot of time trying to oget my hybrid graphic working, and now with catalyst driver I can easily switch !!
Thanks again !

---

### Post by 3602 on 2011-06-20
Hey now. CCC 11.6 is out, but since I re-installed the entire system to *not* game, I'm not installing it for a while. If you want to upgrade, the above steps *should most probably* work.

---

### Post by elldirash on 2011-06-24
Hello.

I tried going through these steps to get switchable graphics working on a Timeline 8371G. I can complete all of the suggested steps with no error messages. But when rebooting, the screen just blinks a few times when trying to start X (i guess) and crashes. If i shift to a different terminal and type startx i get the following output:

Backtrace:
[    84.846] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[    84.846] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[    84.846] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb786b40c]
[    84.846] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs110_atiddxPreInit+0x1468) [0xb6aa0118]
[    84.846] 4: /usr/bin/X (InitOutput+0x835) [0x80b7cf5]
[    84.846] 5: /usr/bin/X (0x8048000+0x1a675) [0x8062675]
[    84.846] 6: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb7588e37]
[    84.846] 7: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[    84.846] Segmentation fault at address (nil)
[    84.846] 
Caught signal 11 (Segmentation fault). Server aborting
[    84.846] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    84.846] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    84.846] 
[    84.857]  ddxSigGiveUp: Closing log

I have the full log file if anyone wants to see it. Does anyone have a clue about what could be going wrong?

---

### Post by ibpa on 2011-07-02
> **3602 said:**
> **Step 1.**
```
sudo /usr/share/ati/fglrx-uninstall.sh
```
If this returns "no such file or directory" it's fine. Proceed.
**Step 2.**
```
sudo apt-get remove --purge fglrx*
```
This will *probably* return a couple of warnings: */usr/share/lib/fglrx* and */usr/share/lib32/fglrx *not empty. You do:
```
sudo rm -rf /usr/share/lib/fglrx
```
and
```
sudo rm -rf /usr/share/lib32/fglrx
```
Proceed.
**Step 3. COPY THIS DOWN on some papers before doing it!**
Reboot. When in the purple boot screen with flashing dots, press F1 key to get into the emergency recovery board (white-on-black screen). Do:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then 
```
sudo reboot
```
You will get a GUI.
**Step 4.**
*cd* into whatever dir you have the .run file.
You might want to
```
sudo apt-get install libqtgui4
```
Then
```
sudo sh (your installation file).run --buildpkg Ubuntu/natty
```
Wait. A Synaptic window might pop up if you're doing this for the first time. Let it go away. 
Later you'll see the xterm returning four packages built.
Now
```
sudo dpkg -i *.deb
```
Wait.
**Step 5.**
```
sudo aticonfig --initial -f
```
then
```
sudo reboot
```
then
```
fglrxinfo
```
If the last command returnes "MESA" then report back.
Else enjoy.

Thanks, working with catalyst 11.6.!!!

---

