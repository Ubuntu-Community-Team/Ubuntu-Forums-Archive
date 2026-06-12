---
title: "Complete newbie to Linux"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by terrypink on 2010-08-24
Hi everyone,

I was wondering, can you install Ubuntu on a Windows XP computer?  I tried to install the Wubi program, but I never got the boot command prompt, it would go straight to Windows... and I tried to find the boot.ini file, but I couldn't figure out where it is...?

---

### Post by JamButty on 2010-08-24
Take this with a grain of salt as one noob advising another.....
Wubi seems an unnecessary step. If you can download a file and burn it to CD, it is dead simple to install, or try without installing, Ubuntu Lucid Lynx.

The install with dual boot from CD (I did it 1 month ago) was very simple - only caveat; I got advice to make the partition myself with GPARTED and point the installation there. This was really not necessary and caused problems. If you let the installation CD create the partitions itself, it is all transparent. As long as you have 40+GB to spare, you will be up and running quickly.

---

### Post by Frogs Hair on 2010-08-24
> **terrypink said:**
> Hi everyone,

I was wondering, can you install Ubuntu on a Windows XP computer?  I tried to install the Wubi program, but I never got the boot command prompt, it would go straight to Windows... and I tried to find the boot.ini file, but I couldn't figure out where it is...?

If Wubi installed Ubuntu properly then Ubuntu should be listed under Windows in the boot loader . If you don't select it by pressing the down arrow and hitting enter , Windows will load automatically after a pause.

If Ubuntu is not listed in the boot loader then installation failed. I suggest down loading the Ubuntu iso and making a disk.

---

### Post by rollin on 2010-08-24
> **terrypink said:**
> Hi everyone,

I was wondering, can you install Ubuntu on a Windows XP computer?  I tried to install the Wubi program, but I never got the boot command prompt, it would go straight to Windows... and I tried to find the boot.ini file, but I couldn't figure out where it is...?

Welcome to the forum! 

To install Wubi should be really easy with a live Ubuntu CD. All you need to do is burn the ISO image you downloaded of Ubuntu, to a CD, Img Burn is a good free software to do this.
Next step when you are booted into Windows, insert the Ubuntu CD. You should see a box appear with the option "Install Inside Windows".
You'll need to be connected to the internet for the setup to run correctly with pyrun.exe which happens automatically.
You'll be prompted to remove the CD and reboot. Do this and you'll see GRUB at boot, choose Ubuntu and the installation will proceed.

Try these steps and post back with any errors you are getting. All the best ;)

---

### Post by terrypink on 2010-08-25
> **rollin said:**
> Welcome to the forum! 

To install Wubi should be really easy with a live Ubuntu CD. All you need to do is burn the ISO image you downloaded of Ubuntu, to a CD, Img Burn is a good free software to do this.
Next step when you are booted into Windows, insert the Ubuntu CD. You should see a box appear with the option "Install Inside Windows".
You'll need to be connected to the internet for the setup to run correctly with pyrun.exe which happens automatically.
You'll be prompted to remove the CD and reboot. Do this and you'll see GRUB at boot, choose Ubuntu and the installation will proceed.

Try these steps and post back with any errors you are getting. All the best ;)

I've never installed an image to a CD before.  I downloaded the ImgBurn program.  But I can't find the Wubi ISO image I'm supposed to burn from... where do I look... what is the file called?

Thank you!

---

### Post by rollin on 2010-08-25
> **terrypink said:**
> I've never installed an image to a CD before.  I downloaded the ImgBurn program.  But I can't find the Wubi ISO image I'm supposed to burn from... where do I look... what is the file called?

Thank you!

No problem! When I first started using Linux I did not have experience of using ISOs either so your far from alone in this situation. 

I'll try and think up a mini-tutorial for your Wubi install process to get you up and running so here goes:


[LIST=1]
[*]Go here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) choose to download either a 32bit or 64 bit version.
[*]Once you have this downloaded you'll see that this is an *.iso file.
[*]Great I have my Ubuntu ISO now what?
[*]You'll need to burn the ISO with Img Burn to a CD, for info on how to do this head here: [http://neosmart.net/wiki/display/G/Burning+ISO+Images+with+ImgBurn](http://neosmart.net/wiki/display/G/Burning+ISO+Images+with+ImgBurn)
[*]Once the "burn" has finished the simplest option will be to eject the CD, close Img Burn and wait a moment. Make sure you are connected to the Internet as you would normally in Windows and then re-insert the CD. Wubi is included in the Ubuntu ISO so everything from here should be easy.
[*]Wait a moment and you should now see an image appear on the screen you'll need to select the option " Install inside Windows" see  this screenie: [http://blogs.tech-recipes.com/shamanstears/files/2008/11/ubuntu_windows_dual_1.png](http://blogs.tech-recipes.com/shamanstears/files/2008/11/ubuntu_windows_dual_1.png)
[*]Set the password (your username may be automatically filled as your Windows login name). Choose the installation size you want, under Wubi I think you get a max install of 30GB. Basically follow the installation instructions and eject the CD when prompted.
[*]Reboot the system without the CD and choose Ubuntu from the menu. Allow the installation to complete and you will be prompted with a login screen.
[*]Type in the password you gave in the installation steps and voila you will be loaded into your " Wubi install" of Ubuntu. You can now experiment installing software and customizing your installation!
[*]Once your finished with your session you can simply exit. When you want to load back into Ubuntu or Windows choose the option name on the screen at boot (Grub Menu).
[/LIST]

If you decide Ubuntu is not for you please post why in the Testimonials bit on the forum (feedback is good) and remove it by booting into Windows and remove it via Add Remove as you would any other software.

I hope these steps clarify things as best as I can think of! Any problem just keep postin' ;)

---

### Post by terrypink on 2010-08-26
Augh!  There was an error with something during the image burn to CD!  

Is there any other way to fix this without burning to CD?

---

### Post by bcbc on 2010-08-26
> **terrypink said:**
> Augh!  There was an error with something during the image burn to CD!  

Is there any other way to fix this without burning to CD?

I use infrarecorder to burn my CDs (and select the slowest possible speed).

If you want to install wubi, you don't need to burn a cd. Just place the downloaded .iso and the wubi.exe program (get it [here]("http://wubi-installer.org/")) in the same folder, and run it. Wubi.exe will check the .iso (validate the md5 hash) etc. and take care of the rest.

You can also create a bootable USB. (The instructions are provided where you downloaded the image): [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

It's definitely better to have a bootable CD/USB and try it before installing. They're also good to recover from problems (and having a windows repair CD/DVD is a good idea too). Since you are playing with a new OS, it's essential to back up important data.

---

### Post by terrypink on 2010-08-26
Ok.  I successfully got the CD to work.  And I installed the CD version as you guys suggested.

But... it still doesn't work!  It still goes straight to the Windows OS, it never shows me a black screen where I can pick Ubuntu from the menu options...

Please help?!

---

### Post by bcbc on 2010-08-26
> **terrypink said:**
> Ok.  I successfully got the CD to work.  And I installed the CD version as you guys suggested.

But... it still doesn't work!  It still goes straight to the Windows OS, it never shows me a black screen where I can pick Ubuntu from the menu options...

Please help?!

Most computers are set to boot from the internal drive. You need to override this to allow it to boot from CD. You can either do it in the bios, or look for a boot options key to select the boot device.

Then when the CD boots, select "Try without installing". It runs slow from a CD but it's a good way to make sure your hardware is compatible.

---

### Post by rollin on 2010-08-26
> **terrypink said:**
> Ok.  I successfully got the CD to work.  And I installed the CD version as you guys suggested.

But... it still doesn't work!  It still goes straight to the Windows OS, it never shows me a black screen where I can pick Ubuntu from the menu options...

Please help?!

OK just to clarify you're at  "Step 8" on mini-tutorial thing I wrote earlier right? You've rebooted and there is no option to choose Ubuntu on the menu and allow the Wubi installation to complete etc... 

If the above is correct it sounds like the installation is not correctly installing itself in steps 1 - 7. We need to get a better idea of your hardware and the Windows version you are running I think.

---

### Post by terrypink on 2010-08-26
> **rollin said:**
> OK just to clarify you're at  "Step 8" on mini-tutorial thing I wrote earlier right? You've rebooted and there is no option to choose Ubuntu on the menu and allow the Wubi installation to complete etc... 

If the above is correct it sounds like the installation is not correctly installing itself in steps 1 - 7. We need to get a better idea of your hardware and the Windows version you are running I think.


Yes, I'm on Step 8.

I'm using Windows XP with a 32 bit.  What other info do you need?

---

### Post by bcbc on 2010-08-26
Post the contents of c:\boot.ini and also the contents of %temp%\wubi-10.04.1-rev190.log (assuming that's the correct version, otherwise whatever wubi-xxxx.log you have in the %temp% directory)

Between [[SIZE="1"] [/SIZE]CODE][/CODE] tags.

---

### Post by terrypink on 2010-08-27
> **bcbc said:**
> Post the contents of c:\boot.ini and also the contents of %temp%\wubi-10.04.1-rev190.log (assuming that's the correct version, otherwise whatever wubi-xxxx.log you have in the %temp% directory)

Between ```

``` tags.


That's one of my problems!  I can't for the life of me find the boot.ini file?!  I've tried searching using the "Search All Files" option, but I get like 7 boot.ini files?  How do I find the boot.ini file??

---

### Post by rollin on 2010-08-27
> **terrypink said:**
> That's one of my problems!  I can't for the life of me find the boot.ini file?!  I've tried searching using the "Search All Files" option, but I get like 7 boot.ini files?  How do I find the boot.ini file??

I think I get the idea that bcbc has in that the boot.ini does have a setting for timeout value which could be why you are switching straight into XP. To learn about accessing boot.ini you can have a look here; [http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

I'm not so good with the Windows type stuff so stick with what bcbc is saying as he seems to know what to do.

---

### Post by Ceedub2 on 2010-08-27
Boot it a couple times and then see. It may pick it up after another reboot. 

Hope this helps you.

---

### Post by bcbc on 2010-08-27
> **terrypink said:**
> That's one of my problems!  I can't for the life of me find the boot.ini file?!  I've tried searching using the "Search All Files" option, but I get like 7 boot.ini files?  How do I find the boot.ini file??
It's a hidden file. Go to a command prompt (Windows key, Run, enter "cmd" (without quotes), and "type c:\boot.ini"

I normally have all hidden files displayed by default (as well as extensions) but forgot some people don't. Or else maybe the instructions in that link *rollin* provided will allow you to get it.

I think you can also get it by Windows Key, Run, "msconfig", and then it will be in one of the tabs.

You can get the wubi log file, by entering "%temp%" in the windows explorer address bar (without quotes). And then looking for something called "wubi......log". Edit: I suppose it might be hidden too :)

---

