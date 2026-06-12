---
title: "is it possible to run a video on first run?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by chrisw92 on 2010-09-02
So, I'm going to create a clean install of Ubuntu for a "older" family member who is sick of his computer running the way it is. And being a Ubuntu user myself since about 7.04, I recommend it and gave him my copy of the 10.04 live CD... he loved it and wants me to install it for him on his computer once he has backed up his personal files.

Anyway I'm going to wait until 10.10 is released until I do so and I'm wondering is there anyway to get a video file to play the first time the computer is booted (like what happens on a macintosh), for example is there a script or something that will open mplayer playing a file in full screen and then automatically close mplayer once the file has finished playing, on a first boot?

also if it isn't any trouble what is the best way to create a install CD from an your own install? I would like to create a clean install in virtual-box and configure it (including the "script or whatever" from the above question) how I want and then create a install CD from it... I know there are ways to do this but what's the simplest?


p.s. sorry if I posed this in the wrong section (I don't know where questions like this go)

---

### Post by chrisw92 on 2010-09-05
I'm sorry about the double posting but does anybody have any idea how I could do such a thing? (its been 3 days now and its "lost" to all the updated topics)

---

### Post by realzippy on 2010-09-05
Have a look at remastersys;it works great creating a boot/installable
copy of your system.Do not know if it works in vitualbox.

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

[http://www.geekconnection.org/remastersys/index.html](http://www.geekconnection.org/remastersys/index.html)

....a small script/command in Startup applications will start any video you want.

---

### Post by realzippy on 2010-09-07
What kind of video do you want to play at first boot?
(File extension) eg., .avi  . mpeg aso ???

Need a shell script which runs the video and deletes itself when done....

---

### Post by chrisw92 on 2010-09-08
I found out that the command line loads the script fully before anything happens so all I had to do was delete the script file any time in the script (not after the video file has played which is what I thought, hey I didn't know what a shell script was until a few days ago).

I have created something that works by playing a specific file (in a hidden folder so nothing looks messy) within mplayer fullscreen, it closes itself after playing as well automatically.

once I have created my first boot video I will upload it for you all to enjoy, as I plan to make a overview of ubuntu video (for first time users).


oh and file type I haven't decided yet, but it won't matter as long as mplayer can play it. the file I used for testing was the one from the examples folder.

---

