---
title: "Ubuntu 10.04 -no intro menu before installation"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ff1-ff1 on 2010-04-30
I downloaded 10.04 RC and final version.In both after inserting cd and booting from cd there was no menu which was from many years (to chose from: installation, check memory etc).In Kubuntu 10.04 such menu exists .My question: is this correct that after booting from cd ubuntu 10.04 disk starts without menu? 
I downloaded file: ubuntu-10.04-desktop-i386.iso  Maybe this is wrong version?

---

### Post by kansasnoob on 2010-04-30
[http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](http://www.ubuntu.com/getubuntu/releasenotes/1004#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

> The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is noninteractive by default. To configure advanced boot options, press any key at the first boot screen.   

---

### Post by kansasnoob on 2010-04-30
I found out the hard way by filing a bug when it first appeared that way in Beta1:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

:lolflag:

---

### Post by ff1-ff1 on 2010-04-30
thank you for your answers.By the way: isn't this strange that some (maybe the same person) introduce into new , long-support version this idiotic solutions like: luck of boot initialization menu in default and window buttons on the left side?

---

### Post by kansasnoob on 2010-04-30
> **ff1-ff1 said:**
> thank you for your answers.By the way: isn't this strange that some (maybe the same person) introduce into new , long-support version this idiotic solutions like: luck of boot initialization menu in default and window buttons on the left side?

You're not alone in that opinion :)

You know not all themes put the window buttons on the left?

I just use the following command to put them back where I want them:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

---

### Post by ff1-ff1 on 2010-05-03
THX again-moving buttons is not difficult. Problem is, that such a need exists! Why after installation i should spend next hour to tune such stupid (mistakes -in my opinion)? This is not windows -or it is going to be? 
Thank you.

---

