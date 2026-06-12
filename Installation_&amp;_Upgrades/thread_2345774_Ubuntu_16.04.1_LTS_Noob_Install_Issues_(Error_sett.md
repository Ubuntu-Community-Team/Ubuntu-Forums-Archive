---
title: "Ubuntu 16.04.1 LTS Noob Install Issues (Error setting up gfxboot/Install hanging)"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by erikj17 on 2016-12-07
Hello -

I have a PC with Windows XP that I built maybe 10 years ago. I'm tired of it being useless and after doing some research, I became infatuated with the thought of Ubuntu. I have no interest in keeping Windows and am ready to jump ship completely to Ubuntu.
- AMD Athlon 64 X2 5600+ (2.8GHz)
- Biostar TF7050-M2 Motherboard with integrated NVIDIA GeForce 7050PV GPU
- 2GB DDR2 800 (PC2 6400) RAM
- 500GB Hard Drive
- DVD/CD-ROM Drive

Currently, I have the PC connected to an HDTV with a VGA connection. There is an HDMI connection typically to the HDTV, but if I don't boot up an OS, the HDMI doesn't do anything.

I have downloaded ubuntu-16.04.1-desktop-amd64.iso. I got a 8GB USB drive... used SDFormatter to format the thing, then used Win32DiskImager to transfer to the USB drive. Prior to writing, I used Win32DiskImager to confirm the MD5 Hash at releases.ubuntu.com/16.04.1/MD5SUMS. Perfect match.

When I start my PC, I get some POSTs, then I select to choose my boot drive, and I can't find the USB drive anywhere.

So I decided to write the .iso file to a DVDR using ImgBurn. While I was at it, I also created a disk for 16.04.1 32-bit and one for 16.10. When I select to boot from these discs, I get the same issue for each...
"Loading Splash Screen" (or similar. I don't have much time to read what that says) and then
"graphics initialization failed"
"Error setting up gfxboot"
"boot: _"

If I wait long enough, I 'll get "Could not Allocate Memory" messages filling the screen.

The 16.10 version allowed me to type "help" in and get to a help screen (this did nothing in either version of 16.04.1), but I can't find anything useful to do in there. I was trying to find information on "nomodeset," (which seems to be a common-ish issue) but I could find nothing.

So, next I used "Universal-USB-Installer-1.9.6.8" to put the 16.04.1 .isos on the USB drive. From here, I get a really generic looking menu where one option is to install Ubuntu. "Hooray!" I thought, but when I select that item, the entire system just hung out there, doing nothing but flashing that cocky little flashing underscore, which I interpret as the system laughing at me.

I'm writing this because I honestly am not good at software, but I have tried numerous methods and honestly did do a lot of searching that just left my head spinning (I even read through [https://help.ubuntu.com/lts/installation-guide/amd64/install.en.pdf](https://help.ubuntu.com/lts/installation-guide/amd64/install.en.pdf)). If there is anyone out there that might have the patience to help me through this process or could even point me down some meaningful path, I would be much appreciative.

Thank you.

---

### Post by oldfred on 2016-12-08
That now is an old nVidia card. You eventually will need an older legacy nVidia driver.

But to boot installer and first boot with grub of installed system you will probably need nomodeset. If only Ubuntu, first boot will require holding shift key from BIOS until grub menu appears. Some systems also require other boot parameters in addition.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I have seen where 2GB is considered the cusp between 32 bit and 64 bit being recommended. My 10 year old laptop with 1.5GB of RAM did run 64 bit, but if I loaded more than one large app and a couple smaller ones, it would turn grey & I new it was using swap.

My 10 year old laptop only had Intel internal video and that just was not enough to run full Ubuntu with Unity Desktop/gui. It was so slow as to be unusable. So I installed fallback or gnome-panel which is a older menu system. Ubuntu has many flavors and those are different desktops or gui/graphical app and set of included applications.  Some like Lubuntu or Xubuntu may work better for your old system.
        
 Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE & new in 17.04 Ubuntu Budgie

---

### Post by erikj17 on 2016-12-08
Thank you for the response, but my ignorance is going to get in the way or progress....

> [COLOR=#000000]If only Ubuntu, first boot will require holding shift key from BIOS until grub menu appears. Some systems also require other boot parameters in addition.[/COLOR]

If I have a DVDR of the 64-bit .iso in my drive, my bios is setup to boot from that before my HD (that has Windows XP). If I hold shift during POST, nothing happens. I get a "Boot from CD:" prompt followed quickly by an "ISOLINUX 6.03" copyright line of text followed by "Loading bootlogo..." and back to the gfxboot faults identified originally. I followed a link you listed that referenced trying to use the "ESC" key rather than SHIFT, but that had the same (non) effect.

Am I misinterpreting your instructions?

As for the RAM, that is simple enough to upgrade. The MOBO can support 8GB, but I didn't want to spend any more money on this hardware until I got something installed.

---

### Post by oldfred on 2016-12-08
With live installer DVD, in BIOS you should first see two tiny accessibility icons at bottom of screen. Press any key when they are shown, then press f6 and add nomodeset as boot option.

The grub options then to add nomodeset are using shift key and manually editing linux line.

---

### Post by erikj17 on 2016-12-08
I think that is further than I can get. I've seen posts regarding that screen with icons... but I have never seen it.

As soon as the DVDR starts spinning...

Boot from CD :
ISOLINUX Copyright
Loading bootlogo
...<wait just a fraction of a second, then transition to a new screen with three lines of text>
graphics initialization failed
Error setting up gfxboot
boot:

---

### Post by oldfred on 2016-12-08
This says type help & press enter.
[http://askubuntu.com/questions/364063/i-cant-boot-from-usb-error-setting-up-gfxboot](http://askubuntu.com/questions/364063/i-cant-boot-from-usb-error-setting-up-gfxboot)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

---

### Post by erikj17 on 2016-12-08
16.04.1 64-bit did nothing when typing "help." This seems to align with the posts I've read before and matches my initial post, but I tried again just in case.

I put the 64-bit version of 16.10 on a DVDR, had the same "Loading bootlogo" issue, but here, I typed "help" and hit Enter.
This brings up a "Welcome to Ubuntu" screen with options F1 through F10, and at the bottom it says "Press F2 through F10 for details, or Enter to boot."
I hit Enter.
Ubuntu 16.10 purple screen with four small dots under measuring some sort of progress status.
Many lines of text that I didn't capture so I can't tell for certain what was happening.
After those occur, I get a single blinking cursor, top left, and the system was hanging.
I restarted the system.
Same process as before up until the purple screen/dots.
After a short while, that clears and I see "Ubuntu 16.10 ubuntu tty1" on line 1, and "ubuntu login: _" on line 2. Keyboard works here
Shortly thereafter, I get a new screen with a blinking cursor in the top-left and the systems appears to be hanging. Keyboard does nothing, but is showing it is connected.
I hit the power button, Ubunto purple screen indicating to remove the installation medium, I do, hit Enter, the system powers down.

Same thing happens on subsequent tries.

Please tell me there is something informative in this explanation!

---

### Post by oldfred on 2016-12-08
Did you press f6 and add the nomodeset boot parameter?

---

### Post by erikj17 on 2016-12-08
It is unclear to me during the process when I need to hit F6.

First, when I am at that help menu (I assume this is not where I press F6 - this only lists possible commands, it appears) and I press "Enter," sometimes nothing happens and the system hangs. It is only when I get two lines of text something does happen (and by "something" I mean I get to the purple screen):
[    6.537973] nouveau 0000:00:12.0: preinit failed with -22
[    6.538037] nouveau: DRM:00000000:00000080: init failed with -22

> [COLOR=#000000]With live installer DVD, in BIOS you should first see two tiny accessibility icons at bottom of screen. Press any key when they are shown, then press f6 and add nomodeset as boot option.[/COLOR]

Well, I never saw two accessibility icons of any size. I assume this is supposed to occur when the purple screen appears, but there is nothing other than "Ubuntu 16.10" and four dots.

[COLOR=#000000][/COLOR]I tried many combinations of keys on this purple screen, including hitting F6, and when I did, I got a new black screen with all sorts of information scrolling, including:
"Generating locales (this might take a while)..."
"Generation complete."
"pwconf: failed to change the mode of /etc/passwd- to 0600"
"Using CD-ROM mount point /cdrom/"
"Identifying... [<bunch of characters>]"
"Scanning disc for index files..."
<more stuff>
"gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
<lots of .mount and .service stuff>
<lots of "Started xxxx Service with green "OK">

... and then back to the single blinking cursor. At no point did I see any sort of menu or any selectable options.

Pressing CTRL+ALT+F1 (through F6) gives me TTY1 (through 6) login prompts, exactly the same screen I got to before.

In your original reply, you referenced this thread:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I found this heading:
> [SIZE=4][COLOR=#000000]**How to enable kernel options on the livecd (before install)**[/COLOR][/SIZE]

[COLOR=#000000]If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom:[/COLOR]

[IMG]http://img829.imageshack.us/img829/3509/dgfdgrunningoraclevmvir.png[/IMG]

[COLOR=#000000]Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see this menu:[/COLOR]

[IMG]http://img827.imageshack.us/img827/3509/dgfdgrunningoraclevmvir.png[/IMG]

[COLOR=#000000]_**If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key**_. You can close the menu with escape key and resume booting by selecting the option &#8220;try ubuntu without installing&#8221; (please note that session does allow you to install ubuntu once you found the kernel options cured your problem).[/COLOR]

[COLOR=#000000]If you need to add kernel options not provided by the F6 menu, you can just type them in at the end of the boot options line.[/COLOR]

**Important: if you select a kernel boot option from the F6 menu and proceed to boot and later install ubuntu, those boot options will NOT be applied to your installation. If you needed nomodeset to get the livecd to boot, you will almost certainly need it again once you reboot in to your fresh install. See below how to set those options on an installed ubuntu. And perhaps click the &#8220;affects me too&#8221; on [this bug report ]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/664526")where I request these settings be applied (semi) automatically.**[COLOR=#000000]
[/COLOR]
This is what I am assuming you are referring to, but I never see this keyboard logo (Also, the included images seem to be broken for me in this section).

---

### Post by oldfred on 2016-12-08
This shows the screens you should get.
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076#162076)

---

### Post by erikj17 on 2016-12-08
I understand I should get them, but I don't.

I tried creating an imgur account and added photos of what is happening:
[http://imgur.com/a/GD5N9](http://imgur.com/a/GD5N9)

I never see the screens shown in the post you referenced. I do not understand how to set nomodeset from the screens I do see.

---

### Post by oldfred on 2016-12-08
Top of screen is BIOS, and the syslinux is the start of boot.
If that is as far as you get, the you have potentially one of several issues users have.

Either ISO not downloaded correctly. Check md5sum
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or installer did not correctly write to flash drive. Usually you can try different installers.
       
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
        Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    
 With newer computers, some ports are USB3 or USB2 and only some ports may be bootable. Try different ports. Very old computers had USB ports but they were not bootable. My older computer had many  boot options, but USB boot was actually listed under hard drives, not any of the USB boot options.

Some flash drives seem to work better. May be combination of above issues, but users switch to a different flash drive and then have success.
      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by erikj17 on 2016-12-09
Verified the hash, wrote the file to DVDR, confirmed the write was successful. I have not used any sort of flash device since the first issues encountered identified in my original post. After reading about how many issues others had, I just figured it wasn't worth the hassle.

I give up. I'll just assume it is my hardware and Ubuntu is completely incompatible.

Disappointing. I started this endeavor with so much optimism.

---

