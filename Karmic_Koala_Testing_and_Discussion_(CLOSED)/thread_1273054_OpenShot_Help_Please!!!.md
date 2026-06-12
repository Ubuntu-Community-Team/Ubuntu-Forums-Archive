---
title: "OpenShot Help Please!!!"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BAMF1501 on 2009-09-22
ok i open the .dep installer and get this error

---

### Post by af20001 on 2009-09-23
You need to download the Openshot Dependencies .deb from here:

[http://www.openshotvideo.com/2008/04/download.html](http://www.openshotvideo.com/2008/04/download.html)

The Openshot PPA will be announced soon, which will mean these extra dependencies will not be needed.

---

### Post by vinutux on 2009-09-23
Download and install this file too.before install openshot..**[http://launchpad.net/openshot/build-wizard/create-a-build-wizard/+download/dependencies_64_904.tar.gz]("http://launchpad.net/openshot/build-wizard/create-a-build-wizard/+download/dependencies_64_904.tar.gz")**

---

### Post by BAMF1501 on 2009-09-23
i have a 32 bit os and i tried to install the ones for 32 bit but they gave me som eerror ;(

---

### Post by Keyper7 on 2009-09-23
> **BAMF1501 said:**
> i have a 32 bit os and i tried to install the ones for 32 bit but they gave me som eerror ;(

Without more details about this "some error" there's not much we can do to help.

---

### Post by BAMF1501 on 2009-09-23
Here is a screen-grab of the error i get when installing the dependicy files...

---

### Post by Keyper7 on 2009-09-23
Try downloading the dependencies again to make sure the file is not corrupted. Also, it seems you executed the .deb directly from the archive manager. Try extracting it first.

---

### Post by BAMF1501 on 2009-09-23
i tried extracting first and downloaded like 5 times still same error :( will try one more time

---

### Post by Keyper7 on 2009-09-23
From the screenshots it seems you're trying to install in Karmic?

I think the packages support Jaunty at most.

---

### Post by vinutux on 2009-09-23
extracting errors means **[COLOR="Red"]archieve is currupted[/COLOR]**

re-downloaded depedndencies.tar.gz extract and install all dependencies before openshot:)

---

### Post by BAMF1501 on 2009-09-23
all my problems my not detecting cd drive and openshot etc.. all problems were due to 9.10 alpha 6 i reformatted and went back to 9.04 all works fine now :0

---

### Post by Stochastic on 2009-09-23
Moved to Karmic Koala Testing & Discussion.

---

### Post by vinutux on 2009-09-24
ok....so plz mark thead solved under thread tools:)

---

### Post by pappfer on 2009-10-12
I just found this topic. The problem what the topic starter experienced was in Karmic and not in OpenShot. More about it here: [http://ubuntuforums.org/showthread.php?t=1280440](http://ubuntuforums.org/showthread.php?t=1280440)

I have a problem with OpenShot though. It just freezes every time after I open a video / image. My CPU runs very high and OpenShot freezes out. I use 64-bit Karmic version. Any ideas what can cause this?

---

### Post by jukingeo on 2009-10-19
> **pappfer said:**
> I just found this topic. The problem what the topic starter experienced was in Karmic and not in OpenShot. More about it here: [http://ubuntuforums.org/showthread.php?t=1280440](http://ubuntuforums.org/showthread.php?t=1280440)

I have a problem with OpenShot though. It just freezes every time after I open a video / image. My CPU runs very high and OpenShot freezes out. I use 64-bit Karmic version. Any ideas what can cause this?

I had the same problem.

Gnome uses quite a bit of resources...switch to a lighter weight gui such as XFCE or LXDE. Also DO NOT run Firefox at the same time (or anything else for that matter). 

I do have to warn you though that Openshot is still in Beta (or even Alpha) stages. There ARE problems with the program.  I got it to run on my system but I have noticed that the video sometimes 'jumps' when edited and it goes out of sync with the audio. There are a couple of other minor issues, but this one is the biggie.  I tried to edit a video and put it in sync with an audio track and noticed that the cue points for the video shifted and you can physically see the video 'jump'.  Supposedly I have only seen this happen with .flv files and have not tested much outside of these files.  I have heard that sometimes .flv's are difficult for video editors to work with.  I might be forced to convert, which is a pain because most of my video files are .flv's.

But overall Openshot does look like it has promise.  The only other alternatives are Kdenlive IF you are using KDE or dive into the steep learning curve for Cinelerra.  Supposedly Cinelerra is the best and after seeing the features it has, I do have to agree, but it is tough to learn if you just want to do some basic home movie editing.  But if you really want to get into video production and want to make precise edits, that is the way to go.

Hope that helps!

Geo

---

