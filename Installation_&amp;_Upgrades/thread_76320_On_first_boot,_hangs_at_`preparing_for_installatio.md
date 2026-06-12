---
title: "On first boot, hangs at `preparing for installation ... 0%'"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by xerxesdaphat on 2005-10-14
Hi. I downloaded Ubuntu 5.10 off torrent, checked the MD5 (was fine) and burnt the cd. Installation seemed to go ahead ok... except for during the `copying remaining packages to hard disk' stage it failed during that, although it said it was ok with that because thats only so I don't need the install cd later, right? Anyway, installation continued fine after that, and I reboot it. It gets past the splash screen with all the usual bootup messages (apart from hotplug which instead of showing `ok', simply didn't display anything but it continued on to the next items so I assume its ok?). Next, it goes into textmode and says `Preparing for installation' and simply hangs at 0%. There's no HDD activity or anything... I left it for quite some time. Please could you help me with this problem? I would really like to use Ubuntu (everytime I try to foray into linux my progress is thwarted somehow...).

---

### Post by stuporglue on 2005-10-15
First thing I'd do, is just try the installation again. If the same problem happens again, then it wasn't just a quirk. 

Can you check the MD5 of the install CD against the downloaded file too? Just to make sure the CD burning happened correctly.

---

### Post by xerxesdaphat on 2005-10-15
Fixed! Ahh. CD was a wee bit broken I think, because when I re-burnt it using DAO instead of TAO (Nero's default for burning images) and burnt it at 4X, it now works perfectly... thank you very much! So, if anybody else gets weird issues: reburn your cd at slower speed. Thank you!

-Tom

---

### Post by Roobert on 2005-12-08
I had the exact same problem as you.....Ubuntu hangs at 0% when installing packages. But I know that the CD must be OK, because I already did a perfect install on the same computer with the same CD! 

Some background: I had a perfect Breezy install working. For some dumb reason, I renamed my home directory with

```
sudo mv /home/eric /home/epatton
```

and then everything was broken after that. I couldn't login past the startup screen. So then I though I would just re-install from the CD. Ok, fine. I got as far as partitioning, but after that the install failed and I never got to the part where GRUB is re-installed. So GRUB was broken too, and then I couldn't even boot Windows anymore (dual boot PC). Soooo.....I re-installed again from the CD, and got as far as I mentioned in the first paragraph. Should I re-install again? I'm really afraid of having to lose all my Windows stuff by re-formatting the hard drive. That is DEFINITELY not an option.

---

### Post by meowmeow on 2005-12-12
Hi guys

Had the same hang on `preparing for installation ... 0%'
In my case it was because there was no installation cd in the cdrom! An Ubuntu did not ask for! =:(

Greetings,
Meow

---

### Post by padraig on 2005-12-16
[QUOTE=meowmeow]Hi guys

Had the same hang on `preparing for installation ... 0%'
In my case it was because there was no installation cd in the cdrom! An Ubuntu did not ask for! =:(

Greetings,
Meow[/QUOTE]

Thanks, this helped me when my latest installation attempt (after a failed upgrade) stalled at "preparing for installation" on the first reboot. I took the CD out and after grub had started booting into the kernel on the hard disc I quickly inserted the CD so it had spun it up and read it before the installer started looking for the rest of the modules. 

Fingers crossed for the rest of the install - it hasn't been easy so far :-(

(I have used *most* distros and would have kept looking if this install had been my first experience of Ubuntu - thankfully it wasn't :-)

---

### Post by damian_ on 2006-04-18
haha. Thanks meowmeow! I asked in a couple of Ubuntu IRC Channels, no one could help .. One forum later, TADA!

---

### Post by NodlezFodlez on 2006-04-18
I was having the same problem!

meowmeow is right, if anyone is having this problem, reboot with the cd in the drive!

I officially love this forum now :D

---

### Post by sion2k on 2006-04-27
Amazing...i still can't believe i didn't think about that...thanks alot meowmeow...another headache avoided....

---

