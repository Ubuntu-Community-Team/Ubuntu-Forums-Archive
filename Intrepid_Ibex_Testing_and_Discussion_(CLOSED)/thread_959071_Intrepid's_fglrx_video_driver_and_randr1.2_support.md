---
title: "Intrepid's fglrx video driver and randr1.2 support"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wired98 on 2008-10-26
Hi there,

I have a couple of questions concerning the newly announced randr support for the new fglrx beta version 8.10 which was included in Ubuntu Intrepid as reported on [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1"). The beta version was included due to the needed support for the xserver 1.5 that comes with intrepid.

I found the information that randr is supported experimentally from version 8.9 on as well on Phoronix (cf [this ]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1") article ).

So yesterday I got to excited about all that and I had try this new driver. I was always on the fglrx driver (since I started with ubuntu Breezy), but I got more and more annoyed with it due to the crappy dual monitor support. It was ok for computers where you never changed the setup, but for my work I was on the road often, and I also use the same laptop for work and at home. So, with always changing monitor setups on different output ports, this was really painful. So I changed to the radeon driver since hardy because like this I can change external monitors attached to my Thinkpad T42p effortless, even while the notebook is switched on (cf. [Thinkpad-FN-F7]("http://www.thinkwiki.org/wiki/Sample_Fn-F7_script") script). However, this decision increases my battery consumption as the powerplay support of the radeon driver seemes to be limited. So, I was very excited that randr finally would work with the otherwise more powerful driver.

After the install of the driver, I activated it through "Hardware drivers" from the kde4 menu and rebooted my machine. The first disappointment was, that it did not deliver randr functionality out of the box. You can see this by typing "xrandr" in the terminal while you have your external monitor connected. If you do so, two monitors with their respective possible modes should be listed. Well, this wasn't the case. So I tried to activate the randr support with the command, mentioned in the phoronix article:

```

aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

```

After rebooting again, xrandr really outputed information on both monitors. However, my desktop was rendered useless, it was horribly slow, there were strange rendering artefacts, and if issued a mouse click or something it took up to 30 seconds for it to get executed. So, it does not yet work for me, but at least there is something underway...

My questions are:
1. Has anyone running ubuntu intrepid with fglrx and WORKING randr support.
2. If yes, what did you have to do, to get it going?
3. Is this maybe less supported on older graphics adapters? I have an ATI FireGL Mobility T2 
4. Does anyone know if the randr support will be activated as default for the final version of the 8.10 driver?

Thanks for your help!

---

