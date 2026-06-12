---
title: "&quot;Updated&quot; to 16.04.7  now having issues playing video"
date: 2020-11-07
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-11-07
I am using canned Firefox and having issues playing videos. 
Not so with Google Chrome. 

Not interested in "upgrade" , video issue is NOT a good reason to "upgrade". 

Maybe periodic " experienced internal error" is better reason to "upgrade". 
( Reported so many times it won't pass  my "report" anymore. ) 

Anyway , Firefox is often automatically "updated" but the problem persists.
Mrs Google reports similar history with older Ubuntu versions - so reporting to Firefox seems redundant as results 
of reporting cannot be easy  identified. 

When replying , please concentrate your comments on the following: 

**What are the chances Ubuntu will fix this in 16 ?** 


Cheers

---

### Post by CelticWarrior on 2020-11-07
What kind of videos? And what issues exactly?

---

### Post by helen314 on 2020-11-07
I do not know "what kind"  - last one I tried was "CNN news"  - I get an error basically saying "...it cannot be played..." 
I am not an expert on "playing videos", just a user and all I know it worked in 16.04.6. I am not sure I can "cut and paste" the error, but I will try.
Here it is :


Code: 4 | Message: Something went wrong during native playback.

---

### Post by Impavidus on 2020-11-08
If there's a bug in Ubuntu 16.04 that causes this issue and that bug is properly reported, then it should be fixed. Ubuntu 16.04 is still supported. However, if the problem is caused by faulty/incomplete installation of software on your computer, or if it's caused by 16.04's libraries being too old to support the video format used by that website, it won't be fixed. Note that "it worked in the past" doesn't tell us a lot. The video website may have changed formats.

---

### Post by CelticWarrior on 2020-11-08
Just checked cnn.com and the videos are MP4 (without extension).
On my side it played fine in all browsers but I routinely install additional codecs:
```
sudo apt install ubuntu-restricted-extras
```

I'm not sure it helps but certainly doesn't hurt to try.

---

### Post by helen314 on 2020-11-09
Did 
flashplugin-installer, ttf-mscorefonts-installer.

Got  little nervous observing the process, had to agree to some MS tool.

I no longer get the error on any video, but it seems to take longer to actually start the video.

Then I periodically  get this note that some package couldn't be updated.
Perhaps I will disable automatic updates.

flashplugin-installer, ttf-mscorefonts-installer

---

### Post by helen314 on 2020-11-09
> **Impavidus said:**
> If there's a bug in Ubuntu 16.04 that causes this issue and that bug is properly reported, then it should be fixed. Ubuntu 16.04 is still supported. However, if the problem is caused by faulty/incomplete installation of software on your computer, or if it's caused by 16.04's libraries being too old to support the video format used by that website, it won't be fixed. Note that "it worked in the past" doesn't tell us a lot. The video website may have changed formats.

This issue has been solved, however, as a user I have very little need or desire to 
a. report a bug - been there , done that and it is not a simple affair for a user to "fill out the forms". 
b. with displayed attitude - which I would summarize as " it is somebody else fault" - it tells that "us" have very little desire to find a solution. Irregardless whose fault it is. 

CASE CLOSED 

Cheers

---

