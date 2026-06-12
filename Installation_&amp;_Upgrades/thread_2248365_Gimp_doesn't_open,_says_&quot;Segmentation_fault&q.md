---
title: "Gimp doesn't open, says &quot;Segmentation fault&quot;"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by Tom 6 on 2014-10-14
Hi :)  
There was an old thread that explored it but didn't get anywhere.  It's wider than just Ubuntu and i found answers from Arch, Manjaro and other distros.  The one that solved it for me was an old Ubuntu bug-tracker thread.  It said to just;  

gimp -version

then if the version is 2.8.?? then the folders need to be created as below.  If the version was 2.6.?? or something else then just adapt those first two lines to suit.  

mkdir ~/gimp-2.8
cd ~/gimp-2.8
mkdir palettes
mkdir gradients
mkdir patterns
mkdir dynamics
mkdir brushes

Errr, you can probably shorten all that to something like this  

mkdir ~/gimp-2.8
cd ~/gimp-2.8
mkdir palettes   gradients   patterns   dynamics   brushes

but it's a lot less clear because all the different folder names get squished together in most forums.  
Regards from 
Tom :)

---

