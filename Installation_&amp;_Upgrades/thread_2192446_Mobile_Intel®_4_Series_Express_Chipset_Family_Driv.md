---
title: "Mobile Intel® 4 Series Express Chipset Family Driver"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by stompitude on 2013-12-07
[SIZE=3]Hello.

Just to start this post I am completely new to Linux/Ubuntu I have decided that I would test this OS out, as after many years of being a heavy windows user with the release of the abomination that is Windows 8, I now feel forced to look for a replacement. 
While I work in the software industry we provide Vehicle Tracking Software via SaaS I feel a little bit of warmth toward the open software movement and so Linux has to be my first port of call.

Now I am playing around with what is best described as a standard £300 laptop, there is nothing special about it, however I really wanted to play around with the OS for a few days get a feel for it and try to see if I can get all of my applications running as smooth as possible.

Now while there are no issues in getting all the software that I use for work to run on Ubuntu, before I install on my desktop which I use less for work and more for games I really wanted to make sure that I can get everything running on this laptop before making the conversion on my main machine.

Now to my question - this machine has Intel's Mobile 4 Series Express Chipset Family built into the motherboard and I know that on a clean windows install with all the latest updates/drivers install I can play games like world of warcraft with some tweaking to the system here or there, at around 25-30 FPS (note: I don’t really play on this machine but I wanted to get a benchmark before I try to get it to work on Ubuntu).

So I do a clean install of Ubuntu I then use the following command:[/SIZE]
 [SIZE=3]```
glxinfo | grep rendering
```

And I get a message in terminal on how to (what I assume is to install the drivers) as once I complete the process when I run the, 

```
glxinfo | grep rendering
```

command again it then shows 'direct rendering: Yes'.

I then install and set-up Wine -> Change the .config file to run the game using openGL rather than Direct3D -> And perform the tweaks to regedit, for the WoW application

Once the whole process is complete, despite the fact that it is a far longer process than when running in windows,  my FPS is still far lower that when running natively in windows 7

So I just want to ask is there a driver supplied via intel for the chipset? or have I even installed the driver?

If so is there a command that I can use in terminal to download/install the driver as to me while I expect to see a slight FPS drop using Ubuntu/Wine as MS is so secretive of there API and Wine is a let's see if we can make applications run using an API we create, I feel that there is an issue or something I am not setting up correctly.

I have read that you need to check the amount of VRAM that wine has allocated to the GPU however I cannot find clear instructions on how to check / remedy this issue.

I am confident that the Wine install / game install are correct - I just feel like there is an issue with the driver for the onboard GPU chipset.

Anyway any help regarding this matter will be greatly appreciated.

Regards.

Adam
[/SIZE]

---

### Post by Bashing-om on 2013-12-08
stompitude; Hi ! Welcome to the forum .

Intel chipsets are well supported - out of the box - rarely requiring any alterations.
 To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```
You can see if you have direct rendering working by typing:
```

glxinfo | grep direct

```
To see how many frames per second your video card is putting out, run the following command:
```

$ glxgears -info

```
(also starts the glxgears graphic)

Other than this, I am not much help. I do not run wine and am not a big gamer. Others with the experience will have to advise further.

I Hope this is
[INDENT][INDENT]a bit of help
[/INDENT][/INDENT]

---

### Post by zobisch on 2013-12-08
Windows does still have some performance lead over Linux for gaming right now (Come on SteamOS developers!) but there are some things you can do that will help. Installing the latest Mesa 10 drivers will drastically help. 

install of trying to compile your own, I would go here [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

There is a link to a forum at the very top that will give you details on installing the PPA and testing it. Also the Phoronix groups are better suited to gaming and graphics HW on Linux IMHO. 


Don't give up, it'll get better.

---

