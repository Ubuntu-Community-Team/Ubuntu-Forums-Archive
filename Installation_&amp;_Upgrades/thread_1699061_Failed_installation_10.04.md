---
title: "Failed installation 10.04"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by mark1960 on 2011-03-03
Following an attempt to install ubunto 10.04 on my 

Acer travelmate 2400 with 
win xp system 
intel celron M
512 ram
1.50GHz
40gb
integrated graphics

I decided to take the clean install which seemed to be going well even asking set-up questions - the next time i looked at the screen it had collapsed to a command line blinking in the top left hand corner with a very short computer start up.

I have put this on utube so you can see 
[http://www.youtube.com/watch?v=5PI0fCgb7WU&feature=player_profilepage](http://www.youtube.com/watch?v=5PI0fCgb7WU&feature=player_profilepage)

The F2/12 functions do not work nor does any attempt to re-boot from disc. The only control i have is the power button, I can open the optical drive draw and i can restart the computer ctrl/alt/del

any help would be appreciated

---

### Post by mörgæs on 2011-03-03
Hi, which graphics card do you have?

---

### Post by mark1960 on 2011-03-05
As far as i can tell these details are correct

Intel
®
 910GML 
(TravelMate 2400) integrated 3D graphics, featuring 
Intel
®
 Graphics Media Accelerator 900 and up to 128 MB  
of VRAM, supporting Microsoft®
 DirectX®
 9.0 and dual 
independent display

I cant access the details on the system -  because of the fault

---

### Post by mark1960 on 2011-03-05
Is there any way i can reset the system and try again or is it doomed? I have looked at the official documentation and tried a number of key inputs Alt F10 F2 / F12 - there is no response.

How about removing the ram memory?

thank you 
mark

---

### Post by mörgæs on 2011-03-05
My guess is that you need to change the boot options:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by YesWeCan on 2011-03-05
The fact that you used to be able to boot from CD but now you cannot is weird. BTW whenever you burn a new CD it is prudent to run the disk check before using it to install.

It is an essential starting point to be able to boot a live CD before you install. This will confirm your graphics hardware is compatible and you have enough RAM. Were you able to do this?

it is hard to tell from the video whether grub is not starting or Ubuntu is not starting. Unfortunately, Ubuntu doesn't display the grub boot menu if there is only one OS available (which is really dumb in my opinion). I would press either the shift or esc key (I can't recall which) during boot to ask the boot menu to show.

If you cannot achieve a boot menu then either your bios is not trying to boot the HD (unlikely) or grub is not installed properly (for example if you had done a manual install and opted to put grub in the Ubuntu partition rather than the MBR). To fix the latter you have to boot from live CD and reinstall grub.

If you see a boot menu then Ubuntu may be having a problem with the graphics hardware. This can usually be overcome by selecting the nomodeset boot option. It is also prudent to run a memory test.

---

