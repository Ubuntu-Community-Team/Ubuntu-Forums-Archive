---
title: "Hardy: Numerous upgrade issues"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by spamking2000 on 2008-04-21
Hey - 

I upgraded to the 8.04 LTS RC on Friday and since then have had a lot of trouble being able to use my PC.

So far I'm seeing the following issues:

1. The 10-key on the keyboard seems now to be intermittant. I've never had problems with this before, and it seems like the keyboard will sometimes work correctly when I first boot, but then for whatever reason the 10 key is lost... I can use the numbers above the letters on the keyboard, but this is definitely slower and a pain, not to mention that it should just work. Any thoughts? I have the US keyboard layout for a standard 105-key keyboard set as the default.

2. My PC is now locking up - A LOT! I've never had this kind of an issue with Ubuntu. Seems though that it happens mostly when Nautilus is open, but I'm not sure if that's the cause of the issue or not. Also, its unpredictable - yesterday when posting something to craigslist and going to add a picture, I I couldn't navigate through any windows for like 5 minutes, but it cleared on its own to the point where even though I couldn't use the mouse to select the pic I wanted to upload, I was able to type in the full path, hit enter and then all was fine. I couldn't select anything with the mouse in that window or any others until that point.

Today as another example though, I was playing music videos, got a phone call, hit pause in Totem and 2 minutes later the computer was locked up hard when I tried to start the video playing again. Nothing was responsive... even the number lock key on the keyboard wouldn't effect the light right above it, the mouse cursor was gone, etc. Nautilus was open on screen 1, Totem on screen 2.

3. Everytime my system goes to screen saver it either logs me out, or the computer locks up. I'll get the window to enter my password and then one of two things will happen, after I put in my password I either get nothing but two blank screens until I hard reset or my system goes back to GDM and I have to log in all over again and start my programs back up.

4. This one is kind of a nit, but even going to the screen saver, screen 1 dims before hand, screen 2 does not... not sure if this might have something to do with the problem above.

5. I've had to hit the reset button on the computer quite a bit in the last few days. When it goes to scan drives, at first I was getting a nice little message at the bottom of the standard loading Ubuntu screen saying soemthing along the lines of "Checking /mnt/sda1... etc." Now I don't even get that, I just get the 80x25 text screen and instead of the checking line getting updated, it gives me a new line for every update. I have 5 different partitions on various drives not including my swap, so this is getting pretty old. Seems like that form of updating the screen is not correct.

6. Another issue related to the drive checking... the drives are getting scanned as sda#, sdb#, sdd#. but in fstab they're showing up as hda#, hdb#, hdd#. They are IDE drives... not SATA or SCSI, so I'm not sure why this is happening either.

7. Immediately after upgrading, I had problems with the screen resolution on my nVidia card. I was getting 800x600 resolution and couldn't get anything higher. On recommendation from another forum post from someone else having a similar problem, I loaded the nVidia drivers again using EnvyNG... and they work now... sort of. I'm able to have the first screen at 1280x1024 and the second at 1024x768, but "Screen and Graphics" has disappeared from my System Preferences and Screen Resolution will not open. I just get an error saying: The X Server does not support the XRandR extension. Runtime resolution changes to the display are not available.

Here's the weird part... and it might explain it to a degree. After setting up the screens using the NVIDIA X Server Settings, my screen layout now works just like I'm using Xinerama, which I've never been able to do before. I love the way the screen layout works now as far as being able to drag windows from one screen to the other and maximize them within their own screen. I know Xinerama wasn't compatible with NVIDIA, but for whatever reason... that part at least seems to be working. I'm just wondering if its working right.

I know 8.04 was supposed to have some better multiple monitor support and I'm not sure if this kind of configuration should work under that, but in any case, I can't adjust it now from the way it is which is nice, to the way it was. I'm thinking I should be able to if this is actually supported at all now... just not sure what to do about it.

8. When I plug in my digital camera to a USB port, I get the normal "Camera Import" window saying a camera has been detected, would you like to add these pictures to your album, with the buttons Ignore and Import Photos. The camera also shows up as a drive on my desktop. However, when I hit import photos it now opens F-Spot instead of gThumb and pops up a window to pick whether to import from Camera: Mass Storage Camera at port disk:/media/dsk or Camera: Panasonic DMC-LC1 at port usb:. If I click on the "Mass Storage Camera," then I get an error that I don't have a ~/Photos folder, but it does find the pics on the camera. If I click on the Panasonic DMC-LC1, the icon for the camera disappears off my desktop and I get an error saying "Error connecting to camera" Received error "Unspecified error" while connecting to camera.

However, if I hit ignore and manually open gThumb and go to File -> Import Photos, I can still get the same import dialog window that I used to get when I hit Import Photos before in Fiesty and Gutsy, but it says "Mass Storage Camera" again like what worked in F-Spot instead of the name of my camera and now importing goes REALLY slowly.

9. Also - I noticed that it takes me 200mb of RAM just to boot up where it used to only take about 160mb. I'm not sure that I really see a lot of reason on why... kind of disappointed that this version might just be a little more bloated.

Please help! I suspect a lot of these issues might be fixed on their own by future updates, so I'm not really wanting to try to downgrade back to Gutsy (if that's even possible w/o doing a fresh install), but I also really don't want to have to do a fresh install either. I'd like to just be able to fix my problems and keep going.

Thanks,
spamking2000

AMD XP1800+, 1.5GB RAM, 200GB + 160GB + 15GB HD's, nVideo GeForce4 MX440 dual head

---

### Post by Pumalite on 2008-04-21
The secret to a great Hardy Heron is a clean install.

---

### Post by mkor on 2008-04-25
I had the same problem with hda drive - /dev/hda6 (my home) not found, system did not boot to X after upgrade, just root console, to fix the problem. Right now I modified it in fstab to /dev/sda6 beacuse it works then, but I would like to know how it _should_ be done. Should I be using the UUIDs to identify drives?

BTW: /dev/hda1 (/) is detected and mounted. What is it with the /dev/sda drives?

Update: I changed to UUIDs - works perfectly, however the drive is still sda.

---

### Post by esdaniel on 2008-04-25
> **Pumalite said:**
> The secret to a great Hardy Heron is a clean install.

If that were the case then it's perhaps a tad dumb to promote 'upgrading'.  Secret or not, I guess the community needs to ask itself do we allow a new release if there's not been sufficient testing done?  How does F&G testing sizes compare to Hardy - did more or less of us test Hardy this time round?

'Canonical' the brand is strong, Feisty and Gutsy as brands have been strong too but... Hardy as a brand is new and is about to cause damage to itself and the other Ubuntu brands unless of course things get resolved swiftly for most users experiencing these challenges.

---

### Post by Elegorod on 2008-04-27
To import photos using gThumb, open Settings - Removable Drives and Media, and in Cameras tab type command
```

gthumb --import-photos

```

---

