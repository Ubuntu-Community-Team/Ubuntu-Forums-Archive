---
title: "Upgrading to the latest version from 9.04"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by skeebs on 2011-05-25
Hi,

I've not really need the computer for much for a while and have let the updates slip! I've got 9.04 and obviously need a newer version. I read that it's best to upgrade to 9.10 first then go from there, but my version is so old all the information is using update manager (just click this button blah blah) but of course this isn't supported now so can't use that method.

I don't really know any other way to upgrade other than following the links in update manager so please can someone help me do this?

Thanks so much in advance!

ps forgot to say my cd coping sometimes messes up, don't know if it's software or hardware so was looking for methods to avoid downloading onto cds then upgrading from that! but will have to try this if no other way

---

### Post by zealibib slaughter on 2011-05-25
have you tried 
```

sudo apt-get dist-upgrade

```

---

### Post by skeebs on 2011-05-25
I have now and have tried different versions of sudo apt-get from other threads but it fails :(

---

### Post by zealibib slaughter on 2011-05-25
what about aptitude?
```
 
sudo aptitude dist-upgrade

```
 
or maybe by cd
[http://www.google.com/url?sa=t&source=web&cd=7&ved=0CDcQFjAG&url=http%3A%2F%2Fsuperuser.com%2Fquestions%2F65369%2Fupgrade-ubuntu-9-04-to-9-10-from-cd-not-work&ei=hmDdTd7MBKq_0AGO2NHRDw&usg=AFQjCNGqR7xd3P0FuzeFTcKVj0EkVBqPvA](http://www.google.com/url?sa=t&source=web&cd=7&ved=0CDcQFjAG&url=http%3A%2F%2Fsuperuser.com%2Fquestions%2F65369%2Fupgrade-ubuntu-9-04-to-9-10-from-cd-not-work&ei=hmDdTd7MBKq_0AGO2NHRDw&usg=AFQjCNGqR7xd3P0FuzeFTcKVj0EkVBqPvA)

---

### Post by skeebs on 2011-05-25
aptitude not having it either. Will attempt the cd... not sure if you saw my edited note about cd burning probs but I'll give it a go via your link and report back... thanks

---

### Post by coffeecat on 2011-05-25
@skeebs, both 9.04 and 9.10 have passed end-of-life so the routine repositories fail when you try to update or upgrade. You need to use the old-releases URLs in your sources in order to be able to update both those releases. More here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by zealibib slaughter on 2011-05-25
I think cd is the only way to go at this point.  You may not have to burn the cd at all. see this link [https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

---

### Post by skeebs on 2011-05-25
I dunno if I'm being really thick here but the links within the link you gave me are all referring to later versions than 9.10 so I'm still not getting info on how to get 9.10...? Or am I missing something really obvious :confused: (ref to fist link, just missed this last post...will check out now...)

---

### Post by skeebs on 2011-05-25
> **coffeecat said:**
> @skeebs, both 9.04 and 9.10 have passed end-of-life so the routine repositories fail when you try to update or upgrade. You need to use the old-releases URLs in your sources in order to be able to update both those releases. More here:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

sounds good will look into it now...

---

### Post by coffeecat on 2011-05-25
> **skeebs said:**
> sounds good will look into it now...

One other thing to bear in mind. That link hasn't been updated since October last year when 9.10 was still supported. Once you've upgraded from 9.04 to 9.10, you'll have to adapt those instructions to use the old-releases sources in 9.10 as well. Once you've arrived at 10.04, you will be OK with the routine sources.

---

### Post by skeebs on 2011-05-26
> **coffeecat said:**
> 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

I'm having problems with finding the source list that the instructions tell me to get in the first place. Like you said, it's not been updated for a while so maybe these instructions need to be adapted.

Still learning it all and trying to find my way round. Trying different sources seen in other links/info, but any further help from anyone would be appreciated as the only thing I have to do with computer programing is here on Ubuntu! Thanks

---

### Post by mörgæs on 2011-05-26
I am afraid this will be a long and cumbersome upgrade. I would recommend a live boot and after that a fresh install of 10.04 or 10.10. As of now, you don't even know how these releases behave on your hardware.

If you have problems burning a CD, you can also use a USB stick. More here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by skeebs on 2011-05-26
> **mörgæs said:**
> I am afraid this will be a long and cumbersome upgrade. I would recommend a live boot and after that a fresh install of 10.04 or 10.10.

Yeah I kinda was hoping I could get round this so I didn't have to copy so many files :wink:

> **mörgæs said:**
> 
If you have problems burning a CD, you can also use a USB stick.[/url]

Ah, now that I didn't think of. Right, off to buy more USB sticks!!

---

### Post by coffeecat on 2011-05-26
> **mörgæs said:**
> I am afraid this will be a long and cumbersome upgrade. I would recommend a live boot and after that a fresh install of 10.04 or 10.10.

+1. @skeebs, I was thinking this yesterday when pointing you to that link. It'll probably be quicker, and certainly more certain, to make a fresh install.

**EDIT**: Ah! I see you've made the decision. Good luck. :)

---

### Post by skeebs on 2011-05-26
This gets more and more... er... fun, doesn't it? ;)....

So now I'm wanting to install ubuntu 10.10 frm my sexy new usb external hard drive bought today, as the cd drive really isn't liking my attempts to use those to make an installation cd (a problem predicted when I started this thread!).

I was following a guide that tells me to download the ubuntu I want onto my desktop (done) then go to system>admin>start up disk creator then go through the process of selecting ubuntu 10.10 from desktop and my usb drive, but when trying to make start up disk I get the "error installing bootloader" message I gather many people have had.

I've looked into it and found I need to get GRUB2 as I've only got the 0.97, so need to manually install this (presumably). I was trying to follow this guide to do it:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("http://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

which makes it so simple when the **sudo apt-get install grub-pc** command doesn't come up with this:

> Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main os-prober 1.29ubuntu2
  404 Not Found
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main grub-pc 1.96+20080724-12ubuntu2.1
  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/o/os-prober/os-prober_1.29ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/o/os-prober/os-prober_1.29ubuntu2_i386.deb)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.96+20080724-12ubuntu2.1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.96+20080724-12ubuntu2.1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


so now what do I do? apt-get update doesn't work due to my dusty old version of 9.04BC (Before Christ that is) and I don't know what the second suggestion is on that final line...

---

### Post by coffeecat on 2011-05-26
I'm not following you 100%. Partly my fault - I had a couple of glasses of a rather nice wine with my supper. :wink:

Anyway... Are you trying to burn the 10.10 ISO to a USB flash drive using Startup Disk Creator in your Jaunty installation? If so, the "error installing bootloader" message was probably to do with syslinux, not grub, so you might want to forget about grub for now.

I'm going to theorise here. There was a bug which prevented burning of 10.10 ISOs with 10.04's Startup Disk creator because of a version incompatibility in syslinux. Which meant that if you were running 10.04, and wanted to make a bootable USB of 10.10 using Startup Disk creator, you were effectively snookered. :rolleyes: It worked - or rather, didn't work - the other way around. You couldn't create a 10.04 bootable USB in 10.10 - as I found out the hard way!

So my theory is that a syslinux version incompatibility between Jaunty and Maverick is getting in your way.

Since you've found you can't create a CD, I have to ask: do you have access to a usable version of Windows? You can create a bootable USB from an ISO in Windows. The exe app for this is in the ISO.

---

### Post by skeebs on 2011-05-26
yeah I'm kinda not following myself right now, been on it all day apart from popping to work and walking the dog!! Seen that many threads and command lines and new words I don't understand I'm sure they'll be chasing me in my dreams tonight... esp the grubs :D

You may be onto something with your theory, in my trawling through endless info about the error msg I didn't see anything like that mentioned so could be why I'm not progressing.

Anyway, my boyfriend has windows on his laptop which I can rip out of his hands and do your suggestion there. How do I do that in windows? (don't answer that I'm already looking at the how to's, stupid question I'm tired)

---

### Post by coffeecat on 2011-05-26
> **skeebs said:**
> Anyway, my boyfriend has windows on his laptop which I can rip out of his hands and do your suggestion there. How do I do that on windows?

I thought you might ask that! :)

Here's how:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows]("https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Windows")

The main challenge will be extracting the usb-creator.exe from the 10.10 ISO. Jaunty didn't come with the neat right-click > Open With Archive Mounter that Maverick does. And you won't be able to install ISO mounting software in Jaunty. So... The choice is to use one of the Windows apps mentioned in that link, or a terminal command in Jaunty. I'm going from memory here*, but I believe you need:

```
sudo mount -o loop -t iso9660 filename.iso /mountpoint
```Obviously, change filename.iso and /mountpoint to whatever they need to be.

* **EDIT**: just tried it. Memory correct!

---

### Post by skeebs on 2011-05-26
> **coffeecat said:**
> I thought you might ask that! :)

You got there before the edit :)

I think I'm gonna go to bed and try all this tomorrow after work. What else would I want to do on a friday night after all?

Thanks so much for being on the other end of this computer! :D

---

### Post by da_g_bomb on 2011-05-26
Or you could always find another way to upgrade.

Update the sources, but save the original first as /etc/apt/sources.list.ORIG
[PHP]
cp /etc/apt/sources.list /etc/apt/sources.list.ORIG
[/PHP]

Change the sources to your required new releases eg, jaunty/karmic. Remember you can only go one upgrade at a time.
These are the available updates
jaunty(9.04) ->karmic(9.10)
karmic(9.10) -> lucid(10.04)
That will at least get you to the latest LTS, safe for at least another 2 years when the next LTS comes out and if you still have the machine you can jump from this release to the next. Or you can pick up standard upgrading procedures from here as well.

[PHP]
sudo sed -i.ORIG 's/jaunty/karmic/g' /etc/apt/sources.list
[/PHP]

Backup the /etc/apt/sources.list.d/ folder and create an empty one in case you have any third party repositories.

[PHP]
sudo mv /etc/apt/sources.list.d/ /etc/apt/sources.list.d.ORIG/
sudo mkdir /etc/apt/sources.list.d/
[/PHP]
Then do the upgrade
[PHP]
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade
[/PHP]

You can then move your sources.list.d folder items back into place

---

### Post by mörgæs on 2011-05-26
Another option: 

On the Windoze machine, download the 10.10 ISO and Unetbootin. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by skeebs on 2011-05-27
I'm trying this first:

> **mörgæs said:**
> Another option: 

On the Windoze machine, download the 10.10 ISO and Unetbootin. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I've got the stuff on my flash drive, it's all in on my linux pc, I'm ready to re-boot from it. I've got to the BIOS menu looking to select an option to boot from usb.

Here's the directions I'm following: 

> while your computer is starting up to get to your BIOS boot menu and select USB drive as the startup target; otherwise if there's no boot selection option, go to the BIOS setup menu and change the startup order to boot USB by default.

So there's no "boot selection option"how do I do the second bit of the instrution of changing the startup order etc??

My BIOS menu basically has different ubuntu 9.04 options then bellow says:

> Press 'e' to edit the commands before booting, or 'c' for a command line

I've pressed both to have a look but I don't know what to enter to make it start up from usb :(

---

### Post by coffeecat on 2011-05-27
> **skeebs said:**
> My BIOS menu basically has different ubuntu 9.04 options then bellow says:

> Press 'e' to edit the commands before booting, or 'c' for a command line 			 		


I've pressed both to have a look but I don't know what to enter to make it start up from usb :(

That's not the BIOS menu; that's Ubuntu's grub menu. To get into the BIOS, you need to press a key long before the grub menu appears, while the POST screen is showing. The POST screen is the first thing to show as soon as you switch on. The POST screen *should* tell you which key - often del or F2, or some other function key. It may display a message which says, "press *whatever* to enter setup."

Some BIOSs can be difficult to get into. In which case I tap the appropriate key repeatedly and rapidly until I get the message, "entering setup" on screen.

---

### Post by skeebs on 2011-05-27
> **coffeecat said:**
> That's not the BIOS menu; that's Ubuntu's grub menu.

aaahh, ok, yeah I recognise that screen now (it's been a while :roll:). Well that killed it. Nothing happening when booting from usb except a blank screen and a cursor line. Plan B is to try your suggestion earlier, so will clear another pendrive and go through that one...

---

### Post by skeebs on 2011-05-27
We've done it Coffeecat & co (nearly) :D:D:D

I stumbled around and have some how got 10.04 on here and will try then upgrading to 10.10 tomorrow night.

For the benefit of anyone else needing this info, I used this 

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Which I did try yesterday I think but not with the flash drive I'm using now, so I'm a bit puzzled as to what I've done and how it's all worked!!

Eitherway, I'm nearly there and it hopefully will be easier tomorrow.

Thanks so so much for all your replies, I was really struggling and wouldn't have done much more than cry with out your help!! :D:D:D:D

---

