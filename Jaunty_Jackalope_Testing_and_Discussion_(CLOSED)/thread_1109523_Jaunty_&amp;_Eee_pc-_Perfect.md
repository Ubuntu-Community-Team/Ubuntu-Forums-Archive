---
title: "Jaunty &amp; Eee pc- Perfect"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lancest on 2009-03-28
Wow nice kernel. Jaunty beta works out of the box- including wireless. Pretty stable. No special configuration required except font size. Nice experience Gnome 2.26. Eee pc 900A

---

### Post by Chemical Imbalance on 2009-03-28
Same exact machine and results here.

Do you also have the 4gb model?

---

### Post by lancest on 2009-03-28
Yes I have the 4G model. Got it extremely cheap recently. I put 2G Ram and have no swap partition. Everything installed on SSD. Jaunty kernel boots exremely fast (but getting past bios is a little slow) Any comments?

---

### Post by Chemical Imbalance on 2009-03-28
Same here, 2gb ram, no swap.

I personally change relatime to noatime in /etc/fstab though to save disk life.

I also mount /tmp to ramdisk

---

### Post by RookieUbuntuUser58 on 2009-03-28
Seriously this new Ubuntu version seems perfect for netbooks. Its running flawlessly on my MSI Wind. Wasn't as easy to setup as your EEE PC though (had to install drivers). Boot up speed is the key with this kernel, 22 secs with Jaunty compared to 47 secs for Intrepid.

---

### Post by wolfen69 on 2009-03-29
i don't have an eeepc anymore, but it's good to see that people are getting on with it.

---

### Post by lancest on 2009-03-29
> **Chemical Imbalance said:**
> 

I also mount /tmp to ramdisk
Can you explain how to do this part?
Also- are you using Ext 4 like myself?

---

### Post by Chemical Imbalance on 2009-03-29
> **lancest said:**
> Can you explain how to do this part?
Also- are you using Ext 4 like myself?

yes, i'm also using ext4

to mount /tmp to ramdisk:

```
gksudo gedit /etc/fstab
```

then add this to the bottom of your fstab file, save it, then reboot.

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

This keeps your /tmp file in RAM, which saves on disk writes and it is wiped clean on reboot.

It would also help to change all instances of relatime to noatime in your fstab file, which again saves disk life.

---

### Post by lancest on 2009-03-29
Ok will do thanks. Is temperature any issue with these devices? I'm noticing 56 degrees or higher sometimes. (I can't remember but I may have read somewhere that with an SSD machine it didn't matter)

---

### Post by Chemical Imbalance on 2009-03-29
For laptops and netbooks, 56 C is pretty much normal under average usage (firefox + music player, etc...)

---

### Post by chestnut1969 on 2009-03-30
Running 9.04 Beta on my eeepc 1000h (2Gb RAM), using Ext4. All good so far, works a treat.

It has now replaced Windows 7 Beta on my eee which running ok until I added antivirus etc, which bogged it down somewhat.

---

### Post by dirtylobster on 2009-03-30
> **chestnut1969 said:**
> Running 9.04 Beta on my eeepc 1000h (2Gb RAM), using Ext4. All good so far, works a treat.

Me too although I have /home as ext3 (to play it safe).

---

### Post by olskar on 2009-03-30
I feel that the mouse feels different on my EEE PC with Jaunty compared to Hardy and Intrepid, anyone else noticed that?

---

### Post by Rhubarb on 2009-03-30
Jaunty runs lovely on my eeepc S101 with ext4 and 2GB of RAM.
I haven't tweaked it very much yet.
I intend to use tmpfs more, and i might disable logging too - or mount it in a RAM disk like tmpfs.

I'm tempted to try out Linux kernel 2.6.29 which has support for ext4 with no journalling.

So far I'm really really really happy with Jaunty :D

---

### Post by bay.b. on 2009-03-30
has anyone tried the MID edition on their ASUS?
I can't get the Keyboard to work with that

---

### Post by Gourgi on 2009-03-30
> **chestnut1969 said:**
> Running 9.04 Beta on my eeepc 1000h (2Gb RAM), using Ext4. All good so far, works a treat.
do the extra 4 buttons and the Fn buttons work as they should ??
or you have extra programs to manage them?

also what about the touchpad feel?
i tried jaunty in liveusb and the touchpad had an awful feel

suspend - hibernation work correct ??

---

### Post by mdurham on 2009-03-30
eeeBox B202 everything works. Great!

---

### Post by dirtylobster on 2009-03-30
The questions weren't directly addressed to me but I have the same setup so:

> **Gourgi said:**
> do the extra 4 buttons and the Fn buttons work as they should ??
or you have extra programs to manage them?

I haven't tried them. What are they supposed to do?

Oh, just pressed the [X] button and it shut the screen down (back up when I pressed it again).

> also what about the touchpad feel?
i tried jaunty in liveusb and the touchpad had an awful feel

Feels great imo.

> suspend - hibernation work correct ??

Yes, no problems whatsoever. Haven't tried hibernation more than once though but I use suspend a lot every day.

---

### Post by dirtylobster on 2009-03-30
> **dirtylobster said:**
> Oh, just pressed the [X] button and it shut the screen down (back up when I pressed it again).

Heh it's the Lock Screen function. The other buttons don't seem to do anything.

---

### Post by olskar on 2009-03-30
> **Gourgi said:**
> 
also what about the touchpad feel?
i tried jaunty in liveusb and the touchpad had an awful feel


I can agree with that :(

---

### Post by ronacc on 2009-03-30
on my eee 701 the touchpad feel problem only affecte the netbook-launcher screen , on all other screens it seems normal , there are several bugs on this already .

---

### Post by Fenris_rising on 2009-03-30
Downloading it now to try on my 904HD. Fingers crossed here :)

Installed on an ext4 partition 40 second boot up which is only
slightly faster than 8.04. The trackpad is defo a bit slow and
skippy. Moves smoothly over an open app though, at least thus far.

regards

Fenris

---

### Post by Bufke on 2009-03-30
I tried the lpia version on my eee 900A.  Everything worked except wifi.  I've tried both free and proprietary drivers.  Looks like I'll be sticking with ndiswrapper again.  Using this wifi card
Atheros Communications Inc. AR242x 802.11abg

---

### Post by Chemical Imbalance on 2009-03-30
> **Bufke said:**
> I tried the lpia version on my eee 900A.  Everything worked except wifi.  I've tried both free and proprietary drivers.  Looks like I'll be sticking with ndiswrapper again.  Using this wifi card
Atheros Communications Inc. AR242x 802.11abg

Jaunty beta works perfectly with this wireless card, I have the same eeepc and wireless card.  Works great.  Are you referring to the MID edition?

---

### Post by Fenris_rising on 2009-03-30
Whoops! I turned of the netbook look to set it up as a normal desktop.....
Currently hoping I have picked the right bits in synaptic :D Incidently the mouse pointer now moves smoothly around so there must be something going on with the netbook look overlay?

regards

Fenris

PS sorted it. The window picker bar was on by default and I couldn't see it so right click to bring up the 'add to' menu wouldn't work :D

---

### Post by olskar on 2009-03-30
> **Fenris_rising said:**
> Whoops! I turned of the netbook look to set it up as a normal desktop.....
Currently hoping I have picked the right bits in synaptic :D Incidently the mouse pointer now moves smoothly around so there must be something going on with the netbook look overlay?

regards

Fenris

Hm, I dont use the netbooklook overlay but still gets mouseproblems..

---

### Post by Chemical Imbalance on 2009-03-30
I agree.  Intrepid's touchpad acceleration was better than Jaunty's.

It just seems less responsive.  Some tweaking in the mouse settings has got it back up to par for me though.

Here is a screen of my mouse settings (I'm using a 900A):

[ATTACH]108084[/ATTACH]

It still doesn't feel right to me though.  This  is the best setting I tried to my liking.

---

### Post by olskar on 2009-03-30
Anyone knows if it is a bug for the mouseproblem?

---

### Post by Chemical Imbalance on 2009-03-30
> **olskar said:**
> Anyone knows if it is a bug for the mouseproblem?

I haven't looked, but maybe one of us can file one on launchpad?

---

### Post by ELWisty on 2009-03-30
Hi,

Anyone able to comment on Jaunty vs. Eeebuntu (standard) on 4G?

---

### Post by Pat L.I. on 2009-03-30
Im running 9.04 beta on my EEEPC 900 and it runs great. It is noticably snappier with ext4 and did not require any battling to get everything running.

the the function + volume and brightness keys work properly.

However the function + Wireless disable/enable does not work at all. There are a few scripts to fix this around on eeeuser.com but I am not currently using any of them.

---

### Post by andrewabc on 2009-03-30
Anyone have experience on eee box?
Thinking of getting one in the future when price drops to replace an old pentium4 computer (only needs to run one or two programs at once, mostly firefox). eee box uses 20 watts, whereas my old pentium4 probably uses 200 watts. I already have decent lcd monitor, so I only need tower.

---

### Post by IanW on 2009-03-30
I found I needed "linux-backports-modules-jaunty" to get my new 1000HE to reconnect after hibernation, otherwise 9.04 is perfect.

---

### Post by Bufke on 2009-03-30
> **Chemical Imbalance said:**
> Jaunty beta works perfectly with this wireless card, I have the same eeepc and wireless card.  Works great.  Are you referring to the MID edition?

Yes I am using the MID edition.  I have the ubuntu-standard and ubuntu-desktop packages installed to make it just like the normal ubuntu, but using lpia.

---

### Post by Maupertus on 2009-03-30
What image is everybody using.
I have downloaded both the i386 and the MID version, but I haven't read enough documentation to make my mind up about the support MID (and LPIA) gives my Eee 904HA.

Would my atompowered Eee profit from the Jaunty MID img, or should I just install the 386? How about WiFi and shortcuts etc.?

---

### Post by Chemical Imbalance on 2009-03-30
> **Maupertus said:**
> What image is everybody using.
I have downloaded both the i386 and the MID version, but I haven't read enough documentation to make my mind up about the support MID (and LPIA) gives my Eee 904HA.

Would my atompowered Eee profit from the Jaunty MID img, or should I just install the 386? How about WiFi and shortcuts etc.?

I use the vanilla i386 version, but apparently some people are having problems with the lpia.

---

### Post by sgosnell on 2009-03-30
I can't tell any difference in my touchpad between 8.10 and 9.04.  It seems identical to me.  The netbook remix desktop is a problem, because by default everything is set for a single click to activate, and thus every icon grabs the focus when the cursor moves onto it.  The result is a slow, jerky cursor which is unusable for me.  The UNR desktop is attractive, but I couldn't stand the cursor problem long enough to look for a solution.  I may check back on it later.  The standard Gnome desktop works fine for me, though.  The 2.6.29 kernel is even better, and everything is more stable on my 900.  It won't be in Jaunty, but it is available.

---

### Post by Bufke on 2009-03-30
I've tried the i386 version and wifi worked fine.  The MID (lpia) version's wifi does not work without ndiswrapper. For those deciding which version, I haven't had any other problems with MID, other than the extra step of uninstalling the hildon based MID version and having to then install ubuntu-desktop.  I don't notice any huge difference in speed with lpia.

---

### Post by bay.b. on 2009-03-31
Has anyone experienced a problem installing the MID image on a 701 4G?
My KB and Touchpad are not working, but I'd really like to try the (Hildon?) desktop in combination with a 3rd party touchscreen

Could anyone point me to how I can get this working?

---

### Post by FredWst on 2009-03-31
Hello,

I've installed on eeebox B202, everything works fine. :)


Fred

---

### Post by Maupertus on 2009-04-01
Mmm, when trying to boot the LPIA from stick, I get a busybox notification. Is there anything that could cause this?

EDIT: Retried with the NBR-iso but still get the same problem. After the Ubuntu-loading screen, I get the message: Loading please wait, immediately followed by a busybox notification.

---

### Post by Bufke on 2009-04-01
> Mmm, when trying to boot the LPIA from stick, I get a busybox notification. Is there anything that could cause this?

EDIT: Retried with the NBR-iso but still get the same problem. After the Ubuntu-loading screen, I get the message: Loading please wait, immediately followed by a busybox notification.

What model eee are you using?  Tried the stock i386 iso?  Safe graphics mode maybe.

---

### Post by anjilslaire on 2009-04-01
I've read that the EEE is similar to the Acer Aspire One. Has anyone tried Jaunty on the Acer yet? I'm running a Mini 9 myself (latest Jaunty Kubuntu beta seems to work great, btw) but I also support a family member's Aspire One and improved performance on the AAO in Jaunty would be great.

Thanks

---

### Post by bobnutfield on 2009-04-01
> **anjilslaire said:**
> I've read that the EEE is similar to the Acer Aspire One. Has anyone tried Jaunty on the Acer yet? I'm running a Mini 9 myself (latest Jaunty Kubuntu beta seems to work great, btw) but I also support a family member's Aspire One and improved performance on the AAO in Jaunty would be great.

Thanks

It is working just peachy on my AAO!  See here:

[http://ubuntuforums.org/showthread.php?t=1105218&highlight=Jaunty+Acer+Aspire]("http://ubuntuforums.org/showthread.php?t=1105218&highlight=Jaunty+Acer+Aspire")

---

### Post by Trespasser on 2009-04-01
Jaunty works great on this Sony VGN-S360 that my son gave me (bought himself an Apple notebook). Works better on this than on my Desktop...though I think this release is the best for at least the past two or three. Very nice.

Later...

---

### Post by Maupertus on 2009-04-01
@Bufke: It's a EEE 904HA, I've now successfully installed a regular i386 image, and will upgrade to NBR later.

Strange though that there's so much problems with the .img files to usb, while there's absolutely no trouble with the iso's.

Will report back with user-experiences :)

---

### Post by DivingWind on 2009-04-02
I have eeepc 901,yesterday installed jaunty 9.04 beta (i386 iso). Wireless works,  bluetooth works, recognizes all devces very well, compiz runs super well with extra effects no slowdown at all, hibernation works.
Battery life isnt that good compared with XP, but i gues you have to pay the price for better performance. Atom really execls with Jaunty. (battery life for me is ~ 5 hours)

---

### Post by Carl H on 2009-04-02
What size is the installed system? 

I want to put Jaunty on my Eee 2G Surf, but I suspect that I won't have enough space to do a standard install.

---

### Post by bennachie on 2009-04-02
A standard install leaves about 1.3G free on my eePC 4G, so I fear that you are correct. I have to say, though, that you get a lot of functionality squeezed into that 2.7G - Fedora 10 chewed up 3.8G for the same end. So far, all the hardware works just fine.

The installation process is simple enough, but I do wish that the Ubuntu developers could take a leaf from their Fedora counterparts and arrange for the installer to detect the screen resolution, and adjust the various windows accordingly. It would also be useful if the Xandros and Fedora "ALT+left-click" window drag mechanism could be incorporated in the final system. Lacking that convenient system, the only workaround while setting preferences in Ubuntu seems to be temporarily to select tiny font sizes to bring the vital elements of the relevant windows into view - even with that adjustment, Evolution is almost impossible to get right, and I have simply resorted to downloading Thunderbird (which uses much less real estate for its preference windows, and works at least as well for mail and news).

---

### Post by ronacc on 2009-04-02
@ Carl H   stick it on an SD card or a usb stick.

---

### Post by Carl H on 2009-04-02
> **bennachie said:**
> A standard install leaves about 1.3G free on my eePC 4G, so I fear that you are correct. I have to say, though, that you get a lot of functionality squeezed into that 2.7G 

I thought that 2Gb was probably not enough. I don't really need most of the functionality, just an email client, web browser, a few retro games, and maybe Emacs. If I need anything more, I've got plenty of other computers to go at. ;)

> **ronacc said:**
> @ Carl H   stick it on an SD card or a usb stick.

That's Plan B. :cool:

Ta for the replies.

---

### Post by IanW on 2009-04-02
> **bennachie said:**
> 
The installation process is simple enough, but I do wish that the Ubuntu developers could take a leaf from their Fedora counterparts and arrange for the installer to detect the screen resolution, and adjust the various windows accordingly. It would also be useful if the Xandros and Fedora "ALT+left-click" window drag mechanism could be incorporated in the final system. Lacking that convenient system, the only workaround while setting preferences in Ubuntu seems to be temporarily to select tiny font sizes to bring the vital elements of the relevant windows into view - even with that adjustment, Evolution is almost impossible to get right, and I have simply resorted to downloading Thunderbird (which uses much less real estate for its preference windows, and works at least as well for mail and news).

A better workaround (IMO) for using the installer in LiveCD:-

1: Select System/Preferences/Appearance.
2: Open last tab (Desktop Effects).
3: Select "None"
4: Close Appearance.

You can now use the "Alt+Left Click" method you describe above.

---

### Post by DivingWind on 2009-04-02
It seems that wifi (fn+F2) hot keys together with fn+F6, fn+F5 on eeepc901 are not functioning, everything else functions properly.
Anyone having similar issues?

---

### Post by olskar on 2009-04-02
> **DivingWind said:**
> It seems that wifi (fn+F2) hot keys together with fn+F6, fn+F5 on eeepc901 are not functioning, everything else functions properly.
Anyone having similar issues?

Yep, would be nice to get that working but will propably not happen before at least Karmic. Am I wrong, or does something in kernel need to be changed for this to start working?

---

### Post by DivingWind on 2009-04-02
Maybe it's just Jaunty beta. Hope final release will fix these issues... :?

---

### Post by olskar on 2009-04-02
> **DivingWind said:**
> Maybe it's just Jaunty beta. Hope final release will fix these issues... :?

If you like, you can test a testkernel that should make it work:
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170/comments/57](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170/comments/57)


If it works for you please make a comment to the bugreport and tell them that! :)

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170)

Looks like there is a chance we will have this in Jaunty after all!

Anyone else with the same hardware should of course test it too if they want!

---

### Post by bennachie on 2009-04-02
> **IanW said:**
> A better workaround (IMO) for using the installer in LiveCD:-

1: Select System/Preferences/Appearance.
2: Open last tab (Desktop Effects).
3: Select "None"
4: Close Appearance.

You can now use the "Alt+Left Click" method you describe above.


Thanks for that helpful comment, it's one of those solutions that becomes obvious once somebody has pointed it out (and is certainly tidier than my suggestion of messing around with font sizes). Neither workaround solves the untidiness of the installation process on older netbooks, of course.

Now, if the installer could detect the screen resolution properly, adjust the dialogue boxes to match, and set Desktop Effects to "none" by default when the resolution is less than 800x600 we could escape having to answer the same questions several times when the final release comes out ...

In fairness, I have been hammering the Jaunty beta on my eeePC pretty hard over the last couple of days, and haven't provoked the system into biting back yet. This is going to be an excellent release.

---

### Post by Chemical Imbalance on 2009-04-02
Has anyone else noticed that if your wireless connection gets disconnected that you have to reboot to get the interface up again?  Also unchecking "enable wireless" in nm-applet then enabling it again has the same effect: no wireless until reboot.  "ifup --all" doesn't work.

Anybody else have this issue?

I have a 900A (with a slow as death SSD)

---

### Post by bennachie on 2009-04-02
> **Chemical Imbalance said:**
> Has anyone else noticed that if your wireless connection gets disconnected that you have to reboot to get the interface up again?  Also unchecking "enable wireless" in nm-applet then enabling it again has the same effect: no wireless until reboot.  "ifup --all" doesn't work.

Anybody else have this issue?

I have a 900A (with a slow as death SSD)

I don't have that problem with my eeePC701-4G (and the SSD doesn't seem to be particularly slow).

---

### Post by Chemical Imbalance on 2009-04-02
> **bennachie said:**
> I don't have that problem with my eeePC701-4G (and the SSD doesn't seem to be particularly slow).

I think I'm just gonna replace this ssd as it is bottlenecking my whole system.

Just out of curiosity, can anyone post their battery times?

I'm getting 2 1/2 - 3 hours on a 4cell.

---

### Post by sgosnell on 2009-04-02
2GB isn't enough for much of anything.  Get a good-sized SD card and install to that.  It's about as fast as the SSD, and it stays in the slot, out of the way.

---

### Post by bennachie on 2009-04-03
> **Chemical Imbalance said:**
> I think I'm just gonna replace this ssd as it is bottlenecking my whole system.

Just out of curiosity, can anyone post their battery times?

I'm getting 2 1/2 - 3 hours on a 4cell.

That sounds about right. I can't remember getting much more than 3 hours even when I still had that awful, crippled, but presumably eeePC-optimised Xandros system installed. 

It's a bit early to be sure, but I think that Jaunty is rather less power-hungry (and definitely takes up about 1GB less disk space) than the Fedora 10 installation that preceded it.

---

### Post by DivingWind on 2009-04-03
> I think I'm just gonna replace this ssd as it is bottlenecking my whole system.

Just out of curiosity, can anyone post their battery times?

I'm getting 2 1/2 - 3 hours on a 4cell. 

I'm getting ~5 hours on 6cell battery with wireless on because it enables itself on boot (in bios wlan is disabled) and I cant disable it when I'm in OS :oops:

---

### Post by Baggers on 2009-04-03
The touchpad issues are definately present for me on my 901.
The movement of the cursor is fine but the "middle click" is much worse than on intrepid. It appears that if you dont hit it just right it misinterprets the action as a scroll and zips up the page...Not the best advert for ubuntu when my mates hear me yelling at my laptop every 5 minutes hehe!
Anyone seen any ideas on fixing this yet?

---

### Post by Fenris_rising on 2009-04-03
Hi all

I've had 2 days of download induced jaunty death :(

Today however I re-installed and ran the updates

which have run fine barring a '139' error on several

items. But everything is running fine. The only

annoyance is having to give the nm-applet my password

at every boot. I know I have seen the answer somewhere
:D

regards

Fenris

---

### Post by Auslegung on 2009-04-04
I booted into Jaunty from my LiveCD for just a few moments on my eeePC 1000H, and immediately noticed a few things.

1. I concur with the mouse feeling odd.  After tweaking it's about 90-95% as good as it is in 8.10.  
2. Fn+F2 does not work (wifi off).  I have heard from some that it does, but most say it doesn't but Ubuntu plans to have it working by RC.  
3. Fn+F11-12 adjust the volume, but the icon on the screen does not change.
4. Basically, the Fn keys are hit-or-miss.
5. Skype gave me the ole familiar Problem with Audio and did not work
6. The Netbook Remix interface is still, to me, ugly, cluttered and unwieldy.  I think there's a way to have the UNR build with a normal GUI, I sure hope so.

I will extend this list this weekend as I play with Jaunty some more.

---

### Post by Fenris_rising on 2009-04-04
Well I am about to install Jaunty again. Not because it's gone wrong, but, because it's dual boot buddy 8.10 has continued to suffer from sound issues. IE there is no bloody sound :mad: I have just spent a couple of hours following various how to's, fixes and even resorted to verbal abuse but to no avail.

So 8.10 can get stuffed and Jaunty can have my eeepc all to itself. During this time I at least know it may well go wrong by it's very nature as a 'beta unit' but as it works where 8.10 doesn't it's at least moderately acceptable.

Thank goodness I haven't upgraded my PC's Hardy OS or there would have been a severe chance of spilling blood :D I love Linux and have been running it for 11 months now. But in the last 3 weeks I have had sudden failure of audio and video on Hardy and the aforementioned 8.10.

Anyhoo fingers crossed :)

regards

Fenris

---

### Post by Fenris_rising on 2009-04-04
Help :( I manage to install but when I run updates it starts installing then locks up. I had it running yesterday with the updates done and dusted but now It wont do bugger all with this install.

A hard restart lets me get to a low res login option which then takes me to the login screen but the 'mouse' is locked up so I can't go to options to try a 'fix' from terminal.

What can I do? I only went the whole hog because easy peasy buggered up I have tried the official ubuntu 8.10 as well but it doesn't recognize the fact that I have built in wireless.

HEEEEEEEEEEEEEELP please!

regards

Fenris

---

### Post by Maupertus on 2009-04-04
> **Auslegung said:**
> I booted into Jaunty from my LiveCD for just a few moments on my eeePC 1000H, and immediately noticed a few things.


6. The Netbook Remix interface is still, to me, ugly, cluttered and unwieldy.  I think there's a way to have the UNR build with a normal GUI, I sure hope so.

I will extend this list this weekend as I play with Jaunty some more.

I don't know for sure, but if you go for synaptic, and search for Netbook, you'll get the NBR package. Couldn't you just uninstall that package, and install the ubuntu-desktop package?

I'm now running the i386 package, and I'm undecided about the NBR, it's very dark, which is my biggest grief. At the moment, I just don't see the upside to the very dark and therefor unclear thingy on my desktop. The normal desktop is very easy to navigate.

Batterylife is pretty bad by the way, is there any advantage in moving to LPIA? Is there an iso instead of an image for LPIA? I can't seem to get the img 'burned' to the USB, iso's no problem.

---

### Post by taavikko on 2009-04-04
> **Maupertus said:**
> Is there an iso instead of an image for LPIA? I can't seem to get the img 'burned' to the USB, iso's no problem.

Use "dd" to "burn" .img
[https://wiki.ubuntu.com/UNR#From](https://wiki.ubuntu.com/UNR#From) commandline with dd

---

### Post by vegetarianshrimp on 2009-04-04
> **lancest said:**
> Wow nice kernel. Jaunty beta works out of the box- including wireless. Pretty stable. No special configuration required except font size. Nice experience Gnome 2.26. Eee pc 900A
same with dell mini 9 :)

---

### Post by jseiser on 2009-04-04
Eee PC 1000HA

everything works great accept the wireless.  It is on, I get an ip, but I can not surf on any router.  the card is a AR242 according to 
lspci | grep net

---

### Post by Fenris_rising on 2009-04-04
Hoorah!!!!! Its installed and updated with no problems not even a single error message :) :) Could this be because I elected to use the standard ext3 rather than the ext4??? Thoughts anyone? Right I'm off to thrash the hell out of it.

Incidently the pointer now moves smoothly around the NBR interface 

regards

Fenris (no longer frothing at the mouth :D )

---

### Post by bennachie on 2009-04-04
> **Fenris_rising said:**
> Hoorah!!!!! Its installed and updated with no problems not even a single error message :) :) Could this be because I elected to use the standard ext3 rather than the ext4??? Thoughts anyone? 
...
Fenris (no longer frothing at the mouth :D )

I chickened out, stuck with ext3, and have had a virtually trouble-free run with Jaunty on my eeePC 4G. Like you, I'd be interested to hear whether others have been successful with ext4 on netbooks.

---

### Post by Maupertus on 2009-04-04
Mmm, okay I have NBR tuned the way I like it by using the Human-Clearlooks theme (not the Netbook version) but after a day of full on use, I have a couple of plusses and minuses

Plus:
- Works out of the box, even WiFi and multi-touch trackpad.
- Most important Fn keys work (sound, brightness)
- Even non-netbook remix works great without resolution problems.
- New notification system works really well on small screens

Minus:
- Couldn't 'burn' lpia image to stick with unetbootin (not really install problem)
- Evolution is completely busted, at least on the calendar side of things, and a little on the gmail/imap side. I now have 3 pretty severe calendar problems which make me want to switch to thunderbird (never! I love Evo! Gimme back my working Evo!)
-Battery life is really bad, easier and better cpu-scaling would be terrific.
-Had a lot of problems with the configuration of the NTFS partition (bug report filed :) )
-Still not convinced of the need or use of NBR

---

### Post by sgosnell on 2009-04-05
I've been using ext4 on my 900 since RC5, and have had no problems at all.  Works great for me.  ISTR a glitch or two with the initial install, but nothing show-stopping.

---

### Post by bennachie on 2009-04-05
> **sgosnell said:**
> I've been using ext4 on my 900 since RC5, and have had no problems at all.  Works great for me.  ISTR a glitch or two with the initial install, but nothing show-stopping.

Thanks - I'll give ext4 a go when the final release comes out. The claimed benefits should make the effort worthwhile.

---

### Post by Auslegung on 2009-04-05
Can anyone report on the battery life, rather than just saying it's not good?  I'd like to know how long, what you're running, the brightness, etc.  

Is the Netbook Remix theme changeable, just like any other theme?

If you're using an ATOM chip and want to have lpia along with the UNR, check out this thread: <[http://ubuntuforums.org/showthread.php?t=1104061&highlight=eee+pc+jaunty&page=2]("http://ubuntuforums.org/showthread.php?t=1104061&highlight=eee+pc+jaunty&page=2")>.  I'm not sure how much success they've had, but if anyone wants to try it out and report that'd help.

---

### Post by Maupertus on 2009-04-05
> **Auslegung said:**
> Can anyone report on the battery life, rather than just saying it's not good?  I'd like to know how long, what you're running, the brightness, etc.  

Is the Netbook Remix theme changeable, just like any other theme?


1- I have a 904HA with a six-cell and I get about 3.5 hours out of it with WiFi on. On XP, I get 4.5 (almost six without WiFi).
Haven't tried it with WiFi of, and in Jaunty the brightness sometimes goes higher without my wanting it (thinking about filing a bug)

2- I think there are some changes when you change theme's, but not a lot. I was very happy with the human-clearlooks theme and a white desktop background, it helped a lot, and a grey/white top bar works beautifully with maximus (standard theme is dark/black)

---

### Post by thecityofgold2006 on 2009-04-05
Ext4 Jaunty running on an eee900 (Celeron 4+16gb) since Alpha 5 with no problems. 

Only thing that doesn't work is the F2 wireless toggle.

Booting into Openbox / LXPanel gives a bootchart time of ~13secs compared to ~21secs under Intrepid.

---

### Post by Auslegung on 2009-04-05
I booted into Jaunty on my USB and the battery life, at moderate brightness, wifi on, firefox, pidgin and rhythmbox running, was 3hrs 10mins at 95% charge.  My total charge is only 88%, so if your battery is higher quality it should be even better.  That's about what I get in Adam's Kernel 8.10, or XP, so that's not bad.  I couldn't get cable or wifi to connect, though both were on.

---

### Post by whitefort on 2009-04-05
I decided to install Jaunty on my eee 901, and I'm surprised to find that everything seems to be working fine, right out of the box.

This isn't even the netbook version, and I thought I'd have all sorts of hassle with stuff like wifi, but no - everything's fine.

I haven't tested the camera yet, but I never used it much anyway.

---

### Post by Fenris_rising on 2009-04-05
Well so far so good. Switch Desktop mode does indeed switch and I have themed up my desktop/activated compiz and all seems well in my linux world :D

I have yet to run my own comparison of battery life. Previously under easy peasy I had 3hrs20mins. 

Is there any manual CPU/Fan control available or in the offing? It would be nice if the associated silver buttons I used before were, again, the CPU/Fan manual control.

Although not a fan of the UNR desktop it does work smoothly and responds at a good pace on my 904HD. All Fn keys seem to be up to snuff as well.

When I'm feeling brave I'll try an install with the ext4 format. Would the format be the reason I had trouble with installing? I did have it installed and working on ext4 when it was dual boot.

It seems to be something called 'scrollkeeper' that failed repeatedly during the updating process when ext4 was the format. Anyone else find this?

Applications open visibly faster as well. In fact very 'snappy'.

regards

Fenris

---

### Post by jacopo.tolja on 2009-04-05
Hi to all, this is my first post... if is the wrong place please let me know.
I use intrepid on my eee 901 4+16 gb
it run fine but boot time rise consistently from 30 seconds to more than 2 minutes and i guess is time to pass to a new version. I am not a good installer it took me a week to figure it out the first time... now the question
there is any easy way to switch from intrepid to jaunty without going through the whole installation?

---

### Post by thefunnyman on 2009-04-05
Found this little how-to to enable horizontal 2-finger scrolling on my eeepc 900 16G.  I must say that it works perfectly so far.

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)

Also note, that before following this how-to a 2-finger click equated to a middle click, and a 3-finger click equated to a right-click...that has now reversed....making rather obvious changes to the xml and rebooting ( restarting hal didn't pick up changes for me ) implements the changes.

---

### Post by Maupertus on 2009-04-06
Mmm, I had absolutely no problems with multi-touch on my 904HA using Jaunty i386.

Anybody using the [eeepc-acpi package]("http://packages.ubuntu.com/hardy/eeepc-acpi-source") that's in universe?

I'm tempted (and it has a small applet for the things it supports in universe as well) but I think it was written pre-jaunty. All the things it corrects are allready working in Jaunty, except the wifi on of thing with Fn+F2. It also has something resembling the SuperHybridEngine thingie that Asus developed for WinXP wich let you under and overclock the CPU.

I'm itching to install, but I don't want to borkify, and neither do I want to install useless cr*p. (Found some info about it being an extension to the Array kernel as well)

---

### Post by xzero1 on 2009-04-08
Is a journaling file system (ext3,4) a good idea on a flash based computer? Is there any other advantage I do not see here? Though journaling can be disabled, it seems a flash based or simpler file system (ext2) might be better. I guess the real question is what is the best file system to use on a flash based computer?

---

### Post by olskar on 2009-04-08
Has anyone tested the kernel mentioned here to check if that makes the wireless hotkeys work? That would be very nice!

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170/comments/57](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/232170/comments/57)

---

### Post by zenithdave on 2009-04-08
If i could work out what to do i would :rolleyes:](*,)

I can see i need to get 3 debs but where does the patch go?

---

### Post by lancest on 2009-04-08
> **xzero1 said:**
> Is a journaling file system (ext3,4) a good idea on a flash based computer? Is there any other advantage I do not see here? Though journaling can be disabled, it seems a flash based or simpler file system (ext2) might be better. I guess the real question is what is the best file system to use on a flash based computer?
Debian [says this]("http://wiki.debian.org/DebianEeePC/HowTo/Install"):
"It is fine to use ext3 as your filesystem, which is the default. See [http://wiki.eeeuser.com/ssd_write_limit](http://wiki.eeeuser.com/ssd_write_limit) for a compelling argument that you're not going to kill your flash drive by the small percentage of extra writes that a journaling filesystem will add over the lifespan of the drive"
I've looked around- and this is a matter of opinion. Many say use ext2. I'd rather not use ext2 myself.

---

### Post by Confuseling on 2009-04-08
[http://forum.eeeuser.com/viewtopic.php?id=62003](http://forum.eeeuser.com/viewtopic.php?id=62003)

You can't say this guy hasn't thought about it, whether you agree with his conclusions or not. ;)

Personally, I think the benefits outweigh the risks - although I will probably mount a few things as tmpfs, and not use swap.


How many people have tried the LPIA kernel yet? I know it was mentioned earlier, but I'm curious as to whether the problems people were reporting have been ironed out...

---

### Post by xzero1 on 2009-04-08
> Debian [says this]("http://wiki.debian.org/DebianEeePC/HowTo/Install"):
"It is fine to use ext3 as your filesystem, which is the default. See [http://wiki.eeeuser.com/ssd_write_limit](http://wiki.eeeuser.com/ssd_write_limit) for a compelling argument that you're not going to kill your flash drive by the small percentage of extra writes that a journaling filesystem will add over the lifespan of the drive"
I've looked around- and this is a matter of opinion. Many say use ext2. I'd rather not use ext2 myself.     Thanks for your response. In doing a bit of digging, I have found an interesting  article [http://www.linuxdevices.com/articles/AT7478621147.html](http://www.linuxdevices.com/articles/AT7478621147.html), which leads me to believe Jffs2 might be the ticket. Is Jffs2 available as a file system on the Eee pc in Jaunty? It seems it is* not *available as a format option in Jaunty's partition editor. Has anyone tried it? Comments  are welcome.

**Forget Jffs2, bad idea see **[http://www.linux-mtd.infradead.org/faq/jffs2.html#L_hdd_jffs2.]("http://www.linux-mtd.infradead.org/faq/jffs2.html#L_hdd_jffs2")

---

### Post by sgosnell on 2009-04-09
Never even heard of it.  I'm using ext4 on my 900, and it's much faster than ext3.  I don't think the additional writes are a problem, and having the additional safety net is a big plus.

---

### Post by lancest on 2009-04-09
Back when the Eee pc came out I put ext2 on a friend's Eee 700*. He ended up losing the system after an inproper shutdown. No journaling.  After that I didn't trust what many say about using ext2. Maybe I missed something on that but as the previous poster said -I much prefer ext4. Faster and safer. Nothing but gain.

---

### Post by Chemical Imbalance on 2009-04-09
I agree about not using ext2 as I've had numerous data corruptions after having to hard-shutdown.  Ext4 is much faster and safer.  Leave the journaling on, its not gonna wear your ssd down because think about all those updates that you install everyday and that get written over--the journals that ext4 makes are nothing compared to what get written and overwritten by you and updates, etc...

Honestly, the benefit is much greater with ext4 to me.

---

### Post by xzero1 on 2009-04-09
Can the Eee pc be used even if its non-replaceable ssd fails for whatever reason? Couldn't we just install an os to an external sd card or usb drive and run it from there?

---

### Post by Chemical Imbalance on 2009-04-09
> **xzero1 said:**
> Can the Eee pc be used even if its non-replaceable ssd fails for whatever reason? Couldn't we just install an os to an external sd card or usb drive and run it from there?

yes, you can

btw, not all the eeepc's have soldered-on ssd's; mine has a replaceable one.

---

### Post by sgosnell on 2009-04-09
You can replace the SSD, but I've run several distros off an SD card for testing, and I can't tell a lot of difference in speed between the SSD and the SD card.  If you look around for awhile, you can find good deals on SD cards.  I got my 16GB card for ~$20, and it has worked fine for me.  With a 16GB SSD and a 16GB SD card, I have plenty of storage, and never really felt a pinch using just the SD card.

---

### Post by Macchi on 2009-04-10
I would appreciate to get hints on fixing the sound of my EEE with Jaunty 9.04 Beta. The problem has been around since 8.04 and it is neither possible to record from the built microphone nor use Skype. The RF-switch is not working.

Unfortunately those problems with the sound may prevent several users from experiencing the full potential of Ubuntu on a netbook. Netbooks are excellent as inexpensive communication stations with email, voice and video calls, etc.


But yes, I do like Jaunty! The latest Ubuntu has been further polished, having a noticeably faster boot, apparently better performance with ext4 and also a cleaner look, more suitable for a wider scope of users.

---

### Post by olskar on 2009-04-10
I recently install Jaunty daily on my EEE pc 900 and all I can say is; luckily Intrepid is still supported :) The preformance with my intelcard was waaay better in Intrepid and also I don't like the way the mouse behaves

---

### Post by sissou on 2009-04-11
Good morning (from france),
I'm running jaunty on an eee 900 since yesterday.

Everything is fast & fine but :

- Toggle wifi on/off does not work (but that seems to be a collective problem...).

- CPU scaling : the celeron M runs at its stock speed 900MHz and never slows down : does anybody had solved that mistake ?

NB : sorry for my bad english...

---

### Post by nchase on 2009-04-12
> **dirtylobster said:**
> Oh, just pressed the [X] button and it shut the screen down (back up when I pressed it again).

> **dirtylobster said:**
> Heh it's the Lock Screen function. The other buttons don't seem to do anything.


Anyone know how to disable this function for the [X] button?

---

### Post by jfernyhough on 2009-04-12
Finally took the plunge and put the Jaunty Netbook Remix on my EeePC 701. Wow. I love how upgrading Ubuntu makes old machines run /faster/.

---

### Post by PopOmatic on 2009-04-13
Anyone having problems with touchpad? 

I'm running current updates on 1000H and at the moment left click doesn't work at all. Everything else seems to behave just fine.

---

### Post by sgosnell on 2009-04-13
I had a problem with that when I had Intrepid installed, but not with Jaunty.

---

### Post by PopOmatic on 2009-04-14
> **sgosnell said:**
> I had a problem with that when I had Intrepid installed, but not with Jaunty.

New updates fixed things for me. I have been using Jaunty since Alpha5 on my eee and this was first time something critical was actually broken temporarily. Hope the final release works even better!

---

### Post by Tom Mann on 2009-04-14
Worth adding as of a few days ago, the Acer Aspire One has full hardware support (including wireless) too - they've fixed the last module causing problems with the wireless :KS

I have to alter my fonts the same way the eeePC guys have to :)

---

### Post by lenooh on 2009-04-14
Installed daily UNR on eeepc 900 (celeron 4+16GB). The 4GB is set up as / (root) partiton using ext4, and the 16GB is set up as /home partition using ext3 (to be safe). On the 16GB I have about 1GB for swap.

Boot time to gdm is excellent, to gnome it could be a little bit better. I turned off bluetooth and cups services, but I am sure there could be more to turn off. Applications start fast.

Everything seems to be working, unless the Fn+F2 wireless toggle keyshortcut. Battery life is good.

I played around with the NBR launcher for a few hours, but it worked very slowly when going with the cursor over an icon as some have already pointed out. Also the "maximus thingy" is not really working out, because there are certain windows that are not supposed and not intended to be fullscreened (most setup/preference dialogs, firefox download window, about windows, etc..), so I switched to "desktop mode", removing the bottom panel, and setting the top one to autohide. Now I have as much usable workspace as with the UNR launcher, but without the maximizing issues.

All together very happy :guitar:

---

### Post by teh603 on 2009-04-14
Funny, I just downloaded the latest build of Jaunty this morning and the wifi was still hammered, or at least it was on the LiveCD. I didn't actually install it.

Put simply, the light was on but it could't detect the wifi access point it was about eighteen inches from. The toggle didn't seem to work, either.

---

### Post by Chemical Imbalance on 2009-04-14
Here's the current desktop on my 900A eeepc 4GB ssd:
[ATTACH]109832[/ATTACH]

Its running Xubuntu Jaunty Beta

My Tweaks:

I've mounted /tmp,/var/log,and /var/tmp to tmpfs in fstab

Uninstalled some bloat included (stuff like bluetooth,telnet,screensavers,etc...)to save space on my 4GB.

Turned on xfce compositing to enable true transparency

Set ufw enable and use gufw as frontend

Set up OpenDNS

set my sudo timeout to 0 so to prompt for password at every request

Variation window decoration (saves space) + clearlooks gtk

Conky to keep eye on battery, cpu %, etc...

Installed Openoffice Impress (Presentation) & Writer, Gnome-Mplayer, wicd (as network-manager replacement--its better for me), sun-java6-plugin, adobe-flash, and a few other apps.

After all this it  takes up exactly 2.32 GBs of space! :)

xfce + netbook = :guitar:

---

### Post by HankB on 2009-04-17
> **teh603 said:**
> ... and the wifi was still hammered, or at least it was on the LiveCD. 

That is the RC? I have the same problem on my Eee PC 901. I understand that WiFi worked OK on the earlier betas.

WiFi runs to the point where it sees my access point and knows that it is using WPA2 authentication. Beyond that it seems not capable of establishing a connection.

I wondered if it would work better once installed and upgraded. I installed to an SDHC card and upgraded and still no WiFi joy.

I wonder if anyone has reported through normal channels.

-hank

---

### Post by teh603 on 2009-04-18
Ok, I installed the RC on my AAO last night. The only things that *don't* work out of the box are the sound, and the card readers. Hopefully they'll get fixed soon, because from what I've read the kernel module is actually missing, instead of borked.

It also installed onto 2 gigs this time, so there's hope for the 2g Surf users in the near future. Although a custom .iso would serve them better.

---

### Post by Stefan_K on 2009-04-21
> **Rhubarb said:**
> Jaunty runs lovely on my eeepc S101 with ext4 and 2GB of RAM.

Very nice to read! I've got an eee pc S101 some days ago, but for now I've installed Eeebuntu NBR 2.0, seemed to be the quickest way to get Ubuntu running and it worked fine. I've made some notes here: [Eeebuntu on the Asus Eee PC S101]("http://texblog.net/latex-archive/linux/eee-pc-s101-eeebuntu/").

If you would have some tweaks and further infos concerning Jaunty on the S101 I would be glad to read it.

Stefan

---

