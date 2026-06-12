---
title: "Need help removing ubuntu!"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Mattread92 on 2007-12-09
I urgently need help, I need to remove Ubuntu.. I can't seem to boot from my factory restore CD, cause when i try to boot from it GRUB starts loading... I can't get into my BIOs set up because for some reason it's password protected.. and I can't get onto ubuntu cause of some "automatic file system check of the root system failed".. so I'm pretty stuck. My dad was messing around with this computer trying to remove ubuntu and get windows back on, and he's well and truly messed it up! I TOLD him that he had no idea what he's doing!! ](*,)

And yes, I have searched

UPDATE: 
I have had a new idea. I have downloaded ubuntu again and am going to burn it to a disc. Then I am going to re-install ubuntu (because at the moment i can't get onto it due to some form of error) and then hopefully when I'm logged into ubuntu there will be a way of removing it / formatting the hard drive. I'm also going to try and get hold on a windows xp disk to boot from.

---

### Post by taurus on 2007-12-09
Why don't you open the box and remove the battery on the mobo.  Leave it out for a day or so and then put the battery back in.  The BIOS should fall back to default so you can get into it to change the boot order again.

---

### Post by Mattread92 on 2007-12-09
> **taurus said:**
> Why don't you open the box and remove the battery on the mobo.  Leave it out for a day or so and then put the battery back in.  The BIOS should fall back to default so you can get into it to change the boot order again.

I can try that, but.. 

A) Would BIOS definately lose the password?
B) Does it really take THAT long?
C) Would my system restore disk definately boot?

I need this sorted out as quickly as possible, as you can probably tell

---

### Post by -=Ghostlike=- on 2007-12-09
depending on your motherboard type you also have a 'emergency reset' jumper on the board (Intel and ASUS have that I believe)

---

### Post by Mattread92 on 2007-12-09
> **-=Ghostlike=- said:**
> depending on your motherboard type you also have a 'emergency reset' jumper on the board (Intel and ASUS have that I believe)

Is this in the form of a button physically on the motherboard?

---

### Post by kubug on 2007-12-09
Hi Mattread,

From what I know, once you set a password on your BIOS it sticks. Meaning, no matter how long you take out the Battery it will not reset, since it is written in an EEPROM (retains infomation without needing constant power).

What make is your computer? HP, Dell, Compaq, or maybe a "homebrew"?
If it's a homebrew, if you opened up your computer, and checked which manufacturer made that motherboard you may find some information how to reset the password. 

The problem you have is that these passwords are there to proctect, and that's why they are so hard to remove. I never set mine, since there is the possibility of forgetting.

Really, your best chance is trying to figure out the password and then removing it from the BIOS. If you can't and can't find a way to reset it by following an online explanation how, you may have to send in your BIOS chip to be reset. And depending on the age of the computer that may not be worth it.

---

### Post by gfg on 2007-12-10
I'm not quite sure here, but on my computer I believe you can change the order of boot by pressing a button, without having to enter the BIOS, and thus having to type a password. Maybe this can be done on your computer as well?

---

### Post by Mattread92 on 2007-12-10
> **kubug said:**
> Hi Mattread,

From what I know, once you set a password on your BIOS it sticks. Meaning, no matter how long you take out the Battery it will not reset, since it is written in an EEPROM (retains infomation without needing constant power).

What make is your computer? HP, Dell, Compaq, or maybe a "homebrew"?
If it's a homebrew, if you opened up your computer, and checked which manufacturer made that motherboard you may find some information how to reset the password. 

The problem you have is that these passwords are there to proctect, and that's why they are so hard to remove. I never set mine, since there is the possibility of forgetting.

Really, your best chance is trying to figure out the password and then removing it from the BIOS. If you can't and can't find a way to reset it by following an online explanation how, you may have to send in your BIOS chip to be reset. And depending on the age of the computer that may not be worth it.

My laptop is a Toshiba Satellite.. I don't know how this BIOS password got there and have tried using all of the passwords that I do use for things, so I definately haven't set it. I asked my dad and he just says "Don't try to blame me bla bla bla" so there's no use there...

> **gfg said:**
> I'm not quite sure here, but on my computer I believe you can change the order of boot by pressing a button, without having to enter the BIOS, and thus having to type a password. Maybe this can be done on your computer as well?

Yes, by pressing F12.. but booting from CD drive still doesnt work!

---

### Post by Rhubarb on 2007-12-10
There are 4 ways to get your laptop working again:

1) Contact Toshiba, they may be able to send out a technician / talk over the phone to you.

2) Get your screw driver out and pull the notebook apart, look for the battery, and pull it out, wait a few minutes (maybe even an hour), put it back in and see if your laptop boots up again with no BIOS password prompt.

3) Do a search on the internet to find a way to reset the BIOS (password) for your laptop

4) Take out the laptop hard drive, put it into another notebook or get a laptop HDD to normal 3.5" converter, install your preferred OS on it (windows does NOT like this), then put it back into your laptop and boot from it.


I have noticed that sometimes the windows installer does not like an non-empty hard disk, if you can boot gparted live cd, then run it and delete all the partitions on the hard drive, then try installing windows from the CD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by Mattread92 on 2007-12-10
> **Rhubarb said:**
> There are 4 ways to get your laptop working again:

1) Contact Toshiba, they may be able to send out a technician / talk over the phone to you.

2) Get your screw driver out and pull the notebook apart, look for the battery, and pull it out, wait a few minutes (maybe even an hour), put it back in and see if your laptop boots up again with no BIOS password prompt.

3) Do a search on the internet to find a way to reset the BIOS (password) for your laptop

4) Take out the laptop hard drive, put it into another notebook or get a laptop HDD to normal 3.5" converter, install your preferred OS on it (windows does NOT like this), then put it back into your laptop and boot from it.


I have noticed that sometimes the windows installer does not like an non-empty hard disk, if you can boot gparted live cd, then run it and delete all the partitions on the hard drive, then try installing windows from the CD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

I have had the battery out all night, and just took the laptop apart to find a reset jumper, which I could not find... I'm now going to put it back together and try it

EDIT: It's still got a password on it...

---

### Post by Rhubarb on 2007-12-10
Sorry Mattread92, I meant to take the on-board battery out of the notebook (it's probably a small CR2032 watch battery somewhere on the motherboard).
Unless you're adventurous and don't mind voiding the warranty (if it still has a warranty) I don't recommend you try doing this.

---

### Post by Mattread92 on 2007-12-11
I tried to access the motherboard to find the "jumper"... but couldnt get to it cause of a star shaped screw that I think covers the processor and heat-sinc... I have had a new idea. I have downloaded ubuntu again and am going to burn it to a disc. Then I am going to re-install ubuntu (because at the moment i can't get onto it due to some form of error) and then hopefully when I'm logged into ubuntu there will be a way of removing it / formatting the hard drive. I'm also going to ask my mateto lend me his windows xp installation disc to boot from

---

