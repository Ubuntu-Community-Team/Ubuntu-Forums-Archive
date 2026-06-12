---
title: "Upgrade to 4.4.0.28 crashed amdgpr-pro (16.04)"
date: 2016-07-02
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2016-07-02
As above-titled, upgrade to 4.4.0.28 crashed amdgpr-pro.  Rebooting to 4.4.0.21 and screen returned to OK.  AMD Carrizo HP notebook.  Just to note an observation.

---

### Post by MAFoElffen on 2016-07-03
Curiosity prompts me to ask if the AMD graphics driver being used for your APU is a packaged or binary driver? Next to ask would be if your driver has a dkms modlue, and is automatically recompiled with a kernel update?

---

### Post by ping-wu on 2016-07-03
> **MAFoElffen said:**
> Curiosity prompts me to ask if the AMD graphics driver being used for your APU is a packaged or binary driver? Next to ask would be if your driver has a dkms modlue, and is automatically recompiled with a kernel update?

amdgpu-pro installed according to AMD's own instruction:

[http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

The driver was installed after upgrading xenial kernel from 4.4.0.21 to 4.4.0.28.  Problem was reproducible.  Now can only boot into 4.4.0.21 kernel (otherwise screen would be corrupted).

Both   [COLOR=#000000][FONT=courier]amdgpu-pro_16.20 (beta) and [/FONT][/COLOR][COLOR=#000000][FONT=courier]amdgpu-pro_16.30 (official release) versions were tested.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2016-07-03
Beta driver(?) Saw that in your link... Read it, went through the output listed there...

On something that would confirm of it is a kernel bug, or just the video driver's module needing to be recompiled under that kernel would be to boot under that kernel in text mode and
```

sudo apt-get install -reinstall amdgpu-pro-dkms

```
Then if still a problem with that kernel a bug with that kernel. If it works, then better, right?

---

### Post by ping-wu on 2016-07-03
> **MAFoElffen said:**
> Beta driver(?) Saw that in your link... Read it, went through the output listed there...

On something that would confirm of it is a kernel bug, or just the video driver's module needing to be recompiled under that kernel would be to boot under that kernel in text mode and
```

sudo apt-get install --reinstall amdgpu-pro-dkms

```
Then if still a problem with that kernel a bug with that kernel. If it works, then better, right?

No difference, screen still corrupted.  As I had suspected, this is most likely a kernel problem.

---

### Post by ping-wu on 2016-07-24
Everything seems to be OK now with Ubuntu 16.04.01.

Way to go, (the new) AMD!

---

