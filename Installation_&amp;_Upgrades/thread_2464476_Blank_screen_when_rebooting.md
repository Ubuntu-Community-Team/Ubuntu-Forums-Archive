---
title: "Blank screen when rebooting"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by hermansenn on 2021-07-02
Everything worked just fine on my raspberry pi 4 until i reboot it, or power it off.

When booting everything seems fine but the screen just goes black after saying this: 

Directory ´fef00700.hdmi` with parent `vc4-hdmi-0` already present.

Backlight is on and caps and numlock works I've reinstalled ubuntu 10 times now, using the raspberry flasher but no luck. Ubuntu mate works just fine.

---

### Post by MAFoElffen on 2021-07-03
Is it a Raspberry Pi4? And if so 4GB or 8GB  RAM?

Which Kernel?

[Bug#986863: linux: Serial terminal for RPi 4 and p400 corrupted during bootup]("https://linux.debian.kernel.narkive.com/iAK4i4Ts/bug-986863-linux-serial-terminal-for-rpi-4-and-p400-corrupted-during-bootup")

---

### Post by hermansenn on 2021-07-04
I have a Raspberry pi4 Model B with 4gb ram

Kernel is: 5.11.0-1007-raspi

Update: Ubuntu Mate works just fine, and i can turn it on with no problems.

I've tried installing ubuntu 21.04 from different places and using different applications to flash my sd card.

---

### Post by MAFoElffen on 2021-07-04
At the Grub2 boot menu, quickly press <down-arrow><up-arrow>, so the menu stays, and pauses the boot process...

Press <E> to edit... Go down to the kernel boot line and add the kernel boot option "hdmi_safe=1"...
Press <Cntrl><X> to Boot...

After it boots, open an editor in elevated permissions... Open /etc/defaults/grub... Go down to the line where you see the kernel boot options, where it says "quiet splash"... Add "hdmi_safe=1". Save the file. Exit the editor.

In a terminal do
```

sudo update-grub

```
To pick up the change and make it persistent..

---

### Post by hermansenn on 2021-07-04
That does unfortunately not work, i had to reinstall ubuntu on the sd card to get to edit Grub and even Did # before the "GRUB_HIDDEN_TIMEOUT=true" to get Grub menu at boot, if it happened again, but it does not appear.

I did GRUB_CMDLINE_LINUX_DEFAULT="quiet splash""hdmi_safe=1" and updated grub.

---

### Post by MAFoElffen on 2021-07-04
Do not put in the extra double quotes...IO just did that so it wouldn't get lost ion the other text of the post, so more like:
```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hdmi_safe=1"
```
...With the extra quotation marks, it is not going to recognize/honor it which the other boot options...

---

### Post by hermansenn on 2021-07-04
Still doesn't work :/

I forgot to mention that i'm not using hdmi cable, but the internal display port on the Raspi. Does that have anything to do with it?

And do you know a way to get out of the black screen when boot fails, so i don't have to reinstall ubuntu every time i restart my Pi?

The grub menu doesn't show up either.

---

### Post by MAFoElffen on 2021-07-05
If on the keyboard, you hold down the <Cntrl><Alt> keys and try <F1> thru <F7>, it will respectively cycle thru virutal consoles TTY1 thru TTY7. System Console is usually TTY1, until the Login Manager starts in it, then transfers to the first open TTY (usually TTY2) so that one is probably the one that is blank.

It's virtual TTY consoles, so virtual terminal sessions overlaid on top of the text console. It's at least a change to make changes and see what is going on...

If you do
```
sudo update-pciids
sudo lshw -C video
xrandr |awk '/connected/{print $1,$2}'
```
What is the output of the lshw and xrandr commands? You can take pictures of that from a phone and post them as attachments(?)

Or find out the IP and SSH into it, from another machine. Just ideas... That way you could just cut and paste the output. If that, then encapsolate the output within [ c o d e ]  output_here  [ / c o d e ] tags... (without the spaces I put between those characters to display that.)

---

### Post by hermansenn on 2021-07-05
The [COLOR=#000000]<Cntrl><Alt> <f(x)> keys does nothing (maybe i'm not pressing them at the right time)[/COLOR]

when i do the commands in the terminal it just says:

```

xrandr: Failed to get size of gamma for output default
default connected

```

lshw does not make an output. it just says: ```

USB
SCSI
Framebuffer devices

```
and closes

---

### Post by MAFoElffen on 2021-07-05
Hmmm. "Framebuffer" would be the video. 

Let me ask my son... He has Raspberry Pi4 8GB. He himself uses Ubuntu Mate 20.04 LTS on it. He says that flavor already has the RaspBian hacks sripted in and included in that image... I remeber him telling me that the response/performance is a lot better than anything else he has found, running on his.

---

### Post by MAFoElffen on 2021-07-05
Oh... In the /boot folder, is there a file called config.txt? Could you post the contents?

Also, if it exists: /boot/firmware/syscfg.txt

---

### Post by hermansenn on 2021-07-05
I did get Ubuntu Mate to work on my Pi4 but i don't really like that flavor as the Pi4 only would be connected to a 7" touch screen when i'm done, and Mate does not support touch screens. 

The best scenario is to get Ubuntu 21.04 to work. 

I just think it's weird that the screen works fine when booting and setting up the first time, but it can't reboot and work... And thanks for helping me btw!

---

### Post by hermansenn on 2021-07-05
There's only a config.txt under the firmware folder, not in /boot
Config.txt:

```

[pi4]
max_framebuffers=2


[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel


# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on


# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
dtoverlay=vc4-kms-v3d
gpu_mem=128


# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1


# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1


# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2


# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host


# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2

```

---

### Post by MAFoElffen on 2021-07-05
Try this config.txt file:
```
# For more options and information see
# http://rpf.io/configtxt
# Some settings may impact device functionality. See link above for details

[pi4]
# Enable DRM VC4 V3D driver on top of the dispmanx display stack
#dtoverlay=vc4-fkms-v3d
max_framebuffers=2

# uncomment if you get no picture on HDMI for a default "safe" mode
hdmi_safe=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1


# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
#overscan_left=16
#overscan_right=16
#overscan_top=16
#overscan_bottom=16

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
#hdmi_group=1
#hdmi_mode=16

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=11


# uncomment for composite PAL
#sdtv_mode=2


[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel


# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on


# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
## Note that this loads a "psuedo" KMS framebuffer that is better on Pi for desktop usage.
dtoverlay=vc4-kms-v3d
gpu_mem=128


# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1


# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2


# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host


# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2

```
There's also a lot of commented graphics options to play with if the changes needs more tweaking...

While you are at it, remove that kernel boot option from the Grub default ( where I had you do previously), as it gets those settings from this file instead.

---

### Post by MAFoElffen on 2021-07-05
Wait a minute... LOL

I have a question... When you say you are not using either of the HDMI ports??? ...and say you are using the "internal display port"... do you mean what they call their 2-lane MIPI DSI display port? And what exactly are you using as a display connected to it?

I know the older boards had an RCA port. Which was, by default, switched off And the Pi4 doesn't have that. And the config changes I have given you, affect HDMI, which you say you are NOT connected to... SO, trying to figure out, which config changes to suggest that would affect what you are doing...

I guess the controller on the Pi4, using that port, uses the same commands as the RCA port did... So. I'll wait for you to answer, then if so, give you "other things" to try.

---

### Post by hermansenn on 2021-07-05
Thats it... 

I'm using a "Smart Pi touch 2 7"" display

---

### Post by MAFoElffen on 2021-07-05
Okay, this one is changed to turn your DSI display port on and be able to use composite video...
```

# For more options and information see
# http://rpf.io/configtxt
# Some settings may impact device functionality. See link above for details

[pi4]
# Enable DRM VC4 V3D driver on top of the dispmanx display stack
#dtoverlay=vc4-fkms-v3d
max_framebuffers=2

# uncomment if you get no picture on HDMI for a default "safe" mode
#hdmi_safe=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
#disable_overscan=1


# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
#overscan_left=16
#overscan_right=16
#overscan_top=16
#overscan_bottom=16

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
#hdmi_group=1
#hdmi_mode=16

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=11

### Composite Video Section ###
# Uncomment to turn the composite video port on
# this setting is off by default
enable_tvout=1

# uncomment for composite PAL
# Valid modes to try
#    2= Normal PAL, 18= Progressive scan PAL 
sdtv_mode=2


# uncomment to remove color and display in monochrome
# sdtv_disable_colourburst=1

# uncomment to change vidoe aspect ratio
# default is 1 (4:3). Others: 2 (14:9), 3 (16:9)
#sdtv_aspect=2


[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel


# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on


# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
## Note that this loads a "psuedo" KMS framebuffer that is better on Pi for desktop usage.
dtoverlay=vc4-kms-v3d
gpu_mem=128


# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1


# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2


# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host


# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2

```

---

### Post by hermansenn on 2021-07-05
It didn't work :/

Do i have to update it or something?

---

### Post by MAFoElffen on 2021-07-05
> **hermansenn said:**
> It didn't work :/

Do i have to update it or something?

From what I read, no... The Raspberry Doc's say that when the board starts loading from it's frimware, it looks for a /boot directory in the SD card, looks for a text file named confgi.txt and in reading the text in that file, applies those configuration parameters to the board and how it boots. It's just a simple asci text file. that can be edited while on the board, or from any system that can read that SD card, and edit text files.

I guess the important thing, is that is is located in the /boot directory on that SD card.

and the 2 configuration parameters you seem to need (additionally to your original file) to turn that port (beyond just simple console text) is:
```
enable_tvout=1 
sdtv_mode=2
```

---

### Post by hermansenn on 2021-07-05
It's already in the config file.. :/

And i can't seem to find anyone else with the same issue as me (i've searched everything on google)
It seems like everyone with the issue is using Raspberry Pi OS, and they fix it by upgrading firmware :?

---

### Post by MAFoElffen on 2021-07-05
Is Your Firmware up to date?

I jst off my phone with my son and described your problem... He asked me why you where? using Mate? LOL... I can't win. He has almost convinced me to buy a Pi4 for my self though.

---

### Post by hermansenn on 2021-07-05
The firmware should be up to date.

And i were just using mate to see if that would work. And it did. That's why i'm wondering why it's not working on Ubuntu. I just can't figure out why the screen goes blank when booting for the second time. It is just so wierd that it picks up the connection and shows the splash screen but nothing else happens... And also the fact that the display works perfectly fine when booting for the first time.

---

### Post by MAFoElffen on 2021-07-05
At what point does it go blank?

---

### Post by hermansenn on 2021-07-06
I’m on the phone so it has to be links.

First splash screen: [https://media.discordapp.net/attachments/692453369805275177/861819816457666590/image0.png](https://media.discordapp.net/attachments/692453369805275177/861819816457666590/image0.png)

Second: [https://media.discordapp.net/attachments/692453369805275177/861819881346170910/image0.png](https://media.discordapp.net/attachments/692453369805275177/861819881346170910/image0.png)

---

### Post by MAFoElffen on 2021-07-06
There. I don't see any successful kernel boot. I see a crash while trying t o boot the kernel. If it is not booting a kernel, it's at no point yet to get any kind of graphics.

Are you sure you have a good image on the SD card?

---

### Post by hermansenn on 2021-07-08
I'm pretty sure, i used the raspberry pi imager

---

### Post by MAFoElffen on 2021-07-09
My Pi4 just arrived this afternoon... In fact I'm posting from it right now, on Ubuntu 20.04 and running Ubuntu Desktop... But I am connected to a TV via HDMI.
```
ubuntu@mikes-pi4-01:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

ubuntu@mikes-pi4-01:~$ uname -r
5.4.0-1038-raspi
```
Used a 32GB Samsung Micro SDcard.

Burned image via the "Raspberry Pi Imager", straight from Ubuntu, via the tutorials page... So I would do just like you did.
 - - I wanted 20.04 LTS, so I downloaded the 20.04 Server image through the imager...
 - - The imager does a Verify stage to make sure it is a successful image.

After it was complete, I put the card in my Pi, and booted the image. It does take a while to boot, but I immediately got text messaging on the screen. When it got to a login prompt... there was some extranious output occasionally from cloud init... but I ignored that and logged in with the default user and password... Where it prompted me to change to a new password.

I setup a static IP through NetPlan, setup my own user as an admin account, upgraded the system... Then installed Ubuntu Desktop. Rebooted and it has been running fine. The graphics and speed are not great... but it works. I've had desktops that were slower. I do notice small quirks every once in a while when I load things while Firefox is loaded. Like the screen goes mostly black... But if I move the mouse across the screen, it repaints the desktop(???)

Actually, Ubuntu Desktop is fairly heavy. I am surprised it runs so well on this. Sorry. That doesn't help you "yet."

The only other Imager, I have used for Pi is Etcher... But it seems that I have seen that "Raspberry Pi Imager" works okay. I like it.

---

### Post by hermansenn on 2021-07-22
Many thanks to you and your son for helping me through my problem.

The solution for me was to install the ubuntu server operating system as you did first and then install ubuntu desktop afterwards.

Everything is now working as I imagined it at first.

---

### Post by MAFoElffen on 2021-07-22
Good job!!! Very happy to hear that... Please remember to mark this as Solved, so others can find your solution.

Yes. My son talked me into my Pi4. Now I have it in the front room and am very happy with it. Currently running Gnome Sessions as my default desktop and KVM servere. Funny that the arm64 updates and packages are so much smaller than amd64.

---

