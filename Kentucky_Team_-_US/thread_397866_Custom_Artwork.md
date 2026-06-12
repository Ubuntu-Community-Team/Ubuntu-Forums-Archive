---
title: "Custom Artwork"
date: 2007-03-31
forum: Kentucky Team - US
---

### Post by comfurtn on 2007-03-31
The Team's custom artwork wiki page is now up at [https://wiki.ubuntu.com/KentuckyTeam/CustomArtwork]("https://wiki.ubuntu.com/KentuckyTeam/CustomArtwork").

Some artwork and logos have already been posted on this page, along with some custom wallpapers to be included with our install CD.  Also, Ubuntu Kentucky logos are now up on the wiki front page, the wiki team page, the web team page, the new members team page, and the knowledge base page.  

Please take a look at these pages and let me know what you think about them so far.

---

### Post by etank on 2007-03-31
We need to find a way to make a desktop them for these. Then if we have our own repo then it will be easy to install on the desktops and also keep them updated.

---

### Post by comfurtn on 2007-03-31
> **etank said:**
> We need to find a way to make a desktop them for these. Then if we have our own repo then it will be easy to install on the desktops and also keep them updated.

I'm in the porcess of making a custom GDM theme package... but I'm not sure how to make a theme package to include the desktop wallpaper. Any ideas on that one?

---

### Post by etank on 2007-03-31
You can try to get a copy of one of the themes already in the repos like blubuntu-look. It should be possible to check out a bzr branch of it and modify it to do what we are wanting. Here is some documentation detailing what I mean [https://wiki.ubuntu.com/Bzr](https://wiki.ubuntu.com/Bzr)

---

### Post by comfurtn on 2007-03-31
> **etank said:**
> You can try to get a copy of one of the themes already in the repos like blubuntu-look. It should be possible to check out a bzr branch of it and modify it to do what we are wanting. Here is some documentation detailing what I mean [https://wiki.ubuntu.com/Bzr](https://wiki.ubuntu.com/Bzr)

I did some digging around, and found that I can simply re-package the official "feisty-wallpapers" package to use our own wallpapers instead.  It will be named "feisty-wallpapers-ky" and will automatically install all the ones that I include.  For now, I'm including all the ones that I've posted on the wiki.  And the great thing is that once the package installs, one of our wallpapers is set as the default!

Well, gotta get this thing packed up and ready to go... I'll post it on the wiki when I'm finished for you guys to test.

---

### Post by Condoulo on 2007-03-31
Would it be possible to include any with the Kubuntu logo? If not, that's ok. But I've recently found myself attatched to KDE.

---

### Post by comfurtn on 2007-03-31
> **Condoulo said:**
> Would it be possible to include any with the Kubuntu logo? If not, that's ok. But I've recently found myself attatched to KDE.

I myself am also a big fan of KDE and Kubuntu... although the recent feisty doesn't work well with my laptop media keys, but i'll get around to fixing that later..  Right now I'm just focusing on getting some stuff together for regular Ubuntu, then I'll go back and make it for Kubuntu.

---

### Post by Condoulo on 2007-03-31
Glad to hear. 
And I'm sure that will probably be fixed by the final release of Feisty, I hope.

---

### Post by comfurtn on 2007-04-01
> **comfurtn said:**
> Well, gotta get this thing packed up and ready to go... I'll post it on the wiki when I'm finished for you guys to test.

Update:  I finally packaged "ubuntu-artwork-ky" and "feisty-wallpapers-ky" ... they are posted on the wiki, along with more details.

I'm about done in for tonight.... my next project will be packaging up the gdm theme and splash screen images.

---

### Post by etank on 2007-04-01
I have a test machine at work and will try this out tomorrow and let you know how it goes. Once again, GREAT job.

---

### Post by montgoej on 2007-04-05
Here are some screenshots of the artwork "in action".  If the borders look weird it's because I used a program called Xnest to get a new login in a seperate window, then I took screenshots of that and cropped them with the GIMP. If anyone's better with Xnest and knows how to make it go fullscreen please share the knowledge. :)

---

### Post by 67GTA on 2007-04-07
I think we need some wallpaper that shows the spirit of Kentucky. I also was wondering if we could use a generic form of the Kentucky Wildcats logo and sound. That has always been a cool logo. Here are a few suggestions:


file:///home/shawnr/Desktop/kentuckysun.php
file:///home/shawnr/Desktop/devilslookout.php
file:///home/shawnr/Desktop/dlwallpaper.php
file:///home/shawnr/Desktop/dogslaughtercreek.php
file:///home/shawnr/Desktop/kentuckymorning.php
file:///home/shawnr/Desktop/mammothcave.jpg
file:///home/shawnr/Desktop/Ky_wildcat.gif
file:///home/shawnr/Desktop/kylogo3.gif
file:///home/shawnr/Desktop/wildcat.wav

---

### Post by 67GTA on 2007-04-07
That didn't work. I made a tar file, but it is too big to attach. I guess I can email it to someone if they want to look at them.

---

### Post by bkingx on 2007-04-07
I agree with 67GTA on this one.  Something that screams KY is warrented here.  I'm sure we can come up with something on this.

---

### Post by 67GTA on 2007-04-07
I made a tar file of the few things I have collected if someone can host them. I am having trouble with my web page right now. Just a few wallpapers, wildcat logos and a wildcat sound file.

---

### Post by comfurtn on 2007-04-07
> **67GTA said:**
> I made a tar file of the few things I have collected if someone can host them. I am having trouble with my web page right now. Just a few wallpapers, wildcat logos and a wildcat sound file.

I like your idea... you can upload your stuff to my server via ftp at:
[ftp://kyle-server.servehttp.com](ftp://kyle-server.servehttp.com)
user: anonymous

and we can take a look at your kentucky stuff.  Pretty much the work I've done so far was simply to get a starting point for our artwork.  I'd love to make something original to show off our team, we just have to make sure that whatever we use in the process is public domain/free from restrictive copyrights.

---

