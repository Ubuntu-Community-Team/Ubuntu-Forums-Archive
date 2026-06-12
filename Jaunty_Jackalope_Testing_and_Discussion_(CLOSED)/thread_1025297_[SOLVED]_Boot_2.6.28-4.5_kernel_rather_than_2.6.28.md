---
title: "[SOLVED] Boot 2.6.28-4.5 kernel rather than 2.6.28-3"
date: 2008-12-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by inxygnuu on 2008-12-29
Hello I am currently testing Jaunty and I want to boot into the newest kernel I did not install GRUB with it, because I did not any trouble. So I can boot fine, but I want ***_[COLOR="Red"]BLEEDING EDGE[/COLOR]_***:o. IS there a fix? when I change everything in menu.lst from -3 to -4.5, it says "file not found" whats the fix?

---

### Post by Slug71 on 2008-12-29
You do not need to touch anything in Grub. Grub is installed by default and the new Kernel will make its own entry into menu.lst.
Just install 2.6.28-4.5 in Synaptic Package Manager.

---

### Post by inxygnuu on 2008-12-30
It said it was already installed. So I simply edited the image and booted. I will change that back soon, I am in windows right now (the comp I am on is on Ubuntu server, I am trying to setup a thin client)

---

### Post by Slug71 on 2008-12-30
> **inxygnuu said:**
> It said it was already installed. So I simply edited the image and booted. I will change that back soon, I am in windows right now (the comp I am on is on Ubuntu server, I am trying to setup a thin client)


Got ya. menu.lst should be edited to 2.6.28-4 not -4.5. ;)

---

### Post by inxygnuu on 2008-12-30
Okay, thanks. I will try it soon. Is that all?

---

### Post by autocrosser on 2008-12-30
That'll work nicely.....

---

### Post by inxygnuu on 2008-12-30
> **autocrosser said:**
> That'll work nicely.....

WOW! just that. So, how many people post in this forum? Where i am it is 12:22 am, so that may mean something. I will tell the results in a while. (windows installation, UGH!)

---

### Post by autocrosser on 2008-12-30
I'd say a couple of hundred total--about 50 regulars...I've been doing this starting with Breezy Badger---seems like a hundred years ago......Been in computers for over 30 years.

Started dabbling in Linux in the late 90's

---

### Post by inxygnuu on 2008-12-30
OH NOES! Me just realized something! Windows installation may = WIndows bootloader on MBR! All of may work may be ruined! [-o<[-o<[-o<[-o<

---

### Post by autocrosser on 2008-12-30
OUCH--if you are reinstalling Windows, it will overwrite your MBR.

There is info to regain your Grub--look in the tutorial section.

---

### Post by inxygnuu on 2008-12-30
we will see, if it at least has it where I can boot into GRUB, I will be happy. Where is the tutorial section?

---

### Post by inxygnuu on 2008-12-30
It did. stupid Windoze, so greedy, even jaunty asked. All M$ thinks about is keeping power. This can be done by cutting off Linux from the boot loader, making the user want to go back to Winblows.

****!
3v4n

---

### Post by inxygnuu on 2008-12-30
Actually, I am going to start dedicating more of my time to finding out how we can get all software to run on wine, that way we can blow winblows! :mad:

Just really angry:mad:,
3v4n

---

### Post by autocrosser on 2008-12-30
Tutorial forum is here: [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

Just search for reinstall Grub on MBR...

---

### Post by autocrosser on 2008-12-30
I'm all Linux here--even my router is Linux....

---

### Post by ShirishAg75 on 2008-12-30
autocrosser, 
 what do you mean? Do you mean busybox or do you mean like one of netgear's open-source routers?

---

### Post by autocrosser on 2008-12-30
Using one of the Linksys 300 series "N" routers--had the option at the time for Linux "underpinnings" & took it.........Now Linksys is not advertising Linux in anything they offer---most likely due to the lawsuit pending........

---

### Post by ShirishAg75 on 2008-12-30
I know what you mean 

[http://www.guardian.co.uk/technology/blog/2008/dec/12/cisco-fsf-opensource](http://www.guardian.co.uk/technology/blog/2008/dec/12/cisco-fsf-opensource)

[http://www.fsf.org/news/2008-12-cisco-suit](http://www.fsf.org/news/2008-12-cisco-suit) 

[http://www.dslreports.com/forum/r21569025-FSF-and-the-CiscoLinksys-WRT54G-lawsuit](http://www.dslreports.com/forum/r21569025-FSF-and-the-CiscoLinksys-WRT54G-lawsuit)

It would be interesting to see what happens there.

---

