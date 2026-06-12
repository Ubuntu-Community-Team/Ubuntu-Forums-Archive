---
title: "VMware"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Jynx on 2007-10-20
So right now I have Windows Vista installed.  I have a separate hard drive that I'm going to be installing Ubuntu on.  I am interested in running VMware under Ubuntu so I can continue to use certain applications for school such as Visual Studio.NET.  My question is, under Ubuntu if I install VMware can I then just select the Hard drive running Vista and have the Vista installation I've always been running just load up under VMware while in Ubuntu and if so are there any docs/screen shots already put together for this.

---

### Post by Jimlas53 on 2007-10-20
You might want to take a look at VirtualBox ([www.virtualbox.org](www.virtualbox.org)).  I've used both VMware and VirtualBox, and VirtualBox has been pretty easy to work with.  I believe you will find some threads and instructions on using an existing windows partition.  VirtualBox also has a seamless windows mode where the windows desktop is suppressed, allowing  the apps show up on your Ubuntu desktop when you run them.

Something to consider!

-Doug

---

### Post by wanchai on 2007-10-20
I am using VMWare extensively under Ubuntu. My company's software products are Windows only and I have one VM per customer that I am supporting. Very nice, don't want to miss it.

Another alternative to VMWare is [qemu]("http://fabrice.bellard.free.fr/qemu/") plus kqemu. You can find that in the Gutsy repository.

Now to your question: your physical PC contains a specific set of hardware with chipset, network card, video card, etc. VMWare emulates a piece of hardware also with chipset, network, video, audio cards etc. Most likely VMWare emulates something different than you real hardware. The question whether your physical Windows installation can be used under VMWare is similar to the question whether a Dell machine can boot from a drive that you took out of your HP box. Probably not. I suggest that you install Windows inside VMWare from scratch. That's probably faster with less headaches. (Well, can't speak for Vista, I'm still using W2k since it does everything I need.)

---

### Post by ruibernardo on 2007-10-21
> **Jimlas53 said:**
> VirtualBox also has a seamless windows mode where the windows desktop is suppressed, allowing  the apps show up on your Ubuntu desktop when you run them.

Something to consider!

-Doug

Wow, didn't know that function. I've been trying to run a similar thing in qemu (the only one I knew that [could do it]("http://fabrice.bellard.free.fr/qemu/qemu-doc.html#SEC56")) but didn't work here. I had virtualbox installed and never saw that option. Can you tell where I can find it in virtualbox? 

Since virtualbox uses and is based in qemu code, I think that virtualbox might have this available and somehow I've missed it.

---

### Post by veloce on 2007-10-21
> **Jynx said:**
> So right now I have Windows Vista installed.  I have a separate hard drive that I'm going to be installing Ubuntu on.  I am interested in running VMware under Ubuntu so I can continue to use certain applications for school such as Visual Studio.NET.  My question is, under Ubuntu if I install VMware can I then just select the Hard drive running Vista and have the Vista installation I've always been running just load up under VMware while in Ubuntu and if so are there any docs/screen shots already put together for this.

It's been done with XP, not sure about Vista.  

MS license system is a pain if you want to switch between using windows directly and from within a vm.  After each switch it complains that you have changed the hardware.  If you want to change to this setup permanently, then you can go through MS licensing and switch it.

---

### Post by Craigus on 2007-10-21
> My question is, under Ubuntu if I install VMware can I then just select the Hard drive running Vista and have the Vista installation I've always been running just load up under VMware while in Ubuntu and if so are there any docs/screen shots already put together for this.

Yes; here's a how to:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

I do this with XP; haven't tried Vista, but it is covered in the tutorial.

---

