---
title: "Skype Video Stopped Working"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dbulante on 2009-03-19
The latest distribution updates must have messed up my Skype video.  Now, it doesn't work.  I can use Cheese Webcam fine, so I assume that it will translate to Skype video usage, but alas.  

Is there any workaround to this?

---

### Post by Toe on 2009-03-19
Which webcam do you use?

Skype video works fine here with a Logitech Quickcam and all the latest Jaunty updates.

You could try booting into an older kernel and test if it works better.

---

### Post by dbulante on 2009-03-20
> **Toe said:**
> Which webcam do you use?

Skype video works fine here with a Logitech Quickcam and all the latest Jaunty updates.

You could try booting into an older kernel and test if it works better.

I tried booting with an older kernel.  That didn't work.  I am using a Logitech high-res webcam.  What's weird is that I can use the webcam in Cheese but not in Skype.

---

### Post by mikebravo on 2009-03-28
Perhaps this will give you a lead:

After complaining about the upgrade from Hardy to Intrepid breaking my webcam, and unsuccessfully trolling the beginners forum for answers, I broadened my search and found a sticky post ( [http://ubuntuforums.org/showpost.php...6&postcount=30](http://ubuntuforums.org/showpost.php...6&postcount=30) ) by spiderbatdad saying try

Code:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
OR
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

and sure enough, I open a terminal, enter either one of those, and my webcam works with skype.

I went on to ask how I could make this automatic and got this answer from pricechild:

right click the 'Applications' menu and choose 'edit menu'. Then navigate to the skype entry and add the command you found(to)the the 'command' box.

That did not work. But, I have half a loaf. Could be this info will help going to Jaunty?

---

### Post by dbulante on 2009-03-30
> **mikebravo said:**
> Perhaps this will give you a lead:

After complaining about the upgrade from Hardy to Intrepid breaking my webcam, and unsuccessfully trolling the beginners forum for answers, I broadened my search and found a sticky post ( [http://ubuntuforums.org/showpost.php...6&postcount=30](http://ubuntuforums.org/showpost.php...6&postcount=30) ) by spiderbatdad saying try

Code:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
OR
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype

and sure enough, I open a terminal, enter either one of those, and my webcam works with skype.

I went on to ask how I could make this automatic and got this answer from pricechild:

right click the 'Applications' menu and choose 'edit menu'. Then navigate to the skype entry and add the command you found(to)the the 'command' box.

That did not work. But, I have half a loaf. Could be this info will help going to Jaunty?

I tried both commands, and it still doesn't work.

What's weird is that the video actually works, but it doesn't show up on my screen.  The other person can see my video, but there's nothing at my end.

---

### Post by tck on 2009-04-04
> **dbulante said:**
> I tried both commands, and it still doesn't work.

What's weird is that the video actually works, but it doesn't show up on my screen.  The other person can see my video, but there's nothing at my end.


this happened to me before, 

stop cam with option whilst viewing there's, the inview one if you know what i mean and start it again (don't disconnect the skype call)

---

### Post by dbulante on 2009-04-04
> **tck said:**
> this happened to me before, 

stop cam with option whilst viewing there's, the inview one if you know what i mean and start it again (don't disconnect the skype call)

Another problem I have is that the other person's video does not show up on my screen.  When I do the test video under Preferences, it just shows a black screen.

---

### Post by nystire on 2009-04-04
I have a slightly different problem. If I try either of those 2 commands, I get video - albeit a tad "dulled out" in the video test page. If I just run Skype, I get coloured bars on the test page and Skype crashes when I try to send video.

---

