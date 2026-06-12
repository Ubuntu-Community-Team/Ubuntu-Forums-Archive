---
title: "Acer Aspire 5336 Ubuntu (11.04) black screen/brightness fix"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by the_crayon_king on 2011-04-28
This fixed a black screen issue and a brightness adjustment issue after installation of ubuntu. Also on 11.04 I couldn't get Unity to work until I edited grub I didn't come up with the fix but it took me forever to find a solution so I figured I would post it. If I have did something wrong just get a mod to delete or move this. I don't use forums often. 
```

sudo gedit /etc/default/grub

Edit two lines to read as follows: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

```

---

### Post by Chris2243 on 2011-04-29
Thanks for this, it sorted it for me. The function buttons are reversed but I can live with it!

---

### Post by docmark777 on 2011-04-30
Either I did it wrong or it didn't work for me.  I think I probably did it wrong. 

Could you rewrite those instructions with any and all details. 

I assume that was not all done in the terminal window?

Thanks,

---

### Post by diehard67 on 2011-05-04
> **Chris2243 said:**
> Thanks for this, it sorted it for me. The function buttons are reversed but I can live with it!
I have an acer aspire 7715 and had the same problem, I upgraded the bios and it went away, the reversed brightness buttons I meen, still waiting for a fix to that backlight issue, however the workaround in the first post allowed me to atleast turn on the light myself.

---

### Post by danielelias22 on 2011-05-15
[QUOTE=: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub
[/CODE][/QUOTE]

My screen was waayyy to white.

NOw i can see better.

I love you.

---

### Post by leisuresuitgreg on 2011-05-23
woops.. ignore post. I'm an idiot.

---

### Post by leisuresuitgreg on 2011-05-24
Can't seem to get this to work on HP 6735s...

Any other ideas anyone? I have noticed others using this

```
echo 9>/sys/class/backlight/acpi_video0/brightness
```

But I have nothing in the folder /sys/class/backlight/ It is empty!

Cheers for any help in advance!

Greg

---

### Post by thelildrummaboy on 2011-07-31
i dont get the code stuff how do you do all this stuff just got linux a few days ago have the same issue dont know how top use the terminal can you please help me

---

### Post by Vines on 2011-09-09
Oh, man! I love you too. Fixed brightness control on Acer Aspire 5755G.

---

### Post by babakmoazzez on 2011-10-02
Thanks to [the_crayon_king]("http://ubuntuforums.org/member.php?u=940485"), the first solution worked for me.

---

### Post by pilotuser on 2011-10-16
Thanks, the_crayon_king. It also works in 11.10 !

---

### Post by Threadbaron on 2011-10-22
It almost works on my eMachines E725
Or it works, until I connect an external monitor to the notebook.

Then the external monitor starts to work, and the notebook backlight is turned off again. Off course if I run the script again, the blacklight is back, but how I could I run it automatically, after an external monitor is attached to it?

Please note that it is also a problem, if the external monitor is plugged in during the startup. The login screen is sort of fine (the notebook is using the resolution of the external monitor for some reason), but after the login the notebook screen goes dark again.

Any idea?

---

### Post by dan_hurst on 2011-10-25
Thanks the_crayon_king, this worked with my Acer Aspire 5736z.  

Buttons reversed but a million miles better than what it was!

---

### Post by Dyskid2011 on 2011-11-03
> **the_crayon_king said:**
> This fixed a black screen issue and a brightness adjustment issue after installation of ubuntu. Also on 11.04 I couldn't get Unity to work until I edited grub I didn't come up with the fix but it took me forever to find a solution so I figured I would post it. If I have did something wrong just get a mod to delete or move this. I don't use forums often. 
```

sudo gedit /etc/default/grub

Edit two lines to read as follows: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

```





Doesn't work for me idk wtf I'm doing lol 
Acer Aspire 5734Z

---

### Post by Dyskid2011 on 2011-11-03
> **the_crayon_king said:**
> This fixed a black screen issue and a brightness adjustment issue after installation of ubuntu. Also on 11.04 I couldn't get Unity to work until I edited grub I didn't come up with the fix but it took me forever to find a solution so I figured I would post it. If I have did something wrong just get a mod to delete or move this. I don't use forums often. 
```

sudo gedit /etc/default/grub

Edit two lines to read as follows: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

```





Doesn't work for me idk wtf I'm doing wrong lol 
I updated from 10.04 lts to 11.04 I can still see that my screen works just no backliht. I'm on it now using a flashlight to see what i'm doing
Acer Aspire 5734Z

---

### Post by la11111 on 2011-12-08
I just purchased an Acer Aspire 5733z and found that although the function keys for brightness were recognized, the brightness setting was not changed. 

FTR, I installed Linux Mint 12 which is Ubuntu-based.

the update-grub fix worked for me. Thought I would add my 2c for the sake of googlers everywhere. here's the relevant info for my HW:

--

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

--
# lsmod | grep ^i915
i915   566711  3

--

good luck!

---

### Post by Mr Heretic on 2012-03-04
Thanks a lot, crayon king!
The brightness had been completely unadjustable, but this fix worked flawlessly.
Using Linux Mint 12 on an Acer 5755G.

---

### Post by workflow on 2012-08-21
Omg, it works!

(On Ubuntu 12.04 @ Acer Traverlmate 8372G)

Thank you crayon_king!

---

### Post by TheoFromSed on 2012-09-24
> **the_crayon_king said:**
> This fixed a black screen issue and a brightness adjustment issue after installation of ubuntu. Also on 11.04 I couldn't get Unity to work until I edited grub I didn't come up with the fix but it took me forever to find a solution so I figured I would post it. If I have did something wrong just get a mod to delete or move this. I don't use forums often. 
```

sudo gedit /etc/default/grub

Edit two lines to read as follows: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

```

Thank you. This solve brightness problem at Acer Aspire 3935, Ubuntu 12

---

### Post by hoffman462 on 2012-11-25
Does not work on Acer Aspire 5732Z.
Thanks

---

### Post by jayismyname on 2013-05-22
Hi this is what I did 

I had this issue with 12.10 and 13.04 when you first boot the disk get into the grub boot menu and press F6 and select **nomodeset**. You will be able to install fine no problems and boot up from drive with no problems but the resolution will be out and it will run slow so to fix this you go into grub **sudo gedit /etc/default/grub** then change **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** to** GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"** then change **GRUB_CMDLINE_LINUX=""** to **GRUB_CMDLINE_LINUX="acpi_osi=Linux"** make sure you use a cap L in Linux. You need to delete **nomodeset** from the grub script that will sort out the resolution and the slowness but not the back light. After you have done all this press save and exit back to the terminal and run **sudo update-grub** so it is set up for the next time you boot. enter **sudo gedit /etc/rc.local **(you might have to be root for this) then between **does nothing **and **end 0** add **setpci -s 00:02.0 F4.B=00** 

This has completely cured it for me I don't have to do anything to it now and it took me 2 days to sort out, running brilliantly with no issues. Just to add you might have read to start it with acpi=off don't as it will disable your WiFi!

---

