---
title: "security system? zoneminder alternitive?"
date: 2015-07-05
forum: Installation &amp; Upgrades
---

### Post by thomas_margotta on 2015-07-05
im trying to setup zoneminder and its a pita. is there anything else similar out there that isnt such a b*tch to install and configure? thanks. also i intend on using aprox 10 cameras, take or give 5. and have xubuntu 14.04

---

### Post by yancek on 2015-07-05
A couple of other options are mentioned at the link below.  Motion and xeoma which are both apparently available in the repositories.  I believe Motion is a little simpler to install and set up but I think it is also more limited in what you can do.  I've installed it to test but don't really use it so I can't really compare to other software.

[http://askubuntu.com/questions/187415/what-cctv-software-is-available](http://askubuntu.com/questions/187415/what-cctv-software-is-available)

---

### Post by linwood2 on 2015-07-11
I've been looking through numerous alternatives as well (though have not discarded zoneminder as one).

Xeoma is a very interesting choice.  It runs the same on linux, windows and (surprisingly) android, same client, same look and feel.  It also has a unique workflow for specifying what happens to the video feed (archiving, motion detection, etc.).  The bad news is that it is very "trust the product", there is almost no configuration you can do, no visibility to status and logs (though some alerts).  Zoneminder lets you set almost anything and change everything, this is exactly the opposite.  It also has some bugs, mitigated by pretty quick response from the vendor.  The trial version is full featured BUT lasts only four hours (with one hour of archiving), so it is hard to do any scale tests with several days of history.  

But in regard to the OP's comments on how hard zoneminder is to configure - this is exactly the opposite.  Just run one self-contained install (it seems to have everything inside, no dependencies) and then run the client (if running linux GUI you can do both at once, but I run it with ubuntu server and then run the client on windows).

---

