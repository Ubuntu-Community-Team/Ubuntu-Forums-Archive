---
title: "Modify xsplash appearance"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-09-02
Has anyone done so yet? I have the new gdm themed and looking pretty good and would like to get xsplash to match at least the background. According to the most recent release notes:

```
xsplash (0.6-0ubuntu1) karmic; urgency=low

  [ Ken VanDine ]
  * New version (LP: #418974)
    - Don't set xsplash binary setuid gdm, use setuid in xsplash
    - Xsplash flickers and uses the gtk_color_scheme's window background
      color (LP: #416004)
    - Image size popping on login (LP: #411720)
    - xsplash crashed with signal 5 in g_type_create_instance() (LP: #412648)
    - Fixes for the non-compositing case
    - Added configure time argument to allow building with a user to run as
    - Added throbber and logo
    - Added command line arguments to set:
      * background image
      * logo image
      * throbber image
      * number of frames for the throbber
      * pingpong (reverse throbber)
  * debian/rules:
    - Added --with-user=gdm to configure

```

However, I am unable to locate the documentation as to what those command line arguments are. Can anyone enlighten me?

---

### Post by MacUntu on 2009-09-02
Xsplash gets called in /etc/gdm/Init/Default and /etc/gdm/PreSession/Default. Add "-b <path-to-your-background>" to it and it should work. 'xsplash --help' will tell you more about how to add custom throbbers and custom logos.

---

### Post by tekstr1der on 2009-09-02
> **MacUntu said:**
> 'xsplash --help' will tell you more about how to add custom throbbers and custom logos.

Doh! I overlooked the simple solution. I was thinking it was more along the lines of the gdm configuration technique.

This is great. Thanks.

---

### Post by taavikko on 2009-09-02
You have to edit /etc/gdm/PreSession/Default
also to gain consistent use of xsplash.

I wish I were any good at gimp so could make throbber to look nicer.

---

### Post by tekstr1der on 2009-09-02
Yes, I modified both /etc/gdm/PreSession/Default and /etc/gdm/Init/Default to match the background I'm using for gdm and it makes everything look much smoother.

Before this, from bootup I would see usplash, xsplash default curtain, custom gdm background, xsplash default curtain, custom desktop background

Cutting down from 5 image changes to 3 makes the whole process look much less messy. Looking forward to the removal of usplash!

---

### Post by bacardiandwatermelon on 2009-09-02
I noticed on launchpad that the throbber actually has 51 frames... Changing it to 51 frames and adding the ping pong effect makes it look alot smoother. :-)

---

### Post by MacUntu on 2009-09-02
Problem is, that the throbber image's height isn't a multiple of 51. That causes the throbber to move upwards/downwards but don't worry - it will get fixed. :)

---

### Post by Schendje on 2009-09-02
[http://www.youtube.com/watch?v=U9J3ueI4hO4](http://www.youtube.com/watch?v=U9J3ueI4hO4)

It was someone here on the Forums, but I can't remember who exactly.

---

### Post by Darkshade on 2009-09-02
> **Schendje said:**
> [http://www.youtube.com/watch?v=U9J3ueI4hO4](http://www.youtube.com/watch?v=U9J3ueI4hO4)

It was someone here on the Forums, but I can't remember who exactly.

It was MacUntu. The original post is somewhere in [this topic](http://ubuntuforums.org/showthread.php?t=1236727).

---

