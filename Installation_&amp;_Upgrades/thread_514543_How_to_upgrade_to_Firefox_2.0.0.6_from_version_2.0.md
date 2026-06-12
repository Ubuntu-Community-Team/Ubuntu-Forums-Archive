---
title: "How to upgrade to Firefox 2.0.0.6 from version 2.0.0.5 for Ubuntu Feisty"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by link2zelda on 2007-07-31
I'm a version junky, good or bad, so the Mozilla Foundation just came out with Firefox 2.0.0.6 today and I had to have it.  Here's how I upgraded from Firefox 2.0.0.5 to 2.0.0.6.  These instructions are for i386 feisty and they may be different for 64 bit installations, such as in the /usr/lib64 folder in the directions below, though I'm not sure, anyway here's the i386 feisty directions.

1) download firefox-2.0.0.6.tar.gz from [http://www.mozilla.com/en-US/firefox/](http://www.mozilla.com/en-US/firefox/) the one on their home page, the Linux i686  9.2MB download.

2) where ever you downloaded it, now move it to the /usr/lib directory and you need sudo permission to make the move, so I downloaded it on my Desktop.
 cd ~/Desktop
 sudo mv firefox-2.0.0.6.tar.gz /usr/lib/

3) use the following command that will extract that archive into /usr/lib/firefox
 sudo tar -zxvf firefox-2.0.0.6.tar.gz

That's all there is too it, flash still works and the all plugins and themes in place, though flash was working for me via Automatix since Firefox 2.0.0.4 as I just switched to Ubuntu from Windows as my main desktop.

Recommended: 
A) remove the archive by the following command
 sudo rm /usr/lib/firefox-2.0.0.6.tar.gz

Optional:
1) fix Firefox Ugly controls
[http://osnovice.blogspot.com/2007/05/firefox-controls-are-ugly.html](http://osnovice.blogspot.com/2007/05/firefox-controls-are-ugly.html)
really works and they look great.  Perfect cut and paste directions.

2) fix Ubuntu fonts (though their not that bad to begin with) for LCD monitors, I used the following forum URL, and included the directions that I copied, note where the deb ... and deb-src ... lines go in /etc/apt/sources.list
Anyway here it is.
Improved subpixel font rendering for Feisty 
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

These are the directions I used as the first two lines assume the following line:
sudo gedit /etc/apt/sources.list

#then the rest

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

If you get errors about missing gpg key
wget [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) -O- | sudo apt-key add -
or
gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

sudo aptitude update
sudo aptitude install libfreetype6 libcairo2 libxft2

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

After the install, you may want reconfigure font settings. I'm currently using Feisty defaults (Native, Always, No bitmapped fonts) myself.

Finally I recommend to have the tabs on the left or right sides via the directions of [http://www.widefox.com/](http://www.widefox.com/) 

That's all.

---

### Post by zidane2 on 2007-08-01
mine updated automatically

the patience to wait a couple of hours is very useful :)

---

### Post by dasunst3r on 2007-08-01
Mine also updated automatically.  I used to have to wait one entire week before the updates propagated to me, but one day for turnaround is definitely impressive by my standards.

---

### Post by link2zelda on 2007-08-01
Same here, it updated the following day, and just overwrote the 2.0.0.6 that I copied, the only thing was I had to fix the firefox ugly controls again, and another fix for colorzilla by the libxpcom* fix and reinstalling colorzilla.

It's nice to know Ubuntu is incredible fast on the updates.  Perhaps if Mozilla don't include the ugly controls fix, Ubuntu can?

---

