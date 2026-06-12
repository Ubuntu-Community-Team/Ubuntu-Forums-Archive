---
title: "Trying to upgrade a MiniPC-based homemade laptop, significant problems encountered"
date: 2017-10-28
forum: Installation &amp; Upgrades
---

### Post by starhawk2 on 2017-10-28
I have a homebuilt 'laptop' (no battery was included) that I've put together. The system unit is a Wintel CX-W8 'MiniPC' from eBay. [One of these awful things.]("https://www.ebay.com/itm/282667234168") In addition to the system unit, there is a Dell-branded PS/2 to USB adapter for the keyboard, the keyboard proper (a SolidTek KB-595PW), an IOGear GUH304 hub (chosen for its ability to supply 1a current to each port, not for being USB3, which it is -- the system unit is USB2-only), an HDMI 7" 1024x600 LCD (with unused touch feature -- I've got it hooked to power but not to USB data -- display is a knockoff of [this WaveShare Raspberry Pi display]("http://www.waveshare.com/wiki/7inch_HDMI_LCD_(C)")), and a "Speed STP-600 USB Smart Pad" external touchpad mouse. Right now the heap is hooked to an Ethernet connection, but when it's in regular use it will have an additional dongle added to it -- a Netgear WNDA4100 WiFi adapter. To combat potential heat issues, I've knocked a hole in the top of the system unit and added a fan... the whole pile is powered by a 5v 6a laptop-style brick.

The system unit's specs are an Atom Z3735F System-on-Chip, 2gb RAM, 32gb eMMC "SSD" -- and none of it upgradeable. Despite being a 64b system with 32b UEFI (!) I managed to get Xubuntu 16.04 on there some months ago... today I decided I wanted that to be 17.10... so, since I couldn't get a LiveCD to work with a known good method of patching it for use with these atrocious systems (see [http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html](http://linuxiumcomau.blogspot.com/2017/06/customizing-ubuntu-isos-documentation.html) for pertinent details), I decided to go the upgrade route.

Of course it wants to put up a fight. I now have a partially booting Xubuntu 16.10 system.

Whether working from patched LiveCD (a non-patched CD will not even boot) 'burnt' to USB using Rufus, or from the botched upgrade, the symptoms are nearly identical. The system boots fine until it's time to pull up graphics, at which point I get a wallpaper with no taskbar, icons, or cursor. The difference is that, with the LiveCD, the "I see wallpaper" point I cannot access a Terminal, whereas with the upgraded system I can get to CLI Mode with CTRL+ALT+F2.

I would prefer vastly to have a working LiveCD and install of 17.10 directly, rather than to continue with the upgrade, as I anticipate having the same exact problem at each successive upgrade stage and I'd really rather not muck with that if I don't have to. The patch script is available at the long URL above (the bloggy one) along with various supporting scripts, and the command I'm using to run the script is ```
./isorespin.sh -i /media/starhawk/DATA/downloads/xubuntu-17.10-desktop-amd64.iso -w /media/starhawk/DATA/linuxium-temp -f wrapper-linuxium-install-UCM-files.sh -c wrapper-linuxium-install-UCM-files.sh 
```

Regarding the above command, 'starhawk' is my username, and 'DATA' is the partition of the SSD in my (main) computer, where the ISO lies. (This is not the same computer as the homebrew laptop, and it runs Mint 18.1... not that that matters here.) I have to use Rufus (on Win10, groan) to 'burn' the patched ISO to the USB drive from which I'm booting the system, by the way, as I don't have a UEFI-compatible optical drive, and these MiniPCs, along with everything else, only support booting from GPT-partitioned drives, which Rufus lets me set (unlike most, if not all, other such utilities).

Can someone advise me on how to proceed here?

---

### Post by starhawk2 on 2017-10-29
...well, in a blaze of mind-boggling stupidity, when I discovered that I could upgrade to 17.10 via CLI, I did.

Now I have the same problem as with the LiveCD -- it does not produce a full desktop, I can't get to CLI, and I don't know quite what to do. I do NOT want to argue this thing all the way back to freaking 16.04.

---

### Post by ubfan1 on 2017-10-29
Might be a memory problem (too little).  Try Lubuntu instead of Xubuntu for a start.  Also, do you have any swap set up?  It might help a lot to dedicate 2G for swap on the SSD.  Did you ever run the straight memory check from the install media?

---

### Post by starhawk2 on 2017-10-29
THANK YOU for replying. FINALLY someone is trying to help me! :)

I never ran the memory check, and I've not set up swap (probably for the better that I didn't, actually -- eMMC is not nearly as resilient, I hear, as a real SSD) -- but there's very little in these things to fall apart (and it has no history of RAM Issues) -- and it if it is the RAM, the system's essentially bricked. These MiniPCs are not expandable in any way -- the RAM is soldered down.

FWIW, I also tried Ubuntu Budgie, and it had the same issue. I'll give Lubuntu a shot, though, after I try one other thing that I found somewhere else. I think the problem may be Wayland, so I'm gonna try to disable that.

---

### Post by efflandt on 2017-10-29
If you get to a desktop background with nothing on it, does Ctrl+Alt+T bring up a terminal window?

---

### Post by starhawk2 on 2017-10-29
No, it doesn't. I wish!

Throwing an idea out there -- I'm reading on The Great Google that *buntu 17.10 is supposed to use something called "GDM" as its display manager, as a switch from something else called "LightDM". (You can tell how much I know what I'm doing here, lol...) I have LightDM and I *don't* have GDM. Could that be doing it? If so, how do I install GDM over LightDM from a LiveCD? (chroot somethingorother? I'm not a *complete* dolt -- I know a little... usually just enough to get me in trouble, tho.)

---

### Post by oldfred on 2017-10-29
This old post?
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

I have never had to change from defaults.

Did you just add the 32 bit UEFI boot file to the live installer?
[https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188](https://h30434.www3.hp.com/t5/Tablets-and-Mobile-Devices-Archive-Read-Only/Linux-on-the-HP-Stream-tablet/td-p/4829188)
Older instructions for 32 bit UEFI:
[https://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393](https://ubuntuforums.org/showthread.php?t=2307022&page=2&p=13410393#post13410393)

I downloaded Fedora Rawhide and its grub/install has support for 32 bit UEFI and the bootia32.efi and a grubia32.efi you need. But its grub is hard coded to certain configurations.

They have this in their notes, I only install 64 bit, but probably same issue with 32 bit.
 Fedora
grub2-install shouldn't be used on EFI systems. The grub2-efi package installs a prebaked grubx64.efi on the EFI System partition, which looks for grub.cfg on the ESP in /EFI/fedora/ whereas the grub2-install command creates a custom grubx64.efi, deletes the original installed one, and looks for grub.cfg in /boot/grub2/. 

Ubuntu's version of grub is hard coded to look for grub.cfg in /EFI/ubuntu. But Ubuntu's grub is just a 3 line configfile to full grub.cfg in your install. Fedora seems to put full grub.cfg in ESP - efi system partition.

---

### Post by starhawk2 on 2017-10-29
The patch script, as described at the relevant link in my first post, does a bit more than add 32b UEFI support. As *I* used it for the LiveCD image described in the same post, it also bundled in some sound drivers.

I don't remember exactly what I did to get 16.04 to boot on this thing, it's been quite a while. I know it involved some combination of an earlier version of that isorespin.sh script, some manual finagling, and an Internet connection. But that's all I remember.

Can you tell me how to boot with a LiveCD/LiveUSB and make the GDM/LightDM change *on the host system* and NOT on the LiveWhatever system...?

Meanwhile, I'm going to try one other thing that's bugging me. This particular box has a clock problem -- the CMOS battery is either dead or disconnected, and so its clock doesn't 'tick' when the machine is off. It doesn't /reset/ the clock, it just doesn't advance it. I have another one of these MiniPCs that doesn't have that issue, and I'm going to try booting Xubuntu 17.10 on it, just to see if there's a difference. If if boots fine on the other MiniPC, I can swap the boards between the two and just be done with it...

Since "Edit Post" isn't working for me...

Trying the other MiniPC didn't work. Same result. Oh well.

Lubuntu /almost/ works. Interesting... I get the wallpaper and a trio of icons (Trash, SSD, and Install) but no taskbar or cursor.

This may very well be a RAM/swap problem.

Ya know, I think I had a brain fart there. (I'll get the air freshener.) 2gb RAM ought to be plenty to run this thing. Xubuntu requires one quarter of that, period, and requests about double the minimum (i.e., needs 512mb, requests 1gb). LXDE being what it is, Lubuntu probably is even less.

This logically can't be RAM.

[B]Hey everybody, I think I figured it out!

[/B]It's GDM. I reinstalled 16.04 (it went smoothly) and then attempted the switch to GDM. Upon reboot, it gave me a gray screen with no wallpaper, icons, cursor, or taskbar.

So... gee, how do I force LightDM in 17.10?

You know what... "if it ain't broke..."

I think for now I'll just stick with Xubuntu 16.10. This system is my box for doing serious writing, and NaNoWriMo (National Novel Writers' Month aka November) is coming up real fast. Maybe in December I'll look at upgrading again, but for right now there's just too much pain there to deal with.

I'm not marking this solved, because it's not, not really, but I am going to say I'm done here.

---

