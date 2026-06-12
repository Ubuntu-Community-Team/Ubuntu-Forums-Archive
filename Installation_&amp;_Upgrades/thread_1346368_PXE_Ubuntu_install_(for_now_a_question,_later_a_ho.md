---
title: "PXE Ubuntu install (for now a question, later a how to)"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Andrew Buchinger on 2009-12-05
So I am new to Linux as a network base and I have a few questions about what linux builds or add-ons I can use for for DHCP and for PXE targeting. 

If you know of multiple builds / distributions feel free to mention them and why you don't think they are good.

Next I was wondering if anyone knows how to configure PXE linux to point to a distribution that I have on a file share/internal site on my network so I don't have to waste bandwidth

The final step is can someone please point towards a good how to on building or stripping Ubuntu to fit specific hardware sets and to remove and add packages like games, then have it all ready for the PXE distribution.

The last thing I will be doing is putting together a step by step in this thread on what I find. I will put credit where credit is due in each section as I write. I expect this project won't get out of the research phase until after February, because I have holiday time off and then I have a business trip until mid February starting in January, but I would love to have plenty of material to work from (and distract me from boring meetings/presentations)

When I am done this thread should be a one stop shop of "how to" for people looking to do simple network distribution of Ubuntu in their home, or an enterprise level customized distribution. Thank you in advance for anyone that helps.

---

### Post by Andrew Buchinger on 2009-12-05
Current Status of this project : Looking into MOTU to see if it will cover my packaging tutorial needs for creating custom package sets for distro. . . (It may be to deep into the rabbit hole for me for now.)

---

### Post by Andrew Buchinger on 2009-12-05
OK that seems both deeper than what I need and at the same time what I need for something else I was considering. I don't need to edit and compile packages, just control which packages are installed with the distro. Later on when I have an Ubuntu IV I would like to be able to do this so if I ever step into an environment where I am ACTUALLY deploying Ubuntu on an enterprise level I can customise how things like apt-get work (IE make it so the only repository is one hosted locally that I maintain, so the people working in the company can't just install all the free games , but they can get to tools the company would need)

---

