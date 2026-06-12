---
title: "We NEED to support the Eee Models this time around."
date: 2008-12-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chris062689 on 2008-12-01
I love using Ubuntu on my Eee, but it's such a pain to set up, why can't Ubuntu simply support the Eee Models?  Can't the array kernel be merged into upstream?  I think Ubuntu will lose a lot of valuable customers that may not have heard of Ubuntu / Linux before using it with their netbooks, and if Ubuntu doesn't work out of the box with them, people are going to pass it up.

---

### Post by ronacc on 2008-12-01
+1 on that . and an included utility to burn the Iso to a usb thumb drive or sdhc card would really help for those who don't have a usb cd/dvd drive to boot their eee from . There are a couple of good projects out there but they need to be "officialy" supported.

---

### Post by snowpine on 2008-12-01
I agree it would be nice if Ubuntu worked on the eee out-of-the-box. That being said, it is very easy to get it working using the array.org kernel--only takes a few minutes.

I've always assumed the reason it doesn't work is that the wireless driver is non-free (so it can't ship with Ubuntu). Does anyone know for a fact that this is the reason?

---

### Post by eentonig on 2008-12-01
> **ronacc said:**
> +1 on that . and an included utility to burn the Iso to a usb thumb drive or sdhc card would really help for those who don't have a usb cd/dvd drive to boot their eee from . There are a couple of good projects out there but they need to be "officialy" supported.

That already exists.

---

### Post by meborc on 2008-12-01
how about this - [http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

isn't this supposed to work on netbooks?

---

### Post by snowpine on 2008-12-01
> **meborc said:**
> how about this - [http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

isn't this supposed to work on netbooks?

The netbook interface is a new interface for Ubuntu. Some people think it looks great on a netbook's small screen. But if Ubuntu does not support your eee's wireless adapter (for example), adding the netbook remix will not change that. It's only an interface, doesn't come with any special drivers.

Most people using Ubuntu successfully on the eee seem to be using the kernel from array.org, either adding it to "vanilla" Ubuntu or using Ubuntu eee.

---

### Post by ronacc on 2008-12-01
> **eentonig said:**
> That already exists.

yes from 3rd parties or using DD from terminal, hardly what I would expect newbes to know where to find or be able to use .

---

### Post by snowpine on 2008-12-01
> **ronacc said:**
> yes from 3rd parties or using DD from terminal, hardly what I would expect newbes to know where to find or be able to use .

No actually starting with Ibex there is a very easy-to-use "Create a Bootable USB" application under the System->Administration menu.

---

### Post by xat_ on 2008-12-01
That's what this is for - [https://launchpad.net/ubuntu-eee](https://launchpad.net/ubuntu-eee)

Ubuntu eee does come with the array.org kernel, but it's on a different development cycle than Ubuntu. Intrepid is due for January 2009.

---

### Post by ronacc on 2008-12-01
> **snowpine said:**
> No actually starting with Ibex there is a very easy-to-use "Create a Bootable USB" application under the System->Administration menu.

thanks for the tip , it isn't installed by default but I found it in synaptic does it do sd cards too ? I prefer them to usb sticks which stick out the side and are vulernable to breakage if you carry the thing around which I do .

@ xat_ I have that installed on an sd card right now , works nice after I massaged grub a bit. but it is not part of the official release which is what the OP was talking about .  I have several sd cards with different distos so I can change the "personality" of my eee just by plugging in a card :) also as a side note unetbootin dosen't work with jaunty it complains about libuuid which is there but the wrong version ( its a later version in jaunty).

---

### Post by meborc on 2008-12-01
> **ronacc said:**
> thanks for the tip , it isn't installed by default

yes it is... i just did a fresh intrepid install... and there is the usb disk option in system-admin

---

### Post by ronacc on 2008-12-01
possibly in the release , mine intrepid was installed at A3 and upgraded through release then to jaunty and it was't there until I installed it .

---

### Post by Gina on 2008-12-01
And it's in Jaunty too - I just checked :)  Will take a look at that soon - saves the hassle of CDs or DVDs (not that it's that bad).  I've not yet tried a USB or memory card install - I expect it's much quicker.

---

### Post by ronacc on 2008-12-01
hmm I wonder why it wasn't in mine ? I'll give it a try later tonight .

---

### Post by Gina on 2008-12-01
I did a fresh install from Jaunty Alpha 1 and Intrepid final releases.  Both with new home partitions (separate).

---

### Post by chris062689 on 2008-12-01
This isn't really a thread about the new USB launcher, please don't go offtopic, we need the Eee's to be supported!

What's the chance of getting them into Ubuntu, and then going upstream?  What can I do to help?  :lolflag:

---

### Post by snowpine on 2008-12-01
> **chris062689 said:**
> This isn't really a thread about the new USB launcher, please don't go offtopic, we need the Eee's to be supported!

What's the chance of getting them into Ubuntu, and then going upstream?  What can I do to help?  :lolflag:

Hi Chris, 
As I mentioned in my previous post, Ubuntu works really well on my eee except for the wireless card not being supported. This is because it uses a non-free driver. As you know, Ubuntu does not ship with non-free software for various philosophical and legal reasons. (For example, this is why Ubuntu does not include the Flash player.) If you can write a free, open source driver for the eee's wireless card, that would be the biggest help in terms of future Ubuntu releases supporting the eee, in my opinion. Glad to have people like you involved!

---

### Post by ronacc on 2008-12-01
> Ubuntu does not ship with non-free software  ubbuntu does not ship with non-free software installed by default it does in some cases make non-free software available through ( but not necessarily from ) the repos , for example the restricted drivers and flashplugin non-free . I'm sure they could accomidate the wireless driver in that fashion and the eee does have an ethernet port .

---

### Post by snowpine on 2008-12-01
> **ronacc said:**
> ubbuntu does not ship with non-free software installed by default it does in some cases make non-free software available through ( but not necessarily from ) the repos , for example the restricted drivers and flashplugin non-free . I'm sure they could accomidate the wireless driver in that fashion and the eee does have an ethernet port .

I thought the madwifi driver needed for the eee was already in the Ubuntu repos? (Never actually tested it, since I went for the array.org kernel insteaad.)

Flash plugin is also in the repos; would you say that "Ubuntu supports Flash out-of-the-box"?

---

### Post by ronacc on 2008-12-01
madwifi is included in the linux-restriced-modules package in the repos , I never used it either I installed ubuntueee with the array kernel also .

---

### Post by chris062689 on 2008-12-01
I also just used the array kernel...

---

### Post by InfinityCircuit on 2008-12-02
What exactly is not supported?

Intrepid should support the Celerons out of the box.

rt2860sta will be mainline kernel by 2.6.29, which probably will make Jaunty.

rt2800pci will be functional ~june which will make jaunty+1.

---

### Post by chris062689 on 2008-12-02
Mostly the Wifi (which probably should show up in Hardware Manager) FN keys, Turning Off the Machine doesn't actually turn it off, etc.
Just minor things that really add up.

(Eee 4G on mine)

---

### Post by Triggerhapp on 2008-12-02
Using array kernel and Hardy on my eeepc, mainly cause Intel drivers borked Runescape HD in intrepid :)

---

### Post by olskar on 2008-12-02
> **ronacc said:**
> madwifi is included in the linux-restriced-modules package in the repos , I never used it either I installed ubuntueee with the array kernel also .

But madwifi is open code now? Even atheros is released with some kind of BSD-license now?

[http://madwifi-project.org/wiki/news/20081129/sam-leffler-releases-hal-source](http://madwifi-project.org/wiki/news/20081129/sam-leffler-releases-hal-source)

---

### Post by ronacc on 2008-12-02
I don't know why it is that way , I just went to synaptic and searched on madwifi and linux-restricted-modules is waht came up .

---

### Post by silkstone on 2008-12-02
As mentioned in an earlier post, Ubuntu-eee supports the eee PC out of the box and includes the Array kernel. You can also run the Elmurato scripts which make the silver function keys do useful things. I'm typing this on an eee PC 901 running Ubuntu-eee and everything seems to work very well.

Unfortunately Ubuntu-eee is a separate project and is not supported by Canonical who have asked the developers to change the name for copyright reasons. I think this is misguided since the Ubuntu-eee developers are doing a great job and should be encouraged. A possible outcome is that they will change it to something that makes no reference to Ubuntu, and personally I don't think that is helpful to either party.

There is also eeebuntu (which I think has escaped the attention of Canonical's lawyers so far), and a new version of this (based on 8.10 and with the Array kernel) is due out very soon.

It would be good if Jaunty provided full support for the eee PC, but it's a pity that those who have already achieved this are not part of the project.

---

### Post by sloggerkhan on 2008-12-02
Don't be so damned eee-centric. What is needed is not just eee support, but a general distro that is specifically targeted towards netbooks. Eee users aren't the only ones who've got to deal with annoying hardware tweaks and driver issues on their netbooks. As an example, try an Acer Aspire One. No matter what you do, there will probably be something that doesn't work quite right, and good luck getting battery life near that of Linpus. 

Seriously, let's see a distro that has support for netbooks in general.

---

### Post by ronacc on 2008-12-02
since the EEE is what started the ball rolling it is sometimes used as a generic for netbook like coke is used when people mean softdrink . and I think Ubuntu is being shortsighted in not taking advantage of the work done by  ubuntueee (and others) since many of their tweaks would translate directly to other netbooks and that is for sure a growing market where linux has an advantage and already has a "foot in the door".

---

### Post by silkstone on 2008-12-02
It is indeed the aim of the Ubuntu-eee developers to extend support to all netbooks, but they had to start somewhere and the Asus eee PC was the first out of the trap.

---

### Post by snowpine on 2008-12-02
This is good news (I think): [http://ubuntuforums.org/showthread.php?t=1000028](http://ubuntuforums.org/showthread.php?t=1000028)

---

### Post by scaine on 2008-12-02
I'm using an EEE 701 with Intrepid.  The only two things I've had to do after install (making sure it's connected to an ethernet cable) is :
1. Install Linux Backport modules (activates WIFI)
2. Edit /etc/init.d/halt to include "rmmod snd-hda-intel" (fixes shutdown).

Everything else works perfectly.  Okay - not quite then... the sound up/down hotkeys don't work, nor does the WIFI toggle.  But then those keys are simply convenience keys anyway.  And the brightness hotkeys DO work anyway.

So, sure, not perfect, but a two-step fix for a perfect Ubuntu experience is actually pretty amazing considering Intrepid never really intended to focus on providing support for the EEE specifically.

Oh, and the Acer Aspire One requires only the first step (above) and it too is a near-perfect install.  Its WIFI hotkey actually does work, but there's no notification of it doing so, which is a shame.  It's sound keys and brightness keys work perfectly after install.

You can be pedantic about this - technically, although the processor does scale normally on the EEE, you can't control it with the CPU scale applet until you add [FONT=monospace]"[/FONT]p4_clockmod" to /etc/modules.  I'm sure that there's other minor niggles, but the core experience is spot on.

Hope this helps till Jaunty comes out... ;)

---

### Post by Gina on 2008-12-02
Interesting :)  I've thought about buying a netbook and the Acer looks the best value ATM here.  I don't "need" one - I already have a perfectly good laptop plus 3 desktops of various vintage.  But it would be nice to play with and, of course, being small and light, very easy to carry about.

---

### Post by aysiu on 2008-12-02
> **scaine said:**
> 
So, sure, not perfect, but a two-step fix for a perfect Ubuntu experience is actually pretty amazing considering Intrepid never really intended to focus on providing support for the EEE specifically. If it's only a two-step fix, why not just incorporate that into Ubuntu? Why make the user do it?

---

### Post by Gina on 2008-12-02
+1 - These little computers look like taking off.  Plus they are an ideal platform for Ubuntu.

---

### Post by plun on 2008-12-02
Just read a good article/howto from Tombuntu which maybe gives more light to this...

> The laptop is surprisingly unfriendly to Ubuntu despite being preloaded with Linux. Ubuntu 8.10 has delivered some improvements for Eee PC laptops, but it still doesn&#8217;t work perfectly out of the box.

[http://tombuntu.com/index.php/2008/11/17/installing-ubuntu-810-on-the-eee-pc-901/](http://tombuntu.com/index.php/2008/11/17/installing-ubuntu-810-on-the-eee-pc-901/)


.

---

### Post by silkstone on 2008-12-02
> **Gina said:**
> +1 - These little computers look like taking off.  Plus they are an ideal platform for Ubuntu.

Agreed!

Xandros is a bad advert for Linux. Ubuntu is a good advert. If the eee PC and Aspire One had come with a fully working version of Ubuntu, we'd have had many converts instead of people asking how to install XP on them.

It doesn't take much to get Ubuntu working on one of these netbooks (and I'm typing this on a 901 to prove it!) so please incorporate full support into Jaunty.

And, as I suggested earlier, talk to the people who do Ubuntu-eee, Array and Elmurato and it could save a lot of work.

---

### Post by ronacc on 2008-12-02
> **aysiu said:**
> If it's only a two-step fix, why not just incorporate that into Ubuntu? Why make the user do it?

thats what we were discussing here . Netbooks are such a natural and "easy" target for Ubuntu that it would be a shame to turn our backs on them .Rightnow there are a limited number of CPU's and GPU's to support so there should be pleanty of things that would not be needed in a special "bookbuntu" edition and could be left out to make room for any customisations on the cd. Ubuntu is I believe already being offered as default on atleast one netbook why not make it easy for the manufactuers and help them out with a special edition that would be easy for them to include and as a side effect also help those of us who have already "taken the plunge" ?

---

### Post by aysiu on 2008-12-02
I don't even see why it needs to be a special edition. How difficult would it be for the regular Ubuntu developers to have Ubuntu detect if you're using a netbook and then make the appropriate adjustments for whichever one you're using?

---

### Post by ronacc on 2008-12-02
I was thinking more of available space on the cd since that is always a consideration when we ask for anything to be included and there might be some apps that would make more sense for "default" on a netbook than what is in the "normal" ubuntu .. But if we can manage the space yes including netbooks in the main cd would be great .

---

### Post by autocrosser on 2008-12-02
As far as the RT2860 wireless driver--I have heard that it will make the .28 kernel tree---so we should see it sooner than later--I'm following it due to a Ralink 2860 wireless card in my system.

---

### Post by SushiR on 2008-12-03
Even with kernel from array.org there's still a lot not working properly - depending on what Eee model you are using. snd-hda-intel is one thing (issues with the mic), the elantech touchpad needs better support, fsb clocking doesn't work when upgrading RAM to 2 GB (have a look here: [http://forum.eeeuser.com/viewtopic.php?id=49242](http://forum.eeeuser.com/viewtopic.php?id=49242)), there are issues with hotkeys, ACPI (eeepc_laptop) and so on.

Since netbooks are becoming popular, I think proper support should be a main goal in Jaunty. It's not about adjustments of the look (smaller fonts, compact gtk-themes, Netbook Remix Interface, whatsoever), but about how the hardware is addressed.

I recommend to regularly have a look at [http://forum.eeeuser.com](http://forum.eeeuser.com), especially the *buntu sub-section [http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)

---

### Post by chris062689 on 2008-12-03
> **sloggerkhan said:**
> Don't be so damned eee-centric. What is needed is not just eee support, but a general distro that is specifically targeted towards netbooks

Why the HECK should we have a completely separate distro, when there's Ubuntu?
I don't know exactly how I can move forward with my goal...
Should I try asking the mailing list for 9.04 for help?
I assume it would be beneficial if we can get in contact with array and the makes of Ubuntu Eee.
This fix would probably take a day, at most, for someone who knows what their doing.

---

### Post by silkstone on 2008-12-03
Chris - it would certainly be worth making contact with Adamm (Array) and Elmurato (ACPI scripts) and the Ubuntu-eee people. As I mentioned earlier, there's a lot going on now - based on Intrepid - with the objective of making Ubuntu compatible with a wide range of netbooks (not just eee PC). New scripts and trial kernels are being released regularly, and the feedback is encouraging.

See [http://forum.eeeuser.com/](http://forum.eeeuser.com/) and look at the Ubuntu/Kubuntu/Xubuntu section.

---

### Post by Gina on 2008-12-03
Sounds good :)  I'll be watching with interest :)

---

### Post by SushiR on 2008-12-04
> **silkstone said:**
> Chris - it would certainly be worth making contact with Adamm (Array) and Elmurato (ACPI scripts) (...)
Maybe you can make contact with marx, too. He made a wonderful tool and is having a closer look at how Super Hybrid Engine (the tool from Asus to set performance modes) works. Have a look at the link I've posted above and 
[http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/)

---

### Post by Gourgi on 2008-12-04
+1 for the whole topic!

i'm writing this now from a EEE 1000H using *bliah* windows...
At my EEE lots of stuff didn't work in intrepid ,wireless and hotkeys to name some.
Problems partially solved using array.org kernel as well as the config scripts. 
things that don't work now : bluetooth on-off key doesn't work, enable-disable wireless leads to a complete freeze (i suspecting this is a wifi driver bug) and when wifi works , Network Manager can't get automatically the WPA2 Enterprise EPAP certificates from the university's wireless server as windows do, so i can't connect to wifi using ubuntu. i 'm stuck with winblowzzz for now :(

I know i should fill bugs, i've found them  already (except the NM bug)!

I hope thing change soon but for now i'm counting on the community cause "official" ubuntu dissappointed me so far ...

---

### Post by scaine on 2008-12-04
> **Gourgi said:**
> 
and when wifi works , Network Manager can't get automatically the WPA2 Enterprise EPAP certificates from the university's wireless server as windows do

Shame that there's such a disparity between the 701 and 901.  I don't even have a bluetooth toggle button (didn't ship the 701 with BT).

Strange about WIFI - if you install the backport module like I did, you should certainly have access to WPA2/Peap networks - I know cos that's what we use at my company and my little 701 has no issues.


[quote=aysiu]If it's only a two-step fix, why not just incorporate that into Ubuntu? Why make the user do it?[/quote]I'm not disagreeing with you there, for sure.  I think given Gourgi's experience, however, that I might have been lucky with a two-step fix for my 701 (and one-step fix for the Acer Aspire One).  I suspect that adding support for such devices automatically is a little more difficult that *knowing* how to add support for you own specific device.

---

### Post by chris062689 on 2008-12-04
All I'm saying is these little discrepancies with each of the Eee models not having something working out of the box is a bad move if this does not get fixed.  Imagine the market were loosing.

Your average user isn't going to know that they need another kernel to get the netbook / Eee working correctly, they'll just say it doesn't work, dump it, and move onto something else.

---

### Post by MaX on 2008-12-05
> **SushiR said:**
> Even with kernel from array.org there's still a lot not working properly - depending on what Eee model you are using. snd-hda-intel is one thing (issues with the mic), the elantech touchpad needs better support, fsb clocking doesn't work when upgrading RAM to 2 GB (have a look here: [http://forum.eeeuser.com/viewtopic.php?id=49242](http://forum.eeeuser.com/viewtopic.php?id=49242)), there are issues with hotkeys, ACPI (eeepc_laptop) and so on.

Basic support for the Asus supplied model will be enough for starters, if you mod your Asus you can't expect stuff to work.

---

### Post by SushiR on 2008-12-05
> **MaX said:**
> Basic support for the Asus supplied model will be enough for starters, if you mod your Asus you can't expect stuff to work.

In fact, upgrading the RAM is a very common mod. A lot of Eee owners do that. They build in bigger ssd or faster/additional hard drives, they even build in touch screens. That's what these netbooks are made for. They were just screaming after some modding...

What do you think why Eee users install Ubuntu? Ubuntu is well known for excellent hardware support, that's why. They are expecting their little beauties (modded or not) to run well with Ubuntu. They want the built-in cam, the mic to be working with skype, they want wifi (which is working well for me) and lan, they want the same features windows users get with the touchpad, they want more time when running on battery. They want to suspend/hibernate and resume.

With kernel from array.org all this is more or less working (as said, depending on model), but a lot needs to be done to support all Eee models (apart from EeeBox and EeeTop) and all hardware to be working correctly. Since netbooks like the Eee (and others with similar hardware) have become popular, it may be self-evident that Ubuntu supports it with an upcoming release.

---

### Post by chris062689 on 2008-12-05
OK, so how can we move forward in getting Eee's supported in Jaunty?  Launchpad?  Wiki?  Ubuntu-Devel?
I need some guidance... ):P

---

### Post by plun on 2008-12-05
> **chris062689 said:**
> OK, so how can we move forward in getting Eee's supported in Jaunty?  Launchpad?  Wiki?  Ubuntu-Devel?
I need some guidance... ):P

Maybe to start with a IRC chat ?

[https://wiki.ubuntu.com/KernelTeam/GettingInvolved](https://wiki.ubuntu.com/KernelTeam/GettingInvolved)

IRC >  #ubuntu-kernel

UDS is next week so maybe its difficult just now.

I don't see any meaning with a brainstorm....its better to discuss it directly with the kernel team.

---

### Post by olskar on 2008-12-06
> **plun said:**
> 
i don't see any meaning with a brainstorm....its better to discuss it directly with the kernel team.

+1

---

### Post by plun on 2008-12-06
> **olskar said:**
> +1

Well... OP for this thread really wants something and also got tons with good arguments from all users in this thread.

After a discussion with a kernel developer its probably much easier to go on with for example a blueprint (or a brainstorm)

If a developer also is involved in this blueprint, it for sure will be a success,   just my opinion...;)

---

### Post by plun on 2008-12-06
Followup.....  **"The Challenge"**;)

This table needs to be filled with more info

[http://event.asus.com/eeepc/comparison/eeepc_comparison.htm](http://event.asus.com/eeepc/comparison/eeepc_comparison.htm)

For example exact wireless circuit and so on....


EDIT ods attached

---

### Post by MaX on 2008-12-06
> **SushiR said:**
> In fact, upgrading the RAM is a very common mod. A lot of Eee owners do that. They build in bigger ssd or faster/additional hard drives, they even build in touch screens. That's what these netbooks are made for. They were just screaming after some modding...

What do you think why Eee users install Ubuntu? Ubuntu is well known for excellent hardware support, that's why. They are expecting their little beauties (modded or not) to run well with Ubuntu. They want the built-in cam, the mic to be working with skype, they want wifi (which is working well for me) and lan, they want the same features windows users get with the touchpad, they want more time when running on battery. They want to suspend/hibernate and resume.

With kernel from array.org all this is more or less working (as said, depending on model), but a lot needs to be done to support all Eee models (apart from EeeBox and EeeTop) and all hardware to be working correctly. Since netbooks like the Eee (and others with similar hardware) have become popular, it may be self-evident that Ubuntu supports it with an upcoming release.


Eh, well I know ALOT of people who bought the EEE 701 and the EEE 900 and none of them know how to even change their OS, that's why we need basic support out of the box.
I'm not saying we shouldn't support touch-screens etc. but basic support is most needed. If you can mod in a touch-screen you can fix Ubuntu to support it too.

---

### Post by chris062689 on 2008-12-06
Shall we file some kind of launchpad blueprint for Jaunty?

---

### Post by plun on 2008-12-06
> **chris062689 said:**
> Shall we file some kind of launchpad blueprint for Jaunty?

Yes.... but first "the ODS" must be filled which I attached
and also a discussion with a kernel developer how he/she sees 
this challenge.

No meaning to start a blueprint without all "cold facts" about this challenge.  

The eeepc ODS table is something for the community to fill with facts...;)

---

### Post by ronacc on 2008-12-06
@ plun info for the ODS the wireless chip in the eee 4G is an atheros AR5007EG  . who is going to keep the "master copy" of the ODS ?

---

### Post by plun on 2008-12-06
> **ronacc said:**
> @ plun info for the ODS the wireless chip in the eee 4G is an atheros AR5007EG  . who is going to keep the "master copy" of the ODS ?

This thread can hold it but maybe the OP can be the one which taking care of the "master"   ?

There are also maybe more software specific issues to look at... ????

The situation in Sweden was that ASUS was going to quit Linux and only deliver EeePc's with XP  :frown:.... after a lot of protests they changed it. (but Xandros is terrible,IMHO)   ;)

---

### Post by ronacc on 2008-12-06
yes  xandros as installed on the eee is pretty sad but then we are looking at it from the standpoint of long time linux users and I belive Asus's original target was total newbes . Atleast for awhile yet I left xandros on the ssd and boot linux (several flavors) from the sd card reader , I prefer sd cards to sticks because they dont stick out the side when traveling and the main beauty of the EEE is extreme portability . At the risk of seeming disloyal to Ubuntu I find Puppy linux a better"fit" for the EEE than any of the "Full featured" distros I have tried , very small,fast and will run completley in ram if you want.

---

### Post by Merk42 on 2008-12-06
> **ronacc said:**
> ...I left xandros on the ssd and boot linux (several flavors) from the sd card reader...

How is that done?
We got my father an EEEPC for Christmas.  He's a complete newbie (and isn't very tech savvy in general) I'm debating putting Ubuntu-EEE on it, since I'm at least familiar with that.  How would I go about putting Ubuntu-EEE on the SD card and booting from it?

---

### Post by ronacc on 2008-12-06
for ubuntu-eee see here   [http://www.ubuntu-eee.com/index.php](http://www.ubuntu-eee.com/index.php)  
There are pretty good docs on how to install it .
What I did was use the unetbootin they provide there to extract and put the ISO on a usbstick first then installed to the SD card from there .
If you have a usb cd/dvd drive you can boot and install from that . 
just when the partioner comes up tell it to use the sd card not the ssd and also to install grub to the sd card . then when you power on the EEE 
and press esc it will give you a choice to boot the ssd or the sd card . read the docs and check the wiki and faqs there are a couple of tweeks that may be needed to get it to boot .

---

### Post by scaine on 2008-12-08
But (I might be wrong here) watch out that you can't suspend when you run from an SD card, since one of the first things that happens during a suspend is a dismount of the SD card.

That may only apply to when you only have /home on the SD card though.  Perhaps ronacc can clarify.

---

### Post by ronacc on 2008-12-08
I can't help there I've never tried it , I never use suspend or hibernate on any of my machines always full shutdown .

---

### Post by jdorwart on 2008-12-30
not sure about the suspend thing but you can save a step if you have an SDI reader on your desktop (or your printer).  Insert your SD card.  When running Netbootin select show all drives to show the SD and then put the iSO directly on it.  I installed Ubuntu eee on a 4GB class 4 and it  boots and runs great from the SD.  The only problem I have is no WIFI and I am hoping Easy Peezy fixes that in two days.

jeff

---

### Post by ronacc on 2008-12-30
wireless works fine on my ubuntu eee install but if I remember correctly the wireless fn key doesn't so wireless has to have been turned on in xandros before booting into ubuntu eee ( may be worng about that I have never turned my wireless off:)

---

### Post by chris062689 on 2008-12-31
> **ronacc said:**
> wireless works fine on my ubuntu eee install but if I remember correctly the wireless fn key doesn't so wireless has to have been turned on in xandros before booting into ubuntu eee ( may be worng about that I have never turned my wireless off:)

That series of words made no sense to me.
Has there been any progress on Eee support in the newest kernel?

---

### Post by scaine on 2008-12-31
> **chris062689 said:**
> That series of words made no sense to me.
Has there been any progress on Eee support in the newest kernel?

Strange - sounded alright to me, despite the total omission of punctuation!

Got the latest kernel on my EEE - no change that I can tell.  You still need linux-modules-backports to get wireless working, and I still don't have any special keys working.  It's an absolutely stock install though - no modifications except what's already in the standard repos.  I run a stock 701.

Think I'll be ditching it towards the end of January for a Samsung NC10 though.  The wee screen is killing me.  And the wee keyboard is a hassle too.

---

### Post by Old_Grey_Wolf on 2008-12-31
Maybe Canonical should have a teaming agreement with Eeebuntu [http://www.eeebuntu.org/index.php?page=faq](http://www.eeebuntu.org/index.php?page=faq) like they appear to have with WUBI.

---

