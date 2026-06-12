---
title: "Installing ubuntu on a laptop that already contains windows 7"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by ltwinner on 2010-08-20
So is it possible to install ubuntu on a laptop that is already running windows 7|? If so how do I go about it?

---

### Post by Skaperen on 2010-08-20
That depends on whether there is space available to install Ubuntu into. If Windows has partitioned the drive all for itself, that has to be changed, first, or else the Ubuntu system has to be showhorned into Windows (as files in some form, usually). I know there are tools around to do this, but I don't know if Ubuntu has them ready to use (since I don't have any need to do this, I've never looked). But I know it is possible.

---

### Post by stlsaint on 2010-08-20
Are you referring to a dual booting system? Or a fresh install of Ubuntu by removing windows. Either way please see my sig. It may say vista or even xp but the procedure is the same.

---

### Post by ltwinner on 2010-08-20
> **stlsaint said:**
> Are you referring to a dual booting system? Or a fresh install of Ubuntu by removing windows. Either way please see my sig. It may say vista or even xp but the procedure is the same.

No, removing windows 7 is not an option as it is not my laptop. I just want to install ubuntu in addition to the existing windows os.

---

### Post by Soulcage on 2010-08-20
[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/]("http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/") Make sure you drag the right hand side when you resize the partion in gparted :/ lol.

---

### Post by JohnElway on 2010-08-20
Windows 7 and Vista both contain their own partition managers so I would recommend using them as opposed to some third party software. Although I have successfully used GParted on a Windows XP laptop, I have heard that it causes many problems with other versions of Windows (particularly Vista).

---

### Post by JohnElway on 2010-08-20
Here's a good tutorial for installing Ubuntu on a Windows 7 or Vista machine:

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

FYI, it's also possible to install Ubuntu alongside Windows without ANY partitioning:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

I used a Wubi install of Ubuntu for over a year before I finally got the balls to partition. The difference between a Wubi install and a 'real' install is very small so I would recommend this method for any new Linux users who are not comfortable partitioning a hard drive.

---

### Post by bcbc on 2010-08-20
> **ltwinner said:**
> No, removing windows 7 is not an option as it is not my laptop. I just want to install ubuntu in addition to the existing windows os.

This is not a very good idea. Installing a new OS has risks and the laptop owner should probably be the one deciding what to do to it. If you are going ahead anyway, make sure you have a full backup, windows repair discs etc.

+1 on not using gparted to partition win7. 

In addition to wubi, you can run ubuntu from a CD or a USB (the USB is fastest) without having to install it on the hard drive.

---

### Post by MaXiMuSePrImE on 2011-07-28
I haven't used Linux for some time now but am trying to get back into it. I want to install Ubuntu on my Toshiba A300 Win Vista laptop without formatting the hard drive. I have partitioned the drive without any problems but cant seem to get Ubuntu to install. When I used to play around with Linux I remember that you had to install Linux first and then Windows as Windows wouldn't allow another OS once it is installed. I found this post and tried what was said on the You Tube clip but cant get it to work. The image gets to the first screen where I select English and then the next one where I tell it to install and then the screen just goes blank and nothing happens from there. Does anyone have any experience with this problem and can tell me how to fix it.

---

### Post by Blasphemist on 2011-07-28
Did you go right into installation or did you choose try ubuntu first? If you went right into installation it could be a video issue but if you choose try it first and mess around a bit you'll no if the video is working. 

This is the best step by step tutorial with screenshots that I know of. Please look at it and see if it doesn't help. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

If it is a video issue and it may well be, please see the first 3 posts of this thread. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) Some of what this thread shows is also mentioned in the link above.

---

### Post by ingeva on 2011-07-28
> **ltwinner said:**
> So is it possible to install ubuntu on a laptop that is already running windows 7|? If so how do I go about it?
Well of course I don't see the point of keeping Windows on your computer, but that's not my decision. What you need to do to install Linux as an alternative choice is to allocate space for it. Use the Windows Disk Manager to reduce your Windows partition to the minimum of you need. You'll then have free space that you can use for Linux. Just install it and the GRUB loader so you can choose the OS when you boot.

---

