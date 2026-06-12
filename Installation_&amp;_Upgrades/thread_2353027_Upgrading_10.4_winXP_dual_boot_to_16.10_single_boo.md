---
title: "Upgrading 10.4 winXP dual boot to 16.10 single boot"
date: 2017-02-18
forum: Installation &amp; Upgrades
---

### Post by arjanjon on 2017-02-18
Hi, I want to dust of an ancient system. It is currently running dual boot Ubuntu 10.4 & Windows XP. I'm a bit lost what the best strategy would be to end up with a single boot 16.10 system. I'd prefer to keep the documents/pictures on the Ubuntu partition and actually upgrade, but a complete reinstall would be acceptable too.
What order should I follow in terms of removing the win partition and upgrading?

Thanks, Arjan

---

### Post by howefield on 2017-02-18
Is the hardware capable would be my first thought ?

There is a big difference in requirements going from 10.04 to 16.10 particularly with regards the graphics card.

What are the machine specifications ?

---

### Post by RobGoss on 2017-02-18
If you're wanting to have a single boot just run the live installer and let it do it's thing, I see you''re installing 16.10, I'm not sure if you are aware but this distribution will be ending in just a few months, you can view the release page for Ubuntu [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I would stick with the** LTS **releases unless you prefer to have to do a new installation every few months. Anything that's running Windows XP would be a concern and you might want to consider a lighter version of Ubuntu like Lubuntu, it requires less resources and might preform better

---

### Post by arjanjon on 2017-02-18
It's a 2.4 GHz quad core with 2 GB RAM and a GeForce 9600 GT card, so that should work, right?

---

### Post by howefield on 2017-02-18
> **arjanjon said:**
> It's a 2.4 GHz quad core with 2 GB RAM and a GeForce 9600 GT card, so that should work, right?

As far as it goes, yes that sounds good and although 2GB is "tight" for Ubuntu with the Unity interface it isn't completely unreasonable, but not sure I'd call specs like that ancient :)

I'd suggest creating the Live media with your preferred Ubuntu and trying it out in Live mode first of all to make sure you are happy with performance and have everything working.

All being well, doing a clean install and mounting the existing Ubuntu partition but not marking it for formatting during the install process would keep your /home folder intact, having said that it's only prudent to have a back up of your important data before taking on such a potentially risky task. You could delete/reformat the XP partition from the installer as well.

My personal preference would be to back up all important data and wipe the disk clean with Gparted from the Live media, create the partitions, mount and install then copy back the important data. This would let me get the partitions exactly how I'd want them.

---

### Post by Bucky Ball on 2017-02-18
> **arjanjon said:**
> It's a 2.4 GHz quad core with 2 GB RAM and a GeForce 9600 GT card, so that should work, right?

Right, but you would probably have a snappier computing experience with, and I would personally go for, a lighter flavour, Xubuntu or Lubuntu for instance.

And as above: why 16.10? Interim releases now have nine months support and 16.10 will be dead by the middle of this year. You'll be upgrading every six months. LTS releases now have five years support (three years for Xubuntu and Lubuntu) and 16.04 LTS is supported until 2021 for Ubuntu.

---

### Post by RobGoss on 2017-02-18
#1 Howefield

> What order should I follow in terms of removing the win partition and upgrading   

I would just backup anything that's important and do a clean installation, avoid having to spend hours trouble shooting your system

If you run the** live media** and all runs well that's a good sign your machine will be able to handle the OS and you can begin your installation

---

### Post by arjanjon on 2017-02-18
Thanks all, this should get me started.

As for the 16.10, that was a misread/false memory on my side, I thought LTS came along once every half year instead of every two years... 16.04 will do just fine.
I'll have a look at the lighter versions.

Topic closed as far as I'm concerned

---

### Post by RobGoss on 2017-02-18
The LTS releases are about every 5-years which is more convenient for it's users

You can mark this thread as solved if you no longer need assistance by using the **Thread tool **at the top of this post  

Thanks so much and best of luck

---

### Post by howefield on 2017-02-18
> **RobGoss said:**
> The LTS releases are about every 5-years which is more convenient for it's users

No.

Long Term Support releases are every 2 years with the option of keeping them for 5 years which may be what you meant. The OP is currently on an expired LTS (10.04) and since then there has been 12.04, 14.04 and the current 16.04, the next one will be 18.04.

---

### Post by slickymaster on 2017-02-18
> **howefield said:**
> No.

Long Term Support releases are every 2 years with the option of keeping them for 5 years which may be what you meant. The OP is currently on an expired LTS (10.04) and since then there has been 12.04, 14.04 and the current 16.04, the next one will be 18.04.

This ^^^

The only exception being Xubuntu. All Xubuntu LTS releases come every 2 years but they only get support for three years, not five like the rest of the flavors.

---

### Post by Bucky Ball on 2017-02-18
> **slickymaster said:**
> The only exception being Xubuntu.

And Lubuntu, I do believe. :)

---

### Post by RobGoss on 2017-02-18
> 
Long Term Support releases are every 2 years with the option of keeping them for 5 years which may be what you meant. The OP is currently on an expired LTS (10.04) and since then there has been 12.04, 14.04 and the current 16.04, the next one will be 18.04.    


Yes that's what I meant thank you for clarifying that Howefeild always good to know

So they are released every **two years **with the option of support for **5-years** correct

---

### Post by slickymaster on 2017-02-19
> **Bucky Ball said:**
> And Lubuntu, I do believe. :)

Right you are, Bucky. My apologies to Lubuntu.

---

### Post by howefield on 2017-02-19
> **RobGoss said:**
> Yes that's what I meant thank you for clarifying that Howefeild always good to know

So they are released every **two years **with the option of support for **5-years** correct

Yes, that's correct. Long Term Support versions are released every two years and supported for 5 years, I believe this is the case for Ubuntu and Ubuntu Kylin. All the other flavours release an LTS every 2 years but are supported for 3 years instead of 5. 

PS. Ubuntu used to support the desktop LTS for 3 years but moved to 5 in order to bring it in line with the server edition life cycle which at that time was 5 years.

---

### Post by RobGoss on 2017-02-19
Great to know thanks so much for letting us all know, I stick to the LTS versions seems the right thing to do

Have a great day

---

