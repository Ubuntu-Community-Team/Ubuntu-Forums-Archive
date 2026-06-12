---
title: "omg! my ubuntu updater just stucked!! what should i do O_O :\\\"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by megouserman on 2009-10-20
it just stucked on applying changes mission! omg panic!!
last time i reseted after updater stucked i gained non-working ubuntu omg omg omg
it not continue since 14:00
and now is 20:37!!!

[IMG]http://img99.imageshack.us/img99/2824/screenrq.jpg[/IMG]

---

### Post by prshah on 2009-10-20
> **megouserman said:**
> it just stucked on applying changes 


Check through the other virtual desktops to see if a dialog box is waiting for your input. Sometime, the upgrade / update seems stalled, but actually it has popped up a dialog box on another virtual desktop, and will not proceed until that dialog box is attended to. Typical symptoms include window responsiveness (eg, window can be moved around) but it will not accept focus, and clicking on it seems to produce no effect.

You can check this by pressing alt+tab a couple of times, releasing, and pressing again. (Alt+Shift+Tab on some systems).

---

### Post by megouserman on 2009-10-20
no. no prompting windows. nothing. window not freezed.

---

### Post by philinux on 2009-10-20
Just click cancel then or force quit if necessary then in a terminal do this.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any errors.

---

### Post by megouserman on 2009-10-20
just restarted upgrade proccess and it ended with success now! cheers!
it's strange :popcorn:


p.s. anyone knows where to find skype for ubuntu 9.10 x64? thank u.

---

### Post by philinux on 2009-10-20
> **megouserman said:**
> just restarted upgrade proccess and it ended with success now! cheers!
it's strange :popcorn:


p.s. anyone knows where to find skype for ubuntu 9.10 x64? thank u.

Click the medibuntu link below in my sig and do the medibuntu dance. Skype is in their repos.

If you dont want to do the dance then go here.
[http://packages.medibuntu.org/karmic/skype.html](http://packages.medibuntu.org/karmic/skype.html)

---

### Post by ViRMiN on 2009-10-20
> p.s. anyone knows where to find skype for ubuntu 9.10 x64? thank u.

It's in the Medibuntu repo.

---

### Post by forumache on 2009-10-20
> **megouserman said:**
> just restarted upgrade proccess and it ended with success now! cheers!
it's strange :popcorn:


p.s. anyone knows where to find skype for ubuntu 9.10 x64? thank u.

I'm using on my ubuntu 9.10 32 bit the version of Skype for 8.10 from skype's website: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

You might have luck with the one for Ubuntu 8.10 64bit.

---

### Post by philinux on 2009-10-20
Why do that when you can get....

[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_amd64.deb)

64 bit from medibuntu.

---

