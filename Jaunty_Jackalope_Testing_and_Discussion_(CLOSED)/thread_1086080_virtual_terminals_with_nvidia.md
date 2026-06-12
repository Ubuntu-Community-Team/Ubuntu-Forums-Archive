---
title: "virtual terminals with nvidia"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-03
hi, i have nvidia 9600m gt with latest driver 180.xx. it works fine but i have blank screen when i use virtual terminal (ctrl+alt+f1). i have this problem in these cases:
- with/without vga=791
- with/without fbcon
- with/without nvidiafb

how can i fix this problem? thanks

---

### Post by cariboo on 2009-03-03
I would suggest you check to make sure you have the driver installed properly. The device section of your /etc/X11/xoeg.conf should look like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Jim

---

### Post by paul_in_london on 2009-03-03
Just tried this out (GPU is nvidia 8800gt).

Blank screen with tty1 on first attempt.

tty2-6 inclusive were Ok.

Then tried tty1 again and it appeared Ok.

Anyone?

---

### Post by jfernyhough on 2009-03-03
My ttys are normally blank when using the nvidia driver. There has been the odd driver version that had given me a visible tty but in general this warm black screen is the norm.

Bloody annoying, but it's alpha. :D

180.35, 29-rc6, 9600GT

---

### Post by paul_in_london on 2009-03-03
@jfernyhough...

Just out of interest mate, did you roll your own version of 29-rc6?

I thought the -29 kernels in the ppa didn't have DKMS built in?

---

### Post by cariboo on 2009-03-03
I'm running the 180.35 from the repositories and I get  tty1->tty7 just like normal.

Jim

---

### Post by nyarnon on 2009-03-04
> **paul_in_london said:**
> Just tried this out (GPU is nvidia 8800gt).

Blank screen with tty1 on first attempt.

tty2-6 inclusive were Ok.

Then tried tty1 again and it appeared Ok.

Anyone?

Confirmed behaviour on 177 hard to put a bug report in as it is a propitiatory driver I guess. But I think I can live with it.

---

### Post by biasquez on 2009-03-04
> **cariboo907 said:**
> I would suggest you check to make sure you have the driver installed properly. The device section of your /etc/X11/xoeg.conf should look like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

Jim

i already have this configuration..but problem isn't fixed..

---

### Post by Nullack on 2009-03-04
> **nyarnon said:**
> Confirmed behaviour on 177 hard to put a bug report in as it is a propitiatory driver I guess. But I think I can live with it.

The nvnews forum has details on how to run the nvidia bug script and where to send the details too

---

### Post by jfernyhough on 2009-03-04
> **paul_in_london said:**
> @jfernyhough...

Just out of interest mate, did you roll your own version of 29-rc6?

I thought the -29 kernels in the ppa didn't have DKMS built in?I did to begin with and DKMS would build (but something would break later in the install so the custom kernel would stay unconfigured and apt/aptitude etc would complain every time I installed something new).

I'm now using the 29-rc6 kernel from the kernel team's "repo" (i.e. file dump): [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . Everything works.

Oh, and as I type I notice rc7 is built. Nice. So in a moment I'll be running 29-rc7. ;)

---

### Post by Kow on 2009-03-04
> **paul_in_london said:**
> @jfernyhough...

Just out of interest mate, did you roll your own version of 29-rc6?

I thought the -29 kernels in the ppa didn't have DKMS built in?

DKMS is completely separate from the kernel. You don't "build a kernel with DKMS support." I don't know how Ubuntu handles the dkms.conf scripts because they may throw some in with the kernel packages... which would be wrong.

---

### Post by Xyem on 2009-03-30
> **jfernyhough said:**
> 
I'm now using the 29-rc6 kernel from the kernel team's "repo" (i.e. file dump): [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . Everything works.
I have the same/a similar problem where my TTYs are blank ( and I think the back-light is off too ) but only after X and nvidia have been used. Before that, the TTYs works fine and they also work fine with the 'nv' driver.

Am I right that you are now using the .29 kernel ( rc6 ) and the TTYs now work with nvidia?

I hadn't considered it be a problem with the kernel but it would also explain the system freeze I experience when I have a second X session in use ( freeze happened under the exact same situation twice ) which doesn't happen with nv.

Edit: By the way, dkms-status: nvidia, 180.11, 2.6.27-11-generic, i686: installed

---

