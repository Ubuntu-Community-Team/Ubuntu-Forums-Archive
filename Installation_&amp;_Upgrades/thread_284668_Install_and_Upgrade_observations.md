---
title: "Install and Upgrade observations"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by wekebu on 2006-10-25
I really would love to install Ubuntu on slightly older computers and give them away to folks who can't afford a new computer.  However, I just can't see Ubuntu as an OS for regular users.  When I first installed Breezy, it took me quite a few hours of reading forums and doing trial & lots of error to get all the media working.  Breezy ran well for a month until I decided to upgrade to Dapper.  So I ordered the Desktop CD through ShipIt -just like I did with Breezy.  Wrong. No documentation says I needed the Alternate CD, I found that in the forums.  Okay, I can't download a file that large; I have Hughes satellite.  Downloading something larger than 146MB is truly out of the question.  I had to ask a friend to download it at their work.  I got the Alternate CD  and went through lots of problems, but finally got the upgrade to work.  I almost gave up and did a fresh install, but I got it to work, with lots of thanks to the forums - again.  How can we expect a regular user to do all this research?

Three suggestions:
-The Ship It area should CLEARLY state that if you are doing an update, you do not want 5 CD's delivered to your door.
-There should be a deliverable Alternate CD.  I'd pay, but I understand the mission statement.  There has to be other people like me, living in remote areas, who only have dial up or limiting satellite.
- There needs to be an easy way to get media to work.  Again, I have read and fully understand why it can't be in the original CD, but this must be solved or Ubuntu will never go mainstream.

-Wendy Kelly Budd

---

### Post by sloggerkhan on 2006-10-26
I agree. An easy way to have regular video/flash playback integrated, including a way to get the "illegal" codecs is needed. Install scripts like automatix are getting somewhere, but they can be a little iffy, and if you have bad internet, pretty much useless. I think this problem helps to show why we need some significant copyright/intellectual property law reform.

---

### Post by Cynical on 2006-10-26
Actually the wmv codec isn't illegal anymore. Microsoft just opened up the spec so they could get manufacturers to use their codec for hd-dvd and bluray discs. So FFmpeg decided to take advantage of that and incorporate it as a native codec. In other words all you need to do is install FFmpeg and have a media player like Mplayer or VLC to take advantage of it. 

Basically install the ffmpeg, mplayer, and realplayer packages if you want to play everything but quicktime media. If thats a necessity then just install w32codecs as well and thats it. You have to search for and select several packages to install. (Tell me, is this much different from downloading a codec pack on windows?)

To be honest, if you can't afford a computer I doubt you could afford a decent internet connection for streaming media in the first place. Also Ubuntu is incredibly easy to use if you just take the time to understand how it works.

Btw the cdrom upgrade spec has already been implemented. I can pop in an edgy desktop iso right now and it will ask me if I want to upgrade my software to the latest release. Give it a whirl and see what you think.

---

### Post by wekebu on 2006-10-26
Cynical,
That's good news about the codec, amazing actually.

Question, please explain "I can pop in an edgy desktop iso right now and it will ask me if I want to upgrade my software to the latest release."  Aren't iso's downloaded? Can this be shipped? Is the upgrade from Dapper to Edgy easier then Breezy to Dapper was?

---

### Post by jdunn on 2006-10-26
Where can I get the w32codecs for edgy?
For Dapper, I used to follow instructions from here:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#w32codecs](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29#w32codecs)
but the w32codecs link isn't working now.

---

### Post by Cynical on 2006-10-27
Yeah it really is amazing. Not sure if ffmpeg is up to date yet but I've read that the vlc package in the repos already plays wmv9.

Hmm, ShipIt still offers dapper for free but edgy iso's cost money apparently.

[http://www.ubuntu.com/products/GetUbuntu](http://www.ubuntu.com/products/GetUbuntu)

The upgrade to edgy was very smooth for me. (I havent tried the cdrom upgrade, but the prompt looked nicely done :D) I ended up reinstalling anyway because I wanted to start using a 64-bit OS again.

---

