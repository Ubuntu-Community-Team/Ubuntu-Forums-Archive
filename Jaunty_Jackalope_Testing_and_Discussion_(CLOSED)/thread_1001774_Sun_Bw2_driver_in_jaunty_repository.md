---
title: "Sun Bw2 driver in jaunty repository"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shirishagarwal on 2008-12-04
Hi all, 
 It seems people having Sun Machines have reason to be joyful. There are drivers for the same. 

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001531.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001531.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001532.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001532.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001533.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001533.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001534.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001534.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001535.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001535.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001536.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001536.html)

Wow 6 **NEW** drivers at one shot, this is cool.

---

### Post by tepsipakki on 2008-12-04
eh? they've "always" been there.. these are just rebuilds as you can see.

---

### Post by shirishagarwal on 2008-12-05
Are you sure, for my Intrepid search doesn't show them. 

```

~$ aptitude search xserver-xorg-video
v   xserver-xorg-video-2.9          -                                           
v   xserver-xorg-video-4            -                                           
i   xserver-xorg-video-all          - the X.Org X server -- output driver metapa
p   xserver-xorg-video-amd          - Geode GX2/LX display driver (dummy transit
p   xserver-xorg-video-amd-dbg      - Geode GX2/LX display driver (dummy transit
i   xserver-xorg-video-apm          - X.Org X server -- APM display driver      
i   xserver-xorg-video-ark          - X.Org X server -- ark display driver      
i   xserver-xorg-video-ati          - X.Org X server -- ATI display driver wrapp
p   xserver-xorg-video-ati-dbg      - X.Org X server -- ATI display driver wrapp
i   xserver-xorg-video-chips        - X.Org X server -- Chips display driver    
i   xserver-xorg-video-cirrus       - X.Org X server -- Cirrus display driver   
p   xserver-xorg-video-dummy        - X.Org X server -- dummy display driver    
i   xserver-xorg-video-fbdev        - X.Org X server -- fbdev display driver    
i   xserver-xorg-video-geode        - X.Org server -- Geode GX2/LX display drive
p   xserver-xorg-video-geode-dbg    - X.Org server -- Geode GX2/LX display drive
p   xserver-xorg-video-glint        - X.Org X server -- Glint display driver    
i   xserver-xorg-video-i128         - X.Org X server -- i128 display driver     
i   xserver-xorg-video-i740         - X.Org X server -- i740 display driver     
p   xserver-xorg-video-i810         - X.Org X server -- Intel i8xx, i9xx display
i   xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-intel-dbg    - X.Org X server -- Intel i8xx, i9xx display
p   xserver-xorg-video-ivtv         - X.Org X server -- IVTV display driver     
p   xserver-xorg-video-ivtv-dbg     - X.Org X server -- IVTV display driver (deb
i   xserver-xorg-video-mach64       - X.Org X server -- ATI Mach64 display drive
p   xserver-xorg-video-mach64-dbg   - X.Org X server -- ATI display driver (debu
i   xserver-xorg-video-mga          - X.Org X server -- MGA display driver      
i   xserver-xorg-video-neomagic     - X.Org X server -- Neomagic display driver 
p   xserver-xorg-video-nsc          - X.Org X server -- NSC Geode GX1 display dr
i   xserver-xorg-video-nv           - X.Org X server -- NV display driver       
i   xserver-xorg-video-openchrome   - X.Org X server -- VIA display driver      
i   xserver-xorg-video-r128         - X.Org X server -- ATI r128 display driver 
p   xserver-xorg-video-r128-dbg     - X.Org X server -- ATI r128 display driver 
i   xserver-xorg-video-radeon       - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeon-dbg   - X.Org X server -- ATI Radeon display drive
p   xserver-xorg-video-radeonhd     - X.Org X server -- AMD/ATI r5xx, r6xx displ
p   xserver-xorg-video-radeonhd-dbg - X.Org X server -- AMD/ATI r5xx, r6xx displ
i   xserver-xorg-video-rendition    - X.Org X server -- Rendition display driver
i   xserver-xorg-video-s3           - X.Org X server -- legacy S3 display driver
i   xserver-xorg-video-s3virge      - X.Org X server -- S3 ViRGE display driver 
i   xserver-xorg-video-savage       - X.Org X server -- Savage display driver   
i   xserver-xorg-video-siliconmotio - X.Org X server -- SiliconMotion display dr
i   xserver-xorg-video-sis          - X.Org X server -- SiS display driver      
i   xserver-xorg-video-sisusb       - X.Org X server -- SiS USB display driver  
i   xserver-xorg-video-tdfx         - X.Org X server -- tdfx display driver     
p   xserver-xorg-video-tga          - X.Org X server -- TGA display driver      
i   xserver-xorg-video-trident      - X.Org X server -- Trident display driver  
i   xserver-xorg-video-tseng        - X.Org X server -- Tseng display driver    
i   xserver-xorg-video-v4l          - X.Org X server -- Video 4 Linux display dr
i   xserver-xorg-video-vesa         - X.Org X server -- VESA display driver     
p   xserver-xorg-video-vga          - X.Org X server -- VGA display driver      
i   xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   
i   xserver-xorg-video-voodoo       - X.Org X server -- Voodoo display driver   

```

There is always the possibility that were under some other name in Intrepid. This is on an updated index of Intrepid. So if somebody knows something please lemme know.

---

### Post by tepsipakki on 2008-12-05
that's because they are only for the sparc architecture..

---

### Post by ShirishAg75 on 2008-12-05
oh, in that case its understandable then.

---

