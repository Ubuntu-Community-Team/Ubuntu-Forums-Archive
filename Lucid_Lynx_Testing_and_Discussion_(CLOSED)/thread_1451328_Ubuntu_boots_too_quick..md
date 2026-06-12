---
title: "Ubuntu boots too quick."
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ibuclaw on 2010-04-10
So apart from the pleasure of not seeing plymouth at work (unless a disk scan is running) - I have to wait 5 seconds before the keyboard module settles and begins working, and I can finally begin to login. :P

I have one or two thoughts as to possibly resolving this, but any ideas will be helpful.

Regards
Iain

---

### Post by Compyx on 2010-04-10
I would think someone from the forums staff would have an idea where to post this question. (Hint: this forum is about programming)

---

### Post by ibuclaw on 2010-04-10
> **Compyx said:**
> I would think someone from the forums staff would have an idea where to post this question. (Hint: this forum is about programming)

Really? I could have sworn it said "Lucid Lynx Testing and Discussion" - I'll have another look just to be sure, ;)

---

### Post by VeeDubb on 2010-04-10
> **ibuclaw said:**
> Really? I could have sworn it said "Lucid Lynx Testing and Discussion" - I'll have another look just to be sure, ;)

:lolflag:


Really?  5 seconds between the login screen showing up and when you can start to type your login?


Out of curiosity, do you have anything 'unusual' about your setup?  Ancient keyboard, custom kernel, really unusual hardware that might require lot's of modules to be loaded that most users don't deal with?

---

### Post by ibuclaw on 2010-04-10
> **VeeDubb said:**
> :lolflag:


Really?  5 seconds between the login screen showing up and when you can start to type your login?


Out of curiosity, do you have anything 'unusual' about your setup?  Ancient keyboard, custom kernel, really unusual hardware that might require lot's of modules to be loaded that most users don't deal with?

Its a HP Pavilion Laptop - dv2000 model - not sure about anything "unusual".

Though, I suppose I might as well note that I usually only expect this sort of thing when I do Debian/Ubuntu netboot installations on the machine. In that instance, it can take up to 15-20 seconds before the keyboard starts accepting/registering keypresses, but have never really been bothered by it enough to look into it.

---

### Post by uRock on 2010-04-10
From BIOS to Login on my machine is about 8-10 seconds on my old Lenovo desktop. Sadly this is still faster than BIOS can run POST on this machine.

On my Netbook, the boot goes sooo fast that the red dots do not even get to change colors. Those dev need to slow my system down so I can have time to make coffee during boot up.:P

Cheers,
Ronnie

---

### Post by forcecore on 2010-04-10
I hope final stays same fast, even one my friend was baffled, it beats Windows XP and even my turbo XP edition (nlited). I cannot even imagine what it does on SSD, Lucid is king of speeds.

---

### Post by malachi1990 on 2010-04-10
Odd, I have the same model machine, but I don't have this issue.  

Did you upgrade your machine from karmic, or is this a clean install?

---

### Post by forcecore on 2010-04-10
i have to wait about 8 secons on dv 2550 and everything works.

---

### Post by ibuclaw on 2010-04-10
> **malachi1990 said:**
> Odd, I have the same model machine, but I don't have this issue.  

Did you upgrade your machine from karmic, or is this a clean install?
Clean install.
> **forcecore said:**
> i have to wait about 8 secons on dv 2550 and everything works.
Is this 8 seconds *after* the login screen appears?

---

### Post by KdotJ on 2010-04-10
Lol looking at the title I had to look at this thread, I didn't release it was posible for an operating system to boot "too quick" lol :P

---

### Post by forcecore on 2010-04-10
> **ibuclaw said:**
> Clean install.

Is this 8 seconds *after* the login screen appears?

after bios text goes, from there 8-11 sec, i do not know but it is little variable but why? i have no idea. Of course i have modified it with UCK (UCK is most important thing to me ever created), i have no couch things, no update manager (synaptic for updates), no hardware drivers detection (jockey) and other ripped stuff like mono but these do not count i guess because they are not autorunning.

---

### Post by ibuclaw on 2010-04-11
> **forcecore said:**
> after bios text goes, from there 8-11 sec, i do not know but it is little variable but why? i have no idea. Of course i have modified it with UCK (UCK is most important thing to me ever created), i have no couch things, no update manager (synaptic for updates), no hardware drivers detection (jockey) and other ripped stuff like mono but these do not count i guess because they are not autorunning.
Then you are talking about a completely different thing to me then.

Just to clarify, again, Ubuntu boots, the login screen shows, and the mouse is usable. **However**, I have to wait a further 5 seconds before the keyboard starts accepting input (and I can finally begin to login).

Thought it might be to do with an application keeping the keyboard in raw mode, however, getting 'kbd_mode -a -C /dev/tty7' to run at boot does nothing.

> **KdotJ said:**
> Lol looking at the title I had to look at this thread, I didn't release it was posible for an operating system to boot "too quick" lol :P
Don't be the least bit surprised, Ubuntu has also been renowned for being [too stable]("http://ubuntuforums.org/showthread.php?t=451592") too.

---

### Post by forcecore on 2010-04-11
for me about 11 seconds then i can use everything, mouse moves etc... but desktop appears about 8-9 sec, after 11 sec then everything its fine. i have some type 250gb Toshiba hard drive 5200rpm splitted that ubuntu is on 7gb ext4 and DATA is manually mountable ext4 partition. 

Fact is that i discovered when i plug printer, gamepad, external mouse, memory card in before boot it goes to about 14sec. How many secs may i win when i put 7200rpm drive in?

---

### Post by 0004tom on 2010-04-11
LOL lucky for some right? with all the updates, mine seems to get longer and longer. when I first installed the Beta 1 it was a 20-25 second boot, now it's 1 minute + :(

---

### Post by rozbarwinek on 2010-04-12
Will this be fixed? or can I do something to make plymouth appear?

---

### Post by philinux on 2010-04-12
plymouth goes by in a flash

---

### Post by Macchia on 2010-04-12
> **philinux said:**
> plymouth goes by in a flash

Then should be removable rather than core package ;)

---

### Post by phrostbyte on 2010-04-12
It boots the same speed as Karmic for me, which is not too slow but it's nothing to write home about. Shutdowns, however, are basically instant. Very weird. :confused:

---

### Post by uRock on 2010-04-12
> **ibuclaw said:**
> I have to wait 5 seconds before the keyboard module settles and begins working

Is the moral of the thread, not the speed before it.:P

Cheers,
Ronnie

---

### Post by ibuclaw on 2010-04-13
> **uRock said:**
> Is the moral of the thread, not the speed before it.:P

Cheers,
Ronnie

Agreed, I wouldn't be having any issues whatsoever if the system didn't cut corners just to get X up as fast as possible, regardless of what stage of the boot process other startup processes are in.

---

