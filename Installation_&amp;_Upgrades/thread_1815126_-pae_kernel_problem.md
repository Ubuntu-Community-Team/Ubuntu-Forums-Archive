---
title: "-pae kernel problem?"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2011-07-30
During tests with 11.04, I met very big problems on my HP ProBook 6550b, which is all intel , but rather recent hardware, so it is 64bit .

When I install ubuntu, the -pae kernel is installed by default.

All did work so far with 10.10, but with 11,04 I get frequent crashes, particularly all kind of browsers will crash every few minutes, no way any flash will work, also office seems to freeze the system very frequently. This regardless if the 11.04 is run from life CD or installed properly.

Somewhere I read, that such behavior was cured when the -pae kernel was replaced by its normal (non -pae) variety.

Any experience with that?

On a very old toshiba, with some old celeron, I may not have the initial performance, but crashes are 90 percent less frequent, as there ubuntu chooses non -pae kernel automatically. Therefore I am thinking the -pae kernel could be the problem.

---

### Post by gordintoronto on 2011-07-30
The HP ProBook 6550b is a large family of computers, so naming it does not tell us much about the specs of the machine.

I assume it has 4 GB of memory or more, or it wouldn't use the PAE kernel. Is there some reason you didn't choose the 64-bit version of Ubuntu? I have been using it for two years with no problems.

Your computer has one of those weirdo switchable Intel/ATI graphics setups. My guess is that the switchable graphics are more likely to cause trouble than the pae kernel.

You should have no crashes at all!

---

### Post by ottosykora on 2011-07-31
well my 6550b is all intel, also graphic is intel, nothing exotic.

the 64bit version I did not choose, as many problems with it were reported by other people and I was simply recomended to use the 32bit which did work almost fine up to 10.10.

From 11.04, nothing seems to work properly any more, permanent crashes of apps, mainly browsers, possibly some incomapatibility with graphic too, as apps with bigger graphic use crash fastest.
So it is not possible to run any flash on it, as the flash itself reports crash,  or the browser it was started from.

This regadrless of using unity, or classic-no effects gui.

As the problems are present also when runnig from life CD, it does not look as being problem of a particular software, but rather of some general issue with 11.04.

On my very old toshiba, the unity will not work propely, ok, but classic-no effects works, or at least problems are different and managable.

---

### Post by ottosykora on 2011-07-31
OK, tried now the 64bit version of 11.04

Works, did not crash so far, also browser did not crash so far, 
but

the software repository is still rather miniature when compared to 32bit.
My favoured apps are not existing in 64 bit yet. 
I tried to install flash for the browser, nothing found, the experimental from adobe tries to be installed , but the software center tells it does not exist.
Via flash-aid some experimental could be installed, works well so far.

My favourite VLC is not available and also my needed tool , the layouting called eagle does not work on this version.
Drivers for the GOBI mobile access is also not available.


So yes, one can use it as it comes out of the box, but thats about it.

does someone has other idea why the 11.04 does nothing but crashes on this HP probook 6550b, which is very generic intel M520/2.4ghz, intel graphics i5 and otherwise nothing very special.

---

### Post by gordintoronto on 2011-07-31
If you run Synaptic Package Manager and go into Settings, Repositories, you can enable all the software sources, then "reload". First thing to install is the "restricted extras." Synaptic has more than 33,000 packages, using 64-bit 11.04 with everything but source packages enabled. That's where I installed VLC from.

---

### Post by jocko on 2011-08-01
> **ottosykora said:**
> the software repository is still rather miniature when compared to 32bit.
My favoured apps are not existing in 64 bit yet. 
I tried to install flash for the browser, nothing found, the experimental from adobe tries to be installed , but the software center tells it does not exist.
Via flash-aid some experimental could be installed, works well so far.

My favourite VLC is not available and also my needed tool , the layouting called eagle does not work on this version.
Drivers for the GOBI mobile access is also not available.

As far as I know, every package that is available in the 32 bit version is also available in the 64 bit version. You just need to activate all sections in the repo.

Flash is available in the repos as a 32 bit plugin running in a wrapper (quite buggy the last time i tried it).
A much better alternative is to use Adobe's 64 bit flash plugin (despite only being available as a beta version, it is fully functional and stable). The easiest way to install it is to install the firefox addon [Flash-Aid]("https://addons.mozilla.org/sv-se/firefox/addon/flash-aid/").

Other than that, there are no significant differences in the packages available in the 64 bit version compared to the 32 bit version:

VLC is, and has always been in the universe section of the repo.
Eagle (if you mean the circuit board design tool) is in multiverse
Don't know exactly what you need for your internet access, but there is a package named "gobi-loader", a firmware loader for Qualcom Gobi USB modems. Could that be it? Also, the ModemManager (which is installed by default) does have a gobi plugin (libmm-gobi.so)...

---

