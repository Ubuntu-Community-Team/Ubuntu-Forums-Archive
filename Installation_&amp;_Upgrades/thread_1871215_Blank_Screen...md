---
title: "Blank Screen.."
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by GoFishy on 2011-10-28
So ever release starting with 10.04 wont install for me.. I have tried Live CD and USB. If i select to just try ubuntu i get a black screen and nothing every happens. If i choose to install it i go the purple wallpaper with the top panel (with wifi etc) on it but install wizard never loads.

I am currently running Ubuntu 10.04. I upgraded from 9.10 it is the only release that will actually install from scratch.

Whats the problem?

Thanks

---

### Post by MAFoElffen on 2011-10-28
> **GoFishy said:**
> So ever release starting with 10.04 wont install for me.. I have tried Live CD and USB. If i select to just try ubuntu i get a black screen and nothing every happens. If i choose to install it i go the purple wallpaper with the top panel (with wifi etc) on it but install wizard never loads.

I am currently running Ubuntu 10.04. I upgraded from 9.10 it is the only release that will actually install from scratch.

Whats the problem?

Thanks
It's a KMS thing = How they handle the graphics is progressively more picky as they try to ask for from it for desktop effects and such...

Please post the results of
```

lspci -vnn | grep VGA

```

---

### Post by GoFishy on 2011-10-29
04:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GX2] [10de:0604] (rev a2)


Let me know if you need anymore info.

Thanks!

---

### Post by GoFishy on 2011-11-01
Does anyone else have any ideas on this?

Thanks

---

### Post by MAFoElffen on 2011-11-07
> **GoFishy said:**
> 04:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GX2] [10de:0604] (rev a2)


Let me know if you need anymore info.

Thanks!
While trying to boot, hold down or press repeatedly the <shift> key > Press the <e> key to enter an edit mode > <down arrow> until you get to the line that starts with "linux" > <right arrow> until you get to the text that says "quiet splash" and replace that text with "nomodeset" > Press <cntrl><x> to boot.

It should boot in a VESA mode. Not fantastic graphics, but good enough to get your graphics installed...

Once it boots to the desktop > Go to System menu > Administration > Hardware drivers >> Select the Nvidia-current driver. > Select Install. > Reboot and test.

//---- Do this only if the above did not work ----//
If for some reason, that does not work-- it may have an older driver installed already, that may be conflicting with the new.  In that case, get back to an edit mode in your grub menu (instructions above) > Go to the same linux boot line > Replace "quiet splash" with "--verbose text" > Press <cntrl><x> to boot.

It will boot in a TTY Text mode. Pay attention to the boot massages for any errors.  When it is through, it will dump you down to a command prompt. Log in, then:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo nvidia-installer --uninstall 
sudo apt-get remove nvidia-* 
sudo apt-get install 'uname -r' 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig
sudo apt-get upgrade
sudo reboot

```The second or third command my return a file not found, which is what we want at that point anyways, so just go on with the commands.  What that does is to purge the old drivers and ensure there is a correct kernel header file before the later commands which install the correct driver for you.

Tell me how it goes.  If I don't answer soon today, PM me again.  I'll be working on 2 Solaris Servers today... They only have Text based browsers. I'll be back active again late this afternoon.

---

### Post by GoFishy on 2011-11-08
I am currently at work and will attempt this when i get home. Just trying to clarify something. Right now i can get into 10.04 so can i just do this all in there? I only get the blank screens when trying to install a new release.

I have read something about nomodest before and think i tried it.

Will get more info later. Thanks

---

### Post by MAFoElffen on 2011-11-08
> **GoFishy said:**
> I am currently at work and will attempt this when i get home. Just trying to clarify something. Right now i can get into 10.04 so can i just do this all in there? I only get the blank screens when trying to install a new release.

I have read something about nomodest before and think i tried it.

Will get more info later. Thanks
Yes you could by opening a terminal session and typing the commands... But since you are "running" it would be much easier to go System > Administration > Hardware Drivers >  Ensure there are no drivers selected or installed. If there is, highlight them and press the remove button. Then, select the Nvidia Current Driver in the list box > Press the Install/activate button.

That should/would update your graphics driver so that it should be fine after a distribution upgrade...

---

### Post by GoFishy on 2011-11-08
Okay so i brought up Hardware Drivers.

It says i currently am using "NVIDIA accelerated graphics driver (version current) [Recommended]"

---

### Post by MAFoElffen on 2011-11-08
> **GoFishy said:**
> Okay so i brought up Hardware Drivers.

It says i currently am using "NVIDIA accelerated graphics driver (version current) [Recommended]"
And are you fixed now?

---

### Post by GoFishy on 2011-11-08
No its always been like that. Works fine right now

But everytime i try to install i do live cd i get blank screen.. or if i try to install i get wallpaper but no wizard

---

### Post by MAFoElffen on 2011-11-08
> **GoFishy said:**
> No its always been like that. Works fine right now

But everytime i try to install i do live cd i get blank screen.. or if i try to install i get wallpaper but no wizard
If you're trying to run a LiveCD, At the first screen, which will be black with a person/keyboard icon at the bottom. > Press escape > That will get you to a low res language selection screen > Press escape > That will get you to the advanced installation menu > Press F6 > That will drop down a boot options menu. > Arrow down to where it says "nomodeset" > Press the spacebar to select. > Press escpe to return to the Advanced Install Menu > select "Try without Installing"  It will bot with your video card....

From the way you had this worded, I thought you were having problems with exisiting... Why are you "installing" new instead of upgrading your existing?

---

### Post by GoFishy on 2011-11-09
Well I'm on 10.04 so i would have to upgrade twice to get there. I play around a lot with stuff i have no clue about so wanted a fresh install to get rid of junk stuff laying around. Also i got a new hard drive i want to install it on.

But yeah when i "Try without Installing" i get a black screen. When i hit "Install Ubuntu" i get the Ubuntu wallpaper and top panel (with wifi and sound stuff) but the wizard never shows up. Its not frozen thought i can move mouse around.

Once again I'm responding from work and will try your suggestions when i get home. Thanks!

---

### Post by MAFoElffen on 2011-11-09
> **GoFishy said:**
> Well [COLOR=Red]I'm on 10.04 so i would have to upgrade twice to get there.[/COLOR] I play around a lot with stuff i have no clue about so wanted a fresh install to get rid of junk stuff laying around. Also i got a new hard drive i want to install it on.

But yeah when i "Try without Installing" i get a black screen. When i hit "Install Ubuntu" i get the Ubuntu wallpaper and top panel (with wifi and sound stuff) but the wizard never shows up. Its not frozen thought i can move mouse around.

Once again I'm responding from work and will try your suggestions when i get home. Thanks!
No you wouldn't.  A Distribution Upgrade "upgrades" to whatever is the current version.  From 10.04 would skip from that version, directly to 11.10. You would have to manually do a lot to work to do else-wise.

But a clean start is always good.

---

### Post by GoFishy on 2011-11-11
> **MAFoElffen said:**
> If you're trying to run a LiveCD, At the first screen, which will be black with a person/keyboard icon at the bottom. > Press escape > That will get you to a low res language selection screen > Press escape > That will get you to the advanced installation menu > Press F6 > That will drop down a boot options menu. > Arrow down to where it says "nomodeset" > Press the spacebar to select. > Press escpe to return to the Advanced Install Menu > select "Try without Installing"  It will bot with your video card....

From the way you had this worded, I thought you were having problems with exisiting... Why are you "installing" new instead of upgrading your existing?

I couldnt get any of this to boot. I used a live usb and when i booted in i got a black and white install menu screen with the "try without installing" etc..

If i hit F6 nothing happened it just seemed to refresh. If i hit Esc it took me a terminal looking screen with "boot:"

---

### Post by GoFishy on 2011-11-11
So turns out if i use the live CD like i told you i was everything works.

Thank you so much for those steps, been pushing off upgrading cause of this problem. Its installing right now so I'm hoping everything turns out okay!

---

