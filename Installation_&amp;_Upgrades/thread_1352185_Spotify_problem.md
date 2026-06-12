---
title: "Spotify problem"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by Borrot on 2009-12-11
Hello, I've been trying to install Spotify for some days now using "Wine". There's no problem with installing the software(Spotify) but when I run it's not able to play the tracks. I've used the terminal(for the first time ever(wiho)) to check the version of Wine. It says that I've version 1.0.1 and Spotify should be able to run without any problems if you're using v.1.0 or higher.

I really love listening to music and especially when it's free. So please, could you help me?

Btw, can you give me a link to some terminal commands for a beginner? I feel like I need to use it more often.

Thanks in advance and have a nice day,
Borrot

---

### Post by Terrycymru on 2009-12-24
If you haven't already seen it take a look at [http://www.spotify.com/en/help/faq/wine/](http://www.spotify.com/en/help/faq/wine/) . The section headed Troubleshooting may cover your problem.

Start winecfg and make sure your audio works.
$ winecfg

Go to the Audio tab in the program and click on Test Sound. If you hear something, then you are all set, if an error message appears you have to configure it. Make sure the ALSA checkbox is checked and press OK and restart winecfg (it needs to re-initialize sound drivers) and click on Test Sound again. When you hear something you can continue. If you can&#8217;t get sound to work, it is unlikely you will hear anything in Spotify.

---

### Post by fleppmar on 2010-02-18
Hi.

I got audio, but Spotify wont start playing tracks. What ever track i choose.
Does anyone know how to fix this? :)

Regards
fleppmar

---

