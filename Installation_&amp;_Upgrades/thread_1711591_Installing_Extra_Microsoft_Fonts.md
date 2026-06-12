---
title: "Installing Extra Microsoft Fonts"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Ashleigh825 on 2011-03-21
I really miss all of my old microsoft fonts, but unfortunately don't have a Windows partition to simply copy and paste all of them over to my Ubuntu OS.

I've already installed all of Microsoft's core fonts, like Arial, Verdana, Times New Roman, etc... but I would like to install all of Microsoft's "extra" fonts that are installed with various Microsoft programs, like Century Schoolbook, Monotype Corsiva, etc...

Could someone tell me which package I should be looking for in the package editor to install these extra fonts, or otherwise tell me how I can get these fonts elsewhere?

Thanks in advance.

- Ashleigh

---

### Post by crossedout on 2011-03-21
Open Terminal window:

```
sudo aptitude update
```
Enter your login password.

```
sudo aptitude install msttcorefonts
```


-Xout

---

### Post by coffeecat on 2011-03-21
> **crossedout said:**
> ```
sudo aptitude install msttcorefonts
```-Xout

@crossedout, unfortunately there are two problems with that. The package is called ttf-mscorefonts-installer, and has been for several releases now. And the OP has already stated that...

> **Ashleigh825 said:**
> I've already installed all of Microsoft's core fonts, like Arial, Verdana, Times New Roman,

@Ashleigh825, with regard to these:

> **Ashleigh825 said:**
>  etc... but I would like to install all of Microsoft's "extra" fonts that are installed with various Microsoft programs, like Century Schoolbook, Monotype Corsiva, etc...

I don't know of any packages that contain these, but have a look at the packages in Synaptic that start with "ttf-". There might be something useful there. I have Century Schoolbook on my Natty system, and I'm sure I didn't install it, so check you don't have it already. For the rest, googling "<name of font> font free" should bring you hits for those not encumbered by copyright. For instance, in case you don't have Century Schoolbook, this came up in a google search:

[http://www.font-zone.com/download.php?fid=2166](http://www.font-zone.com/download.php?fid=2166)

And this for Monotype Corsiva:

[http://www.newfonts.net/index.php?pa=show_font&id=130](http://www.newfonts.net/index.php?pa=show_font&id=130)

To install a downloaded ttf simply unzip the zip file if that is how it comes (double-click on it) and then double-click on the ttf and click on the "Install Font" button.

---

### Post by crossedout on 2011-03-27
@coffeecat:

Good catch on the name.  I try to keep a log of what I install and the package name I suggested is the latest name in my log.  Apparently I didn't update it and didn't see the new name in synaptic.

My bad again on the "extra" fonts being searched for, again I have to place my ignorance on the fact that I only installed that one extra font package and I have the fonts installed that the OP was in search of.

I'll double-check next time.

@Asleigh825:

Hopefully coffeecat has you on the right path.

-Xout

---

### Post by ojahr on 2011-03-28
Hi,

I have tried to install msttcorefons this on my Lubuntu 10.04 for weeks, but it hangs and freeze on the last picture (dos windows with the OK button. 

Any way around? I need to use 10.04 due to lack of memory as Picasa will not work on 10.10.

Any help highly appreciated!!!

---

### Post by howefield on 2011-03-28
> **ojahr said:**
> I have tried to install msttcorefons this on my Lubuntu 10.04 for weeks, but it hangs and freeze on the last picture (dos windows with the OK button. 

Is this the license screen that you need to accept ?

Try using the tab key to highlight the OK button and press enter.

---

### Post by ojahr on 2011-03-28
> **howefield said:**
> Is this the license screen that you need to accept ?

Try using the tab key to highlight the OK button and press enter.
Sic - you are an angel..
:-)

---

