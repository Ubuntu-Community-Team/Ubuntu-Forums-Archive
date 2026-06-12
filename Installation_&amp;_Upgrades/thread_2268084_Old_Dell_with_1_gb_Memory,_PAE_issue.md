---
title: "Old Dell with 1 gb Memory, PAE issue"
date: 2015-03-06
forum: Installation &amp; Upgrades
---

### Post by dal2 on 2015-03-06
Hi All !!!!
Hope one you can come with a solution. 
I've got and old XP machine which has now got infested by my 6 yr old going on various online game places.... Anyways it's about time a got of the xp as it's been left to die so I downloaded Mint ; ubuntu, Bodhi,...All these are not installing !!!

So each time I get the PAE disabled message 

I tried this 
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

However it will not let me go to F6 - other options!

So now it looks as though it might me a script that I have to type in??? Not sure but hoping for some solutions so that I don't have to buy another machine!


Thanks
covspa

---

### Post by mörgæs on 2015-03-06
Hi, welcome to the fora.
Did you try Lubuntu?

---

### Post by Bucky Ball on 2015-03-06
Welcome. With 1Gb of RAM I would attempt to install Lubuntu or Xubuntu and see if you get the same issues. Forget Ubuntu. That is not going to perform well.

* Ninja-ed by morgaes! Yes, try Lubuntu.

---

### Post by sudodus on 2015-03-06
Yes try Lubuntu. I have an IBM Thinkpad T42 with Pentium M and it works well with all new versions of Lubuntu. I suggest that you download the Lubuntu 14.04.2 LTS desktop i386 iso file from [https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS](https://help.ubuntu.com/community/Lubuntu/GetLubuntu/LTS)

See also these links

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by Alienman24 on 2015-03-06
I've run into this problem myself on some of the eeepc's my first grade students use.  The solution I found that worked best was to use the legacy version (not just the 32bit version) of bodhi linux.  This version is specifically designed to work with the PAE issue.  Just go to: [www.bodhilinux.com](www.bodhilinux.com) and on the right hand side click on _legacy_.  The iso you download can be burned to a usb with unetbootin or rufus.

---

### Post by MAFoElffen on 2015-03-06
> **dal2 said:**
> So each time I get the PAE disabled message 

I tried this 
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

**[COLOR=#ff0000]However it will not let me go to F6[/COLOR]** 
So, it had XP, so it probably is not new enough to boot via USB... So I am assuming you are booting via an optical disk right?

At the first panel, a dark aubergine purple with an icon at the bootm containing a keyboard and a person... > press <Escape> at that panel. That should get you to the Advannced Install Menu shown in the link you posted. (That info was missing from those instructions.)

If you don't do that, then it tries to boot normally, into a full graphical install with default kernel boot options, which for you would fail.

You would have to do the same on an Lubuntu LiveCD.

---

### Post by gordintoronto on 2015-03-07
Just how old is the machine? What CPU? Generally speaking, 1 GB is fine for Xubuntu or Lubuntu.

---

