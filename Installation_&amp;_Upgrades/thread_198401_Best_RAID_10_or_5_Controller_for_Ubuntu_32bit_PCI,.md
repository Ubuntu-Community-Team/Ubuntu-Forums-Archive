---
title: "Best RAID 10 or 5 Controller for Ubuntu: 32bit PCI, IDE, max. 250 EUR"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by rso on 2006-06-17
Hi,

can anybody give me a hint about the best or some raid controller that is easily detected by ubuntu?

It should have:
[LIST]
[*]IDE, PATA
[*]PCI interface with 32 bit
[*]maximum of 250 EUR in price
[*]RAID 5 or RAID 10 (not just 0+1) capable
[*]easy setup with ubuntu
[/LIST]

I have already looked at and read bad reviews about:
[LIST]
[*]Promise FastTrak SX4100
[*]Highpoint RocketRAID 454
[/LIST]

Any help is highly appreciated!

Ciao

Richard

---

### Post by blkish on 2006-06-17
3ware - no question IMO

driver has been in the linux kernel for a long time now, very stable.

cards come up quite often on ebay. do a search for '3ware' or 'escalade' (ignore all the cadillac bumpers!)
most tend to be available from the US

the 7500 series ought to be within your budget. the 6400 (i think) series also supports RAID 5 in some incarnations, but i have memories of it being horribly slow.

good luck, have a good weekend

blkish

---

### Post by rso on 2006-06-17
Problem pretty much solved, the 3ware Escalade 7506-4LP [1] has all those things and as I just found out, it does not matter that it is 64 bit since it works on any 32 bit interface just as well.

I will report if the installation worked with the 3ware controller ;)

ciao

richard


[1] [http://www.3ware.com/products/parallel_ata.asp](http://www.3ware.com/products/parallel_ata.asp)

---

