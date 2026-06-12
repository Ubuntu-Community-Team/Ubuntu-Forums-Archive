---
title: "Can't install Ubuntu or Lubuntu on any AMD/ATI computer"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by hstrent51 on 2013-11-23
This one has me stumped. This problem is the same whether I'm using a laptop or a desktop and I have tried several Linux distros on several different machines with the same result. I simply cannot install newer versions of Ubuntu/Lubuntu/Linux on many of the AMD/ATI gpu-based machines I work on these days. This is true whether or not the gpu is onboard or in the form of a discrete card. I have only tried this with Live CDs and it will not either install or run from the live CD. Everything is fine up through choosing my language and choosing whether I will "install" or "try it" and when I hit enter the screen goes blank and the hard drive locks up (the LED is on continually). And I'm dead in the water. This is happening with computers whose gpus are several years old. However, I do not run into this problem on systems with Intel or Nvidia GPUs. Any ideas what's going on? Any suggestions? Now I realize that the ATI/AMD Linux drivers have never been as good as the Nvidia ones but you would think that would not be a problem with the install. Note, I can run Ubuntu 13.10 on my PC that has an AMD 6850 video card. Is the problem that the newer versions of the linux kernel have dropped all but newer AMD gpu drivers?

---

### Post by Bucky Ball on 2013-11-24
Boot from the CD, when you get to the 'Try' 'Install' screen, hit F6. Choose 'nomodset' from the pop-up menu. Proceed.

Any different?

---

### Post by hstrent51 on 2013-11-24
> **Bucky Ball said:**
> Boot from the CD, when you get to the 'Try' 'Install' screen, hit F6. Choose 'nomodset' from the pop-up menu. Proceed.

Any different?

Tried that already. Doesn't change anything. I was working on an old Pentum 4 motherboard that I had inserted a Radeon 9250 PCI video card into. Before adding the video card I had no problem with installing Lubuntu 13.10 using the onboard Intel chipset. But I did burn an older version of Ubuntu to disc (8.10) and it worked fine with the Radeon 9250. My conclusion is that the problem is driver related and that the newer Linux versions have dropped support for older Radeon GPUs. Or maybe something is broken. But I also had this problem a few months ago when I was trying to install Linux on socket AM3/AM3+ motherboards with AMD chipsets that were not that old. If I stuck an Nvidia 210 card in those boards I could install Linux. Now, an Nvidia 210 is not that new.

---

### Post by Mark Phelps on 2013-11-24
> Is the problem that the newer versions of the linux kernel have dropped all but newer AMD gpu drivers? 

Not so much that, but AMD periodically drops support for Linux drivers for their chipsets.  They dropped the HD 2x/3x/4x-series chipset last summer; they dropped the X-series before that.  They have not supported the HD 9xxx series in several years -- which is why Ubuntu 8.x works with that chipset but not the newer Ubuntu versions.

If "nomodeset" does not do anything, try "xforcevesa" instead.  I had to do that with 13.04 and my AMD HD 4xxx chipset.

---

### Post by hstrent51 on 2013-11-24
I guess I don't understand the process of how the kernel is compiled but is it the case that AMD has to rebuild the drivers for every product for each new Linux kernel release? The existing ones just can't be folded into the new kernel? Pardon my ignorance but I'm neither a programmer or a software engineer and I'm really not an experienced Linux user either. 

I play around with Ubuntu every now and then but only at the GUI level and once in a while I'll do something with the terminal. The "xforcevesa" command you suggest would have to be entered using a text mode installer I take it. And that I've never done. Can you give some detailed instructions or provide me with a link that can do that? 

I'll tell you where I'm headed with this. I'm semi retired and run a small technology business out of my home. I work with a lot of older people whose kids have handed down the old Windows XP machine to them. 

In April, MS will discontinue all support for XP, including security patches. 

Since all many of these older folks do with their computers is email and web surfing it occurred to me that Ubuntu (or Lubuntu) might be just the ticket for them since their hardware is not Win 7 or Win 8 capable. 

That's why I've been experimenting this weekend with Linux on this old Pentium 4 motherboard. The old native Intel chipset is accepted by the newer Linux versions but are incapable of rendering streaming video properly. So when you go to a web page with embedded streaming video you get this weird sepia like effect in that part of the page. 

Also, using a discrete video card frees up some system memory which is usually in short supply on these old systems but this is the kind of system I'm often working with in my business. These people are often on fixed incomes and can't afford a new system.

---

### Post by mörgæs on 2013-11-24
Here's a possible solution to the Intel graphics problem:
[http://ubuntuforums.org/showthread.php?t=2182038&page=3&p=12851111&viewfull=1#post12851111](http://ubuntuforums.org/showthread.php?t=2182038&page=3&p=12851111&viewfull=1#post12851111)

Though AMD frequently shut down their closed-source drivers the open ones should work, also for older cards. Have you tried installing Lubuntu 13.10 with the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by hstrent51 on 2013-11-24
Tried the install with alternate ISO as you suggested, morgaies. Install went without a hitch but on the post install reboot it hung up again as it had been doing before. I got an old Nvidia FX 5200 PCI card off ebay on the way later this week. I'll be interested to see if the newer Linux kernels will work with it.

---

### Post by mörgæs on 2013-11-25
Are you able to boot into recovery mode?

Here's something about [boot options]("https://help.ubuntu.com/community/BootOptions").

---

