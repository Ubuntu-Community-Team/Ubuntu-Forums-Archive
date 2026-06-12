---
title: "EmergencyResetSystemMode = ATI? Ack!"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by cyph3x on 2008-10-18
Hmm i've been having some serious trouble doing anything with 3d Graphics. As I am not an ubuntu wiz I'm kindly calling upon the assistance of linux savvy people. (thats you) :)

Basically I am unable to get past the EULA in anything 3d program I try to open. /shrug I know there is a specific forum designated to this but somehow this seemed a bit more technical than "what MMORPG" are you playing now?"

Below is the debug log for one of my crashes (only partial, the original is something like 80000 lines).

Oh and a little background. The game that is crashing is EVE Online (which has a makeshift linux version) that uses Transgamings Cedega to run it. ( So i suppose thats a makeshift windows version hehe)

> 0004:err:*dbghelp:*pe_load_native_module could not open the executable image
0004:fixme:*psapi:*PSAPI_GetModuleFileNameExW swap this function's body with PSAPI_GetModuleFileNameExA() and fix Module32FirstW/NextW()!
0004:fixme:*psapi:*PSAPI_GetModuleFileNameExA swap this function's body with PSAPI_GetModuleFileNameExW() and fix Module32FirstW/NextW()!
0004:fixme:*psapi:*PSAPI_GetModuleFileNameExA swap this function's body with PSAPI_GetModuleFileNameExW() and fix Module32FirstW/NextW()!
0004:err:dbghelp:*pe_load_native_module could not open the executable image
0004:fixme:ntdll:NtQueryInformationThread (0xfffffffe,0x00000000,0x68b940,0x0000001c,(nil)), mostly-stub!
0004:err:dbghelp:SymFromAddr could not find the nearest symbol to the address 0x00000000411f78be
0004:fixme:*psapi:*PSAPI_GetModuleFileNameExA swap this function's body with PSAPI_GetModuleFileNameExW() and fix Module32FirstW/NextW()!
0004:err:psapi:PSAPI_GetModuleFileNameExA could not retrieve the filename for the module 0x40f56000 in this process
0004:warn:seh:doStackWalk could not retrieve symbol information {AddrPC = 0x411f78be, module = 0x40f56000 + 0x2a18be ('')}
0004:err:dbghelp:SymFromAddr could not find the nearest symbol to the address 0x00000000411d402a
0004:fixme:psapi:PSAPI_GetModuleFileNameExA swap this function's body with PSAPI_GetModuleFileNameExW() and fix Module32FirstW/NextW()!
0004:err:psapi:PSAPI_GetModuleFileNameExA could not retrieve the filename for the module 0x40f56000 in this process
0004:warn:seh:doStackWalk could not retrieve symbol information {AddrPC = 0x411d402a, module = 0x40f56000 + 0x27e02a ('')}
0004:err:dbghelp:SymFromAddr could not find the nearest symbol to the address 0x000000004118ecf8
0004:fixme:psapi:*PSAPI_GetModuleFileNameExA swap this function's body with PSAPI_GetModuleFileNameExW() and fix Module32FirstW/NextW()!
0004:err:psapi:PSAPI_GetModuleFileNameExA could not retrieve the filename for the module 0x40f56000 in this process
0004:warn:seh:doStackWalk could not retrieve symbol information {AddrPC = 0x4118ecf8, module = 0x40f56000 + 0x238cf8 ('')}
0004:err:dbghelp:*symt_fill_sym_info couldn't retrieve the type of the symbol
0004:err:dbghelp:*symt_fill_sym_info couldn't retrieve the type of the symbol
0004:err:dbghelp:symt_fill_sym_info couldn't retrieve the type of the symbol
0004:err:dbghelp:*symt_fill_sym_info couldn't retrieve the type of the symbol
0004:trace:seh:EXC_RtlRaiseException code=c0000026 flags=1 addr=0x4001e8f0
0004:trace:seh:EXC_CallHandler calling handler at 0x536767a6 code=c0000026 flags=1
0004:trace:seh:EXC_CallHandler handler returned 3
0004:err:seh:EXC_DefaultHandling Unhandled exception code c0000026 flags 1 addr 0x4001e8f0
0004:trace:x11drv:X11DRV_XF86VM_EmergencyResetSystemMode mode 1
0004:trace:x11drv:X11DRV_XF86VM_EmergencyResetSystemMode xvidmode, switching to mode 1

My specs are:

> cpu: Intel(R) Core(TM)2 Duo CPU     E6850  @ 3.00GHz
cpu_ghz: 3.0
memory: 3029
videocard_manufacturer: ATI Technologies Inc.
videocard_type: ATI Radeon HD 3870
videocard_ram: 512
agp_aperture_size: N/A
videocard_driver_version: 2.1.7412 Release
soundcard: HDA Intel at 0xe2520000 irq 2
soundcard_driver: ALSA Version 1.0.15
machine_bitness: 32
kernel: 2.6.24-21-generic
x_version: 
distro: Debian lenny/sid
GUI version: eve-000066


Oh a little more background. I tried installing the factory ATI drivers that were released for ubuntu. They didn't work. surprise, surprise. So when I was running this I was using the restricted driver (which was enabled through Ubuntu). 

Please help!

---

