---
title: "Issues installing Ubuntu"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by Icerevolt on 2012-03-19
Hi this is my first post, so i don't know if there are any on this same topic but this is the problem i get when i try and install ubuntu 11.10.
I have a net book aspire one with Win XP SP2 (in czech -.-) 
I have currently used LiLi USB Creator to make my 1 tera HDD into a bootabke USB 
I have booted it and it recoginses the HDD as a bootable image and boots
It loasts and the 4 dots come that look like . . . . (and they blink-ish)
then it comes up and says
Begin: Loading essential drivers...done.
Begin:Running/scripts/init-premount...done.
Begin: Mounting root file system ... Begin: running /scripts/-premount... 
done.
done.
ata_id[393] : HDI0_GET_IDENTITY failed for '/devsdb':invalid argument
 
unmount: can't unmount /cdrom: Device or resource busy
Warning : Unable to find the persistence home medium
unmount: can't unmount /cdrom:device or resrouce busy 
Warning: Impossible to include the casper-sn Snapshot
unmount: cant unmount /cdrom: device or resource busy
Warning: Impossible to include the home-sn Snapshot
done.
Begin: Creating debconf-commuicate fifo mechanism ... done. 
Begin: Running /scripts/casper-bottom ... Begin:Moving mount points... ...done
.
Begin Adding live session user... ... _ 
 
And after i tried again and said something about trying to respawn trying to respawn...respawning too fast...
 
any adivce for me, not too savvy with techy stuff so a good explation will help like trying to explain to a grandma :) 
 
Thanks alot
 
[Edit]
 
Tried installing from a normal USB and it get past the pervious session but i still left it up just in case if it is important for this next bit because i got the same results as stated before.
The list goes down with a "* Starting..." a specif path and followed by [OK]. I got one [[COLOR=red]fail[/COLOR]] [COLOR=black]as far as i can see. [/COLOR]
Then the last line says "*Stopped System V runlevel compatibility"
Does that mean my laptop cannot handle ubuntu but can run crappy windowns -.-  ... say it aint so...
 
Again assistance is much appreciated
 
Thanks

---

### Post by varunendra on 2012-03-20
Hi Icerevolt, welcome to the forums.

Please post the specs of your laptop, especially the CPU and amount of RAM it has. Default current ubuntu requires about 1GB to run smoothly.

Also, if you want to use Ubuntu from a usb hard drive (either in live mode or properly installed), you don't need any third party tool to make it bootable. Ubuntu installer would automatically do it for you.

However, I believe it is the no-cd-drive limitation of the netbook that is forcing you to do so. If so, try [unetbootin]("http://unetbootin.sourceforge.net/") instead.

For your info, the live session has some limitations (even with persistence). So for a usb hard drive (internal or external), a full installation is recommended. My preferred way to do it on a 'No cd drive system' is:

[LIST]
[*]Install VMware or VirtualBox on the currently running OS > create a 'blank' virtual machine in it > boot it from the downloaded iso > connect the usb hard drive to it > install Ubuntu on it as usual. If this seems too much work (although it isn't, and having VMs proves very useful later), then another way is:
[/LIST]

[LIST]
[*]Create a bootable usb flash drive using Unetbootin > boot the computer with it > connect the usb hard drive to it > install Ubuntu from the flash drive onto the hard drive. In this method, you have to be careful to make sure the bootloader is installed on the external hard drive, not on the internal one.
[/LIST]
Please tell me if it seems too 'tekky' :) I'll try to simplify the description.

---

### Post by Icerevolt on 2012-03-20
The computer of the top of my head (checked last night) has 2 Gb of ram and as the CPU I think it has 1.86 or 1.68 dual core. 
I don't think the specs are any problems, but what I suspect is, the fact that I got the install from a friend. So I'm suspecting it could be corrupt or some thing else (it's version 11.10). I started downloading my own copy from the Ubuntu server ( version 10.04) so I'm going to try and use this one. I'll see how it works out when I get back to my lappy. 
If this dosent help, I'll use one or both of your methods you mentioned previously. 
Thanks for the help I'll keep you posted. 

N.B. you said something about limitations of booting from USB...I don't know if u mean It should and it not doing it or you assume that it can't boot from USB. Either way I'll add this so just invade u mean one of tr two when I press [F2] it takes me into the blue boot menu. I can then go into the boot order menus and choose the order, I have USB CD drive and USB HDD. I choose USB HDD to be 1st and I believe that why it's booting from USB.

[EDIT] 

I got it working...thanks fr your help :) much appreciated. Uhhh but yea do u know how to make it less laggy?

---

### Post by varunendra on 2012-03-21
> **Icerevolt said:**
> N.B. you said something about limitations of booting from USB... No, it's not about the capability to boot from usb. The limitations in a 'Live installation' are that you can't do kernel updates, sometimes may encounter "insufficient space in /tmp"... type errors, sometimes a bit slower loading time/performance etc.

It is fine and actually recommended for flash drives, since their read-write cycles are very limited in comparison to a hard disk, and the live mode takes good care of this. But for a hard disk, a full installation is recommended to overcome these limitations and get full advantage of Ubuntu.

So, what kind of installation did you make? Full or Live? It would also be interesting to know which method you used.

As for the 'lagging' problem, I don't understand it properly. If you could elaborate the problem you are having, maybe we can find the reason and a solution for it.

---

### Post by mastablasta on 2012-03-21
> **Icerevolt said:**
>  I can then go into the boot order menus and choose the order, I have USB CD drive and USB HDD. I choose USB HDD to be 1st and I believe that why it's booting from USB.
 ?
 
hmm. try to unplug the USB cd drive and boot only with USB HDD attached?
 
LiLi is a good USB creator as is Unetbootin.
 
Here is how you install using virtual box (if you just want to give it a spin):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
10.04 is from april 2010 and it's age is starting to show. if you have new hardware it is better to use 11.10 as it has newer kernel and also newer drivers. they are also different (10.04- uses GNome2, 11.10 uses Unity on top of Gnome3).
 
Additonally if you experience slow performance using live image you need to know that all system is being loaded into ram and that could take some time and it's responsiveness might not be as good as on install. also in live boot oyu owuld need ot any additional install drivers each time you boot.
 
If you have some low powered graphics chip or if you don't want to install grpahics drivers each time then you might want to use Unity2D as it doesn't use hardware acceleration. 
 
hard to give more advice on this issue since we don't know your full hardware specs.

---

### Post by Icerevolt on 2012-04-04
Sorry I didn't get back to you sooner, iv been busy with exams and college crap... The lagging issue is that movement of the mouse causes it to like lower fps. U know when u have a crappy graphics card and u try to play a high end game (ie...crysis 2) and u put everythinong to HIGH I get that effect when I minimize, open, close, click etc ... So I hoped that helped.

---

