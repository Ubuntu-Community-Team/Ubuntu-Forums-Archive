---
title: "flash stopped working after firefox upgrade"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by wonderingwhy on 2012-05-16
I can only just about use Ubuntu and when stuff like this happens I feel almost driven back to a MS OS. 

So I upgraded to Firefox 13 (I was on 3.6) and suddenly youtube stops working or at least intermittently . I tried some fixes via Flash Aid recommended somewhere else and they didn't help.

I'm still on Lucid and don't plan to upgrade to 12.04 until July. I need the most stable version able - I'm a TECHNOPHOBE - let me repeat TECHNOPHOBE!

So is there a straight forward fix, or do I have to spend many hours doing a work around.

Thanks

---

### Post by jadtech on 2012-05-16
have you  done a reboot since the update to firefox ?? also after the reboot check for new updates it is possible now that  you have updated fire fox  there may well be a flash upgrade..

---

### Post by darkod on 2012-05-16
It depends.

If your attitude is "why someone doesn't make this simply work", you will probably spend hours.
If you only want a quick fix, it will take you 5mins.

What I prefer for flash (from the days when 64bit flash was still not installing properly back in 2009), is not to use any solution from the repositories. Remove anything you might have installed trying to make flash work.

Go to the adobe.com website and download flash for inux, it will be a .tar.gz compressed archive. Extract it where ever you want in your Home folder.

While in Home, press Ctrl + H to display the hidden folders. Notice the .mozilla folder. Open it and create a folder named plugins inside.

Then, from the extracted flash, copy only the libflashplayer.so library into the created /Home/.mozilla/plugins folder.

Open your browser (or close and open it if it was open during the operation), and that's it.

As long as you have that file in that folder, it doesn't matter how many times firefox gets updated, or ubuntu.

I use a separate /home partition which stays the same when I do a clean install of ubuntu with a new version, and flash has worked without touching it since 9.10.

---

### Post by wonderingwhy on 2012-05-17
Hey Chaps

Thanks so much Darkod for the fix - I wish I'd met you back when I had my very first prob with flash. It worked a treat.

[COLOR="Red"]I did have to down grade flash from 11.2.202.235 the current version to 10.0.15 my previous version.  With 11.2 it was all very choppy and jerky.[/COLOR]

But with your fix I knew where to put the file - so thanks again.

Oh and you are so right - I do just want it to work out the box - most of what I read on the forums is gobbledygook. I started using Ubuntu about 4 years ago because I was told Ubuntu is the 'user-friendly' version of linux. 

I'm an optimist though - I live in hope that one day MS will be humbled!

---

