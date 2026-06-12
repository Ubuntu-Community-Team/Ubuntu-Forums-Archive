---
title: "The idea behind 'Ubuntu Restricted Extras'"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by katya_sehgal on 2011-12-05
[B]edit: excuse me if I have posted in the wrong section. kindly move it in the case.
[/B]

Hello,
I am enjoying my stay with Ubuntu thus far. 

I believe that 'Ubuntu Restricted Extras' is an important package to install.

Would it:
1. solve browser based flash problems? (chrome, firefox)

2. take care of 'special characters' problem, when I send a file from Celtx to Final Draft? Example: the dots in the script are converted to a special character in Final Draft. 

Why don't I install and see for myself?
Because thus far there is no problem in watching videos and playing mp3. Plus, I am not sure of how useful these files are:

libavcodec53
libavutil51

synaptic removes these files to install the 'Restricted' package.

A prompt response would be useful so I can go ahead with this. Especially if it solves the 2 problems mentioned above.
Regards.

---

### Post by cbowman57 on 2011-12-05
You won't know if you don't try but the two files you list will be replaced by less restrictive, and probably better,  ones.

---

### Post by katya_sehgal on 2011-12-05
> **cbowman57 said:**
> You won't know if you don't try but the two files you list will be replaced by less restrictive, and probably better,  ones.

Yes, and since it should be simple to uninstall 'Restricted' from Software Centre, I may be in safe hands.

Because I wouldn't like to install without knowing what's happening to the system. Or if it is of any use. Windows had too many unnecessary things.

However, cbowman57, is not the browser flash problem (video chatting) common in Ubuntu? And the 'Restricted' package talks about 'flash'.


> This package depends on some commonly used packages in the Ubuntu multiverse repository.

Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

Please note that this does not install libdvdcss2, and will not let you play encrypted DVDs. For more information, see [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Please also note that packages from multiverse are restricted by copyright or legal issues in some countries. See [http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing) for more information.

---

### Post by katya_sehgal on 2011-12-05
The package has not solved the 'flash' problem. Right-click on a video, choose settings, and the Adobe Flash Window hangs, i.e. you cannot click anything on it or close it.

I shall check for the special characters problem and revert later.

Meanwhile, how do you take care of the Adobe flash issue?

---

### Post by cbowman57 on 2011-12-05
> **katya_sehgal said:**
> The package has not solved the 'flash' problem. Right-click on a video, choose settings, and the Adobe Flash Window hangs, i.e. you cannot click anything on it or close it.

I shall check for the special characters problem and revert later.

Meanwhile, how do you take care of the Adobe flash issue?

That can be affected by a few things, one of which is your video card & drivers.

If your primary use of Flash is for things like Youtube videos you may want to opt in for HTML5 trial [http://www.youtube.com/html5](http://www.youtube.com/html5) , if it works for you it's better than flash.

There is also an app, or maybe it's a browser extension that will play video through a vid player, mplayer I think.  You might also want to consider something like that.

---

### Post by katya_sehgal on 2011-12-05
> **cbowman57 said:**
> That can be affected by a few things, one of which is your video card & drivers.

If your primary use of Flash is for things like Youtube videos you may want to opt in for HTML5 trial [http://www.youtube.com/html5](http://www.youtube.com/html5) , if it works for you it's better than flash.

There is also an app, or maybe it's a browser extension that will play video through a vid player, mplayer I think.  You might also want to consider something like that.

There was no issue with Windows in the same Laptop.

I tried changing 'Global Settings' but to no avail.
This thread shows many others with the same issue.

```
http://forums.adobe.com/thread/24111
```

I thought 'Restricted Extras' could solve this issue.
Do I open a new thread for the Flash problem?

---

### Post by Frogs Hair on 2011-12-05
There are many flash related threads on this forum , so you may want to use the forum search before starting a new thread .

---

### Post by nothingspecial on 2011-12-05
You are fine to open a new thread, or I could change the title of this one if you prefer.

---

### Post by katya_sehgal on 2011-12-06
> **nothingspecial said:**
> You are fine to open a new thread, or I could change the title of this one if you prefer.

Sure nothingspecial. 
Do what is preferable for the board. I am not sure of the advantages of the either options. If you decide to rename this thread, then I would follow it up here. Else let me know.
Shall wait for your change.

---

### Post by nothingspecial on 2011-12-06
New thread here

[http://ubuntuforums.org/showthread.php?t=1891685](http://ubuntuforums.org/showthread.php?t=1891685)

Please add as much detail to it as you can, such as what you have tried so far.

---

