---
title: "Ubuntu Desktop Autoinstall"
date: 2021-11-18
forum: Installation &amp; Upgrades
---

### Post by noah3456 on 2021-11-18
Good evening all,
Based upon what I have read about [Ubuntu autoinstall]("https://ubuntu.com/server/docs/install/autoinstall-reference"), it appears it is only possible to execute an autoinstall against Ubuntu Server ISO images. What is required for me to run Ubuntu autoinstall against an Ubuntu Desktop image?

---

### Post by noah3456 on 2021-11-19
Bump

---

### Post by grahammechanical on 2021-11-19
I have no experience in this matter but it seems to me from a little reading that autoinstall is more of a Do It Yourself idea. A person would have to modify the autoinstall config and YAML documents to suit their own situation. Furthermore, the examples provided are for the server installer which is different from the desktop installer which in turn asks different questions.

More is needed than simply substituting the desktop ISO image for the server ISO image. For example, a desktop install might require a proprietary video driver and non-free audio and video codecs. The sample YAML file does not include the code for asking permission to install such packages. I guess the YAML text can be modified according to the pattern shown in the text.

Regards

---

### Post by MAFoElffen on 2021-11-19
Not true... Let's 'correctly' say that "scripted" installations are possible with both Desktop and Server Editions of Ubuntu. (no matter the version of those scripts.)

Though Specifically and technically speaking... There is a caveat to that. At version 20.04, the Server Edition changed the installer from the Ubiquity, to the Live Installer, What that meant in scripting for that, it went from the pre-seed scripts for the debain-installer, to the automatic installer ymal files of the Live Installer...

Ubuntu held off on changing the Desktop Editon to the new installer until version Version 21.10. 22.04 will be the first Desktop LTS edition with the new Live Installer and it's auto-installer Scripts..

Does that clear up any confusion?

---

### Post by grahammechanical on 2021-11-21
> Does that clear up any confusion?

Not a chance! :)

In the past I was able to keep up with the direction Ubuntu was being taken in. But not anymore. Canonical is going in so many directions and it is beyond my understanding to work out the purpose of it all.

The publicity and the tutorials are written by people who know what they are talking about but there is an assumption that the reader also knows all about the subject anyway and only needs a few pointers. I recently read a Canonical article about how they were going to apply a wonder philosophy called Diataxis that will fix the problem with Canonical documentation. I am not going to hold my breath.

Regards

---

### Post by MAFoElffen on 2021-11-22
@grahammecahincical

I sent you a PM... I wasn't sure I should really post what I had to say about it.

---

### Post by ActionParsnip on 2021-11-22
If you want something more consistent then I suggest something like chef or puppet. It'll make system setup super easy.

---

