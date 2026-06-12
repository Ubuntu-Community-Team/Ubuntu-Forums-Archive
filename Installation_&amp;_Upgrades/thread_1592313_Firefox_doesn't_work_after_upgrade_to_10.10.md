---
title: "Firefox doesn't work after upgrade to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by good_man on 2010-10-10
Hey all,

After upgrading to Marevick 10.10 I can't launch firefox, running firefox from terminal revelas the following error:

```
/usr/lib/firefox-3.6.10/firefox-bin: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_source_set_name
```

I assume it's libgdk error, googling this error doesn't return relevant information.

running:
```
ldd /usr/lib/libgdk-x11-2.0.so.0
```

returns the following:
 ```
       linux-gate.so.1 =>  (0x00f1c000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x006dd000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00121000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x0028b000)
        libm.so.6 => /lib/libm.so.6 (0x00600000)
        libpng12.so.0 => /lib/libpng12.so.0 (0x008a0000)
        libgio-2.0.so.0 => /usr/local/lib/libgio-2.0.so.0 (0x00a0e000)
        libgobject-2.0.so.0 => /usr/local/lib/libgobject-2.0.so.0 (0x00987000)
        libgmodule-2.0.so.0 => /usr/local/lib/libgmodule-2.0.so.0 (0x00302000)
        libgthread-2.0.so.0 => /usr/local/lib/libgthread-2.0.so.0 (0x0065c000)
        librt.so.1 => /lib/librt.so.1 (0x008d0000)
        libglib-2.0.so.0 => /usr/local/lib/libglib-2.0.so.0 (0x00c24000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00163000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x003f1000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00710000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00110000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0x00193000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00ed4000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00afd000)
        libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00ee6000)
        libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00f74000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00b23000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0x004d5000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x0071a000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00dca000)
        libc.so.6 => /lib/libc.so.6 (0x00f78000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00d6c000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00e3d000)                                                                                               
        libz.so.1 => /lib/libz.so.1 (0x001a1000)                                                                                                                 
        /lib/ld-linux.so.2 (0x00d31000)                                                                                                                          
        libdl.so.2 => /lib/libdl.so.2 (0x00114000)                                                                                                               
        libresolv.so.2 => /lib/libresolv.so.2 (0x001b6000)                                                                                                       
        libexpat.so.1 => /lib/libexpat.so.1 (0x003b9000)                                                                                                         
        libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x001ca000)                                                                                               
        libxcb-shm.so.0 => /usr/lib/libxcb-shm.so.0 (0x00b65000)                                                                                                 
        libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00118000)                                                                                           
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0x0022a000)                                                                                                         
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00339000)                                                                                                         
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00d10000)                                                 
```

---

### Post by dino99 on 2010-10-10
check your repos: synaptic repo tab, be sure to only use genuine maverick repo (drop out ppa if any) then update and select "firefox" for reinstallation

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by good_man on 2010-10-10
The bad thing is synaptic also not working! anyhow I tried to view sources.list from terminal, it containes:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
```


I didn't get what you mean by reinstalling firefox, did you mean remove/install FF, if so it's a disaster :\

I executed the commands:
sudo apt-get install -f
sudo dpkg --configure -a

several times, with no results.

Thanks for the help.

---

### Post by good_man on 2010-10-11
Thanks [dino99]("http://ubuntuforums.org/member.php?u=129712"), AFAICT it's compatibility problem between libraries in /usr/lib and /usr/local/lib , I removed all libraries under /usr/local/lib (I took a backup first), and after restarting all things back to normal :) FF is working as well as Google Chrome.

---

