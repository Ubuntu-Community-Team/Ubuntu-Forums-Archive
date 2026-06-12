---
title: "Can't even boot into LiveCD!"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by lukster91 on 2010-07-17
Hey,

I just built a new computer. I have 2 Hard drives, and one one I want to install Ubuntu (eventually). The other HDD already has windows.

I've written to DVD the Ubuntu 10.04 64-bit OS. Loaded up, selected Language, selected try Ubuntu without any changes to my computer, and all I get is a flashing "_". Doesn't go off it.

Also, what I know shouldn't be happening is that I can eject the DVD tray. 

How do I boot into the LiveCD, or can I just not...?

Luke

---

### Post by Rubi1200 on 2010-07-17
We need some more information please. Specifically, what type of graphics card do you have installed.

Also, I assume you have set BIOS to boot from the drive you want to use?

---

### Post by lukster91 on 2010-07-18
Yes, it boots into the set-up. Language selection and choice of whether to do an install, or try it out. 

I managed to access the live CD by going into Install (without trying), then quitting the installation. For some reason it won't work by going straight to trying it out.

I hear graphics cards can be a problem, but this one is fine. I've harvested this graphics card from a computer which had Ubuntu on it. 

I know I can enter the LiveCD by quitting the installation. I am guessing the issue is down to something going wrong between me downloading Ubuntu and writing it to DVD. 

If anyone has a suggestion other than my potential explanation about why it won't boot into LiveCD without starting the installation process, I'm going to mark this as solved.

Thanks!

---

### Post by 23dornot23d on 2010-07-18
Have you tried using any other live CDs

See if they do the same thing .......

Download Mint and give that a go ......

Just to see if you can run it as a livecd .... 

if it works

type  

lspci -v

in a console window .... and post the output ..... so we can see what you have there.

More information ....  on the graphics card as said would be useful as asked for before.

Once we can see that it works and the graphics card is ok ,,,, 

Then we can start to get ubuntu working ....... 

MINT is based on Ubuntu, but can sometimes boot into GRUB2 and it may possibly find the graphics card.

Just a thought rather than giving up. 

> 
I hear graphics cards can be a problem, but this one is fine. I've  harvested this graphics card from a computer which had Ubuntu on it. 

What version of Ubuntu did the card work in .... what Graphics Card is it ? ........ Nvidia ... ATI ..... or something else

( from the little you have said it seems to be stopping at a point where the graphics starts up in GRUB2 but who can tell without more info )

(There are other options too booting from a livecd ..... different resolutions ... etc have you tried them)

---

