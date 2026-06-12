---
title: "Kernel image update breaks Display"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by motobeats on 2013-07-04
I am using an Intel x86 64 bit board with the 4000 GPU for 12.04. For my display I am using my Sony LCD TV. When I apply this update:

Start-Date: 2013-07-04  09:10:11
Commandline: aptdaemon role='role-commit-packages' sender=':1.48'
Install: linux-image-3.5.0-34-generic:amd64 (3.5.0-34.55~precise1)
End-Date: 2013-07-04  09:10:43

I get the following error after reboot and my preferred resolution option (and a bunch of others) in Display are gone. I plan to roll back the update, but thoughts on what the issue may be? 



> 

Could not apply the stored configuration for monitors

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 63
CRTC 63: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 63: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 63: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
Trying modes for CRTC 64
CRTC 64: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 64: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 64: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
Trying modes for CRTC 65
CRTC 65: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 0)
CRTC 65: trying mode 1920x1080@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1920x1080@24Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1920x1080@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1280x1024@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1280x720@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1024x768@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 1440x480@30Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 800x600@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 720x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)
CRTC 65: trying mode 640x480@60Hz with output at 1360x768@60Hz (pass 1)



---

### Post by dino99 on 2013-07-04
why dont you let the kernel setting itself the good choices ?

sudo rm /etc/X11/xorg.conf

---

### Post by motobeats on 2013-07-04
I have not created xorg.conf (does not exist by default)

```
andrew@Ubuntu-TV:~$ ls /etc/X11 -la
total 88
drwxr-xr-x  10 root root  4096 Feb 13 17:10 .
drwxr-xr-x 128 root root 12288 Jul  4 09:48 ..
drwxr-xr-x   2 root root  4096 Feb 13 17:10 app-defaults
drwxr-xr-x   2 root root  4096 Feb 13 17:10 cursors
-rw-r--r--   1 root root    18 Feb 13 17:09 default-display-manager
drwxr-xr-x   4 root root  4096 Feb 13 17:09 fonts
-rw-r--r--   1 root root 17394 Dec  3  2009 rgb.txt
lrwxrwxrwx   1 root root    13 Jul  3 21:29 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 Feb 13 17:10 xinit
drwxr-xr-x   2 root root  4096 Jan 23  2012 xkb
-rwxr-xr-x   1 root root   709 Apr  1  2010 Xreset
drwxr-xr-x   2 root root  4096 Feb 13 17:09 Xreset.d
drwxr-xr-x   2 root root  4096 Feb 13 17:09 Xresources
-rwxr-xr-x   1 root root  3730 Jan 20  2012 Xsession
drwxr-xr-x   2 root root  4096 Jul  4 09:02 Xsession.d
-rw-r--r--   1 root root   265 Jul  1  2008 Xsession.options
-rw-r--r--   1 root root   601 Feb 13 17:09 Xwrapper.config
```

---

