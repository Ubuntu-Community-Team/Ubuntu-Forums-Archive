---
title: "xorg.conf missing file?"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by ComputerGuy56 on 2007-02-28
I've tried to use the break=bottom thing but when i tried loading the xorg.conf, it didn't show anything. I tried opening the files somehow but it didn't find it. By the way, can someone repost all the directions, I found the post but I can't find it now.:(

---

### Post by Stemp on 2007-02-28
I don't really understand your problem, but you want to edit your xorg.conf ? 

So open a terminal and type this command :
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by ComputerGuy56 on 2007-02-28
Sorry more info. I'm trying to run the livecd for Ubuntu and I get a major blue and red screen and it says stuff about my V_BIOS for my video card. This has happend to other people and they said to press F6, change break=bottom, then type some directory, then edit the xorg.conf and from ATI to radeon. But when I go to the path, it's just a blank editor, nothing is written.
Can you tell me how to make a pic. so I can take some to show you?
WinXP
1.7 GHz Intel Celeron
256 MB Ram
40 GB Hardrive

---

### Post by Stemp on 2007-02-28
So I was right, I didn't understood your problem at all ;)

---

### Post by ComputerGuy56 on 2007-02-28
SO THEY GAVE ME THE WRONG LOCATION ERRRRRRRR.:confused: 
Thankyou

---

### Post by ComputerGuy56 on 2007-02-28
I tried the directory. Didnt work. It said it couldn't find the file. The other directory I got was "chroot /root nano etc/x11/xorg.conf" Atleast it finds the file but in the text editing thing, it's blank, on the bottom it says [NEW PAGE] so something's messed up. Please help as i'm getting really mad:confused:

---

### Post by ComputerGuy56 on 2007-02-28
C'mon guys. I know I wasn't the ONLY guy with this problem. Can the people that fixed it tell me how? Please?

---

### Post by Stemp on 2007-02-28
BTW it's not etc/x11 it's /etc/X11

---

### Post by ComputerGuy56 on 2007-02-28
It HAS to be uppercase? Can you give me exactly, I'm sorry but I just really want to get Ubuntu on my computer.

---

### Post by Stemp on 2007-03-01
Yes the X HAS to be uppercase :

/etc/X11/xorg.conf

---

### Post by ComputerGuy56 on 2007-03-01
Wow, this is starnge. When I found the driver section. I looked and where it showed which monitor or whatever and it didn't show my ATI card. Instead it showed my old default video card. I didn't change that but still chnged the (well it started as I380 or something) to radeon. Then I tried ATI. Still didn't work, do I have to change the line where it shows the video card im using, then the Driver?
By the way, I found out it said it couldn't start the X server if that helps...

---

### Post by Stemp on 2007-03-01
Ok I think there is really something going wrong.
IMHA try to run **dpkg-reconfigure xorg-server** to get a good xorg configuration

---

### Post by ComputerGuy56 on 2007-03-01
And after that i'll try again. Thanks. And if something goes wrong i'm coming right back.:lolflag:

---

### Post by ComputerGuy56 on 2007-03-01
Let me give you as much info as possible in this post.
So I pressed F6, break=bottom, blah, then I typed indpkg-reconfigure xorg-server
It said it's missing. I am not using the server version of Ubuntu. I'm using the desktop version(trying atleast). I HAVE to use my ATI Radeon 9250 Video card because if I used my default video card, on startup, the monitor would get no signal. But when it sounds like a fan slows down in my computer or something, the monitor gets conection. And the ATI always has connection. When it gets to the command line it says something like tty: jobs disabled. But I dont think it matters since it still works. Maybe if you can PM me your AIM, ICQ, or MSN, we can talk through there.(Though I doubt it for some reason)

---

### Post by ComputerGuy56 on 2007-03-01
Wait, you mean type this:
```
sudo dpkg-reconfigure xserver-xorg  
```
?

---

### Post by Stemp on 2007-03-01
Yes

---

