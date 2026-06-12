---
title: "Lenovo s10-3 idea pad won't install the correct Ubuntu."
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by Morpheas on 2012-04-09
Hello! I got this Lenovo s10-3 laptop for my birthday. I've been trying to get it to work since December & I want beat it senseless.It came with Windows 7 Starter (horrid). All I want is Ubuntu 10.04. I want genome 2 and LTS, I have been using Ubuntu for four years with minimal problems until now.

I used UNetBootin and made a Live USB with Ubuntu 10.04 on it. I used it on two of my friends computers & it worked flawlessly. 

With a little research I found out that this is a "solved" issue. I found this blog with instructions ([http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html)&](http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html)&) I am a bit perplexed by them. I tried for 5~hrs to get it to work then gave up. When I booted it the next day it magically had Ubuntu 11.10 & Windows 7 starter dual boot. I never told the computer to partition or install Ubuntu since I didn't get that far. It wasn't connected to the internet.I have no idea how it installed & updated!   
So now I have Ubuntu 11.10 and Windows 7 Starter which are both my last preferences for both Linux and Windows.
  

I don't know enough about computers to know what the problem is with the Lenovo & installing Ubuntu. I'm guessing it's the bootloader since the instructions I found tell you to edit the kernel boot parameter.
If someone could tell me what exactly the problem is with the Lenovo it would be much appreciated.
If I was to put a different bootloader like "Easy BCD bootloader" would that fix this issue?

Or if I was to use MSDOS command prompt before loading an operating system to format the hard drive & just wipe it clean & start over. Would that work? (I have no clue if that would work)

On the instructions for step 2 it says "When booting the flashdrive or SD card, pres TAB key quickly so you may add the following kernel boot parameter (add this to the end of the line starting with the word "kernel"):
intel_idle.max_cstate=0 "

These instructions show the GRUB bootloader. Idk how I would already have the GRUB bootloader if my computer came pre-installed with Windows & I'm trying to install Linux. These instructions are for my Lenovo which comes pre-installed with Win7 Starter. It loads to Windows Boot Loader, I think it has the files for grub. I tried to download GRUB from the USC and it said I would have to delete 3 files which were all GRUB. 

I tried to use the shell file boot_info_script.sh from sourceforge.net but the file will not open. The file is on my desktop saved as bootinfoscript.sh(It downloaded as bootinfoscript but it didn't work that way either)

my screen terminal attempts were:  "sudo bash ~/Desktop/bootinfoscript.sh" it said:" No such file or directory" 
attempt 2 was when I re-named the file to include the extension .sh and it said the same thing
I then made it into super-user where it says root@ubuntu and tried : "sh bootinfoscript.sh" it said: "sh: Can't open bootinfoscript.sh" then I tried: "chmod +x bootinfoscript.sh" it said "chmod: cannot access 'bootinfoscript.sh' : No such file or directory" I don't know why it won't open.

When I boot with the flash drive Ubuntu comes up and I press TAB like instructed and a screen with a list of options appears. Something like: install Ubuntu, check integrity of DVD and so on with a list of F1 - F6 options displayed at the bottom of the screen with the Ubuntu purple background. It says to press F6 at the same time as you enter a hex code?? To edit the kernel boot parameter. But I don't understand how to get to the correct screen to do this. I must have done it right once since Ubuntu is on there but I can't figure it out again. If someone could maybe dumb down the instructions for my inexperienced mind that would be great. 

I also tried to install Linux mint 10 with a Live flash and it got to the UNetBootin screen and once I selected something the keyboard froze.


I just cannot figure this out and it's driving me mad. Thanks for reading!

---

### Post by zvacet on 2012-04-09
> So now I have Ubuntu 11.10 and Windows 7 Starter which are both my last preferences for both Linux and Windows.

Are both OS work as they suppose to?if they do it is fine.You will be able to upgrade to 12.04 at the end of month.

---

### Post by Morpheas on 2012-04-10
Well if they were running well than I wouldn't be spending so much effort to remove them. Unity runs really slow on my little Lenovo, it only has 1 gig of ram. Plus I greatly dislike unity. If I wanted an OS with that many un-needed bows and whistles I would just run an Apple OS since it is a Unix operating system... I want my computer to boot up fast and have a quick response time once it's booted up. Also as I said above it came with Windows 7 Starter. Besides the fact that it's a crippled version of an operating system I already hate! Both operating systems on my Lenovo take 10X longer to transfer files and boot. Plus programs in Windows become unresponsive. I wanted Ubuntu 10.04 for a reason, I love genome 2 and that's what I want to use. Linux Mint with Cinnamon would be acceptable too. 
 I want both operating systems off that computer. All I want is Ubuntu 10.04. 

I just want someone to dumb down the instructions from [http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html](http://technomess.blogspot.com/2010/11/ubuntu-1010-and-lenovo-ideapad-s10-3.html)
that would be great.
thanks!

---

