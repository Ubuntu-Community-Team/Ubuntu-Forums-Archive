---
title: "Installing a game not working with Wine"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by theonciest on 2008-07-03
Alright, heres my problem... I'm fairly new to Ubuntu, I've been at this problem for almost a month now. I still cannot figure it out. Since I'm new its hard maneuvering around Linux trying to figure it out. I thought I would give it a try figuring it out for myself searching google and getting a feel of how Ubuntu Linux works. (I am a Windows user) How ever I really like Ubuntu. :D This is why I do not want to resort to dualbooting Windows, or what ever... that sounds complicated aswell. 

Anyways, the game is Entropia Universe. Here is the thread that I have been frequenting for some time. 

[http://www.entropiaforum.com/forums/technical/61443-entropia-universe-linux-wine.html](http://www.entropiaforum.com/forums/technical/61443-entropia-universe-linux-wine.html)

I heard Entropia runs more natively on Linux than on Windows. I'm proud of that, but I just want to get it to work. xD

I have installed Wine, I've wiped the c drive for wine clean like 30 times and repeated some process stated by another user on the forums. It isn't helping what-so-ever. I'm starting to get impatient, this game is what I do for my free time. Its turning out that all I'm doing is repeating the same process over and over again during my free time. And I'm forced to wait for someone to post. Thats fine... I just wished their posts weren't... 

"I'm sure if you do this, and this... it'll work. ^__________^"

If you guys can help, it would be GREATLY appreciated. I've already become loyal to Ubuntu, theres no going back now. lawl 

Sorry for the long post.

Thanks.

---

### Post by brazemcee on 2008-07-03
Try using PlayOnLinux. I don't know if they support this game. Maybe they do. Check it out.

---

### Post by theonciest on 2008-07-04
:/ Nope, that didn't work.

---

### Post by Partyboi2 on 2008-07-04
[[COLOR=Blue]This[/COLOR]]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9456&iTestingId=18096") is from the wine website, not sure if its of use. Looks like it needs some customization to get it to work.

---

### Post by theonciest on 2008-07-04
Nah, not working...

---

### Post by theonciest on 2008-07-09
:/ Please somebody help... this is rather important.

---

### Post by upchucky on 2008-07-09
Einstien was heard to say the definition of insanity is doing the same thing over and over and expecting different results.

there are many games that are not in the wine app data base but they work, you just gotta search for clues.

although i do not have the answer to your specific game issue i do know that there are wine registry tweaks that can help, plus the version of wine may be important. and starting from commandline instead of the gui is another variable, also settings in wine.cfg. you will have to search for each of these in ubuntu forums and wine forum tho.

also need to have vid card properly set up for 3d

---

### Post by malleus74 on 2008-10-28
This game (and Family Tree Maker) is the main reason I'm still dual-booting with Vista. Can anyone help?

Edit:  I have followed the info on Wine AppDB, and it starts. I've extensively used winetricks and winedoors to add lots of 'native' drivers to Wine, and added a few directly on my own. The next screen is gray with no gui, where I should be typing in my userid and password. 

Also, has anyone put together a script to 'optimize' Wine's registry instead of manually editing keys? I'm not having much luck with this part of customizing Wine.

---

### Post by malleus74 on 2008-10-29
Has anyone found a way to get this working correctly?

---

### Post by Astinsan on 2008-10-29
Wine is not something that you can just get to work just yet. Plus you haven't told anyone what the issue is...  Using a program like playonlinux to help you install wine so it will work for you is the only option I can recommend. 

You have to remember that if you don't have a 3d graphics driver installed and working from the beginning you will ultamatly fail. 

Make sure you can load anything that requires 3d graphics drivers. Use the screensavers included by default with ubuntu to make sure they work. When you preview them they should run smoth and not choppy. If they are choppy then you are no using 3d graphics.

So the bottom line is.. if we don't know what the problem is... we can't help you.

Also if you respond by saying "nope... don't work" that isn't going to help you get any type of help since we are not in front of the monitor with you... we can not see what the error is.

 You have to provide feedback... 


Not trying to be a dick about it. Just trying to help.

---

### Post by malleus74 on 2008-10-29
Thank you for replying!

I'm very willing to take constructive criticism. I'm supposed to be using the ATI restricted drivers right now, and tonight I'll be able to check how the screensavers look.

As a matter of fact, I'm getting close to probably starting over with Intrepid. I still need to image this install first. After that...

I will document each and every change I do to the generic Wine install, and then I'll reply here again, as I go!

Precise Question 1: I've heard I might have to do some changes to the kernel to make the video work correctly with Wine and gaming. Is there well documented faq anywhere about this?

I am using a Toshiba P205D-S8894 laptop wth ATI graphics.

---

### Post by wesley_of_course on 2008-10-29
Not sure this is constructive or not but , have you tried Crossover ? 
   It was FREE yesterday .   I believe , (if my facts are right ) , wine comes from those kind folks .  Just thought I'd ask .

---

### Post by malleus74 on 2008-10-31
I asked them to send me a key... the servers were too busy to d/l it yesterday. Great idea, though... 

I've installed a generic version of Intrepid as of last night, and am documenting each and every little change I do to customize it. Hopefully this will give someone the info they need if this doesn't work.

---

