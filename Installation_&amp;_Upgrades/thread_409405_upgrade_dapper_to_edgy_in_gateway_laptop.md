---
title: "upgrade dapper to edgy in gateway laptop"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by scarab on 2007-04-14
just did the official upgrade (via update manager) from kubuntu 6.06 to 6.10...

I only have one new unsolved problem, and one problem that persists since I had dapper....
hope someone will can give me some tip on how to solve them, I am not an absolute beginner, but do not have many experience yet...

my notebook is a gateway mx6447

1. I can no more set up monitor brightness... in dapper, I did it by pressing Fn and up/down arrow.... now it does work only when booting up, but not inside kubuntu. volume setting with Fn and PgUp/PgDn works perfectly. that is important for me because I work in a place with very variable external light.

2. I have sound only for output, not input. sound card is recognized by alsamixer as  HDA ATI SB with a  SigmaTel ID7634 chip. opening alsamixer, "capture" is simply empty, and output has only Master and PCM mixers. That was the exact case when I had dapper, so that it is not something I loose with upgrade to edgy, but it is something I really need to fix up, as I need to use Skype.

any suggestions? I already know my sound card is a problematic one, and already tried some suggested solutions for similar (not exactly same) problems found in other forums, with both dapper and edgy.

thanks in advance!!!

---

### Post by zvacet on 2007-04-14
I don´t know about first but you can set sound in proggrams>sound & video>sound cotrol>edit

---

### Post by scarab on 2007-04-14
thank you very much, but I cannot find that menu (meybe because I am in Kubuntu?)...

I tried under K>System Configuration> Sound, and didn't found anything help me... I have it setted to ALSA, and only Full Duplex checked. should I check some other thing? what?

under K>System Configuration> Monitor & Video (sorry, it is in Portuguese, maybe names would vary...), hardware is configurated as generical plug and play. there are SEVERAL Gateway monitors, I do not know if I could check one, but in that case which one?

is there any other information I could supply that would be of help?

---

### Post by zvacet on 2007-04-15
Sorry,I overlooked you are runing Kubuntu.in Alsa chek master,Pcm,PC speaker,CD.For video I can not help you.

---

### Post by scarab on 2007-04-15
I do not have those possibilities... those are not as acheckboxes in sound configuration here.

alsamixer ONLY shows Master and PCM, capture is empty, and I simply do not know where to activate it....

maybe I should open some other sound configuration tool I am not familar with?

---

### Post by erothoff on 2007-04-19
This is a comment problem with this driver. Most people that I have read, upgraded to alsa 1.0.14rc3 to solve it.    It is a driver issue, not a configuration issue. I know they were working on that bug fix with the new Fiesty Fawn which should be out today, but I don't know for sure if they fixed it. Good Luck

---

