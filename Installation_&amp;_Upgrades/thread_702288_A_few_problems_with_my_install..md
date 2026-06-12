---
title: "A few problems with my install."
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by Mb0742 on 2008-02-20
Hi.

I just installed Ubuntu today and I must admit I am having problems. worries but when I went to use it I hit a wall. 

My problems are that when I installed it said something about commenting out updates or something.

Also my res is stuck at 1280*768 and I can't break out to get 1280*768, I managed to get it to boot as 1280*1024 but it straight away flicks back to the bad res when I am prompted to log in. My first guess is the drivers so I went into restricted drivers manager and tried enabling my nvidia drivers. (nvidia accelerated drivers) but when I click new I get a message with: 

> 
the source for the package
Nvidia-glx-new

is not enabled.

So yeah also how do I make ubuntu log in by itself with me having to enter my username and pass?

EDIT: read next post it's major now :(

---

### Post by tangibleorange on 2008-02-20
OK! Firstly, to get your driver, you must enable the different repos. If you install offline, the repos are commented out of your sources list. Enabling them will enable you to download the restricted driver:

Open Synaptic (System --> Administration --> Synaptic Package Manager) and click Tools --> Repositories. (might not be tools but a menu at the top). Make sure all the boxes by the sources are ticked. Then try and install the driver by using the restricted drivers manager.

Secondly, to enable automatic login, try the following:

```
sudo gdmsetup
```

Then select the security tab, check "Enable Automatic Login", and select the user (you).

---

### Post by Mb0742 on 2008-02-20
OK thanks but now it's major :(

I installed it and now when I boot up my computer into Ubuntu my monitor reads out of range.... how can I change this now?

---

### Post by .nedberg on 2008-02-20
You could try this:

Press ctrl+alt+F1

login with your username and password

type:

sudo dpkg-reconfigure -phigh xserver-org

Now type exit and press ctrl+alt+F7, press ctrl+alt+backspace

Not sure if it will use nVidia drivers now...

---

