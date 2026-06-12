---
title: "mini iso"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by Dominic Waldron on 2012-06-19
Hi Everyone,

I could not install 12.04 because my  IBM T41 laptop didn't have PAE.

So I installed "mini iso".

When I  login and enter password I get this....

account name@dom-ThinkPad-T41:~$

What do I do now?

Thanks.

---

### Post by black veils on 2012-06-19
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

> To install, boot your computer from the the Minimal CD and type "cli"  (command line install) at the prompt.  You can then follow the  instructions from the text-based installer. After the base system is installed, log in, and type "sudo tasksel" to select the system to install. 


Edit:

using Space bar to select your choices, and Tab key to select OK etc

---

### Post by Dominic Waldron on 2012-06-19
Hi black veils,

Thanks. I have to go  now will try  your suggestion tomorrow.

---

### Post by black veils on 2012-06-19
this might be useful:  [http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24)

scroll to **Post Installation**

---

### Post by Dominic Waldron on 2012-06-19
Hi Blackveil, 

Thanks for that link. Perfect step by step instructions.  

All goes well up to "Configure the network" which fails each time on auto-configure.

When I select "Configure network manually" I am asked for IP address. I phoned my Internet Provider but they told me they change the number each time I use it!
Do you know how do I find this?

At this stage I feel maybe I'll just continue with my old 11.04 which has worked without problems for almost two years, but I am open to suggestions as all this is giving me a better idea of how it all works (or doesn't). 

Thanks.

---

### Post by black veils on 2012-06-20
you should try installing Lubuntu or Xubuntu, they will give correct kernel. if you dont like the desktops, and want unity, just install ```
unity
``` or ```
unity-2d
``` from within one of those distributions, then choose your session (desktop) at the login screen.


as for the mini, did you have it connected to the internet wired or wirelessly? you should try wired. i am unsure about network matters.

---

### Post by ovasilis74 on 2012-10-22
> **Dominic Waldron said:**
> ...
All goes well up to "Configure the network" which fails each time on auto-configure.

When I select "Configure network manually" I am asked for IP address. I phoned my Internet Provider but they told me they change the number each time I use it!
Do you know how do I find this?...

Hope didn't come late.
I think you need to put the IP address that tour modem/router gives to your PC, not the IP that your ISP(Internet Provider) gives to your modem/router.
It can be found in the routers menu putting its address in a browser(Firefox etc). It's something like 192.168.1.1, 192.168.1.254 or different last 2 numbers. Normaly you find it in the instructions that come with your modem/routerfrom the ISP.
Possibely the modem does not give the same IP after each boot of the PC, so have it in mind.
Good luck.

---

