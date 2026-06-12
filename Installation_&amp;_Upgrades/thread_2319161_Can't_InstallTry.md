---
title: "Can't Install/Try"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by edward39 on 2016-04-01
Trying to install Ubuntu 14.04, first time user.  

Boot to stick, select "Try without Installing" and get "No DVI Signal" and black screen, have to un plug PC to restart.

Same thing on "Install".

Hit F6 on Ubuntu Boot Menu, tried nomodeset, says file not found.

Not a UEFI problem.

Specs:
B85+ mobo
i5 4440 
16gb DDR3 RAM
MSI GTX 970

I know the 970 is the root of the issue, and I'm 99% that nomodeset or some other similar function is the solution, but I have had no luck getting the boot to accept nomodeset.

---

### Post by Bucky Ball on 2016-04-01
Welcome. Ok, my GTX 970 is a different make but has two DVI ports on the back. Has yours? Tried swapping where you have the DVI monitor plugged in? If you have two DVI slots, they may look the same, but actually they're not, at least on mine. Give that a go and see what happens.

(PS: Also, do you have 'use internal video' or something like it switched on or off in the BIOS? A further tip: always have a sniff around before posting. [This]("https://forums.geforce.com/default/topic/780349/geforce-900-series/gigabyte-gtx-970-g1-dvi-i-port-dvi-no-signal-vga-full-signal/") might be of help and there are plenty of others who've already faced [this problem here]("https://duckduckgo.com/?q=gtx+970+No+DVI+Signal&t=h").)

---

### Post by edward39 on 2016-04-01
Okay just tried that, no luck.  Screen stays black, but I hear a chime after about 30 seconds.

---

### Post by edward39 on 2016-04-01
This is after three days of searching every forum post I can find.  I've ready just about every link on that search results.  Nothing works.

I'm about to just give up, honestly.

Use Internal was on when I first started trying, that was one of the first suggestions I read to try.

---

### Post by Bucky Ball on 2016-04-01
Make sure 'use internal' is off. If you're hearing a chime, its working, you're just not seeing it. Do you mean like jungle drums? You're almost there.

No luck with nomodeset? Trouble getting the machine to accept? Not sure how you're going about this, but boot from the install disk> when you see the purple screen with the icon at the bottom, hit any key> hit F6 and you should see some options, one of them 'nomodeset'. Choose that and continue with 'Try Ubuntu'. Any luck?

---

### Post by edward39 on 2016-04-01
Integrated Graphics is Disabled.

Took a couple of pictures, will take more on next attempt.

---

### Post by Bucky Ball on 2016-04-01
Please attach large pictures. 'Adv Reply' or 'Go Advanced' and use the paperclip icon there, thanks. Waste of space inserting in the body of posts and spare a thought for those (potential helpers) with slow connections or vision issues. Thanks. (I've attached the ones in your last post.)

Have you tried 'Continue to boot from first hd' and what happens when you do? Did you hit a key during boot when you got to the purple screen with the icon at the bottom? Seems not. Are you getting that screen? Should come after the manufacturer's splash screen and before the Yumi screen. Not sure why you're using Yumi and know nothing about that, so can't help there, but not sure that has anything to do with this.

---

### Post by edward39 on 2016-04-01
Sorry about the images, edited as attachments.

Continue to Boot from First HD just boots Windows as normal.

No purple screen.

When I get the Manufacturer's screen, I use F9 to select Boot Media, and choose the USB stick I'm using.  It then goes to the first image.

---

### Post by Bucky Ball on 2016-04-01
Click 'Advanced Options'. That should take you to the screen where you can hit F6 to use nomodeset. Not sure if that is the issue here, though. We'll see.

---

### Post by edward39 on 2016-04-01
I've tried that already, but I'll do it again and take pictures.  Thanks for the help, by the way.

---

### Post by Bucky Ball on 2016-04-01
All good. ;)

---

### Post by Bucky Ball on 2016-04-01
I'm thinking [this maybe has something to do with it]("http://nvidia.custhelp.com/app/answers/detail/a_id/221/~/what-is-the-difference-between-dvi-i-and-dvi-d%3F"). Is it a DVI-D input in your monitor? It should have two inputs. Have you tried the other? Could be a DVI-I cable into a DVI-D input or some such obscurity. That's what I meant about my GTX 970 (ASUS Strix GTX 970). It has HDMI, DVI-D and DVI-I outputs. The latter two look the same.

Also, is this an ASUS motherboard and a second monitor?

---

### Post by edward39 on 2016-04-01
[ATTACH=CONFIG]268118[/ATTACH][ATTACH=CONFIG]268119[/ATTACH][ATTACH=CONFIG]268117[/ATTACH][ATTACH=CONFIG]268116[/ATTACH][ATTACH=CONFIG]268115[/ATTACH]

1) Showing BIOS graphics options, Internal is Disabled, would any other settings affect it?

2) What "Advanced Options" looks like.

3) What "Help" looks like.

4) Pressing F6 on the "Help" screen brings me here

5) Typing "nomodeset" gives me this.

Mobo is made by BioStar

Single Monitor, made by ASUS.

---

### Post by Bucky Ball on 2016-04-01
In your first screenshot, you have 'Primary PCIE' in the top block set to 'Auto'. Try setting that to 'Enabled'.

Further to the point I was making previously: have a [look closely at these two]("http://nvidia.custhelp.com/app/answers/detail/a_id/221/~/what-is-the-difference-between-dvi-i-and-dvi-d%3F") here and at the connectors and cables you are using. If it works with Windows, though, redundant point and forget. :|

---

### Post by edward39 on 2016-04-01
Yeah Windows works no problem, and I actually tried switching cables (DVI-D to DVI-I and even tried a VGA cable with a DVI-I converter) no luck.

I will try the Primary PCIE and let you know.

---

### Post by edward39 on 2016-04-01
[ATTACH=CONFIG]268123[/ATTACH]

Primary PCIE gives me this option, no choice for "Enable".

I'm 99% sure that the problem is my graphics driver, and that Nomodeset should be what fixes that issue, but I'm not sure how to get nomodeset to work with what I have?

---

### Post by edward39 on 2016-04-01
I tried changing the Primary PCIE around, no dice.

---

### Post by sudodus on 2016-04-01
I think it is night in Australia now (where Bucky Ball lives). It will soon be late for me too. Let us hope other people will chip in and help you (until it will be late for you too) :-)

I suggest that you try other boot options, not only nomodeset. You can try them separately, and several at the same time. Maybe you need nomodeset plus another one.

See this link, where you find links to instructions how to add boot options in different scenarios, and also a long list of boot options alias kernel boot parameters.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by Bucky Ball on 2016-04-01
PCIE-1, if that's the slot the GTX 970 is in. Might not make a difference, but maybe Linux needs it set and Win doesn't. Stranger things have happened.

Check out sudodus' link, but I suppose if you can't find where to plug an option in, then ...

(* Yes, it is almost sun up here but I fell asleep on the couch for four hours earlier after watching football and eating icecream and haven't been able to sleep. Getting there now. Knocked off some uni work, though. :))

---

### Post by edward39 on 2016-04-01
Figured it out!

On the main screen, at the bottom, it says "Press ENTER to boot and TAB to edit a menu entry" but most of said text was covered on my screen by the Ubuntu logo repeating.

Once I deciphered the text, I pressed TAB on "try without installing" and typed 'nomodeset' and hit enter and boom, Ubuntu purple screen.

Now I've got it installed and I'm learning the Command Line.

Thanks for the help!

---

### Post by Bucky Ball on 2016-04-01
Great news!!! Welcome to Linux and hope you enjoy it and your stay here. 

Good luck and thanks for marking the thread as solved. :D

PS: Don't forget to do a full update to your new install with the Software Updater or in a terminal with:
> 
sudo apt-get update
sudo apt-get dist-upgrade

This will not upgrade the system to a newer version, but it will update/upgrade all installed software.

---

