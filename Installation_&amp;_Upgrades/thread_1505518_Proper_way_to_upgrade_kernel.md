---
title: "Proper way to upgrade kernel?"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by olwe on 2010-06-09
I've heard 2.6.34 is available, but sudo apt-get update sudo apt-get upgrade does nothing. I've seen wget...deb method, but is it safe? Should I just wait, or do I have something set wrong?

---

### Post by darkod on 2010-06-09
> **olwe said:**
> I've heard 2.6.34 is available, but sudo apt-get update sudo apt-get upgrade does nothing. I've seen wget...deb method, but is it safe? Should I just wait, or do I have something set wrong?

As far as I know, 2.6.34 will be the kernel for the next release, Maverick, due in October. It's still in development.

You won't have an upgrade option until October. You can try manual install but not as your main system, it's still in development, so it's not intended to be used as main system.

Otherwise, for trying out as live CD, or to install but not as your main system, you can get the daily build of Maverick here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It changes every few days though. Also, some things that work today, might be broken in the next cd image. That's what happens in the development cycle, until everything gets ironed out.

---

### Post by ajgreeny on 2010-06-09
I tried the beta5 version with no problems by downloading from the ubuntu.kernel site which I will look for again as I can't remember where it was.  2.6.34 is now in final release and should be fine, but don't uninstall the 32 version, keep it just in case.

I will find the address and post back.

---

### Post by snowpine on 2010-06-09
> **olwe said:**
> I've heard 2.6.34 is available, but sudo apt-get update sudo apt-get upgrade does nothing. I've seen wget...deb method, but is it safe? Should I just wait, or do I have something set wrong?

2.6.32 is the correct and supported kernel for 10.04 Lucid. Unless you have a specific reason for doing so, there is no need to upgrade to 2.6.34.

---

### Post by ajgreeny on 2010-06-09
Here you go, as promised, with the web-page for the final 2.6.34 kernel for lucid.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")
You should download the image itself, and the header file for the 32 or 64 bit version as appropriate, and the all deb header as well.  Copy all three files to an empty folder in home, and then from that folder run ```
sudo dpkg -i *
``` If the kernel presents you with any problems you can uninstall it through synaptic if you want to.

I agree with all the others' comments about using it, but when I tried it I was hoping  it would improve the behaviour of my old laptop with an ati9000m card  that ran far too hot.  I also tried it on my desktop, and could see no  problems at all.

However, I repeat, keep the older .32 version just in case anything goes wrong.

---

### Post by darkod on 2010-06-09
> **ajgreeny said:**
> Here you go, as promised, with the web-page for the final 2.6.34 kernel for lucid.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")
You should download the image itself, and the header file for the 32 or 64 bit version as appropriate, and the all deb header as well.  Copy all three files to an empty folder in home, and then from that folder run ```
sudo dpkg -i *
``` If the kernel presents you with any problems you can uninstall it through synaptic if you want to.

I agree with all the others' comments about using it, but when I tried it I was hoping  it would improve the behaviour of my old laptop with an ati9000m card  that ran far too hot.  I also tried it on my desktop, and could see no  problems at all.

However, I repeat, keep the older .32 version just in case anything goes wrong.

Thanks for this. Would you know if this kernel covers TRIM for SSD, or garbage collection or what ever it will be called?

I read somewhere that TRIM for linux is coming with kernel 2.6.34. Since Lucid is LTS I wasn't planning to jump for Maverick right away. However, I am hoping/planning to get SSD soon and it would be great if I can install 2.6.34 this way in Lucid and get the benefits of it.

---

### Post by ajgreeny on 2010-06-09
No, sorry, but I have no idea.

I do not run that system on the laptop now as I found that karmic worked so much better than Lucid on that machine, and the overheating did not seem to be overcome.  Perhaps it all needs a lot more tweaking; I just couldn't be bothered to keep trying when karmic was so good.

Mind you it took a while for karmic to work properly, and it was only after many, many updates.  ATI graphics and karmic (and now lucid) do not seem to work nicely together.  I live in hope that 10.10 will improve this and overcome the difficulty.

---

