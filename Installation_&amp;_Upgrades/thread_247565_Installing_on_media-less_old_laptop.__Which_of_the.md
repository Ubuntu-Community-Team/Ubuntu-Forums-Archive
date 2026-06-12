---
title: "Installing on media-less old laptop.  Which of these options?"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by alanmzifa on 2006-08-30
Hi, I'm awaiting delivey of an old laptop I bought second hand. Stupidly I missed the fact that it had no CD-ROM. I thought they all had! Anyway, I want to get Ubuntu on to it and the chip's a P3 and it has 256MB Ram so I think that should be ok but as I'm new to Ubuntu/Linux I was wondering if anyone might be able to offer some guidance. The laptop will arrive with no OS installed and as far as I can find out does not have the option to boot from USB.

I reckon I have 3 options.

1. Buy the proprietary cd-rom drive and cable (although ideally I'd like to avoid extra cost).

2. Find a way to fool the boot loader to think the USB pendrive is a cd-rom drive and do a live install from the USB pendrive. (I don't know if this is possible).

3. Put the laptop HDD into my desktop p.c. temporarily and install Ubuntu onto it there. I imagine this would identify all the wrong hardware and drivers though and would cause me problems when I put the HDD back into the laptop.

If anyone can contribute in any way to points 2 and 3 I'd find that useful in helping me make a decision.

Thanks

---

### Post by Omnios on 2006-08-30
Hi I am awaiting the delivery of a ibm laptop that had the cd drive broken. Anyways I talked to a few stores around where I live and there are two main options that are not garanteed to work as one store guy stated there is no garantee that it will work on boot and basicly its trail and error. 
 
 The most likely to work is a external cd rom. There is also the pen usb drives that may or may not work on boot pertaining to your speficic laptop biosy.

---

### Post by alanmzifa on 2006-08-31
Thanks for replying though if you re-read my post you'll see that booting from USB conventionally is not an option and the external cd-rom I'm already aware of. 


*I was hoping someone might know how to do points 2. or 3. above.*

---

### Post by Stone123 on 2006-08-31
Buy a 2.5 to 3.5 adapter cable and install ubuntu from desktop. 
[http://www.cable4pc.com/jpg/hard301.jpg](http://www.cable4pc.com/jpg/hard301.jpg)

> **alanmzifa said:**
> 
3. Put the laptop HDD into my desktop p.c. temporarily and install Ubuntu onto it there. I imagine this would identify all the wrong hardware and drivers though and would cause me problems when I put the HDD back into the laptop.


No it won't. Well if they don't change something it usualy modprobes a range of devices. You could install base system and let it install the rest from network. Search for netinstall cd or base system and edit sources.list. Still it needs that adapter. 

//i like this spell check in edgy.

---

### Post by alanmzifa on 2006-08-31
Ah, interesting Stone 123.

I've seen [this thread]("http://www.ubuntuforums.org/showthread.php?t=237431&highlight=netinstall+cd") and I've already got a 2.5/3.5 adapter. Was just wondering exactly how I would go about that.

1/ Would I disconnect my desktop HDD and replace with laptop HDD so that it's recognised by boot as a c/ drive?

2/ Presumably I'd just install as a live cd to the laptop HDD. I'd have to do a proper install while still in the desktop wouldn't I otherwise the OS copied from the desktop's CD drive would be gone.

3/ Then I'd re-install the laptop HDD in the laptop and boot (crossing fingers)?

4/ Anything else I'd have to do?

---

### Post by Stone123 on 2006-08-31
> **alanmzifa said:**
> Ah, interesting Stone 123.

I've seen [this thread]("http://www.ubuntuforums.org/showthread.php?t=237431&highlight=netinstall+cd") and I've already got a 2.5/3.5 adapter. Was just wondering exactly how I would go about that.

1/ Would I disconnect my desktop HDD and replace with laptop HDD so that it's recognised by boot as a c/ drive?


Yes make sure that laptop disk  is on Primary Master so when you take it back it will still be /dev/hda so grub can boot. 

> **alanmzifa said:**
> 
 2/ Presumably I'd just install as a live cd to the laptop HDD. I'd have to do a proper install while still in the desktop wouldn't I otherwise the OS copied from the desktop's CD drive would be gone.

I dont get your point here , anyway linux needs only to know where to boot from. It modprobes all soundcards and most other drivers so changing motherboard , cd rom  and such won't mater. 
Maby X will fail , so just change it later on laptop.Only what matters is /dev/hda where grub need to point linux kernel, but even that isn't that big of a deal. 

> **alanmzifa said:**
> 
3/ Then I'd re-install the laptop HDD in the laptop and boot (crossing fingers)?

Yeah .

---

### Post by Stone123 on 2006-08-31
server crash

---

### Post by Stone123 on 2006-08-31
1

---

### Post by alanmzifa on 2006-08-31
Stone123, thanks. 

That sounds like a plan. Expecting to have the laptop delivered in a few days so should be able to have a go at that then.

---

### Post by alanmzifa on 2006-09-01
Just wanted to update this thread for others to see in future.


Took HDD out of Dell laptop and using an appopriate adapter swapped it for my desktop pc's HDD.

Put in Dapper boot CD and rebooted desktop.

Loaded on and installed without any real problems.

Put laptop HDD back into laptop.

Booted but slight problem on boot with X server not laoding.

Sorted out via a command line instruction I got here which reconfigured the graphical interface.

===>  1 P3 700Mhz old CD-less laptop happily running ubuntu.

---

### Post by Omnios on 2006-09-01
Congratz, what kind of adapter do you need?

---

### Post by alanmzifa on 2006-09-01
Just a standard 2.5 to 3.5 inch HDD IDE adapter. You can pick them up off ebay for £2/£3, £5 delivered.

They come with a power connector and a 44 pin hard drive connector. The only thing that nearly caught me out was that the laptop HDD has it's own micro sized adapter to step down the 44 pins to a smaller set of 44 pins. It pulled off easily though, some might be screwed to the laptop HDD.

Couldn't believe it went so easily. Not at all like anything I normally do.

---

### Post by Omnios on 2006-09-01
Thanks now I have another option if or when I get my broken laptop.

---

