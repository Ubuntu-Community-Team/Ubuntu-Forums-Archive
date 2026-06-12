---
title: "Acer Aspire 5920 &amp; Ubuntu 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by BB88 on 2008-10-31
Well what can I say, this just simply worked straight out of the box, as the saying goes.

I downloaded the .iso on the release day in high anticipation of the newest version of Ubuntu. Having used previous versions on the this laptop, 8.04 and 8.04.1, I was expecting to do some configuration when it had all been installed, but everything worked!

The problematic Wireless Button on the left hand side, worked, and the LED was showing. The  Sound card was also working, no need to enable Surround Sound either. The Touch Pad scroll works, and the Web Cam works great in Cheese.

The only thing that is not working is the multimedia keys on the right hand side, as they are still allowing you to scroll up and down a document, which I think is pretty neat anyhow.

I just wanted to share my experience, as there have been a few problematic installations with the newest release, but it is all fine and dandy over this end!

Cheers Ubuntu!

---

### Post by mangecelle on 2008-10-31
> **BB88 said:**
> Well what can I say, this just simply worked straight out of the box, as the saying goes.

I downloaded the .iso on the release day in high anticipation of the newest version of Ubuntu. Having used previous versions on the this laptop, 8.04 and 8.04.1, I was expecting to do some configuration when it had all been installed, but everything worked!

The problematic Wireless Button on the left hand side, worked, and the LED was showing. The  Sound card was also working, no need to enable Surround Sound either. The Touch Pad scroll works, and the Web Cam works great in Cheese.

The only thing that is not working is the multimedia keys on the right hand side, as they are still allowing you to scroll up and down a document, which I think is pretty neat anyhow.

I just wanted to share my experience, as there have been a few problematic installations with the newest release, but it is all fine and dandy over this end!

Cheers Ubuntu!


For me it was also a pleasant change. Everything work right out of the box. I also tried with a 3G modem with the operator Yoigo. Ubuntu 8.10 detected the card asked me for the operator i used and then voila. 

Now i dont know what happened. I was surfing with the wireless conection and i think i hit the wireless button or something because the wireless was totally disconnected. Now i cannot get it on again. Hitting the wireless button dosent do anything. Somebody have experienced the same thing please advice...

Thanks in advance

---

### Post by Hukei on 2008-11-01
I have experienced the same on my Acer 5920-6864 when I took off the battery to turn the laptop on without it. As always, the wireless went off, and I tried to turn it on with the key switch from the keyboard on Ubuntu 8.10 but nothing happened, however in Ubuntu 8.04 it worked.

I used the help program on Ubuntu 8.10 and it said to reboot on Windows, enable the wireless card, and go back into Ubuntu. That's what I did and it worked.

P.D. If there is anything wrong with the spelling or a word misused, I apologize. I'm not a native english speaker.

---

### Post by tfm_copycat on 2008-11-15
> **Hukei said:**
> 
I used the help program on Ubuntu 8.10 and it said to reboot on Windows, enable the wireless card, and go back into Ubuntu. That's what I did and it worked.

This is what I did too. Isn't there a workaround? I couldn't care less about the led (in fact, I prefer that it doesn't blink at all) but the functionality of the switch (which worked flawlessly in HH) now is gone.

No solutions so far??

---

### Post by Gordini on 2008-11-19
> **BB88 said:**
> Well what can I say, this just simply worked straight out of the box, as the saying goes.

I downloaded the .iso on the release day in high anticipation of the newest version of Ubuntu. Having used previous versions on the this laptop, 8.04 and 8.04.1, I was expecting to do some configuration when it had all been installed, but everything worked!

Update:
Well, I stumbled through the upgrade process (downloaded the .iso, burned it onto a CD, used Update Manager to install it) and it went pretty well.  WiFi works, sound works, web cam works, all data files remained in tact. The touch pad and the smart card reader seem to be dead but my wireless optical mouse is OK and I expect to find help with those issues somewhere on the forum.  Overall, I'm quite pleased.

I have 8.04 on my 5920 and I'd sure like to duplicate your experience but not sure how to proceed. (Ubuntu and this forum are still new to me.) The Ubuntu download page offers 8.10 and 8.10LTS and an option for 32-bit or 64-bit.  Then there's the option upgrade over the network.  Got any advice?

---

### Post by kippa on 2008-11-29
I was hopeing to find a solution to this as well. I only have Ubuntu on this system and wirelss connections is a must. It was working initially when a made the switch to 8.10, but when i pressed the wireless button on the side it has remains off.

Sorry for bumping an old thread.

---

### Post by goldberg333 on 2008-12-12
I haven't found good solution for this but I've noticed that pressing wifi button once and rebooting Ubuntu wifi becomes turned on. Though its not a best solutions it works for me, hope it will help you too :)

---

### Post by khaledziyaeen on 2008-12-16
Oh thank god!! Im so glad I found this page. I have the exact problem. At first everything was okay, then you know, I touched the wireless bottun, and swoosh!! no more wireless! So I see two solutions above. First, reboot on windows to turn it on, then switch to ubuntu. Second, press the button once, then reboot ubuntu.

I really don't understand whats the deal with this button. I wanna turn the wireless on, then break that stupid wireless button!!

Thanks for the help guys ):P

---

### Post by cometa2k7 on 2009-01-07
For the problem with the wireless switch, an easy fix is to hit the switch once, to turn the card back on (it's a hardware switch I think, not a software one). Then run ```
sudo ifconfig wlan0 up
``` in a terminal.

You can also create a launcher (set to launch in terminal) with the above code as the command, just so that you don't have to remember the code.

And if you prefer to have a more graphical password prompt, set ```
gksu ifconfig wlan0 up
``` as a launcher (you don't need to have that run in a terminal).

---

### Post by beyboo on 2009-01-24
I have the asian version of the 5920 model zd1 with intel  X3100 gfx and intel 3945 wireless. Intrepid solved many problems which plagued hardy for me, like the scroll keys on touchpad, speaker deactivation when headphone jack in use and some more. 

Currently I still have to give sudo ifconfig wlan0 up to have my wireless light blink, but connects effortlessly to my wireless network. 

Cheeze was a problem with the webcam due to some bugs in Cheese version and V4L, however recent intrepid updates to upgrade to new version of cheese and V4L updates resolved that one pending issue. 

I guess intrepid maximizes my hardware use by fitting in nicely. 

The only prob i currently encountered is my CPU temp shows 60C which I am not happy about :(

---

### Post by russu52 on 2009-01-24
thanks for the command. i have an acer aspire 5720 with ubuntu 8.10

i have removed vista completely, and running on ubuntu only. the wireless is on when it starts up, but if i hit the button i'm offline till i reboot. there are some quick launch and mm keys on the top that don't work, but otherwise everythign works fine.

btw, my card-reader reads SDHC, but does not recognise XD. any ideas? thanks!!

---

### Post by emolineros2006 on 2009-02-12
Thanks God! It worked. But for me it wasn't enough to run the command. First I had to click the button, if not the command would reply that the wlan0 card did't exist.

He hope we will soon have an update to fix it.

:)

PD: By the way, sorry for my English

---

### Post by rohitfeb14 on 2009-05-26
Just try out jaunty..
Everything works out of the box :p
BUT the multimedia keys do not work :( .... it seems ubuntu understands it as another touchpad..
Please let me know about any solution..
And the battery backup on Ubuntu is significantly less on acer aspire 5920

---

