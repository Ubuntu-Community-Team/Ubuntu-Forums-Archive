---
title: "installing  Tesserect OCR On ubantu"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by programmer_007 on 2010-03-31
can anyone guide me how to install Tesserect engine on Ubantu? i am a newbie on ubantu

---

### Post by ajgreeny on 2010-03-31
Just use whatever way you prefer to install tesseract-ocr, eg synaptic.  This will also install tesseract-ocr-deu by default, but if you don't want German as the language, choose another and the uninstall the german version.  You have to have at least one language, of course.

To use it, you will have to scan documents at high resolution (300dpi or more), save the image as a tif (note tif, not tiff) and then use the command ```
tesseract file.tif text
```which will turn the **file.tif** into a txt file now called **text.txt**.  Note youdo not put the txt suffix on the output file name, it is added by the system.

The only downside of tesseract over gocr is that it can not be incorporated into xsane in the same way that gocr is.  It is, however, much more accurate than gocr, which I found to be a waste of time.

---

