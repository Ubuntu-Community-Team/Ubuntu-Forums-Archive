---
title: "Booting Ubuntu 9.10 live CD asks for username/password ?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by ekh on 2010-02-14
Hi,

I have just searched for an answer to the below problem with no luck, so please excuse me for this apparent stupid question:

When I do a live boot using ubuntu-9.10-desktop-i386.iso burnt to a CD (checked for defects, OK), it asks for user name and password.

I use the "Try Ubuntu without any changes to your computer" boot option.

I have used Ubuntu for some years now ( super OS ), and has so far been able to boot a live CD without password.

Is there any default user and password on the 9.10 desktop live boot now ?
If not what can the problem be ?

I boot on a IBM ThinkPad T41.

If I boot the same live CD on a T30, then no username/password is required.

ekh

---

### Post by phillw on 2010-02-14
> **ekh said:**
> Hi,


I boot on a IBM ThinkPad T41.

If I boot the same live CD on a T30, then no username/password is required.

ekh

Hi, is the LiveCD getting to the log-in prompt, or are you being asked for a password before that ?

Regards,

Phill.

---

### Post by ekh on 2010-02-14
> **phillw said:**
> Hi, is the LiveCD getting to the log-in prompt, or are you being asked for a password before that ?

Regards,

Phill.

Hi Phill,

Thank you for helping :)

Yes, it gets to the login prompt.

ekh

---

### Post by phillw on 2010-02-14
> **ekh said:**
> Hi Phill,

Thank you for helping :)

Yes, it gets to the login prompt.

ekh

Hmmm,

As the cd boots okay on the other computer, my suspect would be the drive in that one. I'd start with a cd-lens cleaner.

Other things that can cause 'funnies' is that the cd you're using was burned at a speed faster then 4X - It's always a bit of problem one this one...  You could try re-burning at 2X speed, although 4X is usually okay.

Does it pass the Disk-Check in the T41 ? If so, it is either muck on the CD Drives' Read LED, possibly an un-detected very minor flaw on the CD you're using.

Not too sure what else to suggest, apart from doing a usb memory stick boot.

Regards,

Phill.

---

### Post by rahilm on 2010-02-14
try "ubuntu" as the username and keep the password blank and press enter..

---

### Post by ekh on 2010-02-14
> **phillw said:**
> Hmmm,

As the cd boots okay on the other computer, my suspect would be the drive in that one. I'd start with a cd-lens cleaner.


The boot option of checking the disk integrity was done on the T41.
The T41 runs another type of live CD flawlessly each day.
But a bit of cleaning don't hurt :)
 
> 
Other things that can cause 'funnies' is that the cd you're using was burned at a speed faster then 4X - It's always a bit of problem one this one...  You could try re-burning at 2X speed, although 4X is usually okay.


My lenovo T61 can not burn less than 10x. I will try 2x on the T41 itself.

> 
Does it pass the Disk-Check in the T41 ? If so, it is either muck on the CD Drives' Read LED, possibly an un-detected very minor flaw on the CD you're using.

Not too sure what else to suggest, apart from doing a usb memory stick boot.

Regards,

Phill.

Thank you for the advice. Unfortunately I can not boot the T41 without doing a BIOS update. As this is risky, I have delayed this update so far, although I have downloaded the updates a year ago.

By the way take care with the Lenovo's if you need to remove the BIOS password. Forgetting the BIOS password on a Lenovo is not so smart, as there is no easy way to recover.

Stupid me tried this. I removed the BIOS backup battery.
Result: The computer locked completely stating it had been tangled with, and it was then to no use at all.

I was so stubborn to search the net to find I was not the only one in trouble. I found some programs. One to read the encrypted password from the I2C memory IC, and one to decrypt the memory contents.

This way I got the T41 back to life.

But I had to make a small interface PCB, and disassemble the computer to solder 3 wires to the I2C memory IC pins in order to read it. What a mess for being sloppy with the password.

If I get this solved, I will report back the solution.

Thank you for helping :)

ekh

---

### Post by ekh on 2010-02-14
> **rahilm said:**
> try "ubuntu" as the username and keep the password blank and press enter..

Yes, that was my first try with some combinations, among them "ubuntu" and a blank password and also ubuntu as password, but no success.

Thanks anyway :)

ekh

PS. By the way doesn't it compromise net security running a live CD without a password ?

---

### Post by kansasnoob on 2010-02-14
I've only seen that happen with the Lucid Live CD and this was the work around:

[http://ubuntuforums.org/showpost.php?p=8548884&postcount=9](http://ubuntuforums.org/showpost.php?p=8548884&postcount=9)

---

### Post by phillw on 2010-02-14
> **ekh said:**
> 
PS. By the way doesn't it compromise net security running a live CD without a password ?

On the grounds that you have physical access to the computer, software protection is not a great deal of use - That is why there is no p/word for the LiveCD, it can be used in disaster recovery.

Regards,

Phill.

---

### Post by phillw on 2010-02-14
> **ekh said:**
> My lenovo T61 can not burn less than 10x. I will try 2x on the T41 itself.

ekh

Deffo, go for the s..l..o..w.. burn on the T41, that will also remove another 'funnie' that is a disk burned on one system not being happy on another - Believe you me, we've seen some real beasties out there !!!

As for the T61 (or any other computer) if you want a way of burning iso's nice and slow, on pretty much any system, head over to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  That covers them all :D

Regards,

Phill.

---

### Post by ekh on 2010-03-11
> **phillw said:**
> Deffo, go for the s..l..o..w.. burn on the T41, that will also remove another 'funnie' that is a disk burned on one system not being happy on another - Believe you me, we've seen some real beasties out there !!!

As for the T61 (or any other computer) if you want a way of burning iso's nice and slow, on pretty much any system, head over to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  That covers them all :D

Regards,

Phill.

Hi Phill,

Thank you so much for helping.

Now I finally got back to the problem.

The CD-R disks I have could not work anymore for some reason, it did not matter if they were burned on the T61 or the T41.

Then I took a CD-RW, and all trouble was gone.

It was burned at 4X on the T61 and then it booted flawlessly on the T41.

ekh

---

### Post by stimpyaw on 2010-03-29
Philw, I got my CD sent from Canonical directly and I still had the problem of being asked to login into Ubuntu using the live cd option.  Currently, my laptop is having a problem after login, the system freezes. I know Ubuntu is working fine on my laptop because I have 8.10 installed.  I will be posting in other threads to figure out the lock up.

Thanks Rahilme, the use of just entering "ubuntu" as the username and  leaving the password filed blank worked.

---

