---
title: "LiveCD not working properly"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Fireguy15 on 2009-12-12
Ok the title is a little misleading. I boot up to the LiveCD and get to the options of "trying without making changes", "installing" etc.

I am able to go through all the "F" keys and choose language etc but whenI got to "try without making changes" and press enter nothing happens?

This is the first time I am trying ubuntu, or for that matter anything other than windows.

I am not able to dl the file to burn a new disc (am at work on a sprint broadband card) and I am hoping maybe something simple might be the issue.

Thanks in advance!

This is the 64bit version BTW

---

### Post by darkod on 2009-12-12
> **Fireguy15 said:**
> Ok the title is a little misleading. I boot up to the LiveCD and get to the options of "trying without making changes", "installing" etc.

I am able to go through all the "F" keys and choose language etc but whenI got to "try without making changes" and press enter nothing happens?

This is the first time I am trying ubuntu, or for that matter anything other than windows.

I am not able to dl the file to burn a new disc (am at work on a sprint broadband card) and I am hoping maybe something simple might be the issue.

Thanks in advance!

This is the 64bit version BTW

Unfortunately it sounds like either corrupted image during download, or badly burnt CD. Another option might be dirty optical drive, not working properly.
You can try the Install Ubuntu option, you can click Quit immediately and after that it loads the desktop from the CD, same as if you selected Try Ubuntu. That might work.

---

### Post by Fireguy15 on 2009-12-12
Thanks, I will give that a try!

---

### Post by Fireguy15 on 2009-12-12
Okay, I tried it but clicking on any option gets the same result, drive spins up and nothing happens.

Is there a certain length of time it should take or should it immediately change over to another screen?

The only option that does anything when I click on it is to boot from hdd.

If nobody can think of anything else i will just try to re-dl it and burn a new disc tomorrow.

---

### Post by darkod on 2009-12-12
> **Fireguy15 said:**
> Okay, I tried it but clicking on any option gets the same result, drive spins up and nothing happens.

Is there a certain length of time it should take or should it immediately change over to another screen?

The only option that does anything when I click on it is to boot from hdd.

If nobody can think of anything else i will just try to re-dl it and burn a new disc tomorrow.

No, it definitely won't be immediately because it's starting to load the OS, especially the Try Ubuntu option, from the CD. Leave it alone for a while, but even on slow computers it shouldn't take more than 5-10min.

---

### Post by Fireguy15 on 2009-12-12
Ok- I will let it sit. I thought maybe it would pop into a new screen letting you know it was executing the request.

I will come back here afterwards to post the results (and clear this thread).

Thanks again!

---

### Post by michy99 on 2009-12-12
Did you run the option to check the CD for errors?

---

### Post by Fireguy15 on 2009-12-12
I tried using the "try without making changes" and waited 15 minutes - Nothing
I tried using the "Install Ubuntu" and waited 15 minutes - Nothing
I tried using the "Check Disc for Errors" - Nothing
I tried using the "Boot from HDD" - Booted up in Vista

Now when I say Nothing, I mean the disc spins up and then after a short period it stops and nothing else happens.

---

### Post by darkod on 2009-12-12
> **Fireguy15 said:**
> I tried using the "try without making changes" and waited 15 minutes - Nothing
I tried using the "Install Ubuntu" and waited 15 minutes - Nothing
I tried using the "Check Disc for Errors" - Nothing
I tried using the "Boot from HDD" - Booted up in Vista

Now when I say Nothing, I mean the disc spins up and then after a short period it stops and nothing else happens.

Is the computer/laptop low spec and older?
One alternative is alternate install cd, but the installer is text based, not GUI, so it's up to you if you want to try installing like that. And there is no Live option, you can't try, just install. The system will still be with desktop GUI, just the installer is text based.

---

### Post by Fireguy15 on 2009-12-12
HP Pavilion DV7 Notebook
AMD Turion X2 Dual-Core Mobile RM-70, 2GHz
4G RAM
64 bit 

I think I will hold off on the install, I really wanted to check out how it works and looks first. I will have an older laptop in my hands by the end of the month that I will have no 2nd thoughts about installing this on. Might have to wait till then if my 2nd attempt at burning the iso to disk doesn't do any better.

Thanks for the help!

---

### Post by darkod on 2009-12-12
> **Fireguy15 said:**
> HP Pavilion DV7 Notebook
AMD Turion X2 Dual-Core Mobile RM-70, 2GHz
4G RAM
64 bit 

I think I will hold off on the install, I really wanted to check out how it works and looks first. I will have an older laptop in my hands by the end of the month that I will have no 2nd thoughts about installing this on. Might have to wait till then if my 2nd attempt at burning the iso to disk doesn't do any better.

Thanks for the help!

Yes, sounds like a good plan. Another option you might try is creating LiveUSB instead of LiveCD. Creating a usb stick instead of cd, saves a cd also. :)
This sounds like a newer laptop and it should be able to boot from usb.

---

### Post by Fireguy15 on 2009-12-12
Will give the usb a try- have to see what I am able to get done over this aircard and will check out the bios to make sure the usb is an option.

---

### Post by darkod on 2009-12-12
> **Fireguy15 said:**
> Will give the usb a try- have to see what I am able to get done over this aircard and will check out the bios to make sure the usb is an option.

As a first try you can use the same ISO image if you have it on the laptop. It's easiest to use program called unetbootin in windows to create the usb. It's free, google it for download.
After you open it you will need to select Image option (I think) and point it to the ISO. In the bottom select the letter of the stick. After it's done ignore the call to reboot, just close the program.
To get rid of the unetbootin menu and enable the ubuntu menu, open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the isolinux folder find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

It will enable the main ubuntu menu at boot. You can use the Try Ubuntu.

PS. The option in BIOS might be called USB HDD. Don't be confused because it says hdd and you're using a stick. On both my netbook and desktop in BIOS it says USB HDD and it works booting a usb stick.

---

### Post by Fireguy15 on 2009-12-12
I have the original file on my desktop at home. I was thinking about pulling the image off the disk to use but figured if it was corrupted somehow, I would end up in the same position. I decided to d/l the torrent and try it with a fresh copy and using USBInstaller v0.2 for Ubuntu (from the help pages). 

If I still have problems I will go forward with your above instructions.

If I still have problems I will wait until I have the old laptop freed up to play with.

Thanks for all the help!

---

### Post by Fireguy15 on 2009-12-12
I got the file dl'd and iso onto the USB stick, took me a bit to find the correct entry method to my bios but moved the USB HDD up before the HDD and everything flowed VERY smoothly!

Then I used the blackberry to do some research which i gave up on, and found my way in to configure my Sprint Mobile broadband Acess and that is how I am posting this now using Firefox on Ubuntu!

Thanks for all the suggestions and knowledge you have imparted upon this dumb old fireman today!

---

### Post by darkod on 2009-12-12
No problem. Glad you got it sorted.

---

