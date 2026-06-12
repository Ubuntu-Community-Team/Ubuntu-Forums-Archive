---
title: "Upgrades and newer kernel"
date: 2020-09-22
forum: Installation &amp; Upgrades
---

### Post by The Cog on 2020-09-22
I installed Xubuntu on my new laptop and a lot of things didn't work properly (hard lockup when screensaver started, screen brightness, sound volume, media keys etc). Then I read that my hardware (AMD Ryzen 7 4700U) needed a later kernel. So I followed the instructions here [https://www.tecmint.com/upgrade-kernel-in-ubuntu/](https://www.tecmint.com/upgrade-kernel-in-ubuntu/) and installed kernel 5.8.9. Everything (except the fingerprint reader) works beautifully. It's gorgeous.

Now I have messages saying updates are available, but it wants to install linux-image-5.4.0-48-generic. I think this would probably break things on the laptop again. I see that there is now a release 5.8.10 on [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/). Should I just download and install that? Is this the way things have to go now until the stock Ubuntu releases a version with a later kernel in it that has the appropriate drivers in it (20.10 maybe)? This is the first time I have gone "off piste" with a non-standard kernel and I'm not really sure how things should be done.

---

### Post by CatKiller on 2020-09-22
The linux-generic package always depends on the latest version in the standard repositories, so updates to that are expected. It's fine to have parallel branches installed - the HWE and non-HWE ones, say, as an example from the standard repositories.

As to whether you should upgrade with a newer version from mainline, that's up to you. They won't be upgraded automatically with the method you've used, so you won't get security updates unless you upgrade the packages yourself. I would lean towards upgrading, since you're already off-piste and feeling adventurous.

After 20.10 is released, 20.04 will get 20.10's kernel as part of the HWE stack. Same again after 21.04.

---

### Post by The Cog on 2020-09-22
That sounds good, thanks. I'll download and upgrade the mainline kernel, and keep an eye open for further upgrades. 

I usually install the latest shiny Xubuntu when it comes out, but for this laptop I might opt to keep with LTS as it's working so well. If I choose to stick, will the normal upgrade include the HWE or would I have to install an extra HWE package of some sort? I've seen mention of HWE but wasn't clear whether it's an optional extra. Now I understand why I couldn't find an hwe package for 20.04 though - it's not out yet.

Once a suitable up-to-date kernel becomes part of the normal packages, I'll switch back to that and re-enable secure boot.

---

### Post by Impavidus on 2020-09-22
The package will be called linux-generic-hwe-something and will come available shortly before 20.04.2, somewhere next January. From that release on it will be installed by default. If you installed 20.04 using an older live disk you'll have to install the package yourself.

You can have multiple kernels installed. I think grub will default to the latest (=highest version number).

---

### Post by The Cog on 2020-09-24
Thanks again. I have installed the latest kernel 5.8.11, then installed updates from the Ubuntu repos (including a 5.4 kernel). The machine still boots with the latest kernel by default, so all is good. I'll mark the thread solved.

---

