---
title: "HOW-TO: Firefox KDE integration in Karmic"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by falkTX on 2009-11-13
The new openSUSE 11.2 brings KDE integration to Firefox (KDE dialogs and other goodies).
See [http://en.opensuse.org/KDE/FirefoxIntegration](http://en.opensuse.org/KDE/FirefoxIntegration) for more info.

So we ask... what about Kubuntu? Can it have that cool integration too?
The answer is **YES**!

There's already a PPA for this!

You can install the patched Firefox using this commands:
```
sudo add-apt-repository ppa:debfx/firefox-kde
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install firefox-3.5 firefox-3.5-kde
```
After restarting Firefox... WOW! There you go!


I hope this was useful. The attachments show an example.

---

### Post by jepong on 2009-11-26
Thanks for the info...

---

### Post by wersdaluv on 2009-11-28
Coool :)

---

### Post by ronnoc on 2009-12-03
In addition to adding the repository above, there are a few other things you can do as well. Together, they really make Firefox look and behave well =)

I wrote about those here
[http://bit.ly/6CcwUW](http://bit.ly/6CcwUW)

---

### Post by falkTX on 2009-12-03
> **ronnoc said:**
> In addition to adding the repository above, there are a few other things you can do as well. Together, they really make Firefox look and behave well =)

I wrote about those here
[http://bit.ly/6CcwUW](http://bit.ly/6CcwUW)

Nice, although I already knew those it might come handy for new users.

---

### Post by James78 on 2009-12-17
I used to love this addon, but however it has completely stopped working from me, I've uninstalled Firefox, xulrunner, etc so many times, reinstalled, all that. It still uses the Gnome dialogs AGAIN. It's so frustrating. =(

---

### Post by falkTX on 2009-12-18
> **James78 said:**
> I used to love this addon, but however it has completely stopped working from me, I've uninstalled Firefox, xulrunner, etc so many times, reinstalled, all that. It still uses the Gnome dialogs AGAIN. It's so frustrating. =(

Are you sure you istalled:
```
firefox-3.5-kde
```

That's the key package

---

### Post by treris on 2009-12-18
I've also posted this in another thread already, but I had this working like a charm but after updating to FF 3.5.6 all the kde integration is gone again......

PS this is other thread I mentioned: [http://ubuntuforums.org/showthread.php?p=8521687&posted=1#post8521687](http://ubuntuforums.org/showthread.php?p=8521687&posted=1#post8521687)

---

### Post by lovinglinux on 2009-12-18
I tried, but it didn't worked well, so I removed the ppa repository and firefox, then installed it again. Now, all my confirmation dialogs have the Cancel button on the right and the OK button on the left, just like Firefox Windows, which is pretty annoying.

Is not a profile issue, since this happens on all, profiles. Anyone knows how to revert this?

EDIT: I have found an workaround, but is not the ideal. It consists of adding the following line to userChrome.css

```
.dialog-button-box { -moz-box-direction: reverse; }
```

Does anyone knows where that version of firefox saved this dialog hack so I can remove it?

---

### Post by falkTX on 2009-12-18
Probably the PPA version hasn't been updated yet.

We should wait... once more...

---

### Post by lovinglinux on 2009-12-18
> **lovinglinux said:**
> I tried, but it didn't worked well, so I removed the ppa repository and firefox, then installed it again. Now, all my confirmation dialogs have the Cancel button on the right and the OK button on the left, just like Firefox Windows, which is pretty annoying.

Is not a profile issue, since this happens on all, profiles. Anyone knows how to revert this?

EDIT: I have found an workaround, but is not the ideal. It consists of adding the following line to userChrome.css

```
.dialog-button-box { -moz-box-direction: reverse; }
```

Does anyone knows where that version of firefox saved this dialog hack so I can remove it?

Nevermind. I was able to revert the changes by re-installing xulrunner

---

### Post by debfx on 2009-12-19
Sorry, I forgot to upload the new version of the kmozillahelper package. :(

After a system update the KDE integration should work fine again.
And always make sure that the kmozillahelper package is installed.

---

### Post by Kyril on 2009-12-19
> **debfx said:**
> Sorry, I forgot to upload the new version of the kmozillahelper package. :(

After a system update the KDE integration should work fine again.
And always make sure that the kmozillahelper package is installed.


Sadly it don´t work for me. kmozillahelper is updated to 0.6.0 but I can´t get the deamon running.

Witch command is needing to start it and why it´s not start automatically?


Edit: Alt + F2 & /usr/lib/mozilla/kmozillahelper bring it up, but KDE-Integration nevertheless don´t work! :(

---

### Post by treris on 2009-12-19
The latest update (of the XUL package) has made things all right again!

Thanks debfx!

---

### Post by didi156 on 2010-02-19
Any change that will be included in Kubuntu repo soon?

---

### Post by treris on 2010-02-19
Are you referring to an update to firefox 3.6? I don't think that's likely to happen....

---

### Post by ssri on 2010-02-23
huh?  There's a firefox theme in kde-looks.org

[http://kde-look.org/content/show.php/Oxygen+KDE+%28Firefox+Theme%29?content=117962](http://kde-look.org/content/show.php/Oxygen+KDE+%28Firefox+Theme%29?content=117962)

---

