---
title: "Firefox Fonts and Theme problem after upgrade... Please help"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2009-11-28
Hello everyone :-)

After I upgraded to 9.10, my firefox fonts got screwed.
I don't know how to describe the problem, so I have attached two images to explain as best as I could.  What could have gone wrong?

My Web experience has been degraded, I can't read very well, especially small characters.  It feels like the fonts have gone a decade back.
I have played with the optimization, LCD fonts and all... the rest of the applications have great, crisp, clear and easily viewable fonts.

Does anyone have any idea how I can fix this problem?  Please note that I uninstalled firefox and reinstalled...

As you can see on the second image the default theme is very old.  On another 9.10 installation I have the version is much more advanced.. I am mentioning that because I believe that for some reason firefox was not updated/upgraded properly.  

I cannot search for an update for the theme either... I can't even press the button.

Thank you all in advance...

---

### Post by phillw on 2009-11-28
Hi,

Odd things and re-installing FFox with a backup of your data is covered over here -->  [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

There have been issues with Flash messing things up - but that doesn't sound like your symptons. Try following lovinglinux's thread of backing up your profile & re-installing FFox.

Regards,

phill.

---

### Post by Ifaistos on 2009-11-28
Thank you, but I have already done that...
I have already reinstalled Firefox twice..

---

### Post by phillw on 2009-11-28
> **Ifaistos said:**
> Thank you, but I have already done that...
I have already reinstalled Firefox twice..


what does ```
aptitude show firefox

```Give you ?

> Version: 3.5.5+nobinonly-0ubuntu0.9.10.1


Is this there ?

Phill.

---

### Post by Ifaistos on 2009-11-28
Package: firefox
State: not installed
Version: 3.5.5+nobinonly-0ubuntu0.9.10.1
Priority: optional
Section: web
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Uncompressed Size: 131k
Depends: firefox-3.5, firefox-3.5-branding
Provided by: abrowser
Description: meta package for the popular mozilla web browser
 Firefox delivers safe, easy web browsing. A familiar user interface, enhanced
 security features including protection from online identity theft, and
 integrated search let you get the most out of the web. 
 
 This is a meta package that will point to the latest firefox package in ubuntu.
 Don't remove this if you want to receive automatic major version upgrades for
 this package in future.

---

### Post by phillw on 2009-11-28
Hmmm... same as mine - so, it's not that :-(

What does Help - About mozilla firefox give you ?

I get Version 3.5.5  
Mozilla for Ubuntu canonical - 1.0

Mozilla/5.0 (X11: U: Linux i386: en-GB:

Phill.

---

### Post by Ifaistos on 2009-11-28
same :-(

---

### Post by phillw on 2009-11-28
I don't think it's FFox ...  

Possibly fonts .....  Now, this may break Flash... 

```
sudo apt-get install ubuntu-restricted-extras
```

Repairing Flash is no big deal - lol

Phill.

---

### Post by ElSlunko on 2009-11-28
I had issues with FF and fonts. Fixed it by creating .fonts.conf in my home directory & inserting this

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

---

### Post by phillw on 2009-11-28
> **ElSlunko said:**
> I had issues with FF and fonts. Fixed it by creating .fonts.conf in my home directory & inserting this

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintslight</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Hi, as you also posted - I'm going to get the OP to check his appearance setting.

Phill.

---

### Post by Ifaistos on 2009-11-28
It worked !!! My fonts are fixed !!
Just out of curiosity, ElSlunko, what does that file exactly do?



phillw, I had already installed the restricted extras.

What does OP mean in this sentence?

*"I'm going to get the OP to check his appearance setting."*

---

