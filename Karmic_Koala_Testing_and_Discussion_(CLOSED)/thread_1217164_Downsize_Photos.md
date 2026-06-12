---
title: "Downsize Photos"
date: 2009-07-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cccc on 2009-07-19
hi

Which program can I use under Ubuntu Karmic to downsize camera photos?

---

### Post by Sef on 2009-07-19
Moved to Karmic Koala subforum.

---

### Post by inportb on 2009-07-19
The GIMP is awesome. Krita works too. Or if you want, you could script it up using PHP/GD, Python/PIL, or Bash/ImageMagick...

---

### Post by qwertyu on 2009-07-19
I recomend you "nautilus-image-converter" you can find it in the repos.

It's completely integrated with gnome, no need to open any program.
Just rightclick the image you want and chose the new size.

I think it should be included by default in Karmic...

---

### Post by aamukahvi on 2009-07-19
Phatch [(install)]("apt://phatch") is a little complex but it gets the job done. You can define various conversion tasks and then run a batch job on selected files.

---

### Post by ranch hand on 2009-07-19
Just use Gimp.

Pull up Gimp.  Pull up your photo.  Click on Image->Scale Image.

---

### Post by knarf on 2009-07-19
On a command line:
```
convert -resample *width***x***height* *inputfile* *outputfile*
```
If this takes to much time use -resize instead of -resample. For more tricks:
```
man convert
```
The *convert* command is part of ImageMagick/GraphicsMagick

---

### Post by el cameleon on 2009-07-19
> **qwertyu said:**
> i recomend you "nautilus-image-converter" you can find it in the repos. +1

---

### Post by afv on 2009-07-19
For multiple images at one folder I use gThumb:
Open one image, Alt+1 (or View > Folders), select the images, Tools > Scale Images… :)

---

### Post by alphacrucis2 on 2009-07-19
> **knarf said:**
> On a command line:
```
convert -resample *width***x***height* *inputfile* *outputfile*
```
If this takes to much time use -resize instead of -resample. For more tricks:
```
man convert
```
The *convert* command is part of ImageMagick/GraphicsMagick


Is the resampling option doing some sort of cubic interpolation like Gimp does?

---

### Post by knarf on 2009-07-20
> **alphacrucis2 said:**
> Is the resampling option doing some sort of cubic interpolation like Gimp does?

As can be [read in the manual]("http://www.imagemagick.org/script/command-line-options.php?#interpolate") you have a wide choice of interpolation methods:
> 
-interpolate *type*

Set the pixel color interpolation method to use when looking up a color based on a floating point or real value.	
When looking up the color of a pixel using a non-interger floating point value, you typically fall in between the pixel colors defined by the source image. This setting determines how the color is determined from the colors of the pixels surrounding that point. That is how to determine the color of a point that falls between two, or even four different colored pixels.

  integer:           The color of the top-left pixel (floor function)
  nearest-neighbor:  The nearest pixel to the lookup point (rounded function)
  average:           The average color of the surrounding four pixels
  bilinear:           A double linear interpolation of pixels (the default)
  mesh:               Divide area into two flat triangular interpolations
  bicubic:            Fitted bicubic-spines of surrounding 16 pixels
  spline:             Direct spline curves (colors are blurred)
  filter:             Use resize -filter settings
This most important for distortion operators such as -distort, -implode, -transform and -fx.

To print a complete list of interpolation methods, use -list interpolate.

See also -virtual-pixel, for control of the lookup for positions outside the boundaries of the image.
For sheer versatility ImageMagick/GraphicsMagick is hard to beat even though it is not always the fastest option.

---

### Post by hugmenot on 2009-07-20
I would use one of these and not -resample

```
convert -filter lanczos -resize 20% in.jpg out.jpg
convert -filter lanczos -resize 800x600 in.jpg out.jpg
convert -filter lanczos -resize 20% -unsharp 1x3+1+.08 in.jpg out.jpg
```

[compare here]("http://www.xs4all.nl/~bvdwolf/main/foto/down_sample/down_sample.htm")

---

### Post by scaine on 2009-07-20
+1 for Phatch.  Very simple interface and yet incredibly powerful.  It can also read Exif tags if necessary and put the resultant files into folders created which represent the date each photo was taken, perhaps with the filename renamed to the time it was taken.  Very slick.  Or add reflections.  Or rotate.  Or tilt and add reflection and rename.  Or... or.. or..  :P

I believe it's in the repos since Jaunty, but you can read about and see it here : 
[http://photobatch.wikidot.com/](http://photobatch.wikidot.com/)

And the homepage is :
[http://photobatch.stani.be/](http://photobatch.stani.be/)

---

