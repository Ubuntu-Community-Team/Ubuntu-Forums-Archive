---
title: "Bug in 8.10 Beta"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by HLEBARKATA on 2008-10-17
I have installed wine 1.1.6(exists in all ver) 
e.g in the game unreal II the game crashes on startup because of no 
permissions opening the sound device
LSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

fixme:process:GetProcessWorkingSetSize (0xffffffff,0x43f3d4,0x43f3d0): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x43cae8,0x00000000), stub!
fixme:dmime:IDirectMusicPerformance8Impl_InitAudio (0x14c3c0, (nil), (nil), (nil), 8, 128, 3f, (nil)): to check
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14c118,0x14c958): stub
fixme:dmime:IDirectMusicPerformance8Impl_InitAudio return dsound(0x147208,0)
fixme:dmime:IDirectMusicPerformance8Impl_Init (iface = 0x14c3c0, dmusic = (nil), dsound = 0x147208, hwnd = (nil))
fixme:dmime:IDirectMusicPerformance8Impl_CreateStandardAudioPath (0x14c3c0)->(8, 128, 0, 0x14c58c): semi-stub
fixme:dmime:IDirectMusicAudioPathImpl_IDirectMusicAudioPath_Activate (0x16ce48, 0): stub
fixme:dmime:IDirectMusicPerformance8Impl_GetDefaultAudioPath (0x14c3c0, 0x43b2e0): semi-stub (0x16ce4c)
fixme:dmime:IDirectMusicAudioPathImpl_IDirectMusicAudioPath_GetObjectInPath (0x16ce48, 0, 12800, 0, {00000000-0000-0000-0000-000000000000}, 0, IID_IDirectMusicGraph, 0x43b300): stub

...and so on, other games run with sound without problems... others also not 
I can run the game with sudo chown root .wine/ && sudo wine unreal2.exe

---

### Post by Neobuntu on 2008-11-16
I think we may want to get pulse working first. I'm still trying to understand that, much less get it working.

Then you may want to append a little command to your game launching command to tell OSS games to utilize Pulse. 

That's all I know so far...

---

