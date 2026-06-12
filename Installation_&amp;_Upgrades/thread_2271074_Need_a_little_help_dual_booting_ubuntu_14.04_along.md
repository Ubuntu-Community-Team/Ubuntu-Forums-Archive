---
title: "Need a little help dual booting ubuntu 14.04 alongside win 8.1"
date: 2015-03-27
forum: Installation &amp; Upgrades
---

### Post by brent20 on 2015-03-27
Hi,

So I recently installed ubuntu on an old laptop and really enjoyed using it, so now i want to dual boot it alongside win 8.1 on my main pc. It's a Lenovo y50 with a 1TB sshd. I booted from my usb and tried to install ubuntu. When i got to the part where you have to decide how much disk space ubuntu may use I got a little confused because i only showed 26gb(iirc) in total. So I figured i need to make a partition on my harddrive to install unbuntu on. Now when i try to shrink my 888gb NTFS windows8_OS partition it only gives me the option to shrink it 3897MB. I however have 535GB free space on that partition and i want to make a 150gb (153600MB) partition for ubuntu. How do I make the partition I want?

Here's an image to show you guys what i'm looking at: [http://i.imgur.com/7dsCXBA.png](http://i.imgur.com/7dsCXBA.png)

I've never done anything to the partitions so this is how I got it out fo the box.
I btw made a full image backup on an external harddrive just in case something goes wrong.

Thx in advance.
Brent

---

### Post by oldfred on 2015-03-27
Full image backup is good, you should also have the repairCD or flash drive for Windows.

You should shrink Windows from Windows own disk tools and reboot immediately so it can run chkdsk and make its repairs to its new size. 
Make sure Windows fast boot or always on hibernation is off. 
If UEFI also has a fast boot setting best to turn it off as some have difficulty getting into UEFI to change settings. When fast boot is on, you only can get to UEFI from Windows and when Windows does not work you can have major issues.

THis is on Windows 7 or Vista, but issue can be the same. 
 [http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7 & 8 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

If fast boot in Windows 8 is on then it has a hibernation file.
      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 
powercfg /h off

See also link in my signature for more info on UEFI install.

Issues are often common across a brand, so even if not same model, you may have some of these issues:

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
      
 See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)

---

### Post by brent20 on 2015-03-27
Thanks for the reply.

I now turned fastboot, pagefile en hibernate off and am defragging the disk. If that does not work, ill try some of the suggested defragging software.

---

### Post by brent20 on 2015-03-27
Windows defragging didnt do work, but powerdefragmenter did the job just fine and I was able to make the partition I wanted using minitool partition wizard :) 

Thanks for the help.

---

