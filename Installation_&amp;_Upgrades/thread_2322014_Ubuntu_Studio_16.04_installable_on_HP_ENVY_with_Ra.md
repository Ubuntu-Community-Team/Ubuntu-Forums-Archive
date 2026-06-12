---
title: "Ubuntu Studio 16.04 installable on HP ENVY with Radeon 7 gpu but with issues"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2016-04-25
These articles as well as the Ubuntu 16.04 LTS release notes explain why some users may want to stick with v14.04.x LTS until later this year when hopefully the AMD graphics will be fully supported with hopefully a better version:

[http://www.pcworld.com/article/3043044/linux/why-linux-gamers-with-radeon-gpus-may-want-to-avoid-ubuntu-1604-lts.html](http://www.pcworld.com/article/3043044/linux/why-linux-gamers-with-radeon-gpus-may-want-to-avoid-ubuntu-1604-lts.html)
[http://fossbytes.com/ubuntu-16-04-features-linux-gamers-with-amd-radeon-no-fglrx-driver/](http://fossbytes.com/ubuntu-16-04-features-linux-gamers-with-amd-radeon-no-fglrx-driver/)
[http://www.pcper.com/news/Graphics-Cards/Ubuntu-1604-Deprecates-AMD-fglrx-Driver-Support](http://www.pcper.com/news/Graphics-Cards/Ubuntu-1604-Deprecates-AMD-fglrx-Driver-Support)

As for installation from the Ubuntu Studio 16.04 LTS LiveDVD...

My home computer is an HP ENVY with an AMD/ATI GPU (graphics processor) based upon the Radeon 7 series. It's not totally new and yet it's not totally old.
Unfortunately, it falls into the range of the affected GPU's so I did have monitor issues during installation... (but they are overcomeable as described)

At first try, all I got was a blank screen when I tried to test run the LiveDVD. It got to the main menu screen but wouldn't go into the full boot without basically abandoning all monitor output. My computer monitor displays success or failure when scanning for input and it showed failure and then put itself to sleep since there was no output going into it.

Later on, I tried again and found success by pressing F6 to get the boot options.
For me, enabling both "Expert" and "NoModeSet" in the popup menu is what worked. But I also had to delete the "---" in the boot string and leave the spaces!
When I did all that, I was able to boot into the LiveDVD and do the full installation.

After installation and bootup, I pressed SHIFT to get to the GRUB menu and pressed "e" to edit the boot options in what I think was the Advanced part of the menu.
I don't remember exactly how I did this but you can consult with the help here in the forums to explain how to edit grub boot syntax.

I added " nomodeset " to the boot text string near the part where it says "splash", a few lines down.
This makes the currently booted session use NoModeSet. I pressed Ctrl-X (or F10) to continue booting.
I think I also may have deleted the word "splash" so that I would get text display instead of the ubuntu logo.

Then the final step after boot was to: sudo mousepad /etc/default/grub ...to edit the grub kernel options.
I found the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (or similar)
and changed it to GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

I think I also may have changed the disabled line:
#GRUB_GFXMODE=640x480
...into the enabled...
GRUB_GFXMODE=1600x900
...to match my monitor's default size.

Personally, I like to see the text info about what is happening during boot, so that's why I deleted the "quiet splash".
After editing grub, I did sudo update-grub so that the changes would affect the future boots.

After I did all that stuff, the Ubuntu Studio 16.04 LTS installation worked and I was able to test it out on my hard drive.
I do remember that during boots, the ubuntu logo would display for just a few seconds after most of the boot process and the logo would be warped, but after that it continued into a non-warped readable screen with the Enter Password type of prompt.

I'm just posting this stuff here to give you guys an idea of how to get an AMD system going with Ubuntu Studio 16.04 LTS so you can fully test it out if you have the free hard drive space/partition. Also, you may want to use the "Do Something Else" option to remain in full control of what get's installed where during the installation. And if you already have a SWAP partition that you want to reuse for the install, be sure to swap it OFF before you run in the installation. gParted can be used to see the partitions and to swapoff, but be sure to quit qParted after you are done so it doesn't conflict with the installer.

According to the article(s) listed above, AMD graphics support will improve later in the year after AMD releases it's newer GPU driver versions.
So if stuff doesn't work out for now, just stick with 14 or 15 and migrate to 16 later on this year, after the AMD gpu driver support improves.

---

