---
title: "Installing problem 6.06/6.10 uge"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by purple_goat on 2007-03-26
I bought a SuSe disk at a barnes and noble a little while back and installed it on my old computer (which was just sitting there). Since then I have been looking farther into linux and have found that it is time to delete XP and upgrade to Ubuntu Ultimate Gamers Edition.

Here is what went down:
downloaded UUGE iso
moved iso to other computer and burnt it while it was on a hdd (external)
wiped XP
put DVD into new comp
*hangs*

(I also tried my ubuntu 6.06 disk on my new comp and that didn't work either, even tho it worked on my old comp)

It says:
something about PnP not having an end
and
PCI is not allocating something
(not exact)


My new comp:
Pentium D -- 2.66ghz
2048mb ram
ASUS p5rdi motherboard
500gb SATA maxtor hdd (just put in last night, not sure if it works)
ATI Radeon X1900 XTX :KS 
...

SO: what's wrong!?
:confused: 


thanks

[b]EDIT: the error message I get for the PCI is:

[17179573.256000] PCI: cannot allocate resource region 3 of device 0000:00:00.0 [/b]

---

### Post by Chappy7777 on 2007-03-26
I am new to this so don't give me too much credence, but since you have no replies so far, I might as well ask a couple obvious questions.

Did you try using either Ubuntu disk on your new (was XP) PC via the CD as a live CD? That is what I would have suggested, and what you should have done to be sure it runs on that machine. Obviously it's not happy there.

You wrote "it says: something about PnP not having an end and PCI is not allocating something (not exact)." I would say check your BIOS and make sure PnP is enabled, but it likely was for XP. You could check and make sure. Same thing re:PCI. 

You have some version of Hi-speed conneck to the net? If you are using dialup, you may need a modem. Likely you know this. This is a reason for running the Ubuntu CDs live 1st.

The fact that Ubuntu worked on an old PC but not on your new one is not surprising. I am running 6.06 quite nicely (tho somewhat slowly) on my old overclocked P2-333. In the last 2 months I have installed 5.10, 6.06, 6.10, and now back to 6.06. No problems w/any of these installs and HDD erases. Are you sure you got your HDD wiped clean before trying the Ubuntu install? I think many on here would have suggested a dual boot, or maybe that's what you did?

Right now I am looking for a used P3-1Gig cpu to make into my Linux box. My new PC has no serial ports to attach my external modem to, plus I prefer keeping them on separate machines. P3 machines are so cheap, and have Linux happy things like serial ports, ISA slots,
etc.

I am sure it's something on your new PC that someone on here that is light years ahead of me 
will answer for you. If for no other reason than to give a true geek a good shot at fixing your problem, answer my questions. That will help.

God bless,
Chappy

---

### Post by purple_goat on 2007-03-26
I have no internet connection on the new computer and the hdd is totally fresh (just popped it in yesterday) but the computer used to have hard drives with windows XP [on them]

[b]EDIT: the error message I get for the PCI is:

[17179573.256000] PCI: cannot allocate resource region 3 of device 0000:00:00.0 [/b]

---

### Post by ollebro on 2007-04-14
i get that error to on my new computer "PCI: cannot allocate resource region 2 of device" but region is 2 for me and not 3 but ubuntu works fine on my old computer what is wrong?:(

---

