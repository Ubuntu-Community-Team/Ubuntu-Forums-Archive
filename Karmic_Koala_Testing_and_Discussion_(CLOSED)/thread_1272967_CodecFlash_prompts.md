---
title: "Codec/Flash prompts"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2009-09-22
Ok...normally when I do a fresh install and I go to a site with flash I prompted to install it.  Now when I go i get nothing.

Also when I would try to play a file I didn't have the codec for, the OS would prompt me to download codecs for it.  It no longer does this either.

Any idea's why?

---

### Post by psyke83 on 2009-09-22
> **keenish27 said:**
> Ok...normally when I do a fresh install and I go to a site with flash I prompted to install it.  Now when I go i get nothing.

Also when I would try to play a file I didn't have the codec for, the OS would prompt me to download codecs for it.  It no longer does this either.

Any idea's why?

Because you're using an alpha release. In the past day or so, Update Manager was updated to use the aptdaemon backend (what the Software Center uses). I'm guessing that the codec buddy will also be transitioned in the same way. I'm not sure about Firefox, perhaps the ubufox extension isn't working at the moment.

---

### Post by keenish27 on 2009-09-22
Ok.  Well I installed the flash-nonfree plugin and now the flash video's render (youtube), but when I click play, nothing happens.  Any ideas on this one?

EDIT:  Okay...now its working for no apparent reason...But its super finicky...

EDIT:  Okay its not working now....I have no idea whats going on....No flash buttons work.

---

### Post by forumache on 2009-09-23
> **keenish27 said:**
> Ok.  Well I installed the flash-nonfree plugin and now the flash video's render (youtube), but when I click play, nothing happens.  Any ideas on this one?

you should have installed flashplugin-installer. This is the right package. I know, a lot of changes...

regarding the codecs, I see it too, it is a known bug, [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/412927](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/412927)

---

### Post by bobince on 2009-09-23
> In the past day or so, Update Manager was updated to use the aptdaemon backend

Is this what has caused saving media links to break?

I have all plugins disabled because I hate playing media in my web browser (and because more plugins means less secure). I set all types to ‘Always ask’ in the Applications tab so I can choose to save the file when I follow eg. an MP3 link or podcast bookmark.

In the past few days, this has broken. If I follow any link to a media file nothing at all happens. No prompt to open/save.

---

### Post by keenish27 on 2009-09-23
> **forumache said:**
> you should have installed flashplugin-installer. This is the right package. I know, a lot of changes...

regarding the codecs, I see it too, it is a known bug, [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/412927](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-base0.10/+bug/412927)

ok, so i removed flashplugin-nonfree and installed flashplugin-installer and i still cannot click any buttons in flahs.  I can't hit play or pause or anything.

any ideas?

---

### Post by forumache on 2009-09-23
You didn't specify the browser.
You are using firefox, right?

Type about: plugins (without space between : and p, I had to use it because : + p results in a smiley in the message) in the location bar.
Do you have:
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

?

---

### Post by keenish27 on 2009-09-23
> **forumache said:**
> You didn't specify the browser.
You are using firefox, right?

Type about: plugins (without space between : and p, I had to use it because : + p results in a smiley in the message) in the location bar.
Do you have:
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r32

?

This is what it says.

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r32

---

### Post by forumache on 2009-09-24
> **keenish27 said:**
> This is what it says.

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r32

You are using 64bit Ubuntu. I am not familiar with it.
You might want to uninstall flash and install the 64 bit version from Adobe manually.

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

---

