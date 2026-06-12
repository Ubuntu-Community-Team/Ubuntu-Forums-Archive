---
title: "Can one Install Ubuntu on a Netbook Flexx 11?"
date: 2015-06-12
forum: Installation &amp; Upgrades
---

### Post by irv on 2015-06-12
I have been looking at the Netbook Flexx 11 Tablet with keyboard. I saw them at Walmart for $227 with Windows 8.1 and $197 With Android 5.0. 
[Walmart.]("http://www.walmart.com/ip/Nextbook-Flexx-11-with-WiFi-11.6-Touchscreen-Tablet-PC-Featuring-Windows-8.1-Operating-System-Black/44503406")
I was wondering if anyone has tried to install Ubuntu on it yet, or if it is even possible?
I know it would have to happen via USB because there is no CD/DVD.
I know the processor is an Intel Atom Z3735F Quad-Core Processor which is not like the i3, i5, or i7.

---

### Post by sudodus on 2015-06-12
I would try a lighter desktop, Lubuntu, Ubuntu-Mate or Xubuntu in a netbook. And I mean ***try***, because several new computers have a non-standard UEFI system, that tries to lock out other operating systems than the one installed. Would you buy it locally or via the internet?

So if you don't get a reply from someone with hands on experience, or find positive information in some other way, avoid buying it via the internet.

---

### Post by irv on 2015-06-12
I thought I would just get it a Walmart. That is if I can talk my wife into letting me buy it. She said I have to may toys already.

---

### Post by meshak on 2015-06-12
Well, I have a Lenovo Flex 10,and Ubuntu is great on it! The only downside is i cannot figure out how to get to the BIOS menu. Or do i even have BIOS? Lol. Unless you are a careful person, and won't do anything dangerous for your Netbook, it should be fine, otherwise, when you need to accsess that menu thing, you may not be able to. So think more than twice.

---

### Post by irv on 2015-06-13
The more I think about it, I have Ubuntu on my laptop and my server, I also have it on my sound system so I might just keep Windows on the netbook if I get it. I know it will come with a free upgrade to Windows 10 when it is released. I dual  boot with Ubuntu and Windows on my laptop, I am not one of those persons who say I am just going to use Ubuntu and Ubuntu only. I do use Ubuntu for every day use but there are times I use and need Windows so I use both. I also have Android on my tablet and Chrome OS on a Chromebook. In this day and age we have a lot to choose from.

---

### Post by hmfan2-0 on 2015-08-16
I say be adventurous, I was able to boot the smaller 10 inch model using a small UEFI trick.  I will explain.  

First step is write your Linux image (grab the 64 bit version) to a USB drive. I recommend using a USB flash disk through the USB OTG for stability due to the wiggly nature of the keyboards.  This is typically the easiest step but I used the windows copy that was pre installed and a program called Rufus to write the image with the settings of GPT for EFI and bios set.  Once it is finished loading up I went into the flash drive to the directory /efi/boot/ and added the file bootia32.efi. I found the file in question in a link within[ this link]("http://askubuntu.com/questions/392719/32-bit-uefi-boot-support").

Once the preliminary parts are completed you will have a usable USB to boot from.  Now all you have to do is do an advanced reboot which is done by opening the charms in windows 8.1 and selecting change PC settings.  Go to Update and recovery, select recovery, and then under advanced startup select reboot now.  This will grant you access to the UEFI settings (I'm sure there is an easier way that doesn't involve windows, but I haven't been successful at it yet) From there, since Secure boot is already disabled on these devices (it was on mine, your mileage may vary, but from that advanced startup it's easy enough to turn off the secure boot if it is enabled) you should only have to select boot from USB and patiently wait for something to happen. It does work, but I noted that it will sit on a black screen for several seconds before any signs of life happen after seeing the linux loader of the flash disk. Eventually you will be greeted by the desired desktop and things will be running.

At first I found the touch screen worked but only as a single point mouse.  I also note that it was stuck in portrait.  This was sort of corrected using a clockwise screen rotation.  but upon doing that the touch screen became useless as it would only register touches on the left side of the screen and not very accurately.  I also noted that WiFi/Bluetooth did not work.  The chip in use in the 10 inch model is a realtek RTL8723BS which I believe is used in a few other models of similar Windows 8.1 with bing tablets.  I am sure that a driver exists already, but it just isn't implemented in the kernel yet. Which would mean that a manual install will be required.  I also found that Sound would not work and when I checked the mixer it claimed it was a dummy audio device.  So obviously there is a missing driver there as well.

So the big answer here is, Can you install Ubuntu or some other Linux? Yes, it is possible with minimal effort, does everything work? Not without some further efforts.

Please note, that my experience was using a Linux Mint 17.2 Cinnamon edition.  It is based on ubuntu so the method should be similar.  Maybe you will get better results with straight Ubuntu.  Also once it reached the desktop everything I attempted to run was really snappy.  I didn't need to use a lighter interface such as XFCE or LXDE.  So what I am saying is that the lighter UIs are not necessary if you don't want to use them.  The Nextbook Flexx series has more than enough power to handle what you throw at them.

Also, sorry for necroing a post that was more than a month or two old...

---

### Post by roland-logikalsolutions on 2015-08-21
> **hmfan2-0 said:**
> I say be adventurous, I was able to boot the smaller 10 inch model using a small UEFI trick.  I will explain.  

Once the preliminary parts are completed you will have a usable USB to boot from.  Now all you have to do is do an advanced reboot which is done by opening the charms in windows 8.1 and selecting change PC settings.  Go to Update and recovery, select recovery, and then under advanced startup select reboot now.  This will grant you access to the UEFI settings (I'm sure there is an easier way that doesn't involve windows, but I haven't been successful at it yet) From there, since Secure boot is already disabled on these devices (it was on mine, your mileage may vary, but from that advanced startup it's easy enough to turn off the secure boot if it is enabled) you should only have to select boot from USB and patiently wait for something to happen. It does work, but I noted that it will sit on a black screen for several seconds before any signs of life happen after seeing the linux loader of the flash disk. Eventually you will be greeted by the desired desktop and things will be running.

Also, sorry for necroing a post that was more than a month or two old...

Well the topic is still very current. Is this really all you had to do for Mint 17.2? I assume it was 64-bit Mint since it had /EFI/BOOT in the ISO. I am making that assumption because the 32-bit ISO for Ubuntu does not have those directories.

I am asking this because I tried exactly this with Ubuntu 15.04 64-bit. I did not install along side, but rather, chose "Erase and install" then the install failed during the final step trying to write grub information. The device was basically empty after that. I could get to the BIOS, but there was nothing on the "disk".

It would be nice if you could put the steps you went through in this post because I have seen a lot of You-tube videos and such of people flailing at this. Might be really nice if the touch screen worked as well, but I assume things will get better there with Ubuntu 16 and the version of Mint based on it.

Did you navigate through the menus (don't remember what they are right now) and ask it to search for proprietary drivers? One needs to do that for certain Nvidia video cards, etc.

Thanks for posting!

---

### Post by wandalalakers on 2015-08-21
This seems really interesting.

---

### Post by roland-logikalsolutions on 2015-08-21
In a week or so when I get my replacement I will try the wubi of Ubuntu 15.04 64-bit. I know, I really should use 32-bit, but...

---

### Post by sudodus on 2015-08-21
... and please don't use wubi. It is no longer developed and no longer supported by Canonical. It cannot work with [most] new computers with Windows. See this link.

[Forums Staff recommendations on WUBI](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by westie457 on 2015-08-21
> **roland-logikalsolutions said:**
> In a week or so when I get my replacement I will try the wubi of Ubuntu 15.04 64-bit. I know, I really should use 32-bit, but...
You will be very disappointed if you try this.
A quick google search using 'wubi and uefi' brings a lot of results all saying the same thing. 

**Wubi does not work **with uefi settings or the 'gpt' partition table on modern drives.

If you do get it to work, you will surprise a lot of users on this forum.

---

### Post by roland-logikalsolutions on 2015-08-21
I don't have any other option on that machine. Actually, I have Flexx 10 not 11. Windows 8 blows. Need to get some kind of Linux on it and with only 1Gig of RAM that means NO VM.

---

### Post by hakuna_matata on 2015-08-23
> **roland-logikalsolutions said:**
> I will try the wubi of Ubuntu 15.04 64-bit. I know, I really should use 32-bit, but...
Besides the current official maintainance situation of Wubi:

Some months ago, an Ubuntu user asked me for Wubi support of a 32 bit EFI. He had purchased an Acer Iconia 8W. I changed a working Wubi version and he tested that version. That version still exists [here]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na?dl=0") (wubi1504-32.exe). As far as I know the boot loader worked but installation failed because drives were not correctly detected. So he could use boot loader only to boot into a live environment by pressing "ESC" and selecting "Demo Mode". 

It often seems that Wubi works if a standard install does not work but it is not possible to use more compatible Windows driver in a Wubi installed Ubuntu. Of course, Wubi is a Windows program but it only runs during Windows part of install and uninstall.  Linux part of install and Ubuntu itself must always run without the help of any Windows program.

So maybe this information is helpful for you but I don't expect that Wubi is a solution for you.

---

### Post by roland-logikalsolutions on 2015-08-23
Actually, everything for a regular installation "worked" once I put a 32-bit efi boot on the media. The very last step, where it tries to install grub failed. That failure step left the drive wiped.

I have not had time to look into it. Current project has me in the office working both Saturday and Sunday. Might have time next weekend, once I exchange the unit. The installer correctly identified the drive. I believe there was some boot sector protection which forced grub install to abend. Others have written one must never delete the special EFI boot partition Windows creates because the BIOS relies on it. I do not know for certain.

What I do know is that Cononical needs to be negotiating with Wal-mart to get a Ubuntu based version of this thing on their shelves. I have no love what-so-ever for Wal-mart. If this client hadn't wanted to test one of those devices and it could have been found at _any_ other place I would have bought it there. According to numbers people working in the hardware side of things have seen, that Flexx 10 is currently the best selling computer in America, if not the world. It doesn't feel "cheap" like the bulk of the sub $300 2:1 computers. With a price tag of around $178 it is flooding the back to school market.

Currently there are 2 flavors. One with Windows 8 and another with Android.

---

### Post by sudodus on 2015-08-24
With a wiped drive you might as well try a system that is still being developed - still in the 'unstable' PPA. Try to install a persistent live system with an Ubuntu flavour with [mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10). It should run from USB as well as from an internal drive, and it can run 32-bit as well as 64-bit operating systems in BIOS mode as well as UEFI mode.

Maybe you would need to put a 32-bit efi boot on the drive - I have no experience of the Flexx 10 and 11.

---

### Post by roland-logikalsolutions on 2015-08-24
> **sudodus said:**
> With a wiped drive you might as well try a system that is still being developed - still in the 'unstable' PPA. Try to install a persistent live system with an Ubuntu flavour with [mkusb version 10]("https://help.ubuntu.com/community/mkusb#mkusb_version_10"). It should run from USB as well as from an internal drive, and it can run 32-bit as well as 64-bit operating systems in BIOS mode as well as UEFI mode.

Maybe you would need to put a 32-bit efi boot on the drive - I have no experience of the Flexx 10 and 11.

Some coworkers were able to install generic Windows 10 on it. We didn't have the OEM version to try. The thing they found there is you had to manually change the orientation and use it in laptop mode because it didn't have the table drivers to understand physical rotation. I would think since Ubuntu is trying to also support phones that it should be a bit better, but who knows. I may get to it this coming weekend.

---

### Post by hmfan2-0 on 2015-09-12
Well I'll be, I lose the link for a few weeks ago, and find it took off without me.  Anyway as I did not actually install to my Flexx 10 and only went as far as live-boot, I never delved into the need to modifying grub to boot with a 32-bit UEFI (hint right here).  That said however, there is a very nice website that covers a similar device that I was using for reference on how to get it going.  They state that once you do the initial install, you are not quite done as you still need to make a modification to Grub itself.  [This link]("http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/") is probably the most useful and closest you will get to getting everything up and running.

The only thing I could think of that would need to be changed for the instructions would deal with which wireless chipset drivers that you install as the Flexx series uses a Realtek instead of a Broadcom.  Also potentially the gyro (or whatever they call that thing) that controls screen rotation and orientation.  Touch "worked" but wouldn't rotate with the screen rotation setting (ended up with left side of the screen touch recording but would move the mouse up and down when going side to side. Probably need some scripting there that I wouldn't be familiar with.

> **roland-logikalsolutions said:**
> I don't have any other option on that machine. Actually, I have Flexx 10 not 11. Windows 8 blows. Need to get some kind of Linux on it and with only 1Gig of RAM that means NO VM.

Not meaning to contradict you here, but the Flexx models actually have 2 GB of RAM. It was the Nextbook 10.1 (earlier model) that had the 1GB.

Also to note, the Android version is called an Ares instead of a Flexx

---

### Post by roland-logikalsolutions on 2015-09-12
> **hmfan2-0 said:**
> Well I'll be, I lose the link for a few weeks ago, and find it took off without me.  Anyway as I did not actually install to my Flexx 10 and only went as far as live-boot, I never delved into the need to modifying grub to boot with a 32-bit UEFI (hint right here).  That said however, there is a very nice website that covers a similar device that I was using for reference on how to get it going.  They state that once you do the initial install, you are not quite done as you still need to make a modification to Grub itself.  [This link]("http://www.jfwhome.com/2014/03/07/perfect-ubuntu-or-other-linux-on-the-asus-transformer-book-t100/") is probably the most useful and closest you will get to getting everything up and running.  The only thing I could think of that would need to be changed for the instructions would deal with which wireless chipset drivers that you install as the Flexx series uses a Realtek instead of a Broadcom.



Not meaning to contradict you here, but the Flexx models actually have 2 GB of RAM. It was the Nextbook 10.1 (earlier model) that had the 1GB.

Also to note, the Android version is called an Ares instead of a Flexx

I had actually followed much of that link before loaning it to some coworkers who put generic Windows 10 on it to test some things. After they did that, nothing using external media would boot. Windows 10 really locked things down. Well, would not boot is a tiny stretch. The text grub menu would come up and after selecting Install Ubuntu it would come up with the multi-dot splash screen then hang at some point before the graphics came up.

Right now the machine is a paper weight. Windows 10 did not have the drivers. Tech support for NextBook is less than useless when it comes to locating original ISO or Windows 10 drivers. The only thing I found out from them is that Windows 10 upgrade is not recommended for most of the product line. In another week or two, when I have some more free time I will once again delve into putting something useable on it. I did pull down a Windows 8.1 installation media set from Microsoft in some attempt at getting the machine functioning again. I will also re-open the technical support ticket trying to get original OEM installation media.

It is really kind of sad. That little machine would make an excellent travel computer if I could get Mint or Ubuntu on it. Certainly better than the HP I'm typing on right now. HP used all 4 primary partitions so I am faced with wiping the thing and running only Ubuntu, but am hesitant with EFI and the way the boot seems to be checking for several of the partitions before booting.

Perhaps when Ubuntu 16 LTS comes out they will finally have 32-bit EFI bundled into the ISO and actually work on that NextBook. It is one of the best selling computers on the market right now. With good reason too. It is physically solider than most Chromebooks I've seen and it is capable of running an actual OS. More importantly, with a sub $200 street price the thing is cheaper than many Chromebooks. With an SD added for data storage it would be quite good for writing documents with Libre Office, checking email, etc. The screen resolution is high enough one might even be able to use it to watch movies while traveling. It has 2 real USB ports as well as a mini port for external monitor so you could plug it into a nice big monitor when you got where you were going as well as connect keyboard and mouse.

---

### Post by hmfan2-0 on 2015-09-12
That's sad to hear.  Then again that's a matter of how it was installed from what I have found. windows 10 supposedly works fine on these devices if it is installed through the "upgrade program".  But if you try a fresh install it pretty much self destructs and becomes useless due to lack of driver availability.  But you likely knew that already right?

To note, even with windows 8.1, the boot from external flash for Linux Mint 17.2 hung for quite a bit after I managed to get to the grub screen.  It had a blank screen for a good minute or so before anything seemed to move.  It did eventually make it to the Cinnamon desktop though and everything ran smooth from there.  It could have been the speed of USB2.0 that was dragging it down on that point though and not so much booting on oddball hardware with some stops for errors dealing with unknown devices.

As they are so cheap though, it's not hard to pick up another. And from what I have seen from the site in question it will in theory get a usable system. but for simplicity and for the lack of Wireless card driver availability, I would suggest getting a wifi dongle that uses a supported chipset for the steps of making the system bootable.  That said the Wireless card is a Realtek RTL8723BS SDIO.  Hopefully someone can run with that info.  Otherwise I can just use my WiPi that I scavenged from my DIY drawer.

Oh the SD card slot sort of worked but wouldn't read an EXfat partition (could have to deal with no EXfat driver or whatever was installed).  The slot is SDXC compatible however.

Also to note the reason they sell so well is not just the price, but the availability. Walmart is everywhere, and all of them from what I have experienced are carrying these things.  Imagine if they decided to put these already low cost devices on sale... I'd probably buy 3 if the price went to 150 or lower.

The only real issue I had is with the pogo connection between the tablet to the keyboard. It's not exactly the most stable of connection points, but I didn't expect it to be as I have an Asus tf300t with the dock and that was flaky too.  Also to note, unlike the tf300t, the USB ports on the keyboard are low power, so don't expect to plug external hard drives to either of the ports.

---

### Post by roland-logikalsolutions on 2015-09-12
> **hmfan2-0 said:**
> That's sad to hear.  Then again that's a matter of how it was installed from what I have found. windows 10 supposedly works fine on these devices if it is installed through the "upgrade program".  But if you try a fresh install it pretty much self destructs and becomes useless due to lack of driver availability.  But you likely knew that already right?

To note, even with windows 8.1, the boot from external flash for Linux Mint 17.2 hung for quite a bit after I managed to get to the grub screen.  It had a blank screen for a good minute or so before anything seemed to move.  It did eventually make it to the Cinnamon desktop though and everything ran smooth from there.  It could have been the speed of USB2.0 that was dragging it down on that point though and not so much booting on oddball hardware with some stops for errors dealing with unknown devices.

As they are so cheap though, it's not hard to pick up another. And from what I have seen from the site in question it will in theory get a usable system. but for simplicity and for the lack of Wireless card driver availability, I would suggest getting a wifi dongle that uses a supported chipset for the steps of making the system bootable.  That said the Wireless card is a Realtek RTL8723BS SDIO.  Hopefully someone can run with that info.  Otherwise I can just use my WiPi that I scavenged from my DIY drawer.

Oh the SD card slot sort of worked but wouldn't read an EXfat partition (could have to deal with no EXfat driver or whatever was installed).  The slot is SDXC compatible however.

Also to note the reason they sell so well is not just the price, but the availability. Walmart is everywhere, and all of them from what I have experienced are carrying these things.  Imagine if they decided to put these already low cost devices on sale... I'd probably buy 3 if the price went to 150 or lower.

The only real issue I had is with the pogo connection between the tablet to the keyboard. It's not exactly the most stable of connection points, but I didn't expect it to be as I have an Asus tf300t with the dock and that was flaky too.  Also to note, unlike the tf300t, the USB ports on the keyboard are low power, so don't expect to plug external hard drives to either of the ports.


I was truly hoping they would have actual technical support which could point me to an ISO I could use to flash back to factory 
fresh, but sadly, they have less than zero technical support. Given the command of the English language and weeks between responses I would not be surprised to hear the tech support center was in North Korea and the reason for the lag is the center only has electricity one day per week.

I did find a downloads page which claimed to have some firmware and driver downloads.

At any rate, I need to find something which can boot and wipe it. If tech support cannot provide a file which lets me fix this myself then I will wipe it and exchange for a fresh one. When it comes back to them, they can do the wipe and install.

When I said it hangs booting from external devices, I really mean it hangs. I went to lunch and came back with it still on that multi-dot splash screen and the dots weren't moving.

---

### Post by roland-logikalsolutions on 2015-09-12
Actually, now that I think of it, what I really need to do is see if I can get an Image For Linux thumb drive to boot on the thing. If I can, then all I need to do is find someone with a factory fresh one of these, send them the IFL thumb and a 16-gig thumb to image onto. (IFL only backs up used sectors and it does compress, I forget how much was free on the initial 32-gig storage, but... I could send a 32-gig I guess, just to be safe.)

That would get me back to where I need to be, then I could try the on-system Windows 10 update. I could probably tough out a worthless Windows 10 thing once Libre Office was installed. It would be a travel computer. Just used for email and book writing on the road. Bit of Web surfing.

Oh well, I will play with it again after the end of the month.

---

### Post by hmfan2-0 on 2015-09-12
I'm not sure what you are asking.  I was able to get a usable flashdrive using the program Rufus and installing the ISO to a 16 GB USB OTG plug. I think I put the directions on here somewhere. [http://forum.xda-developers.com/showthread.php?t=2500078](http://forum.xda-developers.com/showthread.php?t=2500078) also has good instructions.

  Unless you are referring to reflashing windows 8.1 into the system. At which point I don't think it's going to be possible unless Efun will release it, but at which point you would still need the original CD keys.  Though a thought... if you can junk the windows 10 out of it, you can in theory boot into recovery and fix the old system back to normal because Windows 10 can't touch the read only recovery section.

---

### Post by roland-logikalsolutions on 2015-09-12
> **hmfan2-0 said:**
> I'm not sure what you are asking.  I was able to get a usable flashdrive using the program Rufus and installing the ISO to a 16 GB USB OTG plug. I think I put the directions on here somewhere. [http://forum.xda-developers.com/showthread.php?t=2500078](http://forum.xda-developers.com/showthread.php?t=2500078) also has good instructions.  Unless you are referring to reflashing windows 8.1 into the system. At which point I don't think it's going to be possible unless Efun will release it, but at which point you would still need the original CD keys.

Yes, that is how we got the failed Ubuntu install on it and the Windows 10 generic on it. After Windows 10 generic was installed, it seems to have tweaked something stopping other OS from successful boot using thumb drive.

Generally UEFI machines have the Windows license key embedded in the UEFI firmware. At least that is what a Microsoft certified engineer told me. It is why they no longer come with stickers on the machines.

I'm a couple of weeks out from messing with this machine again. Will rejoin this thread early next month.

---

### Post by hmfan2-0 on 2015-09-12
Consider trying to erase the windows 10 system partition and attempt using recovery... otherwise leave wimdows 10 alone and go pick up a new one.

---

### Post by roland-logikalsolutions on 2015-09-12
> **hmfan2-0 said:**
> Consider trying to erase the windows 10 system partition and attempt using recovery... otherwise leave wimdows 10 alone and go pick up a new one.

Well, it violates my religion to buy anything at Wal-mart. I needed this to test an application per a client request. I don't have any need for it in truth.

Windows 10 is useless on it since it has no drivers, no sense of rotation, very little touch capability. Really abysmal.

---

### Post by hmfan2-0 on 2015-09-13
I can see where you are coming from.  When you get back to the device, try to get into the EFI settings and boot the recovery partition, since Windows 10 can't overwrite that section, it should still have windows 81 and all the drivers (hint) If you can get at the drivers from there you could in theory fix the windows 10 with windows 8.1 drivers.  Or if you can manage to access it with Linux and extract the drivers you could try other tricks.

Also not sure if this would be related, but check to make sure secure boot is still turned off.  That could potentially cause problems.

Another thought, try getting a new Linux Iso (Linux Mint 17.2 worked nicely) and make sure to run hash checks to check integrity.  Then try again using:
     a flash drive, 4 GB or more recommended
     Rufus [/url=http://rufus.akeo.ie/]gotten here[/url]

file system should be FAT32, GPT for EFI selected. MBR doesn't work well from what I have seen.  After that just make sure you put the the 32-bit efi file where it needs to go before you try booting from it, but you knew that last part already I believe. as long as those options are set right, it should boot and not hang.  Heck You getting grub says you already have secureboot off.  Just beware of windows 10's fastboot.

---

### Post by roland-logikalsolutions on 2015-09-13
Oh, that recovery partition is long gone. The one thing which worked really well from Ubuntu 15.04 (after I put a 32-bit EFI loader on the thumb) was "Erase entire disk and install Ubuntu". After nuking 8.1 and installing 99% of Ubuntu it died horribly trying to install grub. I believe the EFI has some of that totally obsolete BIOS type boot sector protection. Hadn't seen that in years so didn't think to look for and disable it.

The machine was sitting unused in that state when coworkers needed to test something under Windows 10 and they needed a device to quickly load it on. I told them to take that because it had to be wiped anyway. Once Windows 10 got put on the machine became a poster child for anti-trust violations. Blocks any and all boots of all non-Microsoft products. I should ship it to the EU commission because we all know American justice will take a bribe rather than put a CEO in prison for criminal activity.

I mean _nothing_ has booted from thumb. Parted Magic, System Rescue CD, Ubuntu 15 32 or 64-bit. The device won't even consider booting from external DVD so the dozen or so other utility tools I have won't boot. I even tried some "Windows based" commercial partition tool. Nada.

Yes, Windows 8.1 would let things boot and let itself be replaced, but Windows 10 is an anti-trust violation conviction in an ISO.

---

### Post by hmfan2-0 on 2015-09-13
Well that's difficult.  though I did find something that could be useful. [This Link](http://www.howtogeek.com/220723/how-to-uninstall-windows-10-and-downgrade-to-windows-7-or-8.1/) says that if the key is embedded as you were stating, you should be able to, If you can find a windows 8.1 with bing ISO, use that to go back to the previous version of windows.  Just don't expect the auto rotate to function. (it appears to be the only driver that doesn't look like it could come through Microsoft update as the touch screen is using a generic intel driver)  From there you should be able to get to linux.  

It's odd really that there is nobody trying to uninstall windows 10 to install Linux.  Maybe in time with the next wave of releases there will be options that will be easier.

---

### Post by roland-logikalsolutions on 2015-09-13
> **hmfan2-0 said:**
> Well that's difficult.  though I did find something that could be useful. [This Link]("http://www.howtogeek.com/220723/how-to-uninstall-windows-10-and-downgrade-to-windows-7-or-8.1/") says that if the key is embedded as you were stating, you should be able to, If you can find a windows 8.1 with bing ISO, use that to go back to the previous version of windows.  Just don't expect the auto rotate to function. (it appears to be the only driver that doesn't look like it could come through Microsoft update as the touch screen is using a generic intel driver)  From there you should be able to get to linux.  

It's odd really that there is nobody trying to uninstall windows 10 to install Linux.  Maybe in time with the next wave of releases there will be options that will be easier.

Actually, I may try it this evening, installing Windows 8.1 that is. I burned a thumb drive the other day. Work is going very well today. I might get out of here in another hour. Spend an hour or two in the common area/deck of the corporate housing unit, and save disappointment of dealing with nextbook for the evening.

My current plan is to put Windows 8.1 on it, find the Nextbook download site I found the other day for firmware and drivers, then let it sit a bit. If I get that much working, I will really want to get my bootable backup software to boot on it and take a full image. The device is soooo locked down though, I may just let the Windows 10 upgrade occur, which "should" leave all of the devices working.

Poked around on the Mint forums the other day. The powers that be at Mint have no desire to support tablets. While I can understand that, the 2-in-1 thing does push the issue.

I really hate Unity. Been forced to work with that for the past few months at client site. When you have to test in 12, 14, and 15 both 32 & 64-bit, you can really see that Unity hasn't gotten any better. Everyone says KDE doesn't do well on tablets or small screens. I love KDE, but I can believe that statement without putting it to the test. In truth, what I love about KDE is Kate and KWrite. While I do much of my development in QtCreator on Linux, I do still need other powerful editors. I write a ton of blog posts with KWrite mainly because Libre Office has an on-again off-again cut & paste compatibility with WordPress.

Been experimenting with Atom editor from Git. It is mostly annoying. Doesn't work the same between Windows and Linux, and is missing some features I tend to use quite a bit such as column insert and column selection. I'm also not a big fan of having to open a directory to have a file list on the left. I understand it was created to work with Git projects which exist in directories, but, having just an open file list on the left is what I've become used to.

I have been thinking that either Cinamon or Mate would be better choices on the Nextbook. Can't remember which is based on the old Gnome2, but that one really has come a long way. I cannot honestly call it Gicky-Gnasty-Gnome anymore. Gnome3 on the other hand...<Grin>

Will let you know how the Windows 8.1 re-install goes some time this evening.

Making it this difficult to replace an OS has _got_ to be an anti-trust violation of biblical proportions.

---

### Post by roland-logikalsolutions on 2015-09-13
Windows 8.1 does not have 32-bit EFI boot capability. This puddle of poo has only 32-bit EFI. I have never wasted so much time on something I had no need of.

---

### Post by hmfan2-0 on 2015-09-13
That's why they came with a 32 bit version of windows in the first place, I guess I forgot to mention that. 64 bit hardware, 32 bit OS unless it's Linux. And the one that is based on Gnome 2 is MATE.  Cinnamon is very different.  but you will find that both of them will not be very touch screen friendly.

---

### Post by roland-logikalsolutions on 2015-09-14
Right now Windows 10 isn't "touch friendly" on the machine. Windows 8.1 32-bit from Microsoft didn't have 32-bit EFI. I tried your advice of navigating through to "Restore this device", told it to wipe everything. It appears the Windows 10 install created a Windows 10 restore partition and did not leave the original 8.1 in place. I did ironing and watched some TV because the fresh install took forever. Once it was quasi-functional, I did a search for "nextbook drivers" which came up with a link I cannot find using Bing now. There was a download link from someone in a Microsoft forum. A full zip file of non-Microsoft drivers for nextbook.

I managed to navigate to the device manager and install drivers for all of the devices which were missing drivers.

Touch "sort of" functions. Tablet rotation is simply not even trying to work. If I have time tonight I will go through the long, slow, one at a time, "update driver" of each device pointing it to that directory. Hopefully that will fix things.

Over lunch today though I'm going to surf for a 32-bit EFI bootable ISO which can either secure erase of wipe all partitions on the machine so I can just exchange it.

Windows 10 is even worse than Windows 8.

---

### Post by roland-logikalsolutions on 2015-09-14
Found interesting post here:
[http://www.olli-ries.com/t-242d/](http://www.olli-ries.com/t-242d/)

It sounds like one must wait for Ubuntu Personal releasing some time after 16.04 LTS

Now word on whether Ubuntu Personal will have an LTS version though.

---

### Post by hmfan2-0 on 2015-09-26
I'm not sure exactly what I am reading there. didn't see any mention dealing with nextbook or touchscreen based devices, just things dealing with snappy and such.  If you are saying that there is something there that I missed that says that this Ubuntu Personal is going to be the answer to small touch devices that are being forced to windows 10, then maybe.

Anyway that's kinda surprising that Windows 10 overwrote a read only partition.  though I guess considering how we do it with Linux all the time I shouldn't be to surprised really. Now if you were still within the time to return it to walmart (or wherever you actually got it) and exchange it, I would have suggested doing that and saying that (if asked of course) that windows 10 broke it.

On that note though, If it exists, Windows 8.1 with Bing was what was what was originally installed on these tablets.  It might make a difference in the search for the right ISO file.  Unless there is some crazy way to add that bootia32.efi to the windows install media.  probably not but who knows right?

I do have to say, good luck getting that screen auto rotate to work, I would just make it flip in the settings of the display and call it good. (did that in Linux when I managed to boot it.

---

### Post by roland-logikalsolutions on 2015-10-05
Arrrghhh.

Let us see if the forum will accept this post. My previous response to you went into the ether.

I did get the Nextbook working properly with Windows 10. Even wrote a blog post about it here: [http://www.logikalsolutions.com/wordpress/?p=1529](http://www.logikalsolutions.com/wordpress/?p=1529)

To me the paragraph in the link which indicated Ubuntu Personal would be what works on this was the blurb about "built-in" screens. To me that means tablets, 2:1's, and dumb phones.

For now the Nextbook is boxed up on a shelf in my office. I'm home helping with harvest and haven't had enough free time to chew through my higher priority to-do list. I do have books to promote as well as finish writing. I even got so offended by current political "news" that I turned an old blog post into an official government petition: [https://petitions.whitehouse.gov//petition/pass-ethics-income-act](https://petitions.whitehouse.gov//petition/pass-ethics-income-act)  So I'm dealing with that as well.

---

### Post by hmfan2-0 on 2015-11-07
I'm glad you were able to figure that out, Now if only there were less messy ways to install Linux (any kind that is) to these devices... let alone any bay trail device without using heavily modified Kernels... not that it's a bad thing to modify a Kernel to suit your needs, but it's still too messy for the average user.

Also sorry for being over a month since I replied.  been busy.

---

### Post by roland-logikalsolutions on 2015-11-09
Not a problem. I understand busy. <Grin>

I've done nothing with this device. In fact I just got around to getting my Acer Aspire One NetBook back in service. It had a lot of different stuff installed for client site testing on it. Finally got done with harvest and getting around to my ever growing to-do list. I did do some poking around on-line and this release note attracted my interest.

[https://kororaproject.org/about/news/korora-23-coral-beta-now-available](https://kororaproject.org/about/news/korora-23-coral-beta-now-available)

The blurb about Gnome now supporting gestures was appealing. The current Ubuntu 15.10 Gnome is broken badly, at least on the machine I tried it on. Lots of Xorg crash reports seem to get sent. The Ugly/Unity desktop doesn't seem to have the same problem in that release. The new Mint release seems to be significantly delayed as well.

---

### Post by bjc2 on 2015-11-09
I had to return my 11" with windows 10 installed because I couldn't boot a windows install dvd, nor could I make a system restore image to a usb drive. Also, the on/off only worked part time.

Have you tried 15.10 and failed? I notice a gentoo posting that claims to have linux in a usb drive at [http://www.vanade.com/~blc/html/nextbook8lin/](http://www.vanade.com/~blc/html/nextbook8lin/) He claims the usb will boot just by pressing windows BUTTON and power BUTTON at the same time. These two buttons are on the screen part, not the keyboard.

 See if you can get 15.10 live image working that way.

---

### Post by roland-logikalsolutions on 2015-11-09
I have not tried 15.10 on it and I don't believe I will. I may try the new LTS when it comes out, most likely the Gnome version because I don't see Ugly/Unity working well on a touch device. The brief time 15.10 Gnome was running on a BOINC machine it seemed to be completely designed for a touch screen. You had to "flick" the screen saver away and do other things which seemed very "droid like."

I will be most interested in the new LTS from Mint when it comes out. I have found Mint does a lot more testing than Ubuntu. The down side is the Mint crowd only wants to focus on "desktops" and 2-in-1 computers blur that line.

---

### Post by bjc2 on 2015-11-10
> **hmfan2-0 said:**
> I say be adventurous, I was able to boot the smaller 10 inch model using a small UEFI trick.  I will explain.  

First step is write your Linux image (grab the 64 bit version) to a USB drive. I recommend using a USB flash disk through the USB OTG for stability due to the wiggly nature of the keyboards.  This is typically the easiest step but I used the windows copy that was pre installed and a program called Rufus to write the image with the settings of GPT for EFI and bios set.  Once it is finished loading up I went into the flash drive to the directory /efi/boot/ and added the file bootia32.efi. I found the file in question in a link within[ this link]("http://askubuntu.com/questions/392719/32-bit-uefi-boot-support").


I just noticed that 32 bit support was added to the 64 bit grub in January, 2015, so this 2014 post shouldn't be needed. It should be possible to just use ubuntu 15.10.

By the way, I noticed the same default setting in the bios for secure boot as you (disabled). But since my usb didn't work even on windows, I blame the hardware for my inability to boot ubuntu. Thanks to walmart for free returns within 14 days.

Hey OP, maybe you can try.

---

### Post by roland-logikalsolutions on 2015-11-10
My time for testing may be limited. Just got a phone call about a 6 month contract in Boulder. Far too early to tell if I will be going that way or not, but, I won't be taking the unit with me if I take an out of state contract.

Even so, I think I would wait until we have a new LTS. The Gnome desktop is currently too buggy to use with Ubuntu 15.10. All of those crash/problem reports were annoying. I do like the fact it appears to be designed for use with a 2:1 though with all of the swiping required.

I have both an HP laptop and an Acer Aspire One NetBook for travel though. Can't really see myself taking the Flex along as well. May only take the laptop. I mean, just how many portable computers does one need when travelling for work? The Flex keyboard is a bit tiny for prolonged typing. The NetBook is also a bit on the small side. I did not think I would adjust to the HP laptop, but, have found typing on it while in bed pretty comfortable. My fingers might go numb if I used it to write another novel though.

---

### Post by hmfan2-0 on 2015-11-13
> **bjc2 said:**
> I just noticed that 32 bit support was added to the 64 bit grub in January, 2015, so this 2014 post shouldn't be needed. It should be possible to just use ubuntu 15.10.

By the way, I noticed the same default setting in the bios for secure boot as you (disabled). But since my usb didn't work even on windows, I blame the hardware for my inability to boot ubuntu. Thanks to walmart for free returns within 14 days.

Hey OP, maybe you can try.

didn't work? as in the USB on the keyboard or the USB OTG (the micro usb on the tablet section), just curious.

---

### Post by bjc2 on 2015-11-13
> **hmfan2-0 said:**
> didn't work? as in the USB on the keyboard or the USB OTG (the micro usb on the tablet section), just curious.

keyboard, since I didn't have a micro adapter. By the way, there's a youtube video of the usb booting of a windows 10 usb installer, and it clearly shows you have to hold both buttons for a bit more than a minute.

Also, if you enter a serial number at [http://nextbookusa.com/recovery/index.html](http://nextbookusa.com/recovery/index.html), you'll get  Recovery instructions for Nextbook tablet, including a Nextbook_Flash_Instructions.pdf, a windows ISO tool, isotousb_setup.exe, available at [http://www.softsea.com/download/ISO-to-USB.html](http://www.softsea.com/download/ISO-to-USB.html), and a download link for a 5GB windows 8 recovery iso, and the following instructional video. [https://www.youtube.com/watch?v=myuT4frTz2g&feature=youtu.be](https://www.youtube.com/watch?v=myuT4frTz2g&feature=youtu.be)

I wonder if the same softsea iso tool might be useful for other iso, such as windows 10 and even linux? The procedure they recommend is creating the usb from the iso and the softsea and immediately using windows. They never meantion using the windows-power button combination. Instead, after completing the usb drive creation, Go into the “Recovery” mode of the tablet. Under “Advanced Startup”, select “Restart Now”, Choose an Option: Select “Use a Device ” Choose the option “EFI USB Device”. They say the tablet will restart on the usb drive and the install will start automatically.

---

### Post by roland-logikalsolutions on 2015-11-14
> **bjc2 said:**
> keyboard, since I didn't have a micro adapter. By the way, there's a youtube video of the usb booting of a windows 10 usb installer, and it clearly shows you have to hold both buttons for a bit more than a minute.

Also, if you enter a serial number at [http://nextbookusa.com/recovery/index.html](http://nextbookusa.com/recovery/index.html), you'll get  Recovery instructions for Nextbook tablet, including a Nextbook_Flash_Instructions.pdf, a windows ISO tool, isotousb_setup.exe, available at [http://www.softsea.com/download/ISO-to-USB.html](http://www.softsea.com/download/ISO-to-USB.html), and a download link for a 5GB windows 8 recovery iso, and the following instructional video. [https://www.youtube.com/watch?v=myuT4frTz2g&feature=youtu.be](https://www.youtube.com/watch?v=myuT4frTz2g&feature=youtu.be)

I wonder if the same softsea iso tool might be useful for other iso, such as windows 10 and even linux? The procedure they recommend is creating the usb from the iso and the softsea and immediately using windows. They never meantion using the windows-power button combination. Instead, after completing the usb drive creation, Go into the “Recovery” mode of the tablet. Under “Advanced Startup”, select “Restart Now”, Choose an Option: Select “Use a Device ” Choose the option “EFI USB Device”. They say the tablet will restart on the usb drive and the install will start automatically.

Most of the ISO to USB tools you get from Windows vendors are the repackaged Microsoft Tool which only works with Windows ISO files. Do a Web search for RUFUS. Get it from the creators Web site not one of those "free software" sites. If you get it from one of those it will be bundled with at least one virus. RUFUS works for all ISOs. I use it for lots of Linux things when at a client which forces me to use icky nasty Windows...quite the rarity these days.  [http://rufus.akeo.ie/](http://rufus.akeo.ie/)

Your instructions for rebooting are how I managed to boot Ubuntu thumb drive. It was a regular sized drive and plugged into the keyboard.

---

### Post by bjc2 on 2015-11-14
> **roland-logikalsolutions said:**
> 
It was a regular sized drive and plugged into the keyboard.

What is your experience with the normal size usb 2.0 plugs that come with the keyboard?

---

### Post by roland-logikalsolutions on 2015-11-14
> **bjc2 said:**
> What is your experience with the normal size usb 2.0 plugs that come with the keyboard?

Nothing out of the ordinary. I haven't put hundreds in the thing, but, the drives I have which work everywhere worked in it and the ones which only work in "some" machines didn't. I haven't noticed connection issues like most tablets have. By that I mean most tablets seem to get a _lot_ of slop after a few dozen connections. Gospel truth, the unit is sitting on top of its box on a book shelf. I have far too much else going on to mess with it now. Besides, I want to wait for the new LTS (and the traditional 500+Meg of updates which come out 1 minute after the ISO is made available) before trying anything with it. I might even wait for the new Mint LTS and try that on a regular desktop before once more braving a Linux install on the Flex.

---

### Post by hmfan2-0 on 2015-11-17
consider trying one of [these](http://www.amazon.com/SanDisk-connector-Android-Devices--SDDD2-032G-G46/dp/B00RBGYGMO/ref=sr_1_2/184-9206961-4066330?ie=UTF8&qid=1447776381&sr=8-2&keywords=micro+usb+flash+drive) next time to avoid issues with the keyboard USB, in my experience the unit's USB has a low power issues, which causes certain USB drives to not function correctly. (especially spinning platter drives)  So but yeah that was the drive that I used (an older model but still does the same thing).  It was designed with smartphones in mind but works just fine with these 2-in-1's.  It also does away with one of the issues I typically run into dealing with trying to find an OTG adaptor that will not block the charging port.

---

### Post by roland-logikalsolutions on 2015-11-17
> **hmfan2-0 said:**
> consider trying one of [these]("http://www.amazon.com/SanDisk-connector-Android-Devices--SDDD2-032G-G46/dp/B00RBGYGMO/ref=sr_1_2/184-9206961-4066330?ie=UTF8&qid=1447776381&sr=8-2&keywords=micro+usb+flash+drive") next time to avoid issues with the keyboard USB, in my experience the unit's USB has a low power issues, which causes certain USB drives to not function correctly. (especially spinning platter drives)  So but yeah that was the drive that I used (an older model but still does the same thing).  It was designed with smartphones in mind but works just fine with these 2-in-1's.  It also does away with one of the issues I typically run into dealing with trying to find an OTG adaptor that will not block the charging port.

Never buy anything from/through Amazon. They are a malignant tumor which will one day end the human race.

Whenever I get around to it I have adapter cables that convert USB to micro-USB. They are something like 6-8" long so they don't block things. Had a bunch of devices which only had those tiny ports on last project. Everyone who ordered the adapter cables held them sacred.

---

### Post by roland-logikalsolutions on 2015-11-20
Wow! Mint had to drop back to a beta release of 17.3 instead of shipping at end of October. Beta "just" came out in past couple of days.

[http://blog.linuxmint.com/?p=2938](http://blog.linuxmint.com/?p=2938)

---

### Post by bjc2 on 2015-11-28
> **roland-logikalsolutions said:**
> 
I have an Acer Aspire One NetBook. 

I just bought your acer ONE instead of nextbook. Which linux do you like on it, and are there any special tips to getting it going?

---

### Post by hmfan2-0 on 2015-12-01
nobody said buy one from amazon, they can be purchased from just about anywhere.  I got mine from an office supply store.  I just used an Amazon link to make it obvious what the item is.

---

### Post by roland-logikalsolutions on 2015-12-21
I decided life didn't have enough frustration today so I rufused the Elementary OS ISO onto a thumb drive, then had to drag and drop the 32-bit UEFI file I use everywhere to make it boot. __Thankfully__ I chose "try" instead of install. I could find nothing in the settings which would let me rotate the display.

When I saw this distro's description on distrowatch I pulled it down for when I had time to try. They claimed good touch support. It kinda-sorta-works-sometimes. I would hazard a guess the biggest problem is the fact they don't know how the screen is oriented. They just "assume" tablet instead of laptop orientation.

So, back on the shelf until I need more frustration in my life.

I did post a question on the "support" forum for the distro. [https://elementaryos.stackexchange.com/questions/3637/rotate-display-on-nextbook-flex](https://elementaryos.stackexchange.com/questions/3637/rotate-display-on-nextbook-flex)

Anyone who is interested can follow that question to see if there are any responses. It is really too bad they can't get the orientation correct. The distro itself looked kind of nice.

---

### Post by roland-logikalsolutions on 2015-12-23
Apparently there is not enough frustration in my life. I spent most of the day yesterday and most of this morning attempting to get a version of Linux installed on this thing. Installation has become a bit easier, but still cannot get a boot option. Multiple failed install attempts with Ubuntu 15.10 gnome taught me how to rotate the screen in Elementary. There is an obscure gear in the barely visible "display" icon. You have to navigate to it with the mouse, finger will NOT work. Click it, then click the combo box for orientation.

I'm going to write a blog about the journey, either later today or over the weekend. I can now see the Ubuntu option (Elementary is a front end based on ubuntu) but I cannot get it to boot. Others may wish to pick up the torch.

---

### Post by roland-logikalsolutions on 2015-12-25
Blog post about path I went down can be found here: [http://www.logikalsolutions.com/wordpress/?p=1588](http://www.logikalsolutions.com/wordpress/?p=1588)

Really too bad Elementary wouldn't work.

---

### Post by roland-logikalsolutions on 2015-12-27
According to this post: [http://blogs.intel.com/evangelists/2015/08/11/update-on-ia32-uefi-and-linux-support/](http://blogs.intel.com/evangelists/2015/08/11/update-on-ia32-uefi-and-linux-support/) Debian 8.1.0 has a multi-arch version which solves this issue. I scheduled a download during my "bonus window" for tomorrow morning. Hope to have a chance to play with it over the course of next week. It "seems" like it "should" work because it was developed in direct response to this problem. Doubtful the boys and girls at Canonical will see fit to follow suit with a multi-arch version.

---

### Post by roland-logikalsolutions on 2015-12-30
All,

I wasted a _lot_ of time over the past few days trying to  get Linux in Dual Boot mode onto this device. Debian refused to  recognize the second SD card, so it was mostly a non-starter after  taking the time to download nearly 4Gig over a satellite connection.

I  went back to Elementary since it had gotten so close. On a whim I used  the "diskpart" command line tool from Windows to "CLEAN" the second SD  card. This leaves it in an unformatted state. I experienced great joy  when the installation choices had something like "This machine appears  to be using Windows Boot Manager. Install alongside Windows and you will  be able to select from boot menu..." No such luck.

Read  everything I could find. Some computers force the Microsoft boot loader  no matter what.  [http://www.rodsbooks.com/efi-bootloaders/installation.html](http://www.rodsbooks.com/efi-bootloaders/installation.html)

Tried  every file I could think of with bcdedit command from this link:  [http://unix.stackexchange.com/questions/242627/grub-menu-not-showing-in-dual-boot-linux-mint-17-windows-10](http://unix.stackexchange.com/questions/242627/grub-menu-not-showing-in-dual-boot-linux-mint-17-windows-10)

I  even went so far as to rename bootmgrfw.efi and copy bootia32.efi to  that name in the \EFI\Windows\Boot directory. NO LUCK. It appears the  firmware on this machine has its own Windows Boot Manager with its own  settings. When I navigate to the DOS looking firmware settings screens  and get to the boot manager menu, I do see 2 entries for Windows Boot  Manager which is a bit odd, but....

At any rate. Some time after  supper tonight or early in the morning, I'm going to try the sucky way  which _should_ always work. Install on the second drive and put the boot  manager there. This means I cannot dual boot, but have to boot that  virus known as Windows then navigate to "use a device" to choose the  Ubuntu drive. ^)*(&)(*&)(&*^)*(

We are now at the  point where we need someone who knows a lot about the virus Known as  Windows, in particular, the Windows Boot Manger and how it gets embedded  into firmware. There appear to be some kind of options which can force  default boot of Windows without _EVER_ showing a menu.

I "did"  see visual evidence of attempts. There was a lot of screen flicker, and  it took much longer with the logo up to get to the initial login screen.  When I was in the DOS window as Admin I even tried running each of the  .efi files and it came up with a "not compatible with this version of  Windows...contact the software publisher..." Not exactly the error I  expected ....

When I navigated to the UEFI "Boot from File"  option, the DOS looking screen showed a single entry. It looked much  like the signed value found in the blue window on this page.
[http://www.rodsbooks.com/efi-bootloaders/secureboot.html](http://www.rodsbooks.com/efi-bootloaders/secureboot.html)

Even though Secure Boot is disabled, it appears some kind of signature must be in the database in order for an entry to appear.

---

### Post by roland-logikalsolutions on 2015-12-31
Okay. I have completely trashed my unit. It would boot nothing because the EFI area got messed up with all my copying and renaming of files. I tried a nuclear strike option with Elementary. Even after copying over the bootia32.efi file, this unit would NOT boot Elementary/Ubuntu from either the primary drive OR the micro SD card. The only thing which would boot is the thumb drive.

Many people call these things "fake computers" or "imitation computers" and now I see why. It is _completely_ hard wired for Windows. Really sad because once I rotated the screen with Elementary, it looked great, found the network, and generally performed well.

So, in the next couple of days I need to get up during the wee hours of the morning (satellite bonus time) and pull down Windows 8.1 32-bit base file, install it, find my blog post about drivers, etc for these devices, install them to get network, then let it upgrade to Windows 10 and jump through driver hoops again.

I will conduct no further Linux experiments on this device until someone else figures out how to defeat the Windows only boot restriction.

---

### Post by roland-logikalsolutions on 2016-01-10
Sundays seem to be a day of punishment for me. I tried installing the Debian multi-arch on this in nuclear strike mode with the extra SD card removed. It installs but cannot identify network card. It books to terminal log in as it appears to have no good video driver.

Giving Ubuntu 15.10 another try, but I don't expect it to work better. Elementary has a great looking interface, but being Ubuntu based has the same set of problems. Installs, but cannot boot.

---

### Post by Orion_S on 2016-02-03
Howdy all, finally got linux installed and booting on this after a few weeks worth of work. I got it installed like you did and also wiped out the windows bootloader. To get grub installed on this thing you have to install the 32 bit version of grub. Basically, mount your root filesystem to mnt in a live usb boot (mount /dev/mmcblk0p2 /mnt) then chroot into it. Then mount the booting partition when you install/update grub (mount /dev/mmcblk0p1 /boot). At this point I followed the commands here pretty much:
[http://unix.stackexchange.com/questions/206274/how-do-i-repair-grub2-not-booting-32-bit-efi-on-a-64-bit-machine](http://unix.stackexchange.com/questions/206274/how-do-i-repair-grub2-not-booting-32-bit-efi-on-a-64-bit-machine)

---

### Post by roland-logikalsolutions on 2016-04-30
Well, I have already prepped this frustrating hunk of *&(*&)( to give to someone else. The trail of tears might be getting shorter for the rest of you though. Got email notification about my Elementary bug this morning.

[https://bugs.launchpad.net/elementaryos/+bug/1519733](https://bugs.launchpad.net/elementaryos/+bug/1519733)

Release candidate one is supposed to solve these problems.

---

### Post by roland-logikalsolutions on 2016-05-26
In case anyone cares, there was a new entry on Launchpad today about this. Below is what showed up in email

=====
Just add this to the ISO root dir:
[http://pinguyos.com/files/ISO_Boot&EFI.zip](http://pinguyos.com/files/ISO_Boot&EFI.zip)

Then edit grub.cfg file with your info. This will allow the iso to boot on 32-bit systems.
The main thing that achieves this is the /EFI/BOOT/bootia32.efi file.

As for the packages in the pool for offline install you will need to
edit your builder script to include the packages shown here:
[http://pastebin.com/jBLtUV0U](http://pastebin.com/jBLtUV0U)

You will need different packages for 64-bit and 32-bit ISO's. That
snippet of code will automate it the process.

As mentioned in earlier posts on G+, if you want to use a startup.nsh
file so EFI only bios (as seen in tablets) work you need to create a
file ‘startup.nsh’ in /boot/efi and place the following string in:

64-Bit
Code:
fs0:\EFI\ubuntu\grubx64.efi


32-Bit
Code:
\EFI\custom\grubia32.efi

Its up to you how you want to do that but I do it by making a script
that edits /usr/share/ubiquity/apt-setup

I use something like this: [http://pastebin.com/AZ0MXe9G](http://pastebin.com/AZ0MXe9G)

This should be all the info you need to get 32-bit UEFI systems to boot
and install. As long as you include these packages in the 32-bit iso
(efibootmgr grub-common grub-efi grub-efi-ia32 grub-efi-ia32-bin grub-
pc-bin grub-pc grub2-common grub-gfxpayload-lists libefivar0 mokutil
secureboot-db). Offline install will work.
=====

---

### Post by bobdodds2 on 2016-07-30
I think we're in with very few changes to gui install("grubia32.efi", Roland and see how others use this. cmd prompt shutdown.exe /r /o, or during boot use Fn + F2 to get the F2 functionality during boot and disable Secureboot), but to learn more detail and pick up skill, some reading that may help:
[https://github.com/burzumishi/linux-baytrail-flexx10](https://github.com/burzumishi/linux-baytrail-flexx10)
[http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

---

### Post by bobdodds2 on 2016-07-30
Orion_S, I read your stackexchange link, and it seems that for ubuntu that path might be easier, what do you think, if we take something additonal from this about a debian install:
[https://github.com/burzumishi/linux-baytrail-flexx10](https://github.com/burzumishi/linux-baytrail-flexx10)
..I would consider going back and trying the btrfs compressed file system as in the stackexchange context, but Nextbook has 64GB to play with now in their 11.6 at Wally World. If Wally will give me a credit card, I'll put Ubuntu Touch in there:
[http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/](http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/)

---

### Post by bray908202 on 2016-09-22
Maybe someone here can help me because #ubunu in IRC could not 

Most of the time when I boot the nextbook 11 witg Ubuntu 16.04 it boots to a black screen but like 10% of the time it boots to the desktop I can remedy this problem by using nomodeset and then it boots every time

---

### Post by howefield on 2016-09-22
> **bray908202 said:**
> Most of the time when I boot the nextbook 11 witg Ubuntu 16.04 it boots to a black screen but like 10% of the time it boots to the desktop I can remedy this problem by using nomodeset and then it boots every time

What do you need help with, you seem sorted or do you need help with making the nomodeset a permanent change ?

---

### Post by bray908202 on 2016-09-22
> **howefield said:**
> What do you need help with, you seem sorted or do you need help with making the nomodeset a permanent change ?

I would like help booting without nomodeset 100% of the time since it already boots without it 10% of the time

---

