---
title: "Change your Xsplash and GDM images"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-09-27
To set the xsplash image to one of your choice you need to pick your image and scale it to fit your monitor.
 

 The image that is used is in /usr/share/images/xsplash.  The name of the file is “bg_1440x900.jpg”.   That is the file for my box.  The one you need is the one with your screen resolution in the name.
 

 When you go to that file I would rename the old file (bg_1440x900a.jpg) and pull it up on gimp along with your image.
 

 Click above on “image” on the top bar of the bg_1440x900a.jpg file and then click on “scale image” in the ensuing menu.  Do the same for your image.  Compare the two.
 

 You have “hieght/width” and “x/y resolution”.  Make sure that they are using the same measuring standard and that they match.  If they don't your image will interfer with the Ubuntu logo that appears on the xsplash image and you will get your image with a large white box on it, probably in the upper left hand corner, when you boot.
 

 Save your image to the file with the name “bg_<your resolution>.jpg.
 

 For your GDM you need a .png version of your image.  Got to you /usr/share/backgrounds file and rename the image “warty-final-ubuntu.png” to  “warty-final-ubuntu1.png”.  Put your image in the folder and rename to “warty-final-ubuntu.png”.
 

 You are now done.  You have your xplash image and your gdm image.
 

 If you have trouble with, or do not want, the Ubuntu logo in the middle of your  xsplash image, you will need to go to /usr/bin/xsplash and change the permissions of that file to be not executable.  This will just stop the logo.
 

 I want to mess with the logo image and change the text to label what 9.10 I am booting to.  Ah another toy that I need to find time for.

---

### Post by Longinus00 on 2009-09-28
I've created scripts for modifying xsplash in these posts.

[http://ubuntuforums.org/showpost.php?p=7973329&postcount=54](http://ubuntuforums.org/showpost.php?p=7973329&postcount=54) xsplash background

[http://ubuntuforums.org/showpost.php?p=7973498&postcount=58](http://ubuntuforums.org/showpost.php?p=7973498&postcount=58) logo & throbber color, also has some previews

It's not actually super important that you backup the xsplash images because if you reinstall the ubuntu-xsplash-artwork package it should set it all back to default.

> **ranch hand said:**
> 
 For your GDM you need a .png version of your image.


This is untrue. It only needs to have the filename you specify, the extension is png only for backwards compatibility.
[http://ubuntuforums.org/showpost.php?p=8004714&postcount=151](http://ubuntuforums.org/showpost.php?p=8004714&postcount=151)

If you want to change the background without overwriting the file warty-final-ubuntu.png do this (you can always get it back by reinstalling ubuntu-wallpapers)
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /path/to/newimage.ext
```

---

### Post by ranch hand on 2009-09-28
I just subscribed to that thread.  Thanks, looks neat.

I do not use scripts for tasks like this often.  I am a noob and can't write scripts although I certainly intend to learn.  This means that reading them is a little tough.

I know, I use scripts  every time I use grub2.  Call me weird.

I will however be keeping it for use when I do learn a little more.

Thanks a bunch for your generousity, and scripts.

---

### Post by tad1073 on 2009-09-28
> **Longinus00 said:**
> I've created scripts for modifying xsplash in these posts.

[http://ubuntuforums.org/showpost.php?p=7973329&postcount=54](http://ubuntuforums.org/showpost.php?p=7973329&postcount=54) xsplash background

[http://ubuntuforums.org/showpost.php?p=7973498&postcount=58](http://ubuntuforums.org/showpost.php?p=7973498&postcount=58) logo & throbber color, also has some previews

It's not actually super important that you backup the xsplash images because if you reinstall the ubuntu-xsplash-artwork package it should set it all back to default.



This is untrue. It only needs to have the filename you specify, the extension is png only for backwards compatibility.
[http://ubuntuforums.org/showpost.php?p=8004714&postcount=151](http://ubuntuforums.org/showpost.php?p=8004714&postcount=151)

If you want to change the background without overwriting the file warty-final-ubuntu.png do this (you can always get it back by reinstalling ubuntu-wallpapers)
```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /path/to/newimage.ext
```

There is some thing wrong with that script, I get errors when I run it on an image. 

When I:
```
sudo sh ./xsplashimageconverter ~/Desktop/warty-final-ubuntu.png
```

```
./xsplashimageconverter: 3: Syntax error: "(" unexpected
```

---

### Post by Longinus00 on 2009-09-28
> **tad1073 said:**
> There is some thing wrong with that script, I get errors when I run it on an image. 

When I:
```
sudo sh ./xsplashimageconverter ~/Desktop/warty-final-ubuntu.png
```

```
./xsplashimageconverter: 3: Syntax error: "(" unexpected
```

That's because you're trying to use dash to run the script. Do this instead.

```
sudo ./xsplashimageconverter ~/Desktop/warty-final-ubuntu.png
```

---

### Post by tad1073 on 2009-09-28
> **Longinus00 said:**
> That's because you're trying to use dash to run the script. Do this instead.

```
sudo ./xsplashimageconverter ~/Desktop/warty-final-ubuntu.png
```

Thanks, guess it was a "BTCKB" or "id10t" error...lol:lolflag:

---

### Post by tawmas on 2009-09-28
This is quite cool, but I have a little problem. I don't have a file named after my screen resolution (this is a 1024x600 netbook screen)... So, what file is actually used?

I tried to bypass the problem by using the conversion script linked above, but it crops the background in a different way than the GDM/Gnome background, so I'd prefer to have a try at it manually.

---

### Post by NCLI on 2009-09-28
I also have this problem on my netbook, with a resolution of 1366x768. There must be some way to find the correct file.

---

### Post by ranch hand on 2009-09-28
> **tawmas said:**
> This is quite cool, but I have a little problem. I don't have a file named after my screen resolution (this is a 1024x600 netbook screen)... So, what file is actually used?

I tried to bypass the problem by using the conversion script linked above, but it crops the background in a different way than the GDM/Gnome background, so I'd prefer to have a try at it manually.
What is in your /usr/share/images/xsplash file?

There should be 3 types of files.  If you have a "bg whatever.jpg" that would be the background.  There should be some file for the logo.  There should be something for the throbber.

Look at the buggers in Image Viewer and see what they look like if nothing else.

I have never even seen a netbook so I have no idea what the file system looks like.

---

### Post by tawmas on 2009-09-28
> **ranch hand said:**
> What is in your /usr/share/images/xsplash file?

There should be 3 types of files.  If you have a "bg whatever.jpg" that would be the background.  There should be some file for the logo.  There should be something for the throbber.

Look at the buggers in Image Viewer and see what they look like if nothing else.

I have never even seen a netbook so I have no idea what the file system looks like.

Well, it's just a plain notebook with a silly screen resolution, really!

I have the same files you have... which means no bg_* file is matching my resolution, so I don't know which one is picked by xsplash.

---

### Post by ranch hand on 2009-09-28
> **tawmas said:**
> Well, it's just a plain notebook with a silly screen resolution, really!

I have the same files you have... which means no bg_* file is matching my resolution, so I don't know which one is picked by xsplash.
How many "bg" files do you have?

---

### Post by Longinus00 on 2009-09-28
> **tawmas said:**
> This is quite cool, but I have a little problem. I don't have a file named after my screen resolution (this is a 1024x600 netbook screen)... So, what file is actually used?

I tried to bypass the problem by using the conversion script linked above, but it crops the background in a different way than the GDM/Gnome background, so I'd prefer to have a try at it manually.

> **NCLI said:**
> I also have this problem on my netbook, with a resolution of 1366x768. There must be some way to find the correct file.

Just use the script I posted and don't worry about it.

If you're still curious, the exact logic in xsplash.c is in the function get_background_filename.
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L316](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L316)
*I'm pretty sure there is a bug in that function.

---

### Post by tawmas on 2009-09-28
> **ranch hand said:**
> How many "bg" files do you have?

Quite a bunch! I have 800x600, 1024x768, 1280x1024, 1440x900, 1680x1050, 1920x1200 and 2560x1600.

My native resolution is 1024x600.

---

### Post by zoomy942 on 2009-09-28
subscribed.  im gonna do this later tonite

---

### Post by tawmas on 2009-09-28
> **Longinus00 said:**
> If you're still curious, the exact logic in xsplash.c is in the function get_background_filename.
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L316](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L316)
*I'm pretty sure there is a bug in that function.

If I can still read C, it's picking the smallest resolution whose width is larger than the screen width... So for my case it would pick 1280x1024...

I agree it seems weird. :-)

I'll try that. Is the image aligned to the top left corner of the screen?

---

### Post by ranch hand on 2009-09-28
> **tawmas said:**
> Quite a bunch! I have 800x600, 1024x768, 1280x1024, 1440x900, 1680x1050, 1920x1200 and 2560x1600.

My native resolution is 1024x600.
I would rename the bg_1024x768.jpg to bg_1024x768a.jpg and reboot.  This should resupt in one of the following - a black screen - no change - an image that is noticably different.

If you get no change then just keep trying the buggers by changing their names until you get some change.  I bet that is the one being used though.

If you use an image that can hang over your screen a little without hurting the way it looks I would stick with an image the same size as what your box is using.

If you want the whole image just edit one in gimp to fit your screen and then if you haveto you can kill the logo.

---

### Post by tawmas on 2009-09-28
> **ranch hand said:**
> I would rename the bg_1024x768.jpg to bg_1024x768a.jpg and reboot.  This should resupt in one of the following - a black screen - no change - an image that is noticably different.

The 1024x768 was the first one I tried, and it didn't change a thing. I'm now going for the 1280x1024... :-)

EDIT: Bingo!*It **is** the 1280x1024! And it is downsizing the image so that it fits the screen... So I don't know if I'll be able to resize my wallpaper in such a way that it comes out seamless, but at least I can try! Ranch, Longinus, thanks for the help.

---

### Post by Longinus00 on 2009-09-28
> **tawmas said:**
> If I can still read C, it's picking the smallest resolution whose width is larger than the screen width... So for my case it would pick 1280x1024...

I agree it seems weird. :-)

I'll try that. Is the image aligned to the top left corner of the screen?

I'm pretty sure the image is centered as per this function 
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424)

I filed a bug about the odd image sizing choice here
[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438406](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438406)

Anyway, just use that script I told you about and don't worry so much. This way, even if you plug in an external monitor or something, it'll always show your pretty background.

---

### Post by tawmas on 2009-09-28
> **Longinus00 said:**
> I'm pretty sure the image is centered as per this function 
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424)

From a quick test, it is aligned to top left and scaled...

---

### Post by Longinus00 on 2009-09-28
> **tawmas said:**
> From a quick test, it is aligned to top left and scaled...

The scaling should make it fill the entire screen right? Which scaling mode is it equivalent to in the desktop background chooser?

---

### Post by kansasnoob on 2009-09-28
Awesome Mr. Hand!

Great work, I also like hammering things into shape!

This is the greatest thing about Ubuntu, great people that want to share what they've learned!

---

### Post by tawmas on 2009-09-28
> **Longinus00 said:**
> The scaling should make it fill the entire screen right? Which scaling mode is it equivalent to in the desktop background chooser?

I can't read the scaling code, I'm sorry, but I can tell you the results of my last test.

I took my background image, which is 2140x1200, and I just renamed it to bg_1280x1024.jpg, without resizing it. What I got is a totally seamless, pixel-perfect transition from xsplash to chooser to gnome background! :-) The background style in Gnome is set to Zoom.

---

### Post by Longinus00 on 2009-09-28
> **tawmas said:**
> I can't read the scaling code, I'm sorry, but I can tell you the results of my last test.

I took my background image, which is 2140x1200, and I just renamed it to bg_1280x1024.jpg, without resizing it. What I got is a totally seamless, pixel-perfect transition from xsplash to chooser to gnome background! :-) The background style in Gnome is set to Zoom.

Zoom puts the image at the center of the screen, not the top left. It preserves the aspect ratio and makes sure the wall paper fills the screen by forcing the smallest side of the wallpaper to match the largest side of your screen. Anyway, you mind setting "affects me too" on the bug I wrote so hopefully somebody will look into the wonky image picker logic? ;)

---

### Post by tawmas on 2009-09-28
> **Longinus00 said:**
> Anyway, you mind setting "affects me too" on the bug I wrote so hopefully somebody will look into the wonky image picker logic? ;)

I actually marked the bug confirmed so that it can be looked upon by a developer.

I'm now heading to bed for the night. Thanks again for your help.

---

### Post by MacUntu on 2009-09-28
Actually
```
return gdk_pixbuf_new_subpixbuf (scaled, x, y, w - x, h - y);
```
seems wrong as the resulting image could be larger than the screen: h - y (w - x) where y (x) is only the half of the difference between the width (height) of the scaled image and your screen width (height). Though I don't know if that results into any visual problems. 

I think it simply should be
```
return gdk_pixbuf_new_subpixbuf (scaled, x, y, width, height);
```
but I can't try that right now.

---

### Post by Longinus00 on 2009-09-28
I was wrong about the image scaling code earlier. The actual code for scaling the image is done in two places. First in scale_to_min
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L298](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L298)
As you can see from line 308-311 it has the same logic as the "zoom" option that I was talking about earlier.

```
factor = MAX (min_width / (double)src_width, min_height / (double)src_height);

new_width = floor (src_width * factor + 0.5);
new_height = floor (src_height * factor + 0.5);
```


The other part of the scaling gets done in get_pixbuf, where it centres and crops the "zoomed" image from before to the screen.
[http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424](http://bazaar.launchpad.net/~xsplash-team/xsplash/trunk/annotate/head%3A/src/xsplash.c#L424)

> **MacUntu said:**
> Actually
```
return gdk_pixbuf_new_subpixbuf (scaled, x, y, w - x, h - y);
```
seems wrong as the resulting image could be larger than the screen: h - y (w - x) where y (x) is only the half of the difference between the width (height) of the scaled image and your screen width (height). Though I don't know if that results into any visual problems. 

I think it simply should be
```
return gdk_pixbuf_new_subpixbuf (scaled, x, y, width, height);
```
but I can't try that right now.

[http://developer.gimp.org/api/2.0/gdk-pixbuf/gdk-pixbuf-creating.html#gdk-pixbuf-new-subpixbuf](http://developer.gimp.org/api/2.0/gdk-pixbuf/gdk-pixbuf-creating.html#gdk-pixbuf-new-subpixbuf)

Actually, come to think of it, you're right, it should be like w-2x or something huh...

These guys really ought to comment their code, sheesh. ;)

---

### Post by MacUntu on 2009-09-28
> **Longinus00 said:**
> Actually, come to think of it, you're right, it should be like w-2x or something huh...

Yes, and w-2x (h-2y) equals to the width (height) of your screen.

Just let it spit out some values:

```
scaled: width=1024, height=819
image: width=1280, height=1024
final: x=0, y=25, w-x=1024, h-y=794, width=1024, height=768
```

My screen is 1024*768, it took the 1280*1024 image (which is your bug because there is a 1024*768 image in /usr/share/images/xsplash), scaled it to 1024*819 and cut out 1024*794. Effect? I don't know but it seems wrong to me, will open a bug report.

---

### Post by Longinus00 on 2009-09-28
> **MacUntu said:**
> Yes, and w-2x (h-2y) equals to the width (height) of your screen.

Just let it spit out some values:

```
scaled: width=1024, height=819
image: width=1280, height=1024
final: x=0, y=25, w-x=1024, h-y=794, width=1024, height=768
```

My screen is 1024*768, it took the 1280*1024 image (which is your bug because there is a 1024*768 image in /usr/share/images/xsplash), scaled it to 1024*819 and cut out 1024*794. Effect? I don't know but it seems wrong to me, will open a bug report.

Have you been able to compile and test changes to xsplash? When I compile xsplash and run it no xsplash comes up.

---

### Post by MacUntu on 2009-09-28
For such tests I always bump the version number in debian/changelog and then do a 'debuild -us -uc' to create the .deb files. I then started Xsplash from the command line - worked fine.

Anyways, here's my bug: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438466](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438466)

---

### Post by Longinus00 on 2009-09-28
> **MacUntu said:**
> For such tests I always bump the version number in debian/changelog and then do a 'debuild -us -uc' to create the .deb files. I then started Xsplash from the command line - worked fine.

Anyways, here's my bug: [https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438466](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438466)

Hmm, I've just compiled it and run it from the directory it's built in. I guess I could install it and then run it but shouldn't it work anyway?

---

### Post by Longinus00 on 2009-09-28
Looks like they're going back to having only one image for the background and just scaling the others from it.

[https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438244](https://bugs.launchpad.net/ubuntu/+source/xsplash/+bug/438244)

This effectively solves the bug of choosing the wrong resolution for your screen.

---

### Post by MacUntu on 2009-09-28
> **Longinus00 said:**
> Hmm, I've just compiled it and run it from the directory it's built in. I guess I could install it and then run it but shouldn't it work anyway?

'sudo ./xsplash' from the src-directory works for me.

> **Longinus00 said:**
> This effectively solves the bug of choosing the wrong resolution for your screen.

And will be the same as "zoomed" - I guess that makes it easier to have the same sized background for Xsplash, GDM, and the session.

---

### Post by Longinus00 on 2009-09-28
> **MacUntu said:**
> 'sudo ./xsplash' from the src-directory works for me.


Yea, that doesn't work for me. Admittedly I'm running in virtualbox but I'm not sure if that changes much. I'll try building it on an copy of karmic actually installed on a computer later and see if that fixes it.

---

### Post by alex88 on 2009-10-14
Does the white ubuntu logo with black background also included in xsplash? i think that can be nice to change also that logo..

---

### Post by ranch hand on 2009-10-14
I believe that is usplash.

---

### Post by alex88 on 2009-10-14
Yeah got it..and changed..thanks anyway..

---

### Post by ranch hand on 2009-10-14
> **alex88 said:**
> Yeah got it..and changed..thanks anyway..
I haven't ever looked at that.

Where did you get it?

I want some more FUN too.

---

### Post by alex88 on 2009-10-15
> **ranch hand said:**
> I haven't ever looked at that.

Where did you get it?

I want some more FUN too.


more fun? yeah.. :guitar:

for changing it i've downloaded a usplash theme source from gnome-look.org, then changed images and source file to compile with my resolutions...then everything worked..
if you need more info just ask... :)

---

### Post by solnyshok on 2009-10-15
yes, please more info. got xsplash and grub screen customized. how I can change the ugly usplash?

---

### Post by alex88 on 2009-10-15
I've created this custom usplash source code to make everyone possible to change usplash, just change the images (remember that the colors have to be indicized and the correct resolution) and run:

```
sudo apt-get install libusplash-dev imagemagick
make
sudo make install
sudo make test #to test
```

---

