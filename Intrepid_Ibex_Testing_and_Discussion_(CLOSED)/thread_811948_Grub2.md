---
title: "Grub2"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Josh04 on 2008-05-29
Will Grub2 be included in II by default? I'm currently using the version in the hardy repos and it seems very stable, and a good improvement over Grub Legacy.

---

### Post by talkingwires on 2008-05-29
I'm not a developer, but it probably won't be used by default. Distros seem to be very conservative when it comes to fundamental things like the bootloader. Does anyone know *any* distro is shipping Grub2 as the default bootloader?

---

### Post by olskar on 2008-05-29
What are the good improvements?

---

### Post by smartboyathome on 2008-05-29
Grub2 improvements can be viewed [here]("http://www.gnu.org/software/grub/grub-2.en.html"). Biggest ones, imo, is that it comes with a graphical interface by default and that it now has a rescue mode, which saves you from all the Stage 1.5 errors (Stage 1.5 was eliminated because of this).

EDIT: According to [the FAQ]("http://www.gnu.org/software/grub/grub-2-faq.en.html"), it won't be stabilized until November of this year, which would be too late for II, especially considering it is one of the most important portions of Ubuntu. I would say expect it for Intrepid +1 at the earliest.

---

### Post by syxbit on 2008-05-29
not to burst your bubble, but grub2 was supposed to be stable years ago.
it's been in dev for around 4 years.
i wouldn't get your hopes up.
they talked about making it default for dapper

---

### Post by Josh04 on 2008-05-29
> **syxbit said:**
> not to burst your bubble, but grub2 was supposed to be stable years ago.
it's been in dev for around 4 years.
i wouldn't get your hopes up.
they talked about making it default for dapper

Consider my bubble burst :P

---

### Post by caryb on 2008-05-29
I remember installing it in edgy, oh the problems! I wouldn't install it till it is officially released.


2c Cary

---

### Post by quickshade on 2008-05-30
Ran it a few weeks ago and it was fine. They said that development is taking so long because even one bug can cripple the OS and a computer, so they are testing it really hard. It seemed to work ok for me, but considering it's not something you can just remove or switch to terminal to fix....I'm not going to fully use it until it's released. Although when it is released it's going to go above and beyond any other bootloader.

---

### Post by Gina on 2008-05-30
I too will hang-fire on that one.  The current GRUB is adequate - I enabled and set up colours to make it look a bit prettier.  I now use QGRUBEditor (in the repositories through Synaptic) to edit my menu.lst.

---

### Post by gnomeuser on 2008-05-30
As the Free Software comedy genius Matthew Garrett put it: "GRUB2 will be the ultimate bootloader for the HURD"

---

### Post by plun on 2008-05-30
> **gnomeuser said:**
> As the Free Software comedy genius Matthew Garrett put it: "GRUB2 will be the ultimate bootloader for the HURD"

Well.. I don't believe any main stream user is interested in Hurd...:)

For the software religious "sect" maybe....  0.0001% users


"On topic" it seems that maybe Grub2 passed the unstable stadium and maybe 
is worth a try.

---

### Post by disturbedite on 2008-05-31
> **Gina said:**
> I too will hang-fire on that one.  The current GRUB is adequate - I enabled and set up colours to make it look a bit prettier.  I now use QGRUBEditor (in the repositories through Synaptic) to edit my menu.lst.
bah!  i always thought those grub editors were/are such overkill.  the grub menu.lst file is pretty straightforward & easy to understand, why does anyone need anything but a text editor to edit it?
then again, i know some ppl prefer frontends for everything...frontends usually make things easier, but in this case, i don't think they do as far as offering more functionality.

---

### Post by ShirishAg75 on 2008-06-04
While it may be true that Grub 2 has been in development for 4 years, but what's also equally true is that if distros start supporting an alpha or even a beta package the **possibility** of that package becoming stable is much more than not being supported. I have been using grub2 since almost a yr. and I feel good that I don't have to touch the menu.lst conffile for anything. the new GRUB does updates automatically and is also better looking than grub. Looks-wise the roadmap for GRUB 2 is going to be a killer ;)

---

### Post by ShirishAg75 on 2008-06-04
> **plun said:**
> Well.. I don't believe any main stream user is interested in Hurd...:)

For the software religious "sect" maybe....  0.0001% users


As far as Hurd is concerned, if the micro-kernel is stable and one can have drivers on the fly it would really make sense. My system could live for few more years that way for AFAIK monolithic kernels like the Linux kernel take more system resources then micro kernels like Hurd would. Of course, I also see the issues that Hurd is going through.

---

### Post by RAOF on 2008-06-04
> **ShirishAg75 said:**
> As far as Hurd is concerned, if the micro-kernel is stable and one can have drivers on the fly it would really make sense. My system could live for few more years that way for AFAIK monolithic kernels like the Linux kernel take more system resources then micro kernels like Hurd would. Of course, I also see the issues that Hurd is going through.

Actually, the reverse is true.  Mircrokernels generally incur a performance hit compared with monolithic kernels - because all the kernel subsystems have a separate memory space, you need to do message passing (and, if I understand things correctly, context switches) between subsystems.

---

### Post by Unix_Slayer on 2008-06-04
> **disturbedite said:**
> bah!  i always thought those grub editors were/are such overkill.  the grub menu.lst file is pretty straightforward & easy to understand, why does anyone need anything but a text editor to edit it?
then again, i know some ppl prefer frontends for everything...frontends usually make things easier, but in this case, i don't think they do as far as offering more functionality.

I agree, but you forget about the new users. It needs that frontend to make it easier for people who don't work with binaries regularly.

---

### Post by caryb on 2008-06-04
> frontends usually make things easier, but in this case, i don't think they do as far as offering more functionality.

I can think of a exception, Xorg 7.3 removes the bulk of the conf file so you can't easily force a particular screen resolution.


Cary

---

