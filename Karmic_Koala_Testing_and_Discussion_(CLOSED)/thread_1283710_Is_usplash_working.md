---
title: "Is usplash working ?"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2009-10-05
I get text then xsplash but no usplash, I see it when I shut down or restart.

---

### Post by exploder on 2009-10-05
> I get text then xsplash but no usplash, I see it when I shut down or restart.

That is how it is supposed to be in this release.

---

### Post by Sand &amp; Mercury on 2009-10-05
> **exploder said:**
> That is how it is supposed to be in this release.
I don't think we're supposed to get text, are we?

---

### Post by alexmurray on 2009-10-06
Sometimes I get usplash on boot, sometimes I get corrupted video like usplash tried to run but failed and sometimes I get no usplash at all (like everyone else)... weird... eventually xsplash generally seems to come up though regardless...

---

### Post by blakamin on 2009-10-06
> **Sand & Mercury said:**
> I don't think we're supposed to get text, are we?

Yes, at this (beta) stage.

---

### Post by FrancoNero on 2009-10-06
I don't believe that honestly. We're a few weeks away from the release candidate and there are tons of topics like this about people (including me) getting errors and a text boot but no usplash ever, while there are pictures and videos all over the web and people raving about the new boot experience

---

### Post by exploder on 2009-10-06
> I don't believe that honestly. We're a few weeks away from the release candidate and there are tons of topics like this about people (including me) getting errors and a text boot but no usplash ever, while there are pictures and videos all over the web and people raving about the new boot experience

We think alike! :)

---

### Post by Aearenda on 2009-10-06
I read somewhere that if you append the line```
USPLASH=y
```to the file /etc/initramfs-tools/initramfs.conf, usplash will appear at boot, and this indeed works for me, although I still get a couple of well-known text lines that appear briefly first.
You can use ```
gksudo gedit /etc/initramfs-tools/initramfs.conf
```to edit the file. Just add the extra line at the end, and then run ```
sudo update-initramfs -u -k `uname -r`
```to generate the startup image. 

Before you do this, make sure you have bugged the text lines you see as requested in the [beta release notes]("http://www.ubuntu.com/testing/karmic/beta"), where it says > We've done some work on improving the overall look and feel of booting the system. Please open bugs with the tag "ubuntu-boot-experience" on any messages you see flashed after grub loads and before the new Ubuntu Splash screen (xsplash) displays. If you have trouble catching them before the splash screen loads, you can also check vt1 or dmesg output for copies of these messages. We also accept photos or video attachments if that's easier, however please make sure the text is readable.I think this is why we are seeing the text - some systems generate text, others don't, and the developers need to know so that they can fix it.

---

### Post by cecilpierce on 2009-10-06
Thank Aearenda, that did it for me and boot time was a bit faster !
And I don't see any text at start up.

---

### Post by jcris on 2009-10-07
Aearenda, thank you very much!!! your a hero :P !!! I been searching and searching for days on end for how to get rid of all that text and get the little mouse splashy (xubuntu), to come up before the new cool blue sparkley xubuntu xsplash. And yeah it seems boot time was cut at least by a third. Thanks for the tip, and you are the man!!!

---

### Post by Aearenda on 2009-10-07
I don't think it should make things go faster! Perhaps that's subjective. It is omitted by design in Karmic, unless you have encryption in use. One of the reasons for omitting it is to make boot faster. However, to me this approach is fine on a fast modern system, but we aren't all so lucky, and usplash keeps us amused while we are waiting at an otherwise blank screen.

BTW, all I did is relay what I found with Google...
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/433723](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/433723) 
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/427356](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/427356) (long)
[http://www.netsplit.com/2009/09/02/making-a-splash/](http://www.netsplit.com/2009/09/02/making-a-splash/)

---

### Post by Cenotaph on 2009-10-07
I think having no usplash by default is a terrible decision. From what i've read earlier usplash is only supposed to show in systems that take more than 30 seconds to boot? So what we have now during boot in some computers is about 10 seconds or more of only a cursor blinking giving no input to the user whatsoever. It's like Ubuntu wants us to think the OS wasn't properly installed or isnt working, bizarre option...

---

### Post by FrancoNero on 2009-10-11
with the last kernel update etc it's all good now

---

### Post by ranch hand on 2009-10-11
> **FrancoNero said:**
> with the last kernel update etc it's all good now
Yes, I think it is important to rember that we are 4 days from kernel freeze, 11 days from RC.

No that does not sound like a long time.  Having been in this pretty much from the beginning (I did wait for A1), I would say that 4 days is a long time.  Back just a little while 4 days started with a fairly stable OS that went to no boot and having to update on the terminal for a couple days (and chroot to one version) and back to relative stability.

We have had some rough patches but over all continuous improvement.

---

### Post by warbl on 2009-10-11
I don't see any uflash, and the boot speed is horrible, shutdown hangs as well.

---

