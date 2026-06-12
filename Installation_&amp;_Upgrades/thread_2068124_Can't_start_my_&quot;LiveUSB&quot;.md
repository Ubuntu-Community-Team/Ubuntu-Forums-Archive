---
title: "Can't start my &quot;LiveUSB&quot;"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by ClickyMouse on 2012-10-08
Hi!
I've created a "LiveUSB" installation thumb of the latest stable version of Ubuntu on a Mac; and I can't get it to work.
It boots fine, I can switch the language with the visual and choose the special boot options; but when I choose either to try or to directly install Ubuntu, the prompt get stuck here:
[IMG]http://imageshack.us/a/img545/3113/img0222ac.jpg[/IMG]

I don't have much experience on Linux so I don't know what's going wrong... :(

Any help would be appreciated! Thanks!! :D

---

### Post by Bucky Ball on 2012-10-08
Boot from the disk at the options screen hit F6 and choose 'nomodset' from the popup list. Proceed. What happened?

* Note: Please make screenshots/pics etc thumbnail size and less than 100Kb. You can attach them rather than put in the body of the post. Cheers. ;)

---

### Post by ClickyMouse on 2012-10-08
> **Bucky Ball said:**
> * Note: Please make screenshots/pics etc thumbnail size and less than 100Kb. You can attach them rather than put in the body of the post. Cheers. ;)
Done :)
> **Bucky Ball said:**
> Boot from the disk at the options screen hit F6 and choose 'nomodset' from the popup list. Proceed. What happened?
I'll try that now. In the meantime I made a USB thumb on Windows with Pen Drive Linux's USB Installer just to see what happens, and it got stuck here:

---

### Post by Bucky Ball on 2012-10-08
Same place. Try the F6>'nomodset'.

---

### Post by mips on 2012-10-08
I would try the alternate installer image but that's just me.

---

### Post by Bucky Ball on 2012-10-08
> **mips said:**
> I would try the alternate installer image but that's just me.

Certainly another alternative (no joke intended) and would avoid many potential graphics issues, one of which might be the OP's problem.

---

### Post by ClickyMouse on 2012-10-08
> **Bucky Ball said:**
> Same place. Try the F6>'nomodset'.
Didn't work either... :(

______
Oh, I don't know if this would be useful info, but when I start the USB, when the purple splash screen with the square and the little man at the bottom appears; I have to quickly press F2 or something to have the Ubuntu menu on screen. If I let that splash screen pass without touching anything; the PC freezes with a black screen and I have to reboot it.

---

### Post by Bucky Ball on 2012-10-08
Authentication failure? This seems disrelated. But maybe not ...

So, what happens after you hit F2? You get the Authentication Failure or the other one?

---

### Post by ClickyMouse on 2012-10-08
No, sorry... I didn't explained the process very well...

- When I start the USB, the purple screen with the little guy (accessibility icon) at the bottom appears. There I have two options:
[LIST]
[*]If I don't press any key, a few seconds later, that screen disappears, the monitor turns black, and the PC freezes. (So, I have to reboot it and start all over)
[*]If I press a key (let's say F2 for instance, to change the installation language) the Ubuntu screen with all the options appears (F2 for language, F5 for accessibility, F6 for advanced options, etc.)
[/LIST]
- Then, I chose to install Ubuntu; and after a few minutes of different "command prompts" (I don't know how to call them) showing up on the screen. The "installation" freezes with the Authentication Failure lines that I've attached on my previous post.


______
I have to go to get something to eat right now. Meanwhile I'm downloading the alternate version just in case. I'll be back in a bit. :D

---

### Post by Bucky Ball on 2012-10-08
Yep, try that. 

Tip from another site: Try deleting the partitions and leaving free space to install Ubuntu if you haven't already got that. It's worked for others (on Mac so it could be specific to them). I'd suggest doing this before bothering with the alternate.

The authentication failure is an oddity because the LiveCD uses no credentials; username, password, etc, so this shouldn't be happening. But seems to in this situation with a Mac.

Also, be sure to check the disk for errors. Torrent is the best, quickest, safest way to get the ISO. Good luck.

---

### Post by Bucky Ball on 2012-10-08
*Thread moved to **Installation & Upgrades***


> **ClickyMouse said:**
> 
Do you suggest that I shrink the Wndows partition, leaving unformatted space for the Ubuntu installation, and then try to install it?

Thanks!!

Yes. Do this in Windows using it's software though. Important! DON'T use Gparted (unless you're talking about XP).

---

### Post by ClickyMouse on 2012-10-08
> **Bucky Ball said:**
> Yep, try that. 

Tip from another site: Try deleting the partitions and leaving free space to install Ubuntu if you haven't already got that. It's worked for others (on Mac so it could be specific to them). I'd suggest doing this before bothering with the alternate.

The authentication failure is an oddity because the LiveCD uses no credentials; username, password, etc, so this shouldn't be happening. But seems to in this situation with a Mac.

Also, be sure to check the disk for errors. Torrent is the best, quickest, safest way to get the ISO. Good luck.
Didn't work :(
I'll try the alternate method, it boots from the USB the same way the original installation?

Thanks!

____
EDIT: It worked!! With the alternate installator, now I have Ubuntu on the PC! Thank you all!!
How can I mark the post as [solved]?

---

### Post by Bucky Ball on 2012-10-08
Alternate install exactly the same except text-based install rather than disco graphics ...

---

