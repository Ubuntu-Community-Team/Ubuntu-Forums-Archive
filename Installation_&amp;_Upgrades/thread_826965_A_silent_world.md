---
title: "A silent world"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by offspring_cn on 2008-06-12
I'm sorry,I'm not good at my English

It's very poor....

But I meet a trouble,so I come here to ask for help

Now ,let me to state the problem

I bought a Dell PC in May,but When I want to install Ubuntu8.04

It can't run.(when I use 7.04's livecd ,all was well 

but 8.04's livecd ,all turned bad)

So, I install the Nvidia's device soft(I don't how to say that in Englist,but I have no idea..,sorry)

Haha,I can run CompizFusion!

Beautiful!

But I make a mistake after that

I intall the VirtualBox,and Host turn"silent",

There's no sound in the horn

I never try to unintsall VirtualBox

I don't think it could make the horn work

what can I do?

Thanks!

---

### Post by jelson on 2008-06-12
What language to you speak?  There are other language Ubuntu forums that might speak a language you would understand.  It sounds like you need a driver for your sound card.  What is your sound card?  Is this a desktop or a laptop?  I'm new to Ubuntu, but there should be drivers somewhere for whatever card you have.

---

### Post by offspring_cn on 2008-06-12
> **jelson said:**
> What language to you speak?  There are other language Ubuntu forums that might speak a language you would understand.  It sounds like you need a driver for your sound card.  What is your sound card?  Is this a desktop or a laptop?  I'm new to Ubuntu, but there should be drivers somewhere for whatever card you have.

I speak Chinese

but they ask me to there

They said that only there could solve my problem.

I'm new to Ubuntu,too.

I have been find some drivers to my card(AC'97——we call it like this in china,you may call it alsa driver)

But it doesn't work.

When I at the entrance of Ubuntu,I can hear the sound like "dang"

but after I login ,the sound disappeard

...

---

### Post by Sef on 2008-06-12
> I have been find some drivers to my card(AC'97——we call it like this in china,you may call it alsa driver)

Applications > Accessories > Terminal 


```
gksudo gedit /etc/modprobe.d/alsa-base
```

Check out this [old thread]("http://ubuntuforums.org/showthread.php?t=160576&highlight=sound") of mine too.  I had the same problem and this was how I got sound.

---

### Post by offspring_cn on 2008-06-12
oh ,It still no sound...

Maybe I should reboot my computer or uninstall VirtualBox?

---

### Post by offspring_cn on 2008-06-12
I have reboot my PC

and it still no sound

I'm upset and want to throw it out of my window...

Sef,I had change the file you said ,but it doesn't work

Could you help my?

I have had upload a picture about it,thank you!

---

### Post by Habbit on 2008-06-12
Try to check your sound card is being correcly detected by ALSA: post the output of `aplay -l' and then try to play a (plain WAV) sound file through aplay.

---

### Post by offspring_cn on 2008-06-12
the player said   "Failed to connect stream: Invalid argument"

---

### Post by offspring_cn on 2008-06-12
maybe there is something wrong with GStreamer plugin, but I  fail to instill this plugin,it this plugin cause all problem?

---

### Post by offspring_cn on 2008-06-12
I have install  GStreamer ,but it still doesn't work&#8230;&#8230;

---

### Post by Habbit on 2008-06-12
If the problem is that ALSA (the kernel drivers) cannot find your sound card, then no media framework (GStreamer) will help you. What was the output of `aplay -l'?

---

### Post by offspring_cn on 2008-06-12
aplay: device_list:205: &#25214;&#19981;&#21040;&#22768;&#21345;&#8230;


It means couldn't find sound card

---

### Post by Habbit on 2008-06-12
Hmm... really strange, since AC-97 (if that is your sound card) is extremely common and well supported. However, I cannot help you any further, since I'm leaving for bed - see you tomorrow!

---

### Post by offspring_cn on 2008-06-13
I'm sorry

I almost forget the time difference  

Good Night-though we 'ra having a daytime.

---

### Post by Habbit on 2008-06-13
I'm back now, but I won't stay for long - I have an exam today.

It seems that the kernel cannot see your sound card. Please run `lspci -nn' and post the results here, so that we can see if there is any "suspicious" (i.e. soundcard-looking) device in your PCI bus. In particular, look for devices whose category is "Multimedia audio device [0401]"

If you have some more time in your hands and you think that a particular device is the sound card, google for its PCI ID and you might find web pages telling you what drivers to use - then you can check if the kernel has the relevant modules handy. Hint: in the `lspci -nn' listing, the PCI ID is the [aaaa:bbbb] style number at the far right of each line. Don't include the "(rev xx)" part in you search, but take note of it, since different revisions may require different configuration settings.

Well, that was as far as my knowledge goes. Hope it helps!

---

### Post by offspring_cn on 2008-06-13
Thank you,Habbit

I have been kill that 2.6.24-16 kernel and install it again

It works!

thank you very much!

Good look to you,and wish you get a good mark!

---

### Post by Habbit on 2008-06-14
> **offspring_cn said:**
> Good look to you,and wish you get a good mark!
Thanks, I won't get the results until two or three weeks, but I think I will get at least 70%. Back to your issue, and just out of curiosity :popcorn:
What did you do exactly? You said you reinstalled the kernel, but which one? The default "linux-image" that comes with Ubuntu or another one compiled by you with custom settings to support the card? And finally, which souncard was it?

---

### Post by offspring_cn on 2008-06-14
> **Habbit said:**
> Thanks, I won't get the results until two or three weeks, but I think I will get at least 70%. Back to your issue, and just out of curiosity :popcorn:
What did you do exactly? You said you reinstalled the kernel, but which one? The default "linux-image" that comes with Ubuntu or another one compiled by you with custom settings to support the card? And finally, which souncard was it?

My ubuntu said my cound card is"HDA Intel(alsa mixer)"

but I don't know what soundcrad it is...

by the way ,the kernel I reinstall is with the help of a friend

so ,I'm not sure .

but /boot/grub/menu.lst is kernel 2.6.24-16

Thank you very much!

---

### Post by Pumalite on 2008-06-14
Do you have the .19 kernel in your menu.lst?

---

### Post by Habbit on 2008-06-14
> **offspring_cn said:**
> My ubuntu said my cound card is"HDA Intel(alsa mixer)"

but I don't know what soundcrad it is...

Even more strange :confused: because such a soundcard _does_ have support in the default Ubuntu kernel, in the snd-hda-intel module. Maybe you had a custom-compiled kernel which didn't include support for it :roll:

---

### Post by Pumalite on 2008-06-14
To find out; all you have to do is run:
sudo lshw -C sound

---

### Post by offspring_cn on 2008-06-16
> **Pumalite said:**
> Do you have the .19 kernel in your menu.lst?

No,just have 18 in my menu.lst

I have update my ubuntu

but it still not have

maybe the mirror's mistake?:)

---

### Post by Pumalite on 2008-06-16
Post:
lshw -C sound

---

### Post by Wandering on 2008-06-16
It's a known bug in 7.10, and I tried all the bug fixes posted, but the bottom line is I could make most audio programs work just fine, but never could get system sounds.  Some folks were successful, so look in these forums for some sticky threads on sounds.

It was more or less fixed in 8.04 with the installation of pulse audio. I now have system sounds, but some of the audio software, and the only important one was Audacity, broke. All other programs I use seem fine under pulse audio, but I have to kill the process before running Audacity. I then lose system sounds just as before, but all other audio seems to work though requiring very long start times.  

I know there are folks out there using all audio just fine out of the box, but there are probably as many with some problems. 

Good luck.  I have no solution other than a caution that there may not be a solution.

Perhaps some of these experts will get you there.

---

### Post by mtantawy on 2008-06-16
> **offspring_cn said:**
> I'm sorry,I'm not good at my English

It's very poor....

But I meet a trouble,so I come here to ask for help




hi there, i am not telling you a solution for your problem, but i think i can make it more easy to you to speak english in this forum or anywhere else

to translate from any language to any
go to [www.google.com](www.google.com), another link rather than search states "language tools", you can use it to translate text "no limit i think for the length", also you can translate total pages, and chines and other many languages are available...

i use it but not for Chinese so i cant tell how good is it, but it is google, so i think it is pretty good

Good Luck with your problem&Ubuntu ;)

regards,
Mahmoud Tantawy

---

