---
title: "ERROR:PAE when trying fresh install"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by de Bacon on 2015-01-15
I am trying to revive an old laptop for a friend.  It is a Dell Latitude D600, ventage about 2005 I think? Has a pentium M processor 1600MHz, with marginal ram of 768 Mb.
It has ubuntu 11.10 on it, but since that is beyond life, though it works as is, it should be upgraded to a later version.  So I retreived a 32bit version burned it to a disk but when I try using it, I get the following message:

```
ERROR : PAE is disabled on this Pentium M (PAE can potentially be enabled with kernel parameter "forcepae" -this is unsupported, may cause unknown problems, and will taint the kernel) This kernel requires the following features not present on the CPU: pae
Unable to boot - please use a kernel appropriate for your CPU
```

I have no idea how to enable PAE with the command "forcepae" nor do I believe that a viable option, but in truth I don't know.  

Can this machine take 14.04.1?  I thought of maybe getting a version of xubuntu or even lubuntu, but I don't know that it would be worth the effort, being as ignorant about this stuff as I am.  I have by chance a 32 bit version of 10.04, from some reading I went through in trying to find answers through searches maybe I could load that, then upgrade to 12.04.  I don't have a 32 bit version of 12.04, so I don't know how else to get from nowhere (as I am now) to anything else.  I really don't know that one can upgrade from 10.04 any longer either?  

Anyway, I hope someone knows how to work around this.    Oh, I did try a 32 bit verson of ubuntustudio 12.04 but got the same error message quoted above.  

I guess another question, where would one find a download of 12.04 now?

My own desktop system is 64 bit so those disks are invalid.  

Thanks for any assistance.

---

### Post by mörgæs on 2015-01-16
A fresh install of Lubuntu 14.04.1 or 14.10 with forcepae is your best option.

---

### Post by de Bacon on 2015-01-16
Yes, but what is "with forcepae"?  Where does one get forcepae?  I think that is a command (unsure) but where, how, and when, to employ it, is unknown to me.

---

### Post by mörgæs on 2015-01-16
[https://help.ubuntu.com/community/PAE/PentiumM](https://help.ubuntu.com/community/PAE/PentiumM)

---

### Post by de Bacon on 2015-01-16
Thank You, I'll check it out.

---

### Post by sudodus on 2015-01-16
I think that old Dell will run rather well with ***Lubuntu 14.04.1 LTS*** and the boot option forcepae as suggested by mörgæs.


But there might be problems with the graphics and/or wifi chip/card. In that case

- please post the specification of graphics/wifi, and you might get tips what to try

- and you may have better luck with a light-weight community re-spin ***based on Ubuntu 12.04 LTS***, which promises support until April 2017: ***Bento, Bodhi, LXLE***.

---

### Post by de Bacon on 2015-01-16
Again thanks to all for the assistance,
I have taken steps toward loading lubuntu 14.04 on this machine.  I now have the boot disk ready to use.  Next step is trying to use the forcepae command.  I guess I will fumble around and see if I can figure that one out.  I am sure I know where that is found, it is a matter of typing it in within the correct location, with proper syntax.  Thus far I have not done the look to see if...   I have had to use some of those kinds of options in the past, though just the basic ones that are provided completely in those menues.  That was years ago, when my own hardware was new and in need of special treatment for installation of ubuntu 8.04.

As to the hardware, I know nothing about wyfi other than there is such a thing.  I have never used it per se, having no need with my use of computers. Thus I have made and placed the file lshw.txt for the laptop here:  [http://paste.ubuntu.com/9762512/](http://paste.ubuntu.com/9762512/).  I believe it has all the data required about hardware.  Really I don't know very much about these kinds of things.  I don't have wyfi here in my house so I won't know if it works or not, although I know the person who owns this machine wishes to use wyfi having wyfi availability and need.  The other hardware issues I will take on as I get to them. 

I shall continue and update progress as I get through it.  

Again thanks!

---

### Post by sudodus on 2015-01-16
I'm not sure but I think you can run this old Radeon Fire card with the built-in free driver, but you may not be able to play advanced high-definition video. Lower resolution should work. Other people at the Ubuntu Forums know better about old Radeon graphics.

```
*-display
                description: VGA compatible controller
                product: Radeon RV250 [Mobility FireGL 9000]
```

Broadcom wireless need a special driver. I'm not sure about the wired (ethernet) driver, I think it will work (anyway, it is easy to find out by trial and error).

            ```
*-network:0
                description: Ethernet interface
                product: NetXtreme BCM5702X Gigabit Ethernet
                vendor: Broadcom Corporation
```
           
Intel wireless usually work without problems.

```
*-network:1
               description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
```

This link may provide more details how to enter the **forcepae** boot option

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

---

### Post by de Bacon on 2015-01-16
This link from the wiki is much better than the other.  I really need these pure step by step instructions as this specific wiki provides.  Now if only I had the brain power to use the search and successfully find information.  My own brain language fails to provide capatable words.  An example is before I started this post, I did a search using "ERROR:PAE" among others.  I got a long list of things that I could have spent the next month trying to read through, but I didn't see either of these articles that led to a solution.  

Again thanks, carrying on with the load process directly after posting.

---

### Post by sudodus on 2015-01-16
Good luck, and come back here and tell us your results (good or bad) :-)

---

### Post by de Bacon on 2015-01-16
One thing at a time.  Thanks to you kind folks here, I think this was a rather painless success.  The system loaded and seemingly works fine.  I have not put it through much of a test, no real graphics challenges or other stuff really.  I think I have done enough for today with this though.  
Again I did overcome the pae issue certainly, as per following the instructions provided by sudodus [https://wiki.ubuntu.com/Lubuntu/Adva..._and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/Adva..._and_Celeron_M)  I was unaware of how those options really worked prior.  I would also like to point out that that menu from the .iso file system (on the bottom far right) might be good but there is nothing that explains what any of those possibilities mean to an idiot like myself.  

I will get back to this either later today or tomorrow and do some testing of the graphics card, running some video etc.  As to the wyfi connections, I have no way to test it from here.  The ethernet port worked fine though.  The system is obviously a bit slow due to its old processor most likely, yet that is not nearly as bad as I used to see with old windoz machines.  I will resolve this thread to solved upon completion of these other items that need to be checked. 

Again Thank You All
Cheers and a smile

---

### Post by de Bacon on 2015-01-17
This system seems to be working just as it is designed.  I have not done a lot with it really, although; I did watch a video thruoug its interface and all worked correctly.  Hopefully the wyfi will work, as I stated prior I don't have a wyfi set-up here due to lack of need.  Furthermore, I don't know anyone close by who does, in order to test it.  So, I will solve this link and carry on.  

Thanks to all who helped with this issue, I do so appreciate you all.

---

### Post by sudodus on 2015-01-17
You are welcome, and congratulations, that you installed a system that works well in that old Dell Latitude D600 :-)

---

