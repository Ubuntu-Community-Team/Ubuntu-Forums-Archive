---
title: "Uninstalling the driver from ATI Website"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Ultra_Man on 2010-05-15
I don't know where else to put this. D:

I have a new powercolor HD 5670, installed the drivers from amd's website. It's not working and I need to uninstall it and install the fglrx that comes with ubuntu.

---

### Post by quadproc on 2010-05-15
> **Ultra_Man said:**
> I don't know where else to put this. D:

I have a new powercolor HD 5670, installed the drivers from amd's website. It's not working and I need to uninstall it and install the fglrx that comes with ubuntu.
If your installation was a normal one then you will find a file called
```
/usr/share/ati/fglrx-uninstall.sh
```
If you run this file this way then the uninstall should happen:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

quadproc

---

### Post by Ultra_Man on 2010-05-15
Gee thanks. I remember seeing that path after the installation. I guess I should have read it.

---

### Post by Ultra_Man on 2010-05-15
It's not working D:

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

---

### Post by quadproc on 2010-05-15
> **Ultra_Man said:**
> It's not working D:

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati. 
This is not good.  I will insert a copy of the standard install path default file below.  You might be able to determine where the files ended up on your system by using the Places > Search for files function.

```
# /etc/ati/inst_path_default
#
# Created Fri Apr  2 14:22:07 PDT 2010 with the following configuration:
#
# Driver version: 8.712
# Default policy
# Policy version: default:v2:x86_64:lib32:x740_64a:none:2.6.31-20-generic:modular

# X_VERSION and _ARCH set by check.sh
       X_VERSION=x740_64a
           _ARCH=x86_64

     ATI_XLIB_32=/usr/lib32
     ATI_XLIB_64=/usr/lib64
     ATI_XLIB_EXT_32=/usr/lib32/xorg/modules/extensions
     ATI_XLIB_EXT_64=/usr/lib64/xorg/modules/extensions
   ATI_3D_DRV_32=/usr/lib32/dri
   ATI_3D_DRV_64=/usr/lib64/dri
        ATI_XLIB=/usr/lib64
       ATI_X_BIN=/usr/bin
        ATI_SBIN=/usr/sbin
    ATI_KERN_MOD=/lib/modules/fglrx
      ATI_2D_DRV=/usr/lib64/xorg/modules/drivers
    ATI_X_MODULE=/usr/lib64/xorg/modules
     ATI_DRM_LIB=/usr/lib64/xorg/modules/linux
      ATI_CP_LNK=/usr/share/applications
 ATI_CP_KDE3_LNK=/opt/kde3/share/applnk
  ATI_GL_INCLUDE=/usr/include/GL
  ATI_ATIGL_INCLUDE=/usr/include/ATI/GL
  ATI_CP_KDE_LNK=/usr/share/applnk
         ATI_DOC=/usr/share/doc/ati
      ATI_CP_DOC=/usr/share/doc/ati
ATI_CP_GNOME_LNK=/usr/share/gnome/apps
        ATI_ICON=/usr/share/icons
         ATI_MAN=/usr/share/man
         ATI_SRC=/usr/src/ati
 ATI_X11_INCLUDE=/usr/include/X11/extensions
      ATI_CP_BIN=/usr/bin
     ATI_CP_I18N=/usr/share/ati/amdcccle
         ATI_LIB=/usr/share/ati/lib64     
         ATI_LOG=/usr/share/ati
      ATI_CONFIG=/etc/ati
      ATI_UNINST=/usr/share/ati
```Another thing to look for: if you have an xorg.conf file then it should specify which driver is in use.  You will need to be using something other than fglrx when you are removing the old driver.  I found that the "ati" driver worked well enough for that purpose.  To see what is in the xorg.conf, type this:
```
grep "river" < /etc/X11/xorg.conf
```and look for a non-commented driver line.

quadproc

---

