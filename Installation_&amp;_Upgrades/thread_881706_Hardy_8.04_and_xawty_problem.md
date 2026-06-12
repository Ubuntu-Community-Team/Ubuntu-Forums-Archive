---
title: "Hardy 8.04 and xawty problem"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Midahed on 2008-08-06
Hi,

I'm trying to get a Logitech Quickcam Pro 9000 usb webcam working on my Ubuntu 8.04 Hardy installation.  My ultimate aim is to use it with Zoneminder, a prerequisite of which is that the webcam must work with xawtv.

So far, all I get is error messages :(

The webcam works with Ekiga, so the basic hardware is obviously working.  However, attempts to run xawtv with the -nodga option results in a brief flash of a black window before xawtv terminates:-

```
mike@HomePC:~$ xawtv -nodga
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
xinerama 0: 1024x768+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
v4l-conf had some trouble, trying to continue anyway
ioctl: VIDIOC_QUERYMENU(id=134217738;index=0;name="60 Hz";reserved=3081290080): Invalid argument
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb78781c0b7d71450 [PAL_I,PAL_D1,PAL_Nc,NTSC_M,SECAM_B,SECAM_D,SECAM_G,SECAM_K,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
Segmentation fault
mike@HomePC:~$ 
```

The webcam is correctly identified and recognised as a v4l2 device

```
mike@HomePC:~$ lsusb
Bus 005 Device 004: ID 046d:0990 Logitech, Inc. 
Bus 005 Device 003: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1241:1111 Belkin Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
mike@HomePC:~$ 
```

```
mike@HomePC:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.24-19-generic)
looking for available devices
port 73-73
    type : Xvideo, image scaler
    name : ATI Radeon Video Overlay

ioctl: VIDIOC_QUERYMENU(id=134217738;index=0;name="60 Hz";reserved=3081892192): Invalid argument
/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : UVC Camera (046d:0990)
    flags:  capture  

mike@HomePC:~$ 
```

Can anyone give me some pointers as to what might be wrong?

Do you have a Quickcam Pro 9000 working with xawtv on Hardy 8.04?

I thought that v4l2 devices were well supported in Hardy, so what am I missing?

In case it's relevant, I have a Radeon 9550 graphics card but I'm not using the ATI restricted fglrx driver.  Attempts to do so just seemed to make xawtv even more precarious. :(

Thanks,

Mike

---

### Post by Midahed on 2008-08-07
In the absence of any other replies, here's a bit more info for anyone who may be struggling with the same problem....

I never did get xawtv working with my webcam.  I may be wrong, but I suspect it's because xawtv doesn't support linux4video 2 devices.

I got Zoneminder working without needing to worry about xawtv at all:-

[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=882863[/COLOR]

---

