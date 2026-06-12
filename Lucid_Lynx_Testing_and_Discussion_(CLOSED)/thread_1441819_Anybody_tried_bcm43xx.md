---
title: "Anybody tried bcm43xx?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stardustdk on 2010-03-29
hey all.

I have Intel 3945ABG myself, but are helping someone that needs The Brodcom driver.

Is threre anybody of you that have tried Lucid with the bcm43xx?

If yes:

1: Is it working "out of the box"?
2: Not working "out of the box", what is needed and how to install it?

That PC is actually running 9.04/Jaunty.

I am asking because it will take a lot of time to upgrade 9.04->9.10->10.04.

Looking for the most easy/quickly way to get the job done.

Best regards

Stardustdk

---

### Post by gordi on 2010-03-29
why don't you simply try a live-cd with network cable and download the drivers?

---

### Post by zenarcher on 2010-03-29
I did an install on an HP notebook computer the other day, which used Broadcom wireless.  I can't remember which Broadcom at the moment.  I didn't have wireless "out of the box," but merely ran "Hardware Drivers" which found the Broadcom driver and installed it easily, after which the Broadcom wireless worked just fine.

Cheers,
zenarcher

---

### Post by jeremy1138 on 2010-03-29
> **zenarcher said:**
> I did an install on an HP notebook computer the other day, which used Broadcom wireless.  I can't remember which Broadcom at the moment.  I didn't have wireless "out of the box," but merely ran "Hardware Drivers" which found the Broadcom driver and installed it easily, after which the Broadcom wireless worked just fine.

Cheers,
zenarcher

Same thing here.  It's been working this way for the last 2 or 3 releases I think.  All you have to do is plug it into your router via internet for a few minutes and run the restricted driver manager and enable the wireless card.  It then automatically downloads and installs the appropriate driver.  

It's a ton easier than it used to be.  I remember the first time I tried Ubuntu (version 7.04), it used to be such a pain to get my wireless card to work.  You had to do all that business with copying over your driver from windows and using that ndiswrapper program and all that.  It made my head hurt.  I don't want to go back to that.

Anyway, it all seems to work fine now so give it a try and let us know how it works. :)

---

### Post by praveenmarkandu on 2010-03-29
> **stardustdk said:**
> hey all.

I have Intel 3945ABG myself, but are helping someone that needs The Brodcom driver.

Is threre anybody of you that have tried Lucid with the bcm43xx?

If yes:

1: Is it working "out of the box"?
2: Not working "out of the box", what is needed and how to install it?

That PC is actually running 9.04/Jaunty.

I am asking because it will take a lot of time to upgrade 9.04->9.10->10.04.

Looking for the most easy/quickly way to get the job done.

Best regards

Stardustdk


go to system --> administration --> software sources --> check CD with Ubuntu "Lucid Lynx"
put in the lucid lynx cd. launch the terminal.
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source dkms
```
after that is done, just restart your comp and all should be good to go

if you have a wire connection to the internet, you can just run synaptic and install bcmwl-kernel-source and dkms without needing to enable the ubuntu CD .

---

### Post by TBABill on 2010-03-29
+1 on the replies above. The Broadcom driver worked great for mine as well on an Acer laptop.

---

### Post by fargle on 2010-03-29
I have a new Dell Studio 14z that came with a 4312 card.  I set it up with the B43 driver and it was a mess - constantly posting DMA errors and continuously trying to reload the firmware after that, and the card is dead until reboot.

I switched to the STA driver yesterday and it seems much happier, no problems as yet despite heavy downloads and leaving it on all day.

However, I just have never liked Broadcom cards at all, and this one is G-only anyway while I have a dual-band N router, so I ordered a Dell 5100 AGN card and it will be delivered today.  I've had much better luck with Intel cards in general.

---

### Post by stardustdk on 2010-03-29
Thanks for the answers :)

Now i got the clue ;)

Best regards

Stardustdk

---

