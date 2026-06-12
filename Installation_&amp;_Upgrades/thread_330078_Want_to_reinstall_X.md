---
title: "Want to reinstall X"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2007-01-02
I upgraded to the most recent version of Edgy a few days ago and then tried to install an X package or two, and now I get a black screen of death/snow crash sometimes when I switch between graphical virtual terminals or switch between workspaces.

Is there a way that I can get back where I was before the tinkering? Would it help to reinstall X, and if so, what is the proper way to do that?

I am using Gnome.

---

### Post by Jussi Kukkonen on 2007-01-02
You could try removing the "X package or two"... 

which display driver do you use?

Do you see anything suspicious in the logs after a crash (like /var/log/Xorg.?.log)

---

### Post by jonathanhayward on 2007-01-09
[QUOTE]You could try removing the "X package or two"...

which display driver do you use?[QUOTE]

I think I may have changed that trying to get Beryl working.

How do I query what display driver I'm using and revert if I changed it to something that doesn't work?

The last line of the log before a crash is:

(**) RADEON(0): EngineRestore (32/32)

After, the line above followed by:

(**) RADEON(0): RADEONSaveScreen(2)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) RADEON(0): RADEONSwitchMode() !n(**) RADEON(0): RADEONModeInit()
800x600       108.00   800 34208 34320 1688   600 1050 1053 1063 (24,32)
800x600       108.00   800 34208 34320 1688   600 1050 1053 1063 (24,32)
(**) RADEON(0): Pitch = 11534512 bytes (virtualX = 1280, displayWidth = 1408)
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81ff670
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81ff670)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0xe0ffe000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20025c5c to 20135c5c
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fecc0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0xffff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x003fffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x0000003c 0x000301f7 0x00000000 (0x0000a700)
(**) RADEON(0): Wrote: rd=60, fd=503, pd=3
(**) RADEON(0): Ok, leaving now...

---

