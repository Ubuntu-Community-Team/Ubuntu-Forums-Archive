---
title: "Mppe"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by belred on 2005-10-14
someone posted this in another thread a while ago:

"Kernel in ubuntu support mppe patch by default !!!! 
 try find file like *mppe* in directory /lib/modules .... 
 or try command:
 modprobe ppp_mppe 
 If you don't see any message, your kernel support mppe"

in adept, if you look at the description of package "pptp-linux", it says, "MPPE (Microsoft Point-to-Point Encryption) is supported with the stock kernel."

i just upgraded to breezy today, and was hoping that mppe was in the kernel.

bryan@ubuntu:~$ uname -a
Linux ubuntu 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux
bryan@ubuntu:~$ modprobe ppp_mppe
FATAL: Module ppp_mppe not found.
bryan@ubuntu:~$

does this mean mppe is not supported with the stock kernel?  how do i get it installed?

thanks,

bryan

---

### Post by Enrique on 2005-10-18
Hi, I just installed Breezy and got pptp working on linux.

As you say, thanks guys for that, kernel (mine is 2.6.12-9-686-smp) seems to support mppe by default. In order to check that try

sudo modprobe ppp-compress-18

if you don't see any message, you are ok.
Next, check that pppd program contains MPPE support by entering

strings `which pppd`|grep -i mppe|wc --lines

if you get a number, you are ok. I get 43. 

All this is from [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_kernel]("http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_kernel")

Next thing is to install pptp-linux and configure pppd. I would recommend you to read through 

[http://pptpclient.sourceforge.net/howto-debian.phtml]("http://pptpclient.sourceforge.net/howto-debian.phtml")

There you'll find a front-end for your VPN connections. If it is the first time you use pptp on linux, I suggest you also read [http://pptpclient.sourceforge.net/routing.phtml]("http://pptpclient.sourceforge.net/routing.phtml")

Hope this is of any help.

---

### Post by TheOrangeRider on 2006-01-15
[QUOTE=Enrique]
As you say, thanks guys for that, kernel (mine is 2.6.12-9-686-smp) seems to support mppe by default. In order to check that try

sudo modprobe ppp-compress-18

if you don't see any message, you are ok.
Next, check that pppd program contains MPPE support by entering

strings `which pppd`|grep -i mppe|wc --lines

if you get a number, you are ok. I get 43. [/QUOTE]

Hi,

I verified that I have mppe support using the above checks, but I suspect that the mppe doesn't include 40-bit encryption only 128. The reason that I believe this is becuse when I try to connect to my vpn pptp-config gives me the message:

```
Disabling 40-bit MPPE; MS-CHAP LM not supported
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x1 <mppe +H -M -S +L -D -C>]
MPPE required but peer negotiation failed
```

The L flag means 40-bit MPPE, the S flag means 128-bit MPPE. So it looks to me like my vpn server only supports 40-bit MPPE, while I can only do 128. I don't have the Refuse 40-bit encryption option checked in pptp-config.

So I'm wondering if there is a way I can tell for sure that I do not have 40-bit encryption supported, and how could I get it?

Thanks!

EDIT: Looking at the source code, the "Disabling 40-bit MPPE; MS-CHAP LM not supported" message (kinda obviously) means that it's disabling 40-bit MPPE because MS-CHAP LM is not supported. Anyway, now I must find out what MS_CHAP LM is not supported and how to get it supported

---

