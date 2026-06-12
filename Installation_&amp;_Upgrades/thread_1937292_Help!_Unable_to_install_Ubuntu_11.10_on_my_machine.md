---
title: "Help! Unable to install Ubuntu 11.10 on my machine"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by mdb122480 on 2012-03-07
Okay, brace yourselves, this may end up kinda long...

I'm a new user to Ubuntu. I initially made a USB installer using Lili USB Creator in Windows 7, then attempted to install Ubuntu in place of Windows. (I also created a Live CD to boot from; more on that later.) Here's how I did the install:


[LIST]
[*]When the program first started up and asked me if I wanted to just try Ubuntu from the USB or to install, I chose to install.
[*]I selected the option that would install Ubuntu over Windows. (Of course, I made a backup of my system, just in case.)
[*]I filled in all the necessary information, and also downloaded the driver that allowed me to set up WiFi so that I could download other drivers/updates as it was installing.
[*]Then I waited.
[*]When the install was closed to being finished, it told me that I would need to restart the system in order to finish the setup, so I clicked the "restart" button.
[/LIST]
This is where my problems start...it won't finish the setup! If I left it all alone, then (due to my boot sequence) it would simply restart and put me right back at the installation screen, asking me if I wanted to just try Ubuntu, or install it, just like nothing ever happened!

If I tried to remove the USB while the machine was rebooting, it said, "disk read error" and did nothing.

If I entered the Setup Menu and changed the boot sequence before it could boot from the USB, again, it would do nothing when rebooting. Just a little cursor blinking on a black screen.

Conversely, if I tried booting from the CD I made, the CD would auto-eject while rebooting, and, again, do nothing once the reboot commenced.

I got the brilliant idea to download the previous version of Ubuntu, still available on the site, and make another bootable USB to see if I could get that one to install, but as I cannot get a good install from the current system, I am stuck using Ubuntu on the trial basis from my USB drive and cannot overwrite it while I'm using it. I currently do not have another USB stick, nor do I have another blank DVD to write it to.

As I chose the option that wrote it over Windows, Windows is now gone and I am at my wit's end, stuck without an OS. Does anyone have any ideas on what I'm doing wrong? I would greatly appreciate any constructive feedback. Thanks!

---

### Post by darkod on 2012-03-07
I would try without the wi-fi driver and without installing any updates during the install.
It has everything it needs on the cd/usb. And it doesn't need internet connectivity. The install process doesn't ask for a restart to continue in general. When it asks to restart, it's already done.
Not sure if installing updates at the same time made it ask for a reboot.

Try without it.
Since windows is not there right now, the options to install might be different but just tell it to use the whole disk for ubuntu and that's it.

---

### Post by mdb122480 on 2012-03-07
> **darkod said:**
> I would try without the wi-fi driver and without installing any updates during the install.
It has everything it needs on the cd/usb. And it doesn't need internet connectivity. The install process doesn't ask for a restart to continue in general. When it asks to restart, it's already done.
Not sure if installing updates at the same time made it ask for a reboot.

Try without it.
Since windows is not there right now, the options to install might be different but just tell it to use the whole disk for ubuntu and that's it.

Well, I tried that, and again, I got the blinking cursor of death on a black screen. I'm really at a loss on what to do here, I really love this OS but I just can't seem to get it installed properly.

---

### Post by darkod on 2012-03-07
Hold on, that is different. If the install process said it finished correctly, but the first boot doesn't work, it might be video issue.

Did you check whether the cd can boot into live mode correctly or it does the same? You should always check if live mode works before starting the install.

Right now, you can try:
Since you have only ubuntu, there is no visible grub boot menu at start. When you boot, hit Shift couple of times to make the menu show.
When you have the ubuntu normal entry highlighted (not the recovery entry), hit 'e' to edit the boot lines.
With the arrows keys, move towards the end of the line starting with 'linux', just before 'quiet splash'. Type nomodeset in front of them.
Hit Ctrl + X to boot with the modified lines.

If that boots successfully we can tell you how to make the fix permanent, the editing of the boot lines was only temporary. Sometimes you don't even need to make it permanent, all you need is to boot once and install (activate) a video driver.

---

### Post by mdb122480 on 2012-03-07
When I hit shift a couple of times and select English as the preferred language, this is what I see:


 ubuntu

live mode
install
file integrity check
memory test

There are also options for the F keys at the bottom consisting of Help, Language, Keymap, Modes, Accessibility, and Other Options. When I select Modes, I see Normal, Use Driver Update Discovery, and OEM Install (For Manufacturers). When Normal is highlighted, I press 'E' but nothing happens.

---

### Post by darkod on 2012-03-07
It seems to me we are talking about different things.

You seem to be talking about booting from the cd.
I was talking about booting from the hdd. You do have ubuntu installed right? But it doesn't boot, it just displays black screen with a cursor?

Try booting from the hdd and do the above explained procedure.

---

### Post by mdb122480 on 2012-03-07
> **darkod said:**
> It seems to me we are talking about different things.

You seem to be talking about booting from the cd.
I was talking about booting from the hdd. You do have ubuntu installed right? But it doesn't boot, it just displays black screen with a cursor?

Try booting from the hdd and do the above explained procedure.

But it's when I boot from the hdd that the black screen happens. Something is preventing the install from performing correctly, so I think it just aborts the process completely; with the disc/USB, it just boots to the install page. Without, it boots to nothing. I even tried hitting Shift just to make sure, but nothing happens.

---

### Post by darkod on 2012-03-07
Are you sure you are not hitting Shift too late? Immediately after the POST test ends, start hitting it. It should show you the boot menu.

---

### Post by mdb122480 on 2012-03-07
Positive. Nada.

---

### Post by mdb122480 on 2012-03-07
I also decided, on the advice of a friend, to try typing "Ubuntu (brand of machine)" and discovered that my machine is certified for version 10.10. I suppose I could also try downloading this and trying it out...maybe it's more compatible with my hardware?

---

### Post by darkod on 2012-03-07
If you boot with the cd/usb and select Try Ubuntu, will it load the live mode?

If it does, you can run the boot info script from the link in my signature, and post the results as explained there. It will show more details.

Depending what that shows, you can try with 10.10 later.

---

### Post by mdb122480 on 2012-03-07
Nope, that didn't work either. I'm stumped.

---

