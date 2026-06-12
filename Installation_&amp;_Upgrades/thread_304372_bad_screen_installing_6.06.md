---
title: "bad screen installing 6.06"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by Heemlo on 2006-11-21
I am trying to run 6.06 with the cd i got in the mail. I boot from it and it bring me to the screen with the choices of how to boot (like from hard disk, check cd for error, check memory, boot graphics safe mode etc.). When I select install/boot or whatever it goes through the long string of "ok" thingys. After that the screen is black with the little cursor thing blinking in the upper left hand corner. Then after a few seconds the screen changes and theres colored lines and stuff all over the screen and they change a little and basically its just a mess of colors. I've left it for a while and nothing seems to happen. Safe graphics mode appears to work fine, but I don't want to install anything until i know it works... Can anyone please give me a suggestion/tell me what to do step by step so I don't get lost ](*,)  ?

If it's any help my video card is nvidia geforce 6800 and my monitor is a crt that goes up to 85hertz refresh rate I beleive.

---

### Post by ko_o on 2006-11-21
basicly ubuntu dapper can  install by runing live cd before, I was  tried it before upgrade to edgy.

---

### Post by wpshooter on 2006-11-21
First you might want to try downloading, burning and attempting to install from the 6.06.1 DESKTOP CD of Dapper.

If that does not work then download, burn, and attempt to install from the 6.06.1 ALTERNATE CD of Dapper.

Good luck.

---

### Post by gerkin on 2006-11-22
It sounds like the problem is the Nvivia driver.

I have a simlar Nvidia card (6600) and when I upgraded to Edgy or installed Dapper 6.06.1 I encountered the same problem,

You will need to install the Nvidia drivers.  The easiest way to fix it I found was to (first download where you can still access it) use the "envy" script from here:

[http://www.ubuntuforums.org/showthread.php?t=281823&highlight=envy](http://www.ubuntuforums.org/showthread.php?t=281823&highlight=envy)
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

### take it from me 'Tseliot' is the man!! ###

See also this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)


You will need the Dapper/or Edgy alternate CD as well (as it gives you much more flexability with the install), and the linux headers for the kernel you are using - which "emvy" needs to compile the correct driver etc.

Also.. I'm using the latest Nvidia beta driver and it works really well on my card (on Daper)

hope this helps, but if not there is heaps more on the forums about nvidia

---

### Post by gerkin on 2006-11-22
PS.  I got Tseliot's envy script from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by njzillest on 2006-11-30
Hey scott, im at comp sci class with furry ;)

Ok, so you will need to install the driver. But you dont have GUI..
HMM You have one solution. Boot into safe/non graphics mode- And use the built in browzer "lynx"
I'm sure Ubuntu comes with it. If it doesnt type in

sudo aptitude update
sudo aptitude install lynx

Lynx is a text based browzer that you can use. Use this to download the script. Once done downlaoding the script, you will have to run it. Usually directions are provided, so i recomend you use "vim" to read it. Vim is a text based non GUI text editor. 

Just cd to the directory, and run the scripts as directed. 

Hope this helped... email me if ur confused.

You can find alot of articals on how to use lynx.

---

