---
title: "Screen tearing and other issues on 16.04.2 with AMD Radeon R9 390 and AMDGPU-PRO"
date: 2017-03-01
forum: Installation &amp; Upgrades
---

### Post by stinktier2 on 2017-03-01
I had a running xubuntu 15.04 system with an AMD Radeon R9 390 GPU which used the fglrx-update drivers via the Additional Drivers setting. The system was installed with an AMD HD7770 GPU, later I upgraded the graphic card without much of a hassle to get better game performance. The only drawback came as the new card had no VGA port for my old CRT monitor which I use alongside a Samsung PS63A756T HD TV, so I got a DisplayPort-to-VGA Adapter.

I tried upgrading the system once or twice but always without success as the R9 390 card was not well supported driver-wise on newer ubuntu versions. Now with the arrival of 16.04.2 with the 4.8 kernel and the AMDGPU-PRO drivers supposedly supporting the R9 390 I upgraded again, ruining my working system in the progress. Now after two very stressful days I have accomplished the following:
[LIST]
[*]I did new install of xubuntu 16.04.2 from DVD with the old HD7770 GPU in the pc. 
[*]I installed the AMDGPU-PRO 16.60-379184 drivers from [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx) 
[/LIST]

I noticed a very curious thing: Still running the HD7770 GPU I could not get sound on the HDMI-connected TV as all HDMI options in the Volume Control configurations were marked as "unplugged". Then I switched the graphic card to the AMD R9 390. This resulted in:
[LIST]
[*]HDMI sound was active again (yay!). 
[*]The VGA CRT monitor was no longer receiving any signal from the GPU (via the DP-VGA adapter). So it is currently impossible to use it at all. 
[*]Massive screen tearing happens all the time on the Samsung TV. Regardless of playing a game, watching a video or just using the desktop, this is *very* noticable. While playtesting Tomb Raider Underworld the display completely went black and didn't return (system froze). 
[/LIST]

So now I am at a loss. Can this screen-tearing issue be solved? I cannot find anything like the old Catalyst Control Center to activate tearless display or vsync. And why is the DisplayPort-VGA adapter or the DisplayPort on the graphic card not working? I pretty much need the CRT and know both the adapter and the monitor work fine.

(One last weird thing: I switched the graphic card again to the old HD7770 (to have a working monitor again) and the display settings no longer recognized the CRT as "Sony 18''" with many supported resolutions (up to 1600×1200) but only as "Digital display" with a max 1024×768 resolution.)

---

### Post by QIII on 2017-03-01
Hello!

Tear-free is set manually in 20-amdgpu-pro.conf, which you have to create.  I'm not at home and I don't want to mislead you from my rusty memory about where that goes.  In 7 or 8 hours I'll be home and try to remember to get back to you with content and location.

---

### Post by stinktier2 on 2017-03-02
So no GUI for changing settings? Okay, if that's what AMD wants... :???:

Yes, please get back to me. The tearing/flickering makes the PC unusable and the issue with the old CRT is extremely annoying – I need to get it back to work again.

---

