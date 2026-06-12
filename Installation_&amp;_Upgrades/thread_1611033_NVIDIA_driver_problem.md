---
title: "NVIDIA driver problem"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2010-11-01
I seem to get something like this every time I upgrade. I get the upgrade (10.10) and all my apps installed and working, but then try to install the NVIDIA driver without success. When I reboot after installing it, the system refuses to start and I see error messages saying that there are NVIDIA kernel problems and no monitor recognised.

I have tried using the 'Additional Drivers' utility and also installed from the command line, but neither seems to work.

I have an additional complication, which is that my monitor has never been automatically detected by the graphics board in the past and I have to force an EDID file by adding this to xorg.conf.

Can anyone give me a run-through of how I can install the NVIDIA driver and the EDID mod properly please, as I'm obviously not getting it right.

My current xorg.conf file looks like this:


Section "Module"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	Option         "CustomEDID" "DFP:/home/dave/edid.bin"
	Driver	"nv"
EndSection

---

### Post by gewitty on 2010-11-02
Since my initial post, I've been searching around to find a way to get the NVIDIA driver installed in 10.10. I found and downloaded the latest driver from the NVIDIA site ( NVIDIA-Linux-x86-260.19.12.run ) and then followed these instructions:

1. Choose the ‘Recovery Mode’ on GRUB.
2. Go to the bottom of menu list, choose ‘root console’.
3. Disable the Kernel Nouveau.

#echo options nouveau modeset=0 | sudo tee -a   etc/modprobe.d/nouveau-kms.conf
#update-initramfs -u

4. Change to init 3

#init 3

5. Install the NVIDIA driver

#sh NVIDIA-XXXXXX.run

6. Reboot Ubuntu.

The problem is that I still got an error saying that the Nouveau Kernel was enabled and the NVIDIA driver install was aborted.

I then tried adding Nouveau to the blacklist, which also had no effect.

Anyone got any ideas, because I'm running out?

---

### Post by Sylos on 2010-11-02
Hello there. Im no expert but I have seen this guide:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Perhaps worth a shot.

Also, this line is not what you want in you xorg.conf

```
Driver "nv"
```

That I think refers to the Nouveau driver. Just changing this following your attempt to install the driver from the GUI probabbly wont do it but it may be worth a shot. Might get lucky.

Good Luck

---

### Post by gewitty on 2010-11-02
As far as I know the driver reference, 'nv', means NVIDIA. However, I've taken out the whole xorg.conf file and tried to install the drivers by various means: the 'Additional Drivers' option in the 'Administration' menu; and also manually as described above. But so far, nothing works.

It appears that the Nouveau kernel issue is the source of the fault, but I can't figure out why I haven't been able to disable it using the blacklist or the terminal command shown above.

---

### Post by Sylos on 2010-11-02
I have never used 10.10 so Im not sure whether anything has changed but "nv" used to be the old reference to the open source driver rather than the one from the manufacturer. In the old days (when I last did it) you had to change this to say "NVIDIA" otherwise the .conf file is pointing to the wrong driver.

Unfortunately you are getting barred from installing it and I cant pretend to know any more than you about it (sorry). Just bear in mind the "nv" vs "NVIDIA" thing when you do get the driver installed in case it comes in handy.

Good Luck.

---

### Post by gewitty on 2010-11-02
Thanks for the tip. All I need now is to find a solution to the Nouveau kernel problem :P

If anyone has any ideas how I can get rid of it. I'd be grateful for suggestions.

---

### Post by Sylos on 2010-11-03
Just a thought:

did you remove/purge the previously installed NVIDIA packages before trying to install the new

```
sudo apt-get --purge remove nvidia-*


```

There could be remnants clogging up the process.

If I see anything more of interest I'll post a link to you.

---

### Post by gewitty on 2010-11-03
Yes, I tried that, but the problem still seems to be associated with Nouveau. I just found this in the Ubuntu Wiki, so I might give it a go:

"Sometimes it can be useful to disable nouveau to see if the computer boots correctly without it.

During boot hold down the shift key to get to the grub menu. Press the 'e' key to edit the boot command, and go down to the "kernel" line. Add "nouveau.modeset=0" to the end of the line containing "quiet splash", then press Ctrl+x to boot. Nouveau will be disabled for this boot.

If you want to disable nouveau in this way permanently you can run the following commands:

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u   
"

---

### Post by Sylos on 2010-11-03
Was doing some googling on your issue and found this

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

mentions using the following command

```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```


If you cant get rid of nouveau any other way I wonder if building a custom kernel without it might be a possible answer?

---

### Post by efflandt on 2010-11-03
You have not said which nvidia card/chip you have, so we don't know which driver you need (current or older).

But the easiest way to install nvidia 260.19.12, without having to worry about nouveau, would be to clean up and clear out whatever you have done (or reinstall) then:

[B]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update[/B]

That would make nvidia-current 260.19.12 instead of 260.19.06. Then go to System > Adminstration > Additional Drivers and "activate" nvidia.

PS: My xorg.conf is the real simple default nvidia one, but I use DVI to HDMI or HDMI, so I do not need a manual EDID:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

