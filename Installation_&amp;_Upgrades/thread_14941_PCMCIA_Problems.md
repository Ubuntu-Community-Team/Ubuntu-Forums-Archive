---
title: "PCMCIA Problems"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by Rafael Pais on 2005-02-10
Hi...
My Name is Rafael Pais, from Portugal...

Today My School Gave me the Ubuntu Cd's... I have 2Cds... One is LiveCD and the another one is the Instalation CD.

First I tried the LiveCD on my PC and looks good... The sound works, etc...

But i tried on my Toshiba M30X-128 and it doesn't boot... It stops on "Starting PCMCIA". And i can boot unsing FailSafe Mode.
After this, i tried the instalation cd and after selecting my county and my keyboard, it stops on "Starting PC Card Services".....

Can you help me?? Thanks a lot...  :mrgreen:

---

### Post by nadador on 2005-02-11
Hi Rafael,

You have to choose the following option upon booting:
           
     hw-detect/start_pcmcia=false 

see help screen <F7>.

This appears to be a well known problem on Toshiba MX-30 (mine is a 113).

Good luck! (My installation hangs later, while trying to install the base system.)

---

