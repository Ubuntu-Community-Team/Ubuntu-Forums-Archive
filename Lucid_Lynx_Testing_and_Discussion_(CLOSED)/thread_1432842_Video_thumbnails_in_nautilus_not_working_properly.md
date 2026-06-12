---
title: "Video thumbnails in nautilus not working properly"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2010-03-18
The icons are not turning into video thumbs anymore but just the regular video icon. I have the preview turned on and for some reason it seems to work if i edit the file name. If I change the view to icon then back to list again the thumbnail returns to the video icon.

---

### Post by PenguinInside on 2010-03-18
What kind of video files are you thumbnailing? Open formats or proprietary?

If the latter, codecs need to be installed in order for thumbnailing to work.

An easy way to do so is to just open the video file in Totem Movie Player. You should be prompted to install codecs. Do so, and then go back to the containing folder in Nautilus.

Please tell the forum how it goes.

---

### Post by andrewabc on 2010-03-18
> **sonicb00m said:**
> The icons are not turning into video thumbs anymore but just the regular video icon. I have the preview turned on and for some reason it seems to work if i edit the file name. If I change the view to icon then back to list again the thumbnail returns to the video icon.

I'm running karmic, and I have the same problem.
Some have video screenshot, others just an icon. And this happens in a group of files that have the same file container. So it has nothing to do with codec. Just seems random.

---

### Post by 23meg on 2010-03-18
Check if the size of the files that aren't thumbnailed is above the threshold that's set in Edit > Preferences > Preview > Other Previewable Files. If so, the behavior is obviously normal.

---

### Post by andrewabc on 2010-03-18
> **23meg said:**
> Check if the size of the files that aren't thumbnailed is below the threshold that's set in Edit > Preferences > Preview > Other Previewable Files. If so, the behavior is obviously normal.

Interestingly the files are all the same size (in most cases).

Example:
I have 10 2.2gb files. The first 9 show vid screenshot. The last one does not. They are .mkv

In Edit > Preferences > Preview > Other Previewable Files
It is set to 10mb. So I shouldn't be seeing any vid screenshots??

Another example, I have 12 550mb videos, first two show vid preview, and rest do not. They are .avi
In another folder I have 12 550mb video file and video preview works for them all. avi

I have vlc installed, and set to default video player for most files.

Seems random to me. Especially since according to my settings, I shouldn't be seeing any video previews at all.

---

### Post by sonicb00m on 2010-03-19
I have all the codecs installed and the videos are way below the preview max size.

As i said before, if i edit the file name the thumb is generated from the video but as soon as refresh or go back it returns to an icon.

---

### Post by 23meg on 2010-03-19
[QUOTE=andrewabc]It is set to 10mb. So I shouldn't be seeing any vid screenshots??[/QUOTE]

Sorry, I mistyped: 

[QUOTE=23meg]Check if the size of the files that aren't thumbnailed is **below** the threshold[/QUOTE]

I meant the opposite, *above*. But yours seems like a codec issue. Doing a bug search at LP and GNOME Bugzilla might help.

---

### Post by zekopeko on 2010-03-19
I'm having the same problem both on Karmic and Lucid.

---

### Post by sonicb00m on 2010-03-20
Reinstall of the Beta has fixed it.

---

### Post by Anduu on 2010-03-20
For future reference....

If you start noticing thumbnailing anomalies try deleting the thumbnail cache in home/username/.thumbnails

As far as I can tell nautilus will only try to thumbnail any particular file only once.That is why simply renaming the file will get you a proper thumbnail.

---

### Post by andrewabc on 2010-03-20
> **Anduu said:**
> For future reference....

If you start noticing thumbnailing anomalies try deleting the thumbnail cache in home/username/.thumbnails

As far as I can tell nautilus will only try to thumbnail any particular file only once.That is why simply renaming the file will get you a proper thumbnail.

Thanks for the tip. renaming gets the thumbnail.

I'll try deleting thumbnail cache in /.thumbnails/vlc/
Looks like I have to restart for it to take effect, but I don't plan on doing that right now.

---

### Post by Anduu on 2010-03-20
> **andrewabc said:**
> Thanks for the tip. renaming gets the thumbnail.

I'll try deleting thumbnail cache in /.thumbnails/vlc/
Looks like I have to restart for it to take effect, but I don't plan on doing that right now.

VLC has nothing to do with the thumbnails nautilus generates.
Just delete the entire .thumbnails folder in your home directory.A restart should not be required.

---

### Post by andrewabc on 2010-03-20
Deleted .cache, still has them cached. I'm still guessing a restart/logout is needed. :)

EDIT:
video files are on another hard drive, not OS SSD. is there .cache on hard drive? EDIT: nope.

---

### Post by Anduu on 2010-03-20
OK one more try....

Go to your home folder in nautilus.
Hit Ctrl-h to show hidden files/folders.
Find the folder called [COLOR="Red"].thumbnails[/COLOR]
Highlight it.
Delete it.

---

### Post by andrewabc on 2010-03-20
> **Anduu said:**
> OK one more try....

Go to your home folder in nautilus.
Hit Ctrl-h to show hidden files/folders.
Find the folder called [COLOR="Red"].thumbnails[/COLOR]
Highlight it.
Delete it.

lol that's what I did. garbage can is empty too.

No .cache folder now.
Renamed a file and now .cache folder   /.cache/vlc/cachedir.tag and plugins-04041e.dat  were created.

Maybe those deleted files are in ram or cache and that's why not reset?

---

### Post by Anduu on 2010-03-20
VLC has absolutely nothing to do with nautilus video thumbnails.Those files are irrelevant.

You could try nautilus -q in a terminal to force nautilus to restart.

---

### Post by zekopeko on 2010-03-20
> **Anduu said:**
> OK one more try....

Go to your home folder in nautilus.
Hit Ctrl-h to show hidden files/folders.
Find the folder called [COLOR="Red"].thumbnails[/COLOR]
Highlight it.
Delete it.

This does absolutely nothing on my install. Renaming afterwards does nothing. The "I'm creating the thumbnail" icon shows for a split second and then reverts to the icon from the theme.

---

### Post by andrewabc on 2010-03-20
$ nautilus -q

(nautilus:11890): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


Opened my data (media) folder and now nautilus taking forever to show up. Lots of hard disk activity.

Seems to have maybe the trick. Now it's reloading all media files. Although the ones that weren't showing still are not.

My desktop icons and conky are gone though. Going to have to restart. Be back later.

---

### Post by cor2y on 2010-03-20
Your problem is you probably do not have the correct decoders for creating a thumbnail installed.
By default unless told otherwise gnome will use totem to create your thumbnails and totem itself uses gstreamer to decode video so if you dont have correct gstreamer decoders there wont be a thumbnail.
There are two things you can do to fix this.
1) Install all gstreamer decoder libraries (ugly, gstreamer-ffmpeg etc), sometimes this will not work particularly with VC-1 wmv files, if you have the cash get fluendo's gstreamer decoders which WILL work
2) Change the thumbnail generator to something else like mplayer ,  ffmpeg, xine or vlc , there is a tutorial for that on here but like with gstreamer make sure that you have the relevant decoders for mplayer/ffmpeg/xine , mplayer the w32/w64 codecs etc.

Thats how i got mine working around 7.04 and i havent looked back since.

---

### Post by andrewabc on 2010-03-20
> **cor2y said:**
> Your problem is you probably do not have the correct decoders for creating a thumbnail installed.
By default unless told otherwise gnome will use totem to create your thumbnails and totem itself uses gstreamer to decode video so if you dont have correct gstreamer decoders there wont be a thumbnail.
There are two things you can do to fix this.
1) Install all gstreamer decoder libraries (ugly, gstreamer-ffmpeg etc), sometimes this will not work particularly with VC-1 wmv files, if you have the cash get fluendo's gstreamer decoders which WILL work
2) Change the thumbnail generator to something else like mplayer ,  ffmpeg, xine or vlc , there is a tutorial for that on here but like with gstreamer make sure that you have the relevant decoders for mplayer/ffmpeg/xine , mplayer the w32/w64 codecs etc.

Thats how i got mine working around 7.04 and i havent looked back since.

You should reread one of my previous posts where it is randomly displaying thumbnails. This issue for me has nothing to do with codecs. Some work, some do not work (exact same filetype). If I rename a file it shows up, but after I move out of folder and go back in the thumbnail is gone.

Now this is on my karmic 9.10 install. Maybe there is a error/bug that has since been fixed in 10.04. I won't know until I decide to format/install 10.04 which won't be until final version, unless my 9.10 gets more unstable (unrelated problems).

---

### Post by sonicb00m on 2010-03-22
> **andrewabc said:**
> You should reread one of my previous posts where it is randomly displaying thumbnails. This issue for me has nothing to do with codecs. Some work, some do not work (exact same filetype). If I rename a file it shows up, but after I move out of folder and go back in the thumbnail is gone.

Now this is on my karmic 9.10 install. Maybe there is a error/bug that has since been fixed in 10.04. I won't know until I decide to format/install 10.04 which won't be until final version, unless my 9.10 gets more unstable (unrelated problems).

Think that's the problem. people aren't reading what the problem is exactly.

For the record, I had exactly the same issue as you but I have reinstalled Lucid from scratch and the thumbs are working properly. It's not the codecs. I can't comment on the cahce folder since I didn't try it.

---

### Post by jcpeart on 2010-03-26
I have exactly the same problem with thumbnails.  My preferences are set correctly, the gstreamer plugins are all installed (that I know of including good, bad, and ugly), and the codecs are all installed and the videos play in totem.  I am using Lucid Beta and the problem seems worse after doing an update today, (I had not done one since last Sunday).  I have tried deleting the cache, but if anything I ended up with fewer thumbnails.

Jim

---

### Post by LloydSev on 2010-03-28
I am experiencing the exact same behavior under 9.10 Karmic. I watch a lot of TV and I can download files from the exact same release group which using the exact same codecs, and some of them show a thumbnail and most don't. However when I delete them from the drive, they ALL show a thumbnail in the trash folder.

---

### Post by LloydSev on 2010-03-28
> **Anduu said:**
> For future reference....

If you start noticing thumbnailing anomalies try deleting the thumbnail cache in home/username/.thumbnails

As far as I can tell nautilus will only try to thumbnail any particular file only once.That is why simply renaming the file will get you a proper thumbnail.

For what it's worth, deleting all of the PNG files which showed up in two subdirectories of .thumbnails (normal and fail) caused all of my videos to correct the behavior and show all thumbnails.

Thanks.

/home/<user>/.thumbnails/normal and
/home/<user>/.thumbnails/fail

My best guess is that it attempts to generate a thumbnail while the file is being downloaded and fails, and then the behavior persists after the file has been completed. Perhaps I should set my preferences to append to the filename until it finishs which would cause an auto re-name when the file is completed.

---

