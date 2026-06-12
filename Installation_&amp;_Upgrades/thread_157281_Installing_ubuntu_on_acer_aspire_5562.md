---
title: "Installing ubuntu on acer aspire 5562"
date: 2006-04-08
forum: Installation &amp; Upgrades
---

### Post by Reuven on 2006-04-08
Hi,

I use ubuntu on my desktop pc and i'd like to use it on my new laptop Acer Aspire 5562 with the Mobile Core Duo cpu.

I tried the Breezy Badger and any Development version, but it always stops as it starts booting the kernel, after the graphical boot interface.
I got this message:

Uncompressing Linux... Ok, booting the kernel.

And stop. Nothing else. It doesn't load anything.

Can anyone help me?

Thanks.

Reuven

---

### Post by spandon on 2006-04-09
Hi Reuven,
I have an Aspire 1654 and to test it out on the live cd I have to enter at boot the following:
**Live noapic nolapic, hw-detect/start_pcmcia=false, vga=771**
This works both in Breezy and in flight6 of Dapper.

For an installation, at boot enter:
**linux noapic nolapic, hw-detect/start_pcmcia=false, vga=771**
after installation, edit grub and append the above command line to the end of the kernal line.
Not having a dual core laptop, don't know if it will be the same, but try it out on the live cd first to test.
Enjoy
Don

---

### Post by Reuven on 2006-04-09
Thank you spandon.

I can boot my system specifying these parameters. 
The problem now is the video card, 'cause i've an ATI X1400...

I'll try to solve :)

Bye
Reu

---

### Post by lir on 2006-04-15
My god... Reuven, can you update me on how's it going for you
with linux and that laptop model?

I want to buy that exact model (Acer Aspire 5562) but I couldn't find
any useful information (like a howto or a proof that its actually supported)
on runing a linux distro on it until I was directed to this thread by a friend.


Can you please update me on how's it going for you with Ubuntu or 
any other distro and this model...? What is supported, what is not and
how did you come to solve it?


This is highly important for me,
please, if you can be of any help I'd be really thankful.

Sincerely,
Liran.

---

### Post by nolongerlivecd on 2006-04-15
[http://www.ubuntuforums.org/showthread.php?t=24557&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&pp=10)

Worked for me when configuring my 5504, predecessor of yours, no dual-core.

You'll need some dual-core configuring, and you'll also need to configure Wi-Fi, which I haven't. Check out [http://ipw3945.sourceforge.net](http://ipw3945.sourceforge.net) (i think)

---

### Post by lir on 2006-04-15
Thanks for the links and the reply nolongerlivecd but I think the 5504 is a whole different model than the 5562. I mean, you can see the specs for the 5562 in this link: 
[http://www.acer.com.sg/products/aspire5560/psp_aspire5560.asp](http://www.acer.com.sg/products/aspire5560/psp_aspire5560.asp)

and as you notice it's runing for example on an Intel 945PM Express chipset
while the 5500Z series (which I think your model qualify in) is runing a 915 chipset (if I remember correctly).

So I'm thinking that I'd have to find someone whose got the 5562 model runing linux to be completely sure... unfortunately I can't find one yet.


Anyway, about the duo-core... I don't think it's something that requires handling at all... I mean, it's something that is very very low level and is transparent even to the kernel (i think). I mean... I don't think there's a version for Windows XP for duo-core or even a driver for it but I could be wrong. Never dealt with duo-core before.



Any insight on this subject is very welcome,
Thanks.

---

### Post by nolongerlivecd on 2006-04-19
Yup, I know the differences... For one, you'll need fglrx at [http://www.ubuntuforums.org/showthread.php?t=24557&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&pp=10), then, you need to enable smp (don't ask me about it i don't know). Also, refer to the ipw3945 webbie i 7posted above.

---

### Post by Reuven on 2006-05-16
[QUOTE=lir]My god... Reuven, can you update me on how's it going for you
with linux and that laptop model?

I want to buy that exact model (Acer Aspire 5562) but I couldn't find
any useful information (like a howto or a proof that its actually supported)
on runing a linux distro on it until I was directed to this thread by a friend.


Can you please update me on how's it going for you with Ubuntu or 
any other distro and this model...? What is supported, what is not and
how did you come to solve it?


This is highly important for me,
please, if you can be of any help I'd be really thankful.

Sincerely,
Liran.[/QUOTE]

I'm sorry.. I've read your message today.
Anyway, i'm waiting for a better support for my pc, and i installed linux on VMWare now. I find this solution quite good if you need to use linux, but you have to run always windows.

For any info contact me.

Bye
Reuven

---

### Post by lir on 2006-05-17
[QUOTE=Reuven]I'm sorry.. I've read your message today.
Anyway, i'm waiting for a better support for my pc, and i installed linux on VMWare now. I find this solution quite good if you need to use linux, but you have to run always windows.

For any info contact me.

Bye
Reuven[/QUOTE]


I've managed to install Ubuntu Dapper Flight 7 and got fully support for
almost everything. give it a try.
I'm also using the 5562wxmi model (great laptop)

---

