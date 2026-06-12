---
title: "Boot problems, halp! :P"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by K-Zodron on 2006-03-20
Hi and thanks for viewing my..let's say stupid..thread!

Well, I got mad with Windows after it crashed and didn't want to install again nor repair, so I chose Linux. Some guys @ IRC (Not ubuntus chan) recommended Ubuntu for desktop pc's...so here I am! :d

Well, I managed to do the install pretty well..but after the restart, when it tries to boot from my HDD I get this:

Booting 'Ubuntu, Kernel 2.6.12-9-386 '

root (hd0,0)

Filesystem is ext2fs, partition type 0x83
kernel /boot/vwlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash

  [Linux-bzlmage, setup=0x1c00, size=0x124b1b]
initrd /boot/initrd.img-2.6.12-9-386

<some load>

Error 16: Inconsistent filesystem structure

Press any key to continue...



Ok, not so cool...well, I tried to reinstall, same error again.
Tried an other HDD, freezes at install..

What could be the problem? :O
Should I redownload the ISO and reburn? (Quite slow connection, don't really want to do it if it's not necessary ;p)

Thanks for any help!

Yours,
Me

---

### Post by IYY on 2006-03-20
Well, there is always a chance that downloading a new ISO (or better yet, ordering the free CD's via shipit) will help, but I don't think this is the problem. Since you say that Windows didn't install properly either, it's very likely that there is a problem with your hard drive or some other hardware component.

---

### Post by Bartender on 2006-03-20
This is just a WAG, but based on your initial comments I'm wondering if something's going wrong with your hardware?  How old is the PC?  The fact that Windows kept crashing and finally refused to load sounds like a failing HDD, a stick of RAM that's going south, or something similar.  How do the capacitors on your motherboard look?  Reason I ask is we're still seeing motherboards with capacitors oozing crud and causing very weird problems.
Gotta go back to work

---

### Post by paulproteus on 2006-03-20
Sorry to hear things aren't going well.  (BTW, I'm the paulproteus who replied to you on #ubuntu.)

It would be great if you could download, burn, and boot an Ubuntu Live CD.  That way we can have an operating system running on your computer.

I agree with the previous poster that, on first glance, it appears there could be something wrong with your hard disk.  Once you boot into the Live CD, open a terminal by clicking "Applications -> Accessories -> Terminal".

We'll use the program called "e2fsck" - fsck is short for "filesystem check", and "e2" is short for "ext2", the filesystem you're using.

In the terminal, type this:

sudo e2fsck -c -p /dev/hda1

Please report back with the results!  That will test (and repair) any filesystem problems you have.

I can't emphasize enough that you *must* tell us everything printed by this command!

---

### Post by paulproteus on 2006-03-20
Good points raised by others before.

Before you try my other suggestion, you should see if your Ubuntu system has the option to run memtest86.  If it does have that option, run it and see if it tells you your computer has any memory problems.

---

### Post by K-Zodron on 2006-03-20
Oki doki, downloading the live CD atm..

Well the windows install problem was something like "Unlicensed version" or smth, at least it pointed somewhat to..something like that xd (It wasn't an official copy)

The computer is like 4 years old, but I wouldn't really throw it away anyway, it's still like 2,5GHz :d I'll try your suggestions and post the results, thanks for da halp!

---

### Post by K-Zodron on 2006-03-21
Ran Memtest, no errors. :p

Currently running on LiveCD (I must say that Ubuntu is kickass, the colors are too bright tho, but I guess it's changeable? ;p) and I'm writing this post on it ;D
The only problem was connecting to the internet via PPPOE, but it sorted out (sudo pppoeconf :P)

Also...atm I'm running that command thing paul--- is recommending, I will post the results :O

---

### Post by K-Zodron on 2006-03-21
Ok..ran that thing, nothing happened actually :/ (I stopped it after like 1 hour 30 min running)

I just heard weird noice from the HDD..like "du...du....du.....du" all the time :S

Maybe there's something wrong with my HDD? I'll prolly buy a new one :d

Edit: Bought a new from cd-rw from the shop and burned on 4x and guess what, it worked! :O

Thanks for all help :)

---

