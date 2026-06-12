---
title: "Problem booting USB stick on HP G71-340us"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by mrbrian200 on 2012-01-05
Boot from USB stick halts "syslinux 4.03 2010-10-22 ..." and flashing cursor.
Attempting to run USB live 11.10 x64, also tried natty and kubuntu 11.10 same results.
HP laptop G71-340us BIOS .23 (latest), Patriot XT 8GB stick. 11.10 x64 live .iso /unetbootin win 565 +4GB persistance. Machine boots iso on CD fine but optical not preferred for running a live session.
Anyone had this problem and solved on the G71 or like?
Note tested USB stick on an ASUS/AMD desktop and it booted/ran fine there.

---

### Post by serge_o on 2012-01-06
I am right now dealing with a similar problem.
This has to do with the way how Ubuntu startup disk creator (I suppose you use either this or unetbootin) makes USB sticks and the way how HP laptops see them.  long story, short: they do not like each other.

there  is a workaround hier in forum that worked for me: 
instead of using unetbootin perform this command
sudo dd if=yourubuntuisofile.iso of=/dev/sdc bs=1M

notice that /dev/sdC should be the letter where your USB stick got into the system, it might be a different letter for you. also notice the lack of a number, i.e. it is NOT /dev/sdc1, it is /dev/sdc.

after this the system boots.

One thing: I have not yet figured how to cater for a persistence file, working on this right now.


please write hier whether this solution works (i.e. that you are able to at least boot from it)



[mrbrian]Boot from USB stick halts "syslinux 4.03 2010-10-22 ..." and flashing cursor.
Attempting to run USB live 11.10 x64, also tried natty and kubuntu 11.10 same results.
HP laptop G71-340us BIOS .23 (latest), Patriot XT 8GB stick. 11.10 x64 live .iso /unetbootin win 565 +4GB persistance. Machine boots iso on CD fine but optical not preferred for running a live session.
Anyone had this problem and solved on the G71 or like?
Note tested USB stick on an ASUS/AMD desktop and it booted/ran fine there.[/QUOTE]

---

