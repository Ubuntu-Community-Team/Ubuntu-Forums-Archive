---
title: "Did I brick my computer?"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by Brendan_Doyle on 2014-01-25
Well guys I'm an idiot, I installed on the sad and that didn't work so I wiped Linux off of it, then I started a new install on my hdd that has windows and went through with it, and midway I thought maybe I should restart the computer since I wiped the ssd, well afterwards I figured out that was a dumb idea because it wiped widows off and the install wasn't completed. So now I'm greeted by a blinking white line and have no idea what to do.

---

### Post by Brendan_Doyle on 2014-01-25
Hhheeeeeeelllllllllpppppp

---

### Post by Iowan on 2014-01-25
From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not bump your thread more than once in any 24 hour period. Consider waiting longer than that before bumping - this may help to catch the attention of users outside of your timezone.

---

### Post by Brendan_Doyle on 2014-01-25
> **Iowan said:**
> From the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):


Well sorry but I'm kind of in panic mode over here, I need to know if I can fix this, I can get to the bios, but I can't get to the boot select.

---

### Post by QIII on 2014-01-25
We all understand that panicked feeling.  But remember that we are just users like you -- in all time zones around the world -- who are here as we have time to volunteer.

Can you tell us what you would like the final outcome to be?

Do you want to try to recover Windows or your important files?

Do you want an Ubuntu-only machine?

Do you *not *want to use the SSD as an OS disk, or do you?

---

### Post by Brendan_Doyle on 2014-01-25
> **QIII said:**
> We all understand that panicked feeling.  But remember that we are just users like you -- in all time zones around the world -- who are here as we have time to volunteer.

Can you tell us what you would like the final outcome to be?

Do you want to try to recover Windows or your important files?

Do you want an Ubuntu-only machine?

Do you *not *want to use the SSD as an OS disk, or do you? 

I want an ubuntu only laptop. I did the replace windows install on my ssd and it wasn't working so I wiped the ssd, started a new install on my hd that also has windows and selected replace windows, midway through the install ice it had just started the ubuntu install and wiped windows I tried canceling the install, because I thought I should restart before I did this since I wiped the ssd and hadn't restarted yet, but when I tried to close the install(you're not supposed to close it at this part) it crashed and the install program froze so I shut down the computer and was greeted with the blinking white line, and the inability to boot from my ubuntu live cd.

---

### Post by slooksterpsv on 2014-01-25
What kind of laptop is it? Press F12 to see if you can get to the boot selection menu otherwise go into BIOS and change the boot priority to be the cd; also it does eject the cd at the end when you reboot so make sure the drive is closed. If you needed any data off the Windows partition we can run a program called testdisk to recover the partition or see if it will.

---

### Post by Brendan_Doyle on 2014-01-25
> **slooksterpsv said:**
> What kind of laptop is it? Press F12 to see if you can get to the boot selection menu otherwise go into BIOS and change the boot priority to be the cd; also it does eject the cd at the end when you reboot so make sure the drive is closed. If you needed any data off the Windows partition we can run a program called testdisk to recover the partition or see if it will.

It's an hp pavilion dm4-3090se. F12 is not working and the cd is in. How do I change boot priority? I already backed up all the data I wanted. I'm currently running the primary hard disk self test.

---

### Post by slooksterpsv on 2014-01-25
When you go into the BIOS (F2, Esc, F1, DEL, F10 or F8 generally), you'll need to go through the menu options till you find one that says Boot Priority, it may be under Boot, Security or Advanced. There you should be able to select what is the first item to boot from.

---

### Post by howefield on 2014-01-25
Press esc while the computer is restarting, and then press f9 for boot options.

---

### Post by SuperFreak on 2014-01-25
edit

---

### Post by Brendan_Doyle on 2014-01-25
> **slooksterpsv said:**
> When you go into the BIOS (F2, Esc, F1, DEL, F10 or F8 generally), you'll need to go through the menu options till you find one that says Boot Priority, it may be under Boot, Security or Advanced. There you should be able to select what is the first item to boot from.

I love you lol. Changed the boot order, and made my way back to the ubuntu install.

---

### Post by Brendan_Doyle on 2014-01-25
First attempt to install got to the end and said grub bootloader install failed. Trying install again.

---

### Post by grahammechanical on 2014-01-25
You may also have messed up the Ubuntu installation on that USB memory stick. Can you not re-burn the ISO to that stick?

Regards.

---

### Post by Brendan_Doyle on 2014-01-25
> **grahammechanical said:**
> You may also have messed up the Ubuntu installation on that USB memory stick. Can you not re-burn the ISO to that stick?

Regards.

Second install attempt successful. I am now back on my laptop with ubuntu installed. I notice when it boots there are like three lines that say disabled by bios or something like that, is that anything to be worried about? Or does everyone get that?

---

### Post by Brendan_Doyle on 2014-01-26
Going back to windows after realizing there's so much stuff I can't do in Linux. Maybe one day if ubuntu can have a better filing system, and run all of programs windows can I will go back.

---

### Post by slooksterpsv on 2014-01-26
Linux can run a plethora of Windows programs and even programs Windows doesn't have variants for. It depends on your use. I program, listen to music, watch netflix, do some lite video editing, file conversion, etc. which I feel is handled faster and more properly in Linux than Windows. Granted I can do the same in Windows, there's some apps I just have to have that I could spend the time making a Windows version, but like better with the Linux version.

Fave Linux Programs are:
Exaile
Gimp - Don't know why but Linux version seems to handle better
Scratchpad
Wingpanel - part of elementary OS
VLC - yes there's a windows version
KDENLIVE
etc.

It happens, once you find a distro you're comfortable with you may find it can do all of what you need and more. If you need an Office 2007 like version for Linux look at kingsoft wps. Need photoshop, GIMP; need specific windows programs in Linux? try WINE or run a virtualization (won't be as fast and graphics won't be able to handle 3d games, but still useful), etc.

---

