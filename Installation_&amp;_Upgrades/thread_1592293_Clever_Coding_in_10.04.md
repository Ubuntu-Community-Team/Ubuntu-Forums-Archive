---
title: "Clever Coding in 10.04"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by 11b2p508 on 2010-10-10
Hi all,
I hesitated on the title, generally can solve problems w/o this (20+ year *nix/linux experience).  

hardware Dell 1505, ATI X1400 (nVidia went south replaced with ATI, used at this stage of life for this laptop).
Acer x221w external monitor.

Recently upgraded to 10.04 (should have waited, but hadn't upgraded in a long time).

No real fixes found for the ati X1400 in searches (fixed it on 9.04 and 9.10).

So to troubleshoot, wanted to go to console mode, and start X manually and hopefully debug the config to get the thing working.

So, I get ready to take it down off of X only to find, there are no more consoles???

To work this out and to even come to an end result, when X does not work, you need a console to debug it.  There is code in /etc/init.d/console-screen.sh for starting consoles...

Yet they do not start, notices some comments about doing it 'clever' in there, all I can say is 'clever' is more risky than workable, it worked before, why change it?  It did not make it better, it made it harder, so now, to get it to work, I have to go debug someone else's 'clever' code?  BTW, there are 'getty' running - but still no console.

Not so clever... We need a fix to get (at least at this level), the consoles running, so, where are you 'clever coder', tell us how to turn them back on.

Why in /etc/init/tty*.conf do they not start?

I really find it hard to say anything critical to something that is free, in general, I will not even comment, but just go ahead and find the fix myself, But to even address this, we (IMO) need pretty much a fix for the broken console access, before we can even address X in certain configurations.

A long time user of RH, even back to Yygdrasil, Soft Landing days, I was VERY impressed with ubuntu over the others for a desktop (got it on the Dell), but now, at 10.04, it has become cumbersome and broken.

It is a good product, but we need to get it back to where it is not so bleeding edge and broken.

---

### Post by nlsthzn on 2010-10-11
Greetings,

Could you please elaborate on "there are no more consoles".  Alt+Ctrl+F(x) still opens consoles for me... Or maybe I am not understanding? 


Regards
Neil

---

