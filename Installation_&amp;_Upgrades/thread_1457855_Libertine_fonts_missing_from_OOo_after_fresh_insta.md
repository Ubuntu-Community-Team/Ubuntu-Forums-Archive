---
title: "Libertine fonts missing from OOo after fresh install"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2010-04-19
I  don't know why there would be a difference. I installed Karmic on one computer and the Libertine fonts were available in Open Office, but on another machine they are not. Linux Biolinum is available as the font in Appearances, but I can't find it in Open Office. How do I get it to show up in Open Office? 

Most of my documents were created in this font and are now basically unusable. I need to upload a resume today and the copy I have was very carefully crafted in this font and then exported as a PDF. The original no longer opens in this font. It will take a day and a half to rewrite it and make it work in another fonts. I was not expecting this.


Is there a missing link?

---

### Post by Luxx on 2010-04-19
I found a solution.  
Synaptic did not work. The fonts were already installed. Trying to download or reinstall didn't help. The _manual_ instructions about halfway down on this page allowed the installed fonts to be recognized by Open Office.

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)


My original .odt file opened correctly so I could make changes and export as a .pdf.

---

### Post by coffeecat on 2010-04-19
First of all: thanks for posting this. I hadn't heard of the Linux Libertine and Biolinum fonts. They look interesting and are now installed on one of my systems. Which leads me to...

These are not installed by default - at least not in Lucid. I doubt whether they would be in Karmic, but I'll check this later today. You must have installed them yourself, which probably explains why they are available on one machine but not the other. Why Biolinum should appear in Appearance but not in OpenOffice, I cannot explain. Any installed font should appear in both.

Anyway... this is what I just did. I found this website:

[http://linuxlibertine.sourceforge.net/Libertine-EN.html#download](http://linuxlibertine.sourceforge.net/Libertine-EN.html#download)

... and downloaded and extracted the universal zip archive. After extracting this, I simply moved the ttf and otf files to ~/.fonts/. The fonts then appeared for use in both OpenOffice and Appearance. If you don't have a ~/.fonts folder simply create one and copy any font files that you need into it. They will be available for use immediately - you don't even have to restart the xserver. They will, of course, only be available to your user account. If you need to install them system-wide, you need to create a folder in /usr/share/fonts (possibly in the truetype subfolder), move/copy the fonts into this and then run 'sudo fc-cache -fs'.

---

