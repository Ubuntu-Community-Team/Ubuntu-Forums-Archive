---
title: "Issue with installing Picasa on my UNR 10.10"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by swapnilnarendra on 2011-03-06
I am using an Acer Aspire One netbook running UNR 10.10.
My previous Ubuntu 10.04 messed up while updating so I installed a fresh copy on my netbook and have been running since. Had some updation issues on this one too but **Old_Gray_Wolf** helped me with those and I am thankful to him :)

However, one issue remains unresolved, I am unable to install and use Picasa on my new Ubuntu 10.10. I tried so many times and the installation ran fine, telling me that the program has been installed. But I am not able to locate Picasa on my netbook anywhere. It doesnt show up in my menu (Unity) and also there are no files for 'google' or 'picasa' whatsoever in my file system.

Have tried a few steps, suggested by **Old_Gray_Wolf** but none of them seem to work yet. Please go through this thread if you like to see what I have done. 
[http://ubuntuforums.org/showthread.php?t=1698370](http://ubuntuforums.org/showthread.php?t=1698370)
*(it was a thread which I started for updation issue. but since the topic changed to Picasa's installation, I was asked to start  a new thread)*

Now the latest question asked to me was, if I have installed WINE ?

- No SIR ! I have not and to be honest I am trying to avoid WINE on my system now as it was an update of WINE (which I think) messed up my system last time.

Please help :)
(and a HUGE THANK to **Old_Gray_Wolf** for helping me this far) :KS

---

### Post by swapnilnarendra on 2011-03-06
posted this same issue on stackexchange.com and got the solution.. 
here is the link for my question..
[http://askubuntu.com/questions/29313/picasa-installs-but-is-missing-in-the-menu](http://askubuntu.com/questions/29313/picasa-installs-but-is-missing-in-the-menu)


all thanks to Jorge and Octavian for their quick help :D
:popcorn::KS:guitar:

---

### Post by Old_Grey_Wolf on 2011-03-06
I am glad you got that problem fixed. I don't know very much about Unity; therefore, I couldn't be helpful. :)

---

### Post by swapnilnarendra on 2011-03-07
dont say you weren't helpful my friend..infact you were the only one who helped me here :)
I am really thankful to you !

---

### Post by Old_Grey_Wolf on 2011-03-07
> **swapnilnarendra said:**
> dont say you weren't helpful my friend..infact you were the only one who helped me here :)
I am really thankful to you !

I was referring to the issue with Picasa were I could not be of any help. As far as the other issues you had, I was knowledgeable about them and could help.

---

### Post by Dutch70 on 2011-03-07
Try opening a terminal and type in...
```
locate picasa
```

That should at least tell you where the file is stored on your machine.

Post the output with #(code) tags around it & someone should be able to help you get it into your menu, or your panel.

---

### Post by swapnilnarendra on 2011-03-08
here is what In got after 'locate picasa' command:

```
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/entityTables/transliterate.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/fontEncoding.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/fontNameMap.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfont.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontCMEX10.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontCMSY10.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontMTExtra.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontMath1.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontMath2.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontMath4.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontPUA.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/fonts/mathfontSymbol.properties
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-audio.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-binary.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-find.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-image.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-menu.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-movie.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-sound.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-telnet.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-text.gif
/opt/google/picasa/3.0/wine/drive_c/Program Files/wine_gecko/res/html/gopher-unknown.gif
/opt/google/picasa/3.0/wine/drive_c/windows/command
/opt/google/picasa/3.0/wine/drive_c/windows/fonts
/opt/google/picasa/3.0/wine/drive_c/windows/inf
/opt/google/picasa/3.0/wine/drive_c/windows/profiles
/opt/google/picasa/3.0/wine/drive_c/windows/system
/opt/google/picasa/3.0/wine/drive_c/windows/system32
/opt/google/picasa/3.0/wine/drive_c/windows/temp
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/Vera.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraBI.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraBd.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraIt.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraMoBI.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraMoBd.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraMoIt.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraMono.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraSe.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/VeraSeBd.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/marlett.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/fonts/wineding.ttf
/opt/google/picasa/3.0/wine/drive_c/windows/inf/mozctl.inf
/opt/google/picasa/3.0/wine/drive_c/windows/inf/picasa.inf
/opt/google/picasa/3.0/wine/drive_c/windows/inf/pxhelp20.inf
/opt/google/picasa/3.0/wine/drive_c/windows/inf/wine.inf
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu/Programs
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3/Configure Picasa Photo Viewer.lnk
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3/Picasa 3.lnk
/opt/google/picasa/3.0/wine/drive_c/windows/profiles/All Users/Start Menu/Programs/Picasa 3/Uninstall.lnk
/opt/google/picasa/3.0/wine/drive_c/windows/system32/GPhotos.scr
/opt/google/picasa/3.0/wine/drive_c/windows/system32/IOSUBSYS
/opt/google/picasa/3.0/wine/drive_c/windows/system32/drivers
/opt/google/picasa/3.0/wine/drive_c/windows/system32/px.dll
/opt/google/picasa/3.0/wine/drive_c/windows/system32/pxdrv.dll
/opt/google/picasa/3.0/wine/drive_c/windows/system32/pxhpinst.exe
/opt/google/picasa/3.0/wine/drive_c/windows/system32/pxmas.dll
/opt/google/picasa/3.0/wine/drive_c/windows/system32/pxwave.dll
/opt/google/picasa/3.0/wine/drive_c/windows/system32/vxblock.dll
/opt/google/picasa/3.0/wine/drive_c/windows/system32/IOSUBSYS/pxhelper.vxd
/opt/google/picasa/3.0/wine/drive_c/windows/system32/drivers/cdr4_xp.sys
/opt/google/picasa/3.0/wine/drive_c/windows/system32/drivers/cdralw2k.sys
/opt/google/picasa/3.0/wine/drive_c/windows/system32/drivers/pxhelp20.sys
/opt/google/picasa/3.0/wine/lib/libwine.so.1
/opt/google/picasa/3.0/wine/lib/libwine.so.1.0
/opt/google/picasa/3.0/wine/lib/wine
/opt/google/picasa/3.0/wine/lib/wine/acledit.dll.so
/opt/google/picasa/3.0/wine/lib/wine/activeds.dll.so
/opt/google/picasa/3.0/wine/lib/wine/actxprxy.dll.so
/opt/google/picasa/3.0/wine/lib/wine/advapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/advpack.dll.so
/opt/google/picasa/3.0/wine/lib/wine/amstream.dll.so
/opt/google/picasa/3.0/wine/lib/wine/appwiz.cpl.so
/opt/google/picasa/3.0/wine/lib/wine/atl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/avicap32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/avifil32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/avifile.dll16
/opt/google/picasa/3.0/wine/lib/wine/browser_prompt.exe.so
/opt/google/picasa/3.0/wine/lib/wine/browseui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cabinet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/capi2032.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cards.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cfgmgr32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/check_dir.exe.so
/opt/google/picasa/3.0/wine/lib/wine/clock.exe.so
/opt/google/picasa/3.0/wine/lib/wine/clusapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cmd.exe.so
/opt/google/picasa/3.0/wine/lib/wine/comcat.dll.so
/opt/google/picasa/3.0/wine/lib/wine/comctl32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/comdlg32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/comm.drv16
/opt/google/picasa/3.0/wine/lib/wine/commdlg.dll16
/opt/google/picasa/3.0/wine/lib/wine/compobj.dll16
/opt/google/picasa/3.0/wine/lib/wine/compstui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/control.exe.so
/opt/google/picasa/3.0/wine/lib/wine/credui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/crtdll.dll.so
/opt/google/picasa/3.0/wine/lib/wine/crypt32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cryptdlg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cryptdll.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cryptnet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/cryptui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ctapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ctl3d.dll16
/opt/google/picasa/3.0/wine/lib/wine/ctl3d32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ctl3dv2.dll16
/opt/google/picasa/3.0/wine/lib/wine/d3d10.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3d8.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3d9.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dim.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3drm.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx8.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_24.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_25.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_26.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_27.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_28.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_29.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_30.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_31.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_33.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_34.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_35.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_36.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dx9_37.dll.so
/opt/google/picasa/3.0/wine/lib/wine/d3dxof.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dbghelp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dciman32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ddeml.dll16
/opt/google/picasa/3.0/wine/lib/wine/ddraw.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ddrawex.dll.so
/opt/google/picasa/3.0/wine/lib/wine/desk.cpl.so
/opt/google/picasa/3.0/wine/lib/wine/devenum.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dinput.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dinput8.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dispdib.dll16
/opt/google/picasa/3.0/wine/lib/wine/display.drv16
/opt/google/picasa/3.0/wine/lib/wine/dmband.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmcompos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmime.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmloader.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmstyle.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmsynth.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dmusic32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dnsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplay.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dplayx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnaddr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnhpast.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpnlobby.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dpwsockx.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dsound.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dssenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dswave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dwmapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxdiagn.dll.so
/opt/google/picasa/3.0/wine/lib/wine/dxgi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/eject.exe.so
/opt/google/picasa/3.0/wine/lib/wine/expand.exe.so
/opt/google/picasa/3.0/wine/lib/wine/explorer.exe.so
/opt/google/picasa/3.0/wine/lib/wine/faultrep.dll.so
/opt/google/picasa/3.0/wine/lib/wine/fusion.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdi.exe16
/opt/google/picasa/3.0/wine/lib/wine/gdi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gdiplus.dll.so
/opt/google/picasa/3.0/wine/lib/wine/glu32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/gphoto2.ds.so
/opt/google/picasa/3.0/wine/lib/wine/gpkcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hal.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hh.exe.so
/opt/google/picasa/3.0/wine/lib/wine/hhctrl.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/hid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hlink.dll.so
/opt/google/picasa/3.0/wine/lib/wine/hnetcfg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iccvid.dll.so
/opt/google/picasa/3.0/wine/lib/wine/icinfo.exe.so
/opt/google/picasa/3.0/wine/lib/wine/icmp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iexplore.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ifsmgr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/imaadp32.acm.so
/opt/google/picasa/3.0/wine/lib/wine/imagehlp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/imm.dll16
/opt/google/picasa/3.0/wine/lib/wine/imm32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inetcomm.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inetmib1.dll.so
/opt/google/picasa/3.0/wine/lib/wine/infosoft.dll.so
/opt/google/picasa/3.0/wine/lib/wine/initpki.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inkobj.dll.so
/opt/google/picasa/3.0/wine/lib/wine/inseng.dll.so
/opt/google/picasa/3.0/wine/lib/wine/iphlpapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/itircl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/itss.dll.so
/opt/google/picasa/3.0/wine/lib/wine/jscript.dll.so
/opt/google/picasa/3.0/wine/lib/wine/kernel32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/keyboard.drv16
/opt/google/picasa/3.0/wine/lib/wine/krnl386.exe16
/opt/google/picasa/3.0/wine/lib/wine/license.exe.so
/opt/google/picasa/3.0/wine/lib/wine/localspl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/localui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/lz32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/lzexpand.dll16
/opt/google/picasa/3.0/wine/lib/wine/mapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciavi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mcicda.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciseq.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mciwave.dll.so
/opt/google/picasa/3.0/wine/lib/wine/midimap.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mlang.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mmdevldr.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/mmsystem.dll16
/opt/google/picasa/3.0/wine/lib/wine/monodebg.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/mountmgr.sys.so
/opt/google/picasa/3.0/wine/lib/wine/mouse.drv16
/opt/google/picasa/3.0/wine/lib/wine/mpr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mprapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msacm.dll16
/opt/google/picasa/3.0/wine/lib/wine/msacm32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msacm32.drv.so
/opt/google/picasa/3.0/wine/lib/wine/msadp32.acm.so
/opt/google/picasa/3.0/wine/lib/wine/mscat32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mscms.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mscoree.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msdmo.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msftedit.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msg711.acm.so
/opt/google/picasa/3.0/wine/lib/wine/mshtml.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mshtml.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/msi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msiexec.exe.so
/opt/google/picasa/3.0/wine/lib/wine/msimg32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msimtf.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msisip.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msisys.ocx.so
/opt/google/picasa/3.0/wine/lib/wine/msnet32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msrle32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mssip32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/mstask.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcirt.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcr71.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt20.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrt40.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvcrtd.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvfw32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvidc32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msvideo.dll16
/opt/google/picasa/3.0/wine/lib/wine/mswsock.dll.so
/opt/google/picasa/3.0/wine/lib/wine/msxml3.dll.so
/opt/google/picasa/3.0/wine/lib/wine/nddeapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/net.exe.so
/opt/google/picasa/3.0/wine/lib/wine/netapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/newdev.dll.so
/opt/google/picasa/3.0/wine/lib/wine/notepad.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ntdll.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ntdsapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ntoskrnl.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ntprint.dll.so
/opt/google/picasa/3.0/wine/lib/wine/objsel.dll.so
/opt/google/picasa/3.0/wine/lib/wine/odbc32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/odbccp32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ole2.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2conv.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2disp.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2nls.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2prox.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole2thk.dll16
/opt/google/picasa/3.0/wine/lib/wine/ole32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleacc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleaut32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olecli.dll16
/opt/google/picasa/3.0/wine/lib/wine/olecli32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oledlg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olepro32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olesvr.dll16
/opt/google/picasa/3.0/wine/lib/wine/olesvr32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/olethk32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/oleview.exe.so
/opt/google/picasa/3.0/wine/lib/wine/opengl32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/pdh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/powrprof.dll.so
/opt/google/picasa/3.0/wine/lib/wine/printui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/progman.exe.so
/opt/google/picasa/3.0/wine/lib/wine/propsys.dll.so
/opt/google/picasa/3.0/wine/lib/wine/psapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/pstorec.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qcap.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qedit.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qmgr.dll.so
/opt/google/picasa/3.0/wine/lib/wine/qmgrprxy.dll.so
/opt/google/picasa/3.0/wine/lib/wine/quartz.dll.so
/opt/google/picasa/3.0/wine/lib/wine/query.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rasapi16.dll16
/opt/google/picasa/3.0/wine/lib/wine/rasapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/reg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/regedit.exe.so
/opt/google/picasa/3.0/wine/lib/wine/regsvr32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/resutils.dll.so
/opt/google/picasa/3.0/wine/lib/wine/riched20.dll.so
/opt/google/picasa/3.0/wine/lib/wine/riched32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rpcrt4.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rpcss.exe.so
/opt/google/picasa/3.0/wine/lib/wine/rsabase.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rsaenh.dll.so
/opt/google/picasa/3.0/wine/lib/wine/rundll32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/sane.ds.so
/opt/google/picasa/3.0/wine/lib/wine/sccbase.dll.so
/opt/google/picasa/3.0/wine/lib/wine/schannel.dll.so
/opt/google/picasa/3.0/wine/lib/wine/secedit.exe.so
/opt/google/picasa/3.0/wine/lib/wine/secur32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/security.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sensapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/serialui.dll.so
/opt/google/picasa/3.0/wine/lib/wine/services.exe.so
/opt/google/picasa/3.0/wine/lib/wine/set_lang.exe.so
/opt/google/picasa/3.0/wine/lib/wine/setupapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/setupx.dll16
/opt/google/picasa/3.0/wine/lib/wine/sfc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sfc_os.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shdoclc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shdocvw.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shell.dll16
/opt/google/picasa/3.0/wine/lib/wine/shell32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shfolder.dll.so
/opt/google/picasa/3.0/wine/lib/wine/shlwapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/slbcsp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/slc.dll.so
/opt/google/picasa/3.0/wine/lib/wine/snmpapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/softpub.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sound.drv16
/opt/google/picasa/3.0/wine/lib/wine/spoolss.dll.so
/opt/google/picasa/3.0/wine/lib/wine/spoolsv.exe.so
/opt/google/picasa/3.0/wine/lib/wine/start.exe.so
/opt/google/picasa/3.0/wine/lib/wine/stdole2.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/stdole32.tlb.so
/opt/google/picasa/3.0/wine/lib/wine/sti.dll.so
/opt/google/picasa/3.0/wine/lib/wine/storage.dll16
/opt/google/picasa/3.0/wine/lib/wine/stress.dll16
/opt/google/picasa/3.0/wine/lib/wine/svchost.exe.so
/opt/google/picasa/3.0/wine/lib/wine/svrapi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/sxs.dll.so
/opt/google/picasa/3.0/wine/lib/wine/system.drv16
/opt/google/picasa/3.0/wine/lib/wine/tapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/taskmgr.exe.so
/opt/google/picasa/3.0/wine/lib/wine/toolhelp.dll16
/opt/google/picasa/3.0/wine/lib/wine/twain.dll16
/opt/google/picasa/3.0/wine/lib/wine/twain_32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/typelib.dll16
/opt/google/picasa/3.0/wine/lib/wine/unicows.dll.so
/opt/google/picasa/3.0/wine/lib/wine/uninstaller.exe.so
/opt/google/picasa/3.0/wine/lib/wine/url.dll.so
/opt/google/picasa/3.0/wine/lib/wine/urlmon.dll.so
/opt/google/picasa/3.0/wine/lib/wine/user.exe16
/opt/google/picasa/3.0/wine/lib/wine/user32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/userenv.dll.so
/opt/google/picasa/3.0/wine/lib/wine/usp10.dll.so
/opt/google/picasa/3.0/wine/lib/wine/uxtheme.dll.so
/opt/google/picasa/3.0/wine/lib/wine/vdhcp.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vdmdbg.dll.so
/opt/google/picasa/3.0/wine/lib/wine/ver.dll16
/opt/google/picasa/3.0/wine/lib/wine/version.dll.so
/opt/google/picasa/3.0/wine/lib/wine/vmm.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vnbt.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vnetbios.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vtdapi.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/vwin32.vxd.so
/opt/google/picasa/3.0/wine/lib/wine/w32skrnl.dll.so
/opt/google/picasa/3.0/wine/lib/wine/w32sys.dll16
/opt/google/picasa/3.0/wine/lib/wine/wdi.exe.so
/opt/google/picasa/3.0/wine/lib/wine/win32s16.dll16
/opt/google/picasa/3.0/wine/lib/wine/win87em.dll16
/opt/google/picasa/3.0/wine/lib/wine/winaspi.dll16
/opt/google/picasa/3.0/wine/lib/wine/windebug.dll16
/opt/google/picasa/3.0/wine/lib/wine/winealsa.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineaudioio.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineboot.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winebrowser.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winecfg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineconsole.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winecoreaudio.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wined3d.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winedbg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winedevice.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winedos.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winedumpfontver.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineesd.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winefile.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winefontcfg.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winejack.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winejoystick.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winemenubuilder.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winemine.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winemp3.acm.so
/opt/google/picasa/3.0/wine/lib/wine/winenas.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineoss.drv.so
/opt/google/picasa/3.0/wine/lib/wine/winepath.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wineps.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wineps16.drv16
/opt/google/picasa/3.0/wine/lib/wine/winevdm.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winex11.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wing.dll16
/opt/google/picasa/3.0/wine/lib/wine/wing32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winhelp.exe16
/opt/google/picasa/3.0/wine/lib/wine/winhlp32.exe.so
/opt/google/picasa/3.0/wine/lib/wine/winhttp.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wininet.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winmm.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winnls.dll16
/opt/google/picasa/3.0/wine/lib/wine/winnls32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winoldap.mod16
/opt/google/picasa/3.0/wine/lib/wine/winscard.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winsock.dll16
/opt/google/picasa/3.0/wine/lib/wine/winspool.drv.so
/opt/google/picasa/3.0/wine/lib/wine/wintab.dll16
/opt/google/picasa/3.0/wine/lib/wine/wintab32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wintrust.dll.so
/opt/google/picasa/3.0/wine/lib/wine/winver.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wldap32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wmi.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wnaspi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wordpad.exe.so
/opt/google/picasa/3.0/wine/lib/wine/wow32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wprocs.dll16
/opt/google/picasa/3.0/wine/lib/wine/write.exe.so
/opt/google/picasa/3.0/wine/lib/wine/ws2_32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wsock32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/wtsapi32.dll.so
/opt/google/picasa/3.0/wine/lib/wine/xcopy.exe.so
/opt/google/picasa/3.0/wine/share/applications
/opt/google/picasa/3.0/wine/share/man
/opt/google/picasa/3.0/wine/share/wine
/opt/google/picasa/3.0/wine/share/applications/wine.desktop
/opt/google/picasa/3.0/wine/share/man/de.UTF-8
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8
/opt/google/picasa/3.0/wine/share/man/man1
/opt/google/picasa/3.0/wine/share/man/de.UTF-8/man1
/opt/google/picasa/3.0/wine/share/man/de.UTF-8/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/fr.UTF-8/man1/wineserver.1
/opt/google/picasa/3.0/wine/share/man/man1/wine.1
/opt/google/picasa/3.0/wine/share/man/man1/winedbg.1
/opt/google/picasa/3.0/wine/share/man/man1/wineprefixcreate.1
/opt/google/picasa/3.0/wine/share/man/man1/wineserver.1
/opt/google/picasa/3.0/wine/share/wine/fonts
/opt/google/picasa/3.0/wine/share/wine/generic.ppd
/opt/google/picasa/3.0/wine/share/wine/wine.inf
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coue1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coure.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/couree.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/coureg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/courer.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/couret.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/cvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/hvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/jsmalle.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/jvgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/marlett.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smae1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smalle.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smallee.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smalleg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smaller.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/smallet.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/ssee874.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserife.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifee.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifeg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifer.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/sserifet.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/svgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/tahoma.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/tahomabd.ttf
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1255.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1256.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas1257.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgas874.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasys.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasyse.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasysg.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasysr.fon
/opt/google/picasa/3.0/wine/share/wine/fonts/vgasyst.fon
/usr/bin/picasa
/usr/lib/xscreensaver/showpicasascreensaver
/usr/share/applications/picasa-fontcfg.desktop
/usr/share/applications/picasa.desktop
/usr/share/apps/konqueror/servicemenus/picasa-kdehal.desktop
/usr/share/desktop-directories/picasa.directory
/usr/share/gconf/schemas/picasa.schemas
/var/lib/dpkg/info/picasa.list
/var/lib/dpkg/info/picasa.md5sums
/var/lib/dpkg/info/picasa.postinst
/var/lib/dpkg/info/picasa.postrm
/var/lib/dpkg/info/picasa.preinst
/var/lib/dpkg/info/picasa.prerm
```

---

### Post by Dutch70 on 2011-03-08
Well, I don't know anything about Wine, except that it gives me a headache. :?

That being said & since you have no other answers. Try opening a terminal and type in "picasa" and hit enter. Any non-wine program would open. If it does, you may be able to add it to your menu or panel.

---

