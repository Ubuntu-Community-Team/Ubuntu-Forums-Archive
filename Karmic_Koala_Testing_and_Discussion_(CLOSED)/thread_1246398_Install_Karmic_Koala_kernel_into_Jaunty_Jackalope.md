---
title: "Install Karmic Koala kernel into Jaunty Jackalope"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by M.deHaas on 2009-08-21
Hi all,

I've been given a netbook recently and I really want it to work with Ubuntu Netbook Remix. The interface is just stunning, easy, fast and nicely done for a netbook. 

I just have one problem, my wireless and wired network isn't working. I've found (and verified) the wired interface functions under 9.10 Alpha4. I've also installed it but it's *really* unstable on my machine. According to the post I found the network problem is solved by means of a kernel patch. So I would like to install the shiny new kernel into an existing 9.04 UNR install without network connectivity.

Can anyone guide me to get this done?

Best Regards,
Marcel

---

### Post by jwaffolter on 2009-08-21
You will need some way to download the debfiles from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30.5/"), you will need three of the packages
linux-headers.....alll.deb
linux-headers.....i386.deb
linux-image......i386.deb
(use i386 version, unless you know your using a 64-bit machine)

Open a terminal Applications->Accessories->Terminal; and type
cd /home/<location_of_downloads>

and
sudo dpkg -i *.deb

---

### Post by M.deHaas on 2009-08-22
Thanks,

That's working like a charm. Do I need to edit my sources so this kernel will stay the in use? I'm updating the system now and it stated is would be downloading the .28 kernel which is bad for me, I need 29 or higher.

Best regards,
Marcel

---

### Post by jfernyhough on 2009-08-22
You could also use a PPA which has backports of the Karmic kernel to Jaunty. This means it's updated as and when the kernel itself is updated.

[https://edge.launchpad.net/~a7x/+archive/kbp](https://edge.launchpad.net/~a7x/+archive/kbp)

---

### Post by kansasnoob on 2009-08-26
> **jfernyhough said:**
> You could also use a PPA which has backports of the Karmic kernel to Jaunty. This means it's updated as and when the kernel itself is updated.

[https://edge.launchpad.net/~a7x/+archive/kbp](https://edge.launchpad.net/~a7x/+archive/kbp)

Just FYI I did this a couple days ago and it's working great! No caveats at all on my hardware.

Thanks for the link!

---

### Post by MaxRC on 2009-09-25
Sorry, I am new to all this, how do I install Karmic into Jaunty using the a7x PPA?  I went to the link above and and understand about adding the repository to the sources.list file.  But what commands do I run to install the entire package?

---

### Post by terry_gardener on 2009-09-25
if you have installed the ppa and the key then just run update-manager and it should update the kernel to the latest version in the ppa.

---

### Post by VMC on 2009-09-25
> **MaxRC said:**
> Sorry, I am new to all this, how do I install Karmic into Jaunty using the a7x PPA?  I went to the link above and and understand about adding the repository to the sources.list file.  But what commands do I run to install the entire package?

There's a "?" hovering "Read about installing". If you can't get there then here is the [link]("https://edge.launchpad.net/+help/soyuz/ppa-sources-list.html")It's self explanatory. Backup first though.

---

