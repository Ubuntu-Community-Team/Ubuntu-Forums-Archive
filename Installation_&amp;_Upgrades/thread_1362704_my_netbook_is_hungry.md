---
title: "my netbook is hungry ??"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by cbspools on 2009-12-23
GRUB
 
we have an acer aspire one with 2 8gb SSD's. it has windows xp on it and we downloaded the 9.10 remix for netbooks. Installation went smoothly and it created the ext partition and swap.
 
I was instructed to remove the dvd and reboot. I did so but now the netbook is hungry and asking for GRUB _
 
I tried installing it twice, each time erasing the drives and choosing use full diskdrive amount. I was able to use the "try ubunto before installing" option and it worked well.
 
any thoughts or helpful hints for this? 
 
thx

---

### Post by PhilMize on 2009-12-23
Wat?

"I did so but now the netbook is hungry and asking for GRUB _"

English?

Are you trying to install winblows and netbook remix along side each other? Or are you trying to wipe and do a clean install of netbook remix? I don't understand what your asking...:confused:

Take a step back, breath, and rewrite the post. You sound frustrated and rushed. We can't help if you don't make any sense when you post.

---

### Post by cbspools on 2009-12-23
hi, I want to get rid of windows xp on this machine and replace it with Ubuntu remix.
 
I downloaded the file and burnt the dvd.
I attached my usb ext. dvdrom and booted off it to do the install.
 
I went thru the installation just as the instructions on the website suggested.
At the end of the installation it said to remove the dvd disc and reboot the machine.
 
I did that and when the netboot rebooted, it didnt go anywhere.
 
It is a blank screen with the words  GRUB _    in the top left hand corner of the screen. and it is blinking.
 
Not sure what that means or what I did wrong.
 
does this help?

---

### Post by PhilMize on 2009-12-23
Ahhh yes! Much better!


Well you definitely wiped xp off that's for sure. I'm assuming, when you were going through the install, you selected "Guided mode". Am I right? 

If you have reinstalled more then once and are still getting the same issue there may be a problem with the disc you burned or image you downloaded. It's happened to me before. Try re-downloading the iso image again and using that image instead of the one you are currently using. There's also an option when you first boot off the disc or usb drive to check the integrity of it. Try that! 

I find with my netbook I have much better luck just using an external dvd burner to install with then say installing off a usb drive.

Hope this helps!

---

### Post by wsonar on 2009-12-23
> **cbspools said:**
> GRUB
 
 the netbook is hungry and asking for GRUB _
 

 
thx

^^Sig worthy


[IMG]http://l.yimg.com/us.yimg.com/i/mesg/emoticons7/24.gif[/IMG]


sounds like GRUB may not be installed correctly

---

### Post by cbspools on 2009-12-23
hi yes i choose the guided option.
 
just downloaded the image two days ago so will download again today.
i am also using my ext. dvdrom instead of a usb drive to install the ubuntu.
 
will do resintall after getting new image file.

---

### Post by audiomick on 2009-12-23
you could try re-installing grub. I take it you installed 9.10?
Then it will be grub2. If you look at this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Quite a way down, there is a bit about re-installing from the live cd. Try that. It is quicker than a new install, and if it doesn't work, you can still re-install afterwards.

---

### Post by cbspools on 2009-12-23
audiomick, thats alot to read... thanx.
will try the grub install since I can get into the livecd part and use it with no issues.
then if fails, will redownload and reinstall.
 
look for updates in few hours!

---

### Post by =not4prophet= on 2009-12-23
you said your netbook has 2 SSDs?  The problem you are describing sounds like grub is configured to look for your linux filesystem on the wrong drive.  I would check your grub configuration.

---

### Post by cbspools on 2009-12-23
well I tried all suggested and it was the last one that did it.
 
When i reinstalled on the "other" ssd listed, I booted normaly into Ubuntu.
so why is the 2nd ssd listed really the first drive? seems weird.
 
But we are on and playing the games on it!!!
 
But we cannot log off. it says its a 9" screen and its not so we cannot see how to SHUTDOWN or logoff?    is there a key combo in Ubuntu to shut off the netbook?

---

### Post by audiomick on 2009-12-23
The last resort is a terminal command

```
shutdown -P now
```

if you want to know exactly what that does, look at

```
man shutdown
```

From what you write about the screen, it sounds like you don't have the right video driver installed.

---

