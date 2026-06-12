---
title: "i dont know what to do"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by newbee6 on 2011-04-22
i have one of those old imac where all the hardware is in monitor. im trying to get it running with a OS that takes up less room, its for my daughter. 
i installed ubuntu 6.06.2 on it and deleted the mac os. i go to start it up and it goes to a white screen then a black screen and a long list of white text... well at the end of it it assked for log in so i typed it. then it asked for password so i typed it. then this is wat poped up and where im stuck at (and my usuer name is Xellia):
 
Last login: Mon Aug 27 05:17:49 1956 on tty1
Linux xellia 2.6.15-51-powerpc #1 Thu Dec 6 20:26:26 utc 2007 ppc GNU/Linux
 
The programs included with the Ubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.
 
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
xellia @xellia:~$

---

### Post by marin123 on 2011-04-22
you are missing window manager :)

you sucessfully logged in and you can do whatever you want with command line...

why dont you download newer lubuntu or xubuntu and try that?

---

### Post by newbee6 on 2011-04-22
i tryed to download new version.. i burned cd right... i boot from cd rom and this is what i got... 
 
default catch!, 
 
at the end of that there was a weard little tilted c like line, thats the best i can explain it

---

### Post by Bucky Ball on 2011-04-22
When you boot up with the hard drive install and get to the command prompt, try typing:

```
startx
```... if that doesn't work, try:

```
sudo startx
```This will make certain the desktop environment is missing (your issue is no proof so far that it is). If it doesn't go to a desktop please take note of the message you get and report back. ;)

---

### Post by newbee6 on 2011-04-22
> **Bucky Ball said:**
> When you boot up with the hard drive install and get to the command prompt, try typing:
 
```
startx
```... if that doesn't work, try:
 
```
sudo startx
```This will make certain the desktop environment is missing (your issue is no proof so far that it is). If it doesn't go to a desktop please take note of the message you get and report back. ;)
 its asking for a password after i typed "sudo startx"

---

### Post by newbee6 on 2011-04-22
so anyone knows what to put for password? lol

---

### Post by marin123 on 2011-04-23
what happens with just startx?

---

### Post by mörgæs on 2011-04-23
You shouldn't struggle with 6.06. It is obsolete.

Here are the 10.04 and 10.10 ISO's for powerpc:
[http://cdimage.ubuntu.com/ports/releases/10.04/release/]("http://cdimage.ubuntu.com/ports/releases/lucid/release/")
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)

Best is to use the alternate version.

By the way, a more precise title for the thread would help you to get a faster answer.

---

### Post by coffeecat on 2011-04-23
> **newbee6 said:**
> so anyone knows what to put for password? lol

Your login password.

By the way, those old see-through iMacs didn't have much memory unless you added some. How much RAM does it have? There may be insufficient for the GUI to be able to start up.

---

### Post by newbee6 on 2011-04-23
to answer all of you.
 
when i just put startx it said...  bash: startx: command not found
 
i will try the 10.4... the 10.10 is the one i cant get to work, and thank you about title next time i wil keep that in mind.
 
i dont know how much memory i have in it but i erased the mac os which it was using os 10.2.8, so i was figuring it might hold just ubuntu. i dont really care how fast it runs, its for my 6yo to get on her school website. i just need an os new enough to use wifi usb because this computer will be on the oppisit side of the house where my modem is, and running an ethernet cable will be almost impossible
 
oh and i tryed my log in password but it didnt work.  when i typed y password in it said... sudo: startx: comand not found

---

### Post by marin123 on 2011-04-23
if you are willing to make UTP cable, you just need enough cable, 2 RJ-45 connectors and 15 minutes spare time. max length of cable is 100 m.

you can find out how much ram you have. you can boot ubuntu and in command line type:
```
free
```

that will tell you total ram size, used and free.

---

### Post by newbee6 on 2011-04-23
i checked to see the memory, i typed free and this is what i got, not sure how to read it so i dont understand how much i have or if i have enough.
 
 
.................. total....... used..... free...... sharedd... buffers.... cahed
mem........... 93744.... 30064... 63600......... 0........ 1052...... 17600
-/+ buffers/cache:......11324... 82420
swap.......... 273024...... 0...... 273024
[EMAIL="xellia@xellia:~$"]xellia@xellia:~$[/EMAIL]
 
 
and sence now im trying to get my computer up and running, my enternet isue isnt quite an isssue right now lol

---

### Post by marin123 on 2011-04-23
> **newbee6 said:**
> i checked to see the memory, i typed free and this is what i got, not sure how to read it so i dont understand how much i have or if i have enough.
 
 
.................. total....... used..... free...... sharedd... buffers.... cahed
mem........... 93744.... 30064... 63600......... 0........ 1052...... 17600
-/+ buffers/cache:......11324... 82420
swap.......... 273024...... 0...... 273024
xellia@xellia:~$


total: 92 MB of RAM

xubuntu takes at least 128 to have window manager.

you could try puppy linux, but i dont think that will work either.

what you can do is buy more ram. but the problem is if that ram is still manufactured...

you can run ```
sudo lshw -class memory
```

and see what manufacturer and model of ram and see if you can buy more...

---

### Post by newbee6 on 2011-04-23
Well thank you for your all your help, i dont know what im going to do with this computer now but i will think of something.

---

### Post by ClientAlive on 2011-04-23
I can offer some links to information about other Linux Distributions. Hope it helps the cause . . .

Puppy Linux:

[http://wiki.laptop.org/go/PuppyLinux](http://wiki.laptop.org/go/PuppyLinux)  ("Last edited on 12:45, 4 February 2011")

DSL:

[http://wiki.laptop.org/go/Damn_Small_Linux](http://wiki.laptop.org/go/Damn_Small_Linux)

Take note of the third bulleted line from the bottom. ("Last edited on 00:43, 19 December 2008.")

DeLi Linux:

[http://wiki.laptop.org/go/DeliLinux](http://wiki.laptop.org/go/DeliLinux)

Says it runs on 64 mb ram ("Last edited on 05:24, 26 March 2009")

Here is a list of disributions with columns for how much ram needed, how much hard drive space, and other things. There are many in this list that require much less ram than what you have. This list may be a few years old but may still be relevant or may at least provide some jumping off points for further investigation.

[http://www.goodbyemicrosoft.net/e107_plugins/content/content.php?content.5](http://www.goodbyemicrosoft.net/e107_plugins/content/content.php?content.5)

The only thing I could find with dates on this, last, link are:

"References:
Brockmeier, Joe. "Linux distros for older hardware." February 24, 2006.
Fosdick, Howard. "Reincarnating a discarded laptop with Linux." August 1, 2006.
Provan, Liam. "How to revive an old PC." June 23, 2007."

Hope this helps. Don't give up - there is a Linux for you!

:)

---

### Post by marin123 on 2011-04-24
just for the record, whatever os you install, you wont be able to see flash content.. i have a computer with 128 MB ram and no way that will display flash...

---

### Post by dino99 on 2011-04-24
hey guys, as i read this output "93744" you might consider that number as bytes, so translated it means 93 Kb, thats very very very low. Too low to be able to run a graphic interface, you will be stuck with text mode.

[http://lightlinux.blogspot.com/2009/07/text-mode-linux-applications.html](http://lightlinux.blogspot.com/2009/07/text-mode-linux-applications.html)

[http://unix.stackexchange.com/questions/5733/distro-lightweight-and-easy-to-install](http://unix.stackexchange.com/questions/5733/distro-lightweight-and-easy-to-install) 

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by marin123 on 2011-04-24
you might consider it as bytes, but that arent bytes. i thought we solved this.

---

### Post by shashanksingh on 2011-04-24
sudo apt-get install xserver-xorg-core gnome-core

install this with all the dependencies it asks for.
U'll get a simple GUI which u can then start using
sudo startx

---

### Post by lisati on 2011-04-24
> **marin123 said:**
> you might consider it as bytes, but that arent bytes. i thought we solved this.

That would mean I have 2Tb RAM on my laptop. I don't think so....... :D

---

### Post by coffeecat on 2011-04-24
> **dino99 said:**
> hey guys, as i read this output "93744" you might consider that number as bytes,

Er, no. From man free:

> -k     Display the amount of memory in kilobytes. This is the default.


It sounds as though the OP ran free without any options so the 93744 would be kilobytes, and marin123 would be right in saying that's approx 92MB. Which would also be about right for one of those old CRT iMacs.

I haven't seen a machine with only 92 KB RAM since the days of those toy computers in the 80's. Could you run even MSDOS3 in only 92KB? :?

---

### Post by coffeecat on 2011-04-24
> **lisati said:**
> That would mean I have 2Tb RAM on my laptop. I don't think so....... :D

Well, you never know. Perhaps the manufacturer was being generous on that day. :)

Out of interest, what is the output of free on yours? My desktop with 4GB RAM shows:

```
$ free
             total       used       free     shared    buffers     cached
Mem:       4057132    1220612    2836520          0      87928     528468
-/+ buffers/cache:     604216    3452916

```Which means that "free" without options is displaying in KB for me. Apologies if this is slightly off-topic, but I don't think it is. It would appear that the OP has insufficient memory for a heavyweight desktop so  it's important to get the figures right, imo.

---

### Post by 3rdalbum on 2011-04-24
Don't bother suggesting DSL or Puppy Linux. The OP is using a PowerPC iMac, and therefore needs a PowerPC distribution.

92 megabytes of RAM is too little. My iMac had 128 megabytes of RAM, running Ubuntu 5.10, and it was constantly on the verge of running out of swap and RAM. So ridiculously slow because it was swapping non-stop. You could put more RAM in (expensive, probably, because it's very old type of RAM) or dump it. I dumped mine.

---

### Post by mörgæs on 2011-04-24
Running 

```
free -m
```lowers the level of confusion :-)

---

### Post by ClientAlive on 2011-04-24
> **3rdalbum said:**
> Don't bother suggesting DSL or Puppy Linux. The OP is using a PowerPC iMac, and therefore needs a PowerPC distribution.

92 megabytes of RAM is too little. My iMac had 128 megabytes of RAM, running Ubuntu 5.10, and it was constantly on the verge of running out of swap and RAM. So ridiculously slow because it was swapping non-stop. You could put more RAM in (expensive, probably, because it's very old type of RAM) or dump it. I dumped mine.


Thank you. I was unaware of that. I will remember that in the future.

As far as finding old components - I see old stuff really cheap on craigslist all the time. Just saying.

---

