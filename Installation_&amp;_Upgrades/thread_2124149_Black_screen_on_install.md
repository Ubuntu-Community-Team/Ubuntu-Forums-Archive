---
title: "Black screen on install"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by MrGrey749 on 2013-03-10
Hi, I installed Ubuntu linux 12.10 on my laptop about a month ago and it worked no problem. Now I plan on using my laptop for other thigns and was attempting to install Ubuntu 10.10 on my desktop. Same Bit (64) Same CD.
Heres my adventure.

Boot from Ubuntu 12.10 CD
Boot from DVD reader
Stuck at black screen 
Blinking underscore 
Freezes

Boot from DVD reader again.
Shift key immediately upon graphic of square and person
English -> enter
F6 -> nomodeset -> enter -> esc
Install Ubuntu (no change in code)
Result: Black screen with code:
(Final line of code) 34.233878 ata7: hard resetting link
blinking underscore, does nothing

Boot from DVD reader again
Shift key immediately upon graphic
english -> enter
F6 -> nomodeset -> enter -> esc
Install Ubuntu (this time i changed the code to)
i915.modeset = 0 xforcevesa (i dont know if i typed it right here but i put it in correctly when i did it)
Result: screen of code
(about halfway up says): kernel panic - not syncing:
UFS unable to mount root fs on unknown -block (0,0)

Install from CD INSIDE WIN 7
*help me boot from CD
Install goes.
Reboot now
(upon restart)
Completing Ubuntu installation in 5, 4,3,2,1,0.
freezes at 0. nothing.

Tried above method again with (for more installation boot options press ESC now
ESC does nothing. freeze

After the IN WINDOWS preinstall,
I now have dual boot option for WIN 7 and Ubunutu.. BUT

Ubuntu 
5,4,3,2,1,0 ... nothing

Tried again
this time "safe graphic mode" (or whatever it was called)

ata8: hard resetting link
frozen

Heres another strange thing my DVD/writer/reader gives two boot options when choosing boot device. when i try the second one heres what happens
Install ubuntu
black screen (no nothing. No single or two characters like previous attempts, no purple, not even the little keyboard and man.)
Freeze

Ok, so next time (at this point im not sure how) but i get to the grub thing.
i press e,  i navigate to and delete the words quiet splash and write in nomodeset

ata7: Serror
ata7: failed command: Identify packet device

Ata bus error 
ata8: hard resetting link


I tried installing 12.04 instead to upgrade to 12.10, got similar results
These results happened on more than one occasion, actually for the past 3 days not just once.
I am not running a "raid" thing with multiple HDD's
I have a single 500 GB HDD (for now)

I heard this was a video card problem and i was naive enough to think if i removed my g card something wuld change so i removed it and ran integrated graphics. Same stuff.
[h=1][SIZE=1][ASRock Z77 Extreme4 LGA 1155 Intel Z77 HDMI SATA 6Gb/s USB 3.0 ATX Intel Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157293")[/SIZE][/h][SIZE=1][/SIZE][h=1][SIZE=1][Galaxy 66NPH7DN6ZVZ GeForce GTX 660 GC 2GB 192-bit GDDR5 PCI Express 3.0 x16 HDCP Ready SLI Support Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814162122")[/SIZE][/h][SIZE=1][/SIZE][h=1][SIZE=1][Intel Core i5-3570K Ivy Bridge 3.4GHz (3.8GHz  Turbo) LGA 1155 77W Quad-Core Desktop Processor Intel HD Graphics 4000  BX80637I53570K]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116504")[/SIZE][/h][SIZE=1][/SIZE][h=1][SIZE=1][HGST HDS721050CLA362 (0F10381) 500GB 7200 RPM 16MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822145299")[/SIZE][/h]
These are what i built my PC with and are all the parts that are involved with various issues installing linux as I have been led to beleive by searching for answers. 
Plz help this noob get this cool/functional OS on his machine.

---

### Post by dino99 on 2013-03-10
as you seems having a recent hardware, i suppose you also have an uefi instead of bios

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-03-10
If you have the nVidia card plugged in, you also need to in UEFI/BIOS turn off the Intel video driver. Or without nVidia use the Intel driver. 

       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

      
 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[URL="http://ubuntuforums.org/showthread.php?t=2081649"]http://ubuntuforums.org/showthread.php?t=2081649

[/URL]
 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

If nVidia:

  Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1

OR:

 Force Intel Video mode as boot parameter in grub menu, but use your monitor size not example's 1280x1024.
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
[URL="http://ubuntuforums.org/showthread.php?t=2081649"]
[/URL]

---

### Post by MrGrey749 on 2013-03-10
Thank the both of you for the input, i AM watching the thread i just went to bed after posting. Will definitely give this a try in a little bit!! THANKS!! Also would love input from other if they think otherwise.

---

