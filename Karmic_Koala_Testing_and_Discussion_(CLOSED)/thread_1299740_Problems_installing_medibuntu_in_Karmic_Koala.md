---
title: "Problems installing medibuntu in Karmic Koala"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 2blue on 2009-10-24
I have made a full reinstallation from CD. I am trying to type in the medibuntu repository command in terminal, but are having problems:  

> sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update


Is there a way to do this from Synaptic?

---

### Post by howefield on 2009-10-24
What's the problem ?

You can also download the debs from medibuntu and install.

[http://packages.medibuntu.org](http://packages.medibuntu.org)

---

### Post by 2blue on 2009-10-24
My main problem is that DVDs will not play. I keep typing in the mile long command for the medibuntu repositories, and it goes wrong, and will not install. 

Thanks for the list of binary packages, how do I find the right application to open with?

---

### Post by MelDJ on 2009-10-24
just go to software sources and add medibuntu to your third party sources

---

### Post by howefield on 2009-10-24
> **2blue said:**
> My main problem is that DVDs will not play. I keep typing in the mile long command for the medibuntu repositories, and it goes wrong, and will not install. 

Thanks for the list of binary packages, how do I find the right application to open with?

Not quite what I meant. I was referring to the problem you were having with the medibuntu command, you do not need to type it, copy/paste into the terminal all at once and press enter.

The only problem I had the other night was not being able to get the key as the server was down.

For dvds, try installing libdvdcss2 from the link I gave you.

---

### Post by 2blue on 2009-10-25
Thanks all of you. Medibuntu installed from termial eventually. Something is still missing, and I cannot make it read DVDs. That is Regular bought DVD movies. 

Any suggestions?

---

### Post by KrazyPenguin on 2009-10-25
sudo aptitude install libdvdcss2 vlc w32codecs

good luck!!!

vlc is a player
libdvdcss2 will allow to play dvds

---

### Post by 2blue on 2009-10-25
Thanks, but it seams I already have them. I got this message: 

[sudo] password for lovinguniverse: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
vlc is already the newest version.
w32codecs is already the newest version.
w32codecs set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

In VLC I get this message: 
Playback failure:
DVDRead could not open the disc "/dev/sr0".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for det. 

When I install disk in DVD-rom it will not mount. CD and burner works.

---

### Post by KrazyPenguin on 2009-10-25
well then that is your problem, the dvd won't mount.

So we need to figure out how to mount it.


Try this:
    sudo mount /media/cdrom0/ -o unhide

to unmount:
    sudo umount /media/cdrom0/

---

### Post by coffeecat on 2009-10-25
> **2blue said:**
> Something is still missing, and I cannot make it read DVDs.

Check whether you've got libdvdread4 installed. I believe it doesn't come with a default install. You need both libdvdread and libdvdcss (for the encryption).

What I always do with a new install of Ubuntu is first to install the metapackage "ubuntu-restricted-extras" which gives me libdvdread, flash, MS core fonts, and some other codecs and goodies. I also install VLC (which used to come from Medibuntu, but now comes from the Universe repository). Then I enable the Medibuntu repo for libdvdcss.

---

### Post by 2blue on 2009-10-25
I get this: 

-laptop:~$ sudo mount media/cdrom0 -o unhide
[sudo] password for laptop: 
mount: can't find media/cdrom0 in /etc/fstab or /etc/mtab

It looks like I have libdvdread4 too. From Synaptic I have installed all restricted packages I can find, and also medibuntu-keyring and non-free-codecs from [this]("http://packages.medibuntu.org/karmic/index.html") page. I can't figure out what I'm missing, is there any way to check this?

---

### Post by 2blue on 2009-10-25
Is VLC any good in Ubuntu, should I go for Xine instead?

---

### Post by 2blue on 2009-10-25
I seamed to miss the libdvdcss-dev package, and now DVDs both region1s and 2s  will mount, but reluctantly. It takes time for DVDs to mount, often repeated tries. It looks like my DVD player has become region free?

Thanks for all your help!

edit: DVDs are playing fine :-)

---

### Post by coffeecat on 2009-10-25
> **2blue said:**
> It takes time for DVDs to mount, often repeated tries. It looks like my DVD player has become region free?

Or possibly developed a fault. I have an optical drive, only a little over a year old, which did work fine at first, but recently refused to play or even recognise (most) commercial DVDs. It would work fine with data DVDs and unencrypted DVDs I had burnt myself. At first I thought, like you, that it was something to do with regions, but then I found that a couple of region 2 (all my DVDs are region 2) would play, but most would not. This was with Ubuntu. I took the drive out, put it in a USB casing and tried it with Windows and MacOS. Exactly the same: data DVDs, encrypted DVDs fine; most encrypted DVDs no go. The drive would simply churn away as though it was seeking something.

I replaced the drive.

Have you got or can you borrow an external USB DVD drive to test with your system? Then you'll be able to see whether it's a software issue in your system or a hardware issue with the particular DVD drive.

**Edit:** just seen your edit. :p If the problem is solved, I'm glad. But if you get a recurrence, bear in mind what I've said about the possibility of a faulty drive.

---

### Post by 2blue on 2009-10-25
Thanks Coffeecat, that is not impossible. I shall have to keep an eye on the DVD-rom. I don't play DVDs that often on it. Though right now looks like when Karmic got used to the libdvdcss-dev package it reads regular DVD easier. I have rebooted a couple of times and the DVD-player still seams to be region free. I have only a couple of region1 DVDs, most are region2.

---

