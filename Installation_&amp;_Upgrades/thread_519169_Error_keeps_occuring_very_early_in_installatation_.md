---
title: "Error keeps occuring very early in installatation progress"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by nilfisk1 on 2007-08-06
Hi there,

First of all you should know I am a complete newb when it comes to linux, so eventhough the solution might seem obvious to you experts, I am realy only beginning to learn about it. Second of all english is not my native language so I'm sorry if the spelling is messed up.

My problem:

I am trying to create a multi os system ( windows xp / linux ubuntu ). I downloaded the iso from ubuntu.com and burned it to a dvd-r ( I don't know if that's a problem? Should it be CD? ). I formatted one partition of 15 gigabytes to ext3 filesystem using norton partition magic. This worked fine. Then I booted from the Ubuntu dvd and the menu pops up like it should. I hit try & install Ubunt ( or something of that nature ) and it starts loading the kernel. As far as I can see this goes fine. Then I get the ubuntu logo, with that orange loading bar beneath it. After about 30 seconds or so, the little orange thingy stops moving. And thats it basicly, I have waited for about 7 minutes then I restared my computer. I tried 2 more times, the same happens. Then I hit the check cd for errors in the boot menu ( of the ubuntu dvd ), and it gives me this error: /bin/sf/: Can't access TTY; Job Control Turned Off.

That's it realy, I hope you people can help me with this.

Thanks in advance,

Nils

Edit:

I guess it can't be my HD, since thats only used after you actualy hit install right?

---

### Post by Pumalite on 2007-08-06
Post your specs please.

---

### Post by nilfisk1 on 2007-08-06
well, I have 512 MB RAM ( Dual Channel )
ASUS EAX600XT Videocard ( 128 mb memory )
Onboard sound chip

One thing that might be of importance, I have a LG drive in my computer, it does get power ( opens closes  etc) but does not get recognised by the bios or by windows. could that have anything to do with it?

What other specs of my machine would you like to know?

---

### Post by Pumalite on 2007-08-06
Go to BIOS>IDE Configuration>Set to Enhanced support for PATA+SATA. Save your changes and try again. If you continue to have problems, post again; I still have other ideas.

---

### Post by nilfisk1 on 2007-08-07
I read somewhere on another forum about a strange workaround, keep a floppy in the floppy drive while installing. This worked ( don't ask me why, but it did ).  Flawless installation.

Thanks for your help!

---

