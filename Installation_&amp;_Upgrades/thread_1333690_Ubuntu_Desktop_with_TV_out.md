---
title: "Ubuntu Desktop with TV out"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by tom.swartz07 on 2009-11-21
Hi all,

I recently received a rather modern Dell Dimension 3000, and I would love to upgrade it to use as a Home Entertainment System, use boxee, or some other variation of a media server, and run tv through it, and use a television screen as a monitor.

What kind of work is needed, or rather, what kind of Linux-friendly hardware would allow me to hook up Cable in, and have an s-video/rca out? Helpful links or information regarding specific hardware would be awesome.

Any help would be greatly appreciated!

---

### Post by tom.swartz07 on 2009-11-21
I would also like to point out that I would LIKE to keep cost at a minimum, but for key hardware pieces, some expense is alright.

---

### Post by laceration on 2009-11-21
If you want to tune digital cable or over the air TV, you need a dvb card ($15-$100). The ones that work w/ Linux are here:
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)
or a place like Newegg will have reviews mentioning if they work w/ Linux.
Mostly all that is available from cable is the basic tier, the premium channels need to be decrypted w/ the cable cos. box.

TV screens and Computer Monitors are virtually interchangeable these days.  The video out is just what the computer already has.  I would forget about s-video/rca out as they are low quality leftovers from the analogue age.  VGA hooks up to component as does dvi to hdmi.  If your TV cannot handle those consider that you can get 24" 1080p monitors for $200 and be watching hi definition.  If you want to go that route a better video card for the Dell may be in order too.  You can get a suitable one for $40 or less.

A remote control, Microsoft media center ones w/ a usb receiver work best, can be had for $20-25.

If this is too much $$ it might best to start w/ the dvb and upgrade down the line.  If the video on the Dell doesn't have s-video out, it would be stupid to buy one, but if you do, get it on a card that will do hidef for you later on.

---

### Post by steveneddy on 2009-11-21
Most modern TV's have either a PC VGA input or the wonderful HDMI connection.

VGA give very a very good picture on HD TV's.

---

### Post by tom.swartz07 on 2009-11-21
> **laceration said:**
> If you want to tune digital cable or over the air TV, you need a dvb card ($15-$100). The ones that work w/ Linux are here:
[http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page)
or a place like Newegg will have reviews mentioning if they work w/ Linux.
Mostly all that is available from cable is the basic tier, the premium channels need to be decrypted w/ the cable cos. box.

TV screens and Computer Monitors are virtually interchangeable these days.  The video out is just what the computer already has.  I would forget about s-video/rca out as they are low quality leftovers from the analogue age.  VGA hooks up to component as does dvi to hdmi.  If your TV cannot handle those consider that you can get 24" 1080p monitors for $200 and be watching hi definition.  If you want to go that route a better video card for the Dell may be in order too.  You can get a suitable one for $40 or less.

A remote control, Microsoft media center ones w/ a usb receiver work best, can be had for $20-25.

If this is too much $$ it might best to start w/ the dvb and upgrade down the line.  If the video on the Dell doesn't have s-video out, it would be stupid to buy one, but if you do, get it on a card that will do hidef for you later on.

This is excellent help! thank you so much!
Ive been looking all around for a comprehensive guide that lays out information like you have just done, and certainly exceeded my expectations!

I currently have 1 or 2 TV's that support the pc-video in, as well as the multitude of other video formats, but the Dell in question ONLY has the old, blue monitor out (the one with the 10-15 pins), and several different cable variations werent able to convert the video to a usable state. I used a vga to rca connector from newegg (it was only ~$4) but was unable to hook it up correctly. 

I figured that it was because of both a.) the old hardware and b.) cheap-o cable connections. 

Will those video cards you mentioned do video-out, as well as video-in?
To clarify; will they not only allow me to run the cable or video lines in, but will they also include video out ports for other cable formats, or will i still be limited to vga? 
The reason I ask is because I already HAVE several new tvs, but none have connectivity beyond s-video and rca input. Granted, theyre only 720p HD, but still, given their size and convenience, I would like to be able to use them as monitors.

---

### Post by laceration on 2009-11-22
To make it a little clearer...

**Video In**
For video into your computer you need a DVB device, usually a pci card, but also available as an usb stick.  Within Linux they are often referred to as DVB, but when looking around for one in the USA they probably will not be explicitly called DVB, but will be the cards that support ATSC, which is over the air digital TV and QAM, which is digital cable TV.  Europe, Asia, Australia, etc., use different DVB systems such as DVB-T, DVB-S.  NTSC is the now 98% defunct analogue TV.  Some digital cards support this too, you may possibly want to use this to connect a video camera or playstation or the like to your computer.

**Video Out**
Video out is simply the native video out that your computer already has.  If you cannot match this up to the inputs of your TV screen you can get a new pcie video adapter that will.  The only difference between modern LCD TV's and a computer monitor is that is that the TV's include a tuner.  Since a DVB card is a tuner, in our setup, a Computer Monitor is a perfectly adequate TV screen.

I wondering if you have component and rca confused.  They are the same size and use the same type of cables.  Component inputs have a red, green and blue inputs while rca is just one yellow for video and a red and white for sound.  There are cable adapters for vga to component.  If you have a screen that does 720p, it should have component inputs.  This would be a good way to go for you.

---

### Post by tom.swartz07 on 2009-11-28
> **laceration said:**
> To make it a little clearer...
**Video Out**
I wondering if you have component and rca confused.  They are the same size and use the same type of cables.  Component inputs have a red, green and blue inputs while rca is just one yellow for video and a red and white for sound.  There are cable adapters for vga to component.  If you have a screen that does 720p, it should have component inputs.  This would be a good way to go for you.

Im fairly certain that I have identified the TV inputs correctly... When I get back to school tomorrow, Ill check again, and ill post pictures here to verify. It was a fairly new (purchased in 2007) lcd tv. It only has 720p res, but it is still very sharp. The inputs, like I have said, are s-video, rca X2 (red, yellow, white) and coaxial. There may be one that I am missing, but I do not think so.

I was able to scavenge, over the course of this weekend, a 5-foot vga-vga cable, that I could (hopefully) use on the large 32" tv that has vga-in inputs.

---

