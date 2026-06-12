---
title: "No Line Out sound on fresh install of Lucid"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by pstasho on 2010-08-14
Hi all, 

I'm making the jump to Ubuntu from Windows and I've done a fresh install of Lucid on a newly built box.  The barebones kit I used was a [SG41J1 PLUS]("http://us.shuttle.com/barebone/Models/SG41J1_PLUS.html").  After doing some testing and configuring, I've found that I get no sound output from the rear line out plug.  However, if I plug my speakers into the front "headphones" jack, I do get sound output there.  Could someone please help me in troubleshooting and fixing my issue of getting no sound from my rear line out plug?

---

### Post by jmfal on 2010-08-14
Open a terminal= applications> accessories>terminal

   enter code:
      
        alsamixer

make sure all your line-outs are turned up, cannot use mouse, use arrows on keyboard left right arrows change selections up/down arrows change output/volume

---

### Post by pstasho on 2010-08-14
Thanks for the reply, jmfal!  Unfortunately, that doesn't seem to do anything either.  I see the card showing HDA Intel and chip IDT ID 76c1 with volumes but in fiddling with each of the volumes, nothing happens.  I see the following:
Master, PCM, Front Mic, Line, Mic, and Aux.

---

### Post by gdesilva on 2010-08-14
> **pstasho said:**
> Thanks for the reply, jmfal!  Unfortunately, that doesn't seem to do anything either.  I see the card showing HDA Intel and chip IDT ID 76c1 with volumes but in fiddling with each of the volumes, nothing happens.  I see the following:
Master, PCM, Front Mic, Line, Mic, and Aux.


Try QAMix (sudo apt-get install qamix) and check whether the sound card is in mute state or not. I had a similar issue with my external usb Soundblaster Audigy and tried fiddling with the setting using alsamixer without success. Then by chance I tried out QAMix which gives you settings of your sound devices and found that Audigy was set to mute - no other app, including the Gnome Sound app, showed that the card was set to mute. Not sure what the reason was but it fixed my problem.

---

### Post by pstasho on 2010-08-15
No difference with QAMix either:(

---

### Post by gdesilva on 2010-08-17
Have you checked the hardware settings for this card on Sound Preferences? Open Sound Preferences -> Hardware. Highlight the card you are using and check the profile. If the profile is not correct this could be the reason for no output. For example I use an optical connection so I have to use the digital output profile and not analog output profile.

Hope this helps.

---

### Post by pstasho on 2010-08-18
Unfortunately, this is still a no-go:(  I've tried, as you suggested, to check the hardware profile but it was already set as analog stereo duplex.  I tried switching the profile around and then back but still with no changes:(

---

### Post by gdesilva on 2010-08-18
It is strange. I was just going through your earlier response on the output of the alsamixer and note that you have listed only Master, PCM, etc. In my case I have the Speakers listed as well which allows me to adjust the speaker volume. 

It appears you have tried out all options and only thing left to do is to try plugging in a usb sound device to make sure you can get sound working the way you want to. If this yields the same result then at least you will know that there is an issue with installation or else it is some peculiarity with this particular sound device working under Linux. I am just running out of any other other suggestions.

---

### Post by mudbrickcreative on 2010-10-13
pstasho did you ever get this fixed? I have the same problem.

---

