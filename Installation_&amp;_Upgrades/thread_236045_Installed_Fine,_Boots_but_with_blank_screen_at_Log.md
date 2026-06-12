---
title: "Installed Fine, Boots but with blank screen at Log on"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by SuperBeaver on 2006-08-14
Hi

I've tried searching for similar threads but they become so convoluted i was hoping someone might have a solution by now.

I installed Breezy Badger on my laptop that has some sort of ATI mobility graphics card (i will get the exact model if neccesary - i know it's not a new one).  The installation went fine, however on booting the screen just goes blank.  If i press Ctrl+Alt+F1 i come to a command prompt that allows me to log in.  However If i go back to the graphical display with Ctrl+Alt+F7 the screen is still blank.  The command prompt seems to work fine so  i can do whatever i need from there.  

Just so you know, i learn fast but i am very new to this.

Thanks.

Andy

---

### Post by Macrorip on 2006-08-14
Hope it's cool if I jump on your post. I'm having the same problem. I been reading and think it's a display driver problem. I tried loading the Nvidia driver and the Vesa driver from Ubuntu but to no avail. What's the command to access my cd rom drive? I have the disk and can install it from there.

---

### Post by confused57 on 2006-08-14
> **SuperBeaver said:**
> Hi

I've tried searching for similar threads but they become so convoluted i was hoping someone might have a solution by now.

I installed Breezy Badger on my laptop that has some sort of ATI mobility graphics card (i will get the exact model if neccesary - i know it's not a new one).  The installation went fine, however on booting the screen just goes blank.  If i press Ctrl+Alt+F1 i come to a command prompt that allows me to log in.  However If i go back to the graphical display with Ctrl+Alt+F7 the screen is still blank.  The command prompt seems to work fine so  i can do whatever i need from there.  

Just so you know, i learn fast but i am very new to this.

Thanks.

Andy
I'm not familiar with laptops, here's something that may help, I don't know what the bootup arguments accomplish, just a guess on my part:
[http://www.ubuntuforums.org/showthread.php?t=142070&highlight=noapic](http://www.ubuntuforums.org/showthread.php?t=142070&highlight=noapic)

The above is probably not your problem, it may just be a matter of reconfiguring your xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

---

### Post by SuperBeaver on 2006-08-16
Thanks for the replies.  It could be that i just need to update the OS but i currently don't have internet access so i'll have to wait until the end of the month to give that a go.  

I did find out what graphics card i own if it's any help.  IT's pretty old but it's a S3 Savage8 GFX integrated in KN266.  So the make is savage.  I think the problem is the xserver but i do not get any error messages showing up.  Just a blank screen.

thanks

---

### Post by avtolle on 2006-08-16
SuperBeaver: have you tried typing sudo dpkg-reconfigure xserver-xorg from the terminal you can access by typing ctrl+Alt+F1, and proceeding from there? I would suggest that if you haven't done this, you go ahead and try. Be sure, at the appropriate time, to select your video card. Best of luck.

---

### Post by Herman on 2006-08-16
> Thanks for the replies. It could be that i just need to update the OS but i currently don't have internet access so i'll have to wait until the end of the month to give that a go. 
I did find out what graphics card i own if it's any help. IT's pretty old but it's a S3 Savage8 GFX integrated in KN266. So the make is savage. I think the problem is the xserver but i do not get any error messages showing up. Just a blank screen.
SuperBeaver, I agree with both of the above posters, confused57 and avtolle.
Here is the same link that confused57 gave you again in case you missed it.
If you can take a look there you will see that there is nothing to be afraid of. That web page just shows an example (with illustrations of every step to make it really easy) of how I did mine, so you can see ahead of time what happened to me. It's really not difficult at all. Just give it a try, but of course you will have to substitute your own answers for some of the questions to suit you own computer, rather than just copy mine.
I don't think waiting a month will be any help, it will just be a waste of time. You'll be really happy once you do it. :D  Be brave.
Here is that link again, sudo dpkg-reconfigure xserver-xorg...................................................................[Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")
Regards, Herman

---

### Post by SuperBeaver on 2006-08-17
Sorry

Forgot to mention i tried to reconfigure the X server.  It didn't help.  The X server had detected my card correctly as far as i could tell.

---

### Post by Herman on 2006-08-17
SuperBeaver,
Hopefully then, when you get Dapper Drake at the end of the month you will have better luck. Breezy Badger *should* go in okay, but each newer version gets better, of course, and supports more various hardwares.
Sometimes just formatting or deleting the partition and repeating the same install over again results in better luck if there might have been some small glitch in the install. 
You could try to reconfigure the X server and try out the vesa driver and see if that will get things working.
Regards, Herman :D

---

### Post by SuperBeaver on 2006-08-18
Thanks Herman.  I might try the vesa driver.  what do i select?  For me a list of card makes came up, is there a VESA option in that list?  Or do i dismiss the auto detection of my card?

Thanks

---

### Post by Herman on 2006-08-18
> Thanks Herman. I might try the vesa driver. what do i select? For me a list of card makes came up, is there a VESA option in that list? Or do i dismiss the auto detection of my card?SuperBeaver, again refer to the web-page, 'sudo dpkg-reconfigure xserver-xorg........[Xserver Page']("http://users.bigpond.net.au/hermanzone/p7.html") , You will see by the illustrations there that the first question right after the command is entered is 'Attempt to auto detect the video hardware? You do not need to deselect autodetection, just choose. (Yes). again.

 The next item is a list of X server video drivers. If you have selected 'auto detect', then probably the correct driver on this list for your hardware will already probably be highlighted (autoselected) with the blue selection bar, by the program. In your case that would be most likely to be the one titled savage. 
If you look down the list in the illustration on the web page, you will see the vesa and the vga generic drivers fifth and fourth up from the bottom of that list in the illustration.
[I]What I have not shown there in the illustration, is that in reality this list has a scroll bar, and you need to scroll up and down the list with your arrow keys to view the full list, in order to pick out the vesa or vga generic drivers.
[/I]
Does that help you? This has not been mentioned on that web page. Maybe I had better edit that web-page and clarify that for others who also might have the same question. Thank you for bringing that to my attention.
Regards, Herman :D

---

### Post by SuperBeaver on 2006-08-21
Thanks Herman

It worked with VESA.  It booted up with a large black border around the edge but it worked.  I may wait for my new version to arrive and try again with that.

Thanks for your help

---

### Post by Herman on 2006-08-21
SuperBeaver, okay then, well good luck with Dapper then, Ubuntu does keep improving all the time, a lot of people are putting lots of hard work into it every day. Hopefuly the next version will suit your computer better.
Thanks for trying, Regards, Herman :D

---

