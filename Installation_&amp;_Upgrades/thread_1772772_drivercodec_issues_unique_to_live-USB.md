---
title: "driver/codec issues unique to live-USB?"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Muster Mark on 2011-06-01
Hi All,

I am trying to test 11.04 out before upgrading with the live usb, and I can't get certain things to work.  I have searched the forums and can't really find anything directly applicable, so I think it may be simply the limitations of the live USB:

1, cant play AAC files (.mp4).  I tried ```
sudo apt-get install faac faad 
``` but this results error: ```
E: Package 'faac' has no installation candidate
```.  There was no issue installing these packages in 10.10

2, .avi come out with white as black.  even in  VLC the white always comes out as black, but the other colors are correct.

3.  it can't find the proprietary nVidia through "additional drivers", and thus I can't test out unity on my main laptop (on the asus netbook with intel integrated graphics it boots into unity).  I ran ```
sudo jockey-gtk
``` but all it was able to find were the experimental community drivers.

Are these simply limitations of the live install?  I remember being able to get graphics up and running just fine with 10.10 under the live CD, so I am a little hesitant to just take the plunge and pray I will be able to play my media/use my graphics hardware.

Thanks in advance, and please pardon me if I am simply being dumb.
Cheers

---

### Post by Herman on 2011-06-11
I didn't have any trouble installing the nvidia proprietary driver and I'm able to use the unity desktop. 
After reading your post I went and tried to play as many various video file types as I can find and my totem movie player and vlc media player were able to play all except .swf files. I was surprised at how well the .MTS video files from my Sony Camera worked, they used to be a little choppy the last time I tried, but now they play very nicely indeed. I'm impressed! At least for my hardware, 11.04 seems to be the best Ubuntu yet. I'm very pleased with Natty Narwhal.
So far I have installed or upgraded a number of PCs to Natty and I have been pleasantly surprised each time. In one computer I was even able to easily configure an Australian Telstra 3G Wireless Broadband dongle with almost no effort, which is something that has been quite a problem in the past.

---

