---
title: "&quot;more bad news&quot;"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by flip on 2005-05-03
First off much respect to Ubuntu for making a great looking deb based distro .... now on to my problem

::big frown::

So I finally got Horay and a computer I can install it on but I'm getting what looks to be a pretty nasty SATA problem very early in the install. I get the initial install screen, ::enter key::, familiar linux kernel messages on console, ::full stop::  

:cry: 

I think it's detecting my SATA drive
ata1:SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xFEA0 irq14
ata1: dev0 ATAPI, max UDMA/33

but crapping out pretty soon after
ata1: command 0xa0 timeout, stat 0x58 host_stat 0x21

the only post I could find explicitly mentioning an ata1: command 0xa0 timeout and Ubuntu explicitly was on [osnews](http://www.osnews.com/comment.php?news_id=10156#355120) ... definately not a fix mentioned

I'm no Linux expert, but this one doesn't sound like a quick fix (or even fixable in the near future as it b0rks so early in the install, and some windows users have gone so far as to [slipstream](http://www.fatwallet.com/t/28/461521/) the drivers into a custom built install to get SATA working on an 8400) ... yeah right

any help would be great

- flip

ps my box is a Dell 8400 (I know I don't like Dell either but it was mad cheep on ebay and spankin new, looks like I'm paying for it now though)

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=flip]
any help would be great

- flip
[/QUOTE]

Well. I can't tell you how to make that SATA card work. That suff is hit or miss. But since no one else has posted an idea to help you, I will give you a link for a cheap pci SATA controller that worked perfectly with Hoary for me. Its a cheap way to fix an expensive box-

[http://www2.newegg.com/Product/Product.asp?Item=N82E16815124006](http://www2.newegg.com/Product/Product.asp?Item=N82E16815124006)

---

### Post by bugmenot on 2005-05-04
First off, somebody please rename this thread to something sensible.

Secondly, I just got a Dell Precision 370 and had the same problem.  I worked around it by switching from AHCI to "combination mode" in the cmos setup.  This made my XP partition unbootable but allowed me to boot and install hoary hedgehog (2.6.10).  YMMV.

Edit: more info [here](http://forums.us.dell.com/supportforums/board/message?board.id=sw_linux&message.id=6043), will try 2.6.11 shortly.

---

### Post by flip on 2005-05-04
Apologies for the nonsensical post name ... and thanks for posting some great resources dispite.

I'll be foolin with some of the solutions you linked and hopefully will have some good results to report. Worse comes to worse a $20 SATA board is a great deal  :grin:  Also great reference to X300 graphic card setup too, that's most likely the next hurdle.

Cheers,

- flip

---

