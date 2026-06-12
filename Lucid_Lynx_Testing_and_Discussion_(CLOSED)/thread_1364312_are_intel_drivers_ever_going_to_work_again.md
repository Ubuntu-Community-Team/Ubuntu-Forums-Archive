---
title: "are intel drivers ever going to work again?"
date: 2009-12-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by v1nsai on 2009-12-25
I'm on a Dell Studio 1555 with an Intel GM45 Mobile 4 Series card that hasn't worked properly on Ubuntu since the day I got it.  I've tried Karmic, Jaunty, Lucid and rolling back the drivers on Jaunty and it still registers as 'unclaimed' when I run lshw. Although in Lucid, the VGA adapter is now claimed, but the display adapter for the laptop screen still isn't claimed.

What can I do to help?  This is the first time I've run an alpha Ubuntu release so I'm a little unsure of how and what information I can send in to help get this resolved.  I know a lot of people with Intel cards will be really happy to see this release solve the problems we've been having.

---

### Post by ranch hand on 2009-12-25
Can you boot to the system?  If so file a but by;
```

ubuntu-bug <package with problem>

```
This will collect the needed info and send it, and you to launchpad.  You will need an account there.  They walk you through the whole ordeal very well with their instructions.

---

### Post by keypox on 2009-12-25
I have intel gma 4500mhd 

It works in 9.:04, 9.10.   9.10 being better

---

### Post by v1nsai on 2009-12-25
> **keypox said:**
> I have intel gma 4500mhd 

It works in 9.:04, 9.10.   9.10 being better


Is that the same as mine? I'm having trouble figuring out which card I have.  According to 'glxinfo | grep Intel' I have a Mobile Intel® GM45 Express Chipset, but when I trun 'lshw -C display' it tells me I have a Mobile 4 Series card.

Anyway, like I said the problem is that when I run 'lshw' my display adapter and VGA adapter are both listed as unclaimed.  The performance is actually pretty good, some of the window animations in compiz were a little choppy so I disabled them, but I'm running a pretty sleek and modern desktop very smoothly here.

The problem is that both VMware and wine applications don't seem to recognize the graphics card, which leads me to believe that the 'unclaimed' issue is to blame.

Hey keypox would you run 'lshw -C display' and tell me if your adapter is claimed?  I'm going to cry if yours is claimed, I've gone through Jaunty, Karmic, Lucid, Fedora Core 12 and Debian Testing and all of them tell me the card is unclaimed.

---

### Post by ranch hand on 2009-12-25
I would try;
```

lspci

```

---

### Post by v1nsai on 2009-12-25
lspci | grep Display
```
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)  
```


I don't get why you suggested that.  The card is there, but there isn't a module being loaded for it, as indicated by lshw.

```
  *-display:0 UNCLAIMED                                                                                             
       description: VGA compatible controller                                                                       
       product: Mobile 4 Series Chipset Integrated Graphics Controller                                              
       vendor: Intel Corporation                                                                                    
       physical id: 2                                                                                               
       bus info: pci@0000:00:02.0                                                                                   
       version: 07                                                                                                  
       width: 64 bits                                                                                               
       clock: 33MHz                                                                                                 
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc000000-fc3fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc400000-fc4fffff
```

---

### Post by ranch hand on 2009-12-26
I suggested that because it gave you the chipset which is what you NEED to know to pick a driver.

---

### Post by phillw on 2009-12-26
Hi, a quick search within intel for linux and your chipset threw up --> [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family)

It reports that there are linux drivers available, but, not having your chipset, you're on your own for testing them. Do report back if they are of use to you.

Not wishing to "rub it in" but > 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
 on a Gateway Laptop works 'out of the box' -- These graphics chips will be the death of us all !!!!!

Regards,

Phill.

---

### Post by Starks on 2009-12-26
As I've said in other topics, the drivers for the i945 are quite godly right now. Other chipsets could use a bit more love though.

---

### Post by VMC on 2009-12-26
> **phillw said:**
> Hi, a quick search within intel for linux and your chipset threw up --> [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Graphics&ProductLine=Laptop+graphics+controllers&ProductProduct=Mobile+Intel%C2%AE+4+Series+Express+Chipset+Family)

It reports that there are linux drivers available, but, not having your chipset, you're on your own for testing them. Do report back if they are of use to you.
 Using that link , I put in "Mobile 4" and it reported several drivers. Thats a good link to bookmark. Thanks.

---

### Post by falconindy on 2009-12-26
> **v1nsai said:**
> I'm on a Dell Studio 1555 with an Intel GM45 Mobile 4 Series card that hasn't worked properly on Ubuntu since the day I got it.  I've tried Karmic, Jaunty, Lucid and rolling back the drivers on Jaunty and it still registers as 'unclaimed' when I run lshw. Although in Lucid, the VGA adapter is now claimed, but the display adapter for the laptop screen still isn't claimed.

What can I do to help?  This is the first time I've run an alpha Ubuntu release so I'm a little unsure of how and what information I can send in to help get this resolved.  I know a lot of people with Intel cards will be really happy to see this release solve the problems we've been having.
Ever looked into KMS? Intel cards need it to function properly in later kernels.

---

### Post by v1nsai on 2009-12-26
I tried to download the drivers from Intel before, and after filling out an annoying registration form (every single field had to be answered) I was allowed to download the driver for Fedora Core 10 or 7, Wind River Linux or Red Hat.  I downloaded the Fedora one and got a .exe -_- Intel and their stupid website can shove it.

I'm reading up on KMS before I try it out, I'll post if that works thanks for the tip.

---

### Post by jerrylamos on 2009-12-26
> **v1nsai said:**
> I'm reading up on KMS before I try it out, I'll post if that works thanks for the tip.

For over a year Alpha, Beta, and Release Code Ubuntu Xorg has been failing one way or another on either of my two pc's with intel video graphics i830 and i840.

Frequently to get them to go I resort to editing the grub kernel line to replace "quiet splash" with "nomodeset" which turns KMS off.

Do note I try a number of other linux distros and simply do not have the Xorg problem Ubuntu has with intel graphics.

Jerry

---

### Post by v1nsai on 2009-12-27
So KMS is enabled by default?  I have to use 'nomodeset' if I want to have a display, I only get a weird black and green screen without it. I tried 'i915.modeset=1' in place of nomodeset too, same effect.

---

### Post by jerrylamos on 2009-12-28
> **v1nsai said:**
> So KMS is enabled by default?  I have to use 'nomodeset' if I want to have a display, I only get a weird black and green screen without it. I tried 'i915.modeset=1' in place of nomodeset too, same effect.

You might have better luck with 'i915,modeset=0' since =1 turns it on.

Jerry

---

### Post by v1nsai on 2009-12-28
Wouldn't i915.modeset=0 be the same as nomodeset?

---

### Post by GeorgeVita on 2009-12-29
Hi to all above,
running LL a1 + updates (2.6.32-9-generic #13) on EeePC 1000H **netbook** with the standard Intel **945GME** Graphics Controller I faced a 'psychedelic' result to my screen after trying ```
lshw | grep -i ethernet
``` Screen capture worked well (all in position) but the visual result was as attached photo.

Note: I am using full installation to SDHC

Can anybody with same h/w check it?

Thanks in advance,
George

---

