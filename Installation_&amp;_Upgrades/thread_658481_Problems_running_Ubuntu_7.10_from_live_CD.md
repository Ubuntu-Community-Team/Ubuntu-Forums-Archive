---
title: "Problems running Ubuntu 7.10 from live CD"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by jank on 2008-01-04
Hello!

I am a Linux noob so most of these problems is probably quite easy to solve. I have a relatively weak computer witch now runs on Windows Vista, but I wanted to try out Linux so  downloaded the Ubuntu 7.10 standard Live-CD, booted from it and checked for errors. None were found. Then I started it with the button at the top (start or install Ubuntu, or something like that). Everything started fine I got a nice picture and even from a Live-CD it runs faster than Vista. Then the problems started shoving up.

 Problems:
1: I can't access data on my hard drive when booting from the Live-CD. Do the HDD need to be formated for Ubuntu or something?

2: I can't connect to a wireless network. In fact my wireless connection don't show up at all. In the network box I have Wired connection and Modem, but no Wireless connection. My wireless card is this: Atheros AR5007EG Wireless Network Adapter

3: When I tried to play the media files that followed as examples only the introduction, where they talk about why it's called Ubuntu, works. On the two others I only get the "video" you get when playing music in Windows media player", (sorry i don't know what that is called), but no sound. Additionally I get a very high pitched tone when the sound works. Im not sure if this is my sound card, but it was the only sound hardware I could find. It is only called Sound Max Integrated Digital HD Audio. 

I haven't tried to install it yet as this PC isn't mine, but my school. Therefore i can't install any software without my schools permission and I wont get it for Ubuntu, because the school network only work with Windows computers. I will buy an external HDD and install Linux on it as my agreement with my school only prohibits me from installing new software not running it. So I might not be able to test all suggestions at once, but I will as soon as I get the HDD. I just want everything to work as soon as possible.

Thanks to everybody who will answer. 
PS: if you need any other info just ask.

---

### Post by icheyne on 2008-01-04
1. You have to mount the hard drive. On the liveCD, open a nautilus windows (the file browser). In the left margin you should see all the partitions on the harddrives listed as icons with the size next to them. Double click one to mount it, and it will change name to disk or disk-1 or something. Double click it again to browse its content.
2. You have to install ndiswrapper to make this work - as that is not supported natively by Linux. [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)
3.  Looks like this is also an unsupported sound card. You might be able to get it working, but you'll have to google hard.

Sorry I can't be much more help, but you are unlucky to have linux unfriendly hardware.

If you intend to use a live-cd regularly - I suggest you use a specialised distro - like [Puppy Linux]("http://www.puppylinux.org"). That runs perfectly from a flash drive.

---

### Post by jank on 2008-01-05
thanks for the answer. I will install Ubuntu, but i'm just waiting for an external HDD. When I started from the live CD a second time I found all my files without doing anything. I don't know why, but as long as it works im happy. Thanks for the tip regarding my network card. According the sound I found out that it stops working if I change the volume. Hope anyone have an idea for that too. Thx for all help this far.
Jank

---

