---
title: "Can't Get Into BIOS To Change The Boot Order........"
date: 2024-01-07
forum: Installation &amp; Upgrades
---

### Post by ebozzz on 2024-01-07
Hello all,

I acquired a Lenovo IdeaPad that I planned to install some flavor of Ubuntu on but unfortunately, I am unable to access that BIOS menu during the boot process. I've tried using F1, F2, F12 and those keys in conjunction with the fn key. Nothing works. All of the documentation indicates that it should be F2 for this model. The machine will not boot into Windows I get the following when attempting that task.....[ATTACH=CONFIG]293287[/ATTACH]

---

### Post by MAFoElffen on 2024-01-07
The hotkeys for BIOS for that computer is F2 or (Fn+F2).

If you boot from an Installer LiveUSB, you can use the UEFI setup option.

If you booted within Ubuntu, which from your screenshot, that is not probably going to happen (because it looks like you might have installed Windows after installing Windows, so may have blown out the boot order), but... from a terminal, 
```

sudo systemctl reboot --firmware-setup

```

From any Grub2 menu item > Press the <C> key to get into Grub Command line... 
```

fwsetup

```

If it boot Ubuntu, search on my User name and search the term "force grub2 menu show" to find one of my many posts on modifying your Grub2 menu to show. 

Once within the UEFI setup utility, remember to disable fastboot!!! <-- This is most likely why your keyboard is being ignored (no hotkeys being recognized) during the boot process.

---

### Post by tea for one on 2024-01-08
Do you have the Novo facility on your ideapad?
[https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad](https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad)

---

### Post by MAFoElffen on 2024-01-08
> **tea for one said:**
> Do you have the Novo facility on your ideapad?
[https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad](https://support.lenovo.com/gb/en/solutions/ht062552-introduction-to-novo-button-ideapad)

On my Lenovo ThinkPad they call it the "ThinkVantage" Button. Blue button next to the power button.

---

### Post by yancek on 2024-01-08
The image you posted shows a failed attempt to boot to install windows due to either an unexpected error or unexpected restart.  Have you considered the possibility of posting about this problem at a windows site?  Are you trying to install from a windows usb, a DVD?  Have you tried to use it to boot with another machine to  eliminate a bad write to the device as a possibility?  Do you have any OS on that machine?  Have you been able to access the BIOS at any time since you acquired the computer?

---

### Post by ebozzz on 2024-01-10
I just acquired it and no, since the acquisition I’ve never been able to access BIOS. I’m going to use a USB drive to complete the installation and it has already been successfully flashed.

---

### Post by ebozzz on 2024-01-10
No.

---

### Post by ebozzz on 2024-01-10
This machine has never had Ubuntu installed so what I described in my original post is all that I get. Once it makes it to that Lenovo banner it basically attempts to reboot several times before the Windows related message appears.

---

### Post by MAFoElffen on 2024-01-10
I was a Lenovo, HP an Dell Onsite Warranty Technician...

This is where you should refer to your IdeaPad Owner's Manual. Please refer to the attached screenshot from your Owner's Manual to locate your Novo Button...

On the left side, between the ventilation grill and your power button, if you look closely, there is a small button. That is your Novo Button...
> 
When the computer is off, press this button to start the Lenovo OneKey
Recovery System or the BIOS setup utility, or to enter the boot menu.


---

### Post by yancek on 2024-01-11
In post 6 above, you say that the windows usb has been 'successfully flashed'.  Does that mean you have now resolved the problem and have been able to install windows on this Lenovo or does that mean you have test booted the usb on another computer and do not have this problem?  As suggested before, have you tried posting about this problem with your install of windows on a windows forum?  Have you gone to the Lenovo site to see if you can get more detailed information?

---

### Post by ebozzz on 2024-01-13
The problem still exists on the laptop in question. It’s not a problem with the USB drive. The problem is that I’m unable to change the boot order on the laptop so that it will boot from the USB drive…

---

### Post by ebozzz on 2024-01-13
This machine doesn’t have a “Novo button”.

---

### Post by ebozzz on 2024-01-13
Also, I’ve never installed anything on this laptop. It came to me as is….

---

### Post by yancek on 2024-01-14
Have you read the information at the link below at the Lenovo site on accessing the BIOS?  The ideapad has been around for a long time so how old/new is this machine?  Did you buy it new from Lenovo or buy it used from someone else?

[https://pcsupport.lenovo.com/cr/en/products/LAPTOPS-AND-NETBOOKS/IDEAPAD-S-SERIES-NETBOOKS/S145-14IWL/solutions/HT500216?linkTrack=diagTopSolution%3ARecommended%20way%20to%20enter%20BIOS%20-%20ideapad](https://pcsupport.lenovo.com/cr/en/products/LAPTOPS-AND-NETBOOKS/IDEAPAD-S-SERIES-NETBOOKS/S145-14IWL/solutions/HT500216?linkTrack=diagTopSolution%3ARecommended%20way%20to%20enter%20BIOS%20-%20ideapad)

---

### Post by jeremy31 on 2024-01-14
Remove the internal drive and you can likely get it to boot a USB

---

### Post by MAFoElffen on 2024-01-14
If you are going to crack the case to remove a drive, then another way is to remove to remove the main battery and then remove the CMOS battery, While both are out, press the power button for 1 minute. Then put it back together.
RE: [https://www.youtube.com/watch?v=Rv-x4sW27VU](https://www.youtube.com/watch?v=Rv-x4sW27VU)

On the next boot, it will get a CMOS error on time/date, and ask you to press a button to continue getting into the BIOS Settings to reset it.

---

### Post by ebozzz on 2024-01-15
In my original message I indicated that ALL of the documentation stated that the F2 key was what needed to be used to access the BIOS during the boot process. I also mentioned what other keys I’ve tried and also that I’ve tried using them in conjunction with the FN key…

---

### Post by ebozzz on 2024-01-15
That’s the direction that I’ve determined is my next step. Using the keys during the boot process just isn’t working. Thanks!

---

### Post by ebozzz on 2024-01-15
Thanks for that information! Let me watch that video and make a decision….

---

### Post by him610 on 2024-01-15
FWIW, Be sure to press the function key(s) as soon as you turn the power on and keep pressing it until BIOS screen appears.

---

### Post by MAFoElffen on 2024-01-15
There is another hot-key combination that I found buried in the Lenovo Doc's. 

With the IdeaPad turned off, simultaneously press and hold down the <Fn><R> and the <N> keys... Then press the Power Button to power-on. As it powers on, release all those keys and then press the <F2> to get into the Advanced BIOS Settings Menu.

Worth a try right?

---

