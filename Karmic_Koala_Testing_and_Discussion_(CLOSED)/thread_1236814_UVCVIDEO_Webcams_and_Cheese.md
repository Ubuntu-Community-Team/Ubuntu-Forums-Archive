---
title: "UVCVIDEO Webcams and Cheese"
date: 2009-08-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cheleb on 2009-08-10
Hi fellow Karmic testers,

I have a rather nasty problem with my webcam (Logitech Vision Pro) in combination with cheese.

Basically, sometimes cheese fails to identify the webcam and shows either no image, or a colored test pattern. It often happens after a fresh boot, but it can also happen anytime else.
When it happens, any subsequent access to the cam from any program fails until I unload/load the uvcvideo driver again.
I was never able to produce a similar kind of error with another webcam-related tool. Ekiga, camorama, Skype, luvcview & co were all able to initialize the cam correctly and display an image.

I have this problem since intrepid and I still can't seem to pinpoint the error.
Here's a list of things I tried in order to fix the problem:
[LIST]
[*]updating the kernel+drivers (intrepid->jaunty->karmic)[*]updating cheese versions (intrepid->jaunty->karmic)
[*]updating gstreamer (intrepid->jaunty->karmic)
[*]building and using the latest mercurial tree from [http://linuxtv.org/hg/~pinchartl/uvcvideo](http://linuxtv.org/hg/~pinchartl/uvcvideo)
[*]using different usb ports
[*]checking on another machine
[*]changing usb related bios settings
[/LIST]
Nothing helped so far :)

Now I figured I could give the Fedora LiveCD a try. And well, to make a long Story short, the problem doesn't exist in Fedora-Land!

So i guess my questions is:
Does anybody in here have a similar experience with Ubuntu?

---

### Post by kaanchan on 2009-08-16
I've experienced webcam issues recently as well...

Since upgrading from 9.04 to 9.10 (jaunty->karmic), my *creative live! cam notebook* fails to run in cheese. lsusb shows it is present, but /dev/video0 is not created as it used to be in jaunty. also lsmod doesn't show any drivers which were loaded in jaunty as being loaded in karmic.

---

### Post by rsay on 2009-08-19
My logitech pro 9000 has always been touchy with Cheese, especially on 64bit. There have been occasions in the past when I could get it to work on my laptop running a 32bit ubuntu, but it was never reliable. I tried again recently on Jaunty 64 without success. I considered trying to compile the uvcvideo driver myself, but I thought I would wait for the new release and see if it got fixed. Luckily, I can get by pretty well without cheese. I have read convincing arguments from the Cheese devs, explaining that the problem is not with the Cheese code, but related to the way that the driver relates to the underlying gstreamer architecture, but I haven't had problems with any other program.

---

### Post by cheleb on 2009-08-19
> **kaanchan said:**
> I've experienced webcam issues recently as well...

Since upgrading from 9.04 to 9.10 (jaunty->karmic), my *creative live! cam notebook* fails to run in cheese. lsusb shows it is present, but /dev/video0 is not created as it used to be in jaunty. also lsmod doesn't show any drivers which were loaded in jaunty as being loaded in karmic.

Hmm, that's strange.
Have you looked at dmesg to see if there are any errors in your log while loading the driver?

Try```
dmesg | grep uvcvideo
```to see if anything comes up.

---

### Post by cheleb on 2009-08-19
> **rsay said:**
> My logitech pro 9000 has always been touchy with Cheese, especially on 64bit. There have been occasions in the past when I could get it to work on my laptop running a 32bit ubuntu, but it was never reliable. I tried again recently on Jaunty 64 without success. I considered trying to compile the uvcvideo driver myself, but I thought I would wait for the new release and see if it got fixed. Luckily, I can get by pretty well without cheese. I have read convincing arguments from the Cheese devs, explaining that the problem is not with the Cheese code, but related to the way that the driver relates to the underlying gstreamer architecture, but I haven't had problems with any other program.

That pretty much sounds like my problem. I had a quick look at the uvcvideo homepage and checked your camera model. Seems like some models of the pro 9000 also have the famous hardware bug.
From the comments of that page> Some revisions of this model suffer from issues similar to those described in [[1]("http://linux-uvc.berlios.de/#footnote-1")]. Only specific part numbers are affected. See [Logitech UVC devices list]("http://www.quickcamteam.net/devices") for more information. 

Maybe double check to see if your model isn't affected.

I do believe those comments from the cheese devs. If fact, cheese does run perfectly normal on Fedora, proving that my hardware indeed works and maybe hinting that there is some kind of 'special' configuration in Ubuntu regarding kernel/uvcvideo/gstreamer. That's what i am looking for.

Maybe also pop in an Fedora 11 livecd and see if things are different there? Cheese is default in Fedora, so it is easy to test.

---

