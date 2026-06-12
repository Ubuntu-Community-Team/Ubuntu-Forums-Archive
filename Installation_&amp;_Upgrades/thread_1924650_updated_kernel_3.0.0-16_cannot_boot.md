---
title: "updated kernel 3.0.0-16 cannot boot"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by v923z on 2012-02-13
Hi All,

I have just updated my kernel as requested by the update manager, and I cannot boot with it. For a while, everything seems normal, but at the end of the boot process, I see only the boot messages, the last of which reads as "Checking battery state... [OK]", and then nothing happens. When I try to boot with 3.0.0-15, everything is OK.
 
My question is, whether this is a singular problem that only I have, or there are others who experienced the same. Also, what steps should I take to debug this? I can live with the old kernel, and I don't believe that there is anything in the new one that would offer me too much, but on the other hand, if it doesn't work that it should be fixed.

My parameters are 64-bit, Oneiric Ocelot on a Lenovo G550 laptop.

Cheers,
v923z

---

### Post by dino99 on 2012-02-13
if you know how to search via googling, then you'll find if your issue is unique or not, and most of the time the solution has been found too.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo reboot

---

### Post by v923z on 2012-02-13
> **dino99 said:**
> if you know how to search via googling, then you'll find if your issue is unique or not, and most of the time the solution has been found too.


I have googled, and look what I have found:

In google
```

xconf ubuntu oneiric

```[http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there)

xconf is no longer used. In any case, I have done what you suggested, and nothing has changed. In fact, no xorg.conf file has been created. (Which, again, just confirms that xorg.conf is not used.) I can still boot with the old kernel, though.

As a remark, I don't think that I asked a trivial question, and I had searched for an answer before posting. Also, I posted the question,  because I thought that, if others had the same problem, then the issue would get some attention, and it could be more efficiently solved in a collaborative fashion... I believe that if something is wrong with the kernel, then it is a fundamental problem, and even if I can go and google, and find a workaround, it should still be solved properly.

Cheers,
v923z

---

### Post by Kuniku on 2012-02-13
Hello v923z

I have had the same boot issue, and in my case it was the proprietary nvidia driver (from the nvidia website not the one in the repos) causing the trouble.  A quick look at the lenovo G550 specs shows an nvidia gpu so this may be your problem too.

All I had to do to fix it was boot into the 3.0.0-16 kernel, wait until it stops and then switch to a virtual terminal, rerun the NVIDIA-Linux-x86-??????.run driver installer and reboot.

I hope this helps.

---

### Post by v923z on 2012-02-13
Hi Kuniku,

Yes, indeed it helped! Many thanks for your comments! I will mark this issue as solved.
Cheers,
Zoltán

---

### Post by HousieMousie2 on 2012-06-21
> **Kuniku said:**
> Hello v923z

I have had the same boot issue, and in my case it was the proprietary nvidia driver (from the nvidia website not the one in the repos) causing the trouble.  A quick look at the lenovo G550 specs shows an nvidia gpu so this may be your problem too.

All I had to do to fix it was boot into the 3.0.0-16 kernel, wait until it stops and then switch to a virtual terminal, rerun the NVIDIA-Linux-x86-??????.run driver installer and reboot.

I hope this helps.

I love you in ways I cannot even begin to express!  I have been using kernel 3.0.0-14 all this time because of this issue.  After an update last night (more unusable kernels) World of Warcraft stopped working on 3.0.0-14.  Wine complained about DirectX, even though I use OpenGl to play.  Was getting the "err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems" error.

All is fixed now thanks to your post!  *MUAH*

---

