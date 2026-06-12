---
title: "How can I upgrade my distribution with the command line?"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by nv22nv on 2010-02-20
I feel kind of stupid asking that question, but I can't seem to find anything helpful on the subject, so please bear with me. 

My question is: How can I upgrade my distribution (Kubuntu 8.04) to the next version using the command line only? I failed using the graphical frontend (see [this topic](http://ubuntuforums.org/showthread.php?t=1410807)) and hope that using the command line will at least give me some kind of error message that will be helpful.

What I thought is that I can use
```
apt-get update
apt-get dist-upgrade
```

but when using the latter command I'm only told that everything is up to date and there is nothing to do.

Then I tried
```
apt-get install update-manager-core
do-release-upgrade
```
but it keeps telling me
```

Checking for a new ubuntu release
No new release found
```
Do I need to manually adjust the content of /etc/apt/sources.list beforehand?

Can someone please help me? A helpful link, or basically anything would  be very appreciated. Thanks in advance.

**Edit:** I think I got it myself: In /etc/update-manager/release-upgrades the line
```
Prompt=lts
``` needs to be replaced with ```
Prompt=normal
``` 
Will try it now...

---

### Post by .nedberg on 2010-02-20
> **nv22nv said:**
> 
**Edit:** I think I got it myself: In /etc/update-manager/release-upgrades the line
```
Prompt=lts
``` needs to be replaced with ```
Prompt=normal
``` 
Will try it now...

It should work now with 
```
apt-get install update-manager-core
do-release-upgrade
```

But why not wait until 10.04 comes around? You could update to the next LTS-version.

---

### Post by nv22nv on 2010-02-20
Well basically you're right, but time is a great issue for me, and these days I have to sit at my desk for hours without having to use my computer, which is rare. So it's a personal thing.

---

### Post by .nedberg on 2010-02-20
Just beware that this will upgrade to Kubuntu 8.10, and 8.10 will end its support in April. You can upgrade to 9.04, then 9.10 when it is finished. But it would be easier with a new install of 9.10, and probably better as you could then benefit from ext4 and grub2.

---

### Post by nv22nv on 2010-02-20
I considered installing it again from scratch, but then I'm sure there's about 1000 configuration files which I don't think about right now but which I will need to edit afterwards... so it will probably take more time than the upgrades. Do you disagree?

---

### Post by .nedberg on 2010-02-20
Can't disagree with that!

But upgrading from 8.04 to 9.10, via 8.10 and 9.04 can lead to problems anyway. But it can also work out just fine.

I did a fresh install when I upgraded to 9.10. Made myself a separate /home, that way fresh installs are less pain.

The decision is completely up to you. I have no problem understanding why you want to do it with upgrades! A fresh install might be quicker, but you might also forget to backup some config files.

---

### Post by nv22nv on 2010-02-20
Alright, including my attempts with the graphical upgrade manager this must have been about the 15th failed attempt by now. I'll go with a fresh install when I got the time again.

Using the command line went rather well until the configuration step for the upgrade to 9.10, but when trying to configure *dbus*, *init* crashed and all my attempts to rescue the half-done upgrade failed.

After all this, I'll probably never use the upgrade function again and always do a fresh install. It probably would have been less stressful and a lot faster. Considering the time I spent on the upgrades, I would have adapted all configuration files of a fresh installation by now. I kind of feared to set up my encrypted home directories again because it took me ages to set these up the way I wanted to, but using my backed up data it wouldn't have been too much of a hassle. Well, you never stop learning.

Thanks for your help!

---

