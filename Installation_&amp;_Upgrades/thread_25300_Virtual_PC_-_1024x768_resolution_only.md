---
title: "Virtual PC - 1024x768 resolution only"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by tenjin on 2005-04-09
Hi,

I've installed Ubuntu on Virtual PC on two machines with ATI cards, a R50p IBM Thinkpad, and a Dell Dimension 4600. Both have (different) ATI cards.

I can only get Virtual PC to display at 1024x768. It seems to recognise the video card as a SIS card.

Any ideas how I can get the resoltion up to 1280x1024 or even 1600x1200? Both physical cards are capable of it.

Thanks.

D.

---

### Post by localzuk on 2005-04-10
[QUOTE=tenjin]Hi,

I've installed Ubuntu on Virtual PC on two machines with ATI cards, a R50p IBM Thinkpad, and a Dell Dimension 4600. Both have (different) ATI cards.

I can only get Virtual PC to display at 1024x768. It seems to recognise the video card as a SIS card.

Any ideas how I can get the resoltion up to 1280x1024 or even 1600x1200? Both physical cards are capable of it.

Thanks.

D.[/QUOTE]
 The problem is that VPC is not going to use your cards directly, instead it is outputting the data to a window in windows which then gets rendered to your card. That is why it doesn't recognise as your card but as a SIS one.

To try and fix your problem, have a look at your /etc/X11/xorg.conf file, adding

"1280x1024" "1600x1200" where the list of resolutions are.

You will need to reboot X once you have done this. (You will also have to do it using sudo).

---

### Post by unicynic on 2006-08-21
This thread is old but since I've found the way to do it, I want to share. The instructions is actually meant for beginners, as I am a beginner too.

Using Virtual PC, Ubuntu (mine is 6.06 LTS) will use the S3 driver. Even after you reconfigure the X server, you're still stuck with a max of 1024x7678.

This is how I do it:

Open Terminal and run: sudo dpkg-reconfigure -phigh xserver-xorg

In the configuration, choose to enable 1280x1024. I don't know about higher resolutions but following these steps, you'll get 1280x1024, 1024x768, 800x600, and 1152x768. I did set other resolutions but those are all I get - good enough since I only want the 1280x1024 (my LCD native res).

Once that's done and the xorg.conf is generated, open it. I just use "sudo nautilus" to open nautilus as admin and browse to /etc/X11/, right click xorg.conf, and edit with text editor.

Since we're using Virtual PC, the conf must be about the same. So, in line 93 of xorg.conf, you'll see that Driver is "S3". Change this value to "vesa".

The vesa driver only support 1280x1024 mode in 16 bit color in the Virtual PC. So, in line 108 of the file, change the value of DefaultDepth from 24 to 16.

Then save the file and reboot. That's it.

Funny thing is, then I'm stuck with just 1280x1024.. hmm...

---

### Post by burundanga on 2006-09-27
You da man!!

---

