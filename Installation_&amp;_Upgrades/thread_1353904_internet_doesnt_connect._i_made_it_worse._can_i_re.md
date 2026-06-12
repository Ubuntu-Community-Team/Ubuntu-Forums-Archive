---
title: "internet doesnt connect. i made it worse. can i reinstall ubuntu?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by sofa88 on 2009-12-13
I've recently decided to install ubuntu 9.10 on a laptop given to me by my father.  I have no idea what the specs of this little brick are other than it's an Asus. 

Install of ubuntu went well, other than the fact that I did a full install because I was having problems making it dual boot with the windows XP it had previously...

So I've lost XP indeffinatly.... no problem... didn't like it anyway.

Now I'm left with a system running Ubuntu wondefully, but refuses to connect to the internet (wirelessly or ether)  since I'm brand new to the world of linux my attempts to solve the problem may have messed things up..  I followed some advice i found online and did something that has made my laptop think it has a mac wireless card in it... hmm.  On install it recognized a Realtek wireless card.. now it doesnt do much of anything....

I would like to reinstall ubuntu to get back to the baseline i started at (as i have no idea what else i changed in trying to fix my internet problem) but i cant, for the life of me, figure out how....

has anyone else had a similar problem?

thx

---

### Post by darkod on 2009-12-13
I don't know about the internet problem, but if you just want to reinstall over it, and you have only ubuntu, boot with the cd as previously, select Install Ubuntu, and at step 4 when asked where to install tell it to use whole disk. That will wipe the drive (destroying any mess that might exist there) and install fresh ubuntu 9.10 for you.
After that, report more specifically what's the problem with the internet connectivity, more details, and check if it will work with a cable first. Wireless comes second.

---

### Post by phillw on 2009-12-13
+1 .. One little tip - when re-installing - don't have your ethernet cable plugged in. I had loads of grief getting my wireless to work, then did about the 4th re-install without the ethernet plugged in (I forgot to plug it in) and, lo & behold the little bugga found the wireless network !!!!

Phill.

---

### Post by Dave67 on 2009-12-13
wireless card always give Linux a issue we might be able to fix it even if you reinstall the wireless still may not work.  

read this doc and do what it states then post this output to this post

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

 once this is done highlight the text copy and paste in a post here this will show me the devices in your laptop and tell me the type of wireless card you have than we go from there.

I saw the other post here also realtek cards give Ubuntu issues  the manufacturers of wireless cards lots of time change chipsets on the cards to save money on manufacturing. We can help  have a look at this I need to go to work be back after 7pm est tonight. 


dave

---

### Post by sofa88 on 2009-12-13
thanks for the replies everyone.

my headache persists however... my knee-jerk reaction was to just stick in my install disk and reboot... this did nothing, just fired up ubuntu regularly.  tried rebooting and pushing f8 - which brought me to a command prompt, but booted ubuntu regularly before i could touch a key... 

since posting earlier i have tried to install ubuntu 9.04 to no avail and also hoped that if i ran the ubuntu upgrage that my system might get back to the point where the computer recognized the proper card it had inside... still nothing.

might there be a way to force-boot from cd in terminal or somethiing?

thanks again guys!

---

### Post by darkod on 2009-12-13
You should be able to select cd-rom to boot first in BIOS, or just hitting F12 during start up (provided that laptop uses that F12 option). You can't boot the ubuntu cd to install?

---

### Post by sofa88 on 2009-12-14
so far nothing... no auto boot, no f12 (though i've only tried once a few days ago, so a second try wont hurt)

if i open up the cd in my desktop the only files i recognize are those most windows users would see - a few .exe files, and various text files (which have raised my hopes, but ultimately they have been no help so far).  

what are the executable files that ubuntu recognizes? maybe i can just double click something and watch the magic happen?

the battle continues - thanks to everyone reading and replying!

---

### Post by audiomick on 2009-12-14
I am sorry to say that although Ubuntu recognises an .exe file, it can't run them. They only work on windows.

---

### Post by sofa88 on 2009-12-26
VICTORY! 

i'm unsure what i was doing wrong the first few times but here's how i fixed my problem:

inserted ubuntu cd

power on --> at ASUS screen pushed f2 (discovered this by smashing every function key in frustration), selected my rom drive as the primary boot volume (then f10 to save, computer will restart)

reinstalled ubuntu completely

and then found this thread - 

[http://ubuntuforums.org/showthread.php?t=1329702&highlight=network+disabled](http://ubuntuforums.org/showthread.php?t=1329702&highlight=network+disabled)

followed steps containing the fwcutter downloads and restarted

and here we go! one asus laptop running ubuntu 9.10 ONLINE and WIRELESSLY!

thanks for all the help everyone! if you will excuse me i am about to see how ubuntu stacks up to some heavy usage!

-b-

---

