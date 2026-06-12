---
title: "A couple problems"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by NemoPaice on 2005-10-14
First Last m=night I was trying to install w32 codecs. I finally got the deb file but can't remember how to install it.

Second, when I try to update or anything via Terminal I get the following error....
 dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
I closed the Package manager while trying to install w32codecs earlier that day because I guess the site was down and it was just hanging for oveer an hour.

Lastly, I am a 3D artist and I use C4D almost exclusivly. While I am trying to currently use Blender, I still need C4D I cannot run it under Wine. although I know some people can. So as of last night I have but one 60GB hard drive With Ubuntu on it. I Have my Pc's Original recovery cd with XP, And I have No live CD but I have the Ubuntu instalation cd. What can I do?

---

### Post by aysiu on 2005-10-14
To install a .deb ```
sudo dpkg -i w32codecs.deb
```

Follow the instructions--just put *sudo* in front.

I don't know about 3D.

---

### Post by NemoPaice on 2005-10-14
[QUOTE=aysiu]To install a .deb ```
sudo dpkg -i w32codecs.deb
```

Follow the instructions--just put *sudo* in front.

I don't know about 3D.[/QUOTE]
Thanks it worked of course. For some reason I cant remember that "dpkg -i". (making post-its for thease untill I get use to them.

Now the other problem is basically just this......
I have XP on another HD, If I install the other HD XP automatically boots up. Since I am still new on linux I knew nothing would be lost if I re-installed linux. so I did, and allowed the Grub bootloader. then when everything was done, I could not log into either System. It kept giving me an error. 

So I switched the order of HD's, and XP once again tried to boot but hung. It didn't even give me an option for anything else.

So I just took out the XP HD, Re-did linux yet again, and said the heck with it for now. As of 20 min. ago I have everything on linux working Just perfect. Other than me using C4D, which is what I need XP for. 

So I have a HD with XP on it (But not in the Pc),  I have my Pc's Recover disk, And was wondering how I would go about installing XP, and/or the HD with xp and get it all to "GEL".

---

### Post by NemoPaice on 2005-10-15
I guess there is no way for me to do this then?

---

### Post by Hooplife on 2005-10-15
Hi,
I'm not sure if I understand your situation but I'll try helping out.
When you installed Ubuntu were both hard drives in the computer?
If so, during the Ubuntu installation process it should have asked you installing GRUB as your bootloader. In my system I have an 80GB windows drive and a 30GB Ubuntu drive. When I installed Ubuntu I said yes to installing GRUB and now when my pc boots up there is a boot menu that allows me to choose windows or Ubuntu.
Do you have a boot menu when you boot your pc?

---

### Post by NemoPaice on 2005-10-15
Ok, When I first DL Ubuntu, I did it to try it out. so I installed it on my second HD which is only 10GB. It did install Grub, and I could boot into both. I found that with the exception of my having kind of a hard time installing things, I like it alot. So I decided to put it on my Larger HD and use it exclusivly.

But I also found that I still need windows for My specific 3D apps. So I reinstalled XP using my PC's recovery disk. I knew that it would write it self to the first HD, so I took out the 60GB HD which now housed Ubuntu, and put My smaller HD In the first possition and installed XP. 

Then I put the Larger HD (With Ubuntu) back into the system. Then reinstalled Ubuntu It once again gave me the option for Grub and I accepted. When I rebooted Grub came up and I selected to boot Ubuntu, It gave me errors. So I tryed to Boot XP and got the same errors but with diferent code(which I don't remember). 

So, I switched the order of HD's. Now Windows tried to boot on its own and hung for like an hour. So I took out the Xp HD untill I could figure out how to do it properly. 

And of course had to reinstall Ubuntu yet again.

So now I have Ubuntu on the HD I want alone in the system. And I have my XP HD sitting on my counter wating to figure out how to rectify my situation

---

### Post by NemoPaice on 2005-10-15
OK now I made some progress, And I am praying that someone can help.

XP HD is back in, I redid Ubuntu. and grub installed I oviouly can boot into Ubuntu, But when I try XP, I get the following error.....


Root (HD1,0)
Filesystem type Unknown, Partition type 0x7
Savedefault
Makeactive
Chainloader +1

PLease help if anyone can

---

