---
title: "Can Tesseract3.03 be incrementally trained?"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by IZavorin on 2015-04-24
I built Tesseract3.03 from source on an Ubuntu 14.04.2 machine. There is a **[page ]("https://code.google.com/p/tesseract-ocr/wiki/TrainingTesseract3")**describing how it can be training on new languages/fonts, but what I can't figure out if Tesseract can be trained incrementally. I have some test images that come with accompanying ground truth (UTF8 text files that contain the text shown in the images). I ran Tesseract on these images using the out of the box model for the language (English) that came with the source distribution. Some were recognized well, some badly. So what I want to do is to take some of these bad images and use them with their ground truth + the original English model to make a better English model that would do better on the bad images. Can I do it? Thx!

---

