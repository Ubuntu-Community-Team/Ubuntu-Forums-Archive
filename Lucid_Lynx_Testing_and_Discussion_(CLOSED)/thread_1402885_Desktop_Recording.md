---
title: "Desktop Recording"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mrdoob on 2010-02-09
Hello,

Since I moved to Ubuntu/Linux one of my frustrations is the lack of a decent screen recorder.

I was *very* impressed with gtk-recordMyDesktop for video-only, but no matter how much I tried there was no way to make the app to also record audio.

I guess I shouldn't have to mention how useful having a easy to use app for recording the desktop is. Think about all the people that would use it to create tutorials and upload to youtube. Think of all the people that will realise that Ubuntu/Linux is worth it thanks to these videos.

I wonder if there is any intention of having such app for Lucid default install? Or is there already a working app for that?

Thanks!

---

### Post by phenest on 2010-02-09
Here's a command line way: [Proper Screencasting on Linux]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by mrdoob on 2010-02-09
I guess that's a start. Thanks for pointing me to that post.

An app with a single button that did all these steps for the user would be something desirable tho.

---

### Post by Toadinator on 2010-02-09
There's something (I'm not sure if it's installed by default) called the pulse audio device chooser that puts an icon in the notification area. Left-click it, and select volume control. With record-my-desktop open, go to the "recording" tab on the volume control window, and change record-my-desktop to "Monitor of Internal Audio *something*" (I forget if you have to do it while it's recording or not). Don't close the volume control window, by the way.

Sorry for not being exactly clear, but I hope I helped!

---

### Post by mrdoob on 2010-02-10
Insteresting app! However, I couldn't get the gtk-recordMyDesktop app to appear on it.

Oh well... Maybe in Lucid+1...

---

### Post by tad1073 on 2010-02-11
VLC has screen recording capabilities.

open vlc>media>open capture device>select desktop from "Capture Mode"
Next to the play button is a drop down arrow, click that a select convert.

From there you can select audio/video type, file destination etc.

---

### Post by gjoellee on 2010-02-11
> **mrdoob said:**
> Hello,

Since I moved to Ubuntu/Linux one of my frustrations is the lack of a decent screen recorder.

I was *very* impressed with gtk-recordMyDesktop for video-only, but no matter how much I tried there was no way to make the app to also record audio.

I guess I shouldn't have to mention how useful having a easy to use app for recording the desktop is. Think about all the people that would use it to create tutorials and upload to youtube. Think of all the people that will realise that Ubuntu/Linux is worth it thanks to these videos.

I wonder if there is any intention of having such app for Lucid default install? Or is there already a working app for that?

Thanks!
 
I did a video once, and I just played music in Rythmbox, and I got sound in the video.

---

### Post by todak on 2010-02-11
Istanbul is another app that will record desktop video with sound. It is in the repos. When you start it, an indicator will appear in the tray. Right click on the indicator and you will be presented with a list of options, one of them being "Record Sound".

---

### Post by emarkay on 2010-02-12
What about XVidCap?  That worked for me a while ago - I haven't tested it in Lucid, though.

---

### Post by alfonz19 on 2010-02-12
Hi, I'm also currently looking for program capable of doing this. I've just tried every mentioned program and here are the results for ubuntu 9.10 64b with turned off compiz (if it matters):

gtk-recordMyDesktop: did something, mencoder was processing something, when I ran it, but there is no video when I try to wath what I've recorded.

istanbul: crashes when saving.

XVidCap: first one which recorded video. And audio also, but that audio was some random data comming I do not know where from. But my ears hurts.

EDIT: but maybe xvidcap just attached himself to wrong audio device: how do I find the right one to be able to specify it for xvidcap?

---

### Post by tad1073 on 2010-02-12
xvidcap works for me, but I have no sound with it

---

