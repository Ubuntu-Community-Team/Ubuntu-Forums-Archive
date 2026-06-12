---
title: "Ubuntu 6.06 + Core 2 Duo + SATA2"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by renatosilva on 2007-01-01
People, I've just buyed my machine and no linux I have here is working. Debian does not recognize SATA,. I'm running Kurumim on Live CD, but can't install it because it also doesn't recognize SATA (maybe for being an older version).

The newer Linux, and that which I like, is Ubuntu. My PC is:

Core 2 Duo E6300
MB Intel D946GZis
DDR2 533 1GB
HD SATA2 160GB

After Ubuntu's boot menu, it appears: "Uncompressing Linux......OK Booting the kernel", then the cursor blinks indefenidely....

I've already disabled USB and nothing....
At IRC people told me it's a problem of kernel <= 2.6.17  with the "JMICRON_PATA controller" on Core 2 Duo mobos...

Is there some alternative for me???????

* Make my old Kurumim recognize SATA
* Download a minimalist Linux (dialed connection) which works with C2D + SATA2?
* Dunno, anything!!!!!!!!!!

HEEEEEEEEEEEEEEELLLLLLLLLLLLLLLLLLPPPPPPPPPPPPP!!!!!!!!!!

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by PilotJLR on 2007-01-01
Ubuntu Edgy 6.10 and Fedora Core 6 work on this chipset, with some caveats:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

You should probably get an Edgy CD and pursue that...

---

### Post by renatosilva on 2007-01-06
It's ridiculous have to wait until April  to solve the problem and use Ubuntu.  ](*,) 

Don't break my heart Ubuntu, I love you  :(

---

### Post by PilotJLR on 2007-01-07
> **renatosilva said:**
> It's ridiculous have to wait until April  to solve the problem and use Ubuntu.  ](*,) 

Don't break my heart Ubuntu, I love you  :(

Huh?? Edgy is out now.

But, yes, an out-of-the-box fix where everything just work probably won't happen til Feisty.

---

### Post by clownius on 2007-01-07
If you have another machine running around.  
Plug the HDD in that machine.
Install Ubuntu
Update to the latest Ubuntu kernel
Reboot to make shure all works ok
Place HDD in your C2D and it should boot

I had the same issue with my own C2D a while back.  i actually had to compile my own kernel to fix it back then but the latest Ubuntu 6.10 kernel has this support back ported into it.  i know i have the C2D running on the generic kernel now

---

### Post by frisch16 on 2007-01-07
I had the same problem with my new machine. The live CD worked fine but trying to install gave me a blinking cursor. I had to reduce the LCD screen to something like 1280X1024 at boot time through the BIOS setup and then install Kubuntu (both Edgy and Feisty worked). When the install finished and I was in the new Kubuntu, I then set my display monitor and video cards to the proper higher resolutions. Hope this helps.

---

### Post by renatosilva on 2007-01-08
Pilot, so... it's ridiculous don't? Take a look:

1) There's a problem
2) People know the problem
3) People solve the problem
4) Ubuntu publishes a "hotfix" -- > LACKS HERE, WAIT FEISTY INSTEAD!

Otherwise I was thinking wether only upgrating to kernel 2.6.18 will solve the problem, it's not clear... I'll run Edgy today on my machine and hope at least it installs, then I update kernel and can use it normally....

---

### Post by PilotJLR on 2007-01-08
It's not great, but it's not ridiculous either... they stay a little behind cutting-edge for stability and testing purposes.

---

### Post by renatosilva on 2007-01-10
I've got! Installed Edgy sucessfully!

There's only a little irritant problem: i can't dial-up a connection!!!

The modem is shown on Networking, I've activated it, but there's no dialing application on menu. I've not found on Synaptic too. The only I've got is some **wvdial** whick attemps to connect but says something like "modem is not reponding". My modem is a PCI Lucent 56k.

The incredible fact is that how do I can connect on the older Kurumim 3.1? I've got Fedora Core 6 too but it didn't even detected my modem. Kpp stands on "waiting for modem".

Help me!

Anothyer question: in the future will I have problems with radio connection too???

---

### Post by renatosilva on 2007-01-10
I guess still the system is a kind of instable and I'm considering to install that customized kernel I've seen somewhere...

---

