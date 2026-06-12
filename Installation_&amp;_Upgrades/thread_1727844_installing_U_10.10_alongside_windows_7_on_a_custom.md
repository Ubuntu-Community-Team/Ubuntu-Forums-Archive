---
title: "installing U 10.10 alongside windows 7 on a custom made pc!"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by minasistani on 2011-04-13
Hi,

My pc is custom made with the following config:
MOBO: Asus p7p55d-e pro BIOS 1502
GPU:    Asus GTS 450  1 Gig
CPU:    i7 860
8GB RAM
2 1TB HD, one dedicated to Windows 7 64bit Ultimate
Connected to my LG 42" LCD TV

I asked my friend who is a contributor to ubuntu, and runs a cyber security company to install it on my computer and he said that he will charge me $375 to do this.  And then he said that it is not such a difficult thing, however, it will need a lot of _tinkering_ with ubuntu before it works flawlessly.  I didn't know what he meant and didn't want to get into it with him.  I was wondering if you could direct me to the threads that discuss installation of Ubuntu alongside Windows 7 *already installed* and on a separate hardware.  I don't wanna pay him that money and I'm very new to this.  Also, I hope someone could explain what kind of tinkering is done before it works flawlessly.  I wanna install cinelerra...

thanks.

Mina

---

### Post by earthpigg on 2011-04-13
i hate to say it friend, but your "friend" isn't much of a friend if he wanted to charge you $375 for that. i want to call that person many profane things for trying to pull that over on you, but i will keep those profane words to myself. suffice to say, it upsets me.

OPTION 1:

burn a LiveCD and pop it in, follow onscreen directions. when prompted to "Replace Windows, Install Alongside, or Custom?" hit custom. point the installer at the empty 1tb hard drive.

later on, make sure you hit 'advanced' and tell it were you want the bootloader: on the 1tb ubuntu hard drive.

tell bios that the ubuntu hard drive is the primary hard drive (that is in the "press ___ to enter setup" thing when you first turn on computer)

here is the "tinkering" is spoke of....

Once Ubuntu is installed, go to applications -> accessories -> terminal and type this in:

```
sudo apt-get install ubuntu-restricted-extras
```

"tinkering" is done.

OPTION 2:

if you don't want to do that stuff... google your nearest major city name and "linux users group". for me, that google search would be "San Francisco Linux Users Group" because San Fran is about 20 minutes away from me. find the next meeting of your local LUG. bring your computer, they will do it for you - for free. You need only ask nicely and say "thank you" when they are done. seriously. It'll take about 30-45 minutes. Point the nerds you will find there to this thread, for good measure, and let me know what they said. :)



Do you now understand why I want to say profane things about your "friend"? A "friend" charging you $375 for 45 minutes of work that others will do for $0 and the fun of it.... is not a friend, in my opinion. He should have done it for free, or referred you to the local LUG (I'm assuming you don't live in Siberia?).

edit: did that "friend" also charge you some ridiculous fee for playing LEGO and putting that "custom PC" together? grrrr

edit2: anyone that posts on these forums or posts a bug report from time to time can also claim to be a "contributor to Ubuntu", too. it isn't an impressive line-item on a resume, really. ok, i need to leave this thread before i get myself more worked up.

---

### Post by minasistani on 2011-04-13
> **earthpigg said:**
> i hate to say it friend, but your friend isn't much of a friend if he wanted to charge you $375 for that. i want to call that person many profane things for trying to pull that over on you, but i will keep those profane words to myself. suffice to say, it upsets me.

OPTION 1:

burn a LiveCD and pop it in, follow onscreen directions. when prompted to "Replace Windows, Install Alongside, or Custom?" hit custom. point the installer at the empty 1tb hard drive.

later on, make sure you hit 'advanced' and tell it were you want the bootloader: on the 1tb ubuntu hard drive.

tell bios that the ubuntu hard drive is the primary hard drive (that is in the "press ___ to enter setup" thing when you first turn on computer)

here is the "tinkering" is spoke of....

Once Ubuntu is installed, go to applications -> accessories -> terminal and type this in:

```
sudo apt-get install ubuntu-restricted-extras
```"tinkering" is done.

OPTION 2:

if you don't want to do that stuff... google your nearest major city name and "linux users group". for me, that google search would be "San Francisco Linux Users Group" because San Fran is about 20 minutes away from me. find the next meeting of your local LUG. bring your computer, they will do it for you - for free. You need only ask nicely and say "thank you" when they are done. seriously. It'll take about 30-45 minutes. Point the nerds you will find there to this thread, for good measure, and let me know what they said. :)



Do you now understand why I want to say profane things about your "friend"? A "friend" charging you $375 for 45 minutes of work that others will do for $0 and the fun of it.... is not a friend, in my opinion. He should have done it for free, or referred you to the local LUG (I'm assuming you don't live in Siberia?).
Thank you earthpigg.  
Mina

---

### Post by earthpigg on 2011-04-13
You are welcome.

I'd be curious as to how this works out for you with the local LUG - I may just be spoiled because SF is next to both Berkeley and Silicon Valley, meaning lots of very smart nerds show up to those meetings. Who knows?

---

### Post by minasistani on 2011-04-13
I just found the location for the nearest LUG, (Louisville, KY) and will be there tomorrow.

---

### Post by minasistani on 2011-04-13
I'll let you know how it goes on this thread.  Thanks again

---

### Post by earthpigg on 2011-04-13
> **minasistani said:**
> I just found the location for the nearest LUG, (Louisville, KY) and will be there tomorrow.

my father's side of the family is from those parts.

next time you meet someone with the surname Mason, say hello for me. :)

---

### Post by earthpigg on 2011-04-13
again, be sure to point them to the original post of this thread. it will give them the context - you outlined exactly what you want very clearly in writing. nerds like that kind of thing.

---

### Post by earthpigg on 2011-04-13
oh, and bring a usb thumb drive or blank CD-R with you. just in case. you will see why.

---

### Post by minasistani on 2011-04-13
I have 10.10 on a CD, is that sufficient? or is it for a different use?

---

### Post by earthpigg on 2011-04-13
nope, that is fine. bring that. :D

---

### Post by minasistani on 2011-04-13
you're the best.

---

### Post by earthpigg on 2011-04-13
_***This is for the folks at the Louisville LUG:***_

Make sure you tell BIOS that the Ubuntu hard drive is the primary, and that Ubuntu is to put GRUB on that one and work with that MBR. 

That way, when Windows updates the MBR on the Windows hard drive, it hopefully doesn't break GRUB or the MBR of the Ubuntu hard drive. With her setup, Windows shouldn't even need to know that Ubuntu even exists.

Consider cutting the Ubuntu hard drive in half - 500gb Ubuntu partition, and 500gb shared between Ubuntu and Windows (NTFS). For music and movies and sharing files and stuff.

Please remember to set up video card drivers.

Please remember to show the user how to access this shared partition from both Ubuntu and Windows, so the user can move stuff back and forth without headache.

Please remember to show the user how to connect to wireless networks in Ubuntu.

---

### Post by minasistani on 2011-04-13
> **earthpigg said:**
> ***This is for the folks at the Louisville LUG:***

Make sure you tell BIOS that the Ubuntu hard drive is the primary, and that Ubuntu is to put GRUB on that one and work with that MBR. 

That way, when Windows updates the MBR on the Windows hard drive, it hopefully doesn't break GRUB or the MBR of the Ubuntu hard drive. With her setup, Windows shouldn't even need to know that Ubuntu even exists.

Consider cutting the Ubuntu hard drive in half - 500gb Ubuntu partition, and 500gb shared between Ubuntu and Windows. For music and movies and sharing files and stuff.

Show the user how to access this shared partition from both Ubuntu and Windows, so the user can move stuff back and forth without headache.
Okay. Mercie!!

---

### Post by earthpigg on 2011-04-13
I'm not normally this over-the-top helpful, to be perfectly honest.

Your "friend" trying to charge you **$375 to install Ubuntu** made me feel betrayed and wanting to redeem nerdkind.

---

### Post by minasistani on 2011-04-13
> **minasistani said:**
> Okay. Mercie!!
I respect you guys even more. Thanks to You.

---

### Post by alphaamanitin on 2011-04-15
375 to install and "tinker" with Ubuntu is total BS.  I'd say you would have ended up paying him 375 for about 40 minutes of "work" and most of that would be waiting for the install CD to boot and waiting for it to install.

AlphaA

---

### Post by earthpigg on 2011-04-15
> **alphaamanitin said:**
> 375 to install and "tinker" with Ubuntu is total BS.  I'd say you would have ended up paying him 375 for about 40 minutes of "work" and most of that would be waiting for the install CD to boot and waiting for it to install.

AlphaA

i believe the standard method of operation for outfits like this is to take it for a full 24h and claim 5-6 hours of work.

---

