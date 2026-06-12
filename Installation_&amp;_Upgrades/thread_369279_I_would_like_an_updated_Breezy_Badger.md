---
title: "I would like an updated Breezy Badger"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by mengfei on 2007-02-24
Hi there!

I have a Thinkpad T22 that I have been struggling with forever to get working with Ubuntu.

I've finally gotten the S3 Savage working, among a myriad of other problems. I still can't get it to sleep though, haha.

Well, I went out and bought a 2Wire Hermes chipset orinoco-gold based wireless PCMCIA for the laptop, as I heard these things work beautifully with linux.

And guess what? It doesn't.

A little more research informed me I needed the 2.6.12 Kernel... in other words, I need Ubuntu Breezy Badger (which I still have the shipit CD of, yaay!)

Now, the problem is, I would still love to have all these neat programs in Dapper/Edgy.

:EDIT:

I've also thought about using other linux distros... and actually have tried a whole bunch too!

But I don't think they're a solution for me. A majority of them that I find are suitable for me use KDE, which I'm not too fond of. And Mandriva linux, which has the option of Gnome, makes gnome all ugly and muddled.

So the reason for me wanting to stick to Ubuntu so bad is basically its presentation, haha.

If I can't get the wireless working, then I HAVE to go back to windows :'(

I'm at Penn State, it's a big school, and I need to rely on my laptop for wireless connectivity wherever I go.

Is there a way for me to keep it so that it is Breezy Badger's kernel. yet have the updated look, as well as programs? I hope I don't have to go about re-compiling the kernel or anything.

Thanks so much for your help
Meng-Fei

---

### Post by solar george on 2007-02-24
> I hope I don't have to go about re-compiling the kernel or anything.

Recompiling the kernel is not as scary as it sounds.

You could try adding the breezy cd to synaptic and do a search for "linux-image" if you can find the 2.6.12 kernel there just install it - there will be a option in the grub menu at startup for the kernel. Just select it and it should work.

---

### Post by patwack on 2007-02-26
i have a T22 too and and orinoco based pcmcia card which works absolutely flawlessly out of the box on dapper and edgy, all i have to do is put in my essid and wep key when the installer asks me.

what exactly doesn't work for you, does it not detect the card or doesn't it connect to the network?

---

### Post by mengfei on 2007-02-26
My PCMCIA card is 2Wire.

It is detected fine in Networking, but using network manager or wifiradar does not pick up any signals at all, even ones in the same room.

Kwifimanager does detect and seems to connect, but I can't go on the Internet or anything.

For now I've switched back to Windows; I spent my entire weekend trying to figure this out instead of doing the studying and homework I should've done:(

---

