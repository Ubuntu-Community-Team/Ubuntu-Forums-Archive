---
title: "New to Ubuntu and problems installing it"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by dkoz on 2012-04-15
Hello,

I have a Toshiba satellite cd065D,
it had windows 7 on it previously and I decided to completely replace it with Ubuntu 10.04. The first problem that occurred was a black screen with codes. I found a solution on the net for this by simply going to the advance menu of the cd installation and selecting the acpi=off option. The installation then proceeded and it was a success. I couldn't boot at first, had to write some commands on grub: 
root (hd0,1)
linux /vmlinuz root=/dev/sda1
initrd /initrd.img
then boot

It worked and I booted it successively, I even got the wireless connection working. Everything went well, until I decided to update, after restarting the computer the same commands I used before didn't work, getting messages such as kernel not loaded etc... I couldn't find a solution to this problem so I decided to re-install ubuntu 10.04 and the second installations had problems, it stopped working at about 85% of the installation process. I gave another try of installing and now I keep getting stuck at the ubuntu logo forever. Same problem with the first option loading ubuntu without installation. 

I am not sure how much RAM I have, had windows 7 working fine until a reboot loop problem. Ubuntu was also working until the update. I would appreciate getting some help as I don't want to give up on Ubuntu.

---

### Post by nothingspecial on 2012-04-16
*Thread moved to **Installation & Upgrades**.*

---

### Post by darkod on 2012-04-16
If you do the acpi=off again, and from the main menu select Try Ubuntu, not Install, does it load the live mode correctly?
Can you work on it? Open firefox, browse internet?

Make sure live mode is working first. Then we can see about installing it.

---

### Post by Lemuriano on 2012-04-16
HI,

Perhaps you should try a newer version like 11.10 from a live cd or usb drive first.

Regards.

---

### Post by gordintoronto on 2012-04-16
When I Google cd065D, the only responses I get are your questions. Could you please confirm the model of your computer?

If you have a new computer, you would be better off with a current version of Ubuntu rather than 10.04.

---

### Post by dkoz on 2012-04-17
> **darkod said:**
> If you do the acpi=off again, and from the main menu select Try Ubuntu, not Install, does it load the live mode correctly?
Can you work on it? Open firefox, browse internet?

Make sure live mode is working first. Then we can see about installing it.

It does the same thing, I see the ubuntu logo and nothing happens. The same CD on the same computer used to work.

---

### Post by dkoz on 2012-04-17
> **Lemuriano said:**
> HI,

Perhaps you should try a newer version like 11.10 from a live cd or usb drive first.

Regards.

I did try out newer version 11.10, the same thing is happening, however I don't have to turn on acpi=off. I get the ubuntu logo loading forever.

---

### Post by dkoz on 2012-04-17
> **gordintoronto said:**
> When I Google cd065D, the only responses I get are your questions. Could you please confirm the model of your computer?

If you have a new computer, you would be better off with a current version of Ubuntu rather than 10.04.

Sorry I was tired when I posted the thread, the model is actually Toshiba Satellite C650D.

The computer is almost 2 years old.

---

