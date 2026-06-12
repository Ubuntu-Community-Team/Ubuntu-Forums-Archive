---
title: "nVidia GeForce 310M support"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by gaurav_kukreja on 2010-01-28
Hi,

I am Gaurav. I recently bought a sony vaio laptop, with nVidia GeForce 310M device.

I am new, and not very good with ubuntu. I downloaded a driver version 185, and installed, after installing which, I could not get any display at all. After trying to repair, in vain, I had to reinnstall the whole system.

I really need the correct drivers. I can see a version 190.42 of nvidia drivers, but that doesnt list my device model number, and so im not sure, whether this should work. Someone, also please tell me how do I repair, if I mess while trying this driver out?

Thanks already.

---

### Post by aoxo on 2010-01-28
I am having the same problem with the proprietary nvidia driver on my vaio. The graphics card is a Nvidia GeForce 310m. When I installed the proprietary 185 driver (reccomended in hardware drivers), the laptop then would not start X at bootup and the screen went just black. After reinstalling 9.10, X now starts up but with 3d disabled...Any help would be much appreciated  :confused: as I am a bit new to the ubuntu experience.

edit: 
just to clarify, the generic "nv" driver is working properly, but with 3d acceleration disabled. If I install the nvidia 185 restricted driver, the display goes black after selecting the linux option in grub (dual booting with win 7). The login sound still plays, but that's it.

any help at all would be tremendous, as none of the solutions I found on these forums has worked for me.

---

### Post by Classic_gamer on 2010-01-29
Over at nvnews.net, there was a post about this same issue, but with the G210M. See if following these steps help you out: [http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

Today I bought a Sony Vaio CW (with a G310M) and will be setting it up with Linux later tonight. When I get things figured out, I'll post back to confirm whether or not the post I linked above fixes this issue.

---

### Post by aoxo on 2010-01-30
@classic_gamer: thanks, following the steps on the above link solved my problem :] I am now running the proprietary nvidia-185 driver with 3d enabled. I had to reinstall the 185 driver first through synaptic. The program softMCCS kept crashing in windows 7 for some reason, but luckily I found someone who had uploaded their EDID to the forums :] that download can be found [here]("http://ubuntuforums.org/showthread.php?t=1369420") if anyone else needs it.

---

### Post by ggankhuy on 2010-01-30
Hey Gaurav
How did you download the driver for your 330m chip? Was it through synaptic pck mngr or some other place online.
I recently purchase VPCC series VAIO and ubuntu is super slow because of the driver problem. I dont see 300m series driver for linux-32 on Nvidia website. 
Browsing through packages I found nvidia-glx-180 with the description that 'says Nvidia binary Xorg driver'. I am using 9.10 ubuntu. Thanks!

---

### Post by leo.ttl on 2010-02-10
The EDID file also corrected my problem on my new VAIO VPCF111FX, however I cant get an external monitor or projector to work, and I suspect that the EDID file specification is causing some troubles here, has anybody made the dual monitor work?

---

### Post by azizmulhim on 2010-03-10
leo.ttl


What steps to install nvidia driver (which version) & can you please share your EDID  because I have sony laptop with same video card 310M but with 13" inch screen. 

Thanks,

---

### Post by soad6 on 2010-03-18
Ok so i have a new a505 -6033 laptop and ubuntu doesnt recognize half the things. I really need the GPU from this card so i can use pyrit. If anyone has any ideas besides asking nvidia or using an older driver unless you can explain how to do it simply. Thanx for any help if anyone can help... ](*,) ive hit a wall and had to return to windows... please help i need aircrack-ng and pyrit!!

---

### Post by shaun_54au2 on 2010-03-31
[SIZE=3]For Sony Vaio VPCCW series laptops:

1:KSDownload [_***>[SIZE=3]sonycw.txt[/SIZE]<***_]("http://ubuntuforums.org/attachment.php?attachmentid=141988&d=1262341882") to your "/home/**[SIZE=2]username[/SIZE]**/"  folder:
   [/SIZE][SIZE=3]
2:KSRename *"sonycw.txt"* *to* *"sonycw.bin*"

3:KSOpen terminal and paste these commands.

*sudo mv /home/[COLOR=DarkGreen]**[SIZE=2]your_user_name_here[/SIZE]**[/COLOR]*[/SIZE][SIZE=3]*/sonycw.bin /etc/X11/*[/SIZE]
[SIZE=3] 
   [I]sudo touch /etc/X11/xorg.conf
[/I]
   *sudo gedit /etc/X11/xorg.conf*

4:KSPaste this in xorg.conf and then _save_:

Section "Device"
         Identifier          "Device0"
         Driver              "nvidia"
         VendorName         "NVIDIA Corporation"
         Option             "ConnectedMonitor"   "DFP-0"
         Option             "CustomEDID"          "DFP-0:/etc/X11/sonycw.bin"
      EndSection

5:KSInstall ***[nvidia-glx-185]("http://packages.ubuntu.com/karmic/nvidia-glx-185")***

6:KSRestart the computer and your done





[/SIZE]***[SIZE=3]*******Kudos to [_egghead3_]("http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2") for this solution.[/SIZE]***
[SIZE=3] 

Original Links:

[http://ubuntuforums.org/showthread.php?t=1369420](http://ubuntuforums.org/showthread.php?t=1369420)

[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

[/SIZE]

---

### Post by sti2444 on 2010-04-13
> **shaun_54au2 said:**
> [SIZE=3]For Sony Vaio VPCCW series laptops:

1:KSDownload [_***>[SIZE=3]sonycw.txt[/SIZE]<***_]("http://ubuntuforums.org/attachment.php?attachmentid=141988&d=1262341882") to your "/home/**[SIZE=2]username[/SIZE]**/"  folder:
   [/SIZE][SIZE=3]
2:KSRename *"sonycw.txt"* *to* *"sonycw.bin*"

3:KSOpen terminal and paste these commands.

*sudo mv /home/[COLOR=DarkGreen]**[SIZE=2]your_user_name_here[/SIZE]**[/COLOR]*[/SIZE][SIZE=3]*/sonycw.bin /etc/X11/*[/SIZE]
[SIZE=3] 
   [I]sudo touch /etc/X11/xorg.conf
[/I]
   *sudo gedit /etc/X11/xorg.conf*

4:KSPaste this in xorg.conf and then _save_:

Section "Device"
         Identifier          "Device0"
         Driver              "nvidia"
         VendorName         "NVIDIA Corporation"
         Option             "ConnectedMonitor"   "DFP-0"
         Option             "CustomEDID"          "DFP-0:/etc/X11/sonycw.bin"
      EndSection

5:KSInstall ***[nvidia-glx-185]("http://packages.ubuntu.com/karmic/nvidia-glx-185")***

6:KSRestart the computer and your done





[/SIZE]***[SIZE=3]*******Kudos to [_egghead3_]("http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2") for this solution.[/SIZE]***
[SIZE=3] 

Original Links:

[http://ubuntuforums.org/showthread.php?t=1369420](http://ubuntuforums.org/showthread.php?t=1369420)

[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

[/SIZE]

hey guys ,i can confirm this method for the vaio S series vpcs117gg.

thanks so much 

R

---

### Post by cstahl on 2010-04-14
thank you so very much

---

### Post by sdahale on 2010-04-19
> **shaun_54au2 said:**
> [SIZE=3]For Sony Vaio VPCCW series laptops:

1:KSDownload [_***>[SIZE=3]sonycw.txt[/SIZE]<***_]("http://ubuntuforums.org/attachment.php?attachmentid=141988&d=1262341882") to your "/home/**[SIZE=2]username[/SIZE]**/"  folder:
   [/SIZE][SIZE=3]
2:KSRename *"sonycw.txt"* *to* *"sonycw.bin*"

3:KSOpen terminal and paste these commands.

*sudo mv /home/[COLOR=DarkGreen]**[SIZE=2]your_user_name_here[/SIZE]**[/COLOR]*[/SIZE][SIZE=3]*/sonycw.bin /etc/X11/*[/SIZE]
[SIZE=3] 
   [I]sudo touch /etc/X11/xorg.conf
[/I]
   *sudo gedit /etc/X11/xorg.conf*

4:KSPaste this in xorg.conf and then _save_:

Section "Device"
         Identifier          "Device0"
         Driver              "nvidia"
         VendorName         "NVIDIA Corporation"
         Option             "ConnectedMonitor"   "DFP-0"
         Option             "CustomEDID"          "DFP-0:/etc/X11/sonycw.bin"
      EndSection

5:KSInstall ***[nvidia-glx-185]("http://packages.ubuntu.com/karmic/nvidia-glx-185")***

6:KSRestart the computer and your done





[/SIZE]***[SIZE=3]*******Kudos to [_egghead3_]("http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2") for this solution.[/SIZE]***
[SIZE=3] 

Original Links:

[http://ubuntuforums.org/showthread.php?t=1369420](http://ubuntuforums.org/showthread.php?t=1369420)

[http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=140482&page=2)

[/SIZE]


Great Suggestion ....worked like charm on my Vaio CW23 VPCCW23EN

---

### Post by wirecricket on 2010-04-20
Hi everybody!
First, excuse me for my english)!
I bought an Asus k50ie sx053d laptop with nvidia geforce 310m graphic card and i have problem with 3d effects on ubuntu 9.10 too. I already tried what you wrote above (i mean download and change that sonycw.txt to .bin and edit xorg.conf and after that install nvidia glx 185 driver) but it's freeze on ubuntu bootscreen. Do you know any solve?

---

### Post by luopio on 2010-04-20
thanks for the solution. I'd like to add

that this also [SIZE="4"]**works on Sony Vaio S-series**[/SIZE] (S11V9E) w/ a 13 inch screen using the exact same sonycw.txt

(although it feels a bit odd, since the screens are different).

I also posted a related bug (#567076)

---

### Post by luopio on 2010-04-20
> **wirecricket said:**
> Hi everybody!
First, excuse me for my english)!
I bought an Asus k50ie sx053d laptop with nvidia geforce 310m graphic card and i have problem with 3d effects on ubuntu 9.10 too. I already tried what you wrote above (i mean download and change that sonycw.txt to .bin and edit xorg.conf and after that install nvidia glx 185 driver) but it's freeze on ubuntu bootscreen. Do you know any solve?

Does it freeze just after Grub? If it does you might have the issue I had during install, where you need to put nouveau.modeset=0 to the kernel parameters.

If it freezes later on then you better boot in recovery mode from grub and post the output of
```

grep "EE" /var/log/Xorg.0.log.old

```

---

### Post by wirecricket on 2010-04-20
It freezes on the window when i get that brown window with that vertical running white sign.

---

### Post by iKirby on 2010-04-20
im using the same video card on my toshiba a505-s6020..

im kinda new to ubuntu so i installed it on vmware first and it worked fine.. i forgot that the vmware has its own drivers so it wont be the same when i make a fresh install of ubuntu...

i highly doubt that toshiba would make a driver for linux/ubuntu so i guess i have to wait til someone comes up with a fix or driver itself.

---

### Post by rampage355 on 2010-04-21
This is how I got my NVIDIA drivers working flawlessly

[LIST=1]
[*]let's get that problematic NVIDIA card working. Go to the NVIDIA web-site and download the latest driver. If you have installed the 64-bit (AMD64) variant of Karmic, use the first link - otherwise use the second:
64-bit Ubuntu: [http://www.nvidia.com/object/linux_d...195.36.15.html](http://www.nvidia.com/object/linux_d...195.36.15.html)
32-bit Ubuntu: [http://www.nvidia.com/object/linux_d...195.36.15.html](http://www.nvidia.com/object/linux_d...195.36.15.html)
[*]I'm going to assume that this file is downloaded into the "/home/someuser/Downloads" directory.Restart your machine. When the GRUB menu appears, select the recovery mode for the most recent Kernel version installed (second option from the top, typically). The machine boots and eventually brings up a menu. Select the top menu option (resume). This will bring you to a console login - log in.
[*]When you get to a command prompt, issue the following command to install the NVIDIA drivers:
64-bit Ubuntu:
[/LIST]
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```
32-bit Ubuntu:
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86-195.36.15-pkg1.run
```

Check the version numbers to ensure they match the version you downloaded. Also don't forget to replace "someuser" with your user name.
Thanks to Simulator from another post for these directions

---

### Post by wirecricket on 2010-04-22
rampage355

THANK U, it works perfectly!!! But to be honest, i thought the newest Nvidia driver has same effect like driver 185 & on this way i didn't tried it. So the solve for my problem too easy))) Yes, it's linux))! 
Thanks once more))!
:lolflag:

---

### Post by teo_rossi on 2010-04-25
I used the custom EDID too with my VAIO CW, but with this workaround I can't connect other monitors to the laptop because they aren't detected.
How can I solve thiss problem?
Are there any other ways to make it work without using the custom EDID?

---

### Post by s_f_z on 2010-05-16
Hi
I am new member and also new to ubuntu.
I have an laptop with Nvidia Gforce 310 m and install Ubuntu 9.04 .
I want to install it as you wrote but I can't find nvidia-glx-185 in my synaptic or add/remove  .whate shoud i do?
 
thank already.

---

### Post by MJalbert on 2010-05-19
Hi, I have a Vaio VGN-Z520N with the dual video card. My Linux is using my NVIDIA card (9300M GS). When I install Ubuntu 10.04 32bits everything works perfectly (using a generic video driver) but when I use the "suggested driver" from the "Hardware Driver" component (NVIDIA driver version 173), my screen goes black and I have to enter using the "nomodeset" in the GRUB script.

I've also downloaded the NVIDIA driver suggested by the NVIDIA website (version 195.36.24), same result: black screen.

Anyone with a VAIO Z-series has been able to install Ubuntu with the NVIDIA drivers?

Also, I would like to know if there is any way that I could use the "Stamina/Speed" feature?

Thanks a lot,

---

### Post by MJalbert on 2010-05-19
Update: I've found a website that might be the solution for the Z-series: [http://global-social.net/sony-VGN-Zseries](http://global-social.net/sony-VGN-Zseries)

I will try that tonight and see if it solve the problem!

---

### Post by davoudi on 2010-06-01
[http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822)

---

### Post by Aloon on 2010-06-25
Can anyone help me with a Sony Vaio VPCF111FD , 310M 64 bit Nvidia ?

I've tried just about everything listed and have only ended up with the split-screen. At this point xorg.conf is empty after having tried a few things with /proc EDID etc. An update that came today seemed to change things for me.

Before the xorg-server-core update , when I went to the moniter section it said unknown and I only had a few options. Now I it says "laptop" and I have dozens of choices including my preferred 1600 X 900 setting.

So I'm getting close now. All I need to do is get the Nvidia card accelerated. 

Any help would be greatly appreciated. I'm 90 % there.

---

### Post by Aloon on 2010-06-27
**Re: Nvidia 310M on a Vaio VPCF111FD - Driver won't work.** 			
 			 			 		   		 		 		It's solved !

Anyone with a Sony Vaio F11 series can use these two links to get  harware acceleratioin from their 310M Nvidia card.

Step 1:

[http://code.google.com/p/vaio-f11-li...ki/NVIDIASetup]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup")

Step 2:

[http://idyllictux.wordpress.com/2010...ricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")

---

### Post by FariAzz on 2010-08-24
> **rampage355 said:**
> This is how I got my NVIDIA drivers working flawlessly

[LIST=1]
[*]let's get that problematic NVIDIA card working. Go to the NVIDIA web-site and download the latest driver. If you have installed the 64-bit (AMD64) variant of Karmic, use the first link - otherwise use the second:
64-bit Ubuntu: [http://www.nvidia.com/object/linux_d...195.36.15.html](http://www.nvidia.com/object/linux_d...195.36.15.html)
32-bit Ubuntu: [http://www.nvidia.com/object/linux_d...195.36.15.html](http://www.nvidia.com/object/linux_d...195.36.15.html)
[*]I'm going to assume that this file is downloaded into the "/home/someuser/Downloads" directory.Restart your machine. When the GRUB menu appears, select the recovery mode for the most recent Kernel version installed (second option from the top, typically). The machine boots and eventually brings up a menu. Select the top menu option (resume). This will bring you to a console login - log in.
[*]When you get to a command prompt, issue the following command to install the NVIDIA drivers:
64-bit Ubuntu:
[/LIST]
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86_64-195.36.15-pkg2.run
```
32-bit Ubuntu:
```
sudo /home/someuser/Downloads/NVIDIA-Linux-x86-195.36.15-pkg1.run
```

Check the version numbers to ensure they match the version you downloaded. Also don't forget to replace "someuser" with your user name.
Thanks to Simulator from another post for these directions

I can't follow these instructions in my Asus K42J (GeForce 310M) because when I enter recovery mode .. I also get a blank screen!! even when the Nvidia proprietary drivers are not active.

[UPDATE] I was able to carry out this instructions from the Live CD, so I installed the NVidia driver from the NVidia website (GeForce 310 for linux 64), but I'm still getting the blank screen......

---

### Post by saeed_s58 on 2010-09-04
> **FariAzz said:**
> I can't follow these instructions in my Asus K42J (GeForce 310M) because when I enter recovery mode .. I also get a blank screen!! even when the Nvidia proprietary drivers are not active.

[UPDATE] I was able to carry out this instructions from the Live CD, so I installed the NVidia driver from the NVidia website (GeForce 310 for linux 64), but I'm still getting the blank screen......
I've posted a report of my experience about the similar problem on [http://ubuntuforums.org/showthread.php?p=9804606#post9804606]("http://ubuntuforums.org/showthread.php?p=9804606#post9804606"). I hope that it can be helpful for you.

---

### Post by FariAzz on 2010-09-04
> **saeed_s58 said:**
> I've posted a report of my experience about the similar problem on [http://ubuntuforums.org/showthread.php?p=9804606#post9804606]("http://ubuntuforums.org/showthread.php?p=9804606#post9804606"). I hope that it can be helpful for you.

Thanks saeed_s58, but the NVidia OPTIMUS technology that my laptop uses is not supported by Ubuntu as it is mostly software based:

[http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html](http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html)

[http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2)

This means that my laptop won't be as efficient and powerful as it should in Ubuntu, so gotta stay in Windows 7 for the moment.

---

### Post by saeed_s58 on 2010-09-05
> **FariAzz said:**
> Thanks saeed_s58, but the NVidia OPTIMUS technology that my laptop uses is not supported by Ubuntu as it is mostly software based:

[http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html](http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html)

[http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=144750&page=2)

This means that my laptop won't be as efficient and powerful as it should in Ubuntu, so gotta stay in Windows 7 for the moment.

Yes, of course. But I prefer to stay in touch with ubuntu rather than windows. My problem was really that I have no active screen there and just a blank screen and a system which was not responding to any action and which could not come up in recovery mode and I try to do the repair using an ssh connection trick.

---

### Post by phanindra on 2010-10-30
> **sdahale said:**
> Great Suggestion ....worked like charm on my Vaio CW23 VPCCW23EN
my laptop is vpccw25fn i tried with this but in vain my lcd working since i set the grub to nomodeset but the system colud not start it stops at checking battery state :(

---

### Post by Phis on 2010-11-17
I finally have Ubuntu 10.10 working on my VPCCW21FX with my 310m card.

I followed instructions from disappearedng on launchpad 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/655078)

section 92

Here are the instructions (which I have supplemented with my own steps in red):

*1) Remove all nvidia packages* [COLOR="Red"]( you can do this through synaptic)[/COLOR]
*2) download the files and install this [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973339](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers/256.53-0ubuntu3/+build/1973339).*

[COLOR="Red"](for this step I found a deb on a related forum:[/COLOR] [http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-current_256.53-0ubuntu3_amd64.deb) and [http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb](http://dl.dropbox.com/u/737114/vpcs11e7e/nvidia-settings_256.53-0ubuntu1_amd64.deb)  

[COLOR="Red"]Here is the forum link: [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)[/COLOR]

[I]3) This is where I tried something different, I read somewhere that you MUST use linux kernel 2.6.36, go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/) (thanks to Artem161 from [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)). Download the appropriate architecture files. I downloaded headers, image and headers-amd64
4) Use the custom EDID option in /etc/X11/xorg.conf
*my edid file is located in /proc/acpi/video... yours might be different.
    Option "ConnectedMonitor" "DPF-0"
    Option "CustomEDID" "DPF-0: /proc/acpi/video/IGPU/LCD0/EDID"
    Option "RegistryDwords" "EnableBrightnessControl=1" # For brightness control[/I]

[COLOR="Red"]This is also from: [http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup) [/COLOR]

[COLOR="Red"]before I could add this I had to generate the xorg.conf file with: sudo nvidia-xconfig then opened it with: sudo gedit /etc/X11/xorg.conf
adding the lines under section device. The brighness controls aren't fixed for me but I don't really care, its further discussed in the forums.[/COLOR]

[COLOR="Red"]If the custom path for the edid does not here is a link to another thread discussing another way to obtain with other cards. 
[/COLOR]
[http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22)

[I]5) 
   sudo update-alternatives --config gl_conf (I picked manual)
   sudo ldconfig
   sudo nvidia-xconfig
   sudo reboot[/I]

Thank you to every one from all the forums.

I followed these steps on a fresh install using 
Dark_Stang's method
[http://ubuntuforums.org/showthread.php?t=1481842](http://ubuntuforums.org/showthread.php?t=1481842)

And on a good note, this problem is announced to be fixed in the next version of the nvidia driver, lets cross our fingers ! :) ([http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)) last post

---

### Post by camilleri on 2010-11-23
Thank you so much Phis!!
I've followed your steps in a fresh linux mint 10 install and it worked perfectly with brightness control included :p

---

### Post by HrachMD on 2010-11-25
> I used the custom EDID too with my VAIO CW, but with this workaround I  can't connect other monitors to the laptop because they aren't detected.
How can I solve thiss problem?
Are there any other ways to make it work without using the custom EDID?
Yes, I also have that problem. I solved the problem with black screen (note: in that time I could see the screen on connected monitor on VGA port), but I solved problem by described method. So now I can't connect monitor or projector to VGA port, can't use HDMI, the second layout is't persist and twin mode is inactive. Please anybody help me solve the problem.

---

### Post by enriqg9 on 2010-11-30
I have a Samsung Qx410-J01 and I can't get my nVidia 310m working, I already tried all of the above and I always get into the tty1 screen after I change to the Nvidia driver and I have to restore xorg.conf in order to log into the GUI. ANY IDEAS? Thanks.

---

### Post by losoollenos on 2010-12-07
Hola !!!

Les comento que en la alfa de 11.04, el Wi-Fi esta de lujo !!!!!
Lamentablemente, no pude hacer andar ninguna version de nvidia.....pero no andan tan mal los que trae, creo que estara andando con nouveau.

Disculpas por escribir en español, con mucho esfuerzo apenas entiendo algo al leer ingles jejej

saludos

---

### Post by crownclown on 2010-12-20
I get the same problem here..well im using asus A42J processor is i5 and graphic is Geforce 310m..
this is the thread that i've open [http://ubuntuforums.org/showthread.php?t=1648606](http://ubuntuforums.org/showthread.php?t=1648606)
my lspci

saya@saya:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
07:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
07:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
07:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

---

### Post by basu0009 on 2010-12-21
Hi Enriqg9,

Did you solve this problem? I am having the same issue. 

Thanks. 

> **enriqg9 said:**
> I have a Samsung Qx410-J01 and I can't get my nVidia 310m working, I already tried all of the above and I always get into the tty1 screen after I change to the Nvidia driver and I have to restore xorg.conf in order to log into the GUI. ANY IDEAS? Thanks.

---

### Post by neiltingley on 2010-12-26
if anyone is struggling with sony VPCS13V9E then you need to generate a custom EDID from windows using softmmc as people have described and then add this to Device section of xorg.conf. Copy the EDID.bin file to /etc/X11 for example.


 ```
  
Option       "ConnectedMonitor" "DFP-0"
Option       "CustomEDID" "DFP-0:/etc/X11/EDID.bin"
```


I edited this in the Screen section.

 ```
   SubSection     "Display"
        Depth       24
        Modes      "1366x768"
    EndSubSection

```

I'm using the latest drivers from nvidia.

X was failing to find any screens and the custom EDID fixed it for me. I've spent many hours fiddling.

---

### Post by hueschel on 2011-02-02
Hi

As far as i am concerned, Optimus Technology won´t be supported by Linux because of issues with implementing Optimus in X11. In X11 it is not possible to switch the display device without shutting down X11. (right?) 
Ubuntu 11.04 will have the Unity Desktop available. May this lead to Nvidia supporting Optimus in Ubuntu? Unfortunately i have not found any information about the possibilities in Unity to switch display devices.

edit: oh i mixed something up here. It may be that Unity will be based on **Wayland** instead of X11![U][U]
[URL="http://www.markshuttleworth.com/archives/551"]
[/URL][/U][/U][U][Link]("http://www.markshuttleworth.com/archives/551")
[/U]

---

### Post by atti14 on 2011-02-02
hello all
i am new member in ubuntu forums...
i have facing a problem in install ubuntu..
i have sony vaio vpccw with preinstall win 7. when i install ubuntu inside the window the setup will run and copy all file, after reboot a black screen is occure... 
help me out..
thanks

---

### Post by dbeltrami on 2011-02-07
Hi,

I have a Sony S Series VPCS137GG.
Following the guide on using CustomEDID and updating my GRUB configuration, I've managed to get the latest NVIDIA Beta driver to work fine.

I can also get an external monitor to work in either Separate X-Screen or TwinView mode.  However, I can't manage to configure the system so that when I'm connected to an external monitor, the laptop display is disabled (and when I'm disconnected from the monitor, the laptop display is enabled).

In the past, I've always been able to achieve this by setting up my monitors as separate X screens and disabling the laptop monitor (it always re-enabled itself if it did not detect an external monitor).  If I try this configuration with the Sony, when I'm not connected to my external monitor it doesn't know how to re-enable the laptop monitor.

Does anyone have any ideas?  I assume it's something to do with the CustomEDID configuration that we need to include in xorg.conf.

Thanks.

---

### Post by lightwave on 2011-02-21
NO NO No I was engaged with this NVIDIA driver with 2 days but i cant solved. I have Asus U30j Laptop with Nvidia 310M GPU. At first it was working good with orginal kernel drivers but when i installed the additinal driver at system. My screen became black. I tried all of the solutions previous pages but always same,black screen. I tried updated jockey driver doesnt work for me. I tried this with sentence to sentance but nothing 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

I removed all nvidia drivers

sudo apt-get --purge remove nvidia-*


I downloaded NVIDIA 256.53.** driver and installed

nothing happen. Uff. I got crazy. There must be a way.

please help I am using 10.10

---

### Post by ericklan on 2011-03-09
> **wirecricket said:**
> rampage355

THANK U, it works perfectly!!! But to be honest, i thought the newest Nvidia driver has same effect like driver 185 & on this way i didn't tried it. So the solve for my problem too easy))) Yes, it's linux))! 
Thanks once more))!
:lolflag:
wirecricket Excelent!!! the beta Driver 185, tested in the Toshiba satellite i7!

---

### Post by Marceloeloelo on 2011-03-11
> **ericklan said:**
> wirecricket Excelent!!! the beta Driver 185, tested in the Toshiba satellite i7!


Erick, how did u do that???
I`ve tried with every method posted here and I still can`t make it work.
I have a Toshiba Satellite A665 core i5, with NVidia Geforce 310M. 
I`ve tried donloawding and installing the last driver published by NVidia website, and when I reboot the system, after selecting Ubuntu at grub it sometimes logs with no GUI, and it sometimes just get stucked in a black page loading...
I've also tried by installing the package nvidia-glx-185 and also the nvidia-glx-185-dev and neither worked, the same error happends...
I've also tried by downloading from the NVidia website the Beta versions of the driver!! And still the same...

And with all that combinations, I always tried booting with the default xorg.conf, when it failed, I edited it with the values that were suggested here, and never worked. (Instead of using the "sonycw.txt" I 'stole' the "EDID.bin" from Windows with the software someone suggested in the past, but as you guess, didnt work either)

Any ideas, someone??? :S

---

### Post by karshan on 2011-03-15
Lightwave, you have a laptop with nvidia optimus technology, it has both an intel graphics card inside and an nvidia, and there's some weird acpi stuff that does the switching based on needs, on windows you could choose which card to use from the nvidia control panel. unfortunately there is no linux solution that i know of for this new switching problem, in short there isn't stable support for nvidia optimus on linux. you can however run ubuntu perfectly fine just on the intel card (which was what was happening till you installed the nvidia drivers), but you cannot use the nvidia card, which is a bummer if you wanted to play graphic intensive games, but thats not what you do on linux anyways (do you?). Anyways, the simplest solution would be to reinstall ubuntu, and then NOT to install the nvidia driver (open source or binary blob), if you really don't want to to that then, you can look at this page:
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)
(if you're familiar with linux)it has a little script to do the switching, you can try running it in recovery mode to switch back to the intel card permanently, i have a feeling that wont work though,  another option:
uninstall X, and reinstall it (personally I think this can be more of a pain than just reinstalling ubuntu).

Also, I have the same laptop, and I'm actually planning on working on getting the switching driver working, but till then gotta use the intel chip.

---

### Post by RunLikeHell on 2011-03-24
@dbeltrami

i also have an s137, but i cant get it to work, is there something different you did?

thanks

---

### Post by rez182 on 2011-05-19
anyone facing problem with the latest 11.04 unity and the nvidia gforce 310m 260.x.x.x or 270.x.x.x driver?

mine does not work. after i install the 260.x.x.x driver (270 in not in the synaptic package manager in mine for some reason) the login screen does not appear instead it gets stuck in a black screen...

is there a fix for this?

thanks...

EDIT: btw my laptop is Asus K40IE

---

### Post by eherna2000 on 2011-06-13
Has anyone seen an update for the samsung qx410-j01? I downloaded the drivers from the nvidia site. I activate them via the Propetary hardware manager but nothing. I start the nvidia manager ask me to create an xorg.conf. When I generate one laptop fails to boot here is my current xorg.conf:
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
============================
Also seems like there is no support for the touchpad for this machine correct?

---

