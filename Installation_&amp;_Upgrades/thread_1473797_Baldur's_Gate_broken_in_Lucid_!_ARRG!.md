---
title: "Baldur's Gate broken in Lucid ! ARRG!"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by xdevnull on 2010-05-05
I was happily playing Baldur's gate on Karmic, and was interested in continuing the story once I installed Lucid - but it was not to be.

I did a clean install of Lucid, installed wine from the SW center.  Installed BG with no problems.  Then when I click play, a splash screen comes up and freezes.  I have to xkill the window (it's set to manually run at 1024x768)  I have an Acer Aspire 1410 with Intel graphics -- GMA 950.  Here's the output.  Since xorg.conf is gone and there is no place to fiddle with the graphics driver anymore, I'm not sure what to try next.



fixme:win:EnumDisplayDevicesW ((null),0,0x339b04,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x139008,0x138f28): stub
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 268 requests (267 known processed) with 0 events remaining.
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  38 (X_QueryPointer)
  Resource id in failed request:  0x540000b
  Serial number of failed request:  810
  Current serial number in output stream:  810

---

