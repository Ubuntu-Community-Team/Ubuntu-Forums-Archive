---
title: "ZoneMinder Images Not Displaying After Upgrade to 12.10"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by sgharp on 2012-10-27
Hi Guys,

I recently upgraded from Ubuntu 12.04 to 12.10.  Now ZoneMinder appears to work but camera images don't display.  I can go directly to the IP address of the camera and it displays just fine using the internal software of the camera.  I'm assuming there is some dependency that ZoneMinder needs that was not upgraded or was removed during upgrade.

Can anyone suggest what might be missing or tell me how to determine what may have been removed during upgrade?

Thanks....

---

### Post by Eagle69 on 2012-11-02
Hi sgharp,

I am having the same issue when upgrading from Kubuntu 12.04 LTS (64-bit) to Kubuntu 12.10 (64-bit).  I have tried both Firefox and Chrome and neither will display the video.  I have also tried accessing the ZoneMinder site from a remote computer and had the same result.

Thanks

---

### Post by vertago1 on 2012-11-13
I am trying to setup ZoneMinder on ubuntu server 12.10 and I cannot get the camera to display images correctly.

From looking at v4l-info it looks like the camera is using jpeg 320 by 240. I have tried this setting as well as NTSC RGB24, but everything that shows up is just noise.

I can view the camera using xawtv.

lsusb shows the device as: 046d:08ad Logitech, Inc. QuickCam Communicate STX

v4l-info shows:
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "gspca_zc3xx"
        card                    : "USB Camera (046d:08ad)"
        bus_info                : "usb-0000:00:12.0-2"
        version                 : 3.5.7
        capabilities            : 0x85000001 [VIDEO_CAPTURE,READWRITE,STREAMING,(null)]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "gspca_zc3xx"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "JPEG"
        pixelformat             : 0x4745504a [JPEG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x4745504a [JPEG]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 320
        fmt.pix.sizeimage       : 29390
        fmt.pix.colorspace      : JPEG
        fmt.pix.priv            : 1
......

Maybe we are having related problems?

---

### Post by Eagle69 on 2012-11-14
> **vertago1 said:**
> I am trying to setup ZoneMinder on ubuntu server 12.10 and I cannot get the camera to display images correctly.

From looking at v4l-info it looks like the camera is using jpeg 320 by 240. I have tried this setting as well as NTSC RGB24, but everything that shows up is just noise.

I can view the camera using xawtv.

lsusb shows the device as: 046d:08ad Logitech, Inc. QuickCam Communicate STX

v4l-info shows:
### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "gspca_zc3xx"
        card                    : "USB Camera (046d:08ad)"
        bus_info                : "usb-0000:00:12.0-2"
        version                 : 3.5.7
        capabilities            : 0x85000001 [VIDEO_CAPTURE,READWRITE,STREAMING,(null)]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "gspca_zc3xx"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "JPEG"
        pixelformat             : 0x4745504a [JPEG]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x4745504a [JPEG]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 320
        fmt.pix.sizeimage       : 29390
        fmt.pix.colorspace      : JPEG
        fmt.pix.priv            : 1
......

Maybe we are having related problems?
Did you try setting your camera's capture palette to YUYV mode?  I was having issues getting my webcam (Logitech, USB) to even record in zoneminder and this mode seemed to work for me.

After changing that setting, the camera will record and work with motion detection, but it will still not show in a live stream mode in the browser.

---

### Post by Eagle69 on 2012-11-29
I have found a workaround to the video display problem with my installation.  It appears the issue has something to do with the authentication system for login.  When I disable the authenticate users options, the entire system, including video display, works properly.  If I re-enable the option the video will not display anymore.  If you are still having issues this might provide a workaround until the issue is addressed in an update.

---

### Post by t35t0r on 2013-04-17
Not related to ubuntu directly, but I got these same errors after updating php from the default centos 6 php (5.2?) to the ones used in remi's repo (5.4). 

```

Apr 17 13:11:08 serverName zms[1201]: INF [Debug Level = 0, Debug Log = <none>]
Apr 17 13:11:08 serverName zms[1201]: ERR [Unable to authenticate user]

```

I'm just going to use apache authentication to protect the ZM install instead. Looks like unless you want to venture into the zm svn versions, the "stable" versions haven't been updated in a long time.

---

