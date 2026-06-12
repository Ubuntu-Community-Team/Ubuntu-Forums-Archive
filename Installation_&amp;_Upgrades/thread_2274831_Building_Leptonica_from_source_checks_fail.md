---
title: "Building Leptonica from source: checks fail"
date: 2015-04-22
forum: Installation &amp; Upgrades
---

### Post by IZavorin on 2015-04-22
I am trying to build leptonica ([http://www.leptonica.org/source/README.html](http://www.leptonica.org/source/README.html)) from source on an Ubuntu 14.04 box. Reason for doing it is that I want to build and then train Tesseract 3.03 OCR. 

I ran the standard sequence of commands:

```

sudo ./configure 
sudo make
sudo make install
sudo make check

```

with the last command designed to check the installation. I got a bunch of FAILs:

```

 sudo make check
Making check in src
make[1]: Entering directory `/home/ilya/Tesseract303/leptonica-1.71/src'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/ilya/Tesseract303/leptonica-1.71/src'
Making check in prog
make[1]: Entering directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make  alphaops_reg alphaxform_reg bilateral2_reg binarize_reg blackwhite_reg blend3_reg blend4_reg colorcontent_reg coloring_reg colormask_reg colorquant_reg colorspace_reg compare_reg convolve_reg dewarp_reg dna_reg dwamorph1_reg enhance_reg files_reg findcorners_reg findpattern_reg fpix1_reg fpix2_reg graymorph2_reg hardlight_reg insert_reg ioformats_reg jpegio_reg kernel_reg label_reg maze_reg multitype_reg nearline_reg newspaper_reg overlap_reg paint_reg paintmask_reg pdfseg_reg pixa2_reg pixserial_reg pngio_reg projection_reg psio_reg psioseg_reg pta_reg rankbin_reg rankhisto_reg rasteropip_reg rotate1_reg rotate2_reg rotateorth_reg scale_reg seedspread_reg selio_reg shear1_reg shear2_reg skew_reg splitcomp_reg subpixel_reg threshnorm_reg translate_reg warper_reg writetext_reg xformbox_reg
make[2]: Entering directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make[2]: `alphaops_reg' is up to date.
make[2]: `alphaxform_reg' is up to date.
make[2]: `bilateral2_reg' is up to date.
make[2]: `binarize_reg' is up to date.
make[2]: `blackwhite_reg' is up to date.
make[2]: `blend3_reg' is up to date.
make[2]: `blend4_reg' is up to date.
make[2]: `colorcontent_reg' is up to date.
make[2]: `coloring_reg' is up to date.
make[2]: `colormask_reg' is up to date.
make[2]: `colorquant_reg' is up to date.
make[2]: `colorspace_reg' is up to date.
make[2]: `compare_reg' is up to date.
make[2]: `convolve_reg' is up to date.
make[2]: `dewarp_reg' is up to date.
make[2]: `dna_reg' is up to date.
make[2]: `dwamorph1_reg' is up to date.
make[2]: `enhance_reg' is up to date.
make[2]: `files_reg' is up to date.
make[2]: `findcorners_reg' is up to date.
make[2]: `findpattern_reg' is up to date.
make[2]: `fpix1_reg' is up to date.
make[2]: `fpix2_reg' is up to date.
make[2]: `graymorph2_reg' is up to date.
make[2]: `hardlight_reg' is up to date.
make[2]: `insert_reg' is up to date.
make[2]: `ioformats_reg' is up to date.
make[2]: `jpegio_reg' is up to date.
make[2]: `kernel_reg' is up to date.
make[2]: `label_reg' is up to date.
make[2]: `maze_reg' is up to date.
make[2]: `multitype_reg' is up to date.
make[2]: `nearline_reg' is up to date.
make[2]: `newspaper_reg' is up to date.
make[2]: `overlap_reg' is up to date.
make[2]: `paint_reg' is up to date.
make[2]: `paintmask_reg' is up to date.
make[2]: `pdfseg_reg' is up to date.
make[2]: `pixa2_reg' is up to date.
make[2]: `pixserial_reg' is up to date.
make[2]: `pngio_reg' is up to date.
make[2]: `projection_reg' is up to date.
make[2]: `psio_reg' is up to date.
make[2]: `psioseg_reg' is up to date.
make[2]: `pta_reg' is up to date.
make[2]: `rankbin_reg' is up to date.
make[2]: `rankhisto_reg' is up to date.
make[2]: `rasteropip_reg' is up to date.
make[2]: `rotate1_reg' is up to date.
make[2]: `rotate2_reg' is up to date.
make[2]: `rotateorth_reg' is up to date.
make[2]: `scale_reg' is up to date.
make[2]: `seedspread_reg' is up to date.
make[2]: `selio_reg' is up to date.
make[2]: `shear1_reg' is up to date.
make[2]: `shear2_reg' is up to date.
make[2]: `skew_reg' is up to date.
make[2]: `splitcomp_reg' is up to date.
make[2]: `subpixel_reg' is up to date.
make[2]: `threshnorm_reg' is up to date.
make[2]: `translate_reg' is up to date.
make[2]: `warper_reg' is up to date.
make[2]: `writetext_reg' is up to date.
make[2]: `xformbox_reg' is up to date.
make[2]: Leaving directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make  check-TESTS
make[2]: Entering directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make[3]: Entering directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
FAIL: alphaops_reg
FAIL: alphaxform_reg
FAIL: bilateral2_reg
FAIL: binarize_reg
FAIL: blackwhite_reg
FAIL: blend3_reg
FAIL: blend4_reg
FAIL: colorcontent_reg
FAIL: coloring_reg
FAIL: colormask_reg
FAIL: colorquant_reg
FAIL: colorspace_reg
FAIL: compare_reg
FAIL: convolve_reg
FAIL: dewarp_reg
FAIL: dna_reg
FAIL: dwamorph1_reg
FAIL: enhance_reg
PASS: files_reg
FAIL: findcorners_reg
FAIL: findpattern_reg
FAIL: fpix1_reg
FAIL: fpix2_reg
FAIL: graymorph2_reg
FAIL: hardlight_reg
FAIL: insert_reg
PASS: ioformats_reg
PASS: jpegio_reg
FAIL: kernel_reg
FAIL: label_reg
FAIL: maze_reg
FAIL: multitype_reg
FAIL: nearline_reg
FAIL: newspaper_reg
FAIL: overlap_reg
FAIL: paint_reg
FAIL: paintmask_reg
FAIL: pdfseg_reg
FAIL: pixa2_reg
FAIL: pixserial_reg
FAIL: pngio_reg
FAIL: projection_reg
FAIL: psio_reg
FAIL: psioseg_reg
FAIL: pta_reg
FAIL: rankbin_reg
FAIL: rankhisto_reg
FAIL: rasteropip_reg
FAIL: rotate1_reg
FAIL: rotate2_reg
FAIL: rotateorth_reg
FAIL: scale_reg
FAIL: seedspread_reg
FAIL: selio_reg
FAIL: shear1_reg
FAIL: shear2_reg
FAIL: skew_reg
FAIL: splitcomp_reg
FAIL: subpixel_reg
FAIL: threshnorm_reg
FAIL: translate_reg
FAIL: warper_reg
FAIL: writetext_reg
FAIL: xformbox_reg
=======================
61 of 64 tests failed
See prog/test-suite.log
=======================
make[3]: *** [test-suite.log] Error 1
make[3]: Leaving directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make[2]: *** [check-TESTS] Error 2
make[2]: Leaving directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/home/ilya/Tesseract303/leptonica-1.71/prog'
make: *** [check-recursive] Error 1

```

What do I need to do to get these to PASS? Am I missing 3rd-party libs that I need to install separately? If so, how do I determine the shortest list that I would need to get this to work and where do I get them?

Thanks much!

---

### Post by steeldriver on 2015-04-22
Did you examine the output of the configure script? were there any warnings about missing components? what is the output of

```

grep '^#define HAVE_' config.log

```

As an aside, imho it's never a good idea to use 'sudo' for the configure and make phases, when working in your home directory - it leaves you with a bunch of root-owned files and can cause later permission problems. In fact if you're installing to $HOME as well (e.g. [FONT=courier new]./configure --prefix=$HOME[/FONT]) then you don't even need 'sudo' for the install phase.

I don't know what the checks do, however they seem to write a bunch of stuff to/from /tmp - perhaps there's an issue there? There should be a bunch of logs you can examine to see if there is any more specific information about the failure(s) e.g.

```

cat prog/alphaops_reg.log

```

---

### Post by mc4man on 2015-04-22
I would also suggest to run as user not root
./configure
make
make check
Then sudo make install if installing to /

As far as deps at least in add. to basic stuff - 
libjpeg-dev
libjbig-dev
libtiff5-dev
libgif-dev
libpng12-dev

Also read results of ./configure carefully, passing a configure doesn't mean all you want/can is enabled.
Whether all checks/tests should pass no clue... (quick look here - 10 of 64 tests failed

---

### Post by IZavorin on 2015-04-23
Thank you both!

I reran the commands, than added the libs (actually just one of them was not installed) which gave me the 10 FAILs. Then ran

<CODE>
sudo apt-get install gnuplot
<CODE>

and that got rid of those 10.

---

### Post by IZavorin on 2015-04-23
How do I mark this SOLVED?

---

### Post by dino99 on 2015-04-23
> **IZavorin said:**
> How do I mark this SOLVED?

click on Thread Tools on top right of your first post above, and select Solved.

---

