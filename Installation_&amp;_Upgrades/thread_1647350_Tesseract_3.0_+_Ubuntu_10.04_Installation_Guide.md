---
title: "Tesseract 3.0 + Ubuntu 10.04 Installation Guide"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by Zeon100 on 2010-12-17
Hi guys,
I am using the Tesseract package which provides OCR (optical Character Recognition for electronic document images. The 10.04 repositories currently only have 2.04 however the latest version, 3.00 is out with many new features. Here is how I got everything working:

**1. Install Imagemagick**
Imagemagick helps convert all the document images to a format Tesseract likes. We use PDFs.
"sudo apt-get install imagemagick"

Usage would be like
"Convert -density 300 scanneddocument.pdf -depth 8 scanneddocument.tif"

This converts to a good quality tiff image with 8 bit depth (required by Tesseract). You can change the density amount as you may get better results.

**2. Install Tesseract**
Get the required packages available in the repositories:
```

sudo apt-get install libpng12-dev
sudo apt-get install libjpeg62-dev
sudo apt-get install libtiff4-dev
("sudo apt-get install zlibg-dev" is suggested in the Tesseract readme but isn't available. I found I didn't need this.)

```

I picked this up from a comment made, you need to be able to compile and make the software. Ubuntu needs some packages to help do this. For many of you these may already be present and installed but it doesn't hurt..
```

sudo apt-get install gcc
sudo apt-get install g++
sudo apt-get install automake

```

Download this program which can't be gained with apt-get:
[http://www.leptonica.org/](http://www.leptonica.org/)
My link was here: [http://www.leptonica.org/source/leptonlib-1.67.tar.gz](http://www.leptonica.org/source/leptonlib-1.67.tar.gz)
```

wget http://www.leptonica.org/source/leptonlib-1.67.tar.gz
tar -zxvf leptonlib-1.67.tar.gz
cd leptonlib-1.67
./configure
make
sudo checkinstall (follow the prompts and type "y" to create documentation directory. Enter a brief description then press enter twice)
sudo ldconfig

```

Now we can actually get and install Tesseract! Remember to go back one directory from the above install of Leptonica:
```

cd ..

```
```

wget http://tesseract-ocr.googlecode.com/files/tesseract-3.00.tar.gz
tar -zxvf tesseract-3.00.tar.gz
cd tesseract-3.00
./runautoconf
./configure
make
sudo checkinstall (follow the prompts and type "y" to create documentation directory. Enter a brief description then press enter twice)
sudo ldconfig

```

Now for whatever reason the training data isn't installed with this. I got mine straight from Tesseract's SVN:
(This is from rjwinder)
```

cd /usr/local/share/tessdata
sudo wget http://tesseract-ocr.googlecode.com/files/eng.traineddata.gz
sudo gunzip eng.traineddata.gz

```

Also, we really wanted to use hOCR which allows us to pinpoint the actual images over the original. You could use something like hocr2pdf ("sudo apt-get install exactimage")to remerge the pdf and hocr output to make searchable PDFs. Anyway to get this:
```

cd /usr/local/share/tessdata/configs
sudo vi hocr

*You need to know how to use Vim to do this bit*
Put this in: "tessedit_create_hocr 1"
Save with ":x"

```

That's it! To use Tesseract go into the directory with your scanned PDF (or whatever it is). I will get both plain and hocr output:

```

cd /home/Zeon
Convert -density 300 scanpage1.pdf -depth 8 scanpage1.tif
Tesseract scanpage1.tif outputtext
Tesseract scanpage1.tif outputtext hocr

```

That's it!

---

### Post by Br11 on 2010-12-24
hi, I tried what you've posted but I get the following after I do "tesseract scanpage1.tif outputtext hocr"
 
actual_tessdata_num_entries_ <= TESSDATA_NUM_ENTRIES:Error:Assert failed:in file tessdatamanager.cpp, line 55
Segmentation fault

any ideas?

---

### Post by rjwinder on 2010-12-29
> **Br11 said:**
> hi, I tried what you've posted but I get the following after I do "tesseract scanpage1.tif outputtext hocr"
 
actual_tessdata_num_entries_ <= TESSDATA_NUM_ENTRIES:Error:Assert failed:in file tessdatamanager.cpp, line 55
Segmentation fault

any ideas?

Hi Br11,

I replaced the eng.traineddata with one from this site:[http://code.google.com/p/tesseract-ocr/downloads/detail?name=eng.traineddata.gz](http://code.google.com/p/tesseract-ocr/downloads/detail?name=eng.traineddata.gz)

That seemed to eliminate the TESSDATA_NUM_ENTRIES error for me.

---

### Post by Br11 on 2010-12-30
It worked! Thanks!

Now I need something that lets me have the text as a layer of the PDF and my life will be perfect :)

---

### Post by fungiblename on 2011-01-07
Zeon 100 Thank you! This has dramatically simplified my life. 

BR 11, this--with many thanks to Konrad Voelkel--will superimpose a text layer. It's not 100% accurate (at least with the files I'm using) but it works pretty well: 

```

#!/bin/bash
echo "usage: pdfocr.sh document.pdf \"author\" \"title\""
# Adapted from http://blog.konradvoelkel.de/2010/01/linux-ocr-and-pdf-problem-solved/ 
# NOTE: This script has been substantially modified/simplified from the original. 
# This version does not allow rotation, language selection or cropping.
# Those parameters were all required in the original, but I don't really need them.
# If you can think of a way to make them optional, please share. 
# This version also uses Tesseract, which I find to be substantially more
# accurate than Cuneiform for English text. 
# usage examples:
pdftk "$1" burst dont_ask
for f in pg_*.pdf
do
echo "pre-processing $f ..."
convert -quiet -density 300 -depth 8 "$f" "$f.tif"
echo no splitting
done
for f in pg_*.tif
do
echo "processing $f ..."
tesseract "$f" "$f" hocr
echo "Merging TIFF and hOCR into PDF file at 150 DPI..."
#Downsample to cut down on file bloat
hocr2pdf -r 150 -i "$f" -o "$f-ocr.pdf" <"$f.tif.html"
done
echo "InfoKey: Author" > in.info
echo "InfoValue: $2" >> in.info
echo "InfoKey: Title" >> in.info
echo "InfoValue: $3" >> in.info
echo "InfoKey: Creator" >> in.info
echo "InfoValue: PDF OCR scan script" >> in.info
pdfjoin --fitpaper --tidy --outfile "$1.ocr1.pdf" "pg_*-ocr.pdf"
rm -f pg_*
pdftk "$1.ocr1.pdf" update_info doc_data.txt output "$1.ocr2.pdf"
pdftk "$1.ocr2.pdf" update_info in.info output "$1-ocr.pdf"
rm -f "$1.ocr1.pdf" "$1.ocr2.pdf" doc_data.txt in.info


```Konrad's blog has the full version of the original script. As noted in the script comment above, if anyone can figure out how to change languages and make orientation, rotation, and cropping parameters optional, please share that info here. 

For some reason, I can't seem to get Tesseract to accept both "hocr" and  "-l en" as parameters, so I took out the language because all the documents I work with are written in English. 

I also had to tweak some of the "$f" variables from the original because my bash shell seemed to recursively and progressively substitute them (resulting in errors such as "pg_0001.pdf.tif.pdf.html does not exist"). As written, on my system - a stock 10.04.1 install - this works.

Edit: I also added a step to downsample the hocr2pdf output to  150 dpi  to prevent file bloat. Before this, the script was taking some 40 KB pages and turning them into 400+ KB each: A big problem on a 100+ page document. I've also been able to get away with 200 DPI and 4-bit depth on the  initial conversion, but it really depends on your source material. Your results may differ, but (at least for the files I'm working with) these settings seem to (sometimes) keep the new OCR'd version of the PDF roughly the same size as the original. There is almost certainly some loss in quality, but it's tolerable for what I'm doing. (There was previously a PNG conversion step in there, but that just fouled up everything....)

However, it still doubles the size of some files - it's probably possible to downsample more, but this is not great for quality. Any other thoughts on how to reduce the final file size? (within the script, that is: I know there are external tools for post-processing, but I've had mixed success with those). 

Hope this helps someone....

---

### Post by Gafs on 2011-01-07
Thank you for this useful tutorial. I installed all the package successfully. But when I use the command (like $ **tesseract test.tif outputtext hocr** ), I receive this notice:

**tesseract: symbol lookup error: tesseract: undefined symbol: page_imag**

What does that mean? How can I fix it?
Any help will be appreciated.

---

### Post by Zeon100 on 2011-01-10
> **Br11 said:**
> It worked! Thanks!

Now I need something that lets me have the text as a layer of the PDF and my life will be perfect :)

Hey there,
That's what Exact Image is for! it has a subprogram called hocr2pdf which will impose the hocr output over the pdf and give you a fully OCRd PDF. Use is documented on their website:

[http://www.exactcode.de/site/open_source/exactimage/hocr2pdf/](http://www.exactcode.de/site/open_source/exactimage/hocr2pdf/)

> 
hocr2pdf: Is a command line front-end for the image processing library to create perfectly layouted, searchable PDF files from hOCR, annotated HTML, input obtained from an OCR system.
 
hOCR, annotated HTML, input must be provided to STDIN, and the image data is read using the filename from the -i or --input argument. For example:
 
hocr2pdf -i scan.tiff -o test.pdf < cuneiform-out.hocr
 
By default the text layer is hidden by the real image data. Including image data can be disabled via the -n, --no-image, so that just the recognized text from the OCR is visible - e.g. for debugging or to save storage space:
 
hocr2pdf -i scan.tiff -n -o test.pdf < cuneiform-out.hocr


Also thanks to rjwinder for pointing out the problem with the trained data from SVN. When I first downloaded it, it worked great but I came into the office yesterday after my holiday and it didn't work! Rjwinder's method fixed the problem.

---

### Post by Zeon100 on 2011-01-10
> **Gafs said:**
> Thank you for this useful tutorial. I installed all the package successfully. But when I use the command (like $ **tesseract test.tif outputtext hocr** ), I receive this notice:

**tesseract: symbol lookup error: tesseract: undefined symbol: page_imag**

What does that mean? How can I fix it?
Any help will be appreciated.

Did you install Leptonica properly? Also does it work normally (ie without hocr)?

---

### Post by rtrdom on 2011-02-12
I am running Linux Echo 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux.
Following directions in this seemingly simple tutorial (thanks for making it clear what to do and why), when I get to the part about doing
 ./runautoconfig
I get this result. 
~/tesseract-3.00$ ./runautoconf
[I]Running libtoolize
./runautoconf: 31: libtoolize: not found
Running aclocal
./runautoconf: 38: aclocal: not found
Running autoheader
./runautoconf: 44: autoheader: not found
Running autoconf
./runautoconf: 51: autoconf: not found
Running automake --add-missing --copy
./runautoconf: 64: automake: not found
All done.
To build the software now, do something like:

$ ./configure [--with-debug] [...other options]
$ make[/I]

Being somewhat new, I did't understand [--with-debug] [...other options]
so I ran;
~/tesseract-3.00$ ./configure --with-debug
configure: WARNING: unrecognized options: --with-debug
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking --enable-graphics argument... yes
checking for cl.exe... no
checking for g++... no
checking whether the C++ compiler works... no
configure: error: in `/home/jim/tesseract-3.00':
configure: error: C++ compiler cannot create executables
See `config.log' for more details

Does this mean I must install/reinstall a C++ compiler?
Any help appreciated.

---

### Post by Peter_H on 2011-02-15
After installing libpng12-dev, libjpeg62-dev, libtiff4-dev and leptonica, 
I was using deb packages from [http://notesalexp.net/lucid/main/t/tesseract/](http://notesalexp.net/lucid/main/t/tesseract/)

It works for me in Lucid.

---

### Post by Zeon100 on 2011-03-02
> **rtrdom said:**
> I am running Linux Echo 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux.
Following directions in this seemingly simple tutorial (thanks for making it clear what to do and why), when I get to the part about doing
 ./runautoconfig
I get this result. 
~/tesseract-3.00$ ./runautoconf
[I]Running libtoolize
./runautoconf: 31: libtoolize: not found
Running aclocal
./runautoconf: 38: aclocal: not found
Running autoheader
./runautoconf: 44: autoheader: not found
Running autoconf
./runautoconf: 51: autoconf: not found
Running automake --add-missing --copy
./runautoconf: 64: automake: not found
All done.
To build the software now, do something like:

$ ./configure [--with-debug] [...other options]
$ make[/I]

Being somewhat new, I did't understand [--with-debug] [...other options]
so I ran;
~/tesseract-3.00$ ./configure --with-debug
configure: WARNING: unrecognized options: --with-debug
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking --enable-graphics argument... yes
checking for cl.exe... no
checking for g++... no
checking whether the C++ compiler works... no
configure: error: in `/home/jim/tesseract-3.00':
configure: error: C++ compiler cannot create executables
See `config.log' for more details

Does this mean I must install/reinstall a C++ compiler?
Any help appreciated.

Sorry for the late reply. I ran into the same problem today in fact and I solved it by doing the following:

- sudo apt-get install gcc
- sudo apt-get install g++
- sudo apt-get install automake

---

### Post by poikiloid on 2011-03-07
using "make install" will not let the program show up in Synaptic. for most people, instead of using "make install", they should first install the program "checkinstall" from synaptic. then, at the step where you would have typed "make install", instead use "checkinstall".  if you already followed the original guide, you can simply delete the tesseract-3.00 directory that was created, and start again at the "tar -zxvf tesseract-3.00.tar.gz
" step, this time substituting "checkinstall" (not "make install"). It will ask if you want to create the documentation directory. type "y" for yes and press Enter. Then you can enter a short description of what tesseract is. when done with the description, type Enter twice. Then you can change some of the information that the package will contain about itself (like adding the names of the dependent packages from the beginning of the tutorial [so synaptic will warn you in case you ever try to delete one of them], or changing the name of the package to tesseract-ocr, as it would be named if you were using the one from the repositories.) Otherwise, just press Enter.

---

### Post by Zeon100 on 2011-03-07
> **poikiloid said:**
> using "make install" will not let the program show up in Synaptic. for most people, instead of using "make install", they should first install the program "checkinstall" from synaptic. then, at the step where you would have typed "make install", instead use "checkinstall".  if you already followed the original guide, you can simply delete the tesseract-3.00 directory that was created, and start again at the "tar -zxvf tesseract-3.00.tar.gz
" step, this time substituting "checkinstall" (not "make install"). It will ask if you want to create the documentation directory. type "y" for yes and press Enter. Then you can enter a short description of what tesseract is. when done with the description, type Enter twice. Then you can change some of the information that the package will contain about itself (like adding the names of the dependent packages from the beginning of the tutorial [so synaptic will warn you in case you ever try to delete one of them], or changing the name of the package to tesseract-ocr, as it would be named if you were using the one from the repositories.) Otherwise, just press Enter.

great, thanks. I've updated the guide with your recommendations.

---

### Post by EgoGratis on 2011-03-09
> sudo apt-get gcc
sudo apt-get g++
sudo apt-get automake

I think this should be changed to:

> sudo apt-get install gcc
sudo apt-get install g++
sudo apt-get install automake

?

---

### Post by adempewolff on 2011-03-13
Slightly off topic, but if anyone was trying to get tesseract to read another language when being used by the OCRfeeder (it always seems to default to English otherwise) then do this:

in the tools:OCR Engines, select tesseract, click edit, and in Engine Arguments change

```
$IMAGE $FILE; cat $FILE.txt
```

to

```
$IMAGE $FILE -l $YOURLANGUAGEHERE; cat $FILE.txt
```

where $YOURLANGUAGEHERE is whatever language you want it to use

for example, I want it to use simplified Chinese so I changed it to:

```
$IMAGE $FILE -l chi_sim; cat $FILE.txt
```

this should make everything work fine and dandy.  you could even have multiple instances of tesseract listed in the OCR Engines list with different parameters for different languages.  (just make sure you actually download the language files and put them in /usr/local/share/tessdata/ before specifying them!)

Hope this might help someone at some point. I can't really figure out what the point of OCRfeeder is, I just have been using it because it saves me from having to a)type the path of the files and b) convert the jpgs to tiffs.  I guess GUIs were meant for people who will sacrifice speed for not having to type out and spell correctly filenames/paths, haha!

---

### Post by EgoGratis on 2011-03-14
@adempewolff

Yes i did exactly the same thing! First you have to download the  language you want (as suggested in tutorial) and to use it in OCRFeeder  you have to define it (-l $YOURLANGUAGEHERE).

Maybe this could be added to tutorial on the first page too.

Until tesseract-ocr v3 and  leptonica are in software center maybe this tutorial should be on [Wiki page]("https://help.ubuntu.com/community/OCR")? And i can confirm the same tutorial works on Maverick Meerkat!

---

### Post by xwang on 2011-03-23
Hi to all!
Is there any way to detect (in a bash script) if a pdf file is searchable or not so that to use tesseract only on non searchable pdfs?
Thank you,
Xwang

---

### Post by xwang on 2011-03-24
> **fungiblename said:**
> Zeon 100 Thank you! This has dramatically simplified my life. 

BR 11, this--with many thanks to Konrad Voelkel--will superimpose a text layer. It's not 100% accurate (at least with the files I'm using) but it works pretty well: 

```

#!/bin/bash
echo "usage: pdfocr.sh document.pdf \"author\" \"title\""
# Adapted from http://blog.konradvoelkel.de/2010/01/linux-ocr-and-pdf-problem-solved/ 
# NOTE: This script has been substantially modified/simplified from the original. 
# This version does not allow rotation, language selection or cropping.
# Those parameters were all required in the original, but I don't really need them.
# If you can think of a way to make them optional, please share. 
# This version also uses Tesseract, which I find to be substantially more
# accurate than Cuneiform for English text. 
# usage examples:
pdftk "$1" burst dont_ask
for f in pg_*.pdf
do
echo "pre-processing $f ..."
convert -quiet -density 300 -depth 8 "$f" "$f.tif"
echo no splitting
done
for f in pg_*.tif
do
echo "processing $f ..."
tesseract "$f" "$f" hocr
echo "Merging TIFF and hOCR into PDF file at 150 DPI..."
#Downsample to cut down on file bloat
hocr2pdf -r 150 -i "$f" -o "$f-ocr.pdf" <"$f.tif.html"
done
echo "InfoKey: Author" > in.info
echo "InfoValue: $2" >> in.info
echo "InfoKey: Title" >> in.info
echo "InfoValue: $3" >> in.info
echo "InfoKey: Creator" >> in.info
echo "InfoValue: PDF OCR scan script" >> in.info
pdfjoin --fitpaper --tidy --outfile "$1.ocr1.pdf" "pg_*-ocr.pdf"
rm -f pg_*
pdftk "$1.ocr1.pdf" update_info doc_data.txt output "$1.ocr2.pdf"
pdftk "$1.ocr2.pdf" update_info in.info output "$1-ocr.pdf"
rm -f "$1.ocr1.pdf" "$1.ocr2.pdf" doc_data.txt in.info


```Konrad's blog has the full version of the original script. As noted in the script comment above, if anyone can figure out how to change languages and make orientation, rotation, and cropping parameters optional, please share that info here. 

For some reason, I can't seem to get Tesseract to accept both "hocr" and  "-l en" as parameters, so I took out the language because all the documents I work with are written in English. 

I also had to tweak some of the "$f" variables from the original because my bash shell seemed to recursively and progressively substitute them (resulting in errors such as "pg_0001.pdf.tif.pdf.html does not exist"). As written, on my system - a stock 10.04.1 install - this works.

Edit: I also added a step to downsample the hocr2pdf output to  150 dpi  to prevent file bloat. Before this, the script was taking some 40 KB pages and turning them into 400+ KB each: A big problem on a 100+ page document. I've also been able to get away with 200 DPI and 4-bit depth on the  initial conversion, but it really depends on your source material. Your results may differ, but (at least for the files I'm working with) these settings seem to (sometimes) keep the new OCR'd version of the PDF roughly the same size as the original. There is almost certainly some loss in quality, but it's tolerable for what I'm doing. (There was previously a PNG conversion step in there, but that just fouled up everything....)

However, it still doubles the size of some files - it's probably possible to downsample more, but this is not great for quality. Any other thoughts on how to reduce the final file size? (within the script, that is: I know there are external tools for post-processing, but I've had mixed success with those). 

Hope this helps someone....

Hi,
I would like to know what are the dependencies for this script.
I suppose tesseract 3.0, but I'm not sure about leptonica.
Thank you,
Xwang

---

### Post by xwang on 2011-03-24
> **xwang said:**
> Hi to all!
Is there any way to detect (in a bash script) if a pdf file is searchable or not so that to use tesseract only on non searchable pdfs?
Thank you,
Xwang

I've found that searchable pdf can be detected with the following command
```
grep -rl Font *.pdf > FilesWithFontName.txt
```
Do you agree?
Xwang

---

### Post by xwang on 2011-03-24
> **xwang said:**
> Hi,
I would like to know what are the dependencies for this script.
I suppose tesseract 3.0, but I'm not sure about leptonica.
Thank you,
Xwang

I'm trying to use the script but I've the following segmentation fault:

...
processing pg_0001.pdf.tif ...
Tesseract Open Source OCR Engine with LibTiff
Merging TIFF (pg_0001.pdf.tif) and hOCR into PDF file at 150 DPI...
Warning: tag mismatch: 'span' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'span' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'p' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'div' can not close last open: 'E0'§`/</span'
/home/andreak/bin/pdfocr.sh: riga 18: 31458 Segmentation fault      hocr2pdf -r 150 -i "$f" -o "$f-ocr.pdf" < "$f.html"

What's the problem?
I'm using kubuntu 10.04 and I've not installed leptonic (which seems not to be used by this script.
Thank you,
Xwang

---

### Post by xwang on 2011-03-25
> **xwang said:**
> I'm trying to use the script but I've the following segmentation fault:

...
processing pg_0001.pdf.tif ...
Tesseract Open Source OCR Engine with LibTiff
Merging TIFF (pg_0001.pdf.tif) and hOCR into PDF file at 150 DPI...
Warning: tag mismatch: 'span' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'span' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'p' can not close last open: 'E0'§`/</span'
Warning: tag mismatch: 'div' can not close last open: 'E0'§`/</span'
/home/andreak/bin/pdfocr.sh: riga 18: 31458 Segmentation fault      hocr2pdf -r 150 -i "$f" -o "$f-ocr.pdf" < "$f.html"

What's the problem?
I'm using kubuntu 10.04 and I've not installed leptonic (which seems not to be used by this script.
Thank you,
Xwang

I've solved the problem installing the svn version of tesseract and the latest leptonica.
So I managed to use the script, but the ocred file is very huge compared to the original one (475Mb vs 31Mb) is there any way to reduce this overhead?
Thank you,
Xwang

---

### Post by SL666 on 2011-04-13
I just wanted to say thanks!

unfortunately for my purposes tesseract doesn't go close to reading what i want :(


Does anyone have any experience with training it? or any semi-automated tools?

---

### Post by jukzh on 2011-05-04
Hi, im failing to convert simple example picture created with imagemagick, however demo pics work flawlesly. Would appreciate collaboration on solving issue.
```

juk@box:~/src/tesseract-ocr-read-only$ cat drawtext.sh 
convert -background white \
    -fill black -gravity center \
     -pointsize 72 label:"$1" pic.xpm
juk@box:~/src/tesseract-ocr-read-only$ convert pic.xpm pic.tif
juk@box:~/src/tesseract-ocr-read-only$ file pic.*
pic.tif: TIFF image data, little-endian
pic.xpm: X pixmap image text
juk@box:~/src/tesseract-ocr-read-only$ tesseract pic.tif pic
Tesseract Open Source OCR Engine v3.01 with Leptonica
Error in pixConvertRGBToGray: pixs not 32 bpp
check_legal_image_size:Error:Only 1,2,4,5,6,8 bpp are supported:16
Cannot convert Pix to image with bpp = 16
Floating point exception
juk@box:~/src/tesseract-ocr-read-only$ tesseract phototest.tif phototest
Tesseract Open Source OCR Engine v3.01 with Leptonica
juk@box:~/src/tesseract-ocr-read-only$ cat phototest.txt 
This is a lot of 12 point text to test the
ocr code and see if it works on all types
of file format.
The quick brown dog jumped over the
lazy fox. The quick brown dog jumped
over the lazy fox. The quick brown dog
jumped over the lazy fox. The quick
brown dog jumped over the lazy fox.


juk@box:~/src/tesseract-ocr-read-only$ convert -version
Version: ImageMagick 6.6.2-6 2011-04-27 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2010 ImageMagick Studio LLC
Features: OpenMP 


```

---

### Post by jukzh on 2011-05-04
Hehe, here update :p
juk@box:~$ cat drawtext.sh 
#!/bin/bash

TEX="$1"
OUT="$2"

[ "$OUT" == "" ] && OUT="out.xpm"
[ "$TEX" == "" ] && TEX="Foobar"

echo printing \'$TEX\' to file \'$OUT\'...

convert -background black \
    -fill white -gravity center \
    -font $HOME/.fonts/wqymicrohei.ttf \
     -pointsize 72 label:"$TEX" \
    -compress none \
    -depth 8 \
    -colorspace Gray \
    $OUT

juk@box:~$ ./drawtext.sh 'hello world' hello.png
printing 'hello world' to file 'hello.png'...
juk@box:~$ tesseract hello.png hello.png
Tesseract Open Source OCR Engine v3.01 with Leptonica
juk@box:~$ cat hello.png.txt 
hello world

juk@box:~$ ./drawtext.sh '&#27721;&#23376;&#24456;&#38590;' hello.png
printing '&#27721;&#23376;&#24456;&#38590;' to file 'hello.png'...
juk@box:~$ feh hello.png
juk@box:~$ tesseract hello.png hello.png
Tesseract Open Source OCR Engine v3.01 with Leptonica
juk@box:~$ cat hello.png.txt 
iR¥?E3E

juk@box:~$ tesseract hello.png hello.png -l chi_sim
Tesseract Open Source OCR Engine v3.01 with Leptonica
juk@box:~$ cat hello.png.txt 
&#27721;&#23376;&#24456;&#38590;

juk@box:~$ tesseract 20110504_002.jpg 20110504_002.jpg.scan -l chi_sim
Tesseract Open Source OCR Engine v3.01 with Leptonica
juk@box:~$ cat 20110504_002.jpg.
20110504_002.jpg.scan.txt  20110504_002.jpg.txt       
juk@box:~$ cat 20110504_002.jpg.scan.txt 
&#27721;&#23376;

pngs and jpegs work fine despite of 'must be tif' in man page, sory if it's offtopic, but i just CANNOT not to share...

---

### Post by olalaaa on 2011-06-27
I am not sure why exactly do we need leptonica. :(

Or, if that is really necessary, why couldn't we automate the install of leptonica inside of tesseract program ?

One more question for the most experienced users of tesseract: does that "training" process is really necessary, or we could just use the command line for OCR-ing our image files ? My first guess is that the eng.~ file should be already "trained" to work as intended. :mad:

Thank you very much for your help.

---

### Post by encolpe on 2011-07-28
> **Zeon100 said:**
> Hi guys,
Also, we really wanted to use hOCR which allows us to pinpoint the actual images over the original. You could use something like hocr2pdf ("sudo apt-get install exactimage")to remerge the pdf and hocr output to make searchable PDFs. Anyway to get this:
```

cd /usr/local/share/tessdata/configs
sudo vi hocr

*You need to know how to use Vim to do this bit*
Put this in: "tessedit_create_hocr 1"
Save with ":x"

```


You can use tee to create the file:
```

echo "tessedit_create_hocr 1" | sudo tee /usr/local/share/tessdata/configs/hocr

```

---

### Post by rickyrockrat on 2011-08-30
I used Xane with 300 dpi resolution, scanned to PNM, then opened in gimp and cut bits of my scan out into pages I wanted to scan, then I saved these and I got:

```
check_legal_image_size:Error:Only 1,2,4,5,6,8 bpp are supported:16
```

The fix is to do this with imagemagick's convert program:
```
convert -colors 256 -alpha off -density 300 in.png out.tif
```


Tesseract likes this just fine.

Cheers.

---

### Post by joe_kirchner on 2011-09-30
Hi,

I have been playing around with the script, trying to optimize a number of things for my situation. I also informally tested the script using cuneiform and tesseract with a variety of settings. You or some of your readers may find these of interest. In my case, I plan to use the script to process a large number of documents dating back to the 1930s for a usable electronic archive. Hence, my documents are mix and match formats and the originals vary in quality. Your post asks if anyone has a method of rotating pages depending on the original layout. I have resolved this in a semi-automated fashion.

Here are the changes that I am making to the script:

1) I changed the first part to read in tiff files, because in my use, I need to convert my scanner output to searchable PDFs and maintain high quality tiffs for archival purposes. Eventually, my choice here could be made optional, so a command line argument or the input file name extension would branch the script to handle tiff or pdf or some other format such as jpg or png.

2) I added a component to clean up the image prior to OCR processing. I use Scan Tailor for this. This is the semi-automated portion. Scan Tailor is a linux utility that pulls in an image document, splits it into separate pages, then allows you to operate several clean up stages. I have found it useful to automatically run most of the stages and then visually review and manually adjust each page where necessary. The stages are as follows:

   a) Fix the page orientation
   b) Split the pages (Useful to split photocopied facing pages of a book or journal article)
   c) Deskew (This allows you to straighten out the page if photocopied or scanned at an angle)
   d) Select content (Useful to select just the text, ignoring scan marks made between book pages. The automated method works well.)
   e) Margins (Here you can relocate the text allowing nice margins)
   f) Resolution (Change the output resolution)
   g) Image mode (Choose black and white vs gray scale/color)
   h) Dewarping (This could be used to eliminate the text curvature when scanning large books)
   i) Despekling (Eliminate extraneous noise or speckles on the page)

For a clean document many or all of these steps can be skipped. Once the cleanup is conducted and you close out of Scan Tailor, the script automatically takes over to process the OCR and other steps.

3) After OCRing the document, I send the original tiff and the cleaned up tiff to a tiff archive directory.

4) Next I send the searchable PDF to the pdf directory

5) I combine all of the hocr html to a single html page and send that to an html page. I do this with the concept that multi-document searches can be conducted on these. I believe scanning html is faster than scanning PDF, but I am not sure about that. In any case, I have found it to more accurately find phrases than searching the searchable PDFs. I explain below.

6) This brings me to my last and most important points about optimizing. 

   a) I noticed your comment: 

                #Downsample to cut down on file bloat
                hocr2pdf -r 150 -i "$f" -o "$f-ocr.pdf" <"$f.tif.html"

      I read the man page for hcor2pdf (type "man hocr2pdf" from a shell) and noticed that the -r argument is about the input file, not output file. Hence, when I tried alternate settings of 300 or 150, the output file size did not change. Oddly, I did not find a difference in the the ablility of hocr2pdf to match OCRed text to image text either (Note, I only tested with tesseract). Let me explain. I OCRed a 300 resolution document, so I would expect the hocr settings to match up word placement to that of large (300 DPI) character images. By then setting the hocr2pdf -r argument to 150, I expected a problem because these smaller image characters might not match to the larger hocr character placements. Yet, I was unable to see a difference between the two methods. Of course, there may be a difference that I did not detect. I only did light testing and may have missed a few problems.

   b) In comparing tesseract to cuneiform, I found that the raw OCR accuracy (percentage of accurately detected words) to be fairly high in both, but significant better in tesseract. However, once the searchable text was combined into the PDF document, the cuneiform output was siginificantly better. Why is this? Tesseract accurately identifies more words, but mangles the placement somewhat when placing in the PDF. Try hocr2pdf with the -n argument. That will produce a PDF with the searchable text visible, but no image. Hence, you can see the misidentified and misplaced words. When you search for the word "cat" but OCR has inacurately identified it as "cot" then your search will fail, even though on the PDF image you see "cat". Cuneiform may have a few "cot"s when tesseract correctly identifies "cat"s. However, supposing both search engines correctly identify each word in the sentence, "The brown cow jumped over the moon." When examining both hocr outputs using a browser, both versions appeared correctly, however, in the PDF versions the searchable text may come out as " The browncowjumped overthemoon" in tesseract, but not in cuneiform. Tesseract mangles the placement of words. Sometimes words actually overlap rather than occupy the space between words. Hence, you would correctly find the sentence in a search of the tesseract output in a browser, but not in the PDF. You may also see some of the mangling by copying text from the PDF and pasting to a text editor. That would definately show the missing spaces, but may not show the overlapping words, which you would need see by using the -n argument on hocr2pdf.

   c) Getting the best of both worlds, I compromise is to scan the image twice -- once with tesseract to produce accurate html for my searchable html directory and once with cuneiform to be combined into the PDFs.


If and when I have time to clean up and finish my version of the script, I will post it. Currently, it is still a work in progress, but basically suits my purpose. Others would have to read through it and change the directories where files are found or placed to reflect the directory structure on their machine. They may also want to change some other things manually, which eventually should be command-line options. If anyone is really interested, ask and I will post the "work in progress" version.

One thing I did not do is to adjust any settings in the /usr/share/tesseract-ocr/tessdata/configs/ directory, where tesseract has some settings. The only thing I did in this directory was to create the hocr file as your post suggests. Perhaps there is some settings here that could optimize the hocr to pdf image alignment, eliminating the problem I described above.

Have you or any other readers successfully tried to adjust the configuration settings in this directory?

Cheers,

Joe

---

### Post by Advice Pro on 2011-10-03
I could follow your guide until the mention of training data.
```
cd /usr/local/share/tessdata
```
Output:  ```
bash: cd: /usr/local/share/tessdata: No such file or directory
```

---

### Post by simon_w on 2011-10-28
@joe_kirchner

thanks for the reference to scantailor -- looks good.

I would be very grateful if you would post your script, in whatever state it's in, somewhere.  I would like to work on something similar, and it would be nice to avoid duplicating your effort.  I could probably help to clean it up, if it needs it.  I have tonnes of shell-scripting experience.

Cheers!

---

### Post by nalin4linux77 on 2012-02-27
**Linux-intelligent-ocr-solution**

LIOS is a free and open source software for converting print in to text using either scanner or a camera. It can also produce text out of scanned images from other sources. Program is given total accessibility for visually impaired. LIOS is written in python and we release it under GPL3 license. LIOS will work with Debian based operating systems. LIOS is an effort from the easy-ocr development team. There are great many possibilities for this program. Feedback is the key to it. expecting your feedback. 
**HOW TO INSTALL**

[B]Download deb file from here [http://linux-intelligent-ocr-solution.googlecode.com/](http://linux-intelligent-ocr-solution.googlecode.com/) download the latest deb package and install
What is new in LIOS-1.2
1 Cam-Scan,
2 Cam-Reader,
3 Scan-to-image-only,[/B]:guitar:
[B]4 Scan-to-images-repeatedly,
5 Introduction of py-sane, Glaid library make the program faster and efficient,
6 Multiple arguments are handled effectively,
7 Ocr a single Image,
8 Artha shortcut (alt+control+W),
9 Beta version of spell-checker,
10 Provision for submitting issues in the About Dialog.
Features
1 Single scan & Repeated Scanning,
2 Ocr Folder,
3 Ocr Pdf,
4 Ocr image only,
5 Cam-Scan and Cam-Reader,
6 Scan-for-image-only & repeatedly,
7 24 Language support (Given at the end),
8 Full GUI environment,
9 Selection of starting page number, page numbering mode and number of pages to scan,
10 Selection of Scan area, brightness, resolution and time between repeated scanning,
11 Full Auto Rotation,[/B]:lolflag:
[B]12 Brightness optimizer,
13 Audio converter,
14 Easily Accessible Preferences Window,
15 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD),
16 Good text manipulation with Find, Go-To-Page, Go-To-Line, Append file, Punch File.
17 Display Preferences for Low vision,
18 Dictionary Support for English(Artha)
19 Beta version of spell-checker,
20 Provision for submitting issues,
21 And more features are in the preferences.[/B]
**How to start using LIOS.**
1. Scanning.

In order to start new scan, first press ctrl+n and then press f9 for single scan or ctrl+f9 for repeated scanning. To set the scanning preferences press ctrl+p and set the starting page number, Mode of page numbering, double page mode if you intend to keep 2 pages at a time, rotation to select the way in which you want the program to rotate the images before conversion. In full automatic rotation mode, one can keep the book in 00 90 180 and 270 degree angle. In partial rotation mode program will scan once to find out the position of the book and then the rotation will be kept. In manual mode one should select the angle. partial and manual mode is faster than full auto rotation mode in ocr process. One can select the number of pages to be scanned at a stretch by setting number of pages in the case of repeated scanning. One can stop all scanning process by pressing ctrl f4.
2. Cam-scan.

one can now use Hovercam or a Webcam to produce text in LIOS. Adjustments with these devices can be made using LIOS-cam-preferences in edit menu. This feature will help to read books and other printed materials such as visiting cards currency and like and also it makes the ocr process very fast and accurate. Please be specific to use devices with auto focusing facility. remember that there is no autorotation in this utility.so for the same reason, support of a stand for the webcam will be highly appreciated.
3. Cam-reader.

is the utility which will give a continuous output as one moves the webcam. First it will create the image and then will produce the text and it will start reading. After the completion of reading, it will repeat the process automatically. In cam-scan, one has to take the photo and it will be converted in to text.
4. Ocr Image.

LIOS can convert image file to text which is in jpg, tif, png, pnm and bmp.
5. Ocr folder.

LIOS can convert scanned images from other sources. It can convert jpg, jpeg, tif, tiff png, pnm, formats. To convert the images in a folder, select scan from folder option from scan menu and then select the input folder.
6. Ocr Pdf file.

Select Ocr pdf from scan menu and then select the input file. It is recommended that one can use ocropus as engine more efficiently in pdf conversion.
7. scan for image only and scan for images only repeatedly.

Help one to scan only images and it will give the user opportunity to utilize different ocr engines conveniently. Also it avoids delay between each scan if one does not want to listen to the output. Images will be saved in LIOS or one can choose his own destination. Now conversion can be done using folder option.
8. Brightness checker.

To set a n exact value of brightness or threshold is the best way to ensure maximum efficiency out of ocr engines. To find out the best value, go to tools menu and select brightness checker. This utility will scan for 15 or 17 times to complete the process. After the process, number of words detected at different values will be shone in tabs. If you want to know the precise value only, shift tab and then tab to apply the value.
9. Audio conversion.

LIOS can convert the text opened in LIOS to wav files. To convert the text in to speech, go to tools menu and select audio converter.
10. Text Manipulation.

To go to page, press ctrl+g and then type the page number, and tab to OK. In the case of double page type only odd number, for example 1 in the case of 1-2 and 11 in the case of 11-12. One can go to any line by pressing ctrl+l and ctrl+f will help to find any word in the document.
11. Display preferences.

display preferences in the edit menu will help to set fond size, color , italic, bold and color of the background.
12. Engines.

There are 5 engines in LIOS.out of these only cuneiform can handle 24 languages, list given at the end. All other engines can handle only English. Cuneiform is good for speed and picture skipping ,ocropus is good for layout analysis and pdf conversion.
13. Artha.

In order to find out the meaning of English words, first select the word and then press alt+ctrl+w and tab to find the meaning. Caution for the first time one has to press alt+control+w twice so as to switch on artha
14. Spell checker.

A beta version of spell checker is added to the program.press ctrl f7 and all the misspelled words will appear and one can change them.
Cuneiform support Bulgarian, Croatian, Czech, Danish, Dutch, English, Estonian, French, German, Hungarian, Italian, Latvian, Lithuanian, Polish, Portuguese, Romanian, Russian, Russian-English bilingual, Serbian, Slovene, Spanish, Swedish, Turkish, and Ukrainian.
Disclaimer

    Copyright (c) 2011-2012 LIOS Development Team 

    All rights reserved . Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met: 

    Redistributions of source code must retain the below copyright notice, 

    this list of conditions and the following disclaimer. 

    Redistributions in binary form must reproduce the below copyright notice, 

    this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution. 

    Neither the name of the nor the easyocr team names of its 

    contributors may be used to endorse or promote products derived from this software without specific prior written permission. 

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAG:guitar:E." 

**FREE SOFTWARE FREE SOCIETY**:lolflag:

---

