---
title: "Default Ubuntu partition installation overwrites Windows7 ?"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by krishnamurthig on 2011-02-02
Hi Friends,

Sorry my previous question wasn't that informative so adding more. I had  windows partition and free partition for Linux installation. I got  installed windows7 and it installed fine, When I tried installing  Ubuntu, I remember selected default options. 

I gave me default option as it clearly said "1. If you have another  operating system (e.g. Windows XP) and you want a dual boot system,  select the first option: "Install them side by side, choosing between  them at each startup."  I thought it would keep Windows as it is and I  hit proceeded for installation.

first option: "Install them side by side, choosing between them at each  startup." 

refer URL  [http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml) step  #4.

At the end I am disappointed that I cannot see Windows boot option (Dual  boot) It just gives Ubuntu option.

I kept 50 GB free space for Ubuntu.

Is there any option to recover/switch to windows booting? Or I have lost  Windows installation overwritten by Ubuntu?


I need your help onhow to recover the my previous installed Windows OS?

Thanks in advance

Warm regards
Krishna

---

### Post by Megaptera on 2011-02-02
Hi,
It might just take an update of grub, it did with my dual boot.
Boot in to Ubuntu, go to menu > applications > accessories > terminal. In terminal type sudo update-grub 
your password will be asked for & as you type it in nothing shows on the screen (threw me at first!!) then hit enter.

Then try a re-boot and hopefully you'll have a choice of Ubuntu (with 2 or 3 recovery-type options) & then Windows.

As I said, that worked for me.

---

### Post by kansasnoob on 2011-02-02
Please post the output of the Boot Info script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I hope you didn't do what I warned of here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

More specifically here:

[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)

> Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!


---

### Post by krishnamurthig on 2011-02-02
> **Megaptera said:**
> Hi,
It might just take an update of grub, it did with my dual boot.
Boot in to Ubuntu, go to menu > applications > accessories > terminal. In terminal type sudo update-grub 
your password will be asked for & as you type it in nothing shows on the screen (threw me at first!!) then hit enter.

Then try a re-boot and hopefully you'll have a choice of Ubuntu (with 2 or 3 recovery-type options) & then Windows.

As I said, that worked for me.
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks for your mail. I will try that. However I need one more info. In the URL link above I mentioned, on step # 4 ( Screen shot # 4) it is mentioned that "[/FONT][/COLOR]**[COLOR=#99cc00][FONT=Verdana]Editor's Note:[/FONT][/COLOR]**[COLOR=black][FONT=Verdana] *[FONT=Verdana]This option will ONLY appear if you have another operating system installed, such as Microsoft Windows. Remember that, after the installation, the Windows boot loader will be overwritten by the Ubuntu boot loader! [/FONT]*
"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]What does it mean ? It meas do I need to do something for Windows?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks in advance[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Krishna[/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by Swagman on 2011-02-02
Easiest was I can explain the bootloader is..

Windows (or any other o/s) is an unstarted engine when you switch on your computer. So a "kickstarter" is required (Bootloader) to fire it into action.

The message you are being given is that the Windows specific "kickstarter" (bootloader) is going to be overwritten with a Linux one.

Nothing to worry about as Linux happily accounts for other O/s's and will make an entry in it's own bootloader to allow windows to fire up.

What this **DOES** mean though is that if you then wipe Ubuntu off your system Windows **WILL NOT BOOT** until you repair the windows bootloader.

---

