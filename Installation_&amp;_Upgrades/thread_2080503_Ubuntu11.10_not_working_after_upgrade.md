---
title: "Ubuntu11.10 not working after upgrade"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by skeebs on 2012-11-04
Hi,

I know there are many people who have experienced similar probs of upgrading then just getting a purple dead screen. But looking on other peoples posts I can't seem to find a solution for me. There are a lot of "hold the shift key down and then..." but mine does nothing when I do that but I can hit delete and go into bios.

So, my version of the problem is: didn't get round to upgrading from 10.10, so got a msg saying there will be no more updates, paniced and clicked yes for going straight to 11.10 (so no 11.04). All went well during upgrade. Restarted it and now it stops at the purple screen. I went into bios, changed the boot option from bootng from a disk to booting from hd, re did it, got the purple screen with the message that things were being checked, press c to cancle etc, but then nothing again.Tried boot up again and nothing except for the purple screen again, like before.

Please help as my husband needs the pc for his self employed work nd we hate windows so don't want to have to use that!! I'm not up on my linux lingo and don't work with computers really, so althogh I've had ubuntu for a while, this is just for my home pc so I'm still a beginner, please be kind :) 

Thanks

ps just managed to get into grub but dont kno what's best to do from here!!

---

### Post by ibjsb4 on 2012-11-04
It should be fixable, it was a common problem with 11.10.  But then be prepared to do it again next April when 11.10 reaches EOL.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=purple+screen+11.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=purple+screen+11.10&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Maybe you would be better off with a fresh install of 12.04.  Its an LTS release and supported for five years.  You could use the 12.04 live CD to retrieve you personal files from the current install.  12.04 has a new desktop called Unity, but you could stick with something that looks like your current desktop by switching to Gnome Classic desktop if you wish.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Just something to consider  :)

---

### Post by grahammechanical on 2012-11-04
Are you dual booting or not? With a dual boot you will get a Grub boot menu. If Ubuntu is the only operating system on the machine, then you will not see the Grub menu but it will still be there. That is why we suggest using the Shift or ESC to bring up the Grub menu.

At the Grub menu you will see not only the option to boot Ubuntu but also to boot Ubuntu in Recovery mode. Select that and at the Recovery menu Select Resume. That will you bring you to the log in screen or the desktop if you have login set to automatic.

Once, you get to a desktop you can use the Additional Drivers utility to activate a proprietary driver. That may fix this problem.

For your information. If you set the boot order in the BIOS to boot first from the CD/DVD drive and then the hard disk, the boot process will first look for an operating system on a disk in the CD/DVD drive. If it cannot find an operating system there it will look for an operating system on the hard disk. So, you did not need to change your settings in the BIOS.

By the time you see that purple screen the BIOS has already done its stuff and so has the Grub boot loader. By that point booting has been passed over to the operating system and it is hitting a problem somewhere.

Regards.

P.S. Non-LTS Ubuntu versions get 18 months support. So, the reason you could not upgrade to 11.04 is because by now it also is out of support. And by May 2013 both 10.04 and 11.10 will also be out of support.

---

### Post by skeebs on 2012-11-04
> **ibjsb4 said:**
> 

Maybe you would be better off with a fresh install of 12.04.  Its an LTS release and supported for five years.  You could use the 12.04 live CD to retrieve you personal files from the current install.  12.04 has a new desktop called Unity, but you could stick with something that looks like your current desktop by switching to Gnome Classic desktop if you wish.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Just something to consider  :)

installed 12.04 :) Just checking it's working now, but any probs I'll post on another thread. Thanks!!!

---

