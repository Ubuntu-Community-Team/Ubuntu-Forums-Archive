---
title: "X Server Error with ATI GeCube Radeon 7000 and Integrated Card"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by Austin6641 on 2007-03-05
I have recently installed Ubuntu 6.10 from the alternate CD because of the X Server errors. I thought that the errors would just be in the install, but I found out that even starting Ubuntu would give me these errors. I get a message saying "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" And when I select yes or no it gives me this message: "The X server is now disabled. Restart GDM when it is configured correctly." I have tried making new CDs, 6 to be exact, and nothing I try works. Also, I have tried both my integrated card and the PCI one, both give me the error. By the way, my computer specs are:
512 MB of RAM
40 GB hard drive
GeCube Radeon 7000 graphics card
Intel Corperation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
Intel Pentium 4 2.4 GHz
Here are links to my computer and graphics card for more detailed specifications:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2719679&CatId=1873]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2719679&CatId=1873")
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2155016&CatId=319]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2155016&CatId=319")

---

### Post by Austin6641 on 2007-03-06
I am still looking for some help...

---

### Post by confused57 on 2007-03-06
> **Austin6641 said:**
> I am still looking for some help...

See you're still not getting any responses...you thing you might try is open your /etc/X11/xorg.conf file, go down toward the bottom of the file and DefaultDepth 24...change to Default Display 16...I really think you need video driver "i810" for this controller.

Also, when you did the command "lspci", did it give a BusID for you integrated video controller...if so, does this match the BusID for your integrated controller in Video card section of your xorg.conf file?

---

### Post by Austin6641 on 2007-03-06
When I put in "lspci" I got the my integrated card is "00:02.0" and my PCI card is "02:0a.0". And in the xorg.conf it says that the BusID is 0:2:0.
**EDIT!!!!**
After I edited the xorg.conf file to say 16 instead of 24 I got the system running! But won't this affect the quality of my graphics? Since I plan on using this PC as a DRV. Also, how can I change to my PCI card now because I am using the integrated card right now, but to hook my TV up to the computer I need the PCI card.

---

### Post by confused57 on 2007-03-06
> **Austin6641 said:**
> When I put in "lspci" I got the my integrated card is "00:02.0" and my PCI card is "02:0a.0". And in the xorg.conf it says that the BusID is 0:2:0.
**EDIT!!!!**
After I edited the xorg.conf file to say 16 instead of 24 I got the system running! But won't this affect the quality of my graphics? Since I plan on using this PC as a DRV. Also, how can I change to my PCI card now because I am using the integrated card right now, but to hook my TV up to the computer I need the PCI card.
Glad you were able to get your integrated graphics controller working...yes, you'll get much better performance with the ATI card...I'm not an expert with setting up proprietary drivers for ATI or Nvidia cards, so I can't really help you there.
You'll need to do a forum search or Google search to find an answer, unless someone happens to see your thread first.
Something like this thread may help:
[http://www.ubuntuforums.org/showthread.php?t=221320&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=221320&highlight=ATI)

Good luck with getting your ATI card working.

---

### Post by Austin6641 on 2007-03-06
Thanks for all your help. I will Google and search to forum for an answer to my next problem.

---

### Post by Routly on 2007-03-07
Hey Austin6641, i have the exact same problem as you, caused by the same ati video card. but i just got into this ubuntu thing, and don't know enough to fix the problem. After you disable the GDM you have to login on a black screen (rather then ubuntu's nicer Login). I enter my login, then goes to routly@routly-desktop:`$_ ,,, what do you do from here to load it back up,, and once that is done,, how do you fix the initial graphic card problem,  and attempt what  confused57 suggested  "open /etc/X11/xorg.conf file" and make changes.

iv been looking hard for how to use commands in the terminal menu,, and found nothing on booting ubuntu desktop,,please help

Thanks

---

### Post by Austin6641 on 2007-03-07
I have still yet to find out how to use my ATI card, but if you have an internal card, like I do, then just fallow the directions confused57 gave me.

---

### Post by Routly on 2007-03-07
yah, im loading it on my internal vga and this is as far as i can get,, the ati card will get stuck everytime is a kernal synching error..., but how do you open this -> /etc/X11/xorg.conf  file. i enter that and get permission denied.. entering "lspci"will get me a bunch stuff but i don't know how to change any files (to 16 instead 24) mine says, that the ati radeon 7000 is on the line of 0:1:00.0 
*note that my screen is cut off on the left for some reason and there could be more numbers on this line

---

### Post by Austin6641 on 2007-03-07
To open up the xorg.conf file enter this:
> sudo nano /etc/X11/xorg.conf
And when you are done just hit CTRL+X, then hit Y, and lastly, hit ENTER.

---

### Post by Routly on 2007-03-07
ok thanks,, to make sure i don't do something i don't want to,, when you changed 24 to 16, was it the option under "default depth"  in the "screen" section.

---

### Post by Austin6641 on 2007-03-07
I am pretty sure that is where it was.

---

### Post by Routly on 2007-03-07
I wish i could say that worked for me.. thanks anyway,, if theres anything else anybody can do for me , it would be appreciated.

---

### Post by Routly on 2007-03-07
ended following the steps from this post,,

[http://ubuntuforums.org/showthread.php?t=231811](http://ubuntuforums.org/showthread.php?t=231811) 

worked well,, now just need for the ati card to work

---

### Post by Austin6641 on 2007-03-07
I got my ATI card working... The only problem? I am now using Fedora instead of Ubuntu. I did not have to edit anything, it just worked naturally. Yet another problem? I still need to figure out how to get my computer to use my TV as a screen. But that is a question for another forum.

---

