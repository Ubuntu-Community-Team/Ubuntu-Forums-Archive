---
title: "Blackscreen during install 14.04 and others - ASUS A88X-Pro FM2+"
date: 2016-02-04
forum: Installation &amp; Upgrades
---

### Post by jim132 on 2016-02-04
I have contacted ASUS numerous times on this subject.  I did install Windows 7 pro 64-bit and it worked perfectly, in fact it was so fast on my SSD, I didn’t even realize that it was finished in such a short time.  I did some research on ubuntuforums.org and found the description is called “black screen” and happens sometimes during installation or upgrade.  My specific problem is solved now for Ubuntu 14.04.  The solution was to install a video card into a slot and try installing again.  

Here is what I found out.  

Only Windows XP, Vista, 7, 8, and 10 are supported using the onboard graphics ports.  They work just fine for windows, that’s great.  ASUS documentation through Tier 1 support and the ASUS webpage are absolutely unacceptable.  If you would share the information that for the A88X-Pro motherboard, Linux OS are supported only with a video card installed into a PCIe slot.  In my case, I used a “Gigabyte GeForce GT 730 2GB DDR3 Video Card - PCIe 3” and completed the Ubuntu 14.04 install with no other problems.  I have not tried any other linux distros yet, but I will be trying that later on another machine soon.  cost $69 retail.

This build 
ASUS A88X-Pro FM2+
AMD A6-7400K Black Edition Dual Core (OC to 4.1 Mhz)
Gigabyte GeForce GT 730 2GB DDR3 Video Card - PCIe 3
8 Gb DDR3 1600 evga
Seagate Barracuda 2TB hard disk 6 Gb/s
250 Gb SSD
Corsair CX Series CX600M 600 watt power supply
Samsung SH-224FB/BSBE 24x SATA internal DVD burner
Jim

>>>
Initially I tried to do the Ubuntu 14.04 install using the onboard video ports and tried them all.  The black screen was all I could see, but occasionally I would see a blurry white noise screen.  During this install I booted from a USB thumb drive, got to the language selection, then saw the Ubuntu splash screen with progress bar dots moving for about 10 seconds.  After that it went black, but the thumb drive would occasionally blink indicating access / activity.  I upgraded my bios to the recommended version per the ASUS support pages for that specific mobo, didn't work.  I changed every possible configuration in the bios settings for graphics with the exact same result.  I tried Ubuntu 12, 14 and 15, same.  I tried Mint, puppy, Bodhi and something else I can't remember, didn't work. Tiny Core and Qimo 2.0 worked but they are simple and have low requirements for video.  Of course the windows 7 pro 64-bit worked awesome, but I hate Microsoft.  ASUS support sucks at best.

---

### Post by jim132 on 2016-02-08
I forget to mention that I had upgraded my Bios to 2502 as directed by the ASUS support page for my mobo, but that did not solve the problem.

---

### Post by Bashing-om on 2016-02-08
jim132; Hello ...

Many times with a black screen we find that there is no graphic's driver.
In this situation one boots up with the boot parameter "nomodeset" for ATI and Nvida chip sets . 
see: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
And install the recommended graphic's driver from the Additional Drivers utility.

Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>
Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and insert the term "nomodeset" -without the quotes-; ctl+x to continue the boot process. GUI login -> user name and password -> desktop. Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

