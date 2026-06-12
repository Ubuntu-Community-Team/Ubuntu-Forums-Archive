---
title: "Black screen on bootup"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by parameter on 2010-03-29
Is there supposed to be a graphic on bootup like in 9.10? When I boot I have a black screen with a flashing cursor at the top left. There is also a fsck message that appears and then quickly disappears. I see an ubuntu logo on purple when I shut down. Shouldn't there be something on start up or is it not ready for testing yet?

---

### Post by parameter on 2010-03-31
bump

---

### Post by dino99 on 2010-03-31
how can we help you: what is your config, fresh install or dist-upgrade ?

That seem to be a video driver issue: go to system admin hardware driver, you might see your(s) driver(s), are they activated and in use ?

Note that Lucid dont need xorg.conf, so yours can conflict (rename it in case you have a particular setting)

---

### Post by parameter on 2010-03-31
> **dino99 said:**
> how can we help you: what is your config, fresh install or dist-upgrade ?

Thanks for responding. I take it from your response that Plymouth **is** working on other people's computers. I didn't know if it was broken for everyone or just me.

The problem happens on two different computers. One is a fresh install as of Alpha 3 and upgraded to current packages. The other is a dist-upgrade from 9.10.

> That seem to be a video driver issue: go to system admin hardware driver, you might see your(s) driver(s), are they activated and in use ?

I went there but it shows a window with the message, "No proprietary drivers are in use on this system."

> Note that Lucid dont need xorg.conf, so yours can conflict (rename it in case you have a particular setting)

Where do I find this file? What does it do?

---

### Post by parameter on 2010-04-05
I figured this out. I added FRAMEBUFFER=y to /etc/initramfs-tools/conf.d/splash and then ran update-initramfs -u and then it worked.

---

### Post by zoomy942 on 2010-04-05
i havent seen plymouth in a while.  just a black screen.  i figured it was broke everywhere

---

### Post by cecilpierce on 2010-04-05
I get the black screen to then a flash of plymouth and black again. I looked in: 
/etc/initramfs-tools/conf.d/ amd I dont have splash in there all I have is /etc/initramfs-tools/conf.d/resume.

---

### Post by parameter on 2010-04-05
I had to add the splash file. It wasn't there by default.

---

### Post by zoomy942 on 2010-04-05
> **parameter said:**
> I had to add the splash file. It wasn't there by default.

howd you do that?

---

### Post by parameter on 2010-04-05
> **zoomy942 said:**
> howd you do that?

I used vi to create a new file. You can run the following commands to do everything that the fix requires:

```
sudo echo "FRAMEBUFFER=y" > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

When I did that, the next time I booted plymouth was working properly. I hope that helps.

---

### Post by zoomy942 on 2010-04-05
> **parameter said:**
> I used vi to create a new file. You can run the following commands to do everything that the fix requires:

```
sudo echo "FRAMEBUFFER=y" > /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u
```

When I did that, the next time I booted plymouth was working properly. I hope that helps.

cool.  so when i do this - will this make things worse if the devs decide to fix the bug in a future update?

---

### Post by parameter on 2010-04-06
> **zoomy942 said:**
> cool.  so when i do this - will this make things worse if the devs decide to fix the bug in a future update?

I don't know. I found the solution in [this bug](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108) posted by a Plymouth developer so I guess it's okay to use. You can always remove it and rerun update-initramfs to undo the changes.

---

