---
title: "Ubuntu freezes"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Meuro on 2007-03-10
This is the second lot of attempts i have had at installing ubuntu.  I tried sometime last year but gave up because it was just impossible.  Nothing i did seemed to work.

But windows has been pissing me off again so i decided to have another go.  

First i tried to install the AMD64 version using the live CD.  But this failed as it would get to the tan screen and just stop.  No txt, no hdd activity, no cd activity.  Nothing worked.
So then I tried 

deleting the quiet splash, 
ide=nodma,
irqpoll pci=noacpi noapic nolapic acpi=off
break=bottom then chroot /root nano /etc/X11/xorg.conf and changing the drivers,
or all of the above together

So i tried the alternative version.  And hoorah.  A little bit more success.  Except that it froze when it got to the login screen and wouldnt budge.  No crtl+alt+f1 and all that malarky worked.  So i had to reset my pc.  Then ubuntu came up wiht error 15 or some rubbish and i had to reinstall.  This time i used the alternative 32 bit version.  And it installed and i got to the login screen.  And it froze again.  So i rebooted and it got to the login screen.  But this time it worked!! yay! It loaded and then told me i had to update so i clicked the update icon and it froze  :(

So i restarted and its frozen at the login screen again and again no commands work to break me out.  

Any ideas?

Many thanks.

---

### Post by wj32 on 2007-03-10
I think it's some kind of processor architecture problem (AMD64). But, other than that, I have no ideas.

---

### Post by Meuro on 2007-03-11
Sometimes the login screen does work, but if i use crtl+alt+f1 the sceen gets all garbled and freezes. 

Knoppix works fine and i tried to use that to edit /etc/X11/xorg.conf but the permissions wouldnt let me and i couldnt change them.

Help!

---

### Post by Kateikyoushi on 2007-03-11
Try to install from the live cd by following these instructions. [LINK]("http://www.ubuntuforums.org/showpost.php?p=2193083&postcount=3")

---

### Post by Meuro on 2007-03-11
Thanks Kateikyoushi, but I aleady tried that.  I'm having to use the alternative live CD and the break=bottom command doesn't seem to work. 
 :(

---

### Post by Kateikyoushi on 2007-03-11
I think that only works on the live (not alternate) CD.

---

### Post by Factory on 2007-03-11
For any reason would any of your hardware be bad? I've found that system freezes can sometimes be due to bad ram.

---

### Post by Meuro on 2007-03-11
It could be my hardware, but it passes memtests and the like.

I just tried booting up in recovery mode and trying:

sudo dpkg-reconfigure -phigh xserver-xorg

which i got from another post.  But that didnt work.  It came up with:

xserver-xorg postinst warning: not updating /etc/X11/X; file has been customized
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20070311101621

When I was looking through my posts from last year on my first attempt at linux, it occured to me that this is not the first time I have experienced this problem:
[http://ubuntuforums.org/showthread.php?t=135270](http://ubuntuforums.org/showthread.php?t=135270)
[http://ubuntuforums.org/showthread.php?t=138798](http://ubuntuforums.org/showthread.php?t=138798)

I really want to use ubuntu cause I reckon it totally rocks but I just seem to have no luck with it :(

---

### Post by Factory on 2007-03-11
Well, yes, quite frankly, it does rock.


Now, about your problem. 

Did you ever try just doing the regular 32 bit version? If I read correctly, you've tried the 64 bit, the alternative, and the alternative 32 bit.

I personally have had horrible luck with the 64 bit version.

---

### Post by Meuro on 2007-03-11
Ok, have just tried the 32 bit live version.  And it actually worked... for a bit.  The screen was a bit funny in that the pop-up windows didnt fit on the screen but that was ok.  I managed without it.  But during the setup process, it reset itself.  So I tried again using the tips and tricks picked up trying to make the other versions work but it just froze during the installation setup :(
I even tried editing up various bits of unneccessary fluff from the xorg.conf but it didnt work either.

Am I just going to have to concede that ubuntu and my desktop cant be friends?

---

### Post by Factory on 2007-03-11
[https://wiki.ubuntu.com/hardware](https://wiki.ubuntu.com/hardware)

Check that site out and see if anything you have is listed. If it is, you've probably found your answer. It really does sound like a hardware problem to me.

Scratch that. Try here:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Meuro on 2007-03-11
I found nothing there to suggest that it is or is not my hardware.

My hardware is:

amd64 3400, 
foxconn socket 754 mobo, 
Asus ati X850XT 256mb AGP, 
1024ram, 
samsung 80gb sata hdd
Logitech MX1000 wireless mouse
Saitek Eclipse usb keyboard

---

### Post by Kateikyoushi on 2007-03-11
> **Meuro said:**
> Thanks Kateikyoushi, but I aleady tried that.  I'm having to use the alternative live CD and the break=bottom command doesn't seem to work. 
 :(

Did you try that with the live cd as well ?

---

### Post by Meuro on 2007-03-11
I've tried every cd of ubuntu

---

### Post by Factory on 2007-03-11
I would have to take a guess at a hardware problem/compatibility issue. Not... not entire sure what else to tell you. Someone else with more experience could probably help you out better.

---

### Post by hiker13526 on 2007-03-11
Meuro: What model of foxconn motherboard are you using?

---

### Post by Meuro on 2007-03-12
I am using the K8S755A series motherboard

[http://www.foxconnchannel.com/EN-GB/product/motherboard_detail.aspx?ID=en-tt0000065](http://www.foxconnchannel.com/EN-GB/product/motherboard_detail.aspx?ID=en-tt0000065)

---

### Post by hiker13526 on 2007-03-12
I am using the NF4K8AB-RS. Got nearly the exact same problem. It freezes at a tan screen for me. Ctrl Alt F1 works BRIEFLY, if I press it real fast and type in a command it works for a few seconds, then the whole thing freezes up. You can take a look at my thread to see what hasn't worked for me :) [http://ubuntuforums.org/showthread.php?t=378664](http://ubuntuforums.org/showthread.php?t=378664)

I read on a SUSE forum that foxconn mobo's just plain aren't supported on linux yet. I'm not sure if the guy was telling the truth, or if they still aren't supported. Just didn't sound good for us foxconn users...

---

### Post by Kateikyoushi on 2007-03-12
I can belive that certain components, chipsets are not yet supported, but a whole brand...

---

### Post by Meuro on 2007-03-12
Lol.  Funny you should mention Suse.  I had downloaded and burnt a Suse dvd and tried that and it too also froze.  It installed fine but then on booting it went through the grub and all that and then just left the screen blank expect for a cursor in the top corner.

Its such a pain in the ***.  I really dont want to have to return to windows!

---

### Post by Meuro on 2007-03-12
> **hiker13526 said:**
> I am using the NF4K8AB-RS. Got nearly the exact same problem. It freezes at a tan screen for me. Ctrl Alt F1 works BRIEFLY, if I press it real fast and type in a command it works for a few seconds, then the whole thing freezes up. You can take a look at my thread to see what hasn't worked for me :) [http://ubuntuforums.org/showthread.php?t=378664](http://ubuntuforums.org/showthread.php?t=378664)

I read on a SUSE forum that foxconn mobo's just plain aren't supported on linux yet. I'm not sure if the guy was telling the truth, or if they still aren't supported. Just didn't sound good for us foxconn users...

Was just reading through the above link and thought it looked familiar and then i realised i had read it when searching for others in similar situations lol

---

### Post by hiker13526 on 2007-03-12
I was able to install openSuSe fine, but when it came time to boot I got a greenish screen, and the thing locked up. I just said forget this, I don't even want suse, so I'm not gonna work to make it work. Went back to trying ubuntu. Still stuck.

On another note: I have tried xubuntu, kubuntu, and ubuntu. AMD64 and i386 of each. Also tried openSUSE, another failure. DSL booted fine for me, but wouldn't find my network card. LinuxMint didn't like loading either. I have a few more I'm gonna try though, but it seems my computer just likes windows.

---

### Post by hiker13526 on 2007-03-13
[quote=http://www.newegg.com/Product/CustratingReview.asp?item=N82E16813186056]Pros: Has all the connections that you could ever need for drives. Supports Linux FC5. Price.[/quote]

That is for my motherboard. I can't test Fedora atm, but I will when I get home. Have a go if you get bored, and please, remember to post the results ;)

I don't know how linux compatability works, but I thought that things like chipsets and mobo 'drivers' were embedded in the kernel, so if it works on one distro, it'll work on other ones with the same base linux build. Can anyone verify if this is true?

---

### Post by Meuro on 2007-03-14
Can anyone confirm that foxconn mobos aren't supported yet?  Aren't apples built these days using foxconn mobos too?  How come it works for them?

---

### Post by Meuro on 2007-03-18
Ok so I tried Fedora but it too kept freezing durning setup.  Using the graphical and text setups.  What the hell?

---

### Post by belikralj on 2007-03-18
I can't seem to find the thread I just visited but a guy there had a problem with his motherboard being too new, and the sata drivers didn't want to work, I don't think that that's the case here but I have no other advice to give you than to tryout the Feisty 7.04 build if all else fails. It worked for him, it might work for you. Remember that it is only an Alpha release and it is due for final release somewhere in April this year, so it may not work to specs yet, but it may not freeze. Sorry I couldn't halp more

---

### Post by hiker13526 on 2007-04-21
I was hoping that the new Feisty would fix this problem, but I just attempted another install and I am having the same problem. Any help?

---

