---
title: "Ununtu still wants an alpha CD"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by JdeP on 2010-10-20
Despite being a bit of a newbie, a few months ago I thought I would test the alpha release, so I downloaded the file and burned the .iso to CD.

I had problems with the installation, so I cancelled it half-way through, and continued to use 10.04, which worked fine.

Now, whenever I try to update/upgrade the system, it keeps asking me to insert the old CD, which I no longer have. For example, if I try to 
sudo apt-get update
it seems to work fine, until it stalls with the message:

Media Change: Please insert the disc labelled
 'Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100925)'
in the drive ‘/cdrom/’ and press enter

Apart from this recurring problem, I think I have have now successfully upgraded to 10.10.

I realise that it's probably my own fault (or is it -- shouldn't 10.10 realise that I am way beyond the alpha release now?), but can anyone tell me how to fix this glitch?

Thanks in advance.

---

### Post by sikander3786 on 2010-10-20
Seems like you have enabled the Ubuntu CD as a repository in Software Sources.

You can check in Software Center > Edit > Software Sources or to be sure, post the output of

```
cat /etc/apt/sources.list
```

---

### Post by plucky on 2010-10-20
> Media Change: Please insert the disc labelled
'Ubuntu 10.10 _Maverick Meerkat_ - Alpha i386 (20100925)'
in the drive ‘/cdrom/’ and press enter


You have to open Software Sources and un-tick the CDrom drive as a Source.

Open **Synaptic Package Manager** and go to **Settings > Repositories** and un-tick the CDrom on the first page.


Good Luck

---

### Post by JdeP on 2010-10-20
Thanks guys! I went with the second solution because it seemed more fool-proof (I don't like editing system files by hand if I can avoid it) and this did the trick.

Cheers!

---

