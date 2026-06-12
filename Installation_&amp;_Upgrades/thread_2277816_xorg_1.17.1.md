---
title: "xorg 1.17.1"
date: 2015-05-11
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2015-05-11
Hi,

I've been trying to upgrade my xorg due to lacking the correct version. [Gallium Nine]("https://wiki.ixit.cz/d3d9") requires 1.16 and I'm stuck with 1.15.1.

Is there anyone who can help me upgrade it? Been trying to find a proper guide on this one. Either I've gone blind or there are none.

Regards.

---

### Post by Bashing-om on 2015-05-11
pingaan; Hello;

My 1st thought is to enable HardWare Enablement stack .
Are you aware ?
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
This might serve your purpose.

[INDENT][INDENT]hey, It could happen
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-05-11
X.Org Server 1.17 is in Ubuntu 15.04. 

[http://www.phoronix.com/scan.php?page=news_item&px=xorg-server-1.17-ubuntu-15.04](http://www.phoronix.com/scan.php?page=news_item&px=xorg-server-1.17-ubuntu-15.04)

I am not sure if it is in the repositories of older versions but if we look for it in Synaptic Package Manager we should search for xserver-xorg-core. I do not think that 14.04 will get the 15.04 hardware enablement stack until 14.04.3 is released in August this year. 

Regards.

---

### Post by Bashing-om on 2015-05-11
@grahammechanical :)

That boundless bucket of experience/knowledge .
Me thinks you draw deeply from it .

As always your insight is much appreciated .

[INDENT][INDENT]what would we be without
[/INDENT][/INDENT]

---

### Post by pingaan on 2015-05-12
I forgot to mention that I recently upgraded to 14.10. I thought the 1.17 release was for 14.10 as well. 
I can settle with 1.16. 
That's probably the reason to why it's not working then, eh?

With  that said can you point me in the right direction of proper ppa?

@bashing-om, isn't that enabled by default?

Cheers.

---

