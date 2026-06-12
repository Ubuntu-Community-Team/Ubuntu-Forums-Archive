---
title: "BootiIT NG , &quot;expert&quot; install no grub or lilo to hda1"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by boutros on 2005-06-25
hello all,

posted yesterday about the default install taking over and installing grub to mbr. Bad, bad, bada!!! for me!:) see post "grub to / not mbr???"

tried expert install as Xian suggested. tried to install grub to hda1 which is the root part and it gives a red screen and an error. TRied to go with lilo, which gives the option of root (hda1) error for lilo install also.

Strange i have never had any problem using my own bootloader and installing grub/lilo to /. Any ideas? 

thanks,
Boutros

---

### Post by mingus on 2005-06-25
[QUOTE=boutros]
Strange i have never had any problem using my own bootloader and installing grub/lilo to /. Any ideas? 
[/QUOTE]

That you cannot install either grub or lilo to hda1 is not good - that suggests a problem in the partition table.  When you went back thru the install process, did you repartition and reformat the disk?

Even though you have successfully used BootIT with linux loaders before, that is no guarantee it will work now.  There are variables, and so while one configuration works another may not.  I seem to recall another similar product that completely takes over the partition table and maintains its own extra logical partition extensions.  As you know, the general rule is that mixing partitioners or mixing bootloaders is a no-no.

---

### Post by boutros on 2005-06-25
hello and thanks for the info,

not sure if this info helps. but have recently had mepis and vector installed on the same parition, that i tried to install ubuntu on. Mepis uses grub and vector lilo. I had no problem installing  grub or lilo to /hda1,  and then using bootit to access the parition and grub/lilo to boot linux.

thanks again for your response i will check that parition table. 

peace,
boutros

---

### Post by Xian on 2005-06-25
[QUOTE=boutros]Strange i have never had any problem using my own bootloader and installing grub/lilo to /. Any ideas? [/QUOTE]
Well, as I mentioned I get this all the time. For me, the fix is to return to the installation menu (after it fails), select the grub install step and do the procedure again. For whatever reason it is only on the second attempt that it completes the bootloader configuration. I would say this was just a lark on one of my Ubuntu installs, but I've seen it happen repeatedly and have grown rather used to the occurrence.

---

### Post by boutros on 2005-06-25
hello Xian,

i may try the install routine again. I tried to install both grub and lilo least twice, and still got the errors but i may give it a go again. I have decided to dload the live cd and try it out on my laptop. and if i can get my wireless card and lan working with minimal hassle, I will do the expert install again.

i appreciate everyone's willigness to help. :)

Peace,
boutros

---

