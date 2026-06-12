---
title: "Installation of Adobe AIR: permission denied"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by qrwe on 2009-11-18
Hi there,

I tried to install Adobe AIR, after downloading a file 'AdobeAIRInstaller.bin' from their download URL: [http://get.adobe.com/air/]("http://get.adobe.com/air/"). To my disappointment, I can't install it:
```

# chmod 777 AdobeAIRInstaller.bin
# file AdobeAIRInstaller.bin 
AdobeAIRInstaller.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped
# ./AdobeAIRInstaller.bin 
-su: ./AdobeAIRInstaller.bin: Permission denied

```

..and can't figure out what's wrong. Has anyone succeeded in installing AIR? Please tell me how. Or if you might have an idea of what I've forgotten, please drop a message. Thank you!

---

### Post by renkinjutsu on 2009-11-18
looks like it's trying to run "su" .. so it might work if executed as root, using sudo

but heck.. why would it need to run "su"?

---

### Post by qrwe on 2009-11-18
No idea. Should have mentioned of course: I'm doing all this after running:
```
sudo su -
```
Any ideas?

---

### Post by renkinjutsu on 2009-11-18
try with just 

chmod +x file.bin

and

sudo ./file.bin

---

### Post by qrwe on 2009-11-19
> **renkinjutsu said:**
> try with just 

chmod +x file.bin

and

sudo ./file.bin

I've done that too; ran chmod 777 afterwards, which gives even more permission, to explain that it can't be done any further. A summary:
[LIST]
[*]The file has rwx permission
[*]I am doing everything as root
[*]The file is owned by root
[*]I'm doing all of this in a directory where I'm allowed to
[/LIST]
Any ideas? I know it's tricky and I just hoped that someone had a problem with AIR too. You can go to the URL and try to install it too, it's a beautiful tool anyway.

---

### Post by kostkon on 2009-11-19
Why not install the new *Adobe Air 2* beta. It's working just fine and [there is a deb on its download page for easy installation]("http://labs.adobe.com/downloads/air2.html") (i.e. the deb file in the *Adobe AIR 2 Runtime* section)

---

### Post by qrwe on 2009-11-19
> **kostkon said:**
> Why not install the new *Adobe Air 2* beta. It's working just fine and [there is a deb on its download page for easy installation]("http://labs.adobe.com/downloads/air2.html") (i.e. the deb file in the *Adobe AIR 2 Runtime* section)

Wow, that was definitely something I was looking for, worked immediately when installing it and then installing AIR apps!
It's strange that they haven't released any .deb-packages for the stable version, especially when they mention in a blog (official Adobe dev-blog) that their Linux products are mainly designed for SuSE, Redhat and Ubuntu. But it's not a concern for me anymore now. :-)
Once again: thanks everyone for your help!

PS. Wonder if I should mark this thread [SOLVED], there might be more AIR-issues for other fellows in the future and the subject is very general after all..

---

### Post by kostkon on 2009-11-19
> **qrwe said:**
> PS. Wonder if I should mark this thread [SOLVED], there might be more AIR-issues for other fellows in the future and the subject is very general after all..
Actually, your problem was simple, at least I believe so.

You didn't need to run it as root neither change its ownership. You only needed to make it executable and run it. It would have asked for your admin password later in the installation process.

---

### Post by qrwe on 2009-11-19
> You only needed to make it executable and run it.
That was what I did at first. When it didn't work, I went on with.. well, the rest. :-)

---

