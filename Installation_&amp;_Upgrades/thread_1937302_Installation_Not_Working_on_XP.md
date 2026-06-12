---
title: "Installation Not Working on XP"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by ubunt10 on 2012-03-07
Hi:

I downloaded the iso file for Ubuntu 11.10 and burned it onto a DVD. I used this DVD to install Unbuntu on my laptop computer and it worked fine for the laptop computer. 

The problem arose with my desktop computer. I have only one hard drive. I used [Darik's Boot And Nuke](http://www.dban.org/) to wipe the hard drive. Then I installed a fresh (legit/legal) copy of Windows XP SP2. I installed it with only one partition (NTFS on C:) and I left no unpartitioned space on the hard drive. Windows XP was successfully installed and functions ok. 

Next, I tried to boot from the Ubuntu DVD. The Ubuntu logo came up and was displayed on my monitor for about 10 to 20 minutes. Then a black and white screen came up. I waited for a long time and it was stuck. Here is what the screen looked like. 

[[img]http://img155.imagevenue.com/loc18/th_144892830_ubuntuscreenshot_122_18lo.jpg[/img]](http://img155.imagevenue.com/img.php?image=144892830_ubuntuscreenshot_122_18lo.jpg)

That image shows the left column. The right column had > [ OK ] to the right of each line shown in the image. 

Is this enough information? Do you have any suggestions? Thank you.

---

### Post by darkod on 2012-03-07
If you already planned to dual boot, why would you leave no unpartitioned space on the disk? It makes no sense to install XP onto the whole disk and shrink the partition immediately especially since shrinking can break XP.

You need to make sure the ubuntu cd/dvd runs in live mode first, the Try Ubuntu. It seems it doesn't.

The first thing you can try is:
Immediately when the first purple screen shows up, hit Esc. That should show you the older type main menu.
At the bottom there will be F6 Advanced options. Hit F6 and select nomodeset parameter.
After that select Try Ubuntu from the main menu.

Tell us if that helped. DO NOT start to install yet.

---

### Post by ubunt10 on 2012-03-07
> If you already planned to dual boot, why would you leave no unpartitioned space on the disk?

I was trying to use the same settings I had during a previous, successful installation. I once installed an older version of Ubuntu on the same computer and it had no unpartitioned space. I hardly know what I am doing. (The reason I want to install Ubuntu is to learn.) 

> You need to make sure the ubuntu cd/dvd runs in live mode first, the Try Ubuntu. It seems it doesn't.

While running Windows XP, I inserted the DVD and went to MY Computer to access it. This is what I saw when I double-clicked on the DVD icon in My Computer. 

[http://img132.imagevenue.com/img.php?image=149112975_screenshot1_122_31lo.jpg](http://img132.imagevenue.com/img.php?image=149112975_screenshot1_122_31lo.jpg)

Of the three buttons, I clicked the top one (because prior to this thread, booting was not working). After that, I was prompted with three new options that are displayed in the image linked below.

[http://img243.imagevenue.com/img.php?image=149113124_screenshot2_122_495lo.jpg](http://img243.imagevenue.com/img.php?image=149113124_screenshot2_122_495lo.jpg)

Then I got the error shown in the next screen shot. 

[http://img272.imagevenue.com/img.php?image=150069674_screenshot3_122_163lo.jpg](http://img272.imagevenue.com/img.php?image=150069674_screenshot3_122_163lo.jpg)

Is that enough information or do you want the log file that the error mentions?

---

### Post by darkod on 2012-03-07
It's a bootable cd. You need to boot your computer with the cd in the drive, not use it in windows.
Just restart and if it doesn't boot from the cd enter into BIOS and put CD-ROM before HDD in the boot device list.

You might have installed with no unallocated space earlier but you should know at least the basics, that linux install on its own partitions with its own filesystem. If you have a single ntfs partition on the whole disk, it will have no options but to shrink it. And this can sometimes corrupt XP.

But we can talk about that later, now first check if the ubuntu cd runs in live mode.

---

### Post by ubunt10 on 2012-03-07
I already tried to boot from the DVD and could not. That is what my original post describes. 

It did not get as far as a purple screen or a menu. When I boot from the DVD, I get a black screen with the Ubuntu logo in the center and five dots below the logo that represent a status bar. It stays on that screen for 10 to 20 minutes. Then it just gets stuck on this screen:
[http://img155.imagevenue.com/img.php?image=144892830_ubuntuscreenshot_122_18lo.jpg](http://img155.imagevenue.com/img.php?image=144892830_ubuntuscreenshot_122_18lo.jpg)

---

### Post by darkod on 2012-03-07
As soon as you see the logo try hitting Esc. Basically, at the first screen you get.

Does that open up a menu?

---

### Post by james2b on 2012-03-07
You need to provide some details about your desktop computer as far as all the main hardware components in it, (CPU type, RAM, and the brand name if a pre-built type, or the motherboard if a store built type, and hard drive ) You could boot into the BIOS to check that basic items are being detected okay, and the settings are fine

---

### Post by ubunt10 on 2012-03-07
> As soon as you see the logo try hitting Esc. Basically, at the first screen you get.

Does that open up a menu?I pressed the Esc key right away when I saw the large Ubuntu logo and status bar below it. 

It went to a black (background) and white (text) screen. I was unable to capture everything 

that was displayed on the screen, but I took two pictures of the monitor with my camera and 

I believe the images reveal the majority of what showed up. The images are below. 

[http://img249.imagevenue.com/img.php?image=161530292_screenshot4_122_12lo.jpg](http://img249.imagevenue.com/img.php?image=161530292_screenshot4_122_12lo.jpg)
[http://img23.imagevenue.com/img.php?image=161544536_screenshot5_122_194lo.jpg](http://img23.imagevenue.com/img.php?image=161544536_screenshot5_122_194lo.jpg)


[details removed for privacy]


> You could boot into the BIOS to check that basic items are being detected okay, and 

the settings are fineAll of my hardware is functioning properly right now with Windows XP, so I do not think it 

is a BIOS issue. Do you think I should still go into the BIOS and check? If so, what exactly 

should I press and look for?

---

### Post by darkod on 2012-03-07
Uhhh. I'm not sure, it might be a problem with the dvd disc. Did you download the dvd iso (the big one) or the cd iso?

If it's the cd iso can you try burning a cd, not a dvd?

If you decide burning a cd, do it at max 8x or 10x, never burn install cds at very high speeds.

Another options is downloading a new iso, best with torrent because it checks for corruption during download.

Other than that, I am running out of ideas.

---

### Post by ubunt10 on 2012-03-07
SOLVED: 

Thanks for your help. I looked at the picture in my original post and decided to search on Google for the last thing that showed up on the screen when it got stuck. In my case, it was > stopping system v runlevel compatibility

I found this thread
[http://ubuntuforums.org/showthread.php?p=11667172](http://ubuntuforums.org/showthread.php?p=11667172)

I found a few similar threads and they all said it was something related to the graphics driver. In response, I dug up the manufacturer CD and installed the driver instead of using whatever Windows XP was using. Then I rebooted with the Linux DVD and all went well. Thanks for your help.

---

### Post by james2b on 2012-03-07
Your RAM memory looks like it is mis-matched speeds.

---

