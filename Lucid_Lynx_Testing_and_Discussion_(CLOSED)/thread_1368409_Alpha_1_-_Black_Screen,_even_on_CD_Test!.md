---
title: "Alpha 1 - Black Screen, even on CD Test!"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by recluce on 2009-12-30
And now for my weirdest Ubuntu experience ever. I decided to test the Lucid Alpha 1 on my computer. I downloaded the x64 desktop image from the Ubuntu website and verified the MD5 checksum, so no download error.

I burned the image with Brasero and booted the CD, the inital welcome screen comes up. Now, no matter if I try to start Ubuntu Live or even the CD test, the screen blanks (cursor blinks top left for a while), does a coloured flash and blanks. End of story, no more picture for me, even though the system seemed to be working in the background.

Assuming a strange CD error, I fired up Windows and burned the image with Plextools XL on my Plextor burner, with all bells and whistles and verifies to make a 100% sure I had a good disk. Tried to boot this new disk, same thing. Black screen after starting from the Welcome screen.

I then proceeded to a different computer and had almost the same effect: when starting the CD test the screen blanked, cursor showed for a few seconds, screen flashes once, cursor disappears. The only difference: on this machine I can see a very faint, badly flickering black-and-white image, almost like a ghost image. From that faint image I could make out that the CD test completed successfully. On restarting out of the CD test, I get one incredibly bright white screen flash.

Now to the specs of both machines:

Computer 1: Dell Latitude D830 laptop, NVidia Quadro NVS140 graphics, 256 MB dedicated video memory, 4GB RAM, Intel Core2 Duo CPU. No picture after welcome screen.

Computer 2: Dell Vostro 1000 laptop, ATI Radeon Express graphics, shared video memory, 2 GB RAM, AMD Athlon 64 X2 Dual Core CPU. Flickering ghost image in CD test.

Those machines are about as different as possible, the CD test verifies a good CD, so what gives? :confused:

Bonus question: why has any kind of graphics to be initialized for the CD test? Plain old text mode should be fine and would avoid complications.

Any help would be greatly appreciated.

**Update:** Computer 2 (ATI) will eventually boot into a working desktop, still the splash screen during boot is totally messed up (flickering black and white ghost image). Computer 1 (NVidia) will never get out off the black screen.

---

### Post by phillw on 2009-12-30
Hi,

There is a bug for CD Test --> [http://ubuntuforums.org/showthread.php?t=1363431](http://ubuntuforums.org/showthread.php?t=1363431)

Not sure on the other issue of it not booting, tho'.

Regards,

Phill.

---

### Post by margazhang on 2009-12-31
Yours sounds like an issue with the NVIDIA driver. You need to follow my step-by-step instructions to install EnvyNG before going to the normal installation process:

[http://ubuntuforums.org/showthread.php?t=1366191&page=2](http://ubuntuforums.org/showthread.php?t=1366191&page=2)

Basically you need to boot to the Ubuntu live CD to the Recovery mode which gives you command line operation with networking. From there you can follow the instructions to install EnvyNG which guides you to install a correct NVIDIA driver so that your monitor can display properly the things you could not see.

---

### Post by recluce on 2009-12-31
> **phillw said:**
> Hi,

There is a bug for CD Test --> [http://ubuntuforums.org/showthread.php?t=1363431](http://ubuntuforums.org/showthread.php?t=1363431)

Not sure on the other issue of it not booting, tho'.

Regards,

Phill.

That does not seem to apply here. As I said, the test does complete, but the display is garbled (ATI video). I can only assume that it will complete on the NVidia machine, as I couldn't see anything.

---

### Post by recluce on 2009-12-31
> **margazhang said:**
> Yours sounds like an issue with the NVIDIA driver. You need to follow my step-by-step instructions to install EnvyNG before going to the normal installation process:

[http://ubuntuforums.org/showthread.php?t=1366191&page=2](http://ubuntuforums.org/showthread.php?t=1366191&page=2)

Basically you need to boot to the Ubuntu live CD to the Recovery mode which gives you command line operation with networking. From there you can follow the instructions to install EnvyNG which guides you to install a correct NVIDIA driver so that your monitor can display properly the things you could not see.

I will give that a try, but it will take some work (in other words: some time) to make room for an additional partition on my machine (no way I will overwrite a working Ubuntu installation with any alpha/beta). Thanks!

---

