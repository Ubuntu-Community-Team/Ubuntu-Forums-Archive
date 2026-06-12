---
title: "Is Feisty not friendly for laptops?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by jeecol on 2007-04-23
First of all, I am sorry to use this kind of topic, however, I have failed too many times.

Some failures of installing Feisty on laptops are discussed in Ubuntu Taiwan forum (including myself) and English forum as well; some of them are not new Linux users. I think it could be a coincidence if only one person has a trouble. But now, It seems that it is no coincidence. 

I use Compaq Presario 1536AP (made in 2002), and I use Kubuntu 6.10 now. After endless failures, I decided to wait and keep using 6.10. But I just have few troubles to install 7.04 on desktops (just change the DVD or CD drives when the error comes. I guess some of my drives are too old)

However, I feel that my laptop is not ready to install Feity.  Any suggestion? Any solution? 

---------
jeecol = one dollar

---

### Post by icechen1 on 2007-04-23
Ubuntu 7.04 works great for mine,even changing brightness level works,the only problem is the microphone not working and that is all.

---

### Post by aysiu on 2007-04-23
I can't speak for anyone else, but Dapper and Edgy couldn't give me resume-from-suspend on my Dell Inspiron 500m, but Feisty did it without any tweaking. My laptop keys work (including multimedia keys), sound works, video works... no major complaints here.

---

### Post by jfinkels on 2007-04-23
> **jeecol said:**
> First of all, I am sorry to use this kind of topic, however, I have failed too many times.

Some failures of installing Feisty on laptops are discussed in Ubuntu Taiwan forum (including myself) and English forum as well; some of them are not new Linux users. I think it could be a coincidence if only one person has a trouble. But now, It seems that it is no coincidence. 

I use Compaq Presario 1536AP (made in 2002), and I use Kubuntu 6.10 now. After endless failures, I decided to wait and keep using 6.10. But I just have few troubles to install 7.04 on desktops (just change the DVD or CD drives when the error comes. I guess some of my drives are too old)

However, I feel that my laptop is not ready to install Feity.  Any suggestion? Any solution? 

---------
jeecol = one dollar

Post specific problems you have with your installations in new threads, and we would be happy to help fix your problems.

---

### Post by am_pcguy on 2007-04-24
> **jfinkels said:**
> Post specific problems you have with your installations in new threads, and we would be happy to help fix your problems.

Or not, I have a 5 day old thread about my CD/DVDRW drive not mounting without one reply.  The bug report on lauchpad is getting about the same amount of attention.

I have a Toshiba A135.  Under 6.10 I had everything but sound after suspend and I couldn't burn CD/DVD's.

I upgraded to 7.04 and lost sound.  I also lost my DVDRW drive, it will not mount at all, Ubuntu sees it but wont mount it.  If I boot on battery power I get a blank brown screen, no log in nothing, I can't ctrl-alt 1 to a different terminal, I'm just stuck on the blank screen.  My SD Card reader doesn't work either.  Some of my applications (Cisco VPN Client) stopped working as well.

Most of these problems are kernel issues when you look in launchpad they have been reported, and are being worked.  I was just very suprised to lose so much when everything was working so well under Dapper.

I've decided to stay with Feisty and just wait for the fixes to show up, I don't know enough to contribute anything but results of attempts to make things work.  Giving up on Feisty won't help the community at all.

I'm dual booting so I have a fall back while the problems are resolved.  I just would not recommed upgrading until things are more fleshed out.  Maybe do a search on lauchpad for some of your more questionable devices if you really want to make the jump.

---

### Post by techristian on 2007-04-25
Let's see.

No sound.
No wireless.
and only 600X800 video on a laptop capable of 1280X768

.....................................................nope.


Dan






*** Advertising removed by staff ***

---

### Post by riomx on 2007-04-25
On my laptop I haven't been able to test the extent of how Ubuntu works...because I can't get it to follow a normal installation process

The LiveCD performance is great from what I can tell.

Unfortunately, my Sony Vaio C140G has a 7 GB partition at the beginning of the disk (no idea why) that is automatically mounted instead of the partition on which Windows is installed

Also, even after manually mounting the Windows partition, it still can't recognize it and doesn't offer an option to import user or OS settings, because it can't detect either

---

### Post by Sef on 2007-04-25
> Unfortunately, my Sony Vaio C140G has a 7 GB partition at the beginning of the disk (no idea why) that is automatically mounted instead of the partition on which Windows is installed


Windows needs to be on the first partition, not sure why yours is not.

---

### Post by patrickfromspain on 2007-04-25
maybe you just have poor linux friendly software: a sony vayo, toshiba A135, Compaq... I've heard quite a bit of problems with sony, toshiba and compaq.. back luck, I guess.

Anyway, I have a toshiba satellite L10 and all is working best.. I now even have supesd and hibernate.. cool :)

---

### Post by riomx on 2007-04-25
> **Sef said:**
> Windows needs to be on the first partition, not sure why yours is not.

Not sure either.  It came that way from the factory.  And since it's on the second partition, I guess Windows doesn't really need to be on the first :D

---

### Post by docdailey on 2007-04-25
> **patrickfromspain said:**
> maybe you just have poor linux friendly software: a sony vayo, toshiba A135, Compaq... I've heard quite a bit of problems with sony, toshiba and compaq.. back luck, I guess.

Anyway, I have a toshiba satellite L10 and all is working best.. I now even have supesd and hibernate.. cool :)

my vaio is mostly working.  it hangs quite a bit but restarts...firefox greys out every now and then...almost like power saving when a page is slow to come up.  The camera doesn't work and I havent even fiddled with the mic...but all else seems to work.

Bill

---

### Post by Rinzwind on 2007-04-25
> **riomx said:**
> Not sure either.  It came that way from the factory.  And since it's on the second partition, I guess Windows doesn't really need to be on the first :D

It's probably a windows partition that has your windows installation files (restore to factory settings).
And yes windows boot(!) needs to be on the 1st partition.

---

### Post by GoBieN on 2007-04-25
HP Pavilion dv6017ea -> needed to boot the liveCD with NOAPIC, and change the lines in grub after install.

For the rest: Everyting (every last bit) worked out of the box !

---

### Post by silverbullet007 on 2007-04-25
My Thinkpad A31 works great.  Sounds, wireless, everything except the hot swapping of cdrom devices.  Of course I am not dual-booting either.  The multipedia /document keys work fine

---

### Post by wyth on 2007-04-25
An older Gateway 600 YG2 almost made it; everything works a treat except the video card, which was kind of a show stopper.  Network Manager (with ndiswrapper) also wouldn't connect to secure networks, but the same ndiswrapper version worked perfectly with Network Manager in Edgy.

---

### Post by aztektum on 2007-04-25
works better on my T41 than it does on my tricked out desktop which really is for win-gaming anyway. i just installed it to see how it ran.

I have been using ubuntu on (many) diff laptops since warty and feisty has by far been the most "user friendly".

---

### Post by am_pcguy on 2007-04-28
I posted earlier that I had a bad experience with the upgrade. 

Today I gave up on trying to fix that install after an update broke x, and I couldn't get it running again.  I did a full install of 7.04 on my Toshiba laptop. 

Everything is working as good as it was under 6.10.  My Fn key for brightness works, SD card reader, DVDRW, and sound all work.  

If you are installing on a laptop I would say do not upgrade.  Just backup your data and install fresh.

---

### Post by mostholy on 2007-04-28
Please, which Toshiba laptop?

---

### Post by magudelo on 2007-05-05
I installed ubuntu Feisty in a HP-Compaq nx9110 and is working very good. I'm able to synch my PDA with evolution, watch my DVDs and listen my music while and drinking some beers replying this email. Thanks Ubuntu!!!

---

### Post by Tom Tiger on 2007-05-05
Just my two cents....

I've tested and am running 7.04 Feisty Fawn on several Toshiba Laptops, to me this was oddly painless... I had more problems with Feisty on my desktops :-)

Tested,  (All Toshiba laptops)

Satellite Pro 6100 (with Nvidia)
Satellite Pro A10 
Satellite Pro 6050

Portege R100

All of these were upgrades from 6.10 to 7.04.  I even turned on the 3D desktop on the A10.

No problems found.

---

### Post by chewjoel on 2007-05-12
I installed it on my Asus M2400N, so far everything is working quite OK.
But Sound is not working; 
The boot up is a bit slow;
And I haven't figure out how to type Chinese character with it.

Anyone has any suggestions?

---

### Post by jeecol on 2007-05-23
To chewjoel,

If you use simpilified Chinese, sorry I do not know how to do it. You may find it by Google

For traditional Chinese, please check this: wiki.ubuntu.org.tw

Or see unofficial manual of 6.10   /wiki.ubuntu.org.tw/index.php/Ubuntu6.10Guidetw

You need to install "gcin" or other input methods (I like gcin), and intall "im-switch".
And then set gcin as the default input method:   (sudo?) im-switch -s gcin 

Good luck! 

-------
jeecol = one dollar

---

### Post by diskotek on 2007-06-13
hi there,
i found a page on ubuntugeek (well, they mistype feisty) for speeding up boot time on laptops. but i didn't understand what should i need to do. nobody can explain it briefly? 

[http://www.ubuntugeek.com/how-to-fix-slow-fesity-boot-for-laptops.html](http://www.ubuntugeek.com/how-to-fix-slow-fesity-boot-for-laptops.html)

---

### Post by hardyn on 2007-06-13
Asus Z71vp

everything works, suspend took some massaging... but everthing else worked out of the box; with exception to the installing of the binary nvidia driver.

I have some wishes to have more of the power management devices be employed, maybe gusty.

---

