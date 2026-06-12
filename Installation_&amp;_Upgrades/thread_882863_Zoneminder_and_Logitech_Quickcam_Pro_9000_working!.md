---
title: "Zoneminder and Logitech Quickcam Pro 9000 working!"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Midahed on 2008-08-07
I've been struggling over the last few days to get Zoneminder working with my recently purchased Logitech Quickcam Pro 9000 webcam.

For other newbies who may be attempting to get this working, I can assure you that it _does_ work.

Unlike some webcams that I've used in the past, the Pro 9000 seems equally happy in low light as it is in full daylight.

[IMG]http://i24.tinypic.com/3483r0n.jpg[/IMG]

I've wanted to use the Zoneminder app for a while.  It's a video security system with remote browsing of camera streams or stills, alerts via email, FTP of 'evidence', etc.  However, I was initially put off by the sketchy information provided regarding support for webcams.  The impression given is that old webcams work while new models don't.

My system is based on Ubuntu 8.04 Hardy.  I already had Apache and MySQL installed on the system.  I downloaded Zoneminder 1.22.3 from the repositories.  There is a more recent release on the Zoneminder site, but it's still in beta testing.

Zoneminder doesn't directly support the most recent video4linux standard (v4l2).  The Pro 9000 is v4l2 compliant, so the workround is to use mjpg_streamer and then set-up a 'remote' camera on Zoneminder which uses the output stream from mjpg_streamer.

The Zoneminder documentation states that if you can't get the webcam working with xawtv then it probably won't work with Zoneminder.  However, this doesn't seem to apply if you have a v4l2 compliant webcam and are using mjpg_streamer to create the stream for Zoneminder.  I never did get xawtv working with my webcam - maybe because xawtrv only supports v4l1...?

I eventually found that I had to launch mjpg_streamer with the command

```
mjpg_streamer -i "input_uvc.so -r 320x240 -f 6" -o "output_http.so -p 8080"  -b
```

Having done that, browsing [[COLOR="Blue"]http://localhost:8080/?action=stream[/COLOR]](http://localhost:8080/?action=stream) allowed me to see the webcam output.  I had problems using Firefox 3 for this - it shows a single frame instead of the live video, but VNC works fine.

Having got to that point it was fairly easy to set-up the webcam in Zoneminder and get it working properly.

This isn't a how-to by any means, but it does highlight the things that tripped me up when I was trying to get it working.

This is a useful document on linux supported uvc devices:-

[[COLOR="Blue"]linux-uvc.berlios.de/#devices[/COLOR]](http://linux-uvc.berlios.de/#devices)

This document (and the Excel/PDF document it refers to) is useful if you are considering a Logitech webcam.:-

[[COLOR="Blue"]www.quickcamteam.net/hcl/linux/logitech-webcams[/COLOR]](http://www.quickcamteam.net/hcl/linux/logitech-webcams)

In the case of the Pro 9000 it turns out that there are lots of sub-models some of which have bugs while some are problem-free. Fortunately the part number of mine (the part number is only printed on the paper tag that's attached to the cable near the usb connector) showed mine to be one of the problem-free sub-models - a 861-464-0000.

Hope this might help another Zoneminder newbie. :)

---

### Post by chayzer on 2008-08-18
Nice to see somebody else did the footwork.. i've been wondering for awhile why nothing supports v4l2 devices.. now at least I can use the logitech cam for something.

Only thing I did different was 
 ```
mjpg_streamer -i "input_uvc.so -r [COLOR="Red"]640x480[/COLOR] -f [COLOR="Red"]15[/COLOR]" -o "output_http.so -p 8080"  -b
```

Just to get some better quality out of the cam

---

### Post by Midahed on 2008-08-19
> **chayzer said:**
> ...Only thing I did different was

 ```
mjpg_streamer -i "input_uvc.so -r [COLOR="Red"]640x480[/COLOR] -f [COLOR="Red"]15[/COLOR]" -o "output_http.so -p 8080"  -b
```

Just to get some better quality out of the cam

Good point!  I should have made that clear in my original post.  

I kept the resolution and frame rate relatively low because I'm using Zoneminder to do motion detection and raise alerts when the webcam sees something move.  Doing that at 640x480 and 15 fps would put an unduly heavy load on the CPU of a machine that I use for other things at the same time as its running Zoneminder.

---

### Post by transtech4u on 2009-04-19
It's been a while since anyone has posted to this thread, but I thought I'd give it a shot.  

It's not easy being a newby at this stuff, but I thought I had done my homework.  

Here is what I'm trying to accomplish:
I have somehow fumbled through the installation of Zoneminder 1.23.3 and I was able to get a cheap *** generic webcam to work, but I cannot get my Logitech Quickcam Pro for notebooks to work with it.

I have installed Skype and used the preferences section to test my logitech camera.  Skype recognizes the webcam, but Zoneminder doesn't seem to.  

There are 2 parts to this question:
1. There is a lot of information that talks about which driver to install so that zoneminder recognizes the qc pro for notebooks.  There is a lot of conflicting information.  Would one of you super-smart linux users be kind enough to locate the correct driver on the web (or tell me how I can get zoneminder to recognize the same drive that skype used to make the webcam work)
please could you type out the lines of code that I need to input into the terminal window to install the driver properly?  I'm very new to the linux world, but at least I was able to fumble through the zoneminder installation and get a crappy webcam to work. :)

2. Contrast.  The cheapass webcam works inside, but when I take the webcam outside and try to get a picture it's completely bleached out white.  I've spent an hour trying to get the contrast and brightness adjusted correctly, but it's hopeless.  I did not see any kind of auto contrast/brightness adjustment under the add new monitor creation page.
Are there any tidbits of wisdom to get this friggin thing to adjust and give me a clear picture outside?  I'm in the shade, not pointing at the sun.  

Any links, step-by-steps, or pearls of wisdom welcomed.

Thanks for your help.
Jason

---

### Post by Midahed on 2009-04-20
Hi Jason,

I'm not sure I can help beyond what I wrote in my original post.  Suffice to say that it took me AGES to find a way through the problems and get it all to work.  Since then I've just used it - and forgotten most of the detail of how I set it up.

The key thing for me was to understand the implications of using a v4l2 compliant webcam.  That may be all that's tripping you up.

You don't mention mjpg_streamer in your post.  This is all-important.  The version of Zoneminder that I'm using doesn't support v4l2 devices.  It's therefore essential to use a separate application (mjpg_streamer) to create the video stream that Zoneminder can then use.

You'll need to do a bit of digging yourself regarding Zoneminder and your webcam, theough.  The reason is that you're not using exactly the same version of Zoneminder as me. Your webcam may also be different.

Zoneminder first....

You're using a slightly later version than me.  When I was playing with this stuff back in August, there was some talk on the Zoneminder forum about native support for v4l2 devices.  So it's just possible that your version doesn't need mjpg_streamer.  You'll need to check that on the Zoneminder forum or in the documentation.

Webcam....

The manufacturers commonly use model names that are similar but the underlying device is different.  I'd check on the Logitech website to verify what standards your webcam complies with.  As far as I understand v4l2 is what nearly all webcams now use.  This is the reason that only 'old' webcams work natively with Zoneminder (because Zoneminder didn't/doesn't yet support v4l2 itself).

So, the bottom line is this:-  Unless your version of Zoneminder has moved on sufficiently from mine to support v4l2 natively, you WILL need to use mjpg_streamer if your webcam is v4l2 compliant.  Look at it this way...  Your webcam speaks v4l2, but Zoneminder doesn't.  They need a translator so that Zoneminder can understand what it sees from your webcam.  Mjpg_streamer (google for it) provides that translation.  It turns the pictures coming out of the webcam into something Zoneminder can understand.

I suspect Skype natively supports v4l2 webcams.  That's probably why your Quickcam Pro works on Skype.  Your version of Zoneminder probably doesn't natively support v4l2, so it won't see your webcam, even though it works on Skype.

On the subject of contrast, my understanding is that most webcams won't work in full daylight - they just get washed-out as you describe.  However, the Logitech Quickcam Pro 9000 seems to be OK - and it does it all by itself.  No adjustment is needed anywhere.  It works fine in daylight and it works really very well in the dark with nothing but a streetlight.

Sorry I can't give you all the details, but if you're not using mjpg_streamer that's highly likely to be the reason it's not all working.

One other thing.  This may just be a quirk of the version I'm using, but I find that every time I start mjpg_streamer and browse my webcam with firefox, I need to first disable and then re-enable the webcam on the Zoneminder function menu before it will work.  This may have been fixed in your version.

Hope this helps.

Mike

---

### Post by Paddo on 2009-10-15
Thanks Midahed, your posts have been very helpful.

I'm trying to set up zoneminder on Jaunty and have installed mjpg-streamer as you did but...

> **Midahed said:**
> 
Having got to that point it was fairly easy to set-up the webcam in Zoneminder and get it working properly.


I can't figure out how to set up zoneminder to use the video stream. I can see the video stream with Firefox but where zoneminder (1.23.3) asks for host, port and path I get stuck. I enter localhost and the port (8080) but I don't know what to use for the Remote Host Path. Firefox shows the path as [http://localhost:8080/?action=stream](http://localhost:8080/?action=stream) and nothing I've tried works in the path.

Can you help me here?

---

### Post by phredduk on 2009-10-30
Hey Paddo -

You have probably figured it out by now, but you need to use the following for Remote Host Path:

```
/?action=stream
```

If that doesn't get it running, try reducing the resolution (say 320x240) and decrease the FPS values under the General tab... have a play around with various combinations

Good luck :)

---

### Post by MikePelley on 2009-11-26
Just a note - it appears that this workaround is no longer required as of Zoneminder 1.24 (see [http://www.zoneminder.com/wiki/index.php/Uvc](http://www.zoneminder.com/wiki/index.php/Uvc)).  My system was still "Jaunty", and the standard Ubuntu repository had 1.23.something.  For "Karmic", the repository has a version of 1.24.something, so I'm expecting it to work out of the box.

Mike.

---

