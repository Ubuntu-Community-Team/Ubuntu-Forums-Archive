---
title: "Dell c840 - Gutsy fresh install: black screen"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Sengkim on 2007-10-27
Hi all,

Can as well become one with the rest :-) I've just installed Gutsy on my Del c840 laptop (Geforce 440 Go gfx) and all went well. Boots nice but when installing the restricted drivers (as proposed), the screen goes black. Same when installing 'envy'.

I've tried stuff posted here on the boards but no solutions (yet).

BB
Peter

---

### Post by taurus on 2007-10-27
Boot into recovery mode from GRUB menu and edit /etc/X11/xorg.conf.

```
nano -Bw /etc/X11/xorg.conf
```
Scroll down until you get to the section about Driver for your graphic card.  Change the "**nvidia**" back to "**nv**" and save it with <Ctrl>o and exit with <Ctrl>x.  

Reboot and see if X is running again.

```
shutdown -r now
```

---

### Post by Sengkim on 2007-10-27
Yep, did that. Screen is visible again. But no fancy 3D stuff with the 'old' driver :-)

But thanks for helping!

BB
Peter

---

### Post by taurus on 2007-10-27
Perhaps you need to install the legacy nvidia driver instead of the new one!

---

### Post by Sengkim on 2007-10-28
Hi,

I installed the legacy drivers but although the screen did not go black, I could not enable compiz-fusion. When I do, Gutsy installs the regular driver and *poef* black screen again.

It's really a pity :(

BB
Peter

---

### Post by daffyduck on 2007-10-29
Hi Peter,

I encountered the same problem with my C840 this morning, but using [this info]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065") (copied below) I was able to boot into X. It boots into this funky mode though, with rainbow stribes on the right side of the screen and the top portion duplicated in the bottom - I'm currently trying to resolve this so let me know if you have the same problem (and find a way to fix it!) :)

> Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not recieving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a known bug, and can be resolved by editing your /etc/X11/xorg.conf file:

    *  Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
    *  Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
    *  Find the line that says Section "Screen"
    *  Insert a new line that says Option "UseDisplayDevice" "DFP".
    *  Save the file. If you had to restart into revocery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.


---

### Post by RxRitalin on 2007-10-30
> **daffyduck said:**
> Hi Peter,

I encountered the same problem with my C840 this morning, but using [this info]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#head-f5e28596120b064aca976f5c8a6ddacfee0d5065") (copied below) I was able to boot into X. It boots into this funky mode though, with rainbow stribes on the right side of the screen and the top portion duplicated in the bottom - I'm currently trying to resolve this so let me know if you have the same problem (and find a way to fix it!) :)

Hello there, I know how big of a pain in the *** this is as I ran into this on my very first experience with linux on the very same box you are running on. What a way to start hu?

Well I do have the answer for you. The problem is that after you install the n vidia driver the EDID reports false information to your system. It turns out that this is a known issue and it seems that the EDID in the LCD is actually no good. But fear not you can use the custom EDID I have uploaded below and after a few changes to your xorg.conf you will be ready to roll. 

Ok lets start with the custom EDID. Download the attached file "nvnew.raw.tar.gz" below, Then unzip the contents to your desktop. Now open up your console and type in "sudo nautilus" followed by your password. This will allow you to access your system files as an administrator. Ok, so lets click on file system on the left side of Nautilus and then browse to /ect/X11/ . Paste the nvnew.raw into your X11 folder. Before you close the Nautilus window, double click on xorg.conf. Ok be careful here not to change anything that you are unsure of. Next scroll to           Section "Device"

Copy  the following from here :

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 440 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
        Option          "UseDisplayDevice" "DFP-0"
        Option          "CustomEDID" "DFP-0:/etc/X11/nvnew.raw"
	Option		"NoLogo"	"True"
EndSection

Highlight and paste over yours in the xorg.conf 

*** Make sure not to erase or paste over any other portion of the xorg file or your world will come to and end.***

After you have all of that finished save the xorg file and then you need to hit ctrl+alt=backspace and you should be good to go.

---

### Post by Sengkim on 2007-10-30
RxRitalin,your solution worked fine for me!! Thanks!

---

### Post by dboot on 2007-11-01
I have the same laptop. After following your post, RxRitalin, I was able to install the legacy nvidia driver for the first time. Thanks!

However, I still can't enable 3D effects. I get this error when select "Normal" after going to System -> Preference -> Appearance: Desktop effects could not be enabled.

Any ideas? I would really like to get Compiz Fusion working. Do you think I'm having trouble because of the legacy drivers I'm using?

Driver: nvidia 96.xx downloaded from nvidia website
Restricted Drivers: Enabled
Nvidia X Server Settings: Enabled under System
Xorg file setup as suggested by RxRitalin and changed after nVidia driver installed

Thanks for any suggestions!

---

### Post by Sengkim on 2007-11-01
dboot,

I'm not using the legacy drivers. Now, since I'm only new at this I can't say exactly what I did but from my memory, I tried installing the restricted drivers, didn't work. Installed envy, didn't work. The removed all nvidia drivers again using envy en reapplied restricted drivers. didn't work.
Then did the RXRitalin trick and pats it worked.
After that I was able to use the complete setting for compiz. Then I looked on the web on how to activate the 3D cube thing and I found out that you need to install some extra things to be able to acces the settings for compiz itself.

Hope this helps....no much though but as said, it's all new :-)

BB
Peter

---

### Post by RxRitalin on 2007-11-01
Sorry but im actually new to linux... I havent been running it for all that long. maybe a few months. 

I just used the restricted driver manager to install my video drivers. That of course leads to the black screen issue. I loaded up the Ubuntu Boot CD > Console > Sudo Nautilus > changed the xorg to display from the internal LCD. This gets you to the corrupted EDID issue once you reboot and load the OS from your HDD. Thats what I showed how to resolve above... 

I would try installing the drivers suggested through the restricted driver manager. But again Im a linux noob so I may be missing something.

---

### Post by dboot on 2007-11-01
It seems like we're all in a similar situation. Thanks for the tips. Maybe someone else has been able to figure out the problem.

After a clean install, I followed your instructions successfully to get the restricted drivers working. However, I still can't get 3D support enabled for Compiz Fusion.

Have either of you tried to get it by following these instructions:

```
 Advanced Desktop Effects (Compiz Fusion)

To enable desktop effects, turn them on in:

 System > Preferences > Appearance > Visual Effects

To customize options, install the configuration tool:

 sudo apt-get install compizconfig-settings-manager

And either choose "Custom" in the above Visual Effects menu, or:

 System > Preferences > Advanced Desktop Effects Settings

``` 
From [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Desktop]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Desktop").

---

