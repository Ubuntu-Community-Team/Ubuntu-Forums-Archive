---
title: "installation problem"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Istvan D on 2011-05-20
Hi,

I have a problem upgrading my Ubuntu.
It's an Intel 32bit based laptop, dual boot (with Win7), running Ubuntu since Edgy, right now Maverick is still installed and up. I tried to install 11.04 from a CD, iso MD5 is okay, CD is okay (both burning sw and checking tool on CD say it is). CD works in other machines.
When I boot from CD, it goes until it has to access some parts of the CD (I can get the menu for direct install/memtest/...), but then it gets into some kind of loop, the lines go pretty fast, I can't really read it, but the beginning of the lines is the same, see on the pictures:
[https://picasaweb.google.com/dalicsek.istvan/Ubuntu#5608780625735975714]("https://picasaweb.google.com/dalicsek.istvan/Ubuntu#5608780625735975714")
Only hard reset helps.:(
Do you have any ideas what might cause this?:confused:
Thx

---

### Post by Dutch70 on 2011-05-20
Not sure if this will help or not, but have you tried failsafe mode, or other boot options? 
[[COLOR="Red"]https://help.ubuntu.com/community/LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
Also, if you're not, you should select "Try Ubuntu" before installing it.

Just a thought here, but maybe using a usb stick would help. It only has to be a 1GB stick even though the site says 2GB.

---

### Post by Istvan D on 2011-06-02
Okay, I was able to boot into live CD and install with the "no acpi" option, but after the installation, I cannot boot into Ubuntu (I can boot into my Win though, so GRUB seems to work fine). How can I boot in the installed OS with a "no acpi" option? I did not find any advice in the GRUB2 documentation page on ubuntu.com.
thanks a lot

---

### Post by mörgæs on 2011-06-02
During boot, did you see a screen with a symbol of a keyboard and a man at the bottom?

---

### Post by Istvan D on 2011-06-03
I am trying to boot my installed system already (answering your question: yes, when booting the live CD, I see it, and I do check acpi=off there). But now, it looks like this:
- I turn my PC on
- boot logo
- BIOS pwd
- GRUB menu, 5 options: Ubu, Ubu recov mode, memtest, memtest with console, Win
When I press "e", I can edit the options for booting Ubu, but I do not know what to type to turn acpi off. When I boot in recov mode, I get the same screen as posted above.
please help
thank you

PS: BTW, why do I need to turn acpi off now, when _all_ previous releases of Ubu worked fine?

---

### Post by mörgæs on 2011-06-03
[http://askubuntu.com/questions/3431/boot-with-noacpi-automatically-from-hard-drive](http://askubuntu.com/questions/3431/boot-with-noacpi-automatically-from-hard-drive)

---

### Post by Istvan D on 2011-07-31
thanks, that solved it.

---

