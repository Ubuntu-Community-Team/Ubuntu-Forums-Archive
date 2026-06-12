---
title: "New in repository or upgrade"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by rdoolen on 2007-05-24
Today Synaptic informed me the there were new packages. However, these appeared to be new version of installed packages. This seemed odd. The thing is, they are important looking packages, like linux-image. For example, I have linux-image-2.6.20-15-generic installed, and there is a  linux-image-2.6.20-16-generic new in the respository. This is one of a few similar packages, maybe 5-10. 

Are these new or updates?

Since they are linux images, I am not going to touch them, but I want to know whats up.

---

### Post by Big Ed on 2007-05-25
> **rdoolen said:**
> Today Synaptic informed me the there were new packages. However, these appeared to be new version of installed packages. This seemed odd. The thing is, they are important looking packages, like linux-image. For example, I have linux-image-2.6.20-15-generic installed, and there is a  linux-image-2.6.20-16-generic new in the respository. This is one of a few similar packages, maybe 5-10. 

Are these new or updates?

Since they are linux images, I am not going to touch them, but I want to know whats up.

These are updated version of software you already have installed.  You'll see them turn up occasionally when security holes are found and plugged, bugs are fixed or minor functional enhancements are added.

I keep my system up to date.  Saves problems later.  The only time you need to reboot is after updating the kernel image.

Ed

---

### Post by rdoolen on 2007-05-26
Actually, I understand the concept of an update. The question I had was why these were labelled as "new in the repository" in Synaptic. Usually, upgrades show up as "Installed(upgradeable)." This is when Synaptic sort packages by Status.

I too like to keep things as up to date as posible. This is why I wondered if I wanted to instal these packages. I didn't install them. I think if I instal these component packages it may comfuse dependancies (even worse than a slightly out of date system). I think if there is a kernal update the images will be brought up to date via the instalation of dependancies.

---

### Post by lazyart on 2007-05-26
Like Ed said, these are updates to existing packages. linux-image-2.6.20-16-generic is an update to linux-image-2.6.20-15-generic.  The bump in the version number is to differentiate them.

I would suggest you install them unless there is a compelling reason not to.

---

### Post by Big Ed on 2007-05-31
> **rdoolen said:**
> Actually, I understand the concept of an update. The question I had was why these were labelled as "new in the repository" in Synaptic. Usually, upgrades show up as "Installed(upgradeable)." This is when Synaptic sort packages by Status.

I too like to keep things as up to date as posible. This is why I wondered if I wanted to instal these packages. I didn't install them. I think if I instal these component packages it may comfuse dependancies (even worse than a slightly out of date system). I think if there is a kernal update the images will be brought up to date via the instalation of dependancies.

Ahh, now I see what you are asking.  But I don't have an answer for you.  The new kernel image showed up as an update on my machine.  New in repository usually means software that hasn't been available in _any_ version before.

Ed

---

### Post by rdoolen on 2007-06-02
So, it turns out there is a main package, in this case linux-image-generic. All the packages I mentioned are dependacies of that package. when the master package was updated, it added all the dependant packages. The images showed up in "new" because I guess they are.

I don't think this is how it was suposed to work, but it seems like it must have been a fluke on my machine beause I didn't see any other mention of it in the forums.

Thanks for your help.

---

