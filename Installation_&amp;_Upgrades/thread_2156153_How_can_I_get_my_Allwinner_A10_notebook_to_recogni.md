---
title: "How can I get my Allwinner A10 notebook to recognize Lubuntu SD card at boot?"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by MediaBanger on 2013-06-20
So I have [this 13-inch Android 4.0-powered notebook]("http://avatarpctv.com/android/78-avatar-13-3-titan-avra-138a1"). It has an Allwinner A10 Cortex A8 SOC that's a bit slow for general web-browsing, but does pretty awesome at video playback (even 720p and 1080p HD so long as the internet connection is fast enough), and it can run several useful Android apps that were probably intended more for phones or tablets with auxiliary keyboards.

Anyway, just for fun (and to see if the browsing experience improves, partially) I'm wanting to get Lubuntu 12.04 running on it. I've [tried this version at Miniand]("https://www.miniand.com/forums/forums/2/topics/1") and [this version from Rikomagic]("http://rikomagic.co.uk/forum/viewtopic.php?f=2&t=90"), gone through the whole install process to dd the image to an 8GB SD card. I realize both of the above are directed at the MK802 "PC-on-a-stick" but [the specs at this page]("https://www.miniand.com/products/MK802%20Android%20Mini%20PC") seem to line up with the info from the specs page for my notebook (see link in the first paragraph above.)

After dd'ing to the SD card using my iMac's Terminal, I insert the SD card into my laptop's card slot and power up, and it doesn't even try to load anything from the card. It goes straight into the Android 4.0 OS. I thought Allwinner A10 SOCs supposedly tried to boot from SD first? If that's the case, clearly I'm doing something wrong, or there's a chance the above versions of Lubuntu won't run on my laptop A10 SOC but will, for some reason, run on a PC-on-a-stick A10 SOC. You'd think I'd at least get to a corrupted-looking login screen or an error message or something, but no.

Help?

---

### Post by Supercomputerpower on 2013-06-20
Linux 2.6.36 (Ubuntu 10.04) is only running on the Allwinner A10 Cortex A8 SOC

---

### Post by MediaBanger on 2013-06-20
> **Supercomputerpower said:**
> Linux 2.6.36 (Ubuntu 10.04) is only running on the Allwinner A10 Cortex A8 SOC

If you're meaning only Ubuntu 10.04 can run on the A10 Cortex A8, Miniand's thread and Rikomagic's thread linked in my OP disagree with you. Both are running 12.04. In Miniand's case, they've got Ubuntu 12.04, Lubuntu 12.04, Xubuntu 12.04, and Linaro 12.06 running on the SOC. 

But again, they're using the MK802 PC-on-a-stick. I'm trying to do this on a laptop, so there may be some differences I'm not aware of between the MK802's A10 SOC and mine (I don't see it in the specification links I shared above, but maybe I'm missing something). Regardless, I was thinking I could at least get the laptop to boot from SD, even if something in the display config was wrong or what-have-you, but I've had no such luck.

---

### Post by Supercomputerpower on 2013-06-20
system on a stick i thought, oke then by starting up your system you must go into the bios by hitting Del or F12 or what the system tells you. then go to boot sequence and look if there a possible choice as 1st boot device sd. change noting else than save and quit now it starts from sd otherwise try usb stick hope it helps

---

### Post by MediaBanger on 2013-06-20
> **Supercomputerpower said:**
> system on a stick i thought, oke then by starting up your system you must go into the bios by hitting Del or F12 or what the system tells you.

I'm not able to do this. Remember, I'm dealing with an Allwinner A10 SOC, not x86 hardware here. And believe me, just because I'm used to that method of operation, I have tried different key combinations while starting the computer. No luck.

EDIT: Also, the company that makes my laptop says it should boot directly from SD with no modification/special button-presses/whatever. That's the method they use in re-flashing the Android OS, as you can see from [this help documentation link]("http://www.avatargamingpc.com/download/AVA8-133-01/Readme.pdf").

---

### Post by Supercomputerpower on 2013-06-20
oke i will try to help let me study for a moment i am not familliar with the device checking in progress.......

---

### Post by Supercomputerpower on 2013-06-20
oke he boot automatically from the 1 gb hdd with android installed on it

---

### Post by Supercomputerpower on 2013-06-20
i think he must be restored to original settings now he thinks he is an android

---

### Post by Supercomputerpower on 2013-06-20
[http://avatargamingpc.com/support/818077-is-there-a-way-to-install-Linux-on-the-AVRA-138A1](http://avatargamingpc.com/support/818077-is-there-a-way-to-install-Linux-on-the-AVRA-138A1)

---

### Post by Supercomputerpower on 2013-06-20
i think this will help you must Flash the Firmware titan AVRA-138A1
[http://avatargamingpc.com/support/101285-Titan](http://avatargamingpc.com/support/101285-Titan)

---

### Post by MediaBanger on 2013-06-20
> **Supercomputerpower said:**
> [http://avatargamingpc.com/support/818077-is-there-a-way-to-install-Linux-on-the-AVRA-138A1](http://avatargamingpc.com/support/818077-is-there-a-way-to-install-Linux-on-the-AVRA-138A1)

That link further confirms what I thought: This laptop should be booting straight to SD if the image is burned correctly to an SD card.

So either I did something incorrectly (been through this three times now, following the directions exactly), or there's something in the Lubuntu images on Miniand and Rikomagic that just isn't cooperating with the laptop's hardware. I'll keep working at it, but I'm open to anyone else who can maybe point out where I might be doing something wrong.

EDIT: I'm a moron. The card was in the reader slot upside-down. BUT after I turned off the computer and flipped it, all I got was a black screen. The wifi light came on and illuminated solid green instead of blinking like it normally does, so SOMETHING is alive in there, but I can't see anything. Is there a display difference between the MK802 and my laptop or something? Both MALI GPUs.

---

### Post by MediaBanger on 2013-06-21
And I'm an even bigger moron. I'm posting from Lubuntu on my notebook now.

The thing that never occurred to me is the MK802 is HDMI-only. There is no built-in display like the one on my notebook computer. Plugged my notebook's mini HDMI into the port on the back of our living room TV, and here we are running Lubuntu Netbook 12.04. I tried loading the regular Lubuntu, but it hung up on me for reasons unknown after I hit the "Log In" button. Haven't tried the other two options, which are Openbox-derived.

So with that said, all I need to be able to do to make this functional is to find out how to get it to recognize my built-in display. After that, we can work on why the regular, full-featured Lubuntu won't seem to load.

Also worth a note at this point: As I suspected, general internet browsing is a touch faster in Lubuntu than Android 4.0, even though I've been using Opera Mini, which is the fastest browser I've yet found for Android.

---

### Post by Supercomputerpower on 2013-06-21
problem solved have a nice day

---

### Post by MediaBanger on 2013-06-21
> **Supercomputerpower said:**
> problem solved have a nice day

Yes! Thanks for your help-- my own ignorance/stupidity/Linux noobism knows no bounds.

Note for anyone else trying to run a MK802 Linux distro on one of the many cheap notebook computers running Android on an Allwinner A10 Cortex A8 SOC: You need to be able to connect the computer to an external monitor via HDMI cable when you boot a Linux distro from an SD card. You'll have to use the external display long enough to figure out how to modify the xorg.conf file to use the built-in display. Working on that right now.

---

