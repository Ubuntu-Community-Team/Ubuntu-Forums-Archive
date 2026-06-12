---
title: "No video playback and Firefox crashes after upgrade to Gusty"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by jan on 2007-10-20
Cant play back any avi, mpeg, or wmv videos after upgrade. Seems like I need to reinstall the codecs or what. Also, Firefox turns out to be very unstable - crashed twice per evening without a good reason.

Any hints?

---

### Post by 601 on 2007-10-20
I'm having similar problems after upgrading from feisty to gutsy.
Here are my symptoms:
- video playback is totally messed up: framerate lags and image is either stretched and flipped or not available at all. I have switched through all the available vo modes in Mplayer but to no avail.
- some applications have become very unresponsive. Examples: XMMS, Firefox -> writing text in firefox (in textboxes) hurts - I'm one line ahead than the text being rendered in the window; also scrolling in firefox is jagged. This symptoms show up especially when Visual Effects are set to none and are less annoying (but still perceivable) when visual effetcs are set to normal (in this case, only the annoying scroll delays are visible). 

I also had X crash on me 2-3 times. I think this is mostly a display issue (my display adapter is an ATI Radeon 9800).

I guess my option is a backup and then fresh install of gutsy. I will see if these issues occur then and if they do, I guess I'll just have to stick to feisty

---

### Post by navneeth on 2007-10-20
I think it might be helpful if you post your computers' configurations. I don't have a solution, but it may at least alert those who have the same or similar configs. Thanks.

---

### Post by jan on 2007-10-20
What configuration should i post? When I want to play a video, totem starst and then immideately exits. The same for other video players. XMMS for MP3s works fine though.

---

### Post by phoenixnr on 2007-10-20
Similar problems with my upgrade. Citrix client will hang the pc completely.. Nvidia 6800 video card.

---

### Post by Shaform on 2007-10-21
I can play videos but Firefox crashes on my computer too.
And I found that  the problem is caused by some fonts such as [MingLiU]("http://www.wazu.jp/gallery/views/View_MingLiU.html").
It seems that it is not supported anymore. But I don't know why.
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html
	PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="zh-TW">
<head>
<title>Title</title>
<style type="text/css">
	p {
		font-family: "MingLiU";
	}
</style>
</head>
<body>
	<p>&#28204;&#35430;</p>
</body>
</html>

```

---

### Post by 601 on 2007-10-21
UPDATE: I have managed to reduce the problems to being unable to play videos under mplayer (I noticed Totem Movie player works just fine). XMMS also behaves alright. Another issue would be the delayed scrolling (not that visible but still there) from firefox.

I have however reinstalled ubuntu from scratch and I didn't have any of the issues previously mentioned. I noticed however xgl xserver missing so Desktop effects could not be enabled. After enabling the ATI restricted drivers I have manually enabled composite extension in xorg and installed xserver-xgl. The result was what I have expected: the same as before - under Normal settings firefox showed the usual lag and mplayer stopped working. I reverted the changes and everything went back to normal. 

So, I guess in my case the answer would be the all too often: ATI drivers problems. I'm definitely heading to a computer shop to get an nvidia display adapter as soon as i can.

Those who have such problems and own nvidia adapters may try to install from scratch: it seems it worked in other cases aswell

---

### Post by Bakon Jarser on 2007-10-21
I am working with a clean install of Gutsy and firefox crashed and would not restart after just a couple of hours.  I completely uninstalled it and reinstalled it but it still wouldn't work.  I did another clean install and it crashed again after a couple of hours.  I have now switched to Swiftfox which seems to be working great.

---

