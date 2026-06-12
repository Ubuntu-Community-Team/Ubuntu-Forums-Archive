---
title: "xubunt failed during dual boot install"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by cdoublejj on 2010-06-28
how do i install in the original partition i assigned for it and not a new one?

EDIT if i used manual partition will it be smart enough to let me choose each os or will just divert to xubuntu only?

---

### Post by wilee-nilee on 2010-06-28
> **cdoublejj said:**
> how do i install in the original partition i assigned for it and not a new one?

EDIT if i used manual partition will it be smart enough to let me choose each os or will just divert to xubuntu only?

Since a full description is missing here how about a screen shot of gparted.

---

### Post by cdoublejj on 2010-06-29
100gb drive 98 as the main and 11.6gb for xubuntu 9.04 witch from what i can guess also includes the swap. the install made it all the way to copying files then it failed a file and aborted back to the live session. 

i'm starting to think it's this drive wich will get taken care of if so i really don't want to reinstall 98se again and do updates and drivers again but, if thats what it takes to do it right. 

something tells me when i manually partition with gparted and tell it to use the original 11.6gb partition it's gonna by pass my 98se install.

ugh man last time it was the hard drive it's like the project from hell. i appreciate any help.

---

### Post by wilee-nilee on 2010-06-29
What are the computer specs mainly the ram, and post the screenshot of gparted it's on the live cd.

---

### Post by cdoublejj on 2010-06-29
i'll try to get that screen shot.

it's a toshiba 2805 s503
900mhz
384mb ram
16mb nvidia
100gb ide drive

EDIT: looks like i'm gonna have to swap some drives. (sigh) 
It doesn't want to live boot reads for minute then the drive stops and the bar goes back and forth till i get a blinking under score.

---

### Post by cdoublejj on 2010-06-29
had a drive in the closet can only get you 1 screen shot.

[[IMG]http://img441.imageshack.us/img441/2569/screenshotcgd.th.png[/IMG]]("http://img441.imageshack.us/i/screenshotcgd.png/")



thats is xubuntu wanting to tri boot i want it to use the existing partition from the failed install. am i gonna have to reformat the drive? i can reuse the old partition under manual mode but, that won't necessarily give me the grub boot loader at start up.

EDIT
my idea of using the manual partition ...
[[IMG]http://img139.imageshack.us/img139/1364/screenshot2e.th.png[/IMG]]("http://img139.imageshack.us/i/screenshot2e.png/")

[]("http://imageshack.us")

---

### Post by wilee-nilee on 2010-06-29
I'm not sure you understand what gparted is though since that was I suggested the screen shots of.

What you have is the partitioner in the install showing.

You don't want to just try another install into a partition that has been tried already and has failed I see in the 2nd screenshot 632mb of data from your original failed install. So open gparted remove sda5 and put another ext3 in it's place and install.

I am curious as to why it is ext3, and what OS is it your trying to install and do you know when the support for it ends?

---

### Post by cdoublejj on 2010-06-29
it's xubuntu 9.04 i think newer version get more bloated. plus i know 9.04. ext 3 is bad? is it supposed to be ext2? so basicly reformat sda5 and tell it to use sda5 via manual part. and i will still be able to choose os at start?

---

### Post by wilee-nilee on 2010-06-29
> **cdoublejj said:**
> it's xubuntu 9.04 i think newer version get more bloated. plus i know 9.04. ext 3 is bad? is it supposed to be ext2? so basicly reformat sda5 and tell it to use sda5 via manual part. and i will still be able to choose os at start?

Ext3 is correct, here is a link to the support it ends in October. This is your call, you wont have anymore security updates after this date. As far as bloated I hear that term but I don't really know what that means. To me it is just people using this word (not you) because they think its correct. As far as having the OS to choose from it should be okay, but I'm not real familiar with grub-legacy so I wont be able to help you there if it's a problem, but lots of people on the forum know how to deal with it.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Really if it was me I would install Hardy its support is until April 2011

Really if you got some more ram it would be useful no matter what distro you use. With a computer running this old of a version of Windows, a more updated computer with an more up to date OS would be better, but I don't know your limitations in this area.

---

### Post by cdoublejj on 2010-06-29
bloated means it takes more system resources. i'm gonna give it a try, if all goes bad i will have to reinstall both oses witch might go faster this time with a fully functioning dvd drive.

EDIT gparted doesn't want to work with me cause it gives me a mounting error every time i try to modify sda5, i was only able to format it i'm gonna try the manual installer partitioner and hope it works.

---

### Post by wilee-nilee on 2010-06-29
> **cdoublejj said:**
> bloated means it takes more system resources. i'm gonna give it a try, if all goes bad i will have to reinstall both oses witch might go faster this time with a fully functioning dvd drive.

EDIT gparted doesn't want to work with me cause it gives me a mounting error every time i try to modify sda5, i was only able to format it i'm gonna try the manual installer partitioner and hope it works.

You can only use gparted from the live cd, and at times you have to turn off the swap.

---

### Post by cdoublejj on 2010-06-29
regardless you must have steered me in the right direction. for now it seems to be working grub boot selector and all, grant it 98se was acting a little ornery.
:guitar:

Thank you.

---

