---
title: "Help for installing NVIDIA driver"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by Balaton on 2012-07-06
Hi,

I've got some problem with installing my video card. I've got a dell Inspiron  N5110 (15R) laptop with NVIDIA GeForce GT 525M video card and a basic video card too. I'm a very beginner user of Kubuntu and I don't know how should I install this video card. I read what the webpage of NVIDIA driver wrote, but it doesn't work. Somebody told me because I've got two video card's I have install ironhide, because this program can help by switching between this two cards. But every time I tried, I'v got always some problem. If somebody write me step by step how could I install my video card, I would be very thankful.

Balaton

---

### Post by bogan on 2012-07-07
Hi!,** balaton**,

Please Post the following run from a terminal [Ctrl+Alt+t].
 [Copy/paste to a New Reply Edit box, highlight and press the '#' icon in the tool bar in the  top of the box, to enclose in a Code box for easy reading.] ```
uname -ar
lspci -nnk | grep -iA2 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```Have you used Additional Drivers or run the nvidia download driver .run file?

What exactly is the problem you need help to cure?

 Does it boot up to a GUI and run correctly?

Chao!, **bogan.**

---

### Post by Balaton on 2012-07-07
Hi bogan,

I did what you write and there are this information's:

tiger@tiger:~$ uname -ar
Linux tiger 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
tiger@tiger:~$ lspci -nnk | grep -iA2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Dell Device [1028:04ca]
        Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df5] (rev a1)
        Subsystem: Dell Device [1028:04ca]
        Kernel driver in use: nouveau
tiger@tiger:~$ sudo apt-cache policy nvidia-current
[sudo] password for tiger: 
nvidia-current:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) precise/restricted amd64 Packages
tiger@tiger:~$ cat /sys/module/nvidia/version
cat: /sys/module/nvidia/version: No such file or directory

To tell you the truth I tried several times to install the NVIDIA driver and always got problems with it. After that I always have to re-install my operation system, because the basic video card didn't worked after that. Maybe before I install that video card I have to install other missing things but, I don't know what. As far as I remember I've got problems with configuring NVIDIA X driver. Once when I had the earlier version of Kubuntu, I find NVIDIA driver as additional, and I installed them but after that nothing, as I didn't installed it. I don't know why, it didn't worked. I'm using Kubuntu only a year ago and only know basic things. 
Could you tell me how could I saw this: "Does it boot up to a GUI and run correctly?"

Thanks for helping. :-)

By, Balaton

---

### Post by bogan on 2012-07-07
Hi!, **balaton**,

You Posted:>  Could you tell me how could I saw this: "Does it boot up to a GUI and run correctly?"What I meant was:

A: Do you get through the sequence: Grub Menu, choose boot-option, log-in screen, choose display-option, password accepted, Desktop wallpaper with top toolbar and left Launcher bar with Icons?
Or does the system hang up or freeze with a blank screen?

B: If it boots OK, then can you run the programs from the Launcher? 
Does the 'Dash' - Icon top of Launcher - display applications and can you run them? 
Especially is your screen clear with good colors and no shattered images or shadow images? 
Can you resize and drag windows? 
Do Videos and Movies display correctly?

C: Can you run Unity and programs - eg Games - that demand high graphics performance, satisfactorily?

[If you are in doubt, run, from a terminal:]```
 echo $DESKTOP_SESSION
/usr/lib/nux/unity_support_test -p
```and Post the results.

Apart from the difficulties you had with trying to install nvidia drivers, what is it that you need help for?

The default nouveau driver you are using will run the nvidia card OK for most needs, and the i915 driver should run the Intel integrated graphics.

Chao!, **bogan**.

---

### Post by SeijiSensei on 2012-07-07
You should take a look at [Bumblebee](http://bumblebee-project.org/).  It's designed to handle machines like yours with "Optimus" graphics.

---

### Post by Balaton on 2012-07-07
Hi bogan,

I see, I thinks it's work well. I can view movies, play games, and I have special desktop effects too. But i can't handle multiple monitors and I can't wach movies in my TV if I connected my laptop and my TV with HDMI cable. So I need to install and configure NVIDIA driver. I read the manual of it, but it's too difficult too understand, because, I don't know much how Kubuntu works and which of the instruction should I follow.[http://us.download.nvidia.com/XFree86/Linux-x86_64/295.59/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/295.59/README/index.html)
I tried to do what it's wrote, but I every time comes some problem. I didn't know if I have this nouveau driver or not? If I have it I have do things other way. So that is why I need help. If I'm doing something bad that wouldn't be work.
Thanks for helping.

Chao! balaton

---

### Post by Balaton on 2012-07-07
Thanks for the information, but shouldn't I install and configure NVIDIA driver firs and after that Bumblebee? :S

---

### Post by bogan on 2012-07-07
Hi!, **Balaton**,

You Posted:```
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df5] (rev a1)
        Subsystem: Dell Device [1028:04ca]
       [COLOR=Blue] Kernel driver in use: nouveau [/COLOR]
```So you do have nouveau, it is included in the 12.04 kernal.

From other threads I understand that the nvidia drivers do not handle double monitors with Optimus, all that well. 

However if you want to try I can Post an instruction set for you, it is not that difficult. My only reservation is that I know nothing of Kubuntu, and whether it makes any difference - I think probably not.

Chao!, **bogan.**

---

### Post by Balaton on 2012-07-07
Hi bogan,

Please post me this instruction set maybe that would help. But one thing I can't understand if I used win7 there worked multiple monitors. One of them was my original laptop monitor and other was the TV. But I would like rather use linux than windows. If I can fix that problem I finally don't need windows. The readme of NVIDIA driver wrote that: "If you're installing on a system that is set up to use the Nouveau driver, then you should first disable it before attempting to install the NVIDIA driver. See Q & A 8.1, “Interaction with the Nouveau Driver” for details" Maybe that's the problem. Last time when I tried I didn't know that I have nouveau. But now I know, so maybe with your instruction set I can fix the problem. 
Thanks for helping.

Chao! balaton

---

### Post by bogan on 2012-07-07
Hi!, Balaton,

1. To disable the nouveau driver, check the /etc/modprobe.d folder to see if there is a 'blacklist.conf' file. Run:```
 gksu gedit /etc/modprobe.d/blacklist.conf 
```add a line: 'blacklist nouveau' [ no inverts] save and exit.

2.To install the latest nvidia driver: You need an operating Internet connection for this.

 Down load the appropriate driver from nvidia.com .
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html). That is for the 32.bit version, make sure you have the correct one.
Run 'uname -r' and insert the output in the following command, substituting it for 'uname -r', for example: "sudo apt-get install linux-headers-3.2.0-24-generic-pae"```
sudo apt-get install linux-headers-'uname -r'
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev
``` To install the downloaded driver, Xorg cannot be running. You need to shut down the X-Session. In the terminal enter:```
sudo service lightdm stop # If using 10.10 or earlier use 'gdm' in place of 'lightdm'
```You may get a black screen; if it does not have a login prompt, press 'Ctrl+Alt+F1'to get one, login, enter your password.
[It will not show, just enter it and press 'Enter.]
Alternatively, reboot into recovery and a TTY Text Console and login.

3. In the following, substitute the correct file name:

Change directory [cd] to the directory where you saved your file. eg 'cd  /home/username Downloads '.

Run 'ls', this will confirm you are in the right place and you can be sure the spelling is correct - enter 'NV' and pressing 'Tab' will Auto-complete the file name.
 Mark the downloaded file as executable:```
sudo chmod a+x NVIDIA-Linux-x86-295.53.run
```Run the file to Install drivers:```
sudo sh NVIDIA-Linux-x86-295.53.run
```You may get an error message about a failed script, continue, accept the options, navigating by using 'Tab' and pressing 'Enter'.

When complete reboot,```
 sudo reboot
``` If necessary edit the boot script by pressing 'e' with the boot option highlighted, and entering 'nomodset' after 'splash ' in the Linux line where it shows " ro quiet splash " and press 'Ctrl+x' to boot.

Good luck, let us know how it goes.

Chao!, bogan.

---

### Post by jonnyboysmithy on 2012-07-07
Not to cause any confusion, but wouldn't it be easier to use jockey-gtk to list the installed driver?
In my experience its easy:
 jockey-gtk --list See the available drivers.
jockey-gtk --disable=[drivername]
jockey-gtk --enable=[a driver that was listed as above using the --list command]
 
EDIT: Is it because the driver you get throught the repository is out of date?

---

### Post by bogan on 2012-07-08
Hi!,** jonnyboysmithy**,

If 'jockey-gtk' works for you, then: Fine!

My experience is that together with its GUI interface, 'Additional drivers', it is opaque, uninformative, unreliable and unpredictable.

Moreover, unbeleivably, it is still offering the bug ridden 295.40 as the standard nvidia-current driver, but with no indication of what version number will be installed .

Running anything with 'jockey-gtk' in it,  just now, produced a screen full of 'Gtk-Warning' messages, whilst: ```
jockey-gtk --list # "See the available drivers", additionaly produced:
jockey-gtk: error: no such option: -i
```There is no man file for jockey-gtk, but evidently the correct option would have been '-l', which , in addition to two screens-full of Warnings, produced exactly the same as is displayed by 'Additional Drivers'; ie. no version numbers, only names.
[COLOR=RoyalBlue]EDIT:[/COLOR]*** Apologies! I mistakenly entered: '-list', instead of: '--list', though: '-l' is also correct.***

Edit 2: I also ran 'jockey-gtk -l' on the same computer, but in a different 12.04 LTS installation, and it did not produce any Warnings; so there is something wrong with GTK on my primary 12.04 Ubuntu.

Edit 3:[COLOR=RoyalBlue]* I had been running the Clearwaita Gtk Theme, which was corrupted; changing to the default Adwaita, the Warnings quit.*[/COLOR]

If I** were** to use this system, I would do it from 'Synaptic Package Manager', which at least tells one what version numbers are available, even if the choice is mainly for well out of date versions [13 of them!! ].

Critically, the OP has Nvidia and Intel integrated graphics and needs the most up-to-date version.

Cho!, **bogan**.

---

### Post by Balaton on 2012-07-08
Hi bogan,

I've got problem in the beginning. As you wrote I tried to run this code: gksu gedit /etc/modprobe.d/blacklist.conf after that it wrote me it's missing and you have to install it. I did that and it's seems to be work but I tried run next time and that want from me a password. I wrote that my password but it's wrote me back it's not good. I should enter the administrative password. But I don1t know what is it. I use only one password, and it's work if I want to run something as root. But if I tried to run it as root that message come: root@tiger:/home/tiger# gksu gedit /etc/modprobe.d/blacklist.conf
No protocol specified
No protocol specified

(gksu:3247): Gtk-WARNING **: cannot open display: :0

After that in other forum I got the information somebody else had the same problem as me and there is a topic about it. I found it and I tried to do wath it's wrote. It's seemed to be everything ok but the final came error.
[http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04](http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04) I do what this link wrote. The erros message was that:
tiger@tiger:~$ sudo dpkg -i nvidia-current-updates_*.deb
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 196449 files and directories currently installed.)
Unpacking nvidia-current-updates (from nvidia-current-updates_295.49-0ubuntu0.1_amd64.deb) ...
Setting up nvidia-current-updates (295.49-0ubuntu0.1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Inspiron N5110 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-295.49 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-3-generic
Building for architecture x86_64
Building initial module for 3.5.0-3-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-3-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-3-generic (x86_64)
Consult /var/lib/dkms/nvidia-current-updates/295.49/build/make.log for more information.
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-3-generic
tiger@tiger:~$ sudo modprobe nvidia_current_updates
FATAL: Module nvidia_current_updates not found.

So I'm now the middle of nowhere and I don't know what to do. I think I reinstall my Kubuntu and try to install the driver.

Chao! balaton

---

### Post by bogan on 2012-07-08
Hi!, **balaton**,

Well, that link did warn you!! > this is a set of highly experimental software &#8211; if it works for you, count yourself lucky and if it doesn&#8217;t &#8211; don&#8217;t complain.It certainly lived up to that threat. It is also somewhat out of date, and extremely complex.

I could not make any sense of what you posted; Where did Ubuntu 3.5.03-generic come from?? You have surely not reinstalled to that, have you?
EDIT: Presumably it came from: > sudo apt-get dist-upgrade -yYou Posted:> So I'm now the middle of nowhere and I don't know what to do. I think I reinstall my Kubuntu and try to install the driver.Yes, I guess you do not have any choice but to format and re-install after saving any data if you can.

I am also puzzled by:>  I tried to run this code: gksu gedit /etc/modprobe.d/blacklist.conf  after that it wrote me it's missing and you have to install it. I did  that and it's seems to be work but I tried run next time and that want  from me a password.With no 'blacklist.conf' file, that code should have opened  a blank file of that name, in which to enter the nouveau line and save the file; though 'gksu' will ask for a password - the normal user password.

As to the root password problem, I do not understand why you apparently rebooted at that point, rather than installing the nvidia driver. However I have had the same problem myself in the past, and cured it by booting to a  text login and entering the command to make the root password the same as my user password - but you should not need to do that.

It is not advisable to run things as root, - better to use 'sudo' - unless you know exactly what you are going to do that  needs to be from root.  Especially not to use 'gksu' from root.
As you have found, the results can be catastrophic.

Good Luck!

Chao!** bogan**.

---

### Post by Balaton on 2012-07-08
Hi bogan,

Maybe it's too late, but I re-installed my operation system. Now it's new and I have only updated it.I try now to install this driver. But I'm bit confused, every body tell me other information. After I tried what i wrote come-s the same problem as other time before. Maybe my kernel version is the problem. Somebody told me the kernel version I had is supported by the Kubuntu 12.10 version and maybe that's causes the problem. I found something in the moun software center. There is a NVIDIA binary X.org driver ('version 173' driver).
Thanks for helping.

Chao! balaton

---

### Post by bogan on 2012-07-08
Hi!, **Balaton,.**

For Pete's sake don't install nvidia 173, that an ancient legacy driver.

You need the latest driver for your graphics, at least 295.59 and preferrably 302.xx

I will check out the NV site and post back.

Chao!, **bogan**.

---

### Post by bogan on 2012-07-08
Hi!, **Balaton,**

As I thought, the recommended nvidia driver for your GT 540M card is: v 295.59, and the latest beta version is 302.07.
[http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk)

That is the 64bit[COLOR=Red] beta [/COLOR]version, make sure you get the right one.

Chao!,** bogan**.

---

### Post by Balaton on 2012-07-08
Hi bogan,

Maybe not only the kernel is my problem?:S I found that of readme of this driver:  [http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.59-driver.html) 

Installing the Kernel Interface

The NVIDIA kernel module has a kernel interface layer that must be compiled specifically for each kernel. NVIDIA distributes the source code to this kernel interface layer.

When the installer is run, it will check your system for the required kernel sources and compile the kernel interface. You must have the source code for your kernel installed for compilation to work. On most systems, this means that you will need to locate and install the correct kernel-source, kernel-headers, or kernel-devel package; on some distributions, no additional packages are required.

After the correct kernel interface has been compiled, the kernel interface will be linked with the closed-source portion of the NVIDIA kernel module. This requires that you have a linker installed on your system. The linker, usually /usr/bin/ld, is part of the binutils package. You must have a linker installed prior to installing the NVIDIA driver. 

Other's told me that the driver didn't like my kernel version. I didn't do anything yet. So it's everything as I installed the kubuntu 12.04.

Chao! balaton

---

### Post by bogan on 2012-07-09
Hi!, **Balaton**,

You Posted:>  You must have the source code for your kernel installed for compilation  to work. On most systems, this means that you will need to locate and  install the correct kernel-source, kernel-headers, or kernel-devel  package;Those requirements are included in the instructions I  Posted: #10.```
 sudo apt-get install linux-headers-'uname -r' 
sudo apt-get install build-essential gcc-4.5 g++-4.5 libxi-dev libxmu-dev freeglut3-dev 
```The rest of the quote is carried out by the nvidia-installer when you run it.

Provided that you have cleared out the 12.10 3.5.0 kernal by formatting the partition and freshly re-installing the 12.04 version, there will not be an incompatibilty with 295.59 or 302.07 nvida drivers.

Chao!,** bogan. **

---

### Post by Balaton on 2012-07-09
Hi bogan,

Thanks for the information. I've got one more question. How could I view which one kernel version I have. I re-installed my system, so it have to be good, but I would like to check it. Thanks for helping.

Chao! balaton

---

### Post by bogan on 2012-07-09
Hi!, **Balaton**,

To find out the installed kernal version number and name, run:```
 uname -ar
cat /etc/lib-release
```

Let us know how you get on.

Chao!, **bogan**.

---

### Post by Balaton on 2012-07-09
Hi bogan,

I checked the kernel version and it was  3.2.0-26-generic and after I tried to install bumblebee it's changed and I've got this message now: 
tiger@tiger:~$ sudo dpkg -i nvidia-current-updates_*.deb
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 162913 files and directories currently installed.)
Unpacking nvidia-current-updates (from nvidia-current-updates_295.49-0ubuntu0.1_amd64.deb) ...
Setting up nvidia-current-updates (295.49-0ubuntu0.1) ...
update-alternatives: using /usr/lib/nvidia-current-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-current-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Inspiron N5110 with Latitude E6530
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-295.49 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-3-generic
Building for architecture x86_64
Building initial module for 3.5.0-3-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-3-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-3-generic (x86_64)
Consult /var/lib/dkms/nvidia-current-updates/295.49/build/make.log for more information.
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-3-generic
[QUOTE=bogan;12088605]Hi!, **Balaton**,

I know, you warned me, but I thought maybe the first time I made some mistake. So I think the driver would work if I change the kernel.

Chao! balaton

---

### Post by oldos2er on 2012-07-09
> **jonnyboysmithy said:**
> Not to cause any confusion, but wouldn't it be easier to use jockey-gtk to list the installed driver?


Since OP is using Kubuntu, **jockey-kde** would be the preferred command.

---

### Post by bogan on 2012-07-10
Hi!, **Balaton**,

You seem to be back where you were ante.

I suspect the link you were acting on is both experimental and out of date; in any case it seems to assume you are using Quantal 3.5.0.3, which is, itself, also experimental.

I suggest you look at the Bumblebee project itself, which should lead to the latest version, with proper instructions for installation: [http://bumblebee-project.org/](http://bumblebee-project.org/).

Alternatively, have a look at another approach,'Ironhide':
[http://askubuntu.com/questions/108648/bumblebee-or-ironhide](http://askubuntu.com/questions/108648/bumblebee-or-ironhide)

Chao!,** bogan.**

---

