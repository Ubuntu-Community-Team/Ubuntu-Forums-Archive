---
title: "Install on Thinkpad 600, how to add network"
date: 2005-01-03
forum: Installation &amp; Upgrades
---

### Post by Sentient on 2005-01-03
This is my first foray into the Linux world and ubuntu has had lots of good press so here is where I am starting.

I created the ISO disk and then installed it on an old IBM Thinkpad 600 with a pentium 233MHz processor and 128MB of RAM, the hard drive is about 3GB.  I told it to erase the drive and create it's own partition and the install went smoothly, if not particularly quickly for some time.  During install I left the D-Link Wireless G (DWL-G650) PC card to the side so that the machine would have a simple configuration.  I figured I could add the card later.

When the install asked if I wanted to go online for updates I declined since it has no network at this point.

After booting to the desktop I prowled around looking for a way to add the wireless card.  First I inserted the PC Card and nothing happened.  I guess that is OK, I don't know if ubuntu has plug n play.  So I looked at the device manager and don't even see a PC card controller or a wireless apapter listed.  So I decided that ubuntu may need to boot with the card installed before it sees it.  I did so and noticed during boot a message that may be related.  It said

PnP: Unable to assign resources to device 00:0d

later on it says Starting PCMCIA services   [OK]

So it looks like it should see the card, I hope.

I am not sure what step to take next.  How would I go about getting the wireless adapter recognized so I can enable it and link into my network?  I think I am close, but clueless.

Sentient, feeling strongly clueless at the moment.

---

### Post by Sentient on 2005-01-03
Making progress.  Given some time after booting with the card installed the wireless installation wizard now sees ath0 and I tired setting it up, but so far no soap.  Will it accept a hex wep key?  do I need to preceede or follow it with some sort of hex delimiter?  Where do I tell it to use 128 bit key?  

Advice welcome.

Sentient, and feeling a little less clueless as I wander the land of gnome

---

### Post by poptones on 2005-01-03
That card is not on any supported list I have seen. I have numerous 600s of varying vintage (600e, 600x, etc) and they have had zero trouble with NIC cards, which leads me to believe they would have little trouble with any other (it's just an intel BX chipset with a well supported cardbus adapter) but wireless has been low on my priority list and the only card I have doesn't work in linux at all. I've checked a few times because that card is inexpensive, and I've never seen it on a linux distributiuon's HAL.

---

### Post by Sentient on 2005-01-03
:sad: OK thanks.  ubuntu thinks it is an Atheros chipset.  It is probably a bit more proprietary in some way.  Can you point me to a list of supported PCMCIA wireless adapters?

Thanks,

Sentient

---

### Post by Sentient on 2005-01-04
I found that adapter in a list on the ubuntu website.  Says it does not work out of the box but can be made to work with an open key.  There were links to several very technical pages that are appropriate for a professional integrator or major hobbyist, but beyond this newbie.  I will try degrading my network security to open authentication instead of shared key to see if I can make it work.

Sentient

---

### Post by Sentient on 2005-01-04
OK
I have it working and am posting over my wireless connection.  If anyone can tell me how to tell this mad-wifi driver how to use a shared key instead of an open one I would love to learn how.  Shared key sounds more secure to me and I worry that my wireless might be exposed with its current configuration.  

I see the website is a treasure trove of information if a person has time to dig for it.  I guess linux is an RTFM world.

Next tasks figure out how to download the patches the install couldn't get to with no network and get SMB support working so I can see my windows boxes shared folders.

Sentient, feeling happy to be getting things working  :D

---

### Post by Sentient on 2005-01-06
Setting my network to used open authentication killed my Tivo network connection so I had to put it back.  Where can I find information on how to make the mad-wifi driver use shared key instead?

Sentient

---

### Post by Sentient on 2005-01-07
After spending way too much time reading posts I see that getting madwifi configured to work with this card in ubuntu is probably too hard.  Sound and power management aren't working either, but I wasn't going to try fixing those until I got an internet connection.  I think I will try some different distributions, that seems easier than this has been so far.

Any suggestions what distribution will work with a TP600 with 128M of ram, a pentium-mmx cpu running at 233MHz, some sort of custom sound and modem processor and a PCMCIA wireless card that needs madwifi to run?

Thanks in advance,

Sentient, hoping I am not still talking only to myself.

---

### Post by Dan on 2005-01-07
I use aironet 350 wlan adapters, they will work straight out of the box with almost any distro, as long as you don't need 54g I don't think you can find a better one.

---

### Post by Sentient on 2005-01-07
Yes, I could go out and buy a new wireless adapter.  However, I sitll have other problems like no sound, having to reinsert the PCMCIA card after bootup each time to get it recognized, no power management or ability to power down that make me think this hardware is just too old / different to work with ubuntu.  
I think a cheaper solution of trying other distros will be my first cut at it.  If I do decide to spend money, I will probably just pick up a newer laptop on ebay and use the windows that comes on it.  I thought I would try Linux on this beast since win98se was so slow and clunky on it and Linux has a reputation of being speedy on old hardware.  So far I think what I am learning is that I need to become a hobbyist for this idea to work. 

Thanks for the suggestion.

Sentient, feeling deeply it is time to give up on this.

---

### Post by Dan on 2005-01-07
Unfortunately my 600x died , I now use a T22 and have had no problems at all. I wouldn't recommend getting an all singing and dancing laptop unless you really need the massive storage and fast CPU, you can pick up second hand IBM's at very reasonable costs these days.

---

### Post by fng on 2005-01-07
Dont give up now Sentient!
What soundcard is in the laptop?
Any other issues?

---

### Post by WTF_Shelley on 2005-01-10
yes keep going! it worth it in the end

---

### Post by Sentient on 2005-01-10
I will gladly keep it up if I can.  First, this is a secondhand laptop for my kid to use at high school.  It is cheap specifically since it is less likely to be stolen that way.

I have no idea what sound card it has or a good idea how to find out.  The ibm website wasn't a lot of help, although I am not sure I was looking in the right place there.  I did find some google sites pointing to people who succesfully installed Linux on this or similar laptops, but the descriptions were at a high level and assumed I would understand what they were talking about.  They used terms like emerge and daunting processes like "compile the kernal".  I am not up for those.  
I needed to have this thing running by today for him.  So I am quicly reinstalling win98se and putting a very old version of office on it and hoping that the fresh install will let it run semi-acceptably.  I know keeping it off the internet will help.  I hate that word will still takes a minute to load.  Powerpoint will take two minutes, that's what I saw the last time I freshened it.  My experience with open office with ubuntu was even slower though, so it looks like I would need a very slimmed down linux with something less powerfull than gnome.  But then I don't know if he would be able to use it. 
I might take another run at this at spring break.  Can anyone point me to "installing linux on laptops for dummies" with line by line recipes that have eplanations at a very low level what is going on so I can learn it?
Also, any good ways to learn accurately what hardware this beast has in terms of sound card, and power management?  I am sure I will need to do some sort of customizations for those and having a place to start will help.  If I start reading and studying now, I might be up for it by spring break.

Thanks for the encouragement.

Sentient, regrouping for now

---

### Post by wolfchri on 2005-03-13
Hello there,

if you want to use a PCMCIA card for network (I guess you will, what other way is there for networking), the IBM Thinkpad 600E is a little bit picky with IRQs. I succeeded with the boot parameter 

pci=noacpi 

- after that was able to use both of my network cards (both Netgear, the WG 511 for wlan, another for LAN/ethernet). Ubuntu is kind of difficult here, i did not have this problems when I used PClinuxOS on this machine - but PClinux OS is extremely slow, so it is actually not really usable on the 600E, despite is better hardware detection and IRQ settings.

I am still working on the sound issue too, however, i am sure that it will work , since it worked on PClinux OS already on this machine, after i set up the module paramters as described in the IBM docs for installing Linux on the 600E.  Here, I had to change DMA parameters to get the sound clear.

---

### Post by chrisw on 2005-03-13
[QUOTE=wolfchri]
I am still working on the sound issue too, however, i am sure that it will work , since it worked on PClinux OS already on this machine, after i set up the module paramters as described in the IBM docs for installing Linux on the 600E.  Here, I had to change DMA parameters to get the sound clear.[/QUOTE]

Do you have a link to that doc ? 

I have an old 600E kicking about, it might be interesting to try and get Linux on it.  Win2k does run on it OK, once it finaly boots but does need a hefty chunk of RAM.

---

### Post by wolfchri on 2005-03-15
Here is the link to the IBM doc:

[http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-4BP6Q6.html)
However, that applies to a 2.4.x kernel - Ubuntu uses a 2.6.x

My problem currently is on Ubuntu, that the system does not even see ANY devices - when runnung pnpdump, it does not find any ISA PNP devices. I am getting frustrated - how the heck can I make the system see the devices? 

That is probably also the reason why modprobe snd-cs4236 or snd-cs4232 always says no such device - obviously, the soundcard is not visible at all. 

Way easier in PCLinux OS - you just use drakconf and change the driver. However, PCLinux is so slow on the Thinpad 600 that one cant use it. Ubuntu is really fast with my 296 MB Ram.

---

