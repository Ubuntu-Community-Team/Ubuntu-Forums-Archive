---
title: "Do you see the boot splash screen during login"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Muflon on 2010-03-15
I don't know if this is just me but when I boot my laptop, I don't see the boot splash screen (see screen shot).  I briefly get a line of text then the screen goes black and after 20-30 seconds I get the logon screen. After logging in I always get a crash report complaining about PlymouthD that takes me to this bug report.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262)

Curiously when I shut down I do see the splash screen with the coloured dots.

Is anyone else experiencing this?

Muflon

---

### Post by katie-xx on 2010-03-15
I think, if you look, you might stumble across a mega thread on Plymouth problems :)

Kate

---

### Post by Muflon on 2010-03-15
> **katie-xx said:**
> I think, if you look, you might stumble across a mega thread on Plymouth problems :)

Kate

Thanks Kate.  I had already seen your thread but it didn't seam to be discussing my symptoms.  


Were you intending to be sarcastic?

Muflon

---

### Post by Owen.C93 on 2010-03-15
Yep lots get this, the bug is [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108)

Well I have a feeling it's a combination of them but that is one to check out.

---

### Post by katie-xx on 2010-03-15
> **Muflon said:**
> 
Were you intending to be sarcastic?
Muflon

I was intending to be helpful. All the Plymouth problems would be easier to track in one thread.
IMHO of course.
The description you give has been discussed several times.

Kate

---

### Post by mcoleman44 on 2010-03-15
After a blank screen for about 15 seconds I get the splash screen for about 1 second, and then I get taken to a txt login. I have to do ctrl+alt+f7 to get to a graphical login.

But when I shutdown I get the splash screen working great.

---

### Post by Dysphoria on 2010-03-15
I saw it the first time I booted a fresh Alpha install. After the initial updates it disappeared until I applied the fix mentioned on this blog:

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html)

I should add that, although it is pretty, it actually makes my boot time slower.

---

### Post by Muflon on 2010-03-15
> **Owen.C93 said:**
> Yep lots get this, the bug is [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108)

Well I have a feeling it's a combination of them but that is one to check out.

Thanks dude!  It is good to know that you are not alone.

Muflon

---

### Post by Owen.C93 on 2010-03-15
> **mcoleman44 said:**
> After a blank screen for about 15 seconds I get the splash screen for about 1 second, and then I get taken to a txt login. I have to do ctrl+alt+f7 to get to a graphical login.
See the bug I posted. The [plymouth thread is here]("http://ubuntuforums.org/showthread.php?t=1416872") if you wish to use it.

---

