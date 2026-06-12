---
title: "Installed Ubuntu as a dual-boot and now can't boot into either OS"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by doogster on 2012-03-11
I have a desktop computer with vista on it and I wanted to try Ubuntu. So I downloaded version 11.10 and installed. During the install it asked if I wanted to erase the hard drive and install or install it next to the windows software. I said next to it.... it went through its process and when done, it rebooted. Upon reboot I get an error saying something about the display resolution and it won't boot any further. I also can't figure out how to boot into windows now... it just stops at this video mode error.

I know NOTHING about Linux... is there something I can do to fix this?

I saw another post about typing something from a terminal mode or a command or something... but I don't know what those things are.

I need NEWBIE help... Please.... If I can't run Ubuntu - how can I get back and run my windows partition?

---

### Post by lrgmmc on 2012-03-11
oh. I understand your frustration. when you boot your pc does it say anything before mode not supported? also what is your monitor?

---

### Post by doogster on 2012-03-11
I never get this thing called a GRUB menu... which I think would allow me to get into Windows, yes? When I press the shift key during boot it DOES say GRUB menu at the top, but then the cannot display video mode message comes up and nothing ever happens.... if I just sit for a minute and don't touch ANY keys from when I turn the power on, the message goes away and I get to the Ubuntu desktop... I have a Dell monitor, LCD... flat panel. 

When I boot it says optimal is 1280 X 1024 60hz

What do I do next?

---

### Post by lrgmmc on 2012-03-11
sounds like yor monitor doesn't like grub's resolution. what is your video card?

---

### Post by doogster on 2012-03-11
its built into the motherboard... when I look under drivers in Ubuntu its giving me options to download drivers for NVidia

There must be something I can do to get back into Windows????

---

### Post by lrgmmc on 2012-03-11
go ahead and install the drivers and see if it helps.

---

### Post by doogster on 2012-03-11
I tried them all... no good... can't get to the Grub menu and therefore can't get into windows... I'm stuck

---

### Post by lrgmmc on 2012-03-11
open the terminal. click on the ubuntu icon on top left corner and type terminal into the search. open it and past this into it. ```
sudo add-apt-repository ppa:ingalex/super-boot-manager
``` it will ask for your password and then to click enter to accept. then do ```
sudo apt-get update && sudo apt-get install buc super-boot-manager
``` when thats done type ```
super-boot-manager
``` into terminal.

---

### Post by doogster on 2012-03-11
I'm getting command not found... are there any spaces between these letters?

---

### Post by doogster on 2012-03-11
OK... I guess I have a program now called grub installer... now what?

---

### Post by lrgmmc on 2012-03-11
double post

---

### Post by doogster on 2012-03-11
You did it!! I now get the grub menu and I can boot into windows... Thank you so much.

Now....the whole reason I even started down this Ubuntu road is because I wanted to see if I could run some old windows XP software under Ubuntu for my 6 year old...I installed wine but the exe didn't run...any thoughts? They are just some old games..the error said something about not being an executable file

---

### Post by lrgmmc on 2012-03-11
did you mark them as executable? right click on the file and properties. then permission tab and check the box allow executing.

---

### Post by doogster on 2012-03-11
yes...I tried... but its a CD Rom and it wouldn't let me change it

---

### Post by lrgmmc on 2012-03-11
since this is another topic all together. lets move to pm's. and also mark this thread as solved please.

---

### Post by doogster on 2012-03-11
Will do...please tel me where to mark it as solved

---

### Post by lrgmmc on 2012-03-11
Click thread tools above the first post.

---

### Post by doogster on 2012-03-12
I've been sending you PM's Irgmmc.... not sure if you are getting them because when I check my sent folder it says zero...

---

