---
title: "Nvidia Driver HELL 10.10  Meerkat  HELP!!!"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by Noobjob on 2011-04-27
Hello, I've benn working on this problem for the last few nights and it's driving me crazy...
 
All I want to do is install the best working Nvidia driver for my gtx460 SE 1G card(using the additional current version driver makes the system crash when in 3d games).
 
I'm really looking for a not so complicated way of installing the driver I need and having it run and work like it should. Any idea's?
 
I've tried ppa(don't really understand how it works)
 
Also tried from root: sudo sh nvidia blah blah blah.run

---

### Post by realzippy on 2011-04-27
Welcome.....*which* nvidia-driver do you use?

---

### Post by Noobjob on 2011-04-27
> **realzippy said:**
> Welcome.....*which* nvidia-driver do you use?
 
Thanks for the reply...
 
I've downloaded the 270.41.06 but I have not gotten it to work. Is there a better one?
 
The one I was using when the system would crash was the current version(whatever that was it didn't actually say?)

---

### Post by Noobjob on 2011-04-27
sudo sh failed for that driver (270.41.06)

---

### Post by Noobjob on 2011-04-27
I don't mind using terminal or root but I would like it to work and not ruin my os.

---

### Post by realzippy on 2011-04-27
Have you **succesfully** added [xswat ppa]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates") to your system's sources?
[I]...I've tried ppa(don't really understand how it works)
[/I]
if so,the "current" driver in system/admin/hardwaredrivers
becomes the 270.xx,so no need to install manually,means "sudo sh aso..."

---

### Post by Noobjob on 2011-04-27
> **realzippy said:**
> Have you **succesfully** added xswat ppa to your system's sources?
*...I've tried ppa(don't really understand how it works)*
 
if so,the "current" driver in system/admin/hardwaredrivers
becomes the 270.xx,so no need to install manually,means "sudo sh aso..."
 
Is there a way of checking if it was added correctly?

---

### Post by realzippy on 2011-04-27
...a few.
Easiest:
Open "nvidia-settings" and check the driver version reported.

---

### Post by Noobjob on 2011-04-27
> **realzippy said:**
> ...a few.
Easiest:
Open "nvidia-settings" and check the driver version reported.
 
Terminal stated "the program nvidia settings is currently not installed. You can install it by typing: sudo apt-get install nvidia-settings"

---

### Post by Noobjob on 2011-04-27
should i do that?

---

### Post by realzippy on 2011-04-27
If nvidia-settings is not installed,also no nvidia-driver is installed.
Suggest to
1. update your system;paste into terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

When done,reboot.

2.Add xswat ppa:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

When done,again run:
```
sudo apt-get update && sudo apt-get upgrade
```

Then go to System-Administration-HardwareDrivers and install the
"current" driver,which now is from xswat (270,blah).

3.reboot & pray

If something goes wrong,boot in recovery mode (press shift during boot),
start low graphics session and remove the driver...

---

### Post by Noobjob on 2011-04-27
Ok, I had to swap my eth cable from my win comp to my 10.10 comp sorry for the wait. 
 
Anyways, before you're recent post I activated the driver under "additional drivers" and it said to reboot and I did. It seemed to work, but when I ran the game "Torcs" the system crashed and I had to reboot.

---

### Post by realzippy on 2011-04-27
...so *which* driver did you install then?(check nvidia-settings)

---

### Post by Noobjob on 2011-04-27
> **realzippy said:**
> ...so *which* driver did you install then?(check nvidia-settings)
 
270.41.03 is the one it's using now. It hasn't crashed running Nexuiz? But idk. Do you know of a furmark type test for 10.10 so I can tell if it's running right? Thanks.

---

### Post by realzippy on 2011-04-27
There is no furmark for linux I guess.
You could install natively under linux Doom3 eg,and run the in-game
fps benchmark.
Also there is for linux:
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

Very basic tool is:
[http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)
..just type in terminal
```
glxgears
```

Btw,if you open nvidia-settings,and no error occurs,then your driver
will work.If some games do not,it is very likely due to the game,not the nvidia driver.
Also you could set up your compiz cube,wobbly windows,skydome backround,aso.,which will only work when the nvidia driver works fine.

---

### Post by Noobjob on 2011-04-27
> **realzippy said:**
> There is no furmark for linux I guess.
You could install natively under linux Doom3 eg,and run the in-game
fps benchmark.
Also there is for linux:
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)
 
Very basic tool is:
[http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)
..just type in terminal
```
glxgears
```
 
Btw,if you open nvidia-settings,and no error occurs,then your driver
will work.If some games do not,it is very likely due to the game,not the nvidia driver.
Also you could set up your compiz cube,wobbly windows,skydome backround,aso.,which will only work when the nvidia driver works fine.
 
thank you for your help! I've been running Nexiu this whole time on ultimate settings and it's seems fine. I'll post again if it gives me anymore trouble thanks.

---

### Post by realzippy on 2011-04-27
You are welcome.
Please mark thread as "solved" (threadtools)...

---

