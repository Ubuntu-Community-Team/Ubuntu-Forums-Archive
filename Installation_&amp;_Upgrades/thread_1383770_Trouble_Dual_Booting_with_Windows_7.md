---
title: "Trouble Dual Booting with Windows 7"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by Mars92 on 2010-01-17
After recently getting my flash new rig, I figured I could solve a lot of problem by Condensing my my recording laptop (Running Ubuntu 9.04) onto the large amounts of space on my new computer, thus having to dual boot with Windows 7 Professional, which was already installed and with too much time already invested in it to even consider doing a clean install.

I continued the way you would dual booting anything else, but to no end, as the Windows 7 bootloader doesn't seem to pick up on the Ubuntu install, and continues on it's merry way, booting Windows 7 and not givng me any options. 

My better-at-tech brother told me that Microsoft did some big changes to the Windows 7 bootloader, which may be the source of all my troubles. after MUCH time spent googling the problem, I can't find anything relating to my problem, and strangely all the guides on dual booting Ubuntu with Windows 7 follow almost exactly the same steps I initially took to dual boot 7 and Ubuntu.

So now all this has caused my to run crying to the Ubuntu forums in need of assistance. Help? I thank you in advance for any light you can shed.

---

### Post by oldfred on 2010-01-17
Was this a Wubi install inside windows or a side by side (real) install into new partitions and shrinking the windows partition?
I do not know wubi so I can not help there.

---

### Post by Mars92 on 2010-01-17
Side by side install. Sorry forgot to mention that part.

---

### Post by Leppie on 2010-01-17
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by Mars92 on 2010-01-17
Sorry I deleted my Ubuntu Partition so I can't get the results. Is it the same as dxdiag in windows?

---

### Post by Leppie on 2010-01-17
no, it's not the same as dxdiag in windows as windows does not access foreign filesystems very well.
you can boot off the ubuntu livecd, download and run the script.

---

