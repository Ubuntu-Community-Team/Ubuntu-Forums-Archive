---
title: "Alpha 1 released"
date: 2008-11-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewfn on 2008-11-22
Alpha 1 of Jaunty is available here: 
[http://cdimage.ubuntu.com/releases/9.04/alpha-1/](http://cdimage.ubuntu.com/releases/9.04/alpha-1/)
Come and get it!
(Only server and alternate this time)

---

### Post by Gina on 2008-11-22
Thank you - downloading it now :)

---

### Post by Slug71 on 2008-11-22
Downloading now. What Kernel does it have?

---

### Post by volanin on 2008-11-22
Still 2.6.27-7-generic.

---

### Post by Slug71 on 2008-11-22
Meh, in that case i'll wait.

---

### Post by int on 2008-11-22
> int@int:~$ uname -a
Linux int 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686 GNU/Linux

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)

---

### Post by Kevbert on 2008-11-22
Strange that the kernel isn't 2.6.27-9 which should be out. :confused::confused::confused:
And you can't upgrade from pre-Alpha to Alpha1 as the kernel stays as 2.6.27-7. Looks like a new install of Alpha1 is required.

---

### Post by autocrosser on 2008-11-22
Funny---I had downloaded the .27-9 kernel a couple of days ago--it showed up in Synaptic--just no restricted drivers with it yet---really looking towards the .28 kernel.....

---

### Post by ronacc on 2008-11-22
why they even bothered putting out alpha1 without atleast the .28 kernel is beyond me .

---

### Post by plun on 2008-11-22
> **ronacc said:**
> why they even bothered putting out alpha1 without atleast the .28 kernel is beyond me .

Well... the kernel tree is at least up

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)


Maybe a problem with "whining" users and bugs...

---

### Post by jerrylamos on 2008-11-22
Alternate install did on my test VIA motherboard pc.  Yes it's got the -7 kernel.  I've got 3 jaunty installations, a couple with -8 and a couple with -7.  From an ordinary users standpoint I can't tell the difference.

Doing some setup now.  I couldn't find ubuntu-restricted-extras.

Jerry

---

### Post by Slug71 on 2008-11-22
Hmmm, well i went ahead and did the install anyway and i have 2.6.27-7??

---

### Post by eragon100 on 2008-11-22
> **jerrylamos said:**
> Alternate install did on my test VIA motherboard pc.  Yes it's got the -7 kernel.  I've got 3 jaunty installations, a couple with -8 and a couple with -7.  From an ordinary users standpoint I can't tell the difference.

Doing some setup now.  I couldn't find ubuntu-restricted-extras.

Jerry

I suppose it will be available in final jaunty? If not I will simply stop using ubuntu, and move to something that does allow me to use non-free codecs, fonts, flash etc. OpenSuse for example. Or fedora 10, fedora now has a package that automagically install non-free codecs, like ubuntu-restricted-extras.

---

### Post by plun on 2008-11-22
> **jerrylamos said:**
> 
Doing some setup now.  I couldn't find ubuntu-restricted-extras.

Jerry

I just checked this after my blowout and it works....

```
sudo apt-get install ubuntu-restricted-extras

```


```
Setting up msttcorefonts (2.6) ...
**Setting up ubuntu-restricted-extras (25) ...**
Setting up unrar (1:3.8.4-1) ...

Setting up sun-java6-bin (6-10-0ubuntu2) ...

Setting up sun-java6-jre (6-10-0ubuntu2) ...

Setting up sun-java6-plugin (6-10-0ubuntu2) ...

Processing triggers for libc6 ...

```

---

### Post by ronacc on 2008-11-22
heres a question , why are the kernel updates insisting on installing Lilo ? I just updated to 27-9 and it insisted on lilo so did -7 .

---

### Post by Foaming Draught on 2008-11-23
Well it´s a bit anticlimactic just now, no new kernel, no OpenOffice 3 and no Firefox 3.1.  In fact, if I hadn´t downloaded and installed Alpha 1 myself, and then personalised it, I´d think that I was still running Intrepid.

But everything works, so I´ve got a nice platform ready and waiting for all those lovely updates to which so many of us are addicted and which we´re desolate without before the first Alpha of a new release :)

---

### Post by Kevbert on 2008-11-23
> **ronacc said:**
> heres a question , why are the kernel updates insisting on installing Lilo ? I just updated to 27-9 and it insisted on lilo so did -7 .

How did you get 27-9. Only got 27-7 via the 64 bit alternative install. Still have the same old problems, no ntfs drives, no floppy, sound, orca, but install went without a hitch.

---

### Post by jerrylamos on 2008-11-23
> **jerrylamos said:**
> Alternate install did on my test VIA motherboard pc.  ... I couldn't find ubuntu-restricted-extras.

Jerry

Did upgrade today and the ubuntu-restricted-extras showed up in Synaptic.  Will install and check out Leona Lewis.

Jerry

---

### Post by ronacc on 2008-11-23
> **Kevbert said:**
> How did you get 27-9. Only got 27-7 via the 64 bit alternative install. Still have the same old problems, no ntfs drives, no floppy, sound, orca, but install went without a hitch.

its in synaptic , the restricted moudules aren't done yet so it doesn't update yet but I just installed the image and headders since I use the 180.08 nvidia driver and hand install it. If you need drivers from the restricted set don't use 27-9 yet unless you like low graphics mode.

---

### Post by jerrylamos on 2008-11-23
> **jerrylamos said:**
> Did upgrade today and the ubuntu-restricted-extras showed up in Synaptic.  Will install and check out Leona Lewis.

Jerry

No go!  After today's updates & ubuntu-restricted-extras, sound is DEAD.

This VIA motherboard was the only one of my three Jaunty pc's that would play sound.  The others are an IBM Thinkpad and a Compaq Presario.  No more.

In System Preferences Sound I can get a scratchy tone out of one of the four ALSA choices, and of course PULSE AUDIO IS DEAD.

Oh, well, usual excuse, this is an Alpha, wait for ....... or else boot up an Intrepid image which works fine.

Jerry

---

### Post by bodhi.zazen on 2008-11-23
The kubuntu alternate install disk fails for me.

1. First it is too large an iso to burn to a CDROM (And who wants to burn a DVD image ?).

2. Second, when installing, the base install fails.

Will try Ubuntu.

---

### Post by Gina on 2008-11-23
> **bodhi.zazen said:**
> The kubuntu alternate install disk fails for me.

1. First it is too large an iso to burn to a CDROM (And who wants to burn a DVD image ?).

2. Second, when installing, the base install fails.

Will try Ubuntu.What's wrong with burning a DVD?  It's faster.  I use DVD+RW discs for development testing.  I find them more reliable than CD-RW - I only use CD-Rs for the full release (or DVD-R for Ubuntu-Studio).

---

### Post by philinux on 2008-11-23
Alternate iso bittorent, no seeders. Bah.

---

### Post by bodhi.zazen on 2008-11-23
> **Gina said:**
> What's wrong with burning a DVD?  It's faster.  I use DVD+RW discs for development testing.  I find them more reliable than CD-RW - I only use CD-Rs for the full release (or DVD-R for Ubuntu-Studio).

To be honest, it would be nice if the alpha/beta releases actually worked in virtualization (KVM, VMWare, Virtualbox). I was able to install ubuntu into KVM, but as was typical of 8.10, the mouse does not work.

Changed to the console to manually attempt configuration -> and the console is a colored mix if giberish :(

---

### Post by Progressive on 2008-11-23
Upgrading worked for me :)

---

### Post by ktp on 2008-11-23
That looks pretty good.

---

### Post by k64 on 2008-11-23
Are There Any Screenshots Of Jaunty Alpha 1 Out There? I Really Need A Preview.

---

### Post by Gina on 2008-11-23
ATM it looks just like Intrepid.

---

### Post by Changturkey on 2008-11-23
> **ktp said:**
> That looks pretty good.

Almost makes we want to switch to KDE.

---

### Post by Foaming Draught on 2008-11-25
Well this is fun.  Intrepid has a more recent kernel (2.6.27.10) than Jaunty (2.6.27.7).  When I downloaded the former this afternoon on an Intrepid notebook, I said to myself, "Good-o, I'll get home and 2.6.28 will be waiting."  But it's not.

---

### Post by jerrylamos on 2008-11-25
> **Foaming Draught said:**
> Well this is fun.  Intrepid has a more recent kernel (2.6.27.10) than Jaunty (2.6.27.7).  When I downloaded the former this afternoon on an Intrepid notebook, I said to myself, "Good-o, I'll get home and 2.6.28 will be waiting."  But it's not.

Oh, yeah?

Intrepid 2.6.27.10 KILLED SOUND.  Oops, no way to un-update?  Where's that old Intrepid CD, I'll have to re-install, and then DON'T UPDATE!

Well, it does crackle a little bit, and I can get a tone out of System Preferences Sounds by picking OSS however nothing else Ubuntu uses does OSS.

From an "It Works!" standpoint Hardy is Ubuntu's peak.  Intrepid's going downhill, first Compiz doesn't work on many Intel graphics chips, now sound doesn't, what's next.

I guess I need triple boot now - Jaunty, Intrepid, and Hardy....

Jerry

---

### Post by Slug71 on 2008-11-25
> **jerrylamos said:**
> Oh, yeah?

Intrepid 2.6.27.10 KILLED SOUND.  Oops, no way to un-update?  Where's that old Intrepid CD, I'll have to re-install, and then DON'T UPDATE!

Well, it does crackle a little bit, and I can get a tone out of System Preferences Sounds by picking OSS however nothing else Ubuntu uses does OSS.

From an "It Works!" standpoint Hardy is Ubuntu's peak.  Intrepid's going downhill, first Compiz doesn't work on many Intel graphics chips, now sound doesn't, what's next.

I guess I need triple boot now - Jaunty, Intrepid, and Hardy....

Jerry

:lolflag::lolflag:

Poor ol Intrepid.

---

### Post by jerrylamos on 2008-11-27
Well, one of the 6 pc's on our home network will boot from USB.

The oversized Alpha 1 did fit on a 2 GB USB, it did run, and it did install.  Two other pc's are awaiting Alpha 1 to reduce (i.e. go on a diet) to get on to a CD.

Jerry

---

