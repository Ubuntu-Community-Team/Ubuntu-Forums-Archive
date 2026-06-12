---
title: "Can't install 9.10 on PS3 - keyboard doesn't type!"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Ghinn on 2010-01-28
The title says it all. I'm trying to install Ubuntu 9.10 on my PS3, but the keyboard isn't typing. I can't complete the install, because I can't type anything. I've followed all the steps properly, everything goes smoothly, the mouse works just fine, and the capslock and numlock lights light up on the keyboard, and toggle when I press the corresponding buttons. The keyboard even works at the kboot prompt. After I choose the partition to use, I have to enter my information to continue. Without being able to type, I can't progress. The keyboard obviously works, since I can type just fine at the kboot prompt.

This one's got me scratching my head. I'm going to try a 9.04 cd tomorrow, see if that works, but I was really hoping to get 9.10 on there.

Any ideas as to why I'm unable to type? Also, when I try to click the text boxes with the mouse, there's no cursor. Might have something to do with it, but I'm not sure what.

---

### Post by mkeyes001 on 2010-01-29
where is the procedure you followed to install ubuntu, I'll attempt it this weekend and see if I have any better luck..

Matt

---

### Post by jenaniston on 2010-01-29
> **Ghinn said:**
> . . .the mouse works just fine, and the capslock and numlock lights light up on the keyboard, and toggle when I press the corresponding buttons. The keyboard even works at the kboot prompt. . . . I have to enter my information to continue. Without being able to type, I can't progress. The keyboard obviously works, since I can type just fine at the kboot prompt.


Did the install include the grub bootloader ?

It did with my U9.04 USB OS install from a Live USB on a different machine, and that is making all the difference to me right now.

That grub boot screen offers the choice of getting into the recovery shell - 
and the terminal is allowing me to do ALOT of troubleshooting.

The keyboard works in recovery terminal - neither mouse or keyboard yet in the Jaunty desktop (different reason likely) -
my point being to see how keyboard works in recovery mode - if available.

Good luck.

---

### Post by Ghinn on 2010-01-30
I'm using the instructions from here: [http://psubuntu.com/wiki/InstallUbuntu](http://psubuntu.com/wiki/InstallUbuntu)

and the images from here:

[http://cdimage.ubuntu.com/ports/releases/9.10/release/](http://cdimage.ubuntu.com/ports/releases/9.10/release/)

and here:

[http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)

There are the PS3 releases listed. Also, I just tried 9.04, and I can't even get to the installer.

---

### Post by Ghinn on 2010-01-30
I ordered a new keyboard (hoping the problem is as simple as a wonky keyboard), so maybe that'll work. In the meantime, I'm going to try YDL, just to see if I can get linux on there at all. 

9.10 would work, if the keyboard would type. Also, the installer runs REALLY slow, is there any way to use a text-based installer? 9.04 doesn't even get up to the installer, so that's a bust. Maybe 10.04 will finally let me type. Will try 10.04 at some point, and post results.

---

### Post by KingEric7 on 2010-02-12
Hi, I am having exactly the same problem with 9.10. Tried both a a wireless KB and mouse combo and hard wired. SAme result. KB works ok initially at kboot etc but by the time get to the step where you  need to enter your details it appears the keyboard has stopped responding (caps lock toggle still works) or its maybe the mouse as i can move the cursor but when i click in and of the fields to try and input text i don't get a flashing cursor as you would normally expect. 
Did you get anywhere with a solution yet? Did you have a previous earlier disto working ok? IF so which one 9.04 or earlier >

Cheers.

David

---

### Post by jackrabbit72380 on 2010-02-13
SOLVED I THINK?
 
ok guys this same thang happend to me when I tryed to install 9.10 but after 5 attempts I did get my keybord working & did finish the installation the problum im haveing now is I dont know exactly what I did to make it work.
 
I googled & found a unknown bug that dose exist in both 9.10 and 9.04 that has something to do with the keybord not working 
 
but basicly to get it work I tryed alot of stuff 
 
first I booted off kboot & got all the way to ware I needed a keybord & when it didnt work I then went back to ps3 os & installed petitboot
 
booted from petitboot & tryed the diffrent options in thare I tryed using the installdriverupdates option and what not well went through the install & when I needed a keybord it still did'nt work. 
 
so I boot back to ps3 dash & installed kboot agin 
 
eventuly it worked i dont know how i solved the problum a cold boot may have made the diffrence or maby unpluging the keybord and repluging it in when u need it but its an unknown bug from what I have gatherd 
 
Im curantly wipeing my ps3 system clean to do another fresh install just to find out exactly what it is 
 
it may have something to do with puching a sertin key on the keybord maby the up & down arrows but im not sure 
 
one thang I am sure of is that the installation is smooth once you get past the keybord bug
& its possible to get around it!
 
if I find a fix I will post it hear k hope I helped!
 
EDIT: YEAH OK IM NEW SO WHAT I KNOW HOW TO READ & SEARCH AND IM NEW TO LINUX BUT HAY IM A GEEK!
 
& HEAR NOW TO HELP SO HEARS MY FIX I HOPE IT WORKS FOR YOU GUYS LET ME KNOW OK!
 
problum:keybord wont work to install ubuntu 9.10
 
sorce: at the kboot prompt when you hit enter to boot you see some text 
one of the lines says your first usb2.0 slot gets degrated to a usb1.0 
 
well i think thats whats happening anyway so anyway when you see this text unplug your keybod & plug it in to another slot!
 
it just worked for me 
 
& one more tip if you have your ps3 hooked up to a 720p display 
 
at kboot type ([FONT=Courier New]install video=ps3fb:mode:131) with out qotes insted of just hiting enter![/FONT]
 
[FONT=Courier New]& then installation should take place in full 720p without black borders

When the installation is finished you need to go back to your ps3 dash and install petitboot

when you boot petitboot you will see that your linux start option allredy has 720p listed

this worked very well for me! best of luck guys![/FONT][FONT=Courier New]
[/FONT]

---

### Post by KingEric7 on 2010-02-15
Thanks for the update. Unfortunately i get the saem result. KB wont type anything when I get to the section where you have to put your name / password in etc.....

Have tried 9.04 9.10 and even 10.04. Same result except 10.04 just gave me loads of errors about everything from Kernel issues to device controller problems so i gave up with that....


Anybody know if 8.04 or any other distro just works with the pS3....i mean it shouldn't be this hard should it???

Dave

---

### Post by mellowwood on 2010-02-27
To All

Temp problem solved for keyboard problem installing Ubuntu 9.10 on PS3.

At step 5/6 when prompted to input User name , password etc, you can copy paste parts o the text already on the screen. For instance, User name:   copy  "user" or "name" or what ever you desire and paste it into the relevant fields. This will enable you to get sufficient info into all the required fields to progress to the next step. 

Once Ubuntu is installed i am sure you should be able to change the relevant info to fit you profile, however i am not sure of this , being a 1st time Linux user. 

Hope this helps. 

Mellowwood ;)

---

