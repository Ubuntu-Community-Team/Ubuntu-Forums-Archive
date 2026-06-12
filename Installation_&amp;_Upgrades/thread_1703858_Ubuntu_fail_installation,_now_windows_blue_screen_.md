---
title: "Ubuntu fail installation, now windows blue screen of death? Need Help"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by lazyceltic on 2011-03-09
I just finishing burning ubuntu on my laptop and was getting ready to partition my disk to allow space for ubuntu. I restarted my computer and when it was restarting ubuntu logo came up (as it booted from the disc). I was not wanting to install it at this moment so i was waiting for it to load then cancel it(just like a windows installation).
It then froze and became pixelated with green and white colours.
I thought it was nothing maybe just an error in teh disc. I waited 5-10 minutes then held the power button to shut it off. I then went to settings in the bios and changed it to boot from hdd first. After restart, windows began to load for like 3 seconds then blue screen. I dont know what went wrong or why this is happening... Any ideas?

During installation of Ubuntu on my second try I keep getting:
sudo: can't read /etc /sudoers: Input/Output error
sudo: no valid sudoers sources found, quitting

What are the odds of me still having my windows 7 data?

and could Hiren's boot cd help?

Sorry for the mass amount of questions im quite new to all of this.

My laptop is asus G60JX

---

### Post by lazyceltic on 2011-03-09
Anybody?

---

### Post by Hedgehog1 on 2011-03-10
This is a hard one.

If you are able to get to the 'try' option on the LivdCD, can you please do this:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by lazyceltic on 2011-03-16
Sorry for late reply i just formatted my computer and put windows 7 back on. Im thinking about reinstalling Ubuntu but when I was getting the Ubuntu installation error,i couldnt do anything it was just the Ubuntu logo with the dots flashing underneath. And it stayed on this screen. Do you think this will happen again?

---

### Post by Quackers on 2011-03-16
Sounds like a graphics problem. Which graphics card are you running? You may need to use a boot prompt.

---

### Post by lazyceltic on 2011-03-16
I am using NVIDIA GeForce GTS 360M as my grphx card

---

