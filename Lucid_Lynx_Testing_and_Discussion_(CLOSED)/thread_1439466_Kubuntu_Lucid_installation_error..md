---
title: "Kubuntu Lucid installation error."
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by praveenthivari on 2010-03-26
I downloaded Lucid Beta cd and upadted it today with zsync. and I used this to install Kubuntu. Weird thing is it didn't ask for any username and password. After installation on restarting the system it asks for username and password, and I dont have a clue wat it is. 
I hv reinstalled that and still it's the same.

Someone else having this problem?

---

### Post by SushiR on 2010-03-26
Yeah, same here. Solution: Boot into recovery mode, and choose root access, then enter the following ```
adduser your_use_name
``` and hit enter. Answer the questions an voila.. Dont forget to add your user to the sudo group ```
gpasswd -a your_user_name sudo
```

That's it!

---

### Post by praveenthivari on 2010-03-26
> **SushiR said:**
> Yeah, same here. Solution: Boot into recovery mode, and choose root access, then enter the following ```
adduser your_use_name
``` and hit enter. Answer the questions an voila.. Dont forget to add your user to the sudo group ```
gpasswd -a your_user_name sudo
```

That's it!

Thanks eill try and return back from Kubuntu;):D

---

### Post by praveenthivari on 2010-03-26
Hey, KUBUNTU DOESN'T SEEM TO BOOT INTO RECOVERY MODE. 

It loads some files and then just stops with a static cursor on top left corner of the screen. No msg displayed. :oops::cry:

---

### Post by SushiR on 2010-03-26
Uh, well, I installed from a daily iso the day before yesterday and I had no problems booting into recovery mode. Maybe the best idea is to download a new daily iso and reinstall. Sorry I could not help you any further..

---

### Post by VMC on 2010-03-26
> **praveenthivari said:**
> Hey, KUBUNTU DOESN'T SEEM TO BOOT INTO RECOVERY MODE. 

It loads some files and then just stops with a static cursor on top left corner of the screen. No msg displayed. :oops::cry:

From grub, add "single" to the linux boot string.

---

### Post by praveenthivari on 2010-03-26
> **SushiR said:**
> Uh, well, I installed from a daily iso the day before yesterday and I had no problems booting into recovery mode. Maybe the best idea is to download a new daily iso and reinstall. Sorry I could not help you any further..

Thanks

> From grub, add "single" to the linux boot string.
Thanks for the reply. Could u pls explain a little more on how to add tht to boot string.

---

### Post by VMC on 2010-03-26
> **praveenthivari said:**
> Thanks


Thanks for the reply. Could u pls explain a little more on how to add tht to boot string.

When grub menu shows up, move to the selection of choice, push 'e', then use arror keys to move to the line beginning with 'linux', push the "End" key and add ***single*** to the end of that line, then Ctrl+x to boot.

---

### Post by praveenthivari on 2010-03-28
> **VMC said:**
> When grub menu shows up, move to the selection of choice, push 'e', then use arror keys to move to the line beginning with 'linux', push the "End" key and add ***single*** to the end of that line, then Ctrl+x to boot.

Thanks VMC:D, I tried even that and the result was same, so I had to do away with Kubuntu, and now I will wait for beta2 to be released:(

---

