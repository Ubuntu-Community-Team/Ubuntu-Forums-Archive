---
title: "Small fonts in Jaunty"
date: 2009-03-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-03-08
Running Jaunty with a resolution of 1280 x 1024 as I did in Intrepid. The font size is now very small, the icon size seems to be the same than before. Tried to change the font size in System - Preferences - Appearance - Font but it has no affect on the desktop and in programs.

Where can I change?

Upgrade was very successful, only SCIM disappears, maybe only needs reinstalling.

Michael

---

### Post by DougieFresh4U on 2009-03-08
> **Yumi said:**
> Running Jaunty with a resolution of 1280 x 1024 as I did in Intrepid. The font size is now very small, the icon size seems to be the same than before. Tried to change the font size in System - Preferences - Appearance - Font but it has no affect on the desktop and in programs.

Where can I change?

Upgrade was very successful, only SCIM disappears, maybe only needs reinstalling.

Michael
I can open Firefox (or what ever browser you use) go to Edit>Preferences>Content, or Tools>Options>Content,  and I make Font adjustments there, but I also UNCHECK the box that says 'Allow pages to use there own font'
Good luck

---

### Post by Yumi on 2009-03-09
Sorry, works as out of the box. I used the font settings and believed that 11 pt. size would be enough, but is also too small. Now I have it on 15 pts and it is ok.

Michael

---

### Post by kansasnoob on 2009-03-09
Actually this is a known "issue".

> Font size optimization

Font dot-per-inch settings are now optimized based on your monitor's capabilities, rather than defaulting to 96 dpi. You can further customize your dpi settings via System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details... 

[http://www.ubuntu.com/testing/jaunty/alpha5#Font%20size%20optimization](http://www.ubuntu.com/testing/jaunty/alpha5#Font%20size%20optimization)

Changing individual font sizes did not produce the desired results for me so I just changed the dpi as described above until I got what I liked with the default font sizes.

---

### Post by calc on 2009-03-09
> **kansasnoob said:**
> Actually this is a known "issue".



[http://www.ubuntu.com/testing/jaunty/alpha5#Font%20size%20optimization](http://www.ubuntu.com/testing/jaunty/alpha5#Font%20size%20optimization)

Changing individual font sizes did not produce the desired results for me so I just changed the dpi as described above until I got what I liked with the default font sizes.

Changing the font size should work in most cases if you know what to change them to, but you need to make sure the DPI setting is set correctly for your screen first.

Then you can do (Fake DPI 96)/(Real DPI)*(Font Size)

Eg a font that is 10pt on a monitor that is actually 147 DPI would have gotten much bigger when Ubuntu realized the screen was 147 DPI instead of 96 DPI. To make it the same size as before you would need (96)/(147)*10 = 7.8pt font. For cases where your DPI is actually less than 96 DPI your fonts would have gotten smaller, but you use the same formula to calculate what to change the font sizes to.

Note: 72pt == 1 inch, but since all monitors had been hard coded to a fake 96 dpi this didn't actually work, which was why among other things 100% setting in OpenOffice.org wasn't the size of your actual printed page.

--

This is how to determine what DPI is correct for your screen. In most cases Xorg will determine this automatically. In cases where it doesn't, it usually doesn't know the size of your screen, you need to use the size of your screen, the resolution, and the aspect ratio.

Eg: Laptop 15.4" 1920x1200 (16:10 Aspect Ratio)

sqrt(16^10+10^2) = 18.87

Width = 15.4 in. * (16/18.87) = 13.06 in.
Height = 15.4 in. * (10/18.87) = 8.16 in.

Horizontal DPI = 1920 pixels / 13.06 in. = 147.0 dpi
Vertical DPI = 1200 pixels / 8.16 in. = 147.1 dpi

In almost all cases Horizontal/Vertical DPI will match.

--

You can also workaround Xorg not knowing what size your screen is by using this line in your xorg.conf. As long as Xorg knows your screen size or you hardcode it, then it will do the DPI calculation for you automatically:

DisplaySize  width height

Note: The size is in millimeters.

---

### Post by garba on 2009-03-09
thanks calc for bringing up the "fakeDPI" thing, this might prove that this post of mine was not so pointless after all ;)

[http://ubuntuforums.org/showthread.php?t=1082053](http://ubuntuforums.org/showthread.php?t=1082053)

I think people should be educated about what DPI actually means: that setting in the font preferences dialog is not meant to make fonts "bigger or smaller" but as a hint to render them in their "actual size" should the xserver not detect your screen size correctly... btw why not provide some info about the size of your screen as detected by the X server and the resulting dpi?

---

### Post by Yumi on 2009-03-10
Well, I am unable to understand all of what has been said above. However, I am willing to post any data I can find, but you have to tell me how to retrieve them.

Followed the link from kansasnoob and there is a known issue with large fonts. I read through the workaround and it seems to centre on EDID.

My /var/log/Xorg.0.log tells me that Jaunty is not receiving a EDID signal from my Monitor (Samsung SyncMaster 171s).

I put the line "DisplaySize 337.2 x 270.336" into xorg.conf as Calc suggested. Am not sure about the effects as I twittled the font settings before.

Am fairly happy with the results at the moment with various states. Thunderbird is still showing small fonts in its list of mails, but the program font is normal.

Michael

---

### Post by calc on 2009-03-17
> **Yumi said:**
> Well, I am unable to understand all of what has been said above. However, I am willing to post any data I can find, but you have to tell me how to retrieve them.

Followed the link from kansasnoob and there is a known issue with large fonts. I read through the workaround and it seems to centre on EDID.

My /var/log/Xorg.0.log tells me that Jaunty is not receiving a EDID signal from my Monitor (Samsung SyncMaster 171s).

I put the line "DisplaySize 337.2 x 270.336" into xorg.conf as Calc suggested. Am not sure about the effects as I twittled the font settings before.

Am fairly happy with the results at the moment with various states. Thunderbird is still showing small fonts in its list of mails, but the program font is normal.

Michael

An easy way to see if your DPI setting is close to accurate is to set OpenOffice.org view to 100% and then hold a sheet of paper up to your monitor. It should be identical in width as long as it is the same type of paper (eg Letter or A4).

And to verify that Xorg thinks your screen is what you set it to run in a console window:

xdpyinfo | grep ^screen -A2

Which shows this for me:

ccheney@x200:~$ xdpyinfo | grep ^screen -A2
screen #0:
  dimensions:    1280x800 pixels (261x163 millimeters)
  resolution:    125x125 dots per inch

---

### Post by Gourgi on 2009-03-17
```
xdpyinfo | grep ^screen -A2
screen #0:
  dimensions:    1680x1050 pixels (490x321 millimeters)
  resolution:    87x83 dots per inch

```
so what is the correct value for me?
87 , 83 or 85 ?

---

### Post by calc on 2009-03-20
> **Gourgi said:**
> ```
xdpyinfo | grep ^screen -A2
screen #0:
  dimensions:    1680x1050 pixels (490x321 millimeters)
  resolution:    87x83 dots per inch

```
so what is the correct value for me?
87 , 83 or 85 ?

None of the above, its both 87 and 83 but for horizontal vs vertical DPI. For some reason even though your monitor is 16:10 aspect ratio the panel is reporting it is not actually 16:10 physically, which means its either reporting the information incorrectly or they made a screwy panel. It should be something like 490x306 or 513x321, not 490x321

---

### Post by Yumi on 2009-03-20
Thank you Calc, this is becoming an interesting lesson to follow.

```
xdpyinfo | grep ^screen -A2
screen #0:
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

```

Reporting the dimensions of the panel correctly. 

But your trick with openoffice, set to 100% shows the page smaller than the actual A4 paper. A real A4 page is 21cm wide, the on screen page is 16cm wide.

Maybe I have to increase the resolution from 96 dots/inch. I have read that DPI for this model is 98.

Michael

---

### Post by Yumi on 2009-03-20
Found an interesting notice here [http://www.ubuntu.com/testing/jaunty/alpha6]("http://www.ubuntu.com/testing/jaunty/alpha6")

It states under "New Features in Jaunty" that:
> Font size optimization

Font dot-per-inch settings are now optimized based on your monitor's capabilities, rather than defaulting to 96 dpi. You can further customize your dpi settings via System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details...  

It cerainly changed the appearence, as it was set to 71DPI where the monitor is 98DPI.

Now the A4 paper and monitor page are the same.

Learned something.

Michael

---

### Post by lean on 2009-03-21
What if you have multiple monitors? Can you set individual DPI for each monitor?

---

### Post by rudenko_ruslan on 2009-03-21
Just one short question about command "xdpyinfo | grep ^screen -A2":
> screen #0:
  dimensions:    1280x1024 pixels (342x271 millimeters)
  resolution:    95x96 dots per inch
9**5**x96 - is that OK?

---

### Post by Copernicus1234 on 2009-03-22
> screen #0:
  dimensions:    1920x1200 pixels (524x331 millimeters)
  resolution:    93x92 dots per inch

93x92 here...

---

### Post by jerrylamos on 2009-03-24
Quote:
Font size optimization

Font dot-per-inch settings are now optimized based on your monitor's capabilities, rather than defaulting to 96 dpi. You can further customize your dpi settings via System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details... 

Thanks for the hint.  My problem was over a few minutes more and more font letters getting blotches on them so the character was unreadable.  Went into Details and clicked "smoothing none".  Now I can read the characters again,

IBM Thinkpad R31, i830 VGA, jaunty 2.6.8-11

Jerry

---

