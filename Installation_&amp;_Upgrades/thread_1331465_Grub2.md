---
title: "Grub2"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by phillw on 2009-11-19
Hmmmm... Well kinda ready to give Grub2 a blast. So, found the instructions here  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

sudo apt-get update  ... fine
click on the link within
> To upgrade to GRUB 2: [install the ''grub-pc'' package]("apt:grub-pc"). A simple script will guide the user through the installation: 
And I get a pop-up window saying that it wants to open with aptgui, which i say is okay .... and now ? - Nothing, zilch, zero.

Not overly impressed - I was a bit nervous of the upgrade & this has done nothing to allay any nagging doubts.

Any ideas as to why the official instructions don't work ? I upgraded from 9.04 to 9.10 which went fine. I dual boot with Vista, which still works.

Phill.

---

### Post by darkod on 2009-11-19
Don't know about scripts, but tried?
sudo apt-get install grub-pc

---

### Post by raymondh on 2009-11-19
Phillw,

Maybe drs305's guide can help.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

Regards,

---

### Post by phillw on 2009-11-19
> **raymondhenson said:**
> Phillw,

Maybe drs305's guide can help.

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

Regards,

Thanks, I've had a good read through that thread, believe me, before I decided to go for the switch.

Guess what the 1st link is in his post ? - yup ... the [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)  one :-(  This does not bode well if their instructions don't work.

Phill.

---

### Post by phillw on 2009-11-19
> **darkod said:**
> Don't know about scripts, but tried?
sudo apt-get install grub-pc

Thanks, but having read the many horror stories - I want to use the 'official' set of instructions & more importantly, be able to tell others to do so with confidence. Which is now slightly below 0%.

Phill.

---

### Post by wkulecz on 2009-11-19
> **phillw said:**
> Thanks, but having read the many horror stories - I want to use the 'official' set of instructions & more importantly, be able to tell others to do so with confidence. Which is now slightly below 0%.

Phill.

Can I ask why you want grub2 unless installing to ext4 or raid, I see all pain and no gain otherwise.

I did the default install to ext4 as I'm just testing 9.10 in advance of my next real update to 10.4 as I only use LTS releases.  I'm still on 6.06 for my six "real" systems as 8.04 didn't really offer any benefits to pay for the effort, although its worked well for me and my wife in general use.

I had a grub2 problem that was frustrating but fixable, basically grub2 ignored my BIOS setting making IDE the primary boot devce (where I installed to!) and installed itself to the first SATA drive :(

--wally.

---

### Post by drs305 on 2009-11-19
phillw,

I wrote both my Grub 2 Guide and the community doc. I'm sorry the aptgui link doesn't work. I was following the documentation guidelines when I included that link. The doc people want us to use links rather than give actual commands. The actual command I would have used would have been:
```

sudo apt-get install grub-pc

```

I take responsibility for using the link and will either correct the link, add an explanation, or include the actual command. I want the guide to be as simple as possible and having something that confuses new (and old) users on that site is unacceptable.

---

### Post by phillw on 2009-11-19
> **wkulecz said:**
> Can I ask why you want grub2 unless installing to ext4 or raid, I see all pain and no gain otherwise.

I did the default install to ext4 as I'm just testing 9.10 in advance of my next real update to 10.4 as I only use LTS releases.  I'm still on 6.06 for my six "real" systems as 8.04 didn't really offer any benefits to pay for the effort, although its worked well for me and my wife in general use.

I had a grub2 problem that was frustrating but fixable, basically grub2 ignored my BIOS setting making IDE the primary boot devce (where I installed to!) and installed itself to the first SATA drive :(

--wally.

I also will be switching over to ext4 and the LTS (Yippe, no more for 3 years after that) In the mean-time I want to set up an area for Lucid to have a 'play' on. For this, it will have it's own native ext4 partiton and Grub2 loader - I do, however, need this computer for working on, so I will be triple booting (Vista and 2 lUbuntus).

Phill.

---

### Post by phillw on 2009-11-19
> **drs305 said:**
> phillw,

I wrote both my Grub 2 Guide and the community doc. I'm sorry the aptgui link doesn't work. I was following the documentation guidelines when I included that link. The doc people want us to use links rather than give actual commands. The actual command I would have used would have been:
```

sudo apt-get install grub-pc

```I take responsibility for using the link and will either correct the link, add an explanation, or include the actual command. I want the guide to be as simple as possible and having something that confuses new (and old) users on that site is unacceptable.

Thanks drs, I will use the apt-get.  When vpolink is re-instated by vB you'll be able to read my Blog on 9.04 -> 9.10  This is the first glitch I've hit. And, easily rectified. You may, however, want to have a look at the community doc.

Regards,

Phill.

---

### Post by phillw on 2009-11-19
Hmmm.... It's picking on me !!!!!

> The following Linux command line was extracted from /etc/default/grub or the `kopt` parameter in GRUB Legacy's menu.lst. Please verify that it is correct and modify if necessary

And ...... it's a blank line    YIKES !!!!!!

Phill.

---

### Post by drs305 on 2009-11-19
> **phillw said:**
> Hmmm.... It's picking on me !!!!!
And ...... it's a blank line    YIKES !!!!!!
Phill.

No it's okay. Really. It means you didn't have any *extra/special* commands on the line in your original grub kernel line.

---

### Post by phillw on 2009-11-19
Thanks ... all done & it found Vista - re-boot time - brb :D

Phill.

---

### Post by phillw on 2009-11-19
Ohh, lovely ....  chain load ... fine ... legacy-update ... fine, select sda ... fine .... boot  grub error 15 -- I shall now go find the instructions to rebuild it. 1st stop drs's thread.

The bit that REALLY narks me, tho' is that I watched it build the cfg file & it found all the kernels, memtest & Vista....

Not a happy bunny.

Phill.

---

### Post by phillw on 2009-11-19
That was FUN - lol

Re-installed grub2 from the liveCD 

I also know how / why it failed. When you get the choice of sda (and that's it on my one disk system) as the device to place the MBR onto - when I tried to put the 'X' in the box I used the 'tab' key to move (correct) and then hit "enter" -- always a bad thing to do with those sort of windows.

I'll have to brush up on my keyboard commands for those critters (not used them since i put LAMP on).

So, for anyone reading this after me - the correct way is to use the tab key to select the drive and press the space bar (from memory - some one please check) to put the 'x' in the box.
(as soon as this is verified, I'll mark the thread solved)

The recovery from LiveCD works well, tho :D

Next up, re-slicing and teaching Grub2 about a new ext4 area especially for lucid .... I'll leave that until another day ;-)

Phill.

---

### Post by drs305 on 2009-11-19
> **phillw said:**
> So, for anyone reading this after me - the correct way is to use the tab key to select the drive and press the space bar (from memory - some one please check) to put the 'x' in the box.
(as soon as this is verified, I'll mark the thread solved)


Yes, that is the correct procedure, althoughIIRC it's an asterisk * rather than an X.  ;-)

---

### Post by raymondh on 2009-11-19
> **phillw said:**
> I also will be switching over to ext4 and the LTS (Yippe, no more for 3 years after that) In the mean-time I want to set up an area for Lucid to have a 'play' on. For this, it will have it's own native ext4 partiton and Grub2 loader - I do, however, need this computer for working on, so I will be triple booting (Vista and 2 lUbuntus).

Phill.


Me too, Phil.  I'm done with the 6-month tweaks.  'Just installed a 3rd HD and checked that it was recognized.  That's reserved for Lucid.  I plan to multi-boot as well (jaunty + win 7 in sda, karmic in sdb,  plus lucid in sdc)  but using BIOS to alter OS choices until Lucid is tweaked and stable .... and then I re-do down to a dual-boot (lucid and win7) but this time using GRUB.

happy ubuntu-ing.

---

