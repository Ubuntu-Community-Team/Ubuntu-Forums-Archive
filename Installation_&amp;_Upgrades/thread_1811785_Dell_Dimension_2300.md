---
title: "Dell Dimension 2300"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Robinfox88 on 2011-07-25
Hi, I do know that this question has been asked before, but it wasn't answered properly, at least, not in any way that could help me.

But I'm looking to install Ubuntu 10.10 on a Dell Dimension 2300, which has been upgraded to 1GB of ram, a Silicon Image 3114 PCI 4 port SATA add-in card, 500GB WD Caviar black HDD, Sony Optiarc DVD RW drive, a 450 Watt PSU with dual 12V rails with plenty of amperage to power the whole PC, and a 512MB PCI GeForce GF6200 Graphics card, it also includes the original DVD ROM drive as well.

However, when I come to run the live CD, it hangs at the splash screen with the four (Correct?) dots, and I have to pull the plug in order to switch the machine off.

I think I already know where the problem lies, and it's with the PCI graphics card, however, I haven't found any information on how to get around this, and as the graphics card is quite uncommon and also quite expensive, and helps massively with the speed of this computer, I'm unwilling to get rid of it. It works in Windows XP , but seeing as XP is outdated, I wanted to move to something else, and Ubuntu is my first port of call.

I know that this is extraordinarily long, but I wanted to provide as much info as possible in order for anyone who can answer this to be able to help me. I thank you in advance for any help that you can provide me on this, it's very much appreciated

---

### Post by Quackers on 2011-07-25
Welcome to UF.
Try the nomodeset boot option.
While booting from the live cd at the FIRST purple screen (with the little man icon at the bottom) press any key.
Choose your language then on the next screen press F6 key.
Some options will appear bottom right. Choose the NOMODESET option and see if the desktop boots. 
Select "try Ubuntu" first, rather than going straight for installation.

---

### Post by Robinfox88 on 2011-07-25
Thank you for the (very) quick response, I wasn't expecting anyone to get to me on this so fast, so thanks for that :)
I will try that now, actually, I had seen the nomodeset parameter, but I couldn't find out where or how to select this, so your info has cleared that up for me :)
I have tried the disk as a live CD and it works, but only when the Graphics card is not plugged into the computer, so I'll plug it back in and try that out and I'll let you know what happens, again thank you for the quick response, and thank you for the welcome too :)

I've tried using nomodeset, but it hangs at this point:
3-Ubuntu
[  61.486122] Call Trace:
[  61.486164]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[  61.486204]  [<c012d4cb>] ? check_for_bios_corruption+0xcb/0xe (can't see full message past this point, it's covered by the Ubuntu splash image, and the next fully viewable line is 4 lines down from this one)
[  61.486356]  [<c012d4ed>] check_corruption=0xd/0x30
[  61.486399]  [<c0161a4e>] run_workqueue+0x8e/0x150
[  61.486436]  [<c012d4e0>] ? check_corruption+0x0/0x30
[  61.486471]  [<c0161b94>] worker_thread+0x84/0xe0
[  61.486511]  [<c0165e10>] ? autoremove_wake_function+0x0/0x50
[  61.486550]  [<c0161b10>] ? worker_thread+0x0/0xe0
[  61.486583]  [<c01659e4>] kthread+0x74/0x80
[  61.486619]  [<c0165970>] ? kthread+0x0/0x80
[  61.486654]  [<c010363e>] kernel_thread_helper+0x6/0x10
[  61.486689] ---[ end trace ac11a009a9e320ec  ]---

I'm not sure if any of the above will help anyone, but that is where it hangs, and the CD no longer is accessed the minute this text shows up, and it's much much longer than this, about 150/200 lines of this code shows before it stops.

---

### Post by Quackers on 2011-07-25
Sorry I didn't see you'd edited your post.
That looks like a kernel panic.
Try one of the other boot options, like noapic, nolapic or worst of all acpi=off.

---

### Post by Robinfox88 on 2011-07-25
Oops, my bad I should have made a new post ^__^
I've just tried acpi=off, and it hangs at the same point as when I first tried to run the live CD. :(
I have heard of agp=off, but I'm not exactly sure if it will help in this case or if it's even a valid parameter. :(
If this can't be solved when I have the graphics card installed, then I can maybe install without it, and then add it in later, but the question is, how to then get Ubuntu to accept the card once I'm up and running? As I have heard that even this causes problems, and can even break the install if not done right. :(
Thank you for your help and patience btw, it really is appreciated

---

### Post by Quackers on 2011-07-25
Have a look at the page below and in particular at the F6 part and explore more options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It is possible that there is a hardware problem too.

---

### Post by Robinfox88 on 2011-07-25
Thank you for your help, but unfortunately,none of the options that are  on there, and many that I have found elsewhere will work, it hangs in  exactly the same spot every time, you've been really helpful though, so  thanks again, but unfortunately, nothing seems to work, the only option I  have left is to install without the graphics card and then install it  after I'm up and running, and hope for the best. :(

And if that doesn't work, then I'm either going to have to use a  different distro in the hopes that one of those will work, or, learn how  to build my own kernel that either ignores or has no support for agp  graphics entirely, or just the integrated intel i845 graphics adapter.

And if that doesn't work, then its back to windows xp, until I can figure out something else :(

Thank you very much again for all your help :)

Just to clear up something that I forgot to mention, is that there is no  option in the dell bios to disable the integrated graphics, and as I  don't have a floppy drive or even a floppy disk, I have no means to  flash it to the bios for the Dimension 2350, which does, if I could do  that, I would have done, thus none of this would have been a problem.

From what I've gathered, is that ubuntu is receiving from the bios that  there's two different graphics adapters, and because ubuntu can't ignore  for whatever reason the integrated graphics, it confuses it into a  kernel panic, and there is no solution for it, apart from flashing the  bios to the one for a dimension 2350 :(

---

### Post by Robinfox88 on 2011-07-26
For anyone else who reads this, I've gone with a different distro, PCLinuxOS, that one works just fine with the Dell with the graphics card installed. But I'm a bit disappointed tbh, I really wanted to use Ubuntu because it was the first distro I ever used that got me into going down the path of Linux, and I was hoping to use it for this Dell, but I guess that it wasn't meant to be :(

Thank you again for taking the time to help me Quackers, it really is much appreciated. :)

For anyone (If, indeed, there is anyone else) That has a Dell Dimension 2300 and a graphics card and wants Linux, I'm afraid it's either flashing the BIOS to one for a Dimension 2350 (This does work, the motherboards are almost identical, and it has been mentioned a few times on the web, but I am unable to try it as I don't have a working floppy drive) or going with a different distro, as Ubuntu refuses to work with the graphics card installed. :(

I will still use Ubuntu though, as I have it for my own computer, and I have had my girlfriends mum migrate over to Ubuntu from Vista, after a nasty virus that practically wiped her hard drive clean, and she enjoys using Ubuntu as much as what I do. :)

I will be coming here in case I have any more queries, but as for this, I'm afraid I'm going to have to call it a day. :(

---

### Post by Quackers on 2011-07-26
I'm sorry that things haven't worked for you. It seems that it can be necessary to switch off the onboard graphics to get Ubuntu to work on occasions. Sadly this is not an option sometimes.
Maybe this will be addressed in the future.

---

