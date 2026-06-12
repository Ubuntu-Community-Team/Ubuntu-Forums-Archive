---
title: "Stuck at login, 9.10 (Newbie)"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by ReneBL on 2009-11-13
Hello fellas

Im totally new to the forums and to linux. I just recently decided to try out linux myself for the first time. 
At first i was very impressed by the overall feel of the system, but ive run in to a lot of trouble, and now im simply stuck. I cant login. Ive been stuck at this point to times now. First were i tried to install ubuntu alongside windows and i ended up stuck. And now where i installed it as the computers only OS. 

The thing is. I wanted to update the graphics driver, so naturally i went to the hardware driver updater. (yes no terminal use, as i said, newbie)

It found a propritary (correct?) driver that was good for my ATI card. naturally i installed and rebooted as requested.

The thing is, now i cant login. I dont get the usual login screen its like its stuck in some kind of universal terminal. I get these 2 lines:

ubuntu 9.10 rene-laptop tty1

rene-laptop login:

And on top of this they kinda "blink" like there is some kind of malfunction, plus i cant write properly (takes like 3 times to get it to write a letter)

I managed to start it in recovery mode when i had 2 OS on the computer, where i got to the same 2 lines, but without the strange "blinking".
Here i was able to login, i surpose, but i never left this terminal.... And since i have no clue about terminal use yet this is kinda useless for me..

OK. What should i do?

Im pretty much on the verge of giving up and returning to the OS that i was fleeing from (Windows obviously)


On top of this, this time i only have linux on the computer, and i dont know how to start it in recovery mode, so now i cant even get past the "blinking" ****, so i cant even log in in this "universal terminal" or whatever.
This ended up a bit messy, and unstructured, im just a bit annoyed since ive worked on this pretty much all day, and at this point i cant do jack.

---

### Post by seenthelite on 2009-11-14
You could try logging in as root not your user name, but maybe you should consider reinstalling windows and using Ubuntu with the live CD and become more familiar with it before using it as your main OS. It is worth the effort.

---

### Post by CoryThompson on 2009-11-14
I had the same issues when i started. Although the screen was flashing and when it flashed black wouldn't allow me to type which made it impossible to get my password right. 

Start again, reinstall ubuntu, i assume just starting out you have no important files (correct me if i'm wrong). Your lucky and have got a ATI graphics card, I would install Envy, And don't worry ill run you through it.

Open terminal (Applications -> Accessories -> Terminal) and type 

```
sudo apt-get install envyng-core
envyng -t
3
```

Reboot and you should be good. If the first command doesn't work you might may need to run
```
 sudo apt-get update 
```

Hope this works :)

---

### Post by ReneBL on 2009-11-14
I dont have anything on there yet, that i dont have elsewhere, correct.

So i should not try installing the driver for the graphics card that the system suggests? ever?

I never imagined that drivers would be such a big issue in linux

---

