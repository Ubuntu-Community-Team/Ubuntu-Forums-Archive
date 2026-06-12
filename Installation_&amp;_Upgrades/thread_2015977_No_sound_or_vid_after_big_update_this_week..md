---
title: "No sound or vid after big update this week."
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by psmattreid on 2012-07-03
Hey, first time here. I've been using Ubuntu for a couple of years now and but I'm having some major problems with a recent update. Earlier this week there was a major update, about 100 mb's worth. After the update. Google Chrome would not launch. Chromium crashes and Firefox won't play video or audio.

Chrome was working perfectly before the update, video and sound played with no trouble.

I thought the trouble might be that I was using Ubuntu 10, so I upgraded to Ubunto 11.10. Didn't fix the issue.

Any help or pointers would be most appreciated.

Thanks!!

Matt

---

### Post by msammels on 2012-07-03
Try this out:

Open your System Settings and navigate to sound. Make sure the output device is set to the correct one (on my system it was set to Digital Output by default). If you're satisfied with these settings and they still don't work, try manual volume editing. Open a terminal window and type:

```
sudo alsamixer
```

---

### Post by psmattreid on 2012-07-04
> **msammels said:**
> Try this out:

Open your System Settings and navigate to sound. Make sure the output device is set to the correct one (on my system it was set to Digital Output by default). If you're satisfied with these settings and they still don't work, try manual volume editing. Open a terminal window and type:

```
sudo alsamixer
```

Thanks for the info. Actually, the problem, more specifically, is that when I try to preview a song in google play, I can click on the triangle icon to start playback, but nothing happens. Before the upgrade songs would launch and play fine. I can hear audio if I'm playing a vid, mp4, using the video player. I just can't get anything, sound or vid, to playback in any browser.

---

