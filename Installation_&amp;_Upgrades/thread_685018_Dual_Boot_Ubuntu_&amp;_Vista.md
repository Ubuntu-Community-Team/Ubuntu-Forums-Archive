---
title: "Dual Boot Ubuntu &amp; Vista"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by NatroXz on 2008-02-01
Hi ,

Just installed Ubuntu7.10, I have Vista on another partion.

The problem now is that "Grub" Ubuntu is the only one that will boot.
I have no choice to  Vista.
I really need to get into Vista/outlook for some important documents.

I have found that you can edit the files to Grub(like "boot.ini") and add
your OS there, but Im kinda a newbee on Linux and having problems with this.

Please, Please help me!

---

### Post by skierkegaard on 2008-02-01
You will have to add Vista to your menu.lst file.  There are many posts all over the forums about this,

Example: [http://ubuntuforums.org/showthread.php?t=566874](http://ubuntuforums.org/showthread.php?t=566874)

---

### Post by NatroXz on 2008-02-07
Finaly, I found the solution:)

So Easy It Was, see [here]("http://auscoder.com/2007-05-18/restore-vista-mbr-bootloader.html")

Now a new problem shows up, now I can´t boot into Ubuntu anymore.

Think I have tried every setting there is in EasyBCD, but no luck.

Anybode an expert on the program?

Here is the setting from EasyBCD
```
There are a total of 2 entries listed in the Vista Bootloader.
Bootloader Timeout: 30 seconds.
Default OS: Windows Vista (TM) Ultimate (recovered) 

Entry #1

Name:  Windows Vista (TM) Ultimate (recovered) 
BCD ID:  {current}
Drive:  D:\
Bootloader Path:  \Windows\system32\winload.exe
Windows Directory:  \Windows

Entry #2

Name:  NeoSmart Linux
BCD ID:  {f1e13d41-d513-11dc-a757-cd8d118dfcec}
Drive:  C:\
Bootloader Path:  \NST\nst_grub.mbr
```

And here is a picture from the partions in EasyBCD

---

### Post by NatroXz on 2008-02-08
Hmm, nobody that knows:confused:

I got the fealing that this was the forum that was "**The Place**"
People was telling me that this was almost like "**Live Chat**"

So people I realy need you input on this.
I´m kinda  ](*,) these days.

---

### Post by confused57 on 2008-02-08
> **NatroXz said:**
> Hmm, nobody that knows:confused:

I got the fealing that this was the forum that was "**The Place**"
People was telling me that this was almost like "**Live Chat**"

So people I realy need you input on this.
I´m kinda  ](*,) these days.
I have no experience with EasyBCD or Vista, but you may need to install grub to the root partition, which you can do with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

See the above instructions, but to install to the root partition:
```
root (hdx,y)
setup (hdx,y)
```

---

### Post by NatroXz on 2008-02-08
Thanks:)

Will try that guide!

---

