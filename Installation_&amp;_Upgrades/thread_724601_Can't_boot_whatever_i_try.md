---
title: "Can't boot whatever i try"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by Ahito on 2008-03-14
Hello.
I downloaded the ubuntu 7.10 live cd checked de md5sum burnit on a cd (spped 4x) cd is ok but when trying to boot the loading page stops after 3 squares and a quarter. Safe grapichs mode also stops and the last line is something like (==========). Seeing that this doesn't work i downloaded the altrnative cd checked md5sum burn it on a cd with the same speed checked the cd and after that i managed too install ubuntu in text mode. All well for now :D. When rebooting the loading screen stops at the same place like the livecd and in recovery mode the same like safe graphics mode.I've searched about the problem on google and i found out it may have something to do with the nvidia drivers(i have a geforce 5700 at 256 mb ram 256 bit) so i changed to the onboard vga. When starting ubuntu it seems to load but after that the screen goes black and the computer starts to beep continuously, i've tried again recovery mode and i seem to get to a console where i tried diferent commands to update the driver from diferent sites but when i type exit the screen goes black again and starts to beep. it's one a clock here (am) trying to get it work for about 5 hours but i'm fresh out of ideas and searched allot of forums already and i'm tired to be honest so i thought 'd just ask for some help. 
Thank you very much. 
my specs : intel pentium 2.4 ghz , nvdia geforce 5700 256 mb , 80 gb hdd, 1gb ram .

---

### Post by lockdown on 2008-03-14
I have the same problem. Can someone help??

---

### Post by Pumalite on 2008-03-14
[http://ubuntuforums.org/showthread.php?t=710093&highlight=geforce+5700](http://ubuntuforums.org/showthread.php?t=710093&highlight=geforce+5700)

---

### Post by Ahito on 2008-03-15
ok maybe i haven't been clear : i can't even get in ubuntu. i installed it yesterday and i havent't even seen it's desktop  because it freezes at the damn loading screen like i explained in the first post. sry but i just woke up :). btw i also run xp on this machine an it's loading just fine.

---

### Post by confused57 on 2008-03-15
Try booting into recovery mode(with your Nvidia card connected?), then enter:
```
dpkg-reconfigure xserver-xorg
```

You can probably go with the defaults for most selections, but try "vesa" for the driver...or you can try "nv", which would give better performance.  When you're finished reconfiguring your xorg, then enter "reboot", without quotes.

---

### Post by Ahito on 2008-03-15
Made some progress. :) I pluged my onboard video card and booted in recovery mode. The i applied dpkg-reconfigure xserver-xorg and reconfigured that file with the nv option then rebooted in normal mode. Now a warning appears saying that ubuntu is running in low-graphics mode and i can configure cancel or continue. I tried to configure my monitor and both graphic cards and then i selected continue and the screen goes black. I hit ctrl+alt+f1 and enterd in console and managed to login in ubuntu in text mode. Now i just want to know how to configure the damn nvidia card from here and the internet connection if that is need because when i plug back my 5700 it still doesn't work. Thx for you're support untill now.

---

### Post by Peter09 on 2008-03-15
HI,
go here

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

download Envy and let it install the best driver for your card.

PC

---

### Post by Ahito on 2008-03-15
Ok but how do i do that in console mode ? Or can i dld it on windows and then i can copy it to  a fat32 partition that i made when i installed ubuntu. would that work ?
edit:
i can't access the internet from console because my connection is not configured and i don't know hot to configure it form console mode. I have a PPPoE connection.

---

### Post by Peter09 on 2008-03-15
try typing

```
startx
```

at the command prompt

---

### Post by Ahito on 2008-03-15
already tried that but it failles :(

---

### Post by Peter09 on 2008-03-15
You need to do

```
dpkg-reconfigure xserver-xorg
```

again so that you can get back to your normal startup - even with bad graphics. Then get Envy.

---

### Post by Peter09 on 2008-03-15
Note that if the nv driver does not work then try the vesa driver.

PC

---

### Post by Ahito on 2008-03-15
before this console mode from heaven :) there was not even a ugly graphics mode it just froze at bootup. edit i'll try the vesa driver even do i don't know if it's going to work

---

### Post by Peter09 on 2008-03-15
Note that you appear to say that you have disabled your Nvidea card and enabled your onboard graphics. I am suspicious that this is working because the machine sitting beeping tends to indicate a H/W fault. Might be worth checking that.

You would do better to keep to a configuration that you know works (for windows or the live CD) and then go from there.

---

### Post by Ahito on 2008-03-15
Like i said in the first post the live cd never worked for me, i installed ubuntu from the alternative cd. And it's interesting that with my nvidia card i can boot windows just fine and i cant boot ubuntu and with my onboard card i can boot ubuntu in console mode but can boot windows. btw tried vesa and what a srprise it didn't work :). Another interesting thing is that with kiwi a romanian form of ubuntu i had the same problems that's why i got ubuntu. I also tried to boot from my  sub slax pendrivelinux and another 2 that i forgot they're name but all of them didn't work and the only linux that i could boot (from a usb) was feather  linux. edit: i've just started with linux this week  and had high hopes for it but it's getting really  annoying. (windows installs in only 30-45 minutes and you don't have driver problems :P)

---

### Post by Peter09 on 2008-03-15
The fact that you cannot boot the live CD is an issue. 

Anyway your O/S is working its just the graphics drivers that are the problem. I would stick with the Nvidea card, at least we know what that is and that windows works with it. Support for that card is good. 

Suggest you re-enable that and see if you can configure it to work.

PC

---

### Post by Peter09 on 2008-03-15
Hi,
just another thought, which live CD are you using, there are several flavours and what is the model of your mother board.

PC

---

### Post by Ahito on 2008-03-15
the live cd is ubuntu 7.10 for x86 and the alternative is the same and i have a ASRock  P4i45GV with AGI 8X.

---

### Post by confused57 on 2008-03-15
> **Ahito said:**
> the live cd is ubuntu 7.10 for x86 and the alternative is the same and i have a ASRock  P4i45GV with AGI 8X.
Maybe this will help with installing Envy from the terminal:
[http://ubuntuforums.org/showpost.php?p=2685120&postcount=5](http://ubuntuforums.org/showpost.php?p=2685120&postcount=5)
You may want to go to the Envy download site from another pc to find out the latest version.

---

### Post by Peter09 on 2008-03-15
Unfortunately the Internet is full of problems regarding your Motherboard and Linux.

 Note that the specification for the graphic card interface is AGI. This appears to be a non standard implementation and causes the graphics drivers to crash. I have looked but not seen a solution posted.

PC

---

### Post by plovin on 2008-03-15
I  have just installed Ubuntu and I am having problems getting the Totem Movie Player to work.  I get a message, "error cannot read disc. install appropriate plugins".  I checked the add and remove programs and it intidicates that the Gstreamer plugin is installed.   I also have followed the instructions on the Totem help and tried double clicking on video in the Nautilus file manager.  Still no luck.  Help!

---

### Post by Pumalite on 2008-03-15
sudo aptitude install ubuntu-restricted-extras

---

### Post by Ahito on 2008-03-15
Thx pete for you're help i'll search and see what i can do to solve this problem. btw when you say this motherboard and linux you  don't mean just ubuntu. right?

---

### Post by Peter09 on 2008-03-15
It seems to be all Linux distributions. 

There may be a solution I have not found but unfortunately there is a lot of people in your position out there.

PC

---

### Post by Ahito on 2008-03-15
Hello. I found a possible solution to fix my problem. It seems  that my onboard vga can't be disabled and so there's some sort of conflict with the 5700. The only viable solution i found is to recompile the kernel without onboard vga mode or something like that. Now the only thing is left is to learn how to do that.
Anyone knows how to recompile the kernel without the onboard vga support and explain it to me.
An how to do that in the console mode :D
Thank you.

---

### Post by Ahito on 2008-03-15
Sorry to bump but it's late around this part of the world and i am rather sleepy.

---

### Post by Ahito on 2008-03-16
just bumping :p

---

### Post by Ahito on 2008-03-17
Problem solved by blacklisting intel_agp and then booting with the nvidia card and configuring xorg.conf

---

### Post by Peter09 on 2008-03-17
Well done, that was a complex problem.

---

### Post by Pumalite on 2008-03-17
Glad you got it working.

---

