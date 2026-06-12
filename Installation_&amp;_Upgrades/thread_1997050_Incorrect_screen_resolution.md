---
title: "Incorrect screen resolution"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by indianya on 2012-06-04
I recently installed Ubuntu 12.04 LTS and plan to switch from windows for all my computer needs.
Problem: I don't see an option to set resolution to 1920 x 1080. Since I  am a newbie and not much familiar with Ubuntu. I am not sure how to check for correct drivers, configuration and how to fix the issue.

H/W is ACER ASPIRE M1610 with integrated SIS video chipset

lspci | grep -i vga
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
Monitor is HP 2311x with 1920x1080@60Hz native resolution.

I have searched google and tried various things but have not succeeded so far.

I have also attached zipped version of Xorg.0.log for someone who understands the errors logged in that file.
Following is output of xrandr. Any help to configure correct resolution will be much appreciated otherwise I will have to revert back to Windows due to fuzzy screen in Ubuntu.


xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1920 x 1440
default connected 1680x1050+0+0 0mm x 0mm
   1920x1440      60.0  
   1600x1200      75.0     70.0     65.0     60.0  
   1680x1050      60.0* 
   1400x1050      75.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1280x854       59.0  
   1360x768       60.0  
   1280x800       60.0  
   1152x864       75.0     60.0  
   1280x768       60.0  
   1280x720       60.0  
   1024x768       75.0     70.0     60.0  
   1024x576       60.0  
   960x600        60.0  
   960x540        60.0  
   800x600        75.0     72.0     60.0     56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0     76.0  
   848x480        60.0     76.0  
   800x480        60.0  
   720x480        61.0  
   640x480        75.0     73.0     60.0  
   640x400        72.0  
   512x384        60.0  
   400x300        60.0  
   320x240        61.0  
   320x200        71.0  
  1920x1080 (0x18c)  148.5MHz
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.5KHz
        v: height 1080 start 1089 end 1095 total 1125           clock   60.0Hz
  1920x1080_60.00 (0x18f)  172.8MHz
        h: width  1920 start 2040 end 2248 total 2576 skew    0 clock   67.1KHz
        v: height 1080 start 1081 end 1084 total 1118           clock   60.0Hz

---

