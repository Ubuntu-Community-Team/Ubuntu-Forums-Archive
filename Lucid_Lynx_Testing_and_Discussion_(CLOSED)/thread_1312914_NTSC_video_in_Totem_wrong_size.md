---
title: "NTSC video in Totem wrong size"
date: 2009-11-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-11-03
I'm not sure what project to report this to, but I'm guessing gstreamer and not totem.

When playing an NTSC DVD, the preview window is displayed at 640x480 instead of 720x540 (4:3 display aspect). PAL DVD's are displayed correctly. Totem-xine plays them at the correct size as does mplayer.

---

### Post by phenest on 2009-11-04
In fact, although a PAL DVD plays correctly, if you convert it to say an mp4 and crop the width, then they don't play at the correct size neither. But again, mplayer and totem-xine play them correctly.

This is looking like a gstreamer issue.

---

### Post by phenest on 2009-11-04
Further testing with Kaffeine-gstreamer shows the same problem.

I'll report this as a bug against gstreamer asap.

I can't believe I haven't noticed this before.

---

### Post by phenest on 2009-11-04
Bug reported: [NTSC DVD not played with par applied correctly]("https://bugs.launchpad.net/gst-opencv/+bug/474174")

---

### Post by VertexPusher on 2009-11-04
If the MPEG-2 stream is flagged 4:3 DAR, then 640x480 is the correct size. For 16:9 DAR the correct size would be 853x480.

The format is called "480p" for a reason. Why would 720x540 be more correct in your opinion?

---

### Post by VertexPusher on 2009-11-04
> **phenest said:**
> In fact, although a PAL DVD plays correctly, if you convert it to say an mp4 and crop the width, then they don't play at the correct size neither. But again, mplayer and totem-xine play them correctly.

This is looking like a gstreamer issue.
Note that there may be conflicting AR fields in the container and the stream. For example, if the MP4 header says "1:1" and the MPEG-4 stream says "4:3", there is no way for the media player to tell which one is correct. libavcodec-based players usually give preference to AR signals embedded in the stream while GStreamer looks at the container first. That's why you see different aspect ratios in Totem and MPlayer/Xine. Both are in fact correct. The error happened at the MP4 muxing stage and should be fixed by remuxing.

---

### Post by phenest on 2009-11-04
> **VertexPusher said:**
> If the MPEG-2 stream is flagged 4:3 DAR, then 640x480 is the correct size. For 16:9 DAR the correct size would be 853x480.

The format is called "480p" for a reason. Why would 720x540 be more correct in your opinion?

So your saying that the height must remain constant and that the par only affects width? What would be the purpose in losing some of the pixels hence losing detail? Having a par that increases the size 720x480 to 720x540 loses no detail and is still 4:3 dar.

> **VertexPusher said:**
> Note that there may be conflicting AR fields in the container and the stream. For example, if the MP4 header says "1:1" and the MPEG-4 stream says "4:3", there is no way for the media player to tell which one is correct. libavcodec-based players usually give preference to AR signals embedded in the stream while GStreamer looks at the container first. That's why you see different aspect ratios in Totem and MPlayer/Xine. Both are in fact correct. The error happened at the MP4 muxing stage and should be fixed by remuxing.

That doesn't explain DVD's.

---

### Post by VertexPusher on 2009-11-05
> **phenest said:**
> So your saying that the height must remain constant and that the par only affects width?
NTSC television has 480 visible scanlines. Its horizontal resolution is **undefined** because there are no pixels in analog TV. On DVD it can be 352 (PAR 20:11), 704 (PAR 10:11 or 40:33) or 720 (PAR 10:11 or 40:33). As you can see, 720 and 704 use the same PAR values, i.e. 720x480 is slightly wider than 4:3 or 16:9, with (usually black) bars on the left and right side that don't count as part of the picture. So your proposed solution would actually be wrong.

> What would be the purpose in losing some of the pixels hence losing detail?
Increased sharpness, especially in deinterlaced video. Most 4:3 video on DVDs is original TV footage and therefore interlaced. It has only 240 scanlines per field which have to be converted to 480p in a process called deinterlacing. The result is some degree of blur in the picture, which will be emphasized if you scale the picture beyond 640x480.

I'm not saying that it's wrong to scale the video up or even watch it at fullscreen on a 23inch display. That decision is up to the individual viewer. I'm just saying that opening the video at 640x480 by default is not a bug.

> That doesn't explain DVD's.
I was referring to your example of DVD video that has been converted to MP4. In that case you must make sure that the container and stream aspect ratios don't conflict. This is a non-issue in DVD video because there is no global container header in MPEG-2 program streams (.vob). In fact DVD video can switch aspect ratios at any time during playback.

---

### Post by kixome on 2009-11-05
use vnc instead, is better

---

### Post by phenest on 2009-11-06
> **kixome said:**
> use vnc instead, is better

I take it you meant VLC. VLC does show consistency, so I think this is now my preferred video player.

Still a shame that gstreamer lacks consistency. I've just encoded 2 MPEG-2 files (ripped from DVD, PAL 720x576 @ 25fps 16:15 PAR), and encoded them to MP4 using the exact same encoding method, and both muxed using the same method. Both videos have been cropped to remove the letterbox, one is now 702x380, the other 702x400. Totem plays them as different widths. Go figure.

---

### Post by VertexPusher on 2009-11-06
> **phenest said:**
> I've just encoded 2 MPEG-2 files (ripped from DVD, PAL 720x576 @ 25fps 16:15 PAR)
There is no valid PAL DVD with a PAR of 16:15.

> and encoded them to MP4 using the exact same encoding method, and both muxed using the same method.
Which method?

> Both videos have been cropped to remove the letterbox, one is now 702x380, the other 702x400. Totem plays them as different widths. Go figure.
Please read this bug report carefully:

[https://bugs.launchpad.net/gstreamer/+bug/103038](https://bugs.launchpad.net/gstreamer/+bug/103038)

Prepare to see your bug report marked invalid the same way as this one.

If media players treat aspect ratio differently, it's always because there's a conflict in the file. You have to understand that there are two possibly conflicting ARs in the MP4 container header and in the MPEG-4 video stream *inside* the container, and there is no rule as to which one is to be given priority over the other. The players are free to choose, and Totem just happens to make a different choice, which is no less correct than the other.

The bug is in the file, not in the player.

---

### Post by phenest on 2009-11-06
The video is encoded with x264. Before I have muxed it with the audio, the inconsistency is already there.

But this has nothing to do with the files if other players don't exhibit this behaviour. Also, as you have explained, this is because gstreamer is favouring one ratio over the other (container or stream). If other players don't have this 'issue', then clearly there is a better way to do it. Gstreamer should follow this, as the current behaviour is undesirable. If something is not consistent, then it is a bug.

---

### Post by VertexPusher on 2009-11-06
> **phenest said:**
> But this has nothing to do with the files if other players don't exhibit this behaviour. Also, as you have explained, this is because gstreamer is favouring one ratio over the other (container or stream). If other players don't have this 'issue', then clearly there is a better way to do it. Gstreamer should follow this, as the current behaviour is undesirable. If something is not consistent, then it is a bug.
Good luck finding someone to fix it.

The aspect ratio of the stream is determined by the codec. The aspect ratio of the container is determined by the muxer. One of these goofed up and put a wrong value into the file. Maybe the tools required you to specify aspect ratios manually, so **you** were the one who goofed up. Anyway, for some reason, the wrong value happened to end up where GStreamer looks for it. That's why you think there is a bug in GStreamer.

Now here's what you don't understand:

**Someone else may be using a different codec and a different muxer. In that case the wrong aspect ratio may end up where VLC looks for it, so that the video will show up wrong in VLC but correct in GStreamer.**

Conclusion: This "bug" is unfixable.

If there are conflicting aspect ratios in a video file, there is no way for media players to tell which one is correct. Either choice has a 50% chance of being wrong. If you create video files, you are responsible for making the aspect ratio values match. If you find that difficult, rescale the video to PAR 1:1 and use a container such as AVI which does not have an aspect ratio field.

---

