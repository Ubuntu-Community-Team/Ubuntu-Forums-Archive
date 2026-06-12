---
title: "Help with Nvidia Legacy Drivers"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by jholsenback on 2010-03-23
Boy this is probably the most discussed topic on this forum. I've done a lot of looking and tried several things without any joy.

From what I gather I'm supposed to be installing this driver package: NVIDIA-Linux-x86-71.86.13-pkg1.run as I have an older Vanta card. Before I started I looked in system->administration->hardware drivers and this list is empty ... OK to go for it right?

So I do ctrl-alt-f1 and get the login prompt and was able to kill gdm (not by /etc/init.d/gdm stop OR stop gdm) but had to kill from pid in process table ... I DID get it to stop however, and was able to run the above mentioned package via sudo. I then was able to make the nvidia-xconfig package. I got that to build and install, and I was able to run that binary (nvidia-xconfig) and it wrote me a XF86Config in /etc/X11 but after rebooting it went into x-failsafe mode. It was complaining about a couple of modules (type1 was one of them). It appeared to be in kind of in a loop and didn't let me do anything until I bailed and I was eventually back in using ctrl-alt-f1 where I ran sudo NVIDIA-Linux-x86-71.86.13-pkg1.run --uninstall and rebooted ... again the x-failsafe mode with the same messages. Once I gained access I decided to move XF86Config aside and reboot.

Well at least I'm back in and writing this message so I count myself lucky ... dodged a bullet as they say!

What have I done wrong here? I really have looked at this from many angles, so I'm NOT just screaming help and expecting someone to magically solve my problem for me ... I've done my homework without much success!

So if someone could shed some light on what I've done so far, and what needs to be done to move my situation forward that would be great!

Cheers Jim

---

