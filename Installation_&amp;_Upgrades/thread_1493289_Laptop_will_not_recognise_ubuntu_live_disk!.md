---
title: "Laptop will not recognise ubuntu live disk!"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by kit21 on 2010-05-25
Hello, 
 
I'm new to ubuntu and have been trying to install it onto my laptop (its about 4 years old - a Sony Vaio VGN FS315E).
 
I have been given a live disk of the latest edition of ubuntu (10.4?) by someone at work, but my CD drive on my laptop seems to think the disk is blank. I know this is not the case as when the disk is inserted into a different laptop is it recognised as an ubuntu installation disk.
 
My aim to boot ubuntu from the disk to get a feel for what it's like before installing it fully on my laptop, and also to check that it would work on said laptop.
 
Any advice on what I can do to either get the disk to be recognised (I'm not that hot with computers, but I know a little) or to get around this problem would be MUCH appriciated. 
 
Thanks for your time! :)
Kit

---

### Post by darkod on 2010-05-25
Can you tell if cd-rom is before hdd in boot devices?

Depending how the screen looks like when you start your laptop, there should be text written which button is for Quick Boot menu, or similar, if it exists. Usually it is F12. So if you hit F12 it will let you choose what to boot from, you should select the cd/dvd.

Alternatively, pressing F2 or F10 (it differs for different laptops) should open the BIOS, and you need to look around in the boot options whether cd-rom is before hdd, to try to boot from the cd instead of booting the hdd straight.

---

### Post by kit21 on 2010-05-25
Thanks!  The f12 key worked and my computer tried to boot from the CD - however - with limited sucess.  Ubuntu starts to load, I can select the language, and then choose to boot without making any changes to my system.  The program then begins to load (black screen is white logo in centre) which seems to complete, and then runs some script.  The script seems to return many errors and after a short while stops running so that I cannot make my laptop respond  and so have to turn it off.  :(
 
I realise this is probably a very bad description of what is happening, if you need more information, what would be the best way to give this to you?  as I can't print screen or anything so show you whats happening.
 
Also, I am unsure how to enter BIOS in windows...but I have the CD working now, so not sure if this is relevent any more.
 
Thanks again for your help!
Kit

---

### Post by darkod on 2010-05-25
OK, that's progress. Do the same, but when you see the ubuntu main menu, before selecting Try Ubuntu, hit F6 to show advanced options. Select Safe Graphics, and then Try Ubuntu.

If it loads fine to a desktop, that means it's a video driver issue. If not, there are other things to try under F6 but try them one by one so you know which worked.

---

### Post by kit21 on 2010-05-26
Ah Success!  I am now running ubuntu from the disk!  Thanks for your help :)  

I hit F6 and used the safe graphics option and it worked, so this means I have a video driver issue?  What does this mean?  And how would I go about fixing it?  Sorry to keep asking so many questions, I'm a newbie who's never used anything but windows!

---

### Post by darkod on 2010-05-26
In live mode you can see the Install icon on the desktop. You can install like that but be aware that on first boot you will probably have the same problem, until you boot it once and try to find updated driver (ubuntu should find it for you automatically).

So the thing is to manage and boot that first time. :) The boot menu will be slightly different so the option with F6 might not be the same. I can't remember the options exactly right now, but if it comes to that we'll figure it out.

---

### Post by WinRiddance on 2010-05-26
Some older laptops also have initial configuration issues that Ubuntu, LiveCD or not, needs to bypass first. I installed Jaunty Jackalope on a 4 year old machine from some friends of ours and they have to wait about **3 whole minutes** before the entire installation has completed the boot process ... even though it's a single 3 Ghz. processor with 1 GB of Ram. Once completed though, everything runs perfectly, even compiz 3D settings. (while the fan starts screaming)

---

### Post by bondo101 on 2010-05-26
I had the same problem with my vaio laptop only i tried to install on a partion on the other side of windows. As a clean install it worked but wouldn't recognise some of the hard ware. I'll try again when i have some time . still luv linux .:)

---

### Post by sgosnell on 2010-05-26
If it takes 3 minutes to boot, there are configuration problems.  Sort those out and the boot will be much quicker, on the order of 30 seconds.

---

