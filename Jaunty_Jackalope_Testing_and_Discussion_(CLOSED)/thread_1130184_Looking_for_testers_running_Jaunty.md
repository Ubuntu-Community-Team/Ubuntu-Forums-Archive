---
title: "Looking for testers running Jaunty"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Daniel G. Taylor on 2009-04-19
Hey,

I've been working on a desktop transcoder project for a little while and I'm looking for people to help by trying it out. Jaunty is the first release that supports everything needed to run it (GTK+ 2.16, latest GStreamer libraries, etc) which is why I'm posting here. I'd like to work out any bugs for the big Ubuntu release.

It's basically a small app that will take DVD or video files and convert them to various devices like the computer, your iPod, your DVD player, etc. I put up a first release + screenshots on a page here:

[http://programmer-art.org/projects/arista-transcoder](http://programmer-art.org/projects/arista-transcoder)

Make sure you have all the GStreamer plugins installed (including those in Multiverse!) Currently the error handling for missing plugins is near non-existent, but I'm working on it.

I would really appreciate any feedback and/or help others can provide.

By the way, Jaunty seems to be running great. I've been using it for a while now and I'm very happy with it - I think this will be a good release in a few days!

---

### Post by cubeist on 2009-04-19
It looks nice! Although there are programs that already do what yours does...so I am not sure what sets yours apart from existing programs.

I will test it, and I am sure many others will too.


Also, on another note, some of your panoramas rock!  I am a huge pano fan, always experimenting, and if I can offer a tip, the latest stitching algorithms can handle a wide range of light, so I know the common task is to lock your exposure before shooting the pano, but try shooting each shot with its own exposure (using P mode on your camera for example) with lots of overlap, then when stitching in hugin, after creating control points, use celeste to remove cloud points, then stitch, and the final pano will have a perfect exposure without blown bright areas and dark areas...  cheers!

update - edited out the part about sourceforge...nevermind!

---

### Post by olskar on 2009-04-19
> **cubeist said:**
> It looks nice! Although there are programs that already do what yours does...so I am not sure what sets yours apart from existing programs.

I will test it, and I am sure many others will too, but first you need to create a project page on sourceforge or freshmeat or launchpad.


Also, on another note, some of your panoramas rock!  I am a huge pano fan, always experimenting, and if I can offer a tip, the latest stitching algorithms can handle a wide range of light, so I know the common task is to lock your exposure before shooting the pano, but try shooting each shot with its own exposure (using P mode on your camera for example) with lots of overlap, then when stitching in hugin, after creating control points, use celeste to remove cloud points, then stitch, and the final pano will have a perfect exposure without blown bright areas and dark areas...  cheers!

I think this is the best program in this category I've tried :) Clean and simple, gnomish :)

---

### Post by Daniel G. Taylor on 2009-04-20
> **cubeist said:**
> It looks nice! Although there are programs that already do what yours does...so I am not sure what sets yours apart from existing programs.

I will test it, and I am sure many others will too.

Thanks. The general idea about it being different is that it should really fit into the desktop and act like a native GNOME app hopefully following the HIG and using GNOME technologies like GStreamer, GConf, etc. The focus of the application is the end result - that is devices rather than worrying about bitrates and encoder profile features. For people that care about such things I agree that e.g. avidemux is probably better.

The other big difference is that I made it, and honestly it is an experiment to learn more about the various technologies I used, but one that is hopefully useful to others.

> **cubeist said:**
> Also, on another note, some of your panoramas rock!  I am a huge pano fan, always experimenting, and if I can offer a tip, the latest stitching algorithms can handle a wide range of light, so I know the common task is to lock your exposure before shooting the pano, but try shooting each shot with its own exposure (using P mode on your camera for example) with lots of overlap, then when stitching in hugin, after creating control points, use celeste to remove cloud points, then stitch, and the final pano will have a perfect exposure without blown bright areas and dark areas...  cheers!

update - edited out the part about sourceforge...nevermind!

Thanks! I'm slowly getting better at the panorama thing, and Hugin has come a long way from a couple years ago. Thanks for the tip, I'll have to try that. The only panos I've really had exposure troubles with are the really old ones from before shooting full manual. I'll be back in Heidelberg visiting family in a month or two and can hopefully make a better shot of the castle then.

[Edit] I will actually be in Orlando, Portland, and Pittsburgh next month and should get some nice shots there as well. I'll definitely try the auto-exposure blending stuff!

About the version control stuff, I've got the project in a private svn repo at the moment and I'm deciding what service I should use, if any. I've heard a lot about github and such lately. The alternative is to open up my repos and setup Trac or something. I also went ahead and registered on the python package index.

[quote=olskar]I think this is the best program in this category I've tried :D Clean and simple, gnomish :D[/quote]

Thanks! I assume neither of you had issues installing or running the application? Is any part of the UI confusing?

---

### Post by el-mar01 on 2009-04-20
Please provide .deb packages for your excellent program so we can install it easily .. thanks !!

---

### Post by megamania on 2009-04-20
Will it accept a streaming source (i.e. TV card) and convert it to mpeg? In that case, I'd be happy to test it because I'm experimenting with analog-to-digital encoding.

---

### Post by Daniel G. Taylor on 2009-04-20
> **el-mar01 said:**
> Please provide .deb packages for your excellent program so we can install it easily .. thanks !!

Glad you like it. I'm working on reading up on how to make .debs and I've just registered the project on launchpad. It should land in the bazaar repo there soon and I'll try to setup a ppa to do builds of all releases for all architectures so you can apt-get install it.

> **megamania said:**
> Will it accept a streaming source (i.e. TV card) and convert it to mpeg? In that case, I'd be happy to test it because I'm experimenting with analog-to-digital encoding.

Currently it does not, but this is an excellent suggestion. I will investigate automatically discovering V4L devices and try to get it working. I have a webcam and a firewire camcorder that I might be able to test with. I assume the capture card will show up as a similar device and I can use a v4lsource in gstreamer.

If anyone has experience with any of the above I'd love to hear about it.

Thanks for the replies. I'll let you know when the code is available on launchpad so anyone that wants can branch and send patches, open bugs, etc.

---

### Post by KhaaL on 2009-04-20
I'll happily test your app, as soon those debs gets fired up ;-)

---

### Post by hotweiss on 2009-04-20
I just tried converting a XVID video into the Ipod format. The video converted nicely, but the sound is choppy and there's static.

PS-the interface is simple and intuitive

---

### Post by Teamgeist on 2009-04-20
If you need a German translation just let me know! :)

---

### Post by cubeist on 2009-04-20
in my experience, gstreamer is ok, but I think mencoder (with ffmpeg) might do a much better job on the back-end... This might be worth looking into.

Also, if you really want to set this apart from other programs in the class, optimize it for multiple cores... this is something all other video encoders fail to do.

Lastly, for the deb package, it ideally should test for dependencies before installing, such as the right gstreamer packages, and optionally install them from synaptic.

---

### Post by yoasif on 2009-04-20
not to rain on the parade needlessly, but what does this offer that handbrake: [http://handbrake.fr/](http://handbrake.fr/) does not?

several good options are great, but perhaps your time would be better used in improving the gtk gui for handbrake? unless i'm missing the point -- if i am, please say so!

---

### Post by cubeist on 2009-04-20
> **yoasif said:**
> not to rain on the parade needlessly, but what does this offer that handbrake: [http://handbrake.fr/](http://handbrake.fr/) does not?

several good options are great, but perhaps your time would be better used in improving the gtk gui for handbrake? unless i'm missing the point -- if i am, please say so!

Daniel already answered this, as I asked the same thing, see post 4
[http://ubuntuforums.org/showpost.php?p=7105499&postcount=4](http://ubuntuforums.org/showpost.php?p=7105499&postcount=4)

I like reason 2, cause he made it! I have also written software that already exists because sometime things can be done better from scratch than adding to existing programs...

---

### Post by BGFG on 2009-04-20
Look forward to 1.0 This app will probably make everyone's short list very soon :)

---

### Post by Daniel G. Taylor on 2009-04-20
Hey everyone, thanks for the feedback!

While most conversion software does use mencoder and ffmpeg directly I chose to use gstreamer (which coincidentally is using ffmpeg, though I only use two ffmpeg-based elements at this point). I think that gstreamer has been around for a while now and is fairly mature, that it provides a neat pipeline system that is very configurable and lets me easily do stuff like the live preview, and it's incredibly easy to use from python. Aside from that it also seems to be THE multimedia library for GNOME (and KDE through Phonon IIRC). The only real downside IMO is speed in that it is somewhat slower than straight ffmpeg.

As to contributing to Handbrake, I believe there is a very nice GTK GUI for it already and I actually use it to rip my DVDs to H.264. I consider it much more of a power-user program, just like avidemux. I do not think that my goals for this project can be easily realized by modifying the Handbrake GUI, nor do I think it would be as easy to support many different formats as Handbrake is fairly streamlined for just DVD ripping.

About transcoding from tuner cards and such, I just hacked in video4linux support. When you attach video devices they will now show up in the source combo box, and they can be passed to arista-transcode using e.g. v4l2:///dev/video0. Sadly I'm still waiting on the code to land in bazaar in launchpad, but for now anybody that wants to try it can use my svn repo:

svn co svn://programmer-art.org/arista

I've tried it with my built-in iSight and it works beautifully, though you of course get no percentage complete or time remaining and you have to manually remove the job from the queue when you want it to stop recording. I don't have many other devices I can test this with so if anyone runs into issues let me know!

Interesting realization: it's weird seeing yourself in a live video feed in a program you wrote.

[Edit] By the way, any device that supports H.264 is already set to use as many cores as the system has (x264enc threads=0 makes it auto-detect) so the iPod, Computer, and PSP presets should already be using all your cores. The other encoders aren't multithreaded so there isn't much I can easily do about that (and multithreading an encoder is fairly complex and would take me a long time to implement)

---

### Post by Wiebelhaus on 2009-04-20
> **olskar said:**
> I think this is the best program in this category I've tried :) Clean and simple, gnomish :)

I agree , thanks to the OP for all the hard work , it's much appreciated.

Although I'm a bit jealous I don't posses the same skills - lol

Cheers!

---

### Post by qweac on 2009-04-20
This looks awesome! Been looking for something like this for a while... I would really love a PS3/Xbox 360 preset in the future! :)

---

### Post by Daniel G. Taylor on 2009-04-21
Once again thanks for the feedback. The code is now in bazaar without history since I have no clue how long importing the history will take. You can check it out using:

```
bzr branch lp:arista
```

You can create your own branches and push them, then propose they be merged to trunk, or just send me patches, whatever people are comfortable with.

Please file bugs for media files that don't properly transcode on Launchpad, and include the smallest sample possible to reproduce the issue so that I can fix things or push the samples upstream.

I realize GStreamer isn't perfect and we will find bugs, but as we do we are making it better.

Just a warning, I borrowed a PSP from a friend today and the preset doesn't work, but the firmware is quite old. I'll be investigating this more and updating the preset if needed for the latest firmware. I also have several iPods/iPhones and some Nokia smartphones from work to test stuff on and setup presets for. I will also look into a PS3/Xbox 360 preset, but it is difficult to test without having those, so if you own one and are willing to be a guinnea pig message me.

---

