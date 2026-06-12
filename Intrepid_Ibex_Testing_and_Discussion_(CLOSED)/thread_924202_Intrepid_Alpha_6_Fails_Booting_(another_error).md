---
title: "Intrepid Alpha 6 Fails Booting (another error)"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2008-09-19
I've been experiencing a serious booting error with latest nightly builds and also with Alpha6. 
(Tried CD/R CD/RW and more than one PC)
It fails booting and stops showing this error

[IMG]http://kosimo.googlepages.com/intrepiderror.JPG[/IMG]

I can't boot live sessions and not even the installation only procedure.  I don't really think that is a drive error (CD) because I've tried burning it with another media in another computer and booting there having exactly the same problem.

In my case I'm using a Sony Vaio VGN-FZ335 Core 2 Duo with intel chipset 965, S-ATA HDD and nVidia GeForce 8400m GT.

The other computer (with exactly the same problem) was a desktop computer Pentium 4 2.8HT with a GeForce 4MX

Any idea about this bug? It has been mentioned already?

Thank you guys

---

### Post by Nullack on 2008-09-19
In the kernelteam bug policies on the ubuntu wiki is guides on how to progress this.

---

### Post by Kosimo on 2008-09-19
> **Nullack said:**
> In the kernelteam bug policies on the ubuntu wiki is guides on how to progress this.

Could you please give me the link?

Thank you

---

### Post by Gourgi on 2008-09-19
> **Nullack said:**
> In the kernelteam bug policies on the ubuntu wiki is guides on how to progress this.
is this the link ?
[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

i face the same problems trying to boot alpha6

---

### Post by Kosimo on 2008-09-19
> **Gourgi said:**
> is this the link ?
[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

i face the same problems trying to boot alpha6

Thank you.

Yeah, you seems not to be the only one

---

### Post by Kosimo on 2008-09-19
> **Gourgi said:**
> is this the link ?
[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

i face the same problems trying to boot alpha6

I made a new bug in launchpad notifying this problem. 

[Bug #272155]("https://bugs.launchpad.net/ubuntu/+bug/272155")

---

### Post by Gourgi on 2008-09-19
subscribed there :)

---

### Post by Swarms on 2008-09-19
Yeah I had that issue too with the installation of alpha 5. It seemed like it was just spitting out these errors between the other information it gave and I just had to wait it out.

---

### Post by Kosimo on 2008-09-22
Anyone else is having the same problem?

---

### Post by Perpetual on 2008-09-22
> **Kosimo said:**
> Anyone else is having the same problem?

Yes.  I can boot Hardy just fine on my HP DV6910US but Intrepid will not boot the live cd.

---

### Post by Kosimo on 2008-09-23
> **Perpetual said:**
> Yes.  I can boot Hardy just fine on my HP DV6910US but Intrepid will not boot the live cd.

Do you may have a nVidia Card?

---

### Post by Perpetual on 2008-09-23
> **Kosimo said:**
> Do you may have a nVidia Card?

Yes I do.  AMD 64 processor, Nvidia GeForce Go 7150M.  Neither the 32 bit or 64 bit will boot.

Yours Nvidia as well?

---

### Post by Kosimo on 2008-09-23
> **Perpetual said:**
> Yes I do.  AMD 64 processor, Nvidia GeForce Go 7150M.  Neither the 32 bit or 64 bit will boot.

Yours Nvidia as well?

Yes.
All computers that I've seen having the same problem have a nVidia videocard. Maybe is the reason?

---

### Post by lancest on 2008-09-24
Didn't bother running the live desktop this time. Too bad- Intrepid 6 installation won't boot. Nvidia 7300 on notebook.

---

### Post by Kosimo on 2008-09-24
> **lancest said:**
> Didn't bother running the live desktop this time. Too bad- Intrepid 6 installation won't boot. Nvidia 7300 on notebook.

Another user with nVidia card and boot problems....
Is your error the same one this topic shows?

---

### Post by Nullack on 2008-09-24
Im not convinced the root cause has been identified. I have an Nvidia card and I boot fine. As well, there is levels of video card startup like how it starts with basic framebuffer and then proceeds from there. Usually with a video specific problem X fails to load but the kernel still will.

---

### Post by lancest on 2008-09-24
As I watch it try to boot and it just stops somewhere after bluetooth. Maybe that was Nvidia next. Guess I gotta wait, Hardy is pretty good.

---

### Post by Gina on 2008-09-24
I have GeForce 6200 graphics in my AMD64 and I did manage to run the Alpha 6 64bit Live CD also I installed onto HD from the Alternate CD.  However, I had problems with the 177 and 173 drivers.  The 177 (recommended) was a no-no but after several attempts I did get the 173 to download and install.  The download was sporadic and took several minutes.  Without the nvidia driver my screen (1280x1024) only displayed the top half of the desktop.

I have not updated to the 27-4 kernel as the update on my previously working (and updated from Alpha 5) version refused to boot the 27-4 kernel - hence the reinstall.

---

### Post by Kosimo on 2008-09-24
> **Gina said:**
> I have GeForce 6200 graphics in my AMD64 and I did manage to run the Alpha 6 64bit Live CD also I installed onto HD from the Alternate CD.  However, I had problems with the 177 and 173 drivers.  The 177 (recommended) was a no-no but after several attempts I did get the 173 to download and install.  The download was sporadic and took several minutes.  Without the nvidia driver my screen (1280x1024) only displayed the top half of the desktop.

I have not updated to the 27-4 kernel as the update on my previously working (and updated from Alpha 5) version refused to boot the 27-4 kernel - hence the reinstall.

So, you are using a nVidia card and you can´t boot 27-4 kernel.  
+1 then

---

### Post by Perpetual on 2008-09-24
> **Kosimo said:**
> So, you are using a nVidia card and you can´t boot 27-4 kernel.  
+1 then

I just found that I can not boot Fedora 10 Alphas either yet Fedora 9 boots fine.  :(

---

### Post by jerrylamos on 2008-09-25
Intrepid Alpha 6 CD Live doesn't boot on IBM Thinkpad R31.  That's 32 bit, 1 gHz Celeron, Intel graphics.

An Alpha 5 updated upgraded to Alpha 6 levels 2.6.27-4 Gnome 2.24.0.1 won't boot any more either.  In recovery mode, the root command line prompt is O.K.  Normal boot freezes the screen and keyboard at the point where Gnome should have loaded the background screen.  Since the computer is locked up at point of failure it can't report any logs or messages on what failed.

Icewm will come up.  It's something about Gnome loading a panel that hangs everything.  Yes I submitted a launchpad bug 259385, also reported on Alpha 6 ISO testing.

Jerry

---

### Post by Kosimo on 2008-09-26
I'm still experiencing the same issue. I haven't try any other distro but I can say that Hardy boots fine.

---

### Post by listener on 2008-09-27
I am having this problem, since alpha 5 I think. I am running on last-good-boot since then.  In my case it seems to be a problem with possibly the PCIEx1 drive controller/adapter.  Silicon Image I think.  My root partition and possibly the entire drive disappears between grub and busybox.  I've been trying to work it out now and then, since I can boot the alpha 4 kernel < 27.  So enjoying Intrepid very much none-the-less.

I did report this earlier but the topic was unclear.  Also filed a bug report some time ago, no real response.  

nVidia card: yes (7600gt)
amd64: yes
I built it - don't recall everything in it. Several drives. 4gigs ram.

I do really appreciate all the work the developers must put into these!

---

### Post by Kosimo on 2008-09-27
> **listener said:**
> I am having this problem, since alpha 5 I think. I am running on last-good-boot since then.  In my case it seems to be a problem with possibly the PCIEx1 drive controller/adapter.  Silicon Image I think.  My root partition and possibly the entire drive disappears between grub and busybox.  I've been trying to work it out now and then, since I can boot the alpha 4 kernel < 27.  So enjoying Intrepid very much none-the-less.

I did report this earlier but the topic was unclear.  Also filed a bug report some time ago, no real response.  

nVidia card: yes (7600gt)
amd64: yes
I built it - don't recall everything in it. Several drives. 4gigs ram.

I do really appreciate all the work the developers must put into these!

+1 Another nVidia User

:mad:

---

### Post by Perpetual on 2008-09-27
[Update to the launchpad bug.]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/272155")

---

### Post by Kosimo on 2008-09-29
> **Perpetual said:**
> [Update to the launchpad bug.]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/272155")

Perpetual!  I'm writing this using Intrepid Daily Build, (September 29th)
Give it a try, I could boot my system with no issues at all. The only thing is that the image is 710MB, so I had to use overburn option.

Good luck, and let me know how it goes!

---

### Post by Perpetual on 2008-09-29
> **Kosimo said:**
> Perpetual!  I'm writing this using Intrepid Daily Build, (September 29th)
Give it a try, I could boot my system with no issues at all. The only thing is that the image is 710MB, so I had to use overburn option.

Good luck, and let me know how it goes!

I tried the 9/27 daily (I figured I was being premature) and was able to get further with it by holding down keys during boot.  It failed though with an xserver problem.  It too was 710 MB.  I will download todays daily and see what happens.

Thanks for the update!

---

### Post by Perpetual on 2008-09-29
Well, still does not work for me.  When the Ubuntu splash screen appears at boot, the progress bar moves a 1/3 of the way then stops.  I hit alt+F1 and it sits at 'Loading, please wait....'.  At this point, the cd drive is doing nothing.

If I then hold down ctl+alt the drive starts to work again.  If I hold ctrl+alt long enough, the disc will finally boot.  At 'Starting Hardware abstraction layer hald' it stops again.  If I then press ctrl+alt, the boot process begins again.  Eventually it stops at 'ubuntu@ubuntu:~$ and I have to hold down ctrl+alt to get it going again.  Immediately after I receive an error 'Ubuntu is running in low graphics mode'.  I can not get beyond this point.

Still a no go for me :confused:

---

### Post by captive on 2008-10-02
> **Kosimo said:**
> So, you are using a nVidia card and you can´t boot 27-4 kernel.  
+1 then

+1, on amd64.
don't know if it is the same issue, but I filed my bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276911")

---

### Post by Kosimo on 2008-10-03
> **captive said:**
> +1, on amd64.
don't know if it is the same issue, but I filed my bug [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276911")

From three days ago I can boot all daily builds with no issues at all, you should try them.

---

